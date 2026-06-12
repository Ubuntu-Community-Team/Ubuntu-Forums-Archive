---
title: "what is all this sudo crap and how do i use this thing"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by blake7 on 2008-09-30
and how do i use this thing with out having to use sudo this  sudo  that

---

### Post by seshomaru samma on 2008-09-30
read about [sudo ]("http://en.wikipedia.org/wiki/Sudo")
it's quite possible to use ubuntu without needing it . if all your hardware is recognised at installation , you probably wouldn't need to use it. if you are following some guide on the internet that would require it then just do what the guide says .sudo command will ask you for a password (your password) and you will not see anything on the screen when you enter the password

---

### Post by lisati on 2008-09-30
Once you've got your system working to your satisfaction, it is possible to use it without having to resort to sudo.

---

### Post by zxscooby on 2008-09-30
sudo is what keeps people from hacking you.
You could log in as super user or run a root session, but then
you would loose a lot of the security features.

---

### Post by wilsong on 2008-09-30
I am going to put this in terms of someone that doesn't use Linux much, (not to insult your intelligence but to try to give you an idea and why things are like this) 

If you have used Windows Vista EVER, you have probably noticed the new feature where the screen goes black, anytime you try to install a program and ask for your password.  This is the new "UAC" User Account Control.  

Linux does what you tell it to, Windows does what it thinks you want it to do, before there was this UAC for windows, Linux had a root (admin account) and users. Most users would log in as root only, causing security risk.  Most people using Windows XP log in as their admin user, causing security risk.  

This is a major reason for sudo, it ask " Super user, DO! " and does a command with SUPER USER authority! 

It has been a part of ubuntu since ubuntu is for linux lovers novice and expert.   Its great for security!  

You can disable it, but you would still have to switch to super user mode, and then run whatever you needed to (unless you logged in as root all the time which is really unsafe because like i said linux listens to you if you typed a command like

 " I removed this command.. it is a RM (remove directory command  " but if you want to read more about it and why i cant type it view this [http://ubuntuforums.org/announcement.php?a=54](http://ubuntuforums.org/announcement.php?a=54)  it tells you what the command is and why its bad. but i was trying to make a point of how linux will listen to you if you say to do something... thats why there is sudo 

 which says remove recursively without asking all the files mounted on the hard drive. Linux would go right ahead and do it! because super user said so, windows would say "are you sure you want to do that. and then stop you and say I cant do this because i need this to run, linux... doesnt do that it wont ask, it does what super user says... so when you type SUDO just know your giving linux the power to DO!

---

### Post by Elfy on 2008-09-30
@wilsong - it might be better to remove the command from that post :)

---

### Post by muteXe on 2008-09-30
> **blake7 said:**
> and how do i use this thing with out having to use sudo this  sudo  that

How can you have posted on here 120 times and not know about sudo?  Are you taking the piss mate?

---

### Post by lisati on 2008-09-30
> **muteXe said:**
> How can you have posted on here 120 times and not know about sudo?  Are you taking the piss mate?

See [this thread]("http://ubuntuforums.org/showthread.php?t=934038")

---

### Post by muteXe on 2008-09-30
Ah :)

---

### Post by hyper_ch on 2008-09-30
blake:

I think you're better off with Windows with that attitude of yours that you show.

---

### Post by wilsong on 2008-09-30
> **hyper_ch said:**
> blake:

I think you're better off with Windows with that attitude of yours that you show.

haha, I dont care how awful someones attitude is, no one deserves windows... i guess sometimes its easier to just give up.. but thats no fun... 

but i agree he seems a little frustrated that theres all this unknown stuff heh

---

### Post by Idefix82 on 2008-09-30
> **hyper_ch said:**
> blake:

I think you're better off with Windows with that attitude of yours that you show.

Totally agree!

---

### Post by AgainstTheDarkArts on 2008-09-30
Possibly it's not an indication of attitude, but an indication of frustration.  Linux can be difficult, and overwhelming. A dozen years ago, it was enough to make most users say "neat, but I'll take plug-and-play."

The current loads are great, and users who do not know the details of program interaction or OS architecture can still use the desktop loads quite happily... except that they have to type their password all of the time.

But, like always, education is the key.

To the OP, I would simply say this:

You do not have to worry about viruses, spyware, or malware in Linux, but as a tradeoff, you have to type your password a lot.

To me, I like the trade-off. 

When something goes wrong with Linux, I don't think "rats, another virus got me," and I diagnose the problem from another angle.  In Windows, I always check to see who has been messing with my system before I diagnose other problems.

The peace of mind is more than worth the repeated typing of my password.  I hope you feel the same.

---

