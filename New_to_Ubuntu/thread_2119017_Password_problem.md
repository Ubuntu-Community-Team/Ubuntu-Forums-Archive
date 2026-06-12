---
title: "Password problem"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by igormo2013 on 2013-02-22
I am a real beginner.

I D'not assign password to turn and see first start my new laptop.

To install or uninstall any new program asking for password.

How I can retrieve or assign a new password.

:D

---

### Post by Impavidus on 2013-02-22
To change your password:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by oldos2er on 2013-02-22
Did you actually install Ubuntu (which version?) onto your laptop, or are you running it from DVD or USB?

---

### Post by igormo2013 on 2013-02-24
Thank you.

I held the shift key pressed and it did not work. Do not go into recovery mode.

Besides, I do all the steps in the help to assign a new password, from cd.

Please any other suggestions?

---

### Post by igormo2013 on 2013-02-24
Thanks

The laptop is an ASUS A45V, Core i5, 4 GB RAM, 750 GB HDD, bought a week ago.

Latest version of Ubuntu

We try to do as described in the help to do it from a CD, just did not work.

Any other suggestions?

---

### Post by gordintoronto on 2013-02-28
If you are running from CD, you should be able to install a program, but as soon as you reboot, it is gone. If you don't want to alter your hard drive, install Ubuntu onto a flash drive, 8 GB is big enough to play around.

---

### Post by jackclarck on 2013-03-04
you should have to reset your password, by using control panel settings. once you reset your password then its easy for you to provide it wherever it is required.

---

### Post by POworker62 on 2013-03-04
I'm also having a problem with passwd and have used the link provided and tried to reset my passwd.  However, I am continously getting "authentication token manipulation error"  after I retype my passwd the 2nd time.

Can anyone help?  Yes, I'm a NUG.....


Thank you, thank you very much.

---

### Post by steeldriver on 2013-03-04
> **POworker62 said:**
> I am continously getting "authentication  token manipulation error"  after I retype my passwd the 2nd  time.

That particular error usually means you skipped this step:-

>  In recent versions of Ubuntu, the filesystem is mounted as read-only, so  you need to enter the follow command to get it to remount as  read-write, which will allow you to make changes: 

```
mount -o rw,remount /

```


---

### Post by POworker62 on 2013-03-04
Well I'm having just the worst of times with it as that command 

mount -o rw,remount /

will not work for me.  Maybe I'm not spacing it correctly.

---

### Post by POworker62 on 2013-03-04
Now I've figured it out... I was putting a space between rw, and remount.  It worked fine when I typed it correctly of course!  Duh!

Thanks for the help!
:popcorn:

---

