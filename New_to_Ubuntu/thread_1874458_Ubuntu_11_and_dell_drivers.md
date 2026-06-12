---
title: "Ubuntu 11 and dell drivers"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by antobbo on 2011-11-03
Hi there I have just installed the latest version of ubuntu on my dell 1300 (it works fine although it is a wee slow) and I have 2 questions:
1) if there is a way to find out what drivers are missing. I know the wireless is missing because it says that the firmware is missing for example. I have in mind devices manager in windows where you can see what's missing, is there a simple way in ubuntu?
2)where do I get the missing drivers from? Like the wireless drivers, where do I get the version that will work with ubuntu?
thanks

---

### Post by Script Warlock on 2011-11-03
check the "additional drivers" how about gnome-device-manager

---

### Post by antobbo on 2011-11-03
thanks I will have a look , but how about then downloading them? I have all the drivers form my laptop in a cd, but those are for windows I believe, so I assume they won't work with ubuntu? Or will it be able to find it automatically?SOrry I am pretty new to it so I am not really sure what I am doing

---

### Post by Mark Phelps on 2011-11-03
Drivers are the bane of Linux Distros because mose hardware builders won't both with writing Linux drivers.  And you're right, your Dell drivers won't work in Linux.

You would need to check the Dell website to see if they have any Linux drivers.

---

### Post by antobbo on 2011-11-03
Hi there, thanks for that.
@Script Warlock I checked additional drivers but it is empty, it says No proprietary drivers  are n use on this system.
@Mark Phelps I have found somthing maybe: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?mediawiki/index.php/Ubuntu](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?mediawiki/index.php/Ubuntu) could that be a good point to start?
Sorry forgot to mention though, because the additional drivers is empty I can't determine which driver I am missing. ANy other suggestion?
ta

---

### Post by antobbo on 2011-11-03
uhm...sorry chaps, still can't get this to work.
I have checked whether the drivers for the wireless are installed but it looks like there is nothing, when I run iwconfig, I get no wireless extension.
So I attempted to download the last ndiswrapper package following [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Identifying_Wireless_Adapter](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Identifying_Wireless_Adapter)
I downloaded the drivers from here [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Dell_Truemobile_1300](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Dell_Truemobile_1300)
Now, the trouble I have is to do this:
"
[LIST=1]
[*]Unpack the Windows driver by using the unzip,  cabextract and/or unshield tools (run from the Terminal), and find the  INF file (.INF or .inf extension) and the SYS file (.SYS or .sys  extension). You may first need to install *cabextract* and *unshield*. 
[*]If there are multiple INF/SYS files, look in the ndiswrapper [list]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/") to see if there are any hints about which of them should be used. 
[/LIST]
"
because I am not sure which are the names of the inf and sys files and dunno what cabextract / unshield is
any suggestion?

---

### Post by spcwingo on 2011-11-03
What is the output of this command ran from a terminal:

```
lspci
```

---

### Post by wildmanne39 on 2011-11-04
Hi, please post the results of this command and it will help tell us what driver you need for your wireless.

Just copy and paste the command into the terminal and paste the results here it is much easier that way.
```
lspci -nnk | grep -iA2 net
```
Thank you

---

### Post by antobbo on 2011-11-04
Hi guys, thanks for that.
I run the two commands: 

lspci
lspci -nnk | grep -iA net

and I took 2 screenshots, as attached.
I thought this was the easiest way, if they are not good I will type the results

Now one thing that occured to me was that when I installed ubuntu the other day the network cable was unplugged. At the end of the installation I had a message saying something about the "airforce one drive" or sth like that can't remember exactly, and I said "no". Now, reading through forums, and google search results I noticed that this "airforce one" thingy seems to be one of the missing drives...

---

### Post by wildmanne39 on 2011-11-04
Hi, first we need to get rid of ndiswrapper if you still have it installed please run this command one line at a time.
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
Then install the driver and firmware with this command.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
then disconnect your wired connection and run this command please.
```
sudo modprobe b43
```
now it should come a live if it does not you probably have other drivers you installed conflicting so run this command and post the results.
```
lsmod | grep b43
```
Thank you

---

### Post by antobbo on 2011-11-04
Hi wildmanne39,
thanks for that it's sorted now.
I run all the commands except the last one and I am now connected to the wireless network.
Some of the commands failed though, like this
 sudo rm /etc/modprobe.ndiswrapper.conf
and the next one. The console said "rm: cannot remove ' /etc/modprobe.ndiswrapper.conf: no such file or directory" and similar for the other command.
Now, wildmanne39 I am a newbie so is there anywhere I can learn some of the commands for the console? I mean I don't know many commands at all, so it would be good if I learn some. COuld you point me to some good resource please? I would like to understand all the commands you make use one day : - )

---

### Post by wildmanne39 on 2011-11-04
There are so many commands this well get you started, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/)
[http://linuxcommand.org/](http://linuxcommand.org/)

The pocket guide can be downloaded for free at the top of the page that the link opens.

If you want to know how to use a command and you know the name of it just open the terminal and type man, then the name of the command and it will tell you the options you can use with that command.

Man stand for manual pages.

---

### Post by antobbo on 2011-11-05
thanks a lot!

---

### Post by wildmanne39 on 2011-11-05
Hi, your welcome! 
Enjoy

---

