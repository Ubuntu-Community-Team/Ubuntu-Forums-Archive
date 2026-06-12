---
title: "HOWTO: Get SKIM working in breezy"
date: 2005-11-24
forum: Outdated Tutorials &amp; Tips
---

### Post by GoldBuggie on 2005-11-24
Finally after breezy has been released I've gotten a full set of scim and skim working. (not that some packages are for japanese, if you want for chinese, korean or whatever then you hopefully know what you need)

I used the repositories from the chinsese ubuntu. So add the following to */etc/apt/sources.list*

```
deb http://svn.ubuntu.org.cn/ubuntu-cn/ breezy main
``` or if for some reasone the above doesn't work use```
deb http://archive.ubuntu.org.cn/ubuntu-cn/ breezy main
``` Then after a ```
sudo apt-get update
```. I did a ```
sudo apt-get install skim scim libskim0 scim-anthy libscim8 scim-gtk2-immodule scim-modules-socket scim-modules-table scim-tables-ja im-switch
``` 
I did get error complaining about mismatch in size from skim and libskim0 so I downloaded them by hand and installed them using dpkg. I'm hoping you will not get the same but if you do then just do the following.

in ~
```
mkdir tmpSkim
cd tmpSkim
wget http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/skim/[skim_1.4.3-0ubuntu2_i386.deb]("http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/skim/skim_1.4.3-0ubuntu2_i386.deb")
wget [http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/skim/]("http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/skim/")[libskim0_1.4.3-0ubuntu2_i386.deb]("http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/skim/libskim0_1.4.3-0ubuntu2_i386.deb")
sudo dpkg -i *.deb
cd ..
rm -R tmpSkim
``` 
Restart computer...open up application by choice and do a ctrl-space and vola! :D

[SIZE=1]*I am assuming that most things are set up from the deb packages. If for some reason it doesn't work please read the below posts since they go thrue practically everything you need(if you use utf8 that is)*[/SIZE]

---

### Post by kairu0 on 2005-11-30
You don't get segfaults when you run scim-setup do you?

Are you able to input Japanese in all QT apps?

---

### Post by GoldBuggie on 2005-11-30
It works for all apps! After upgrading to breezy skim stopped working basically. But using these packages from these repositories I got it to work perfectly. No seg. fault. or anything.

---

### Post by kairu0 on 2005-11-30
I've gotta try that. Poor Japanese input was the primary reason why I left Kubuntu.

---

### Post by GoldBuggie on 2005-11-30
Tell me if you get it to work. Only additional info I can provide that is the setting of
LC_CTYPE=ja_JP.UTF-8
LANG=en_US.UTF-8
in /etc/environment

Only other setting that can effect it are the variables
XMODIFIERS="@im=SCIM"
GTK_IM_MODULE="scim"
XIM_PROGRAM="scim -d"
QT_IM_MODULE="scim"

But hopefully you wont have to enable these yourself. My system has them but I'm guessing the packages added them. Don't remember where I should have forgotten to remove them prior to installing skim otherwise.

Hope it works out for ya.

---

### Post by kairu0 on 2005-11-30
[QUOTE=GoldBuggie]
Only other setting that can effect it are the variables
XMODIFIERS="@im=SCIM"
GTK_IM_MODULE="scim"
XIM_PROGRAM="scim -d"
QT_IM_MODULE="scim"
[/QUOTE]

Were these settings in the same /etc/environment? If no, where did you find them written?

I might have had a complicated locale issue last time so I want to be as careful as possible.

---

### Post by GoldBuggie on 2005-11-30
At the moment I only have them in .bashrc but the best thing would probably be to put them in /etc/environment. If you do decide on trying to put them in .bashrc do not forget to do a
export XMODIFIERS GTK_IM_MODULE XIM_PROGRAM QT_IM_MODULE
(this is only needed for .bashrc)

please note that this is only a remain from me using hoary before and I would put them in /etc/environment if I was doing a complete reinstall of breezy.

I would recommend just install skim like mentioned in first post and reboot. Then in konsole write $ and press tab twice. This will show you the global variables. If you find $XMODIFIERS $GTK_ ... etc there you will know that the package has deliviered them for you. If you do not find them and skim is not working then put the variables in /etc/environment reboot and check again.

---

### Post by kairu0 on 2005-12-01
On a fresh Kubuntu Breezy install, I just tried it out.

First, I installed all the packages in your "apt-get install..." line and that went fine without any problem.

I logged out, logged back in and scim wasn't getting started. So, I added "LC_CTYPE=ja_JP.UTF-8" to /etc/environment and logged out, and in again.

I don't have a skim applet in my tray and Japanese input only works in GTK programs. When I enter a QT app and push Ctrl+Space scim comes up with English as the only available language in it's list. Did I miss a step?

---

### Post by GoldBuggie on 2005-12-01
Well...if you can get it to pop up in QT apps...that sounds good...even without the the engines.

hmmm did you check the other variables that I mentioned..they are vital...I just hopes that skim had them installed without doing them manually. So please make sure you have those variables set as well.
```
 sudo kate /etc/environment
```
Put this there
```
 XMODIFIERS="@im=SCIM"
 GTK_IM_MODULE="scim"
 XIM_PROGRAM="scim -d"
 QT_IM_MODULE="scim"
``` 

Only other japanese related thing I got is the anthy package, not scim-anthy just anthy. ```
sudo apt-get install anthy
``` 
hmmm...what more...hmmm...make sure your locales are available and configured(there will come a section where you choose which languages your system should support, make sure you have english and japanese checked, the UTF8 version) ```
sudo dpkg-reconfigure locales
``` Can't think of anything more at this moment.

---

### Post by kairu0 on 2005-12-01
I ran "dpkg-reconfigure locales" to install ja_JP.UTF-8.

I also noticed that the QT_IM_MODULE variable was missing so I added it to /etc/environment. Now, all of the variables seem to be okay.

But now that I've added QT_IM_MODULE, Ctrl+space will not bring up SCIM! And if I type "scim" at a konsole I get:


Smart Common Input Method 1.4.2

Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
SCIM has exited abnormally.


This is a lot like the segfaults I was getting before.

---

### Post by GoldBuggie on 2005-12-01
just running scim in the konsole will give you that. It does the exact same thing for me. Running skim doesn't give me anything. So I don't know what is done behind the scenes there.

Running ```
scim-setup
``` I see the engines that are used. Do you have a IMEngine->Anthy option? You did install the package anthy( sudo apt-get install anthy )?

When running ps aux | grep scim I get this.
```
/usr/lib/scim-1.0/scim-launcher -d -c simple -e all -f socket --no-stay
/usr/lib/scim-1.0/scim-helper-manager
/usr/lib/scim-1.0/scim-panel-gtk --display :0.0 -c socket -d --no-stay
/usr/lib/scim-1.0/scim-launcher -d -c socket -e socket -f x11
```
Try running this please.

---

### Post by kairu0 on 2005-12-02
I don't have IMEngine -> Anthy although "dpkg -l|grep anthy" returns:


```
ii  anthy                                 6724-1                             A Japanese input method (backend, dictionary
ii  libanthy0                             6724-1                             Anthy runtime library
```


"ps ax|grep scim" returns:

```
8115 pts/1    S+     0:00 scim
 8117 ?        Ss     0:00 /usr/lib/scim-1.0/scim-launcher -d -c simple -e all -f socket --no-stay
 8118 pts/1    S+     0:00 /usr/lib/scim-1.0/scim-launcher -c socket -e socket -f x11
 8137 pts/2    R+     0:00 grep scim
```

---

### Post by GoldBuggie on 2005-12-02
Ok...I tried some things to see how to disable and reenable scim for me.

First I checked
```
dpkg -l | grep anthy
ii  anthy 6724-1ubuntu1 
ii  libanthy-dev 6724-1ubuntu1  
ii  libanthy0 6724-1ubuntu1
ii  scim-anthy 0.7.1-1ubuntu1

``` Then a 
```
dpkg -l | grep scim
ii  libscim-dev 1.4.2-0.3ubuntu
ii  libscim8 1.4.2-0.3ubuntu 
ii  scim 1.4.2-0.3ubuntu 
ii  scim-anthy 0.7.1-1ubuntu1
ii  scim-gtk2-immodule 1.4.2-0.3
ii  scim-modules-socket 1.4.2-0.3ubuntu 
ii  scim-modules-table 0.5.3-0.2ubuntu
ii  scim-tables-ja  0.5.3-0.2ubuntu
``` 
then
```
ps ax | grep scim
 6811 ? Ss 0:00 /usr/lib/scim-1.0/scim-launcher -d -c simple -e all -f socket --no-stay
 6830 ? Ss  0:00 /usr/lib/scim-1.0/scim-helper-manager
 6831 ? Ssl  0:00 /usr/lib/scim-1.0/scim-panel-gtk --display :0.0 -c socket -d --no-stay
 6833 ? Ss 0:00 /usr/lib/scim-1.0/scim-launcher -d -c socket -e socket -f x11
``` 
After this info I started to kill the above 4 processes. The two process that always seemed to return to me was scim-helper-manager & scim-panel-gtk. But now with only those two processes scim wasn't working. So I started the processes again exactly like how they looked from before but starting from the ihghest process no.
*scim-launcher -d -c socket -e socket -f x11*
this didn't bring anything back
*/usr/lib/scim-1.0/scim-launcher -d -c simple -e all -f socket --no-stay*
well...it works in firefox but not in konsole now. So I killed the two scim processes again and started them, this time starting with the lowest priority no.
1. ```
/usr/lib/scim-1.0/scim-launcher -d -c socket -e socket -f x11
``` still nothing
2. ```
/usr/lib/scim-1.0/scim-launcher -d -c simple -e all -f socket --no-stay
``` POOF...now scim works in konsole again.

So please try and kill your scim-launcher processes and run them as I have done(starting with 1). Try and run */usr/lib/scim-1.0/scim-helper-manager* and */usr/lib/scim-1.0/scim-panel-gtk --display :0.0 -c socket -d --no-stay* as well. Your processes doesn&#7831; match exactly with the arguments so please use my arguments.

Now after you have done this I can only think of 2 things that you can try and these are final resort. I'm using kde3.5 don't know if that matters. Maybe downloading the anthy library and compiling it yourself will help in bringing it there([http://sourceforge.jp/projects/anthy/]("http://sourceforge.jp/projects/anthy/")) I may have done so in the distant past.

Hope this works out for ya...I was so happy when I got scim working fully again and I can even kill it and restore it so it is quite stable on my machine now we need to get it to work for you. Hopefully the scim-launcher parameters will make a difference.

---

### Post by GoldBuggie on 2005-12-02
Ahh..one final thing that I can give info on.
check that your locales are correctly set up
```
locale
```
```
LANG=en_US.UTF-8
LC_CTYPE=ja_JP.UTF-8
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

Notice that LC_ALL is empty. This is important since LC_ALL owerrides the other LC_XXXX

---

### Post by kairu0 on 2005-12-02
Hey, it works!

I noticed in your "dpkg -l" list that you had scim-anthy and I didn't. So I installed it, logged out, logged back in, and now I'm in business!

Thanks a million for your help man.

By the way, you don't have a tray icon for scim or skim do you?

---

### Post by GoldBuggie on 2005-12-02
It works!!!\\:D/ PERFECT! I'm so very happy for ya'. I was getting worried. Thanks for sticking thrue it all. Now I know it works. 

And no I do not have an icon in the systray. Don't really know why.

---

### Post by kairu0 on 2005-12-02
Now I can use Ubuntu + Kubuntu together again! :)

---

### Post by kLy on 2006-01-28
OK, I've tried everything here but there's NOTHING! Running "skim" or "skim -d" (even with --verbose) displays absolutely nothing and there's no tray icon or anything, and "scim -d" just says:
```

Smart Common Input Method 1.4.2

Launching a SCIM daemon with Socket FrontEnd...
Loading kconfig Config module ...
Creating backend ...

Launching a SCIM process with x11...
Loading kconfig Config module ...
Creating backend ...
Failed to launch SCIM.

```

 I've followed everything here and my locales etc. are set up properly... what is the darn matter? :( Help! Thx.

---

### Post by GoldBuggie on 2006-01-28
I know that scim nor skim won't run when executed from the konsole. Please follow the whole thread and do the debug that it explained. The thread contains basically all that I can give you as information. 

Make sure that the right processes are running etc.

There will be no icon in the systray but scim will work with all apps.

---

### Post by kLy on 2006-01-30
Hi

I *have* tried the things in the steps provided but nothing... :(

Running scim-launcher as above has scim daemonised but nothing when I Ctrl+Space. Trying to run the panel produces: "Failed to initialize Panel Agent!" :(

Thx

---

### Post by kLy on 2006-01-30
OK, this is what I've done:

1. installed the scim, skim, scimlib, scim-modules-socket etc. packages mentioned (from the CN Ubuntu repo) and scim-pinyin as the input (I'm trying to write Chinese, not Japanese :)

2. adjusted locales (dpkg-reconfigure locales) and installed the zh GB UTF8 locale.

3. Added environment variables

4. Reboot

Then tried running the above things... but nothing :(

And scim-setup gets me a segfault :(

---

### Post by kLy on 2006-01-30
Something else strange. I've added to my /etc/environment:

XMODIFIERS="@im=SCIM"
GTK_IM_MODULE="scim"
XIM_PROGRAM="scim -d"
QT_IM_MODULE="scim"

However, GTK_IM_MODULE and XIM_PROGRAM just aren't getting set (even after reboot), but XMOD and QI_IM is... huh? :(

---

### Post by GoldBuggie on 2006-02-02
Please try and follow the whole thread if you haven't done so. I had a chat with [kairu0]("http://www.ubuntuforums.org/member.php?u=37152") and basically all that is explained there is all the checking I can give you.

I recently got a person doing this and he got it working.

---

