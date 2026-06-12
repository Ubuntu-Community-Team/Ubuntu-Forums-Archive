---
title: "Ubuntu - Eclipse"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by guy.dillen on 2014-01-06
What is the difference between sudo apt-get install **eclipse** and sudo apt-get install **eclipse-platform **when installing Eclipse? Which one should I take?
Thanks.

---

### Post by oldos2er on 2014-01-06
The difference in the two packages descriptions is ```
apt-cache show eclipse

Description-en: Extensible Tool Platform and Java IDE
 The Eclipse Platform is an open and extensible platform for anything and yet
 nothing in particular. It provides a foundation for constructing and running
 integrated software-development tools. The Eclipse Platform allows tool
 builders to independently develop tools that integrate with other people's
 tools so seamlessly you can't tell where one tool ends and another starts.

This package provides the whole Eclipse SDK that contains Eclipse Platform,
 Java development tools and Plug-in Development Environment, including source
 and both user and programmer documentation.

``` and ```
apt-cache show eclipse-platform

Description-en: Eclipse platform without development plug-ins
 The Eclipse Platform is an open and extensible platform for anything and yet
 nothing in particular. It provides a foundation for constructing and running
 integrated software-development tools. The Eclipse Platform allows tool
 builders to independently develop tools that integrate with other people's
 tools so seamlessly you can't tell where one tool ends and another starts.
 .
 This package provides the Eclipse Platform and is the base for all Eclipse
 development plug-ins, but it does not include any. These are available in
 different packages, for example:
 .
  * eclipse-jdt Java Development Tools
  * eclipse-pde Plug-in Development Tools
  * eclipse-cdt C/C++ Development Tools
```

---

