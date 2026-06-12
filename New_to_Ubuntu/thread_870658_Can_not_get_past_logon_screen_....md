---
title: "Can not get past logon screen ..."
date: 2008-07-26
forum: New to Ubuntu
---

### Post by jbenuntu on 2008-07-26
Hello, tried to download ISO for Ubuntu, can not get past log on screen. Tried downloading Wubi as well; again can not get past log on screen. Ordered and have received Ubuntu 8.04 LTS Desktop Edition; STILL CAN NOT GET PAST LOG ON SCREEN. I do not have, nor in the installation did it prompt for a username and password. .....???????????
:confused::confused::mad::mad::twisted::shock::?::x

system: Microsoft Windows XP
Home Edition
Version 2002
Service Pack 2
machine:
eMachines
T6212
AMD Athlon(tm)64 Processor
3200+
1.99 GHz, 384 MB of Ram

---

### Post by Dark_Stang on 2008-07-26
Whenever you install ubuntu you are required to setup a username and password.

---

### Post by hogwartsnigel on 2008-07-26
Do you mean you are receiving the logon screen during install? Try root root if you are receiving this opening a live cd.
Or are you encountering problems after install on your first login?
If so is it just hanging or giving an error message?
Did the live cd run ok?
Did you check disc contents?

Happy to help

Nigel

---

### Post by jbenuntu on 2008-07-26
cd is from canonical itself. i did not install ubuntu, i selected the option to "Try Ubuntu without installing", so i was NOT prompted to select a user name and password...i sat and watched the program run, all the way to the login screen. nowhere did it ask me for a username and password.

---

### Post by stevoo on 2008-07-26
try 
root 
root 

for username and pass ...

---

### Post by louieb on 2008-07-26
> **jbenuntu said:**
> ...selected the option to "Try Ubuntu without installing",...watched the program run, all the way to the login screen. 

So you booted with the live CD. and it runs and finally displays the login screen? Right?

If that is what happened there is something wrong. Booting to the live CD should not give you a login screen.

Either you have a bad CD. Run the **check media for defects** option.

Another common reason is not enough memory. How much memory does this PC have? (Just noticed 384MB should be  enough for the Live CD)

A 3rd reason is hardware detection gone bad. sometimes you have to use **boot options **for the live CD to run properly. [BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")
Good Luck.

---

### Post by hogwartsnigel on 2008-07-27
I have only experienced what your describing when trying to install Ubuntu 7.1 on a really old lap top that only had 128mb of ram and a really low graphics capability. I agree with louieb it sounds like a hardware issue, have you tried to install in safe graphics mode..sometimes this can give insight as it shows on the terminal any errors that arise.
I know on some installs of other flavours of Linux you are asked for a login and typing root for both user and password is needed but I have never had to do this with Ubuntu.

I am at a loss and will be watching others helping you.

Good Luck
Nigel

P.S. You could try downloading and installing Ubuntu Lite, to get a basic install and upping its content if succesful but you shouldn't have to do tis.

---

### Post by ckomurlu on 2008-11-26
Hi,
   The problem seems not to be solved. I suffer from the same problem. I boot the Ubuntu 8.04.1 iso CD, then select the "Try ubuntu without installing". In the end, it stops at a login screen asking me a username and password. I check the integrity of the CD, receive an error at a file that the name is not given.
   I tried the same CD on a different machine, it booted normally to a live desktop with a live session user. And I checked the integrity of the CD, it reported that everything is fine. I repeated the same procedure on virtualbox, no problem.
   Finally, I tried to create a bootable USB disk using this CD. Exactly the same thing happened. Recently I tried booting Intrepid via CD. Same case. It doesn't work on that machine but works on other computers and on virtualbox.
   Apparently, the problem is due to the hardware. It's an industrial computer manufactured by Advantech. The mainboard is AIMB 252, the CPU is Celeron 1GHz (So 32 bit), the RAM size is 1GB.
   It seems to be a specific case, for only that hardware, but it is not. There are many threads reporting this issue.

Any idea is highly appreciated.
Thanks in advance

---

### Post by scottmac112 on 2008-11-26
Are you wanting to install it? Or just use the Live CD? If you're just wanting to install it, you can try the Alternate Install CD.

---

### Post by ckomurlu on 2008-11-26
> **scottmac112 said:**
> Are you wanting to install it? Or just use the Live CD? If you're just wanting to install it, you can try the Alternate Install CD.

Thanks, for the advice
In the end, I want it installed. I've already tried Intrepid's alternate installer. It worked. But the problem is that I can't boot it in live session. Indeed, I have a modified CD sent by Advantech. It boots in live session and can be installed on that session. Unfortunately I don't have its alternate installer version. Advantech's people said that they had optimized some packages for this hardware, I don't think that they are related to installation or booting the live session. In addition, this CD behaves exactly the same as Intrepid's official desktop installer in booting. I mean, both of them get stuck in login screen on that machine and both work on other PC's.

Regards

---

