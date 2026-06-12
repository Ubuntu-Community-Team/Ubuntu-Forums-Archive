---
title: "root access"
date: 2013-03-22
forum: New to Ubuntu
---

### Post by Otsenior on 2013-03-22
I have just installed Ubuntu 12.10 and I need to edit a root protected file and when I su and enter the password that I setup at the installation I get an authentication failure Why? what am I doing wrong

---

### Post by steeldriver on 2013-03-22
You should be using 'sudo'

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by deadflowr on 2013-03-22
Just run
```
gksudo gedit path-to-file
```

or if terminal savvy
```
sudo nano same-path-to-file
```

---

### Post by ManamiVixen on 2013-03-22
Canonical reserves "su" and only they have the password. So you have to use sudo.

---

### Post by nothingspecial on 2013-03-22
> **ManamiVixen said:**
> Canonical reserves "su" and only they have the password. So you have to use sudo.

That is misleading.

Ubuntu ships with the root account disabled because it is unecessary if sudo is available.

---

### Post by deadflowr on 2013-03-22
> **ManamiVixen said:**
> Canonical reserves "su" and only they have the password. So you have to use sudo.

Nobody is stopping you from setting a root password.

It's just that sudo does the job just as well.
So the need is moot.

---

### Post by ManamiVixen on 2013-03-22
Huh, I didn't know root was disabled. I read Canonical reserved root with a custom long complex password so as to deture hacking the OS and to keep the user safer. Thanks for correcting me! :)

---

### Post by oldos2er on 2013-03-22
> **ManamiVixen said:**
> Canonical reserves "su" and only they have the password. So you have to use sudo.

I can't imagine the hue and cry that would result if people thought Canonical was somehow keeping passwords; needless to say they do not.

---

### Post by haqking on 2013-03-22
> **ManamiVixen said:**
> Canonical reserves "su" and only they have the password. So you have to use sudo.

That is the funniest thing I have read for weeks, and there is always something in this forum that makes me laugh.

Thanks ;-)

:lolflag:

---

### Post by ManamiVixen on 2013-03-22
Ok, I pull by my thanks and call you jerks now. I told you it was what I read somewhere and didn't know it was wrong yet you rub it in and laugh even though the reason I why I believed it was a good, valid one.

---

### Post by squakie on 2013-03-22
They have the root account "disabled" as already mentioned by the password so that idiots like me or just newbies don't go logging in as root and messing up their systems.  It can be enabled, but I don't think we are allowed to talk about that here, only point you to were it might be posted.  BUT, as has already been mentioned, you really shouldn't need to login as root anyway.  All the access you need can be accessed by "sudo" (for command line) or "gksudo" (for command line access to graphical apps - like an editor, etc.).  Way back when I jumped the gun on root (I had prior experience with Unix) and messed some things up - so stick with sudo or gksudo. ;)

---

### Post by haqking on 2013-03-22
> **ManamiVixen said:**
> Ok, I pull by my thanks and call you jerks now. I told you it was what I read somewhere and didn't know it was wrong yet you rub it in and laugh even though the reason I why I believed it was a good, valid one.

you need a thicker skin for these forums ;-)

Peace

---

### Post by squakie on 2013-03-22
> **ManamiVixen said:**
> Ok, I pull by my thanks and call you jerks now. I told you it was what I read somewhere and didn't know it was wrong yet you rub it in and laugh even though the reason I why I believed it was a good, valid one.Please don't be offended!  We really are here just to try and help - we've all been there!

---

### Post by haqking on 2013-03-22
> **squakie said:**
> Please don't be offended!  We really are here just to try and help - we've all been there!

Indeed, it's all good fun ;-)

---

### Post by ManamiVixen on 2013-03-22
Alright sorry... I can be prude at times. We're all friends here! :)

---

### Post by QIII on 2013-03-22
Well, ManamiVixen, we were going to close the thread temporarily for staff review (well, we were watching it already), but if you're OK with it we can leave it go.

Most of the posts were simple, straightforward corrections of a misconception.  A couple of posts were a bit *too* humorous -- so everyone please take into account that written text on a forum is not as subtle as tone of voice.

Thanks.

---

### Post by ManamiVixen on 2013-03-22
Thank you and welcome.

---

