---
title: "xorg"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Jookia on 2008-04-25
While I was upgrading to 8.04, I had loads of xorg errors from the alt CD, now I'm on the live CD since X won't boot on my HDD.

How can I fix this?

---

### Post by Saya on 2008-04-25
Can you access a console? If so, try ```
sudo dpkg --configure -a
```

---

### Post by Jookia on 2008-04-25
I tried that, it got me errors from the Xorg thing, it's damaged beyond CONFIG. I think it damaged the actualy program.

---

### Post by PmDematagoda on 2008-04-25
Do:-
```
sudo apt-get remove --purge xserver-xorg-core && sudo apt-get install xserver-xorg-core
```
to see if you can reinstall it, post any errors you get if any.

---

### Post by Jookia on 2008-04-25
Will that work in the root recovery console?

---

### Post by aeiah on 2008-04-25
> **Jookia said:**
> Will that work in the root recovery console?

yes, although since sudo (kind of) means 'super user do', you dont need to put the two 'sudo's in your command, just ```
apt-get remove --purge xserver-xorg-core && apt-get install xserver-xorg-core
```


sudo is a command that asks for temporary root control, which you already have in your root console

---

### Post by Jookia on 2008-04-25
none of it works, it chucks ******** about dependancies and asks for a cdrom which I don't seem to have. I'm running apt-get update right now. It's going SLLLLOOOOOWWW, as usual for when a new release comes out.

---

### Post by PmDematagoda on 2008-04-25
Post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by Jookia on 2008-04-25
I can't it's on my other PC. I could take a pic if you want me to.

---

### Post by PmDematagoda on 2008-04-25
> **Jookia said:**
> I can't it's on my other PC. I could take a pic if you want me to.

A picture won't be necessary. just run:-
```
sudo nano /etc/apt/sources.list
```
and then add # to the front of the "deb cdrom:" line, save the file and then run:-
```
sudo apt-get update
```

After that is done try reinstalling Xorg again.

---

### Post by Jookia on 2008-04-25
Thanks. That's downloading nicely.

---

### Post by Jookia on 2008-04-25
It didn;t do anything at all. I still get dependancy problems. If macgyver can fix this, I have these things:

Computer
Mother's laptop
Mother's phone w/ camera which can transfer pics to PC
1GB usb Drive
Ubuntu 7.10 Live CD
internet on both computers

---

### Post by PmDematagoda on 2008-04-25
Boot Ubuntu in Recovery Mode and then execute:-
```
sudo xfix
```

After that is done, execute:-
```
sudo startx
```

See if that allows you to start the X-Server properly.

---

### Post by Jookia on 2008-04-25
I have one CD drive. I'm on Live CD right now. I need to burn the 8.04 cd.
Upgraded from alternative mounted cd broke 7.10 on HDD, recovering data onto flash drive using Live CD, now up to this problem.

---

### Post by PmDematagoda on 2008-04-25
> **Jookia said:**
> I have one CD drive. I'm on Live CD right now. I need to burn the 8.04 cd.
Upgraded from alternative mounted cd broke 7.10 on HDD, recovering data onto flash drive using Live CD, now up to this problem.

Did you try the commands I provided? There still might be a chance to try and fix the problems.

---

### Post by Jookia on 2008-04-25
I've tried them all. It's gone.

---

### Post by PmDematagoda on 2008-04-25
> **Jookia said:**
> I've tried them all. It's gone.

That's a pity, we could have kept going but in any case with all the effort that has already been put into fixing the issue, perhaps you would be better off doing a clean reinstall(which is what you are doing).

---

### Post by Jookia on 2008-04-25
In this situation, it's the same as fixing a broken leg with band aids. Any ideas on how to burn the alt CD?

---

### Post by PmDematagoda on 2008-04-25
> **Jookia said:**
> In this situation, it's the same as fixing a broken leg with band aids. Any ideas on how to burn the alt CD?

Install the "burn" package using:-
```
sudo apt-get install burn
```

The burn package contains tools that include burning an ISO image, so you can use that. You can learn about using burn using:-
```
man burn
```

---

### Post by Jookia on 2008-04-25
But in order to burn, I have to take the live CD out.

```
The following packages have unmet dependencies:
burn: Depends: cdrecord (>= 4:2.01+01a01-2) but it is not installable
Depends: mkisofs (>= 4:2.01+01a01-2) but it is not installable
```

---

### Post by Jookia on 2008-04-25
I've had this idea SINCE I got the error: Could I somehow copy the xorg from liveCD to HDD

---

### Post by PmDematagoda on 2008-04-25
> **Jookia said:**
> But in order to burn, I have to take the live CD out.

```
The following packages have unmet dependencies:
burn: Depends: cdrecord (>= 4:2.01+01a01-2) but it is not installable
Depends: mkisofs (>= 4:2.01+01a01-2) but it is not installable
```

Why don't you try using the normal Ubuntu installation? Also, I believe the error you are receiving is because the Ubuntu servers are under quite a bit of pressure, so you may want to try installing the package again by executing:-
```
sudo apt-get update
```
at regular intervals.

---

### Post by Jookia on 2008-04-25
At really hacky methods, I deleted 8.04's corrupted Xorg and reverted it back to.. 7.10's default Xorg.

[img]http://img164.imageshack.us/img164/1183/screenshotsynapticso7.png[/img]

---

### Post by Jookia on 2008-04-25
Any ideas?

---

### Post by PmDematagoda on 2008-04-25
> **Jookia said:**
> At really hacky methods, I deleted 8.04's corrupted Xorg and reverted it back to.. 7.10's default Xorg.

[img]http://img164.imageshack.us/img164/1183/screenshotsynapticso7.png[/img]

So you actually got the Ubuntu 7.10 X-Server running properly? But do not think that the problems are solved, downgrading the X-Server has a good chance of creating more problems related to dependencies or functionality instead of solving them.

---

### Post by Jookia on 2008-04-25
I have it running, so I can copy and paste now. How would I perhaps fix this 'broken' problem?

---

### Post by PmDematagoda on 2008-04-25
> **Jookia said:**
> I have it running, so I can copy and paste now. How would I perhaps fix this 'broken' problem?

You would have to edit the files that contain the dependencies for the X-Server, but trust me, it will be hard.

---

### Post by Jookia on 2008-04-25
If you can explain and/or need me to run commands, I'll do it.

Edit: Also if it helps, my nvidia-glx-new package is corrupted.

---

### Post by PmDematagoda on 2008-04-25
> **Jookia said:**
> If you can explain and/or need me to run commands, I'll do it.

I don't think there are any commands, and I can't really explain what files are to be edited and how since you need to know the dependencies and what exact version they depend on.

In your case, a clean reinstall would be the best thing to do.

---

### Post by Jookia on 2008-04-25
Okay. Thanks.

---

