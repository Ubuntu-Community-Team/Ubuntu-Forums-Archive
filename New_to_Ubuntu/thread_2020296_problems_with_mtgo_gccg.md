---
title: "problems with mtgo gccg"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by nevilshute on 2012-07-08
Hey,

So just finished upgrading to ubuntu 11.10 and am trying to run MTGO. Following this guide [http://gccg.sourceforge.net/](http://gccg.sourceforge.net/) I can get the program to run. But when the MTGO window opens it immediately issues a 'Bad mode' statement. It says in the top "right click for menu'. When I do so, however, I get this error message in my terminal:
> 
Code caused exception:
{MenuByContext();}

LangErr exception at net_isopen(const Data& ): Invalid argument NULL for function net_isopen()

Stacktrace:
[ 0. ] net_isopen(NULL)
[ 1. ] ConstructMenu("Main Menu - ")
[ 2. ] MenuByContext(NULL)
Does anyone know what do to from here? I'm a bit of a newbie when it comes to ubuntu.

---

