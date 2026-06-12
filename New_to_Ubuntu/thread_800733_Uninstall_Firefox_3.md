---
title: "Uninstall Firefox 3"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by scotcella on 2008-05-20
Hi,e.

I installed the latest version of Ubuntu today- yay!

I am amazed to discover some changes, and practically everything works out of the box. Just need to customise some things to my personal taste and what not and fiddle with bluetooth.

Now.. my question is (been doing some thread search but couldn't find anything relevant) how do i uninstall the latest Firefox and downgrade it to the more stable 2.0 version.

I am aware that I can't have any add ons while Firefox 3 is in beta stage.

Thanks in advance.

---

### Post by hyper_ch on 2008-05-20
you can have the addons with firefox while it's in beta stage...

---

### Post by scotcella on 2008-05-20
Okay,

most add-ons require an older version of firefox hence my difficulty to finding the add ons that i want to use.

---

### Post by alienexplorers on 2008-05-20
Yes, but only add-ons that are written for 3.0 beta.  I know you can force others to run, but that has caused me problems.

---

### Post by hyper_ch on 2008-05-20
install the nightly test tools add-on and it will remove that "version compatibility issue"... most addons just run and are only prevented by the versioning in their files.

---

### Post by scotcella on 2008-05-20
Hyper thank you..

But still doesn't really answer my question, how to uninstall and put in an older version of firefox.

---

### Post by Ryadt on 2008-05-20
hi..go in synaptic and mark firefox3 for complete removal..then go in your home directory and delete the .mozilla directory( its hidden)..
you can then install firefox2 from synaptic..

---

### Post by PmDematagoda on 2008-05-20
> **scotcella said:**
> Hyper thank you..

But still doesn't really answer my question, how to uninstall and put in an older version of firefox.

While Fx 3 is better than Fx 2 is, you can remove Firefox 3 with:-
```
sudo apt-get remove --purge firefox
```
and install Firefox 2 with:-
```
sudo apt-get install firefox-2
```

---

### Post by kdx on 2008-05-20
Edit: Nevermind

---

### Post by aeshanw on 2008-07-02
Hi guys,
My firefox3 was working fine till I updated just a few days back and now:
[LIST]
[*]My back/forward icons have dissappeared
[*]My Firefox keeps crashing when 3+ tabs are in use
[/LIST]

I've tried re-installing but problem still remains.
Any tips?
Cheers!

---

### Post by Paraphysicist on 2008-07-03
[http://www.ubuntux.org/how-to-downgrade-to-firefox-2-in-ubuntu-hardy](http://www.ubuntux.org/how-to-downgrade-to-firefox-2-in-ubuntu-hardy)

---

