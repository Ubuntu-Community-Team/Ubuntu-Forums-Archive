---
title: "Could someone explain this please..."
date: 2012-05-07
forum: New to Ubuntu
---

### Post by PADDYKCSDC on 2012-05-07
hello Ubuntu users could you please assist me with the following tutorial...This tutorial is copied from this forum and I need help with the third number (i need to get to where i extracted the file)...Could someone please tell me the line of code i will need to put ito the terminal window.I'm not sure on the syntax/layout
Thank you very much I appreciate anyones help asap
1) Download [SIZE=4][COLOR=Red]**THIS**[/COLOR][/SIZE] driver (previous version didn't work for me):

[http://www.realtek.com.tw/downloads/...=true#RTL8187L]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L")

or (this is the same file):

[http://www.4shared.com/file/BSepYhR2...08202010r.html]("http://www.4shared.com/file/BSepYhR2/rtl8187L_linux_26104008202010r.html")
(I HAVE DOWNLOADED A DIFFERENT DRIVER TO THE ABOVE 2 BUT PROCESS IS THE SAME)

2) Extract

3) Open a terminal window, go to where you extracted.
---HOW DO I DO THE ABOVE I DO NOT UNDERSTAND---
---I CAN GET INTO TERMINAL BUT I DO NOT KNOW THE COMMANDS---
THE FILE NAME IS 036H_Linux_26.1040.0820.2010
AND IT IS INSTALLED TO MY DESKTOP (unpacked)
WILL IT LOOK SOMETHING LIKE THIS sudo/desktop/036H_Linux_26.1040.0820.2010/
please correct me as i am new to Ubuntu and do not know the terminal well

4) run:
sudo make

5) run:
sudo make install

6) reboot

Please could somebody explain this in simple terms please.
I get it all but No.3) and i have the correct driver downloaded from alfa website not this one.

Please don't point me to a different tutorial as I am confused ,i know its 1 line of code I do not know how to write number 3 above...Thank you for your help

---

### Post by jerome1232 on 2012-05-07
First before you attempt to build something from source, you need the build-essential package, then go ahead and build it


Edit: I also note that you downloaded the driver for linux kernel 2.6 (at least I assume that's what the 26 in the name implies), what version of Ubuntu are you using? 12.04 LTS uses 3.2, you can see what kernel you have with
```
uname -r
``` 

These are the commands for installing build-essential, cd'ing to the folder and building the driver. [COLOR="Red"]***should be updated for the correct driver* You can always just cd Desktop, then type cd and hit tab to see a list of files, type the first few letters then hit tab again to auto complete the name.[/COLOR]
```

sudo apt-get install build-essential
cd ~/Desktop/rtl8187L_linux_1041.0209.2012/
make
sudo make install
```

---

### Post by ashhab2010 on 2012-05-07
For the third step you need to use the cd command
Lets assume you put the extracted folder on your desktop
Then in terminal type 
 
cd /home/your user name/Desktop/036H_Linux_26.1040.0820.2010

---

### Post by PADDYKCSDC on 2012-05-07
ok thank you very much you guys are very fast here on Ubuntu forums.
I will type in the above commands and get back to you 1 second.

and the place where i got this tut was 

[http://ubuntuforums.org/showthread.php?t=1605285](http://ubuntuforums.org/showthread.php?t=1605285)

---

### Post by jerome1232 on 2012-05-07
I edited my post extensively make sure you refresh to catch the changes.

---

### Post by ashhab2010 on 2012-05-07
> **jerome1232 said:**
> First before you attempt to build something from source, you need the build-essential package, then go ahead and build it


Edit: I also note that you downloaded the driver for linux kernel 2.6 (at least I assume that's what the 26 in the name implies), what version of Ubuntu are you using? 12.04 LTS uses 3.2, you can see what kernel you have with
```
uname -r
``` 

These are the commands for installing build-essential, cd'ing to the folder and building the driver.
```

sudo apt-get install build-essential
cd ~/Desktop/036H_Linux_26.1040.0820.2010
make
sudo make install
```
  
He needs to know how to cd into the directory where the file is extracted not what you have given

---

### Post by PADDYKCSDC on 2012-05-07
i am running 3.2.0-24-generic

---

### Post by ashhab2010 on 2012-05-07
just use my command in the 3rd step and youll be fine

---

### Post by jerome1232 on 2012-05-07
> **PADDYKCSDC said:**
> i am running 3.2.0-24-generic

Then you downloaded the wrong driver, go back to the site and download the driver for kernel 3.0/3.1/3.2. I'll edit my post so that the cd command will be correct for cd'ing into the 3.x drivers folder.

---

### Post by jerome1232 on 2012-05-07
I also wanted to note, keep that source code around after you install, anytime there's a kernel update, you will have to re-make your source and install it. I keep source code in my home folder under a folder called src, so I have a handy way of finding it. You also need the source code to do a clean uninstall of the driver should you need to do that.

---

### Post by PADDYKCSDC on 2012-05-07
You guys are fantastic i really, really ,appreciate your help 
i have done the above and here is the last few lines of code..
Processing triggers for man-db ...
Setting up libtimedate-perl (1.2000-1) ...
Setting up libdpkg-perl (1.16.1.2ubuntu7) ...
Setting up dpkg-dev (1.16.1.2ubuntu7) ...
Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build2) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up libstdc++6-4.6-dev (4.6.3-1ubuntu5) ...
Setting up g++-4.6 (4.6.3-1ubuntu5) ...
Setting up g++ (4:4.6.3-1ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu2) ...

Should i plug my wireless adapter in and update drivers but the last time i plugged my wireless adapter into laptop without the drivers the green light was flickering dimly ,different from when it is connecting...
how do i get this driver onto my alfa awus036h ? or is it ready to plug and play now ? Please explain in very simple terms thankyou ?

---

### Post by jerome1232 on 2012-05-07
That is the last few lines for installing build essential, it doesn't indicate a successful build of your driver.

btw when posting output, go into advanced mode, highlight it all, and press the # symbol.

Have you cd'd into the drivers folder and run the make commands? What was the output of make install?

---

### Post by PADDYKCSDC on 2012-05-07
SORRY I have just seen your reply i will download the other drivers now sorry for being a noob

---

### Post by PADDYKCSDC on 2012-05-07
> **jerome1232 said:**
> Then you downloaded the wrong driver, go back to the site and download the driver for kernel 3.0/3.1/3.2. I'll edit my post so that the cd command will be correct for cd'ing into the 3.x drivers folder.
what driver do i need [http://www.alfa.com.tw/in/front/bin/ptlist.phtml?Category=105397](http://www.alfa.com.tw/in/front/bin/ptlist.phtml?Category=105397)

---

### Post by PADDYKCSDC on 2012-05-07
what driver do i need from here ? [http://www.alfa.com.tw/in/front/bin/ptlist.phtml?Category=105397](http://www.alfa.com.tw/in/front/bin/ptlist.phtml?Category=105397)

---

### Post by jerome1232 on 2012-05-07
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L)

Scroll down until you see the one for 3.0/3.1/3.2, click the US1 link in the far right and it will (slowly, takes a long time for me to connect for some reason, so have patience with it) download the correct driver.

---

### Post by PADDYKCSDC on 2012-05-07
This is what i get back from terminal

paddy@ubuntu:~$ sudo apt-get install build-essential
[sudo] password for paddy: 
Sorry, try again.
[sudo] password for paddy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
paddy@ubuntu:~$

---

### Post by jerome1232 on 2012-05-07
Why are you trying to reinstalling build essential?
That was a one time thing. Move on to the rest of what I gave you.

---

### Post by PADDYKCSDC on 2012-05-07
ok i took out the first line of code and ran it now i have got  this...below is that correct or has something gone wrong...also when my  driver is installed can i just plug my usb wifi adapter in or will i  have to go to additional drivers and update my alfa wireless card...  this is what terminal gave me 

paddy@ubuntu:~$ cd ~/Desktop/rtl8187L_linux_1041.0209.2012/
paddy@ubuntu:~/Desktop/rtl8187L_linux_1041.0209.2012$ make
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.o
/home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c: In function &#8216;rtl8180_tx&#8217;:
/home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:1382:12:  warning: cast from pointer to integer of different size  [-Wpointer-to-int-cast]
/home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c: In function &#8216;rtl8187_usb_initendpoints&#8217;:
/home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:1588:14:  warning: cast from pointer to integer of different size  [-Wpointer-to-int-cast]
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_93cx6.o
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_wx.o
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_rtl8225.o
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_rtl8225z2.o
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_led.o
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_pm.o
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_dm.o
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_softmac.o
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_rx.o
/home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_rx.c: In function &#8216;ieee80211_network_init&#8217;:
/home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_rx.c:1046:4:  warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 4 has  type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_tx.o
/home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_tx.c: In function &#8216;ieee80211_xmit&#8217;:
/home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_tx.c:426:28:  warning: assignment makes integer from pointer without a cast [enabled  by default]
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_wx.o
/home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_wx.c: In function &#8216;ieee80211_wx_set_gen_ie&#8217;:
/home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_wx.c:887:2:  warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has  type &#8216;size_t&#8217; [-Wformat]
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_module.o
/home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_module.c: In function &#8216;store_debug_level&#8217;:
/home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_module.c:271:22:  warning: comparison of distinct pointer types lacks a cast [enabled by  default]
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_crypt.o
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/r8187l.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/r8187l.mod.o
  LD [M]  /home/paddy/Desktop/rtl8187L_linux_1041.0209.2012/rtl8187/r8187l.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
paddy@ubuntu:~/Desktop/rtl8187L_linux_1041.0209.2012$ sudo make instal
[sudo] password for paddy: 
make: *** No rule to make target `instal'.  Stop.
paddy@ubuntu:~/Desktop/rtl8187L_linux_1041.0209.2012$ 
paddy@ubuntu:~/Desktop/rtl8187L_linux_1041.0209.2012$ 
paddy@ubuntu:~/Desktop/rtl8187L_linux_1041.0209.2012$ 

is the above normal ? and when should i connect my usb wifi adapter ?

---

### Post by steeldriver on 2012-05-07
> **PADDYKCSDC said:**
> 
paddy@ubuntu:~/Desktop/rtl8187L_linux_1041.0209.2012$ sudo make instal
[sudo] password for paddy: 
make: *** No rule to make target `instal'.  Stop.
paddy@ubuntu:~/Desktop/rtl8187L_linux_1041.0209.2012$ 
paddy@ubuntu:~/Desktop/rtl8187L_linux_1041.0209.2012$ 
paddy@ubuntu:~/Desktop/rtl8187L_linux_1041.0209.2012$ 

is the above normal ? and when should i connect my usb wifi adapter ?

it's normal... when you mis-spell 'instal**l**' :P

---

### Post by jerome1232 on 2012-05-07
rerun 'sudo make install' spelled correctly, reboot and plug in your wifi card.

Best of luck.

---

### Post by PADDYKCSDC on 2012-05-07
So what should i do now ? should i install it again spelling install right lol....and reboot then plug and play...once this driver is installed will the adapter work out of the box or will i have to update my wireless card with the driver ?

just a note for anyone reading this you do have to update the drivers after rebootign using the additional driver app

---

