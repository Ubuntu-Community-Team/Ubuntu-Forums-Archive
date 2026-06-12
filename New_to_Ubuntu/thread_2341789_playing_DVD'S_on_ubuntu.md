---
title: "playing DVD'S on ubuntu"
date: 2016-10-31
forum: New to Ubuntu
---

### Post by peter.rollason on 2016-10-31
Ive just installed ubuntu 16 lts onto to my acer laptop. It flew on without a hitch .....

however I can't seem to get it to play dvd's - Ive installed VLC media player - but the dvd's just sit there - ive downloaded libdvdcss - but not sure if its installed - some google sites suggest typing commands into terminal - which I have no idea how to do....    any ideas ?

---

### Post by yetimon_64 on 2016-10-31
> **peter.rollason said:**
> ... - ive downloaded libdvdcss - but not sure if its installed - some google sites suggest typing commands into terminal ...

Firstly to check if something (libdvdcss2 in this case) is installed or not open a terminal and use the "apt-cache policy" command eg.
> ```
yetiman:~ $ apt-cache policy libdvdcss2
libdvdcss2:
  Installed: 1.2.13-0
  Candidate: 1.2.13-0
  Version table:
 *** 1.2.13-0 0
        100 /var/lib/dpkg/status
```
You can see from my results (the "Installed" result) I actually have it installed here. If the "Installed" line shows "none" you still need to install it.

Now about the commands in terminal you mention from your googling ... probably the easiest way to install libdvdcss2 is to use the terminal and enter the next command and your user log in password (for sudo access).
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
This command will download and install libdvdcss2 for you. Rerun the apt-cache policy command again afterwards to see the installation and its version if you wish. 
**Edit:** when entering your sudo password in the terminal you will not see any visual feedback like asterisks etc, this is a security measure for Linux only; the password will still be going in and if you enter it correctly will work fine.

Regards, yeti.

**Edit 2:** OP, see Frog Hair's next post, a better command to use for installation would be "apt-get install".

---

### Post by Frogs Hair on 2016-10-31
First check in Details and see if VLC is set to default, then copy and paste the following commands in the terminal and enter your password. 

```
sudo apt-get install ubuntu-restricted-extras
```

```
sudo apt-get install libavcodec-extra
``` 

```
sudo apt-get install libdvdcss2
```

---

### Post by ajgreeny on 2016-10-31
All the info you need is summed up at [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) with all the differences needed according to version of Ubuntu noted separately.

---

### Post by peter.rollason on 2016-11-01
> **Frogs Hair said:**
> First check in Details and see if VLC is set to default, then copy and paste the following commands in the terminal and enter your password. 

```
sudo apt-get install ubuntu-restricted-extras
```

```
sudo apt-get install libavcodec-extra
``` 

```
sudo apt-get install libdvdcss2
```

I tried this - but after the first command it all appeared to be installing but then I got this microsoft EULA windows in terminal - I COULDN'T WORK HOW TO OK this - and get back to terminal ? - any ideas ?

Edit - got it to play - but sound is very quiet ? - any ideas ?

---

### Post by coffeecat on 2016-11-01
> **peter.rollason said:**
> I tried this - but after the first command it all appeared to be installing but then I got this microsoft EULA windows in terminal - I COULDN'T WORK HOW TO OK this - and get back to terminal ? - any ideas ?

That was for the microsoft core fonts, which are well worth having. Simply press the TAB key to highlight OK, and then press enter.

---

### Post by deadflowr on 2016-11-02
> **peter.rollason said:**
> Edit - got it to play - but sound is very quiet ? - any ideas ?

Click on the speaker icon in the top panel and open sound settings, then click on the allow louder than 100%(may distort sound) just below the volume slider.
See if that boost the volume.
Also, check the levels in vlc.
You can also access the equalizer in vlc through the menu item Tools >> Effects and Filters.

---

