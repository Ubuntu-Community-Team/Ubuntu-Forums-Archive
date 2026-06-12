---
title: "Ubuntu and Gnome help"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by firas2 on 2014-05-08
Need some advice Please I want to install Gnome but I dont understand do I need ubuntu first and then install gnome or how does this go 

BTW I have os7  64X  raid 0 on 2 ssd and I do have an 80gb extra hhd I want to put gnome on it 

can any one direct me on witch one should be installed first many thanks and extra info will help me alot 

many thanks

---

### Post by kansasnoob on 2014-05-08
> **firas2 said:**
> [COLOR=#000000][FONT=microsoft sans serif][B]Need some advice Please I want to install Gnome but I dont understand do I need ubuntu first and then install gnome or how does this go 

BTW I have os7  64X  raid 0 on 2 ssd and I do have an 80gb extra hhd I want to put gnome on it 

can any one direct me on witch one should be installed first many thanks and extra info will help me alot 

many thanks[/B][/FONT][/COLOR]

It depends on what you mean by GNOME.

The standard GNOME UI is now GNOME Shell which is the default interface offered by Ubuntu GNOME which also offers a GNOME Classic session, but that classic session does NOT use 'gnome-panel'.

If you want 'gnome-panel' you want the "flashback" sessions as described here:

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

---

### Post by firas2 on 2014-05-08
Thank u sir for the fast feedback   

But please let me explain    I found this  [http://gnome-look.org/?xsection=home](http://gnome-look.org/?xsection=home)  so i was reading and Looking around

then I found an old hdd  with 80gb   so I was interested in the desktop and the eye candy icons  and at the same time I would Like to use gnome for surfing and other-stuff  

But I cant figure out can I just Install Gnome  or do I need the Ubuntu  ??   

Many thanks  I hop I explained it better this time    :D

---

### Post by kansasnoob on 2014-05-08
You could just try Ubuntu GNOME:

[http://ubuntugnome.org/ubuntu-gnome-14-04-lts-is-released/](http://ubuntugnome.org/ubuntu-gnome-14-04-lts-is-released/)

---

### Post by pfeiffep on 2014-05-08
> **firas2 said:**
> Thank u sir for the fast feedback   

But I cant figure out can I just Install Gnome  or do I need the Ubuntu  ??   

Many thanks  I hop I explained it better this time    :D
[Gnome is a desktop environment]("http://www.gnome.org/") that requires an OS to run it.
Ubuntu provides a [Gnome release]("https://wiki.ubuntu.com/UbuntuGNOME") which contains the Gnome desktop environment with Ubuntu OS.

---

### Post by grahammechanical on 2014-05-08
If you install Ubuntu you will get the Gnome 3 desktop environment (DE). But you will not get the Gnome 3 shell user interface. Ubuntu has the Unity interface. There are other Linux distributions that come with Gnome 3 DE and also Gnome 3 shell.

So you need to install a Linux distribution. Some come with the Gnome 3 DE and Gnome 3 shell. Some also offer alternatives such as KDE (K Desktop Environment). Ubuntu has a range of desktop environments and user interfaces.

Ubuntu = Gnome 3 DE + Unity UI
Ubuntu Gnome = Gnome 3 DE + Gnome 3 shell
Kubuntu = KDE + Plasma UI
Xubuntu = Xfce DE
Lubuntu = LXDE

[http://www.ubuntu.com/tour/en/](http://www.ubuntu.com/tour/en/)
[http://ubuntugnome.org/](http://ubuntugnome.org/)
[http://www.kubuntu.org/](http://www.kubuntu.org/)
[http://xubuntu.org/](http://xubuntu.org/)
[http://lubuntu.net/](http://lubuntu.net/)

In each case we can download an image, burn it to DVD or USB and run a live session to test it out before we install it.

Regards.

---

### Post by Kingsrookie on 2014-05-08
Ubuntu will need to be installed first. If I'm not mistaken, you can go into terminal afterwords with sudo apt-get install gnome-panel. You will need root password to let it install. Afterwords, log out and choose the gnome desktop environment when logging back in.

---

### Post by firas2 on 2014-05-08
Thanks Guys for all the Info 

Please forgive me for asking this again ,, I just want to make sure 

So pretty mush go to the Link that was provided by Kansasnoob    
[**Download Ubuntu GNOME 14.04 LTS**]("https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME")
and download it right ??  


thank u downloading now

---

### Post by pfeiffep on 2014-05-09
@firas2, yes download Gnome 14.04 LTS

---

### Post by firas2 on 2014-05-09
> **pfeiffep said:**
> @firas2, yes download Gnome 14.04 LTS


Thanks  man I have it   Just got to clear my head and get some time for me to install 

any advices before I start   I will be thankful  as this is my first time installing this   ,,,,,   with windows 7 64X [U]Ultimate 

many thanks [/U]

---

### Post by pfeiffep on 2014-05-09
If you want to use separate partitions choose ***'something else'***. 

[LIST]
[*=1]10 - 15 GB for root ( / )
[*=1]probably swap = GB memory installed in hardware (if you want to hibernate)
[*=1]remainder for /home
[/LIST]

---

### Post by firas2 on 2014-05-10
@[[COLOR=#000000]pfeiffep[/COLOR]]("http://ubuntuforums.org/member.php?u=1788249")[COLOR=#000000] 

thanks for the reply   U mean install it on my raid 0  ??

or just take 20gb  from the 80gb hdd that i have set aside ??

thank u [/COLOR]

---

### Post by pfeiffep on 2014-05-10
@firas2, If your computer has the capability to boot your 80 GB external drive you should [B]100% choose 'something else'

[/B]IMO take 40 GB [10 for /  , # GB ram in your system for /swap , and the remainder for /home] 

I have 0 experience with raid

---

### Post by firas2 on 2014-07-31
Hi to all again ;)

been away for a little bit,  had an accident on my motorcycle   and because of that 
every thing on my to do list got delayed ;)

so i have installed gnome  on a  virtual machine ,,,

my question is   do i still need to treat it as a normal pc ?  meaning  install antivirus and do scans and all of that good stuff ??
on the ubuntu virtual machine ??

and also  can u please direct me to where should i look for installing eye candy  for gnome ?

many thanks  please for give my writing   using my left hand only ):P

---

### Post by Vladlenin5000 on 2014-07-31
I don't do eye candy so I'll leave that for others...

No, you don't need antivirus in a Linux, VM or not.

Please don't make duplicated posts.

---

### Post by firas2 on 2014-07-31
thank u  and yes i did do a double post please forgive me as i was 
waiting for an answer ,, but did not relise the time different  

thank u

---

