---
title: "HOWTO: DV Camcorder and /dev/raw1394"
date: 2004-10-31
forum: Outdated Tutorials &amp; Tips
---

### Post by jaboo on 2004-10-31
I am trying to work with kino and my dv camcorder. It was working just fine on Gentoo. The problem is that I am trying to get /dev/raw1394 to show up. When I issue the command tail -f /var/log/messages, I get the following output:

> Oct 31 17:33:00 localhost ieee1394.agent[4751]:      dv1394: loaded successfullyOct 31 17:33:00 localhost kernel: ieee1394: raw1394: /dev/raw1394 device initialized
Oct 31 17:33:00 localhost ieee1394.agent[4751]:      raw1394: loaded successfully
As you can see, raw1394 module gets loaded, and it says /dev/raw1394 device is initialized. However, looking in /dev, I do not see an entry for raw1394. Has anyone else had any experience with firewire devices on Ubuntu, maybe a dv camcorder on /dev/1394? Thanks for any help.

---

### Post by jaboo on 2004-11-01
Well, I did find a solution, but I am not truly satisfied with it as it seems like a dirty hack. I am a former Gentoo user, and their user forums are top notch with some brilliant people. So, I went looking there for an answer, and I stumbled upon a thread that had some interesting info:

> it appears that the raw1394 driver does not yet export info into SYSFS, therefore udev can't create nodes for it.
for now, you can use:
mknod /dev/raw1394 c 171 0
So, I basically edited the /etc/init.d/bootmisc.sh file with the following:
> # Begin Edit. 20041031 RCB - Added to hopefully get the raw1394 devicenode.
mknod /dev/raw1394 c 171 0
chown root:video /dev/raw1394
chmod 666 /dev/raw1394
#End Edit

: exit 0
Of course, this creates a device node called /dev/raw1394 each time I boot the system. It works, but I hope a more elegant solution involving udev can be found in the future.

---

### Post by [S2] on 2005-03-15
this made my dv camera work. thanks for posting the solution.

---

### Post by trash on 2005-03-16
didn't do anything for me:(

---

### Post by trash on 2005-03-19
YAY! Thanks guys, this is the first real progress I've made getting my ibot webcam working.

with the above and 'mknod /dev/video1394 c 171 16' in the bootmisc.sh file it's working... controls in GM don't work but at least now i have an image:). I might also have to add a line to add the device to the 'video' group to give user full control.

edit:
I should also add that i am doing this in hoary with the 'libptdv-plugin' from universe/multi.. for those interested.

---

### Post by rkn on 2005-03-22
What works for me is to add:
raw1394
video1394
to my /etc/modules file.
Once I did this, my device file was created automaticaly by udev.

Bob

---

### Post by trash on 2005-03-22
[QUOTE=rkn]What works for me is to add:
raw1394
video1394
to my /etc/modules file.
Once I did this, my device file was created automaticaly by udev.

Bob[/QUOTE]


Strange, I commented out what I had in my bootmisc.sh file and added what you did to my modules file, rebooted and nothing was created. I no understand!
Are you using a webcam or camcorder, if its a webcam do your image controls in gnomemeeting work? I cannot alter my image at all.

---

### Post by lompolo on 2005-08-20
I have Canon MV20 pal camcorder. Doesn´t work with Kino. When I am trying to capture, Kino says cannot read/write /dev/raw1394.  Group and others have rw-priviledges to /dev/raw1394. When I turn computer on camcorder in play mode, there is some ieee1394 errors.

Help me to get started solving this problem please.

---

### Post by claydoh on 2005-08-20
Take a look at [these posts]("http://ubuntuforums.org/showthread.php?t=56468&highlight=raw1394") and specifically [this link]("http://www.bxlug.be/en/articles/220") found there.

The dev nodes are created but users do not have read/write permissions. This can be changed easily but upon reboot it the permissions are reset. The method described in the second link above solves that problem.

---

### Post by imwithstupid on 2005-08-29
I'm having similar problems.

Samsung D535 plugged into a firewire PCI card.
PCI card is recognized by hardware config stuff in ubuntu.
modified files so modules are loaded at startup for raw and video1394.
kino terminal output when set to raw1394 is:
```
ieee1394io.cc:355: errno: 22 (Invalid argument)
ieee1394io.cc:355: In function "virtual bool raw1394Reader::Open()": "raw1394_set_port( handle, port )" evaluated to -1

```

I don't know what this means...other than the -1 is for error (not 1 for working or 0 for completely off).  Looks like it can't find the port, or open the port?

Any help would be great (and would hopefully help other people too).

---

### Post by lompolo on 2005-09-20
[QUOTE=lompolo]I have Canon MV20 pal camcorder. Doesn´t work with Kino. When I am trying to capture, Kino says cannot read/write /dev/raw1394.  Group and others have rw-priviledges to /dev/raw1394. When I turn computer on camcorder in play mode, there is some ieee1394 errors.[/QUOTE]


I tested with my friend. Camcorder worked in his computer with gentoo. We tested Breezy live in his computer. There was not errors when we tried dmesg. In my computer dmesg gives when camcorder plugged in:
Error parsing configrom for node 0-00:1023
ieee1394: Error parsing configrom for node 0-01:1023
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...  and so on.

I think problem is my hardware. My motherboard is abit as8. It has integrated firewire. Device manager founds Texas Instruments TSB43AB23 IEEE-1394a-2000.

I don't have windows so I don't know if it's working there. Abit as8 bios updates are .exe files so updating bios might be hard.

Any suggestions please.

---

### Post by nmsa on 2006-07-25
apt-cache search dvgrab
install if not installed dvgrab
this will create all devices required by Kino

works on my AMD64 Ubuntu and Kino 0.8.0 with a Sony Camcorder connected via  ieee1394

---

### Post by JOWIROMA on 2006-08-24
**i Got My Jvc Dv Running For Kino But I'm Trying Amsn Webcam Feature And I Get A Message "no Current Devices Installed", Some Help Please!!**

---

### Post by macpointman on 2007-06-13
> **rkn said:**
> What works for me is to add:
raw1394
video1394
to my /etc/modules file.
Once I did this, my device file was created automaticaly by udev.

Bob

Bob,

This one worked like a charm for me.  Thanks for the tip.  Now all I have to do is get my Camcorder to work as a Webcam with Gyachi.  Hopefully Ill find the answer soon.

MacPointMan

---

### Post by pratik5705 on 2007-06-15
Changing the /etc/modules file also worked for me.

I was able to capture video from my JVC GRD650US Handycam on Kububtu running Fiesty via Kino.

However, the captured video was choppy and not smooth?  Any suggestions?

---

### Post by hodenkat on 2008-05-27
> **jaboo said:**
> Well, I did find a solution, but I am not truly satisfied with it as it seems like a dirty hack. I am a former Gentoo user, and their user forums are top notch with some brilliant people. So, I went looking there for an answer, and I stumbled upon a thread that had some interesting info:


So, I basically edited the /etc/init.d/bootmisc.sh file with the following:

Of course, this creates a device node called /dev/raw1394 each time I boot the system. It works, but I hope a more elegant solution involving udev can be found in the future.

This just made Kino fail to open on my system.
The window opens blank and I have to force quit to shut it down.
Didn't work for me but...
Looks like an excellent try though. I hope it helps some people!

---

