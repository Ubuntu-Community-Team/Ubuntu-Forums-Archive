---
title: "HOWTO: Tether AT&amp;T Fuze to Ubuntu"
date: 2009-02-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Neon Lemmy Koopa on 2009-02-18
**UPDATE: As of Ubuntu 9.10, this tutorial is no longer valid.  I would update it, but I no longer have the HTC Fuze.  My apologies for the inconvenience.**

This is a tutorial showing folks how to tether AT&T's Fuze phone (AT&T version of HTC's Touch Pro) to Ubuntu Linux via USB.  It is a little different from tethering a regular Windows Mobile phone to Ubuntu.  This describes the steps to do so.  I am mainly writing this tutorial out of my many hardships of getting this to work.  Most of this tutorial is stuff I figured out myself, however one part is taken from [this post]("http://ubuntuforums.org/showpost.php?p=5888254&postcount=1").

To tether the Fuze to Ubuntu Linux, 3 things need to be done:

[LIST]
[*]Crack the phone so that any connection can be shared
[*]Create a connection on the phone other than AT&T's MEdia Net
[*]Mod usb-rndis-lite to allow connection from Fuze
[/LIST]
Please note that this tutorial is ONLY for the HTC Fuze on the AT&T (USA) Network.  For other HTC Touch devices (such as the Diamond or the Touch Pro), please refer to [this post]("http://ubuntuforums.org/showpost.php?p=5888254&postcount=1").

This tutorial is done under Ubuntu Linux 8.10 aka Intrepid Ibex with software up-to-date (according to the update manager).  It is also recommended that you have an unlimited data plan with AT&T.  Tethering plan is recommended but not required.

Let's go.

[SIZE=5]_**PART I: Allow any connection on phone to be shared**_[/SIZE]

AT&T has modded the registry of the Fuze so that ONLY folks with dedicated tethering plans can tether.  If you have a tethering plan with AT&T, please move on to part 2.  Otherwise complete this step.

[LIST=1]
[*]Download a registry editor for Windows Mobile.  I recommend [PHM Registry Editor for Pocket PC]("http://download.majerus.net/RegEdit/regedit.Mrln_ARM.CAB").  This links directly to the install file, so I would recommend downloading this to the phone.
[*]Open File Explorer (Start > Programs > Tools > File Explorer) and navigate to where you saved the install file.  Install it by tapping it once.
[*]Once it installs, open it.  It should be in Start > Programs.
[*]Navigate to HKEY_LOCAL_MACHINE/Comm/InternetSharing/Settings.
[*]You will notice a key in settings called "ForceCellConnection".  Delete it.
[*]That's it.  Any connection can be used for tethering.  Verify this by opening Internet Sharing and seeing that there are two combo boxes (one for PC Connection and one for Network Connection)
[/LIST]
[SIZE=5]_**PART II: Create a connection alternative to MEdia Net**_[/SIZE]

AT&T configures the Fuze's network slightly differently from its other WinMo phones.  I don't know how, but when tethering with it's MEdia Net connection, I can never seem to log on in Ubuntu.  This wasn't a problem on my Windows box, but that box ain't my main box.  Anyway this step is rather simple.

[LIST=1]
[*]On your phone, go to Start > Settings and tap on the connections tab.  Open Wireless Manager and make sure that Data Connection is turned *_**OFF**_*.
[*]Close Wireless Manager and go into Connections.  You should see "MEdia Net" and "My Work Network".  Under MEdia Net, tap "Manage existing connections".
[*]You should see a radio botton labled "MEdia Net".  Tap and hold it to bring up the menu and select "Delete"
[*]Now tap the "New" Button.  In the dialog that comes up, enter a name for your connection.  This name will be the name you select in Internet Sharing later.  From the combo box below it, select "Cellular Line (GPRS, 3G)".  Tap Next.
[*]Leave the Access Point Name box blank.  Tap Next.  Leave those boxes blank as well and tap finish.
[*]If you did all right, you should be able to get on the web.  Verify this by opening Opera on the Fuze.  If web pages load, it worked.
[/LIST]
[SIZE=5]_**PART III: Mod usb-rndis-lite to allow Fuze connection**_[/SIZE]
 
This is a mod to Ubuntu now.  Not the phone.  Apparently HTC phones have some issues tethering to Ubuntu.  This is usually due to rndis failing with some packets exceeding error.  Here we will modify and recompile the source code for usb-rndis-lite to (I think) ignore that error.  The source for this part is [here]("http://ubuntuforums.org/showpost.php?p=5888254&postcount=1").

[LIST=1]
[*]Open up a terminal and do this:
```
sudo apt-get install subversion
```This will install subversion, which is needed to get the latest version of usb-rndis-lite.
[*]Using that same terminal, do this:
```
svn co http://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite
```This will download the latest code of usb-rndis-lite.
[*]Still in the terminal, move into the folder by doing this:
```
cd usb-rndis-lite
```
[*]Terminal again, open the source file we are going to edit by doing this:
```
gedit rndis_host.c
```
[*]Around line 524, find the following code
```
       if (tmp < dev->hard_mtu) {
        dev_err(&intf->dev,
            "dev can't take %u byte packets (max %u)\n",
            dev->hard_mtu, tmp);
        goto fail;
    }
```and change it to this:
```
       if (tmp < dev->hard_mtu) {
        dev_err(&intf->dev,
            "dev can't take %u byte packets (max %u)\n",
            dev->hard_mtu, tmp);
        retval = -EINVAL;  
                /* goto fail;*/
    }
```Save and close the file
[*]Returning to the terminal, type the commands in this order to compile and install it:
```
make
sudo ./clean.sh
sudo make install
```
[/LIST]
Now that the steps are completed, verify everything worked by plugging your Fuze into your preferred USB port.  Open the Internet Sharing app on the Fuze (somewhere in Start > Programs), select USB for PC Connection and the name of the network you typed earlier for Network Connection, and tap Connect.  Ubuntu should see and connect to the phone, and you should be able to browse the web, get email, IM, and so on.  

From this point on, all you should need to do is open Internet Sharing, select the right things and hit "Connect" to connect.

_**ONE THING TO NOTE:**_ updating usb-rndis-lite will break this.  To fix it, just repeat part 3 and your good to go.

That should be all.  I am willing to help anyone with problems.  Also please post any ways you think will improve this tutorial.

---

### Post by binbash on 2009-02-20
Thanks for the tutorial!!

---

### Post by cleatus99 on 2009-02-23
I've Hard Reset, like 4 times now everytime I try to remove the conenction for media net, my opera stops working?

My Tilt Worked Plug & play with 8.10 on my laptop, this fuze is driving me up the wall. :confused:

---

### Post by Neon Lemmy Koopa on 2009-02-23
You shouldn't have to hard reset.  The steps are described exactly as I did them.

What do you mean by opera stops working?  How does it stop working?  does it not open? freeze? not load web pages?  You gotta give me more info to work with so I can help you.

---

### Post by cleatus99 on 2009-02-27
If I make the mods to the phone, Opera will not browse.... it doesn't get the data connection properly.

So I do a Hard Reset, re-install my apps etc...


Wht I am confused about is my tilt worked plug and play with Ubuntu 8.10, now my Fuze.... Set to internet sharing & connected USB it will do google searches, but will not access any page with graphics. Kind of like the new HTC Fuze (aka Raphael) has a larger packet size or something that Ubuntu doesn't understand....

I did the Subversion and tried to reconfigure the rndis-lite....
but now I can't even surf the google.com search page with Ubuntu.

Thanks for the help

---

### Post by cleatus99 on 2009-02-27
ok when running make i get
```

root@dv9200:/home/cleatus99/usb-rndis-lite# make
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/cleatus99/usb-rndis-lite modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/cleatus99/usb-rndis-lite/rndis_host.o
/home/cleatus99/usb-rndis-lite/rndis_host.c: In function ‘rndis_bind’:
/home/cleatus99/usb-rndis-lite/rndis_host.c:524: error: expected ‘)’ before ‘hard_mtu’
/home/cleatus99/usb-rndis-lite/rndis_host.c:525: error: stray ‘\342’ in program
/home/cleatus99/usb-rndis-lite/rndis_host.c:525: error: stray ‘\200’ in program
/home/cleatus99/usb-rndis-lite/rndis_host.c:525: error: stray ‘\234’ in program
/home/cleatus99/usb-rndis-lite/rndis_host.c:525: error: expected ‘)’ before ‘dev’
/home/cleatus99/usb-rndis-lite/rndis_host.c:525: error: stray ‘\342’ in program
/home/cleatus99/usb-rndis-lite/rndis_host.c:525: error: stray ‘\200’ in program
/home/cleatus99/usb-rndis-lite/rndis_host.c:525: error: stray ‘\231’ in program
/home/cleatus99/usb-rndis-lite/rndis_host.c:525: error: stray ‘\’ in program
/home/cleatus99/usb-rndis-lite/rndis_host.c:525: error: stray ‘\342’ in program
/home/cleatus99/usb-rndis-lite/rndis_host.c:525: error: stray ‘\200’ in program
/home/cleatus99/usb-rndis-lite/rndis_host.c:525: error: stray ‘\235’ in program
/home/cleatus99/usb-rndis-lite/rndis_host.c:525: warning: too few arguments for format
/home/cleatus99/usb-rndis-lite/rndis_host.c: In function ‘rndis_tx_fixup’:
/home/cleatus99/usb-rndis-lite/rndis_host.c:663: warning: assignment makes integer from pointer without a cast
make[2]: *** [/home/cleatus99/usb-rndis-lite/rndis_host.o] Error 1
make[1]: *** [_module_/home/cleatus99/usb-rndis-lite] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [default] Error 2
root@dv9200:/home/cleatus99/usb-rndis-lite# 

```

Fuze Info
ROM version: 1.95.502.5 WWE
ROM date: 10/20/08
Radio Version: 1.02.25.32
Protocol version: 52.39c.25.22U

Computer 
Linux HP dv9200 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

---

### Post by mbarvian on 2009-02-28
great tutorial!!

I have an old Tilt, but it worked well :)

now how about syncing with Evolution? :P

thanks again man

---

### Post by Neon Lemmy Koopa on 2009-03-03
@cleatus: looking at that output, it appears you may have made a mistake in modifying the code.  I have attached the source file rndis_host.c to this post. Extract the file and replace the version you have with it one.  I have already modified it myself so just compile again and see what happens.

regarding your issues with the phone, you are creating another connection after deleting MEdia Net, correct?  You have to create that separate connection for this to work.  Also, this is a rare case, but go back into Wireless Manager once you're done and turn Data Connection on.  The fuze will normally start the connection when you open opera, but do it anyway.

See what happens with that.

@mbarvian: I posted a tutorial on how to sync Windows Mobile 6 with evolution [here]("http://ubuntuforums.org/showthread.php?t=1035920") though some have reported some problems regarding HTC Touch devices.  Worth a try though, no? ;)

---

### Post by cleatus99 on 2009-03-04
thanks Worked Great!!!! 

I don't know what what wrong I just copied & replaced that section of code... it's like a comment was off or something....

I wonder can you submit that to get it installed in the next release of Ubuntu?

AT&T HTC FUZE Tethered Ubuntu Intrepid Ibex 8.10

Download Speed: 915 kbps (114.4 KB/sec transfer rate)
Upload Speed: 554 kbps (69.3 KB/sec transfer rate)

---

### Post by Neon Lemmy Koopa on 2009-03-04
glad to hear that it worked.  Happy to help.

As for submitting this into Ubuntu, there isn't really much to submit, seeing that 2 out of the 3 steps here regard the phone.

Also, if you are in an area with REALLY good 3G coverage, you can get a download rate of up to 197 kb/sec.  That's the highest I've seen.

---

### Post by cleatus99 on 2009-03-04
My speed with AT&T HSPDA & HTC FUZE
Download Speed: 2362 kbps (295.3 KB/sec transfer rate)
Upload Speed: 1164 kbps (145.5 KB/sec transfer rate)


Faster than my DSL

---

### Post by LOL you said 1337 on 2009-04-17
Great article!  However, my fuze never really connects during internet sharing, it just says Check USB cable connection. and unbuntu doesn't act like it sees the phone at all.  Any guidance would be helpful.

---

### Post by Neon Lemmy Koopa on 2009-04-17
> **LOL you said 1337 said:**
> Great article!  However, my fuze never really connects during internet sharing, it just says Check USB cable connection. and unbuntu doesn't act like it sees the phone at all.  Any guidance would be helpful.
I had that too.  Not really a big problem.  When it says Check USB Cable Connection disconnect the phone and reconnect it and it should work.

---

### Post by williambrab on 2009-05-07
Hey, great post.  I finally got everything working, sort of.  I can browse the web using Sea Monkey, but Firefox doesn't seem to be able to use the Fuze as the modem.  I ifconfig when the phone is connected and get rndis0 to show a valid IP address.  I can ping yahoo.com and get responses. I prefer Firefox, but can use Sea Monkey in the meantime.  Any ideas that would fix this small issue?

Another small issue is that the rndis0 does not show up in the Gnome Network Manager or show that a connection exists when using the rndis0 modem.  I am using Ubuntu 9.04 Jaunty with Gnome as my window manager.  Any command line outputs needed will be posted following a reply.

---

### Post by cleatus99 on 2009-11-20
Ok so I made the mistake of upgrading to 9.10, everything is hosed including not being able to tether HTC FUZE Ubuntu 9.10. I am running a HP DV9000 I tried to re-run the SVN and no dice get erros during make.

---

### Post by Neon Lemmy Koopa on 2009-11-22
I think 9.10 uses a newer version of rndis that is no longer compatible with this tutorial.  I tried to do it too, and I also received the make error.

Have you tried just doing steps 1 &2 and then plugging in and starting internet sharing?

---

### Post by cleatus99 on 2009-12-10
I've tried several different things, I am certain it is a packet size handling issue, cause if it's a basic page, it works. If it has graphics or flash etc. Grinds to a halt.....

---

### Post by harrisupstate on 2009-12-13
Hi all,

Any ideas on what we should do if we've upgraded to 9.10?  My AT&T Tilt's USB tether connection stopped working, as of 9.04 actually, I'm pretty sure.

The error I'm getting is "device not managed" under the section "Wired Networks (HTC Generic RNDIS)".  So it appears that Ubuntu sees my device, but it won't let me connect.  I can connect with synce, by the way...

Thanks in advance!
Harris

---

### Post by cleatus99 on 2009-12-13
Actually, I gave up. Mine did work with 9.04, using the steps above. I tried the WiFi Router app from XDA for the fuze, and it wouldn't work with the stock ROM, so I re-flashed my FUZE with the NATF 5.7 ROM from NATF.... So now I can use the Fuze as a WiFi mobile hot spot... Not a solution, but a do-able work around.

---

