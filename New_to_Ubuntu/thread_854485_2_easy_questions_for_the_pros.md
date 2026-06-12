---
title: "2 easy questions for the pros"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Exxon on 2008-07-09
whelp xp was <acting up> on my laptop and I got pissed off and installed ubuntu....Keep in mind I'm posting this from my desktop, it still has internet connection of course, but my laptop don't.

All I want to do with my laptop is simply:

Surf the Web
Watch Movies

Ubuntu 6.06

First problem: My Belkin network card only comes with xp drivers, and it doesn't work what soever......

well I downloaded the NdisWrapper and installed it, and I have the windows drivers copied to the main screen......But I can't figure out how to open up nsidwrapper to install the .inf and .sys files.........



Second Problem: The dvd player that comes with ubuntu don't play your encrypted dvd's.........I downloaded libdvdread3.09 and installed it, but dvd's still wont play......



any help here? i'm a noob right now and hate it....

I gotta have this figured out by friday because I'm flying outa state and need me laptop.


thanks

---

### Post by YaroMan86 on 2008-07-09
> **Exxon said:**
> whelp xp was being gay on my laptop and I got pissed off and installed ubuntu....Keep in mind I'm posting this from my desktop, it still has internet connection of course, but my laptop don't.

All I want to do with my laptop is simply:

Surf the Web
Watch Movies



First problem: My Belkin network card only comes with xp drivers, and it doesn't work what soever......

well I downloaded the NdisWrapper and installed it, and I have the windows drivers copied to the main screen......But I can't figure out how to open up nsidwrapper to install the .inf and .sys files.........



Second Problem: The dvd player that comes with ubuntu don't play your encrypted dvd's.........I downloaded libdvdread3.09 and installed it, but dvd's still wont play......



any help here? i'm a noob right now and hate it....

I gotta have this figured out by friday because I'm flying outa state and need me laptop.


thanks

I don't know anything about wireless, since I don't use it, but...

Open a terminal and type the following:

```

sudo apt-get install fakeroot build-essential debhelper
sudo /usr/share/doc/libdvdread3/install-css.sh

```

That'll get your DVD playback working.

---

### Post by bobnutfield on 2008-07-09
Let me give this a try:

1.  If your laptop will handle it, you should upgrade to Hary Herron.  The newer kernel will support more hardware, namely more wireless cards.  You may not even need ndiswrapper with a newer kernel.  

2.  You will also need libdvdcss2 to play encrypted dvd's, also available from Medibuntu repos.

If you MUST continue with such an old version of Ubuntu, post back and we can get you through ndiswrapper.

Bob

---

### Post by billgoldberg on 2008-07-09
> **Exxon said:**
> whelp xp was being gay on my laptop and I got pissed off and installed ubuntu....Keep in mind I'm posting this from my desktop, it still has internet connection of course, but my laptop don't.

All I want to do with my laptop is simply:

Surf the Web
Watch Movies

Ubuntu 6.06

First problem: My Belkin network card only comes with xp drivers, and it doesn't work what soever......

well I downloaded the NdisWrapper and installed it, and I have the windows drivers copied to the main screen......But I can't figure out how to open up nsidwrapper to install the .inf and .sys files.........



Second Problem: The dvd player that comes with ubuntu don't play your encrypted dvd's.........I downloaded libdvdread3.09 and installed it, but dvd's still wont play......



any help here? i'm a noob right now and hate it....

I gotta have this figured out by friday because I'm flying outa state and need me laptop.


thanks

Ubuntu 6.06 is two years old and outdated.

I suggest upgrading to 8.04. A clean install of 8.04 would be even better.

(it comes with a newer kernel, so your card might have support then)

Also the 6.06 repositories are outdated.

I don't know much about ndiswrapper as I never needed it but can help on the dvd issue.

Just click on the "install all codecs" link in my signature.

All you need on the codecs front is there.

---

### Post by niyonk on 2008-07-09
Hardy?? anyone? :(

Welcome to the forums, Exxon :biggrin:
Try hardy or gutsy. They will more likely work "out-of the box" than 6.06(dapper i think)
as for your wireless...there should be somekind of ndispwrapper icon in the menus...:) check it out!

And download "ubuntu restricted extras" to play music, video and DvDs
Don't know much about 6.06 tho ;)

---

### Post by richardjennings on 2008-07-09
check out [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

open up a terminal

move to the directory the .inf is in

cd ~/Desktop 


to install the .inf:
sudo ndiswrapper -i filename.inf


to check it installed:
sudo ndiswrapper -l

check for problems with depmod:
sudo depmod -a

No problems then load the ndiswrapper module:
sudo modprobe ndiswrapper

After that you need to configure the connection with either iwconfig or System / Administration / Network

---

### Post by bobnutfield on 2008-07-09
Most Belkin cards use either the rw1211zx module or the rt2500.  Both of these drivers are in the newer kernels stock. But if you are going to use ndiswrapper, there is a nifty little GUI for it in the Ubuntu repo called ndisgtk.  It makes it easy to install the windows drivers.

---

### Post by Exxon on 2008-07-09
:lolflag:  I downloaded ubuntu 6.06 2 years ago and put it on a cd, and just now got around to installing it........


I'll download the newest version and see what happens :popcorn:


thats for the great and fast input guys!!

---

### Post by deNoobius on 2008-07-09
> **YaroMan86 said:**
> I don't know anything about wireless, since I don't use it, but...

Open a terminal and type the following:

```

sudo apt-get install fakeroot build-essential debhelper
sudo /usr/share/doc/libdvdread3/install-css.sh

```

That'll get your DVD playback working.

Just wanted to say I had the same problem with DVD playback and that did indeed fix it!  Thanks.

---

### Post by Exxon on 2008-07-09
ok I downloaded 8.04 heron....it detected "Belkin Unknown Device 701f (rev20)......but I have no internet or wireless signal detected, and the lights on my card arn't flashing....I entered in the code sudo ndiswrapper -i BLKWGNv7.sys.inf (also tried net8185)  and it says couldn't copy at /usr/sbin/ndiswrapper line 135 for both codes...

Heres the info from the wireless section....

>  Belkin
	

F5D7010 v7
	

Realtek 8185
	

no must use(ndiswrapper)
	

Works in Feisty with ndiswapper-utils and the Realtek Windows driver (net8185.inf). Belkin's driver won't work well. After installing the driver, use the command "ndiswrapper -a" to link the driver to the card. My computer would intermittently freeze for 5 seconds, but this is rare after I stopped NetworkManager (sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop); got my network's SSID (iwlist wlan0 scan) and configured the interface (sudo iwconfig wlan0 essid <ESSID>)
	

2007-10-10
	

PCMCIA 


Could a moderator move this thread to the wireless section?

---

### Post by Exxon on 2008-07-09
:popcorn:

---

