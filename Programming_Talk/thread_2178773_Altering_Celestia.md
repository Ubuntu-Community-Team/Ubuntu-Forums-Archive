---
title: "Altering Celestia"
date: 2013-10-05
forum: Programming Talk
---

### Post by tsunalugi on 2013-10-05
Hey there,

I'm actually trying to use Celestia program alterations with the goal of using linguistical & culturally arcane names for the Astra. The appearing problem is it's missing the local files & potentially loading from a database. Configuration file suggests a folder named '/data/...' where such is not visible in the file system. Addon scripts are mentioned a potential. I'm refrencing the wiki page resources at:

[http://en.wikibooks.org/wiki/Celestia/Customization](http://en.wikibooks.org/wiki/Celestia/Customization)

Any helps are greatly appreciated...

:)

---

### Post by Vaphell on 2013-10-05
celestia like most programs stores its resources in /usr/share/
data dir would be /usr/share/celestia/data

iirc you can extend/modify/override these global files without changing them for other users by putting stuff into user specific $HOME/.local/share (~/.local/share is user specific /usr/share)

---

