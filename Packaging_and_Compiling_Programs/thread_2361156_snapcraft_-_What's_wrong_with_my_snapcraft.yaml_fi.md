---
title: "snapcraft - What's wrong with my snapcraft.yaml file?"
date: 2017-05-13
forum: Packaging and Compiling Programs
---

### Post by jsc12345 on 2017-05-13
I'm trying to snap the code contained it [https://githun.com/LLK/scratch-flash]("http://[URL")]this repository[/URL] to port it to Linux, as the official version relies on the Adobe AIR framework to run. I created a snapcraft.yaml file as per the instructions at [Ubuntu Tutorials]("https://tutorials.ubuntu.com/tutorial/create-first-snap#2"). My file is as follows: 
```
name: scratch-2.0-offline-editor # you probably want to 'snapcraft register <name>'version: '2.0' # just for humans, typically '1.2+git' or '1.3.2'
summary: 
description: |
This app is an unofficial Snap of the Scratch 2.0 Offline EditoThe standard version is dependant on the Adobe AIR framework, which has not
supported Linux since version 2.6.0. For more information, please visit: 
wiki.scratch.mit.edu/Scratch_2.0_Offline_Editor


grade: devel # must be 'stable' to release into candidate/stable channels
confinement: devmode # use 'strict' once you have the right plugs and slots


parts:
my-part:
source: https://github.com/LLK/scratch-flash
plugin: nil[CODE]
However, when I run it with the "snapcraft" command, it returns the following error:
[CODE]Issues while validating snapcraft.yaml: The 'name' property does not match the required schema: 'scratch-2.0-offline-editor' does not match '^[a-z0-9][a-z0-9+-]*$'
The 'name' property does not match the required schema: 'scratch-2.0-offline-editor' does not match '^[a-z0-9][a-z0-9+-]*$' 
``` 
What's wrong?

---

