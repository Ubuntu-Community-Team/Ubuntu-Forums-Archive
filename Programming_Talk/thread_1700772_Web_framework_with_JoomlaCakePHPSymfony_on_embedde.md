---
title: "Web framework with Joomla/CakePHP/Symfony on embedded"
date: 2011-03-05
forum: Programming Talk
---

### Post by AchimRS on 2011-03-05
Hi all experts,
I want to start a new web project and need some recommendations according the framework technology. The aim is a controllers user interface, so a kind of Human-Machine-Interface (HMI).

I'm using Ubuntu/Debian with Apache, PHP and (if needed) MySQL on an embedded environment (ARM with 400MHz and 64MB RAM). Here are some requirements:
- fast access even on this slow hardware
- support of a wide set of browsers (MS IE >=5, Firefox, Safari Mobile)
- user groups with different access rights
- live update of some values (without manual refresh, some kind of push)
- wizard driven installation routines to add new hardware or functions
- similar look&feel on PC, netbook, mobile with different screen resolution
- unit test support
- undo and redo functionality
- l10n and i18n
- dynamically loadable extensions (call it modules, applications or plug-ins)

But what is the framework able to implement this with lowest effort? I thought on:
- Joomla
- Symfony
- Lithium
- CakePHP
- Joomla + CakePHP
- or some other combination or tools

Any idea?!?!?!?
  thanks Achim

---

### Post by garak on 2011-07-29
Symfony

---

