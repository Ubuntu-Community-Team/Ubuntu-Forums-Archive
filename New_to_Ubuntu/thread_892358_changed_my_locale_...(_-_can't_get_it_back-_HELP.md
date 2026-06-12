---
title: "changed my locale ...:( - can't get it back- HELP"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by lanchongzi on 2008-08-17
My problem is as follows
I installed Ubuntu using Hongkong locale - so I can use chinese input with scim without all that trouble.
well didn't work after all, so i installed UIM which worked but its chinese is really strange and not nice too use at all.
so last week i came across sth in the net talking about fcitx ( always wanted to try that ), 
first step was to change the locale into english by doing that: 
 sudo gedit ~/.fcitx/config
                 then change it to this
                 PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
         LANGUAGE="en_US:en"
                 LANG="en_US.UTF-8"
                 LC_CTYPE=zh_CN.UTF-8

i did that.
now my Ubuntu system cant open my chinese Texts and data anymore, it says "doesn't exist".

how can i change my locale back
or   change the english locale so that i can still use my chinese data
plus chinese input

:confused:

P.S.   sorry for the long blahblah


Thanks

---

### Post by Pro-reason on 2008-08-17
There are two issues here.  One is about how your system is set up for languages.  The other, more serious issue is that you seem to be indicating that your files have been deleted.  Could you please elaborate on that?  What exactly do you try to do, and what exactly is the result?

---

### Post by lanchongzi on 2008-08-17
I am embarrased to say that it is just me being too -unclever- sometimes, especially when something doesn't work.
well the file was not deleted, it was still there, after renaming the file to latin characters I&#12288;&#65347;&#65359;&#65365;&#65356;&#65348;&#12288;&#65359;&#65360;&#65349;&#65358;&#12288;&#65364;&#65352;&#65349;&#65357;&#12288;&#65345;&#65351;&#65345;&#65353;&#65358;( name was in chinese characters ) 
so, after turning on my brain i simply set the language within the controll center.
installed scim again and wabamm it works exactly the way it should

again i feel quite stupid right now for wasting your time on that.

anyways many thanks for your concern

---

