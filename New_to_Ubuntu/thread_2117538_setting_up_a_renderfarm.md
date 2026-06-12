---
title: "setting up a renderfarm"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by kysg on 2013-02-18
Hello, at work we considering to linux for render farm, we are currently just set up to use maya and vray for render farm.  I was wondering how I could pull this off with ubuntu?

thanks

---

### Post by kysg on 2013-02-22
I know it has been asked before,

but I'm trying to just get 2011 or 2012 on my desktop.  I got a laptop with 2013 and need to have the other machine for rendering.

Tried ubuntu and tried to convert the .rpm's to .deb and wasn't successful in getting it to work.  

I tired fedora and that didn't work...

I seriously am about to give up on this.  I got houdini working, and nuke working but can't get maya working I just don't think I can do it.  I may just have to swallow this one and spend 100 bucks on windows.

---

### Post by QIII on 2013-02-22
*Threads** merged.***

Hello and welcome to the forums.  I've merged your two threads.  It is best not to create threads with the same general subject, as it dilutes the community's efforts to provide help and makes things confusing.

This is for Precise, but you might find something in a similar vein if you are using a different version.  Remember that I cannot guarantee its applicability and you will be using it *at your own risk.*  It would be wise to do some research.

[https://gist.github.com/heiths/3250500](https://gist.github.com/heiths/3250500)

This was provided as a possible answer on [AskUbuntu](http://askubuntu.com/questions/248208/how-to-install-autodesk-maya-2013-on-ubuntu-12-10).



Good luck with this!

---

### Post by thermion on 2013-02-22
Don't use ubuntu at all if you want to use Autodesk Maya (or any other autodesk product with linux support). Autodesk only provides rpm packages and they only support RHEL, Suse and CentOS. In case you have a valid Autodesk Subscription, support will refuse to help you if run any other system that is not supported by Autodesk.

PS: Converting the packages to .deb with alien (might) no longer work. Maya (and any other Autodesk Product for Linux) is now made up of many different packages (backburner, stone+wire, wiretap, etc...). So you would have to convert these packages too and all of their dependencies. Since most Autodesk Products only work on RHEL and CentOS, the needed dependencies are mostly out-dated packages in most other distributions.

---

