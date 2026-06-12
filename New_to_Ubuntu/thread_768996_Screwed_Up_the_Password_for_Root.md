---
title: "Screwed Up the Password for Root"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by droppedonjapan on 2008-04-26
I know, I know.  I've done the thing that isn't ever supposed to be done here.  I just installed Ubuntu (which, by the way, the new version's installer was amazing), and I went about trying to figure out if the username that I made was a regular user, or a super user.  

That being said, I think that I may have changed my password for root, and I'm not quite sure what it is.  Now, I remember what it was supposed to be, however somehow it may have recorded something different (possibly a bad keystroke in both fields for the password).  So here comes my questions.

First off, does Ubuntu use a generic password for root?  I may have just ended up changing my username instead of root's for some reason, and if so, I can just change the pass through root.

If there isn't, or I did end up changing the password for root, is there any way to get it back?  I know that there shouldn't be, seeing as the root user's stuff isn't supposed to be easily changed, but if there's a way, I'd kind of like to know it.

And if the inevitable did happen, could you outline the uninstillation of Ubuntu so that I can reinstall it again (Ubuntu currently is on a 20 gig unused partition of my hard drive).  I REALLY wouldn't want my other partition (Windows XP) to be lost, mostly because that's where I have all my media at the moment.  I also worry that if I just go through windows and reformat my Ubuntu partition, it will mess up the first track of the hard drive, and then not be able to start up anything.  So, that being said, any suggestions?

(Thanks for the help, by the way.  It's really appreciated.  :biggrin:)

---

### Post by tamoneya on 2008-04-26
ubuntu does not allow you to login as root until you set the root password.  Since it seems like you currently have no passwords for admin users what you should do is boot into recovery mode.  When grub loads hit escape and select recovery.  This will launch a command line interface.  From here you can reset the necessary passwords since you have root permissions at this point.
```
passwd username
```

---

### Post by Michael.Godawski on 2008-04-26
I have gathered some info in this article about loosing the root passowrd.
(scroll down a bit)

[http://godawski.piranho.de/linuxsecurity.html](http://godawski.piranho.de/linuxsecurity.html)

---

### Post by droppedonjapan on 2008-04-26
Awesome.  My only question for you is this.  What is GRUB?  Are you talking about the part in the beginning when it asks you to hit escape if you want to access the menu?

---

### Post by Nesman on 2008-04-26
Yup.  That's GRUB.  GRUB is the program that tells your computer where to find your operating system(s) and gives you a choice between them if you dual boot.  It's a boot manager.

---

### Post by Michael.Godawski on 2008-04-26
Yes. It is the entry during booting.

Grub Loading stage 1.5 something something
and you have two seconds or so to hit escape.

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by droppedonjapan on 2008-04-26
Alright, I took the jump, and it worked.  Now I have that issue set up.  Now to figure out how to install programs.  :P

But in all seriousness, thanks for the (very) quick replies.

---

### Post by tamoneya on 2008-04-26
installing programs is even easier than windows once you get used to it since they are all in repositories(any common program at least).  To install VLC you would just go like this```
sudo apt-get install vlc
```

---

### Post by akiratheoni on 2008-04-26
> **droppedonjapan said:**
> Awesome.  My only question for you is this.  What is GRUB?  Are you talking about the part in the beginning when it asks you to hit escape if you want to access the menu?

Yes.

Ahh!! I'm late. Sorry.

---

### Post by Michael.Godawski on 2008-04-26
Great to hear you have solved it.

For installing new applications check out these sites:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

