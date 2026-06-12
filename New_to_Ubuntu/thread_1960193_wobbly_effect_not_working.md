---
title: "wobbly effect not working"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by biju1256 on 2012-04-16
Hii,

I hv just installed compizConfig setting into my laptop(Dell with Intel Pentium). But wobbly effect is not working.. Pls help..

rgds,
biju

---

### Post by daslinkard on 2012-04-17
Here is a [tutorial]("http://www.howtoforge.com/enabling-compiz-fusion-on-ubuntu-11.10-oneiric-ocelot") for you pertaining to Compiz.  Good luck!

---

### Post by rectec794613 on 2012-04-17
Have you enabled it yet? Start CCSM and search for "wobbly", then click the checkbox beside "Wobbly Windows". NOTE: If you're running Unity, enabling this may crash Compiz. Usually it just makes Compiz restart, but make sure you're not working on anything important.

---

### Post by biju1256 on 2012-04-17
Hi,
I opened the CCSM, then clicked the checkbox besides Wobbly window, its not working.
But u had asked did i enable it? would u pls let me know how to enable it..

rgds,
Biju

---

### Post by daslinkard on 2012-04-17
When you selected the checkbox beside Wobbly that was you actually enabling the feature.  Where you prompted with a pop up of any kind once you selected/enabled Wobbly?

---

### Post by orange2k on 2012-04-17
Install CCSM, and install Ubuntu-Tweak, and in there you can set wobbly windows...

---

### Post by biju1256 on 2012-04-17
There was a POP UP.. But i exactly dont remember what it said... But once again i enabled it but there was no POP Msg this time..

---

### Post by biju1256 on 2012-04-17
Installed the latest version of Ubuntu Tweak. Enabled both Wobbly Windows and Wobbly Menus.
Both functions have no response...

---

### Post by mcduck on 2012-04-17
> **biju1256 said:**
> Installed the latest version of Ubuntu Tweak. Enabled both Wobbly Windows and Wobbly Menus.
Both functions have no response...

Make sure you are actually running Compiz in the first place. Open a terminal and run "compiz --replace", just to see if things work after that...

---

### Post by stinkeye on 2012-04-17
Are you logged into the **ubuntu** session and not being dropped back to the **ubuntu 2d** session.
In the terminal 
```
echo $DESKTOP_SESSION
```

---

### Post by biju1256 on 2012-04-17
> **mcduck said:**
> Make sure you are actually running Compiz in the first place. Open a terminal and run "compiz --replace", just to see if things work after that...

Done as said.. but the terminal got hanged.. I closed the terminal window but had the wobbly effect for sometime.
And restarted the system but the wobbly effect wasnt there any more.

I have Gnome Fallback session installed.

---

### Post by biju1256 on 2012-04-17
> **stinkeye said:**
> Are you logged into the **ubuntu** session and not being dropped back to the **ubuntu 2d** session.
In the terminal 
```
echo $DESKTOP_SESSION
```

I am logging in through gnome-classic.

---

### Post by zombifier25 on 2012-04-17
Did you enable Compiz? Since Compiz is not enabled by default in classic.
```
ps x | grep compiz
```
Then give the output.

---

### Post by mcduck on 2012-04-17
> **biju1256 said:**
> I am logging in through gnome-classic.

Yep, that would be the problem. Gnome-Classic doesn't use Compiz by default, you'll need to set it to start on login yourself.

---

### Post by biju1256 on 2012-04-17
> **zombifier25 said:**
> Did you enable Compiz? Since Compiz is not enabled by default in classic.
```
ps x | grep compiz
```
Then give the output.

pls find the details in the terminal... i am NOT so tech savy...

biju@ubuntu:~$ ps x | grep compiz
 2143 pts/0    S+     0:00 grep --color=auto compiz

---

### Post by biju1256 on 2012-04-18
Hi,

Not yet received any help...

---

### Post by zombifier25 on 2012-04-19
Run this:
```
compiz --replace & disown
```
to use Compiz on the classic session. Of course you have to this everytime you login, so may as well as add it to startup.

---

### Post by biju1256 on 2012-04-19
> **zombifier25 said:**
> Run this:
```
compiz --replace & disown
```
to use Compiz on the classic session. Of course you have to this everytime you login, so may as well as add it to startup.

Thank u.. its working.
But would u pls help me in placing this command in the the startup.
I mean to say that, pls tell me the steps for placing the said command in the startup. For which i shall be very thankfull.

---

### Post by biju1256 on 2012-04-20
pls help...

---

### Post by biju1256 on 2012-04-21
> **biju1256 said:**
> Thank u.. its working.
But would u pls help me in placing this command in the the startup.
I mean to say that, pls tell me the steps for placing the said command in the startup. For which i shall be very thankfull.

Hi,

Unable to set the command in the startup...

---

