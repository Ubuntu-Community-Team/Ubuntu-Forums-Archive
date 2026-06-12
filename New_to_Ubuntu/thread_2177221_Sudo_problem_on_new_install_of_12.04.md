---
title: "Sudo problem on new install of 12.04"
date: 2013-09-27
forum: New to Ubuntu
---

### Post by mark allyn on 2013-09-27
Hello everyone,

I just installed 12.04 on an external hard drive.  I'm booting off a system with Windows XP on the internal hard drive.  The installation appeared to go smoothly, and when I boot off the external drive Ubuntu shows up nice and shiny.

But, something is haywire with my password.  The system logs me in without a problem when I use the password I thought I had assigned.  However, I can't seem to do anything much in my HOME directory without prefixing with "sudo".  For example, if I try to compile a C program, it will require me to prefix with my password.  It doesn't have to be anything as fancy as compiling; if I just try to cp a file, I'm refsed permission until I prefix with "sudo".  

Moreover, if I type "su"  <cr> and type in the password, ubuntu tells me that the password can't be authenticated.  

I've not had these problems in the past.  Can someone point out the folly of my ways?

Thanks,
Mark Allyn

---

### Post by Impavidus on 2013-09-27
Have you checked who is the owner of the files in your home directory and what are the permissions? Also for your home directory itself.

su will swith user to root, but you need a root password for that. sudo -i is equivalent.

---

### Post by mark allyn on 2013-09-28
Good morning, Imavidus,

Thanks for the tip.  Yes, I checked the ownership following your advice.  The files I had created (mkdir) in my home directory immediately following the install were owned by "root" not by user "mark".  I changed ownership (chown) to "mark" and they now behave as they "should"--or as I expected they would, to put the thing more accurately.

I don't understand the behavior of the su command, however.  Could you give further details?

Thanks,
Mark Allyn

---

### Post by Impavidus on 2013-09-28
Ubuntu doesn't have a root password by default, the root login geing disabled. It uses sudo instead, which is considered more secure. Therefore the command **su** doesn't work. To get a root shell, you can use **sudo -i**. Read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more details.

---

### Post by whitesmith on 2013-09-28
To build on the previous suggestion, if you absolutely, positively, must work as su--do this:```
sudo su
``` and you will magically become su, but my sig line doesn't lie!

---

### Post by coffeecat on 2013-09-28
> **whitesmith said:**
> ```
sudo su
```

Please see the RootSudo link that impavidus posted to see why sudo -i is much to be preferred over sudo su or sudo -s if one "absolutely, positively, must" invoke a root shell. 

But I agree with you about the absolutely, positively, must bit. :) Absolutely, positively, must is rare in my experience.

---

### Post by mark allyn on 2013-09-28
Hello everyone,

It seems to me that I recall dimly that I was able to use su in changing to a different user.  Some time ago I added a second user to my system ("Dave") and I think I could switch to Dave from Mark by doing something like su -s -u dave.  

Does that make sense?  Maybe my memory is just lousy.

Cheers,
Mark

BTW, thanks to all of you for helping me out with this thread.  I finally realized what had caused the problem.  Namely, I had issued this command from my home directory:

sudo mkdir newdir

So, the permissions were messed up.  I have no excuse for using sudo in this context.

---

### Post by Jonathan Precise on 2013-09-28
I think it's:

```
su **user-name**
```

to run the commands as that user. However, running a graphical application under su always brings this up:

```
Warning! Can not open display:
```

---

### Post by mark allyn on 2013-09-28
Hi Jonathan Precise,

Yes.  You need to set the environmental DISPLAY=.0 variable and the user must have xauthority.

Mark

---

