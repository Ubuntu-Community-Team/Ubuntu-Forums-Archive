---
title: "Howto: Install VirtualBox and integrate it with Compiz"
date: 2007-11-05
forum: Outdated Tutorials &amp; Tips
---

### Post by P4man on 2007-11-05
[SIZE="4"]Purpose of this how-to:[/SIZE]

Install and configure VirtualBox, set up a (virtual)  windows environment, and integrate it seamlessly with your Ubuntu desktop using Compiz. 

[[IMG]http://img155.imageshack.us/img155/9128/cubelargewm8.th.png[/IMG]](http://img155.imageshack.us/my.php?image=cubelargewm8.png) [[IMG]http://img206.imageshack.us/img206/5053/exposesmallns6.png[/IMG]](http://www.youtube.com/watch?v=Kxk6oFqMJVY)


[SIZE="4"]Requirements[/SIZE]

Prerequisites: 
- working Ubuntu installation 
- Windows installation disks (not recovery disks!)
- optional: working composite video for the Compiz part

Tested with: 
- Ubuntu 7.10,
- VirtualBox 1.5.2 (both binary and OSE),
- Windows XP.


[SIZE="4"]Step 1 download and install VirtualBox[/SIZE]



**Downloading**

There are two versions of VirtualBox, the OSE (opensource edition) and the closed source, binary one. The OSE edition is the one you will find in  "add/remove programs", but it lacks some features of the binary one, most notably, USB support. For this reason, I would advice using the binary. The binary version can be found in the repositories or downloaded it here (for gutsy)::
[http://www.virtualbox.org/download/1.5.2/virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb](http://www.virtualbox.org/download/1.5.2/virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb)

**Installation**

After installing, you will get a warning that you need to add users to the vboxusers group. Let's do so now:

System menu > administration > users and groups > manage groups

Select the “vboxusers” group > properties > check any users you want to be able to use VB.

Now log out, and log in again for these changes to become effective.
[B]
Configure VirtualBox[/B]

Run VirtualBox from Applications > System Tools

Fill out the registration form, and create a new VM, give it a name, select the appropriate OS Type for what you intend to install (XP in my case):

Select the amount of RAM you want to give to your VM. For XP you will need at least 256 Mb RAM, depending how much RAM you have and on what windows applications you intend to run 500Mb or more is probably better:
[B]
Create a new virtual hard disk[/B]

Select Dynamically expanding. Give it a name and size.
[COLOR="Red"]Important![/COLOR] you will not be able to increase the size after creating it (although you can add other virtual drives). Since unused space on your virtual drive will take no room on your real hard disk, make this disk large enough! Click finish.

**Prepare booting your VM**

Click on “Settings” to modify some properties of your VM. If you use Gutsy, you may now get this error: "Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND)":

To fix it, we need to enable usbfs. Open a terminal and type:

```
sudo gedit /etc/init.d/mountdevsubfs.sh
```

Find this part:

```
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb
```


remove the # sign in front of the last 4 lines so it looks like this:

```

    # Magic to make /proc/bus/usb work
    #
    mkdir -p /dev/bus/usb/.usbfs
    domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount --rbind /dev/bus/usb /proc/bus/usb
```

Reboot Ubuntu.

Restart virtualbox, select your VM, then click settings. You should have no error messages now.

Go to CD-DVD-ROM, and select the “mount CD/DVD drive” checkbox. Verify that the device is correct((/dev/cdrom in my case).

You probably also want to enable sound in audio /enable audio. ALSA is the most likely choice. If you want any USB devices to be available to windows, go to USB, enable it and click the tiny “add from..” button, select the device(s) you need.

Setting up some shared folders is a good idea too, these will be network drives available in your VM. 

Now insert your windows installation disk (not a recovery disk!) in the cd drive, and start your virtual machine. Windows setup should boot from the CD.

Install windows as you would normally.

If the VM "steals" your mouse and keyboard, the default key to release them is the right control key on your keyboard. You can change that, but we will change this behaviour later anyway.

[SIZE="4"]Step 2 configure your virtual machine[/SIZE]

At this point, you should have a working virtual windows in a window. You may have to do some "windows stuff" like activating (/"patching") windows. Your sound should work, as well as your network. 

If you installed Vista rather than XP, please refer to the virtualbox manual how to enable your network. The manual can be found here:
[http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)
[B]
Guest additions[/B]

Now lets install the VirtualBox Guest additions by selecting it from the "Devices" menu in your VirtualBox VM window/

If nothing happens automatically, then in the VM, go to "my computer" and doubleclick on the CD icon. This should launch the wizard to install some drivers that make integration with the host OS much better. Follow the wizard, accept the license, ignore the unsigned driver warnings, etc. At the end, reboot the virtual machine.

Now you can go in and out of the VM with your mouse without it being trapped inside the VM. You can also resize the window, and the VM will automatically adjust the resolution.

**Network drives**

You can also map the network drives now, so your VM has access to your real disks. They are available through windows networking. Just create a new network location through the windows wizard and browse to the VirtualBox shared folders (assuming you set them up earlier):

You can also open a command prompt (yes windows has them too! :) and type:

```
net use x: \\vboxsvr\sharename
```

where x: is the drive letter you want to assign, and sharename is the name you gave to the location in VirtualBox configuration earlier.

**Time for some magic**

In the VM, open a window, like IE, or any app, it doesnt matter. Make sure it is neither minimized,nor maximized, then press right-control + L. This activates "seamless mode", which basically means putting the VM in fullscreen and no longer drawing the windows desktop, instead you get to see your Ubuntu desktop. If your windows taskbar gets hidden behind the Gnome panels, try pressing rctrl+L again twice.

There is at least one problem with this seamless mode: it doesn't work with all windows minimized (or no open windows at all). You have to keep at least one windows app open and visible or the screen will go black or corrupt. If this happens, rctrl+L is still your friend. Untill this problem is solved, you can work around it by installing a desklet style app that always shows a clock or something. I run calculator on startup and hide it behind it the taskbar :)

[SIZE="4"]Finishing Touches[/size]

I am going to assume you have accelerated videodrivers working with compositing enabled. There are hundreds of how-to's to achieve that, and in most cases its almost automatic.

Then configuring Compiz is something I'm not going to explain in detail either. The short version is:

```
sudo apt-get install compiz-config-settings-manager
```

Then go to system > preferences > appearance > visual effects > custom

In the preferences enable the 3D cube and cube rotation plugins, configure them as you see fit.

**Wallpaper**

If you've seen my video, you may have noticed I have different wallpapers on different sides of the cube. This is something normally not supported, but there are ways to achieve it.

First, let me say I just bumped into this tutorial:
[http://ubuntuforums.org/showthread.php?t=600909]("http://ubuntuforums.org/showthread.php?t=600909")

I have not tried this yet, and it does look tricky and intimidating, but feel free to give it a try and let me know if it worked.

The method I used is far simpeler, but does have a drawback: you loose your desktop icons. If you don't mind that, then all you have to do is first disable nautilus painting the desktop. In a terminal type:

```
gconf-editor
```

Browse to apps > nautilus > preferences > show_desktop and unselect it.

Next, we define the wallpapers in Compiz setting manager.
Go to Desktop Cube > Appearance
And in background images add the ones you want:

If you liked the one's I used, you can download them from here:
[http://www.gnome-look.org/content/show.php/Ubuntu+Dragon+%2B+Windows+Dragon+wallpaper?content=69464]("http://www.gnome-look.org/content/show.php/Ubuntu+Dragon+%2B+Windows+Dragon+wallpaper?content=69464")

**Launching of VirtualBox**

An easy way to launch VirtualBox is creating a starter on your panel (right click on it > add to panel > custom launcher) , or even adding it in your session list if you want to start it automatically each session. The command to use is simply:

```
VBoxManage startvm name_of_your_virtual_machine
```

(please note the uppercase letters)

That's all follks!

---

### Post by SonnySee on 2007-11-30
This is exactly what I was looking for.
You made it crazy easy for me to do it.
Now, to try using multiple backgrounds.
Thanks again.

---

### Post by maka on 2007-12-01
great howto! thanks much. fixed all the problems i had.

---

### Post by de_valentin on 2007-12-03
Thanks for the Howto, everything worked out great except for the last line of code .

I get this error when I click the button in the panel

>  Could not launch application
Failed to execute child process "VBoxManage" (No such file or directory)

---

### Post by de_valentin on 2007-12-03
Just figured it out, indeed note the uppercases.
In /usr/bin there was only a vboxmanage and not a VBoxManage so fixed that now I have the quickest loading XP I ever had:lolflag:

---

### Post by sowelie on 2007-12-05
I have virtualbox all working with an install of server 2003, but seamless mode doesn't work, it basically just goes into full screen mode...any suggestions?  Alternatively, i could just use it in full screen mode, but I can't get my native resolution to work in the guest.  Any help is much appreciated.

---

### Post by sowelie on 2007-12-09
For anyone reading this thread, I figured the issue out.  I had installed Virtualbox Guest Additions off of their website, rather than through virtualbox itself (because it did not work the first time).  Once I installed the guest additions through virtualbox everything worked perfectly.

---

### Post by Vinno on 2007-12-10
Your guide seems to be easy enough,

My main reasons would be to use webcam on msn and use adobe photoshop.

My question would be:

**Does virtual box emulate hardware like webcam and etc like a normal windows install? 

**The ram setting installation, if i set say 500 aside for xp, does linux seperate that from ubuntu ram allocation or do they just share my total ram and window can only have so much as i set when needed?

---

### Post by P4man on 2007-12-10
> **Vinno said:**
> Y
**Does virtual box emulate hardware like webcam and etc like a normal windows install? 

Well, yes. You can "pass through" USB devices. That doesn't always work with every device but there is a good chance your webcam will work. You have to select the USB devices you want windows to see in the virtualbox config. Beware though, this option is ONLY available on the binary version, not on the OSE version.

> **The ram setting installation, if i set say 500 aside for xp, does linux seperate that from ubuntu ram allocation or do they just share my total ram and window can only have so much as i set when needed?

AFAK the first. It doesn't support dynamically expanding RAM the way it does for harddisk space. I think it would be extremely hard to make that work

---

### Post by johnnybirdman on 2007-12-13
> **P4man said:**
> 


**Launching of VirtualBox**

An easy way to launch VirtualBox is creating a starter on your panel (right click on it > add to panel > custom launcher) , or even adding it in your session list if you want to start it automatically each session. The command to use is simply:

```
VBoxManage startvm name_of_your_virtual_machine
```

(please note the uppercase letters)

That's all follks!

Is there a way to make it launch to a specific workspace on the cube/wall?

PS: brilliant work, got win2000 up and running with your how to in now time.  xp is next.

---

### Post by mdpalow on 2007-12-18
Your video put a smile on my face. Very well done!

Would love it if you could add to your HowTo a small section that gives us the exact settings you used in Compiz to make it do the things you do.

I've played around with Compiz, but could never get it to work like you. For instance, I can get the cube to show and rotate it, but I can only do that while holding the mouse rollerball down. Once I let go, it snaps back to the screen and no more cube. It looks like you're able to get the cube to show and then do other things before making it snap back to the screen.

I'm going to subscribe to this thread now in hopes you will add the instructions to your original post.

Very well written by the way. I'm going to send to a friend who had problems with his VirtualBox and see if this helps him.

Thanks!

---

### Post by tenchu77491 on 2007-12-20
Will this fully work like a normal Windows? I thought Virtualbox did not support direct rendering, and therefore can not run many games?

---

### Post by P4man on 2007-12-20
> **mdpalow said:**
> Your video put a smile on my face. Very well done!

Would love it if you could add to your HowTo a small section that gives us the exact settings you used in Compiz to make it do the things you do.

I've played around with Compiz, but could never get it to work like you. For instance, I can get the cube to show and rotate it, but I can only do that while holding the mouse rollerball down. Once I let go, it snaps back to the screen and no more cube. It looks like you're able to get the cube to show and then do other things before making it snap back to the screen.

First, install compiz-config-settings-manager:

```
sudo apt-get install compiz-config-settings-manager
```

that gives you a nice gui to configure and tweak everything (system / preferences / advanced desktop efftects settings)

I don't remember the default settings, but to rotate the cube manually, go to the rotate cube plugin and define something to "initiate rotate" (I think). I think by default holding down both mouse buttons while grabbing the desktop does the trick.

If there is any other questions about the compiz-fusion plugins I used in that video, just ask. But having the settings manager will make it easy to find out I think.

---

### Post by P4man on 2007-12-20
> **tenchu77491 said:**
> Will this fully work like a normal Windows? I thought Virtualbox did not support direct rendering, and therefore can not run many games?

Direct rendering appears to work, but you can safely forget about 3D gaming. Virtualbox emulates some Cirrus Logic videocard, so forget about 3D acceleration.

AFAIK, the only way to play windows games on Linux right now is Wine. This may change in a year or so when AMD releases a new CPU that allows virtualization of  IOMMU I/O, essentially meaning the GPU can be used in a VM, unlike now.

---

### Post by olavjunior on 2008-01-22
Do I need to worry about viruses? Just delete the os if I get it, or...?

Anyways, I have a hp dv2130 with built in webcam. When I used the usb-filter to filter existing connections, it found it, and windows was installing it, and it said everything went well. Can't find it though (neither do messenger). Went to HP and downloaded drivers for the cam, installed fine, but still no cam. Any ideas?

---

### Post by P4man on 2008-01-22
(double post)

---

### Post by P4man on 2008-01-22
Yes, you should worry about virusses; your virtual windows will be as vulnerable as a real one, so its a very good idea to run an antivirus on it. 

Also If you create read/write enabled shared network folders to access Linux partitions from windows, a windows virus could cause damage there.

If you don't create (writeable) shared folders, or at least not to anything important  in Linux, your Linux installation ought to be safe from windows virusses, safer even than  dualboot because the virtual windows would not be able to see or damage the physical Linux partitions, something a windows virus in a dual boot configuration theoretically could do.

As for the webcam.. I can't help you there Im afraid. My webcam (logtech fusion) doesn't work at all in VirtualBox either 

BTW, sound playback works fine, but I also haven't managed to get sound recording abilities in Virtualbox. Anyone have an idea ?

---

### Post by TwiceOver on 2008-01-22
This is awesome and I plan to try this when I get home.  I had previously tried VirtualBox but could not find a way to get a real network IP.  It always wanted to NAT the IP of the virtual machines.

Has this been fixed yet?

On a side note... If there were a good financial manager for Linux I could just ditch Windows...  Alas, Microsoft Money is my crutch.

---

### Post by detroit/zero on 2008-02-06
What about Avant Window Navigator, and once I activate the seamless mode, the start bar and the AWN bar cover each other depending on which I last selected. 

Is there any way to have AWN not show on the desktop I plan to use for XP?

An alternative would be to not use seamless mode and have one of the desktops on my cube dedicated to XP at startup, but how can I make it so when the VM is in full-screen mode the compiz commands (for, say, rotating cube faces) are still recognized? As it is, I have to leave the VM window and click somewhere on my Ubuntu desktop so I can rotate cube faces or use any of my preset hotkey combos. This doesn't change if I have the mouse/keyboard integration enabled or not. You don't have to leave a Firefox window, for example, for your compiz commands to still be executed. I know this is a little different, but....

I'm just curious if anybody managed to find a workaround for this yet...

---

### Post by olavjunior on 2008-02-19
I can't play mp3 from shared folders with windows media player. It says the file is missing or something. Any ideas?

---

### Post by Prinssimikko on 2008-02-20
Otherwise it's all going well, but when starting my virtual machine, i get the error:

Unknown error creating VM (VERR_HOSTIF_INIT_FAILED).
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by Prinssimikko on 2008-02-20
Oh, nevermind. i had for some reason selected the network as "host". changing it to "nat" solved the problem! Thanks for the great guide!

---

### Post by mk4umha on 2008-03-05
Does anyone know how to make Virtual Box automagically overlay on top of the Gnome Task bars?

1.5.4 was doing it correctly and I upgraded to 1.5.6 and that's when this problem occurred.

I did a complete remove of 1.5.4 then installed 1.5.6.

---

### Post by timjohn7 on 2008-05-29
I have a strange problem... I have Virtual Box 1.6 up and running fine.  When I start XP I get the nessage requiring activation (30 days limit has passed).  I click yes to activate.  I get a message saying that the copy is already activated.  I press OK.  I get a message saying that this product needs to be activated.

I am in a Microsoft loop.

Please help me out of here!!!! :confused:

---

### Post by P4man on 2008-05-29
You have a bad activation crack. Further discussion about that is not appropriate on this forum, if you have a legal copy, contact MS. If you don't.. well, ask elsewhere ;)

---

### Post by timjohn7 on 2008-05-29
> **P4man said:**
> You have a bad activation crack. Further discussion about that is not appropriate on this forum, if you have a legal copy, contact MS. If you don't.. well, ask elsewhere ;)
Thanks, but I have a legal copy and have not installed or used any cracks.  I am currently dual booting on the same machine with the same legal copy of XP.  I would like to activate again in VB but would like to contact MS over the internet rather than by phone as the local phone support (South Africa) is atrocious.  I cant connect in VB until I get the VB running.

---

### Post by P4man on 2008-05-29
> **timjohn7 said:**
> Thanks, but I have a legal copy and have not installed or used any cracks.  I am currently dual booting on the same machine with the same legal copy of XP.  I would like to activate again in VB but would like to contact MS over the internet rather than by phone as the local phone support (South Africa) is atrocious.  I cant connect in VB until I get the VB running.

You can't activate the same windows copy on two machines. The virtual machine is considered a different computer. You'll need to buy another windows license, give up the dual boot (and you'll still need to contact MS then I think), or be more creative :)

---

### Post by benhur99ph on 2008-06-02
> **sowelie said:**
> I have virtualbox all working with an install of server 2003, but seamless mode doesn't work, it basically just goes into full screen mode...any suggestions?  Alternatively, i could just use it in full screen mode, but I can't get my native resolution to work in the guest.  Any help is much appreciated.

I think you haven't installed the Guest Additions. 
After installing the Guest OS on virtualbox, make sure you are running it on windowed-mode. Click on the Devices button and select the Mount CD/DVDROM. Then choose Mount CD/DVDROM image. Click on the add button and go to /usr/share/virtualbox. You will see there an iso named VBoxGuestAdditions.iso. Select it to mount it and then run it on your Windows XP (which is your guest OS) and install it. After that it will require you to reboot your Guest OS. Do it and when it reboots, the virtualbox graphic driver will be installed and now you can adjust your screen resolution to the right one. Also, seamless mode will be available. Just press "Host_Key" + L. Host key is the right_ctrl by default.

---

### Post by flinstonex on 2009-01-23
You said:
> 
Configure VirtualBox

Run VirtualBox from Applications > System Tools

Fill out the registration form, and create a new VM, give it a name, select the appropriate OS Type for what you intend to install (XP in my case):

Select the amount of RAM you want to give to your VM. For XP you will need at least 256 Mb RAM, depending how much RAM you have and on what windows applications you intend to run 500Mb or more is probably better

Lets say I have 2 gb ram, and i give 500mb to virtualmachine, does that mean i would only have 1.5 left for ubuntu? Or would i still  have 2 gigs for ubuntu, but it would share the 500mb from the 2 gigs only when virtualbox is running?

Please explain, i'm sorta new to ubuntu.

---

### Post by P4man on 2009-01-23
You can not "share" RAM between the host and the guest OS. The guest OS (windows here) is just a program as far as the host OS (ubuntu) is concerned; so if you give the guest 500Mb, it will be 500Mb less the host can use or give. Can't have your cake and eat it I'm afraid :) Short answer: yes ubuntu will only have 1500Mb left (which probably is still much more than you will need)

Now that said, please note this howto is old. Ubuntu has seen one or 2 upgrades, and virtualbox has changed significantly, so  Im not sure how correct it still is. If I find time I'll update it for Ubuntu 8.10 and the current release of virtualbox.

---

### Post by Andre-D on 2009-01-23
> **tenchu77491 said:**
> Will this fully work like a normal Windows? I thought Virtualbox did not support direct rendering, and therefore can not run many games?

VmWare Workstation 6.5 runs DirectX just fine.  - any chance of integrating it ?

---

### Post by Badcam on 2010-09-24
> **detroit/zero said:**
> What about Avant Window Navigator, and once I activate the seamless mode, the start bar and the AWN bar cover each other depending on which I last selected. 

Is there any way to have AWN not show on the desktop I plan to use for XP?

An alternative would be to not use seamless mode and have one of the desktops on my cube dedicated to XP at startup, but how can I make it so when the VM is in full-screen mode the compiz commands (for, say, rotating cube faces) are still recognized? As it is, I have to leave the VM window and click somewhere on my Ubuntu desktop so I can rotate cube faces or use any of my preset hotkey combos. This doesn't change if I have the mouse/keyboard integration enabled or not. You don't have to leave a Firefox window, for example, for your compiz commands to still be executed. I know this is a little different, but....

I'm just curious if anybody managed to find a workaround for this yet...

I too am looking for a full solution to this. I too use AWN. I can get pretty close with Seamless mode and I can still use my Alt-Tab and Alt-Shift Tab (I've changed the key combo from Super to Alt to help with Windows in Compiz and Windows is always keying for the Super (Windows) key) to Switch between windows using Compiz Swift Switcher. It works fairly well, but sometimes stops recognising the Compiz key combo's, so you have to click on another workspace and then Alt-Tab or click back.

---

