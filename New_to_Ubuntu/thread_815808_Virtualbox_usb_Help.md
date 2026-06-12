---
title: "Virtualbox usb Help"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by coubury on 2008-06-02
I have Xp running through VirtualBox (x64 amd)works fine but one thing is annoying me

I have a 3 usb modem [http://www.three.co.uk/personal/products_services_/mobile_broadband_/index.omp](http://www.three.co.uk/personal/products_services_/mobile_broadband_/index.omp)
to connect to the net, virtual box recognizes this as something that can be mounted under the cd/dvd thing in virtualbox settings, (Ubuntu recognizes this as a Mobile_Connect device and has an icon of a disk on the desktop when i boot up) so i thought maybe that would do, so i started xp and mounted it and it installed ok but then when i goto log on it says modem invalid


When i go into usb settigs in virtualbox it says enable usb controller then somthing about filters but nothing about a device were i could pick my 3 usb modem and another thing when i have virtualbox running xp i click devices at the top then usb but no usb devices are picked up to load


Am i missing somthing? do i need to add a usb setting to virtualbox??


I downloaded VB for Ubuntu 7.10 amd x64

Thanks in advance!

---

### Post by bumanie on 2008-06-02
Are you using the binary (free for home use) or ose version of virtualbox? The ose version doesn't have usb support.

---

### Post by HotShotDJ on 2008-06-02
> **coubury said:**
> When i go into usb settigs in virtualbox it says enable usb controller then somthing about filters but nothing about a device were i could pick my 3 usb modem and another thing when i have virtualbox running xp i click devices at the top then usb but no usb devices are picked up to loadUnless the devices are connected when you do this, nothing will appear.

---

### Post by coubury on 2008-06-02
THe binary

---

### Post by coubury on 2008-06-02
> **HotShotDJ said:**
> Unless the devices are connected when you do this, nothing will appear.

the device is connected tho as i be using it for the internet on ubuntu

although ubuntu doesn't recognizes it as a usb device, and it isnt made for linux only windows and mac is possibly why virtualbox doesn't recognize it?

but even still when i mount it when i have VB ON (as i said in my first post thats what VB thinks it is a cd/dvd ) It starts to install on xp but when i goto log in it says its invalid


is there any way i can share the connection between ubuntu and xp?

---

### Post by HotShotDJ on 2008-06-02
> **coubury said:**
> although ubuntu doesn't recognizes it as a usb device, and it isnt made for linux only windows and mac is possibly why virtualbox doesn't recognize it?Possibly...  how about other USB devices... are they working ok through VirtualBox?  If not, I may know the problem, but I don't want to type out the instructions until I know for sure. :)

---

### Post by coubury on 2008-06-02
I ahve a usb pen and its not working :(

---

### Post by HotShotDJ on 2008-06-02
> **coubury said:**
> I ahve a usb pen and its not working :(Ok... just to verify... you have the PUEL version that you downloaded directly from Sun and NOT the ose version in the repository, right?  If that is the case, you probably have a permissions problem.. to correct:

[LIST=1]
[*]Open System --> Administration --> Users and Groups
[*]Unlock the dialog (see "Unlock" button)
[*]Click On "Manage Groups"
[*]Click "Add Groups" and add a group called "usbusers" & write down the Group ID number.
[*]Check off the user(s) that you want to allow usb privilages in VirtualBox
[*]Click "OK" then "Close" then "Close" again.
[*]Open Applications --> Accessories --> Terminal
[*]type "gksudo gedit /etc/fstab" (without quotes)
[*]Add the following two lines to the end of the file:```
# For USB access with Virtualbox
none	/proc/bus/usb	usbfs	devgid=1001,devmode=664	0	0
```
[*]IMPORTANT:  Change "devgid=1001" to whatever number you wrote down in step number 4
[*]Save the file and close.
[*]Reboot your system.  You should now have full access to all USB devices in Virtualbox
[/LIST]

---

### Post by coubury on 2008-06-02
Still not working :(

but we are makeing progress lol


when i start VB and xp loads i goto device at the top then own to usb i can see the usb modem and the flash drive but i cant click them (they aint in bold if you know what i mean)

---

### Post by coubury on 2008-06-02
as a last resort

is there anyway i can share the internet connection?

---

### Post by HotShotDJ on 2008-06-02
> **coubury said:**
> as a last resort

is there anyway i can share the internet connection?If you've got internet connectivity going under Linux, it should automatically be working under VirtualBox..

I should have asked you before... have you installed the Windows Guest Additions yet?  That may solve your problems.

---

### Post by coubury on 2008-06-02
No what does that do?

---

### Post by coubury on 2008-06-02
Im stupid lol your right the internet does work 


why the **** did i not check it first? :lolflag:

---

### Post by HotShotDJ on 2008-06-02
> **coubury said:**
> No what does that do?Well, lets not get into too much detail on that... suffice it to say that it will likely fix the problems you are having. :)  Open VirtualBox and start up Windows.  Once it is booted up, look in the VirtualBox menu for the Devices menu, open it and select "Install Guest Additions" --  if it doesn't start automatically, go into "My Computer" and the Guest Additions should appear as a CD device.  Double click on it to start the installation.  After it is completed the installation, you will reboot the virtual machine.  Now see if you've got USB support and internet.

---

### Post by HotShotDJ on 2008-06-02
> **coubury said:**
> Im stupid lol your right the internet does work 


why the **** did i not check it first? :lolflag:Because, like the rest of us, you, sir, are a geek.  We geeks always look for zebras when horses are the more reasonable answer. :)

---

### Post by coubury on 2008-06-02
:):):)

Cheers mate!

---

### Post by coubury on 2008-06-02
Maybe you can help me with this

I have a wireless card aswell but virtualbox cant recognize it

is there any reason why it doesnt?

---

### Post by HotShotDJ on 2008-06-02
> **coubury said:**
> Maybe you can help me with this

I have a wireless card aswell but virtualbox cant recognize it

is there any reason why it doesnt?Because Virtualbox sets up a VIRTUAL environment.  The guest operating system (Windows, in your case) doesn't see the actual hardware (with a few exceptions), it only see's the VIRTUAL hardware that VirtualBox sets up for it.  For the internet, including Wireless, Virtualbox provides a virtual network card, which, in turn, uses the host OS tcp/ip stack to "talk" to the outside world.

---

### Post by coubury on 2008-06-02
That went  way over my head lol

i see someone commented about getting their wireless acrd working

[http://www.blog.arun-prabha.com/2007/05/21/configuring-virtualbox-for-sharing-and-mouse-control/](http://www.blog.arun-prabha.com/2007/05/21/configuring-virtualbox-for-sharing-and-mouse-control/)

**update
got my wireless working as well. pheww!!!
i had to choose the host interface name which needed to be mapped to the virtual adapter in the settings.


but i havent a clue what they are on about lol

---

### Post by HotShotDJ on 2008-06-02
> **coubury said:**
> **update
got my wireless working as well. pheww!!!
i had to choose the host interface name which needed to be mapped to the virtual adapter in the settings.


but i havent a clue what they are on about lolI understand what they are talking about, but I have no experience doing it.  Is there some reason why you want to do it that way?  If you just get your wireless card up and running in Ubuntu, it will be used by the guest OS (Windows) automagically.  It seems to me that you are making it more difficult than it really is (unless I completely misunderstand what it is you are trying to accomplish).

---

### Post by coubury on 2008-06-02
> **HotShotDJ said:**
> I understand what they are talking about, but I have no experience doing it.  Is there some reason why you want to do it that way?  If you just get your wireless card up and running in Ubuntu, it will be used by the guest OS (Windows) automagically.  It seems to me that you are making it more difficult than it really is (unless I completely misunderstand what it is you are trying to accomplish).


For some starnge reason i cant connect to the internet using my wireless card in ubuntu ebven tho i have the right drivers etc but it connects not a problem with xp

thats why i have to use the 3 usb modem on ubuntu but that has a 3gb download limit a month and my wirelss network is unlimited! so id rather use my Wireless, i only use the usb ,modem for my laptop when im on the move

---

