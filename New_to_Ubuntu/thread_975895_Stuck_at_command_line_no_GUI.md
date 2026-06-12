---
title: "Stuck at command line no GUI"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Lakeside on 2008-11-08
Im on another comuter- one with missing keys lol- as mine is stuck at the command line- No GUI. I had rebooted the comuter, after taking advice to enter a few lines to fix my sound card issue- I had no sound. And now I am stuck. Searching this forum, I entered  first, sudo /etc/init.d/gdm start  but was told it was not a command..
then I entered  sudo dkg-reconfigure -*high xserver-org and was told there    was no xserver or x-org or whatever, it was not installed. The asterix was a letter this keyboard cant ty*e for some reason, like from *rincess, for exam*le lol *lease tell me what to do, I dont want to be in my teenagers room- its gross!! with this bad keyboard too long lol
thanks!

---

### Post by fooman on 2008-11-08
try to boot into recovery mode and choose the xfix option.

---

### Post by Lakeside on 2008-11-08
> **fooman said:**
> try to boot into recovery mode and choose the xfix option. I did see that, too, but I didnt know how you do that. I tried again just now (rebooted, went to safe mode, but information just flew by, there was no way of chosing the xfix o*tion (sorry, have missing keys  So how do I choose that
thanks again

---

### Post by handydan918 on 2008-11-08
> **Lakeside said:**
> I did see that, too, but I didnt know how you do that. I tried again just now (rebooted, went to safe mode, but information just flew by, there was no way of chosing the xfix o*tion (sorry, have missing keys  So how do I choose that
thanks again

From safe mode, ty*e xfix at the *rom*t


Sorry, couldn't resist the tem*tation.


:D

---

### Post by Lakeside on 2008-11-09
Ha ha..now I know why my daughter is so crabby- this com*uter is slooowww too- has Windows X* on it, lol.  I dont think I am in safe mode, I reboot, and only see 4 o*tions, I take the second one- for Recovery Mode 8.o.4 adn end u here  karen@bayside-deskto* ~$
and  sudo xfix or just xfix just gets me  xfix command not found.
I must have to get into the setu* to get safe mode, something like ctrl F1o, or F2. I did something like that to get into BIOS to change the boot drive, as installed from a boot disc. Ho*e to fix this tomorrow- its 2 am here :D

---

### Post by Crafty Kisses on 2008-11-09
Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X server:
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo shutdown -r now
```
Once you're in your GUI look for the proper drivers and install them and once you done that that should bring your system back to life, and you can get back to using Ubuntu. :D

---

### Post by Lakeside on 2008-11-09
Thanks Codename, I will try that now, as I am having  Linux withdrawals lol..feels like Im locked out of my house :cry: Im not sure what drivers I should choose though, wish me luck

---

### Post by Lakeside on 2008-11-09
Ok. I rebooted, and I guess it brought me to the Grub (black screen, about 7 choices, one of which was Recovery mode 8.o.4
Id did its thing then I had the command *rom*t and entered your commands. The machine shut off, then rebooted, back into the Grub menu, so I icked the first choice this time, the normal bootu, not the recovery, for 8.4 but it brought me back to the command *rom*t!  so I ty*ed in your commands again and got-  *ackage xserver-org is not installed and no info is available ...use dkg --info to examine archive files and dkg --contents to list their contents
ust/sbin/dkg-reconfigure  xserver is not installed
I tried  dkg --info= comment not found  tye dg-deb --hel* for hel* about maniulating deb files.. .....this is agony lol
*edit* Just curious, I had other advice about doing something in  safe mode, but forget how to get into safe mode as the com*uter is booting, some sort of F_ key^
thanks again

---

### Post by PmDematagoda on 2008-11-09
It seems like that you don't have the X-Server installed, try installing it with:-
```
sudo apt-get install xserver-xorg
```
and after installation reboot the system with:-
```
reboot
```
and see if your problem is now solved.

---

### Post by Lakeside on 2008-11-09
Entered command, got this-  reading *ackage lists, building deendancy tree...couldnt find xserver-org :(

---

### Post by PmDematagoda on 2008-11-09
Try:-
```
sudo apt-get update
```
and then try installing X again.

---

### Post by roger_1960 on 2008-11-09
Hi

Its xserver-xorg , did you type it right?

---

### Post by Lakeside on 2008-11-09
Ok  PmDematagoda, Roger and Codename, I got the xserver, udated/installed it with your commands, and it said it was there, then I did reboot, and it went into Grub, I guess, this time I let it boot from the first o*tion, not recovery mode and I thought it was going to give me back my GUI and..back at the command *rom*t again. NOw that xserver is installed, should I try the first commands recommended to me in this thread, I really dont have a clue anymore :confused:

---

### Post by Lakeside on 2008-11-09
Doesnt look good...TELL me I dont have to take this thing to a sho*!!:(

---

### Post by bodhi.zazen on 2008-11-09
boot to recovery mode

Enter these commands :

```
apt-get install ubuntu-desktop
telinit 2
```

---

### Post by Crafty Kisses on 2008-11-09
What are the results of this command?
```
glxinfo
```

---

### Post by Lakeside on 2008-11-09
BodiZazen, this is this is what I get from the at-get udate..and I ran it just like that, just at-get udate, I also tried sudo a*t-get u*date ubuntu-deskto* etc.    [B]Some index files failed to download etc...Failed to fetch tc.  
 and then it advised me to *run*[/B]at-get udate **** am I doing this wrong  And Codename, for   glxinfo I get  Unable to o*en disl*lay...some index files failed to download etc.

---

### Post by Crafty Kisses on 2008-11-09
Post your sources list:
```
cat /etc/apt/sources.list
```
Then try to run the following, you need to be logged in as root while you update. So try the following and hopefully this gets you back on the right track.
```
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by bodhi.zazen on 2008-11-09
it is "apt-get" not at-get :)

I assume it is a typo.

Is your Internet connection working ?

sudo apt-get update
sudo apt-get install ubutnu-desktop

---

### Post by jnw222 on 2008-11-09
did you use the server install cd instead of the alternate or desktop cds?

---

### Post by Lakeside on 2008-11-09
BodhiZazen,yes it is ty*o, the key between o and q does not work.  My internet connection is working, and I did try those codes, but will try again. I will try the last few ideas here. JNW222- I am starting to wonder if the disc is not good. A local comuter service sho* was giving them out free, they burned co*ies, it is the Ubuntu Hardy Heron 8.o.4 Server edition LTD.

---

### Post by Crafty Kisses on 2008-11-09
> **Lakeside said:**
> BodhiZazen,yes it is ty*o, the key between o and q does not work.  My internet connection is working, and I did try those codes, but will try again. I will try the last few ideas here. JNW222- I am starting to wonder if the disc is not good. A local comuter service sho* was giving them out free, they burned co*ies, it is the Ubuntu Hardy Heron 8.o.4 Server edition LTD.

That's your problem right there, it's the Server Edition, you need to get the "Desktop Edition".

---

### Post by Lakeside on 2008-11-09
*Gee but it`s great to be back home, home is where I wanna beee*:guitar:.. carried away with a little Paul Simon, but I`m sooo happy that it worked because of all your persistence and patience :)
Desktop is back! and I will be verrry careful with any future code I enter, this happened when I was trying to fix my sound card problem (which by the way, I still can`t hear anything). Funny, but I ran that apt-get installubuntu-desktop code, and ...upgrade ...update  one numerous times,  and it just kept taking me back to the grub and `recovery mode` then the command line.  This time it worked, go figure.
Thanks, you guys are awesome!  Oh, just curious, why is  the desktop edition better? If I am trying to host my own website, wouldn`t the server LTD be better? (sorry if that is for another forum/thread)

---

