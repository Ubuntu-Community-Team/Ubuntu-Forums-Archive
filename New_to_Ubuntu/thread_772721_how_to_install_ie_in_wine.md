---
title: "how to install ie in wine"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by DarinB on 2008-04-28
how to install ie in wine
I am getting an error when trying to open up firefox in wine to watch ABC

more media player
the plug in performed an illegal operation...

I thought that if i install ie maybe it will work
halp
I am getting an error when trying to open up firefox in wine to watch ABC

more media player
the plug in performed an illegal operation...

I thought that if i install ie maybe it will work
help

---

### Post by pro003 on 2008-04-28
try Wine-Doors...
within got some other appz too...

---

### Post by Joeb454 on 2008-04-28
Do a google search for 'ies4linux'

Without quotes of course. It does it all for you :)

---

### Post by Dunrobin on 2008-04-28
Maybe this is a silly question, but why are you trying to open Firefox in Wine?  You should have the Linux version of Firefox already installed with your Ubuntu distribution.  You don't need to install a Windows version of it.

If you feel that you do need to have IE installed, check out IEs4Linux at
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by DarinB on 2008-04-28
i tried ie4linux but it was only for edgy???

---

### Post by Dunrobin on 2008-04-28
Oops - somehow I managed to post my response twice.  Sorry about that!

---

### Post by pro003 on 2008-04-28
Here you go:

You have to enable universe packages first. It is also recommended that you use the official winehq ubuntu package:

1) Open a terminal

2) Open /etc/apt/sources.list

 sudo gedit /etc/apt/sources.list

3) Uncomment (or add) following lines:

 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe

4) Add this line:

 deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

5) Close gedit. Update and install wine and cabextract:

 wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
 sudo apt-get update
 sudo apt-get install wine cabextract

6) Download IEs 4 Linux and install

 wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
 tar zxvf ies4linux-latest.tar.gz
 cd ies4linux-*
 ./ies4linux

Note for Dapper users: if you use ubuntu dapper, replace edgy with dapper on lines above. Note for Feisty users (7.04): if you use ubuntu Feisty, replace edgy with feisty in the lines above. Also replace gedit with kedit if running Kubuntu instead of Ubuntu.

For "Fiesty" K/Ubuntu Users (and 64-bit "Fiesty): [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by pro003 on 2008-04-28
Here you go:

You have to enable universe packages first. It is also recommended that you use the official winehq ubuntu package:

1) Open a terminal

2) Open /etc/apt/sources.list

 ```
sudo gedit /etc/apt/sources.list
```

3) Uncomment (or add) following lines:

```
 deb http://us.archive.ubuntu.com/ubuntu edgy universe
```

4) Add this line:

 ```
deb http://wine.budgetdedicated.com/apt edgy main
```

5) Close gedit. Update and install wine and cabextract:

 ```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
 sudo apt-get update
 sudo apt-get install wine cabextract

```

6) Download IEs 4 Linux and install

```
 wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
```
```
 tar zxvf ies4linux-latest.tar.gz
```
```
 cd ies4linux-*
```
```
 ./ies4linux
```

Note for Dapper users: if you use ubuntu dapper, replace edgy with dapper on lines above. Note for Feisty users (7.04): if you use ubuntu Feisty, replace edgy with feisty in the lines above. Also replace gedit with kedit if running Kubuntu instead of Ubuntu.

For "Fiesty" K/Ubuntu Users (and 64-bit "Fiesty): [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by DarinB on 2008-04-28
crap!!! i installed wine doors now i lost my keyboard ;ayout i use dvorak
jow do i remove the wine doors crap

---

### Post by DarinB on 2008-04-28
please help 
i installed wgne doors messed up my keyboard i removed it now i can't get my dvorak back

---

### Post by forrestcupp on 2008-04-28
For a lot of web sites, you can use the [User Agent Switcher](https://addons.mozilla.org/en-US/firefox/addon/59) addon for Firefox to make the web site think that you are using IE7 with Windows Vista.  I use that addon to view media on a lot of sites that claim to not support Linux.

It didn't work at ABC, though.  It couldn't detect that I have Flash installed.  I think you'd be a lot better off installing the Windows version of Firefox with Wine than you would trying to get IE working.  Firefox in Wine should work, too.

---

### Post by DarinB on 2008-04-28
ok T fixed it by removing the keyboard styles then restoring the defaults
then adding the dvorak again
whew! glad thats over

---

### Post by DarinB on 2008-04-28
I use firefox in wine. It used to work so i thought i could try ie

---

### Post by pro003 on 2008-04-28
why would you run firefox in wine?

as for wine doors I can assure you that it did not change your keyboard layout.... but anyway, you can always go

System > Preferences > Keyboard

...and manage your keyboard layout.

I have installed IE6 few minutes ago and it works just fine...

you have post above how to install it.:popcorn:

---

### Post by forrestcupp on 2008-04-28
> **pro003 said:**
> why would you run firefox in wine?


I can't say why someone would use Firefox in wine as their primary browser, but there are uses for it.  One being exactly what the OP needs help with.  For those sites that only work in Windows and not Linux.  I used to use it when Fox had their OnDemand shows at MySpace.  They didn't work in native Linux, but they worked with Firefox in Wine.

---

### Post by pro003 on 2008-04-29
I am 10 hrs / day on internet and I've been for all these years maybe twice faced with situation in which the site I'am visiting is asking for IE6 or above. However, this is a free world...

---

### Post by tliotis on 2008-04-29
thanks for wine doors

---

### Post by forrestcupp on 2008-04-29
> **pro003 said:**
> I am 10 hrs / day on internet and I've been for all these years maybe twice faced with situation in which the site I'am visiting is asking for IE6 or above. However, this is a free world...

Sure, but if one of those two sites is one you visit frequently, it's worth it.  Just try going to abc.com and watching their videos with your Linux Firefox and see what happens.  Fox News media on their web site is another one that works with Firefox, but not in Linux, unless you trick them into thinking you're using Vista with the User Agent Switcher.  TurboTax's online version is another.  I could go on and on, but you get the picture.

---

### Post by pro003 on 2008-04-29
what about Konqueror? I think he has some options to appear / mask himself as firefox, ie, etc. ?

---

