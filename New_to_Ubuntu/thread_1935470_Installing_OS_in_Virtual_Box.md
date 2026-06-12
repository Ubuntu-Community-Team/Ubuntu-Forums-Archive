---
title: "Installing OS in Virtual Box"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by daniell59 on 2012-03-04
I am in the process of installing windows in Ubuntu using Virtual Box. I reached a point in which I do not know how to proceed.
Please see image.

Any assistance will be appreciated.

---

### Post by synaptix on 2012-03-04
I've gotten that before, however I didn't notice any loss of functionality from it.

---

### Post by CharlesA on 2012-03-04
You just need to add yourself to the vboxusers group if you want to use USB devices with the virtual machine.

---

### Post by baumanno on 2012-03-04
It only means that in your VM you won't be able to use USB devices such as external drives or memory sticks. If you don't plan on doing this, you'll be fine, but if you do want to be able to use them, do as the dialog suggests and add your user to the vboxusers group:

[EDIT: the following was edited according to Dangertux' reply. Thx for clarifying!]
```

$ usermod -g vboxusers your_username

```

then check whether all is cool by
```

$ id your_user | grep vboxusers

```

You should see the vboxusers-group highlighted.

Cheers

---

### Post by Dangertux on 2012-03-04
To fix this just add your user to the supplemental group vboxusers by doing the following.

```

sudo usermod -g vboxusers yourusername

```Hope this helps.

Please note that the above useradd command with -G is innapropriate for usermod as G (capital) will force vboxusers to be the primary group of the user you're adding. Which will limit your functionality , the lowercase -g flag will APPEND an additional group.

---

### Post by daniell59 on 2012-03-04
> **Dangertux said:**
> To fix this just add your user to the supplemental group vboxusers by doing the following.

```

sudo usermod -g vboxusers yourusername

```Hope this helps.

Please note that the above useradd command with -G is innapropriate for usermod as G (capital) will force vboxusers to be the primary group of the user you're adding. Which will limit your functionality , the lowercase -g flag will APPEND an additional group.

I am sorry to admit it, but I am confused. Is the username the name that I sign in as?

---

### Post by baumanno on 2012-03-04
> **daniell59 said:**
> I am sorry to admit it, but I am confused. Is the username the name that I sign in as?

Yes, that should be the normal user you log in as. If you're unsure who you are, the Terminal will tell you:

```
$ whoami
```

---

### Post by irishrover on 2012-03-04
you have gotten further than I have. Virtual box wont detect my CD.

---

### Post by daniell59 on 2012-03-04
> **baumanno said:**
> Yes, that should be the normal user you log in as. If you're unsure who you are, the Terminal will tell you:

```
$ whoami
```

Command not found is what I got.

---

### Post by CharlesA on 2012-03-04
You run it without the $.

```
whoami
```

---

### Post by daniell59 on 2012-03-04
> **CharlesA said:**
> You run it without the $.

```
whoami
```

At least I now know who I am.

By the way, that is one of my favorite poems.

---

### Post by CharlesA on 2012-03-04
Heh, so now you know what user to add to the vboxusers group. :)

---

### Post by baumanno on 2012-03-04
One question off-topic:
Is it common around here to omit the "$" when referring to shell-commands? I always thought it made things a little clearer.

---

### Post by daniell59 on 2012-03-04
No matter what I do, I son't seem to be able to enable the USB.

---

### Post by CharlesA on 2012-03-04
> **baumanno said:**
> One question off-topic:
Is it common around here to omit the "$" when referring to shell-commands? I always thought it made things a little clearer.

It's generally omitted because we can use code tags here and it makes it easier to copy/paste.

> **daniell59 said:**
> No matter what I do, I son't seem to be able to enable the USB.

Run this please:

```
id $USER | grep vboxusers
```

---

### Post by daniell59 on 2012-03-04
> **CharlesA said:**
> It's generally omitted because we can use code tags here and it makes it easier to copy/paste.



Run this please:

```
id $USER | grep vboxusers
```

This is the result

daniel@daniel-desktop:~$ id $USER | grep vboxusers
uid=1000(daniel) gid=124(vboxusers) groups=124(vboxusers),4(adm),20(dialout),24(cdrom),46(plugdev),104(lpadmin),115(admin),120(sambashare)
daniel@daniel-deskto

---

### Post by CharlesA on 2012-03-04
Ok, reboot and USB should work fine.

---

### Post by daniell59 on 2012-03-04
For some reason, when I re-booted, some of my BIOS setting were affected. I had to go into the BIOS and change them back.

---

### Post by CharlesA on 2012-03-04
Adding yourself to another group would not modify the BIOS in any way.

---

### Post by daniell59 on 2012-03-04
> **CharlesA said:**
> Adding yourself to another group would not modify the BIOS in any way.

When I re-booted I got a message to the effect that my overclocking had failed, and if I wanted to go back to the default setting. I never attempted to overclock. I agreed, then I went into the BIOS and changed the timing, the frequency and the voltage of the memory.All I can do it to report the facts, I cannot interpret them however.Your help was invaluable and very much appreciated. It is now working.

---

### Post by CharlesA on 2012-03-04
It probably detected something was unstable. If you changed the voltage/timing/frequency that the memory runs at that might be the cause of the message.

Glad you got it working in any case.

---

### Post by daniell59 on 2012-03-04
> **CharlesA said:**
> It probably detected something was unstable. If you changed the voltage/timing/frequency that the memory runs at that might be the cause of the message.

Glad you got it working in any case.

When I first build the machine it would often freeze. Spoke to the MB manufacturer. The MB did not do well with automatically choosing the correct setting for the memory. It was necessary to do it manually. Once done, the problem was solved.

---

### Post by daniell59 on 2012-03-04
I successfully installed the Windows into Virtual Box. I plugged in a Flash Drive. Is there anyway that I can access the flash drive in the virtual Windows OS?

Thanks

---

### Post by CharlesA on 2012-03-04
You have to tell vbox to use the USB device.

[https://www.virtualbox.org/manual/ch03.html#idp11188688](https://www.virtualbox.org/manual/ch03.html#idp11188688)

---

### Post by daniell59 on 2012-03-04
> **CharlesA said:**
> You have to tell vbox to use the USB device.

[https://www.virtualbox.org/manual/ch03.html#idp11188688](https://www.virtualbox.org/manual/ch03.html#idp11188688)

Thanks

---

### Post by thane1 on 2012-03-04
One other point to consider.  You may have already done this, but do you have the Oracle VM VirtualBox Extension Pack installed on the host?  It is required for usb to work in Vbox.

---

### Post by daniell59 on 2012-03-05
> **thane1 said:**
> One other point to consider.  You may have already done this, but do you have the Oracle VM VirtualBox Extension Pack installed on the host?  It is required for usb to work in Vbox.

I am not sure whether I have it installed on the host. How do I check?
I think that I installed it with the terminal.

---

### Post by baumanno on 2012-03-05
You can find the most recent one here (this will go immediately to the download) [http://download.virtualbox.org/virtualbox/4.1.8/Oracle_VM_VirtualBox_Extension_Pack-4.1.8-75467.vbox-extpack]("http://download.virtualbox.org/virtualbox/4.1.8/Oracle_VM_VirtualBox_Extension_Pack-4.1.8-75467.vbox-extpack")

Then, in your Download-folder, just double-click the file to install it via VirtualBox

Oh, in case your using an version prior to 4.1.8 please go here:[https://www.virtualbox.org/wiki/Downloads]("https://www.virtualbox.org/wiki/Downloads")
You'll see the paragraph regarding the Extension Pack, that should help you.

---

### Post by daniell59 on 2012-03-05
> **baumanno said:**
> You can find the most recent one here (this will go immediately to the download) [http://download.virtualbox.org/virtualbox/4.1.8/Oracle_VM_VirtualBox_Extension_Pack-4.1.8-75467.vbox-extpack]("http://download.virtualbox.org/virtualbox/4.1.8/Oracle_VM_VirtualBox_Extension_Pack-4.1.8-75467.vbox-extpack")

It says that I already have a later version installed. 
I want to be able to see the flash drive in the virtual Windows OS.

---

### Post by baumanno on 2012-03-05
Go to File --> Global Options --> Additional Packages (or similar, I'm not on an English system), if you see the packet there you're fine.

Have you tried the following:
Click on the cogwheel to edit the virtual machine.
In the USB-tab on the left, are both USB checkboxes selected? One should be 'enable USB Controller' and the other 'enable USB 2.0 Controller'.
Then try adding the device manually by clicking on the USB plug-icon with the green plus and selecting it from the list of devices that pops out (the flash drive has to be connected).

Were you able to use the drive outside the VM?

---

### Post by daniell59 on 2012-03-05
See Image

---

### Post by baumanno on 2012-03-05
Well that's really all that you need... I remember my drives taking sort of 3-4 minutes until the Windows guest recognised and initialised them. 

I'm at a loss here, sorry :confused:

---

### Post by daniell59 on 2012-03-05
> **baumanno said:**
> Well that's really all that you need... I remember my drives taking sort of 3-4 minutes until the Windows guest recognised and initialised them. 

I'm at a loss here, sorry :confused:

Thanks

---

### Post by daniell59 on 2012-03-05
Hopefully this new image will give somebody enough information to help.

Thanks in advance

---

### Post by baumanno on 2012-03-05
Did you install the Guest Additions in the guest (double click on the "drive")?

---

### Post by daniell59 on 2012-03-05
> **baumanno said:**
> Did you install the Guest Additions in the guest (double click on the "drive")?

I have done so several times. It goes through the installation, yet I still cannot see the flash drive in the Windows.

---

### Post by pootan on 2012-03-05
Ok you have installed Guest additions on both host and guest. Now did you go devices in the top tool menu of the and see there any usb devices you can tick?

[IMG]http://friendlydrupal.com/files/screencasts_screenshots/vboxdevelopment_part1_figure00014.jpg[/IMG]

You can see in the image above USB Devices. If you find your device there tick it and restart the guest.

---

### Post by daniell59 on 2012-03-05
> **pootan said:**
> Ok you have installed Guest additions on both host and guest. Now did you go devices in the top tool menu of the and see there any usb devices you can tick?

[IMG]http://friendlydrupal.com/files/screencasts_screenshots/vboxdevelopment_part1_figure00014.jpg[/IMG]

You can see in the image above USB Devices. If you find your device there tick it and restart the guest.

I see the flash drive in the devices, but when I go to virtual XP and check my computer, it is not there.

Thanks for the assistance

---

### Post by pootan on 2012-03-05
Ok I'm thinking something from when I used XP before. In Windows XP:

[LIST=1]
[*]Click **Start on the taskbar**, click **Run**, type compmgmt.msc, and then click **OK**.
[*]In the console tree, click **Disk Management**.


Can you see your drive there? If so, you need to right click it and assign a drive letter. That's all I can really think of so sorry if it doesn't help.
[/LIST]

---

### Post by ixtok on 2012-03-05
Isn't it the virtualbox "extension pack" which must be installed for usb devices to work? It can be downloaded from the virtualbox site and has to match the version of virtualbox used. I think the guest additions helps with things like screen resolution and file sharing.

---

### Post by CharlesA on 2012-03-05
If you haven't created a filter yet, you need to do that before booting the guest OS.

---

### Post by daniell59 on 2012-03-06
> **CharlesA said:**
> If you haven't created a filter yet, you need to do that before booting the guest OS.

I still cannot understand why the flash drive does not show in the virtual XP.
AS before, thanks again.

---

### Post by daniell59 on 2012-03-06
I am getting closer, but not there yet.
The flash drive shows in the task bar.
What I want is to be able to access it in the virtual XP.
In XP I look for it in my computer, but it is not there.

---

### Post by Ms. Daisy on 2012-03-06
I had trouble sharing files as well. Here's what I did to get it to work. Hope it's helpful to you.

[http://ubuntuforums.org/showthread.php?t=1916076](http://ubuntuforums.org/showthread.php?t=1916076)

Also here's the [virtualbox manual]("http://dlc.sun.com.edgesuite.net/virtualbox/4.1.8/UserManual.pdf"). A lot of VB is intuitive but some of it is not (like sharing files).

---

### Post by daniell59 on 2012-03-06
> **Ms. Daisy said:**
> I had trouble sharing files as well. Here's what I did to get it to work. Hope it's helpful to you.

[http://ubuntuforums.org/showthread.php?t=1916076](http://ubuntuforums.org/showthread.php?t=1916076)

Also here's the [virtualbox manual]("http://dlc.sun.com.edgesuite.net/virtualbox/4.1.8/UserManual.pdf"). A lot of VB is intuitive but some of it is not (like sharing files).

Thanks,

I will have to go over the manual later in the day.

---

### Post by JKyleOKC on 2012-03-06
> **daniell59 said:**
> I see the flash drive in the devices, but when I go to virtual XP and check my computer, it is not there.When you do this, is there a check mark by the flash drive? If there isn't, select the drive and one should appear. Soon after that you should hear the "clunk" sound that XP makes when it detects a flash drive, and get the usual XP series of dialogs about installing a new device. Click through them and you should be in business.

Also, when you plug the flash drive in, you will probably get a File Manager display of its contents in Ubuntu even before you get any reaction at all from XP. You need to click the Unmount option in the file manager (I use Xubuntu's Thunar, not Nautilus, so your wording may be different) to make the drive available to VBox.

And finally, you need to create a single, empty, USB filter in the VBox settings dialog where you checked the two USB boxes. Just click the "add" button there, and click through the OK buttons. This enables the auto-detection capabilities of vbox.

Others may have already given you these tidbits; I've not yet read the entire thread. However I have nine XP and Win2K VMs set up on this machine, and USB works on all of them. These are the things I had to do to make this happen.

---

### Post by daniell59 on 2012-03-06
> **JKyleOKC said:**
> When you do this, is there a check mark by the flash drive? If there isn't, select the drive and one should appear. Soon after that you should hear the "clunk" sound that XP makes when it detects a flash drive, and get the usual XP series of dialogs about installing a new device. Click through them and you should be in business.

Also, when you plug the flash drive in, you will probably get a File Manager display of its contents in Ubuntu even before you get any reaction at all from XP. You need to click the Unmount option in the file manager (I use Xubuntu's Thunar, not Nautilus, so your wording may be different) to make the drive available to VBox.

And finally, you need to create a single, empty, USB filter in the VBox settings dialog where you checked the two USB boxes. Just click the "add" button there, and click through the OK buttons. This enables the auto-detection capabilities of vbox.

Others may have already given you these tidbits; I've not yet read the entire thread. However I have nine XP and Win2K VMs set up on this machine, and USB works on all of them. These are the things I had to do to make this happen.

There was no clunk sound.
I ejected the drive. Is that the same as unmounting it?
I made a single empty USB filter. I am not there yet.

And thanks for your effort on my behalf.

---

### Post by JKyleOKC on 2012-03-06
Does it have the check mark?

I don't know whether the Nautilus "Eject" command does the same as Thunar's "Unmount" so can't comment on that.

Since the drive shows up in the "Devices" menu, that means that vbox is detecting it. If it's mounted by Ubuntu, though, vbox might be locked out from accessing it. Check your "places" in Ubuntu to see whether it's showing there; if it is, that could be the problem but someone else will have to chime in with the details of how to release it...

---

### Post by baumanno on 2012-03-07
Hya,

to unmount the drive, what I did was this:

```

mount

```

lists the mounted filesystems. Where your flashdrive gets mounted at depends on your setup, my external drive is in /dev/sdb1 for example. But seeing as Ubuntu creates a mountpoint in /media for external devices, you should get half-decent results by running

```
mount | grep /media
```

There, locate what looks like your drive, and find the device node; it looks something like this: /dev/sdXY, with X being a lowercase letter and Y being an arabic number.

Then, with the device node figured out, run
```
sudo umount /dev/node_name
```
which should unmount the drive. But i daresay, i doubt this will make it available for Win... 

Could it be a driver-issue perhaps? Don't these Sandisk Cruzers have some sort of Autostart-stuff on them? Perhaps thats preventing the whole thing from working... 

Just some thoughts.

---

### Post by daniell59 on 2012-03-07
> **baumanno said:**
> Hya,

to unmount the drive, what I did was this:

```

mount

```

lists the mounted filesystems. Where your flashdrive gets mounted at depends on your setup, my external drive is in /dev/sdb1 for example. But seeing as Ubuntu creates a mountpoint in /media for external devices, you should get half-decent results by running

```
mount | grep /media
```

There, locate what looks like your drive, and find the device node; it looks something like this: /dev/sdXY, with X being a lowercase letter and Y being an arabic number.

Then, with the device node figured out, run
```
sudo umount /dev/node_name
```
which should unmount the drive. But i daresay, i doubt this will make it available for Win... 

Could it be a driver-issue perhaps? Don't these Sandisk Cruzers have some sort of Autostart-stuff on them? Perhaps thats preventing the whole thing from working... 

Just some thoughts.

The flash drive works everywhere else.
Thanks for the input.
I think that the problem has me beat.

---

