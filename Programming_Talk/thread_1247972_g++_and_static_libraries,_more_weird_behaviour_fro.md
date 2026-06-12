---
title: "g++ and static libraries, more weird behaviour from this compiler/linker"
date: 2009-08-23
forum: Programming Talk
---

### Post by bender1234 on 2009-08-23
Hey

I'm currently porting some code to linux, and I've run into (yet another) abnormality with the g++ compiler, well linker.

I have several static libraries, some are dependent on the lower lvl ones. If I don't use any of the lower lvl ones in my project that use the higher lvl ones, the linker doesn't understand that it has to link the lower lvl ones at all... Is there any flags to force the linker to link them in? Does the linker behave differently with .so libraries?

forinstance these two classes are from two different libraries.
Xml_t cXml("ballefrans.xml");
Scene_t cTestScene("test.xml", "textures");

that works, but when dropping the first line the linker just skips linking in the lib and generates tons of um
"unresolved externals" in windows terms.

cheers,
bender

---

### Post by bender1234 on 2009-08-23
Solved.

Change the order in which you link the libraries........

nogood:
../common/linux/common.a ../xml/linux/xml.a ../glengine/linux/glengine.a

good
../glengine/linux/glengine.a ../common/linux/common.a ../xml/linux/xml.a 

hehe and y I know a bit of a ******* structure there ;)

---

