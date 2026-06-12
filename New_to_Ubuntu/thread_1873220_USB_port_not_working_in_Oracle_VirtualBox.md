---
title: "USB port not working in Oracle VirtualBox"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by Ymurti on 2011-11-01
I have Ubuntu 11.10 and I have installed Oracle VM VirtualBox.
I installed windows 7 in VirtualBox but the USB port is not working in windows 7 only with Ubuntu. I do have the "Extension Pack" of VM VirtualBox installed. Someone please can help me? :(

---

### Post by shan109 on 2011-11-01
I'm having the same problem with XP. I thought that when i installed the extension, it would detect my USB devices, but nothing happened. I have vitualbox 4.1.2. Apparently there is a 4.1.4 update but I cannot install it since it says in the Software Center that it is in conflict with my currently installed Virtualbox. (downloaded a deb file from vitualbox website)

I'm still hesitating to install 4.1.4 because I'm not sure if my XP machine would be preserved if I upgraded, or if the USB problem would be solved. (the worst that could happen is that my XP machine would get deleted and the USB devices would still not function.)

I'm planning to sync my iphone with itunes from VB, I have done it before but now it just can't detect the device.  

(sorry for my poor English)

---

### Post by anewguy on 2011-11-01
Be sure you have set up at least 1 USB filter.  Just do an add of a filter but don't put anything in it.  This allows all USB devices.  Also, since I've been running the newer version for a while I'm not sure how far back it goes, but it used to be you had to download the PUEL version from Oracle (with the new there is just a single version) to have USB access.  The version from the repositories was the open-source version and did not have USB support.

I would think you should be able to save off all of your current vb files, remove your current virtualbox, then download and install the new version from Oracle.  Be sure to download the extension pack as well.  Once installed, you should be able to restore your saved vb files and open your existing vm's.

Dave ;)

---

### Post by haqking on 2011-11-01
you need to make sure you are in the vboxusers group

```
sudo usermod -a -G vboxusers username 
```

or do it from user accounts

---

### Post by Ymurti on 2011-11-01
I tried everything and still it is not working.:(

---

### Post by haqking on 2011-11-01
> **Ymurti said:**
> I tried everything and still it is not working.:(

so you have the latest Vbox install 4.1.4 ?

Extensions pack ?

You are in the vboxusers group ?

You plug in your device and it does not show up on the Vbox Devices menu ? (you need to plug device in, go to Vbox VM devices menu and choose USB device then it should mount in the VM)

You have a USB filter setup ?

---

### Post by Ymurti on 2011-11-01
> **haqking said:**
> so you have the latest Vbox install 4.1.4 ?

Extensions pack ?

You are in the vboxusers group ?

You plug in your device and it does not show up on the Vbox Devices menu ? (you need to plug device in, go to Vbox VM devices menu and choose USB device then it should mount in the VM)

You have a USB filter setup ?

Dear haqking,  I do have the latest Vbox 4.1.4.
I do have the Extensions pack.
I am not sure if I am in the vboxusers group. Can you please give a step by step way of checking it? Sorry I am a neophyte.
- Vbox Devices menu - That is another problem. I can not see the Devices menu when I am using the guest system. Attached is a screenshot.
Yes I have a USB filter, I did not fill up it, I left it empty.

---

### Post by haqking on 2011-11-01
> **Ymurti said:**
> Dear haqking,  I do have the latest Vbox 4.1.4.
I do have the Extensions pack.
I am not sure if I am in the vboxusers group. Can you please give a step by step way of checking it? Sorry I am a neophyte.
- Vbox Devices menu - That is another problem. I can not see the Devices menu when I am using the guest system. Attached is a screenshot.
Yes I have a USB filter, I did not fill up it, I left it empty.

use user accounts or from command line

however i posted in post #4 how to add yourself (replacing username with your username)

Do you usually see the window title bar or are you having compiz issues ?

is that VM window movable or snapped to the top right ?

You probably need to to sort out your compiz/windows issues first.

Anyways you need to go to top left  of VM and choose devices menu (see attachment) and then from that menu you can choose what USB device you wish to use in your VM

---

### Post by Ymurti on 2011-11-01
however i posted in post #4 how to add yourself (replacing username with your username)

I DID THAT (SORRY I AM USING CAPITAL LETTERS TO DIFFERENTIATE)

Do you usually see the window title bar or are you having compiz issues ?

I NEVER COULD SEE THE WINDOW TITLE BAR. I AM CERTAINLY HAVING COMPIZ ISSUES.

is that VM window movable or snapped to the top right ?

IT IS SNAPPED TO THE TOP RIGHT, I CAN NOT MOVE IT.

You probably need to to sort out your compiz/windows issues first.

I AGREE WITH YOU (PLEASE HELP)

Anyways you need to go to top left of VM and choose devices menu (see attachment) and then from that menu you can choose what USB device you wish to use in your VM.

I CAN NOT SEE THE DEVICES MENU.

---

### Post by JKyleOKC on 2011-11-01
> **Ymurti said:**
> I CAN NOT SEE THE DEVICES MENU.This appears to be a frequent problem with the Unity system of newer Ubuntu versions; the title bar of a running program overwrites the program's menu bar, making use of the program difficult if not impossible!

Fortunately, VirtualBox has a CLI utility called VBoxManage that allows you to do everything from a command line, which helps when the user interface is obscured. Bring up the Virtual Device Manager itself (VirtualBox) and click its "Help" option, then find VBoxManager in the table of contents and read away. It will tell you much more than you want to know, but there's a "list devices" option that can get you on your way.

The actual VM you have already created will survive an update, but you have to manually remove the existing copy of VirtualBox before the new version will install. For some reason, Oracle has removed the feature that used to be present, to automatically remove a conflicting package after asking your permission to do so! I just went from a 4.0 installation to 4.1.4 yesterday, with no trouble at all after doing the manual removal via Synaptic.

If using VBoxManage seems too dangerous for you, try selecting "Ubuntu Classic" from the screen that asks for your password when you log into the system. This will keep Unity from getting in the way, which should allow you to see the VBox menu bar and select your devices. Hopefully this "helpful" feature of Unity will be corrected someday soon. I'm using Xubuntu so it has not yet affected me, but I see many complaints about it on the forum.

---

### Post by Ymurti on 2011-11-03
Thank You all for responding my thread. The problem is solved. I have created a new VM and installed Windows XP and now I can see the "Devices" and use my USB

---

### Post by IPEX-731BA5DD06 on 2013-01-11
Virtual box 4.2.6

Running USB DEVICES.

To run usb devices, you need to install the extended pack, for your version.

Now you need to enable a USB FILTER, under settings (top right, cog icon) go to usb devices and enable a filter, as well as USB 2.0 support. Now just don't enable 1, Tried and failed many times, as I have 6 ports, and a 4 port hub connected to one port, and I was [SIZE=4]*_**EXTREMELY FRUSTRATED**_*[/SIZE]. I enabled [s]9[/s] 13 ports. :twisted:

And lo and behold, it synchronised my HARMONY 300 remote control.


*Insert rant about windows, hardware, harmony web site support, life in general*

Yeah me \\:D/

---

### Post by squakie on 2013-01-11
> **IPEX-731BA5DD06 said:**
> Virtual box 4.2.6
 
Running USB DEVICES.
 
To run usb devices, you need to install the extended pack, for your version.
 
Now you need to enable a USB FILTER, under settings (top right, cog icon) go to usb devices and enable a filter, as well as USB 2.0 support. Now just don't enable 1, Tried and failed many times, as I have 6 ports, and a 4 port hub connected to one port, and I was [SIZE=4]*_**EXTREMELY FRUSTRATED**_*[/SIZE]. I enabled 9 ports. :twisted:
 
And lo and behold, it synchronised my HARMONY 300 remote control.
 
 
*Insert rant about windows, hardware, harmony web site support, life in general*
 
Yeah me \\:D/
 
And hence why the OP was advised to be sure the pack was installed early in this thread. The filter was also covered previously.
 
But the biggest thing is that this is an old thread.  Best to open a new one *if* you have a problem yet.  If you have your problem solved then there's probably no need to comment or open a new thread.

---

### Post by lisati on 2013-01-12
Whoops, old thread from 2011 brought back to life!

Closed: a lot can change in a year.

---

