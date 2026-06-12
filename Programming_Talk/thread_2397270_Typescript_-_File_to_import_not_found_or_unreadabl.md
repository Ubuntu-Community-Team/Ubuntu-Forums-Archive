---
title: "Typescript - File to import not found or unreadable"
date: 2018-07-27
forum: Programming Talk
---

### Post by paulsabana on 2018-07-27
Hello all,

I've been working to figure out a solution to my Typescript problem on-and-off for a couple of weeks. I have tried all stackoverflow and forum answers I could find but my Typescript has difficulty traversing the source files linking imports.

Module build failed:
    @import "./resizedImagePreview/resizedImagePreview.scss";
    ^
          File to import not found or unreadable:

Error like the one above are many. I've tried multiple Typescript versions, types versions, and specified the ModuleResolution strategy in the tsconfig.json file. This project compiles fine on Windows 10.

This is an error on the following Ubuntu:

Description:    Ubuntu 18.04 LTS
Release:        18.04
Codename:       bionic

---

