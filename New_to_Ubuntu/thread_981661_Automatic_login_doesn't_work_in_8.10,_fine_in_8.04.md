---
title: "Automatic login doesn't work in 8.10, fine in 8.04"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by AncientPC on 2008-11-13
I have Login > Security > Enable Automatic Login > my profile.  However this doesn't work in 8.10, I still get prompted for my user / password upon bootup.

---

### Post by Vadi on 2008-11-14
Did you select the proper user to logon as and everything?

---

### Post by AncientPC on 2008-11-14
Yup, the odd thing is it works about half the time without changing any settings . . .

---

### Post by art_erickson on 2008-12-07
Say Ancient,

Did you ever solve this?  I have the same problem and was hoping for an easy fix :)

---

### Post by AncientPC on 2008-12-07
Unfortunately not.  It happens sporadically and I've just learned to deal with it. :(

---

### Post by art_erickson on 2008-12-08
I did some searching but I'm not smart enuf to know what I read.  This has some entertaining, but not very informative, comments.
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/236264](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/236264)

This one also mentioned keyring with an alleged work-around but now it doesn't load so I can read it again.  I've been trying for a couple of hours but it just times out.
[http://www.ubuntu-tutorials.com/2008/07/09/enable-timed-or-automatic-login-on-ubuntu-804/](http://www.ubuntu-tutorials.com/2008/07/09/enable-timed-or-automatic-login-on-ubuntu-804/)

In my case it doesn't seem to work but I suspect it does.  That is, I think it logs me into gdm but another app (network manager?) doesn't want to play.

I have disabled remote login ability to the best of my knowledge and physical security of the machine is not an issue so I just wanted to make life a little easier.  Alas, that is not in the unix playbook.

---

### Post by art_erickson on 2008-12-08
I got thru to the second site and it did suggest deleting the default keyring and entering a blank one.

I could not find a gui for this so I renamed the login.keyring file at ~/.gnome2/keyrings.  No change - the file was just recreated.

I have read in the past how text config files were so much more flexible than Win but this issue doesn't support that.  It's just a different group of people pulling the strings.

---

### Post by deepone on 2008-12-10
FYI, I have this problem as well... Automatic login works sometimes, but not all the time... I don't have time to dig into this myself now, I was kinda hoping to not have this kind of problems with Ubuntu now... I recently made my first serious install of Linux in many years...

---

### Post by art_erickson on 2008-12-10
Dee,

I hope you don't use Skype.

---

