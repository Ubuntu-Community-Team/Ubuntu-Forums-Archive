---
title: "Slitaz question"
date: 2009-01-31
forum: Other OS Talk
---

### Post by DeadRobot on 2009-01-31
I was trying to get my wifi working in Slitaz.  I went to the netbox manager and clicked on the wifi tab.

But what do I put in all the boxes? I know the network name and the password but in which boxes do I enter that information?

Also, I was trying to install a package.  The instructions said to use "make", so I typed make in to xterm but it said the command make was not found.  How do I install the package then if make is not found?

---

### Post by init1 on 2009-01-31
> **DeadRobot said:**
> I was trying to get my wifi working in Slitaz.  I went to the netbox manager and clicked on the wifi tab.

But what do I put in all the boxes? I know the network name and the password but in which boxes do I enter that information?

Also, I was trying to install a package.  The instructions said to use "make", so I typed make in to xterm but it said the command make was not found.  How do I install the package then if make is not found?
It looks like you were trying to install a source package. SliTaz doesn't have a compiler, so that won't work. You'll have to find a binary version, or compile it with another distro and copy it over to your SliTaz partition.
**Edit:** See below

---

### Post by smartboyathome on 2009-01-31
> **init1 said:**
> It looks like you were trying to install a source package. SliTaz doesn't have a compiler, so that won't work. You'll have to find a binary version, or compile it with another distro and copy it over to your SliTaz partition.

Oh yeah, then how does [this work]("http://www.slitaz.org/en/doc/cookbook/wok-tools.html"), then? Seriously, I was looking into Slitaz, it'd be a bummer if I couldn't compile from source. :(

---

### Post by init1 on 2009-01-31
> **smartboyathome said:**
> Oh yeah, then how does [this work]("http://www.slitaz.org/en/doc/cookbook/wok-tools.html"), then? Seriously, I was looking into Slitaz, it'd be a bummer if I couldn't compile from source. :(
gcc isn't installed by default, but it can be installed from the repos.
So, in order to compile the package, you'll need to install the toolchain
```

tazpkg recharge
tazpkg get-install slitaz-toolchain

```
Then, make should work.

---

### Post by cardinals_fan on 2009-01-31
> **smartboyathome said:**
> Oh yeah, then how does [this work]("http://www.slitaz.org/en/doc/cookbook/wok-tools.html"), then? Seriously, I was looking into Slitaz, it'd be a bummer if I couldn't compile from source. :(
You can absolutely compile from source on SliTaz, but not out of the box.  Do you really expect a compiler for 28 MB? ;)

@OP: What version of SliTaz are you using?  You need wireless_tools, linux-wireless, and linux-crypto installed (default on Cooking 20081231).

---

### Post by DeadRobot on 2009-02-01
Im using SliTaz GNU/Linux cooking-20081231.

So do I need to install wireless_tools, linux-wireless, and linux-crypto?
And if I need to how do I do it without internet?

---

### Post by snowpine on 2009-02-01
> **DeadRobot said:**
> Im using SliTaz GNU/Linux cooking-20081231.

So do I need to install wireless_tools, linux-wireless, and linux-crypto?
And if I need to how do I do it without internet?

Slitaz 20081231 includes the wireless tools.

Here is an easy (but slightly outdated) guide to wireless: [http://wiki.slitaz.org/doku.php?id=lang:en:wifi_easy](http://wiki.slitaz.org/doku.php?id=lang:en:wifi_easy)

---

### Post by DeadRobot on 2009-02-01
Thanks for the link snowpine!

I tried doing
modprobe ath_pci

but it said it couldnt find the ath_pci module.  Where can I get that from?

---

### Post by cardinals_fan on 2009-02-01
> **DeadRobot said:**
> Im using SliTaz GNU/Linux cooking-20081231.

So do I need to install wireless_tools, linux-wireless, and linux-crypto?
And if I need to how do I do it without internet?

> **DeadRobot said:**
> Thanks for the link snowpine!

I tried doing
modprobe ath_pci

but it said it couldnt find the ath_pci module.  Where can I get that from?
[This]("http://forum.slitaz.org/viewtopic.php?pid=6635#p6635") might be useful.

---

### Post by DeadRobot on 2009-02-01
> **cardinals_fan said:**
> [This]("http://forum.slitaz.org/viewtopic.php?pid=6635#p6635") might be useful.

Ok thanks!

It says to install madwifi, and in the readme in madwifi it says to use make.  And I know someone above said you have to use gcc to get make, but can I get gcc without an internet connection?

---

### Post by cardinals_fan on 2009-02-01
This might also apply: [http://forum.slitaz.org/viewtopic.php?pid=6809](http://forum.slitaz.org/viewtopic.php?pid=6809)

EDIT: There is a madwifi tazpkg: [ftp://download.tuxfamily.org/slitaz/packages/cooking/madwifi-r3861_2.6.25.5.tazpkg](ftp://download.tuxfamily.org/slitaz/packages/cooking/madwifi-r3861_2.6.25.5.tazpkg)

---

### Post by DeadRobot on 2009-02-01
Thanks!  Once I have the .tazpkg, how do I install it?

---

### Post by cardinals_fan on 2009-02-01
> **DeadRobot said:**
> Thanks!  Once I have the .tazpkg, how do I install it?
Open the directory with the file in a terminal (either right-click in PCManFM or use cd) and (as root) run "tazpkg install filename".

---

### Post by DeadRobot on 2009-02-01
Ok so i would do:

tazpkg install madwifi-r3861_2.6.25.5.tazpkg
and then
modprobe ath_pci

?

---

### Post by cardinals_fan on 2009-02-01
Probably "modprobe madwifi"...

---

### Post by DeadRobot on 2009-02-01
Thanks.

And that will install the necessary things for the AR242x?

What do I enter into netbox, under the wifi tab, for key, interface, and all that stuff?

---

### Post by cardinals_fan on 2009-02-01
> **DeadRobot said:**
> 
What do I enter into netbox, under the wifi tab, for key, interface, and all that stuff?
Click "Wifi", enter the interface name (probably ath0, click "Status" for a list).  Enter your essid and key and click "Start".  The "Kernel Modules" tab provides some useful tools as well.

---

### Post by DeadRobot on 2009-02-01
But what exactly is my essid and key?

Is essid the name of the network and key the password?

---

### Post by cardinals_fan on 2009-02-01
> **DeadRobot said:**
> But what exactly is my essid and key?

Is essid the name of the network and key the password?
Yes.

---

### Post by DeadRobot on 2009-02-01
*sigh*

I installed madwifi, did modprobe madwifi, modprobe ath_pci, and modprobe ath5k, then entered my information into the wifi tab and clicked start and it didnt work.  

I dont know what to do now. :(

---

### Post by cardinals_fan on 2009-02-01
> **DeadRobot said:**
> *sigh*

I installed madwifi, did modprobe madwifi, modprobe ath_pci, and modprobe ath5k, then entered my information into the wifi tab and clicked start and it didnt work.  

I dont know what to do now. :(
Open a root shell and post the output of "ifconfig" and "iwconfig".

---

### Post by smartboyathome on 2009-02-01
The output of ifconfig -a might be more helpful than ifconfig alone, since it includes all interfaces.

---

