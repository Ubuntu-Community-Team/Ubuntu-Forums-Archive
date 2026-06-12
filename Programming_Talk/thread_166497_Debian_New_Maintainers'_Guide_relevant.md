---
title: "Debian New Maintainers' Guide: relevant?"
date: 2006-04-26
forum: Programming Talk
---

### Post by Rxke on 2006-04-26
Hi,

I've been trying to build some stuff, and found out the boring way Ubuntu doesn't come with dev-stuff installed as default.
Fair enough, you won't hear me complain, because I love the fact that the installer fits one one disk :)

So, after some piecemeal installing of dev libraries, I thought I'd better look for a good howto/tutorial re: building the Ubuntu/Debian way, and swiftly found my way to the excellent [Debian New Maintainers' Guide]("http://www.debian.org/doc/maint-guide/").
Very nice, but there's one question that popped up when reading the lead-in of section 1:>  Before you start anything, you should make sure that you have properly installed some additional packages needed for development. Note that the list doesn't contain any packages marked `essential' or `required' - we expect that you have those installed already.


Now I know Ubuntu is a younger halfbrother of Debian ;) so a very whole lot is the same, but can I safely assume things Debian considers 'essential' and 'required' are also in Ubuntu? I mean: following the guide, will i have set up a system that's 'complete' to buid stuff the Debian/Ubuntu way?

---

### Post by Rxke on 2006-04-26
:-# Answering my own question, looks like my suspicion was correct...

From UDSF (and shame on me for not checking my own sig (!):     >  * There is a few programs to install: 


sudo apt-get install build-essential dh-make debhelper devscripts



---

