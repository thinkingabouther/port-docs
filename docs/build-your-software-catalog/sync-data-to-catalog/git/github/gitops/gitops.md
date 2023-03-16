---
sidebar_position: 3
---

import Tabs from "@theme/Tabs"
import TabItem from "@theme/TabItem"
import PortYmlStructure from '../../\_port_yml_gitops_structure_template.md'

# GitOps

Port's GitHub integration makes it possible to manage Port entities with a GitOps approach, making your code repositories into the source of truth for the various infrastructure assets you want to manage.

## 💡 GitHub GitOps common use cases

- Use GitHub as the source-of-truth for your **microservices**, **packages**, **libraries** and other software catalog assets;
- Allow developers to keep the catalog up-to-date, by making updates to files in their Git repositories;
- Create a standardized way to document software catalog assets in your organization;
- etc.

## Managing entities using GitOps

To manage entities using GitOps, you will need to add a `port.yml` file to the **default branch** (usually `main`) of your repository.

The `port.yml` file can specify one or more Port entities that will be ingested to Port, and any change made to the `port.yml` file will also be reflected inside Port.

This configuration turns your GitHub repositories to the source-of-truth for the software catalog.

### GitOps `port.yml` file

The `port.yml` file is how you specify your Port entities that are managed using GitOps and whose data is ingested from your Git repositories.

Here are examples for valid `port.yml` files:

<Tabs groupId="format">

<TabItem value="single" label="Single entity">

```yaml showLineNumbers
identifier: myEntity
title: My Entity
blueprint: myBlueprint
properties:
  myStringProp: myValue
  myNumberProp: 5
  myUrlProp: https://example.com
relations:
  mySingleRelation: myTargetEntity
  myManyRelation:
    - myTargetEntity1
    - myTargetEntity2
```

</TabItem>

<TabItem value="multiple" label="Multiple entities">

```yaml showLineNumbers
- identifier: myEntity1
  title: My Entity1
  blueprint: myFirstBlueprint
  properties:
    myStringProp: myValue
    myNumberProp: 5
    myUrlProp: https://example.com
  relations:
    mySingleRelation: myTargetEntity
    myManyRelation:
      - myTargetEntity1
      - myTargetEntity2
- identifier: myEntity
  title: My Entity2
  blueprint: mySecondBlueprint
  properties:
    myStringProp: myValue
    myNumberProp: 5
    myUrlProp: https://example.com
```

</TabItem>

</Tabs>

Since both of the valid `port.yml` formats follow the same structure, the following section will explain the format based on the single entity example.

### `port.yml` structure

<PortYmlStructure/>

## Examples

Check out the [example repository](https://github.com/port-labs/github-app-setup-example) for a microservice blueprint and a matching `port.yml` file which specifies a microservice entity.

## Advanced

Refer to the [advanced](../advanced.md) page for advanced use cases and configurations.