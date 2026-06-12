---
title: "Ubuntu Performance Issue, Nautilus"
date: 2014-02-02
forum: New to Ubuntu
---

### Post by chirag4 on 2014-02-02
Hello,

I am new to Ubuntu.

I recently installed Ubuntu 12.04 in my PC But I am facing Performance Issues with Ubuntu.

Problems occurs like when I open File Manager it will take too much time to open like wise.

Need to solve it urgently.

Thank You.

---

### Post by jondog154 on 2014-02-02
This could be caused by a dying hard drive or many things... Please click the gear on the top right hand of your screen and then about pc and input your specs to us.

Will try my best to help you where I can. I'm new to linux myself was a long time windows power user and have coded in c# for sometime.

please open system monitor and watch Resources for a bit. Try to view a video maybe even two while doing this and report that back thanks :).

---

### Post by chirag4 on 2014-02-02
This is my system configuration :
[http://imgur.com/RNks693](http://imgur.com/RNks693)

What should i Check in Resources Tab in system monitor??

---

### Post by jondog154 on 2014-02-03
Yes that is where it will show cpu and ram being used by the os.

Check how much ram and cpu is being hogged up.

---

### Post by chirag4 on 2014-02-03
Statistics of CPU and RAM Usage : 

CPU-1 : Avg. 25%
CPU-2 : Avg. 30%

Ram : 1.2 GiB (67.2%) of 1.9 GiB
Swap : 118.4 GiB (6.0%) of 1.9 GiB

---

### Post by chirag4 on 2014-02-03
That's with nothing else running?? Or with a video or background programs?

Yes i am using currently NetBeans,Google Chrome and Rhythmbox.

---

### Post by jondog154 on 2014-02-03
I know this seems sickening welcome to the world of computers. Well this sounds like a driver issue or like I said a hard drive issue. When a hard drive starts to die sometime it makes the rest of your pc work harder to carry it. It's hard for data to be pulled from the disk and takes it for ever......... to do anything. Now don't freak out just yet I suggest to do some looking up on Google for any known issues with your cpu and linux. I also think you should run a test on your hard disk.

First thing I would do is test your hard disk there is a tool for this built into the os. Search your os for disks and then click on the disk your os is installed on and at the top right you will see a gear click on it. Then go to smart data and self testing run a long test and this can take a long time depends on if your drive is in good shape or not. Then if that all comes back good try to find anything on Google about your hardware and linux I will look when I can and try to report back to you! Hope things go well for you man enjoy LInux

Oh and by the way it is a known issue that you tube videos or anything that uses Adobe flash lags. It is nothing to do with Linux not that I have heard. Your pc may use high ram and cpu while watching a flash video hopefully this issue will be fixed soon.

[http://www.intel.com/p/en_US/support/highlights/processors/pentium](http://www.intel.com/p/en_US/support/highlights/processors/pentium)

---

### Post by PotatoHead007 on 2014-02-03
Recently someone was having similar issues, and i asked him to install drivers for his graphics card, and that worked. 
What graphics card do you have?

---

### Post by chirag4 on 2014-02-03
This is my tech help deal get out of here potato ;) I will be on for a few can help ya find drivers for him :)

Yes it was heavy

This is screenshot from disk utility:
[http://imgur.com/O7T1fzo](http://imgur.com/O7T1fzo)

---

### Post by PotatoHead007 on 2014-02-03
lol jondog154 ok lol :P Just follow up on the drivers :P I'll leave ya :)

---

### Post by chirag4 on 2014-02-03
How do i know which graphics driver should i install???

---

### Post by mörgæs on 2014-02-03
> **jondog154 said:**
> This is my tech help deal get out of here potato ;) I will be on for a few can help ya find drivers for him :)

There's no such thing as 'my' thread, with or without smileys.

---

### Post by jondog154 on 2014-02-03
The main thing like I said before is check that hard drive out before you go driver hopping. The drives that are loaded when you install Linux are in most cases really good for Intel. It just is hard to think this is a drive issue. Did you build this pc yourself?

Sorry I'm a joking kind of guy was hoping to work with him about helping Chirag out. Didn't mean to run him off...

Well is your hard drive a ssd or hdd?

If it's a ssd don't fool with testing it if a ssd dies it just dies no slowing just nothing a hdd will try to hold on since it has moving parts.

---

### Post by chirag4 on 2014-02-03
Yes i build it my self.

How do i check that whether my hard drive is ssd or hdd??

---

### Post by jondog154 on 2014-02-03
Well you said you built your pc when you put it together was the hard drive big and heavy or was it small light and kind of thin?

Then it was a hdd so please open a search and try and find something called Disks. Find your drive within Disks and the gear at the very top right click it and go into the option smart data and self testing. At the bottom left hand side of this page you will see start self test. Run a extended test.

I need to head in for the night my friend. You can add me on skype if you want anymore of my help later I will check back in here when I can. I hope your test comes back A ok on your hard drive. Maybe someone smarter then me will help ya out. I'm just a old windows service tech trying to learn a new os as well. Good luck man! p.s skype name is jondog154 same as on here feel free to add me on anything steam what every you want............

Oh they changed this in 13.10 which is what I'm on sorry told you wrong!

Well it seems your drive is in good shape! How much you can trust that I don't know I use a boot up cd called hirens to test my disks has a lot of old dos tools in it.

I would Google search around for this. Like the guy that was in here before asked before I pissed him off.... Do your have a graphics card in your pc?

---

### Post by chirag4 on 2014-02-03
No there is no graphics card in my pc.

---

### Post by PotatoHead007 on 2014-02-03
> **jondog154 said:**
> I would Google search around for this. Like the guy that was in here before asked before I pissed him off.... Do your have a graphics card in your pc?

lol you didn't **** me off xD I just stood back a bit. No offense taken.
@chirag4, to check for a graphics card, try this

```


sudo lshw -c display


```

Just to speed things along :) Post output.

---

### Post by chirag4 on 2014-02-03
Output of the command is :

 ```
*-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:fe000000-fe3fffff memory:c0000000-cfffffff ioport:f000(size=64)
```

---

### Post by PotatoHead007 on 2014-02-03
jeepers.... i do not have much experience with Intel processors, although i have one. Will try using this link: [http://www.ubuntuupdates.org/package/xorg-edgers/precise/main/base/xserver-xorg-video-intel](http://www.ubuntuupdates.org/package/xorg-edgers/precise/main/base/xserver-xorg-video-intel) to update my intel, and will tell you what has happened. Will post feedback in a little while :)

**EDIT: **I did not do what i said, because i have to update my system first(450MB and my internet is sooooo slow). Always make sure you updated your system first:

```

sudo apt-get update
sudo apt-get upgrade

```

Then you can try this:

```

sudo apt-get install xserver-xorg-video-intel

```

This download and install the intel driver. Please note that i have not done this, i can not guaranty that this will not mess up your PC. Please, if you do this, backup your files.

---

### Post by mörgæs on 2014-02-03
A good first test before adding PPA's and new drivers is simply comparing Nautilus to another file manager, say Thunar. Any difference in speed?

```
sudo apt-get install thunar
```

---

### Post by jondog154 on 2014-02-03
Good morning friend I told you I would check in. Has any of these steps helped your issue at all?

---

### Post by bc.haynes on 2014-02-03
Would it help to:
```
sudo apt-get update
sudo apt-get upgrade
```
?

EDIT: I was on an earlier page when I posted this. Sorry.

---

### Post by ManyBeers on 2014-02-03
Try this. It worked for me

I thought I'd just post a bit of info regarding thunar and network gvfs cuasing very slow first time opening due to setting up the network.

If you edit /usr/share/gvfs/mounts/network.mount and change it from:


```
[Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
AutoMount=true
```

to

Code:

```
[Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
AutoMount=false
```

it will make opening up thunar very quick again even for the first time. If you want the smb browsing you just click on the network:/// link in thyunar and it will then do the browsing search which takes a bit.

From this thread:[http://ubuntuforums.org/showthread.php?t=1939729](http://ubuntuforums.org/showthread.php?t=1939729)

---

### Post by chirag4 on 2014-02-04
Good Morning to all My Friends.

Thanks for helping on this issue.

The issue resolved by installing the graphics driver.

Now the PC Works fine as expected.

Thanks all for helping.

---

### Post by mörgæs on 2014-02-04
Good, please mark the thread 'solved'.

---

