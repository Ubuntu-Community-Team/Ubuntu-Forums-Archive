---
title: "Howto: Simple kernel upgrade (Feisty or Edgy) to Gutsy's developing kernel."
date: 2007-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by walkerk on 2007-07-28
This should work for Feisty Fawn and Edgy Eft users. This will install the current developing kernel that will be realeased with Gutsy Gibbon.

[SIZE="5"][COLOR="Green"]Check out my new thread > [Upgrade to 2.6.24]("http://ubuntuforums.org/showthread.php?t=646755")[/COLOR][/SIZE]

**[COLOR=Red]Do not upgrade any packages while you have the Gutsy repository open.[/COLOR]**

[COLOR=Red]Disclaimer:[/COLOR] This is how I successfully upgraded my kernel without having to compile it myself. A couple of users have had issues with this method so be aware that problems can arise. At this point removing the new kernel using the instructions at the end of the post should do the trick, but if it doesn't I take no responsibility. I will monitor this thread to try to help out anyone thats had issues.

*** With that being said, most users have not had any problems and are enjoying the new kernel. Also, this will not remove your current kernels.***

[SIZE=3][COLOR=DarkOrange]**After you've upgraded please reply with your machine Model and specs so that others can benefit :)**[/COLOR][/SIZE]


[SIZE=4]**You can download the script I've attached and do the following:**[/SIZE]

**[COLOR=DarkOrange]kernel.sh[/COLOR]** will upgrade to the current kernel using meta packages, meaning if you run this every week or so it will upgrade your kernel if a new version has been released. Current version is **2.6.22-14**

Move to the directory in which you downloaded the script.. for example:
```
cd /path/to/file/
```make the script executable:
```
chmod +x kernel.py
```run it:
```
sudo python kernel.py
```This installed the new kernel. Enjoy :)



[SIZE=4]**Or you can do it manually...**[/SIZE]

First you need to add the Gutsy repository (this is only temporary to pull the new kernel):
```
echo 'deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted' | sudo tee -a /etc/apt/sources.list
```Now that you've added the repository you need to update:
```
sudo apt-get update
```Next you need to install the new kernel:
```
sudo apt-get -y install linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
```Now that you've pulled the kernel you should remove the Gutsy repository from your sources.list:
```
gksudo gedit /etc/apt/sources.list
```Now you can remove the line or simply comment it out: (It'll be the last line of the file)
```
#deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
```Once again you need to update so that you'll stop pulling updates from the Gutsy repository:
```
sudo apt-get update
```Alright. If you've done all of the above without errors, you've successfully installed 2.6.22-14-generic. Now you need to reboot into the new kernel:
```
sudo reboot
```Enjoy :)

[SIZE=5][COLOR=DarkOrange]Miscellaneous fixes [/COLOR][/SIZE]
> 
**[COLOR=YellowGreen]1. Having issues with your nVidia video cards?[/COLOR]**[COLOR=YellowGreen]
*    > A possible fix: [Look here]("http://ubuntuforums.org/showpost.php?p=3246585&postcount=342")*
*    > Use Envy. Post: [http://ubuntuforums.org/showpost.php?p=3430398&postcount=520](http://ubuntuforums.org/showpost.php?p=3430398&postcount=520) / Envy's [offical website]("http://www.albertomilone.com/nvidia_scripts1.html")*[/COLOR]

**[COLOR=SlateGray]2. Is Nautilus crashing?[/COLOR]**[COLOR=SlateGray]
*    > Update it using the gutsy repository: *[/COLOR]*[Look here]("http://ubuntuforums.org/showpost.php?p=3290551&postcount=396")*

**[COLOR=Blue]3. Are having issues with direct rendering and such with ATI video (specifically 200M chipset)?[/COLOR]**[COLOR=Blue]
*    > Take a look at jamiepluncinski's post: *[/COLOR]*[Here]("http://ubuntuforums.org/showthread.php?p=3136258#post3136258")*


[SIZE=3]**Ok.. Did it hose your box? Too easy.**[/SIZE]

Reboot your computer and at Grub press esc to boot into your last kernel. (probably 2.6.20-16-*)

Remove the installed kernel and then upgrade. 
```
sudo apt-get remove linux-image-2.6.22-14-generic linux-headers-2.6.22-14-generic linux-headers-2.6.22-14 linux-restricted-modules-2.6.22-14-generic linux-ubuntu-modules-2.6.22-14-generic
``````
sudo apt-get upgrade
```
**Updates**
10/08/07: *Cleaned up the network test*
09/20/07: *Added a network test*
09/18/07: *Cleaned up the python script...*
09/08/07: *Updated to python.*
08/12/07: *Added GUI (zenity dialogs) to the script*
08/08/07: *Changed script to look for and install Meta packages*
08/07/07: *Cleaned up kernel.sh*

---

### Post by Blindraven on 2007-07-30
Excellent, Thanks for the info.

One thing though, I notice multiple "old" kernels in my grub that I never use that seem to be placed there after I finish doing major updates, how do i get rid of them? or is that not advisable?

---

### Post by Frostmourne on 2007-07-30
I think it would only be necessary to temporarily add the main and restricted Gutsty repositories, since all the kernel packages come from there. So you would add this line instead:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

I don't think the src line is needed either.

---

### Post by walkerk on 2007-07-31
> **Blindraven said:**
> Excellent, Thanks for the info.

One thing though, I notice multiple "old" kernels in my grub that I never use that seem to be placed there after I finish doing major updates, how do i get rid of them? or is that not advisable?

 you can remove the listings by removing them from /boot/grub/menu.lst..

you can remove them through synaptic (easiest method) or you can delete them by removing them from /boot. though i strong advise you to leave a back up kernel on your system. i actually keep two backups in there..

---

### Post by walkerk on 2007-07-31
> **Frostmourne said:**
> I think it would only be necessary to temporarily add the main and restricted Gutsty repositories, since all the kernel packages come from there. So you would add this line instead:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

I don't think the src line is needed either.

good call.:)

---

### Post by rebegin on 2007-07-31
hey, i'm going to try it now, thanks for the post. anyway, why did you changed the header packae to "linux-headers-2.6.22-8"it doesn't exist to me...?
```
Couldn't find any package whose name or description matched "linux-headers-2.6.22-8"
```
i'll go with the "linux-headers-2.6.22-9" and let you know if it's ok.

---

### Post by walkerk on 2007-07-31
> **rebegin said:**
> hey, i'm going to try it now, thanks for the post. anyway, why did you changed the header packae to "linux-headers-2.6.22-8"it doesn't exist to me...?
```
Couldn't find any package whose name or description matched "linux-headers-2.6.22-8"
```
i'll go with the "linux-headers-2.6.22-9" and let you know if it's ok.

Yep.. Sorry for the confusion. You're right, I missed that one package when I updated the thread. It's fixed now :) 2.6.22-9 works great..

Let me know how it goes..

---

### Post by rebegin on 2007-07-31
i've rebooted to the new kernel (2.6.22-9-generic) and so far everything is working well. thanks again.

---

### Post by jspangler on 2007-07-31
Very cool. It worked like a charm!

---

### Post by walkerk on 2007-07-31
> **rebegin said:**
> i've rebooted to the new kernel (2.6.22-9-generic) and so far everything is working well. thanks again.

> **jspangler said:**
> Very cool. It worked like a charm!

Good to hear guys :)

---

### Post by walkerk on 2007-07-31
Simplified the process for you all.. I added a script to install the kernel.. See the original post.

---

### Post by NikoK on 2007-07-31
> **walkerk said:**
> Simplified the process for you all.. I added a script to install the kernel.. See the original post. Since i am using 686 right now and I use your script to install 386, will my t2060 still be detected as dual core?

---

### Post by walkerk on 2007-07-31
> **NikoK said:**
> Since i am using 686 right now and I use your script to install 386, will my t2060 still be detected as dual core?

this installs the generic kernel not the 386 kernel. i have 686 and generic uses my dual cores.. so the answer is yes :)

---

### Post by walkerk on 2007-07-31
please reply once you've upgraded to let me know all is well. :)

---

### Post by wnelson on 2007-07-31
Can  not wait for an official release of 2.6.23 to come out. Alot of really good changes. Change log too big to list. Go here for listing of changes: [http://kernelnewbies.org/LinuxChanges](http://kernelnewbies.org/LinuxChanges)

---

### Post by andrewsomething on 2007-07-31
Doh! Doesn't work with an AMD Turion 64 X2 Dell Inspiron 1501

```
[0.196000] .. MP-BIOS bug: 8254 timer not connected to IO-APIC
[0.240000] PCI: Cannot allocate region 7 of bridge 0000:00:05.0
[0.240000] PCI: Cannot allocate region 8 of bridge 0000:00:05.0
```

I should have know that since it's a known bug with Gutsy which will be fixed before release. Hopefully in Tribe 4. [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121111](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121111) 

BTW: I didn't even have to manually remove the info from Grub. Did it itself after removing the packages.

Edit: Hummm... Seems to have deleted my custom boot splash. No big deal though...

---

### Post by bogolisk on 2007-08-01
will nvidia-glx-new from feisty work with linux-restricted-modules from gutsy?

nvidia-glx-new from gutsy depends on libc6 2.6!:( feisty version is 2.5!

---

### Post by walkerk on 2007-08-01
> **bogolisk said:**
> will nvidia-glx-new from feisty work with linux-restricted-modules from gutsy?

nvidia-glx-new from gutsy depends on libc6 2.6!:( feisty version is 2.5!

i have 2.6 on my computer though I never upgraded it. the kernel install might have upgraded it.  but nevertheless you can always add libc6 2.6 by yourself after adding the Gutsy repository:

```
sudo apt-get install libc6 libc6-dev
```

**I altered the script for you.. See my original post to download it. :) This will upgrade libc6 to 2.6 and install the kernel**

---

### Post by Jhongy on 2007-08-01
Hello,

Would like to try this, but have a few reservations.

I understand it's easy to just boot up with an older kernel -- but (a big but), what about all the kernel modules I have installed? Had to modify options for sound, ACPI, and several other kernel modules. 

If the new kernel (& I assume the  restricted modules, etc) don't work out, you have to do more than just boot with a different kernel, right? -- can I just use Synaptic to uninstall all the restricted modules, and then re-install the Feisty versions?

---

### Post by walkerk on 2007-08-01
> **Jhongy said:**
> Hello,

Would like to try this, but have a few reservations.

I understand it's easy to just boot up with an older kernel -- but (a big but), what about all the kernel modules I have installed? Had to modify options for sound, ACPI, and several other kernel modules. 

If the new kernel (& I assume the  restricted modules, etc) don't work out, you have to do more than just boot with a different kernel, right? -- can I just use Synaptic to uninstall all the restricted modules, and then re-install the Feisty versions?

This method **will not remove** the restricted modules for your old kernels. It will only add the new kernel (& restricted modules) and enable you to boot into 2.6.22-9-generic.

If it doesn't work out for you, you can simply uninstall the new kernel like I posted (or through Synaptic).. Your old stuff will still be installed and bootable..

I left it up to you to remove your old kernel and modules if you feel the need. I didn't want to strand anyone by deleting their kernels..

---

### Post by magoo on 2007-08-01
hello,

do you know where I can find the kernel config file prior to installing it?

---

### Post by walkerk on 2007-08-01
> **magoo said:**
> hello,

do you know where I can find the kernel config file prior to installing it?

you can download the .deb by adding the -d option (download only) This method won't install the kernel. From here you should be able to dig into it and find the config..

```
sudo apt-get install **-d** linux-backports-modules-2.6.22-9-generic linux-headers-2.6.22-9 linux-headers-2.6.22-9-generic linux-image-2.6.22-9-generic linux-restricted-modules-2.6.22-9-generic linux-ubuntu-modules-2.6.22-9-generic
```

---

### Post by st0nes on 2007-08-01
Thanks Walkerk.  Your instructions worked flawlessly and ended weeks of frustration trying to get sound to work on my new laptop.  Much appreciated.

---

### Post by walkerk on 2007-08-01
> **st0nes said:**
> Thanks Walkerk.  Your instructions worked flawlessly and ended weeks of frustration trying to get sound to work on my new laptop.  Much appreciated.

Good to hear :)

---

### Post by tact on 2007-08-01
The process worked well, no errors, and rebooted into the 2.6.22-9 kernel no problem.

Most things seem to work on the surface.  Did a quick run thru my essential applications.  VMWare server is broken under this kernel.  If I boot back into older kernel VMWare Server works fine.

This is an observation, not a bug report of course.

---

### Post by walkerk on 2007-08-01
> **tact said:**
> The process worked well, no errors, and rebooted into the 2.6.22-9 kernel no problem.

Most things seem to work on the surface.  Did a quick run thru my essential applications.  VMWare server is broken under this kernel.  If I boot back into older kernel VMWare Server works fine.

This is an observation, not a bug report of course.

Glad it worked. As for VMWare, I had a similar issue with VirtualBox. There was a simple solution.. 2 lines in the terminal to configure it to work with the new kernel.. shouldn't be tough w/ VMWare.

---

### Post by lemurian on 2007-08-01
walkerk, thanks for the instructions.  I will use that in my page about [installing Ubuntu on a Compal IFL90]("http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/").  I don't have the machine yet but based on preliminary research, there are a few pieces of hardware that require 2.6.22 to work properly.

---

### Post by Jhongy on 2007-08-02
Worked great for me -- Suspend to RAM finally works on this laptop -- again and again and again :-)


For VMWare -- for me, it breaks on every kernel upgrade. Just need to run the install script again to fix it (however, on occasions, it messes up the guest OSes).

---

### Post by magoo on 2007-08-02
> **walkerk said:**
> you can download the .deb by adding the -d option (download only) This method won't install the kernel. From here you should be able to dig into it and find the config..

```
sudo apt-get install **-d** linux-backports-modules-2.6.22-9-generic linux-headers-2.6.22-9 linux-headers-2.6.22-9-generic linux-image-2.6.22-9-generic linux-restricted-modules-2.6.22-9-generic linux-ubuntu-modules-2.6.22-9-generic
```

thanks,

don't think I am lazy but adding reps just to get a config file...

Could you send me the config file as a PM? It would be awesome.

---

### Post by walkerk on 2007-08-02
> **magoo said:**
> thanks,

don't think I am lazy but adding reps just to get a config file...

Could you send me the config file as a PM? It would be awesome.

Not sure if this is what you're looking for.. It's too large for a PM. Let me know..

---

### Post by fooman on 2007-08-02
everything seems to be working fine here after the update....kubuntu 7.04

thanks walkerk!  :)

---

### Post by walkerk on 2007-08-02
> **Jhongy said:**
> Worked great for me -- Suspend to RAM finally works on this laptop -- again and again and again :-)


For VMWare -- for me, it breaks on every kernel upgrade. Just need to run the install script again to fix it (however, on occasions, it messes up the guest OSes).

> **fooman said:**
> everything seems to be working fine here after the update....kubuntu 7.04

thanks walkerk!  :)

Glad to hear it guys :) Did you guys use the script of did you do it manually? Just curious to see if anyone is using the script or not..

---

### Post by realo on 2007-08-02
Hello world,

The behaviour here is not quite the same as you people.

The install of the new kernel is successful, however, at restart, the kernel just stops at some point in the middle of the reboot.  This occurs always exactly after a message after the USB HID core loading.  Bear in mind that the problem is probably not related to the USB, as I don't know what it is doing next that makes it stop.

Now, this is not a crash, mind you, but the kernel just stops.  I can still switch virtual screens (alt-Fx) and I can type, etc...  but nothing else occurs.

At first , I suspected the 22-9 kernel was somehow having problems with my machine (a toshiba laptop), however I can boot the August 1st Gutsy CD very well, and everything seems to work...!

Anyone else with this problem?  At this point, I am quite curious as to what is going on.

thx

---

### Post by walkerk on 2007-08-02
> **realo said:**
> Hello world,

The behaviour here is not quite the same as you people.

The install of the new kernel is successful, however, at restart, the kernel just stops at some point in the middle of the reboot.  This occurs always exactly after a message after the USB HID core loading.  Bear in mind that the problem is probably not related to the USB, as I don't know what it is doing next that makes it stop.

Now, this is not a crash, mind you, but the kernel just stops.  I can still switch virtual screens (alt-Fx) and I can type, etc...  but nothing else occurs.

At first , I suspected the 22-9 kernel was somehow having problems with my machine (a toshiba laptop), however I can boot the August 1st Gutsy CD very well, and everything seems to work...!

Anyone else with this problem?  At this point, I am quite curious as to what is going on.

thx

in your currently working kernel lets see the output of:
```
uname -r
```

---

### Post by realo on 2007-08-02
2.6.20-16-generic

---

### Post by obavjestenja on 2007-08-02
im new in ubuntu world but this work for me and my wireless work great now:)
i have question : i need to select new kernel every time i restart mu computer ?
thanks !!!

---

### Post by walkerk on 2007-08-02
> **realo said:**
> 2.6.20-16-generic

thats strange. shouldn't have any issues that i can think of. could you try uninstalling the new kernel, reboot and then run the kernel.sh (or kernel_libc6.sh ..updates libc6 aswell, this is what i did)?

I'm about to head out for a couple of hours with the family but I have a few minutes. I'll be back to see if there was any progress..

to remove:
```
sudo apt-get remove linux-backports-modules-2.6.22-9-generic linux-headers-2.6.22-9 linux-headers-2.6.22-9-generic linux-image-2.6.22-9-generic linux-restricted-modules-2.6.22-9-generic linux-ubuntu-modules-2.6.22-9-generic
sudo reboot
```

---

### Post by walkerk on 2007-08-02
> **obavjestenja said:**
> im new in ubuntu world but this work for me and my wireless work great now:)
i have question : i need to select new kernel every time i restart mu computer ?
thanks !!!

No, the default kernel should now be 2.6.22-9-generic. to verify in terminal type
```
uname -r
```

also you can verify by checking your grub menu.lst..
```
gedit /boot/grub/menu.lst
```

Ubuntu, 2.6.22-9-generic should be the first kernel listed.. correct?

---

### Post by obavjestenja on 2007-08-02
> **walkerk said:**
> No, the default kernel should now be 2.6.22-9-generic. to verify in terminal type
```
uname -r
```

also you can verify by checking your grub menu.lst..
```
gedit /boot/grub/menu.lst
```

Ubuntu, 2.6.22-9-generic should be the first kernel listed.. correct?


yes is the first one and one more question : to delete the old kernel or to keep  ?

---

### Post by realo on 2007-08-02
Hello ,

I already did that.  No change.  I can also confirm that I use libc6 version 2.6 :


real@laptop:~/Desktop/Gutsy_Scripts$ ./open_gutsy.sh 
Opening gutsy repository... Password:
... (skipping setup lines)

real@laptop:~/Desktop/Gutsy_Scripts$ sudo apt-get install libc6 libc6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
libc6-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 842 not upgraded.

real@laptop:~/Desktop/Gutsy_Scripts$ ./close_gutsy.sh 
Closing gutsy repositoryRestoring /etc/apt/sources.list

I don't think this is a simple thing to crack, but hopefully I'll prove wrong.

---

### Post by BLTicklemonster on 2007-08-02
The drive I have Feisty installed on is almost totally full for some reason. I don't have a whole lot of programs installed on it, and I purge locale and everything else I can think of, but it's only got like less than a gig left out of 26 gigs. 

I have another drive with Feisty that's not as full, and I want to put gutsy on it, but I would rather do a clean install on it. (I can boot to xp - which not only boots faster, but is way faster than ubuntu regardless of what any naysayers may say nayingly thank you very much - and download and burn a boot cd) My question is, where can I get the download of gutsy? 

Yes, I could just upgrade the other feisty, but I really don't want to do that because of the ever present likelyhood of problems which I just don't care to face.

Is there a straight download for gutsy?

---

### Post by walkerk on 2007-08-02
> **obavjestenja said:**
> yes is the first one and one more question : to delete the old kernel or to keep  ?

I advise you to keep your old kernel around.. Just in case. :) I keep 2 backups..

---

### Post by obavjestenja on 2007-08-02
Thanks for this !!!

---

### Post by walkerk on 2007-08-02
> **BLTicklemonster said:**
> The drive I have Feisty installed on is almost totally full for some reason. I don't have a whole lot of programs installed on it, and I purge locale and everything else I can think of, but it's only got like less than a gig left out of 26 gigs. 

I have another drive with Feisty that's not as full, and I want to put gutsy on it, but I would rather do a clean install on it. (I can boot to xp - which not only boots faster, but is way faster than ubuntu regardless of what any naysayers may say nayingly thank you very much - and download and burn a boot cd) My question is, where can I get the download of gutsy? 

Yes, I could just upgrade the other feisty, but I really don't want to do that because of the ever present likelyhood of problems which I just don't care to face.

Is there a straight download for gutsy?

Sure.. you can download Gutsy Gibbon Tribe 3 but be advised it is in testing still. If it breaks you get to keep both pieces. :) I run it on a vBox.. Enjoy.

[Gutsy Gibbon Tribe 3]("http://www.ubuntu.com/testing/tribe3")

---

### Post by walkerk on 2007-08-02
> **obavjestenja said:**
> Thanks for this !!!

No problem :)

---

### Post by Jhongy on 2007-08-02
> **walkerk said:**
> Glad to hear it guys :) Did you guys use the script of did you do it manually? Just curious to see if anyone is using the script or not..

I just did it manually. BTW the feisty libc6 was already at the latest version before the upgrade.

---

### Post by Gremlinzzz on 2007-08-02
Great job upgraded my kernel  using your directions was very easy and work for me thanks.
:guitar:

---

### Post by fooman on 2007-08-02
> **walkerk said:**
> Glad to hear it guys :) Did you guys use the script of did you do it manually? Just curious to see if anyone is using the script or not..

i used the kernel_libc6.sh script.

i tried this a couple of days ago with the kernel.sh you had posted at that time....but when i rebooted,  the new kernel just kinda hung at some point and would not boot.  it did not crash or anything,  just got hung up and would not respond.  i booted to the previous kernel and followed your steps to undo the changes.  i was going to post about my problem,  but was running out at the time.

anyways,  i tried again this morning using the kernel_libc6.sh and all is working fine now!

thanks again.  :)

---

### Post by BLTicklemonster on 2007-08-02
> **walkerk said:**
> Sure.. you can download Gutsy Gibbon Tribe 3 but be advised it is in testing still. If it breaks you get to keep both pieces. :) I run it on a vBox.. Enjoy.

[Gutsy Gibbon Tribe 3]("http://www.ubuntu.com/testing/tribe3")


Thanks. I don't mind tinkering with a new install, I just don't want to tinker with broken stuff from an update.

Besides, if I have to, I can just reinstall feisty and upgrade, so no big deal, but I'd rather start with a clean slate. (oh yeah, the feisty I'll be doing it on broke for the most part on the last kernel upgrade anyway, and I never went in and fixed anything. none of my window managers appear any more, and of course nvidia is geeked out)

---

### Post by lemurian on 2007-08-02
> **Jhongy said:**
> I just did it manually. BTW the feisty libc6 was already at the latest version before the upgrade.

The latest libc6 for feisty is version 2.5-0ubuntu14.  I checked [here](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libc6&searchon=names&version=feisty&release=all).

Gutsy is at 2.6-5ubuntu1.

---

### Post by walkerk on 2007-08-02
> **Jhongy said:**
> I just did it manually. BTW the feisty libc6 was already at the latest version before the upgrade.

2.6-5 is the current libc6 version being used in Gutsy. The script will pull this from the Gutsy repos while it pulls the new kernel. You won't be able to see it until  the Gutsy repos have been added to your sources.list..

---

### Post by duydaniel on 2007-08-02
It works well on my Dell Laptop i6400

Core 2 Duo T5200
2GB Ram
integrated graphic intel 945GM

They system runs much faster after upgrade :)

---

### Post by walkerk on 2007-08-02
> **duydaniel said:**
> It works well on my Dell Laptop i6400

Core 2 Duo T5200
2GB Ram
integrated graphic intel 945GM

They system runs much faster after upgrade :)

:)

---

### Post by duydaniel on 2007-08-02
One thing I notice is the brightness adjustment of the LCD.
I have a better adjustment (I have twice the number of brightness level I can choose from on the brightness level bar). It does not mean the LCD screen can be brighter than before, but I meant I can adjust it more.
:)

---

### Post by walkerk on 2007-08-02
> **duydaniel said:**
> One thing I notice is the brightness adjustment of the LCD.
I have a better adjustment (I have twice the number of brightness level I can choose from on the brightness level bar). It does not mean the LCD screen can be brighter than before, but I meant I can adjust it more.
:)

Good stuff :)

---

### Post by duydaniel on 2007-08-02
:confused:
Hi...
it seems to have problem with Compiz Fusion.
Whenever I active compiz fusion

compiz --replace

Every windows' titles bar gone ==> can't use 3 buttons (minimize, maximize, close)
Any idea?

---

### Post by fooman on 2007-08-02
> **duydaniel said:**
> :confused:
Hi...
it seems to have problem with Compiz Fusion.
Whenever I active compiz fusion

compiz --replace

Every windows' titles bar gone ==> can't use 3 buttons (minimize, maximize, close)
Any idea?
 
try alt+F2,  then enter:

```
compiz --replace -c emerald &
```

---

### Post by walkerk on 2007-08-02
> **duydaniel said:**
> :confused:
Hi...
it seems to have problem with Compiz Fusion.
Whenever I active compiz fusion

compiz --replace

Every windows' titles bar gone ==> can't use 3 buttons (minimize, maximize, close)
Any idea?

I have the same laptop with the same video (945GM). I didn't have any problems. I usre Compiz Fusion w/ Emerald. Does Compiz Fusion work in your old kernel? I'm sure this is a problem with your CompizFusion install and not the new kernel.

whats the output of:
```
compiz --replace &
```

---

### Post by gav616 on 2007-08-02
if everything works do i even need,     (if soo play explain why someone would need them)

restricted-modules (fglrx nvidia driver i guess)
ubuntu-modules (no idear)
backport-modules (drivers?)

would just the image be sufficient..? or is one orall of them totally nesecessary?.. maybe teh less modules i use faster it is :)

(build the fglrx myself soo nevermind about the restricted)

---

### Post by walkerk on 2007-08-02
> **gav616 said:**
> if everything works do i even need the,

restricted-modules
ubuntu-modules
backport-modules

would just the image be sufficient..? or is one orall of them totally nesecessary?

(build the fglrx myself soo nevermind about the restricted)


you'll need them for something im sure. restricted-modules will enable you to use wireless for example..

you can remove as need after you've upgraded but i added them all in there to suit everyones' needs..

---

### Post by duydaniel on 2007-08-02
> **fooman said:**
> try alt+F2,  then enter:

```
compiz --replace -c emerald &
```

The problem still the same sir.

> ```

compiz --replace &
```


Still the same :confused:

---

### Post by walkerk on 2007-08-02
> **duydaniel said:**
> The problem still the same sir.



Still the same :confused:

Did Compiz Fusion work before or did you just install it? Can you boot into 2.6.20-16 and run it w/out problems?

---

### Post by gav616 on 2007-08-02
> **walkerk said:**
> you'll need them for something im sure. restricted-modules will enable you to use wireless for example..

you can remove as need after you've upgraded but i added them all in there to suit everyones' needs..

well i compile the newest fglrx myself and dont need or use wireless stuff and everything works soo can i uninstall all thoughs above?

p.s.
what does the;
ubuntu-modules
backport-modules 

give you? will backport give you newer drivers?

---

### Post by duydaniel on 2007-08-02
> **walkerk said:**
> Did Compiz Fusion work before or did you just install it? Can you boot into 2.6.20-16 and run it w/out problems?

Compiz had run well before, ===> then the generic 2.6.20-16 went wrong... ===> I upgraded the 2.6.22-9 ===> compiz did not work ===>[COLOR="Red"] boot back to 2.6.20-15 ===> did not work too[/COLOR]

Here is what I notice:
When I click on SYSTEM \ About GNOME ([COLOR="Red"]when I booted in the oldest 2.6.20-15[/COLOR])
It reads:
Version: 2.19.6
Distributor: Ubuntu
Build Date: [COLOR="Red"]07/30/2007[/COLOR] ==> :confused: I thought it should be older than that day.

P.S. After I upgrade the new kernel, I let the system automatically update and upgrade (like 100 MB or something)...

---

### Post by walkerk on 2007-08-02
> **gav616 said:**
> well i compile the newest fglrx myself and dont need or use wireless stuff and everything works soo can i uninstall all thoughs above?

p.s.
what does the;
ubuntu-modules
backport-modules 

give you? will backport give you newer drivers?

I'm not to sure what the two add but I included them in case someone depended on something in there. I didn't want to strand anyone. 

you'd be OK with the image, headers, and restricted-modules.. that's all I needed but it didn't hurt to install them all.. unless you have 0 space left on your hdd :)

---

### Post by walkerk on 2007-08-02
> **duydaniel said:**
> Compiz had run well before, ===> then the generic 2.6.20-16 went wrong... ===> I upgraded the 2.6.22-9 ===> compiz did not work ===>[COLOR="Red"] boot back to 2.6.20-15 ===> did not work too[/COLOR]

Here is what I notice:
When I click on SYSTEM \ About GNOME ([COLOR="Red"]when I booted in the oldest 2.6.20-1[/COLOR]5)
It reads:
Version: 2.19.6
Distributor: Ubuntu
Build Date: [COLOR="Red"]07/30/2007[/COLOR] ==> :confused: I thought it should be older than that day.

Thats strange. I suggest you boot back into 2.6.22-9 an uninstall compiz-fusion completely through synaptic, reboot, and then re-install it.. I'd be surprised if you are still having problems after this. I believe something has gone wrong w/ Compiz .. because if it worked with a different kernel, it should still work with it..

---

### Post by gav616 on 2007-08-02
> **walkerk said:**
> I'm not to sure what the two add but I included them in case someone depended on something in there. I didn't want to strand anyone. 

you'd be OK with the image, headers, and restricted-modules.. that's all I needed but it didn't hurt to install them all.. unless you have 0 space left on your hdd :)
your right, i installed all the meta packages soo i'll always be up-to-date when a new kernel version comes out;

```
sudo apt-get install linux \
linux-headers-generic \
linux-backports-modules-generic

```

seems faster i swear :)

---

### Post by Sunflower1970 on 2007-08-02
I  just installed it. I don't notice any speed difference, but...SUSPEND WORKS on my laptop again! WOOHOO! 

Thank you for this script! I'm more than thrilled! :D

---

### Post by duydaniel on 2007-08-02
> **Sunflower1970 said:**
> I  just installed it. I don't notice any speed difference, but...SUSPEND WORKS on my laptop again! WOOHOO! 

Thank you for this script! I'm more than thrilled! :D

:lolflag::confused::(:(

---

### Post by fallencyi on 2007-08-02
I Installed via the script & it worked like a charm. Thanks for this.

---

### Post by BLTicklemonster on 2007-08-02
Question: (and this may sound totally newbish) is this essentially the same as upgrading to gutsy?

(I tried the upgrade mentioned on the site linked above, and it hosed my installation. there's some error in the terminal and I can't get to a desktop so I'm going ahead and upgrading this kernel.)

---

### Post by duydaniel on 2007-08-02
Here is what happened when I tried to install Compiz after removed it completely via synaptic:

```
daniel@daniel-laptop:~$ sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-gnome: Depends: libwnck18 (>= 2.15.90) but it is not going to be installed
E: Broken packages

```

:confused:

any idea???

---

### Post by BLTicklemonster on 2007-08-02
Just did the kernel upgrade as per this post, and for the first time ever, I didn't have to redo nvidia. Nice. Fluxbox and icewm work, too.

So is this gutsy, or do I have more to do?

Oops, I tried to run vmware, and it didn't work, so I tried to fix it and got this:

Your kernel was built with "gcc" version "4.1.3", while you are trying to use 
"/usr/bin/gcc" version "4.1.2". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.1.2" anyway? [no] 

Where can I get 4.1.3? All I see is rpms for 586. Can I run that? (and I don't see 4.1.3 in repos)

---

### Post by DizzyTech on 2007-08-02
No, it's not a full Gutsy upgrade.  You're pretty much temporarily using the Gutsy repo to download the new kernel, and then removing it (the repo).  You're still using Feisty; it's just like compiling your own kernel.

---

### Post by duydaniel on 2007-08-02
plz... help :(

---

### Post by walkerk on 2007-08-03
> **duydaniel said:**
> Here is what happened when I tried to install Compiz after removed it completely via synaptic:

```
daniel@daniel-laptop:~$ sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-gnome: Depends: libwnck18 (>= 2.15.90) but it is not going to be installed
E: Broken packages

```

:confused:

any idea???

just upgrade that package.
```
sudo apt-get upgrade libwnck18
```

---

### Post by walkerk on 2007-08-03
> **BLTicklemonster said:**
> Just did the kernel upgrade as per this post, and for the first time ever, I didn't have to redo nvidia. Nice. Fluxbox and icewm work, too.

So is this gutsy, or do I have more to do?

Oops, I tried to run vmware, and it didn't work, so I tried to fix it and got this:

Your kernel was built with "gcc" version "4.1.3", while you are trying to use 
"/usr/bin/gcc" version "4.1.2". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.1.2" anyway? [no] 

Where can I get 4.1.3? All I see is rpms for 586. Can I run that? (and I don't see 4.1.3 in repos)

I don't think that's a huge deal. I'm using VirtualBox in this manner and it doesn't care..

---

### Post by lemurian on 2007-08-03
> **BLTicklemonster said:**
> Just did the kernel upgrade as per this post, and for the first time ever, I didn't have to redo nvidia. Nice. Fluxbox and icewm work, too.

What method did you use to install nVidia initially?  I'm asking because A) I've never used the nVidia drivers before.  (I used to have an ATI GPU in my laptop.  Now, let's have a minute of silence for everyone who is stuck with ATI.....)  

And B) I'm writing up a procedure to install Ubuntu onto a Compal IFL90.  This is a newly released laptop so there is some work required to get all the components working.

So I'd like to find a good optimized procedure to install the nVidia drivers.  I'm edging towards using Envy right now.

---

### Post by walkerk on 2007-08-03
> **lemurian said:**
> What method did you use to install nVidia initially?  I'm asking because A) I've never used the nVidia drivers before.  (I used to have an ATI GPU in my laptop.  Now, let's have a minute of silence for everyone who is stuck with ATI.....)  

And B) I'm writing up a procedure to install Ubuntu onto a Compal IFL90.  This is a newly released laptop so there is some work required to get all the components working.

So I'd like to find a good optimized procedure to install the nVidia drivers.  I'm edging towards using Envy right now.

for nvidia you might want to pull these packages along with the new kernel: (they are recommended but not dependent.)
```
nvidia-glx-new
nvidia-glx-legacy
```


with the linux-restricted-modules-2.6.22-9-generic you get these modules:
```

 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN)
```

---

### Post by duydaniel on 2007-08-03
> **walkerk said:**
> just upgrade that package.
```
sudo apt-get upgrade libwnck18
```

Thanks for the reply.
After I did:```

sudo apt-get upgrade libwnck18[sudo] password for daniel:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

It said 0 upgrade
So I tried the Compiz again:
```
daniel@daniel-laptop:~$ sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcompizconfig-backend-gconf is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-gnome: Depends: libwnck18 (>= 2.15.90) but it is not going to be installed
E: Broken packages

```

:confused:

P.S.
I also tried:```

sudo apt-get -f install
```

---

### Post by walkerk on 2007-08-03
> **duydaniel said:**
> Thanks for the reply.
After I did:```

sudo apt-get upgrade libwnck18[sudo] password for daniel:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

It said 0 upgrade
So I tried the Compiz again:
```
daniel@daniel-laptop:~$ sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcompizconfig-backend-gconf is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-gnome: Depends: libwnck18 (>= 2.15.90) but it is not going to be installed
E: Broken packages

```

:confused:

P.S.
I also tried:```

sudo apt-get -f install
```

Whats the output of:
```
cd /var/cache/apt/archives

ls | grep libwnck
```

---

### Post by duydaniel on 2007-08-03
> **walkerk said:**
> Whats the output of:
```
cd /var/cache/apt/archives

ls | grep libwnck
```

Here is the output:
```

daniel@daniel-laptop:~$ cd /var/cache/apt/archives
daniel@daniel-laptop:/var/cache/apt/archives$ ls | grep libwnck
libwnck22_2.19.6-0ubuntu1_i386.deb
libwnck-common_2.19.6-0ubuntu1_all.deb
daniel@daniel-laptop:/var/cache/apt/archives$ 

```

---

### Post by walkerk on 2007-08-03
> **duydaniel said:**
> Here is the output:
```

daniel@daniel-laptop:~$ cd /var/cache/apt/archives
daniel@daniel-laptop:/var/cache/apt/archives$ ls | grep libwnck
libwnck22_2.19.6-0ubuntu1_i386.deb
libwnck-common_2.19.6-0ubuntu1_all.deb
daniel@daniel-laptop:/var/cache/apt/archives$ 

```

what does this give you:
```
dpkg -i libwnck-common_2.19.6-0ubuntu1_all.deb
```

---

### Post by duydaniel on 2007-08-03
> **walkerk said:**
> what does this give you:
```
dpkg -i libwnck-common_2.19.6-0ubuntu1_all.deb
```

Here sir:

```
root@daniel-laptop:/var/cache/apt/archives# dpkg -i libwnck-common_2.19.6-0ubuntu1_all.deb
(Reading database ... 159938 files and directories currently installed.)
Preparing to replace libwnck-common 2.19.6-0ubuntu1 (using libwnck-common_2.19.6-0ubuntu1_all.deb) ...
Unpacking replacement libwnck-common ...
Setting up libwnck-common (2.19.6-0ubuntu1) ...

```

---

### Post by lemurian on 2007-08-03
> **walkerk said:**
> for nvidia you might want to pull these packages along with the new kernel: (they are recommended but not dependent.)
```
nvidia-glx-new
nvidia-glx-legacy
```


with the linux-restricted-modules-2.6.22-9-generic you get these modules:
```

 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN)
```

Thanks.  However, I am under the impression that this won't work.  I've downloaded the packages and saw that the drivers included are too old for the 8600 GT that comes with the Compal IFL90.  I think the only route is to use Envy (or a similar process) or install manually.

---

### Post by walkerk on 2007-08-03
> **duydaniel said:**
> Here sir:

```
root@daniel-laptop:/var/cache/apt/archives# dpkg -i libwnck-common_2.19.6-0ubuntu1_all.deb
(Reading database ... 159938 files and directories currently installed.)
Preparing to replace libwnck-common 2.19.6-0ubuntu1 (using libwnck-common_2.19.6-0ubuntu1_all.deb) ...
Unpacking replacement libwnck-common ...
Setting up libwnck-common (2.19.6-0ubuntu1) ...

```

ok now:
```
dpkg -i libwnck22_2.19.6-0ubuntu1_i386.deb
```

---

### Post by Scotty562 on 2007-08-03
Honestly all I can say is thank you! I coudln't get my nvidia graphics to work in gutsy but I could in Feisty. I couldn't use my wireless in Feisty but I could in gutsy. You have given me the best of both worlds.

THANK YOU!!

Hardware: dv6500t 2.0 ghz core two duo, nvidia geforce 8400 gs, 120 GB hdd, 2 gigs of ram.

---

### Post by duydaniel on 2007-08-03
> **walkerk said:**
> ok now:
```
dpkg -i libwnck22_2.19.6-0ubuntu1_i386.deb
```

```

root@daniel-laptop:~# dpkg -i libwnck22_2.19.6-0ubuntu1_i386.deb
dpkg: error processing libwnck22_2.19.6-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libwnck22_2.19.6-0ubuntu1_i386.deb
root@daniel-laptop:~# 

```

everything screws me up :)

---

### Post by walkerk on 2007-08-03
> **Scotty562 said:**
> Honestly all I can say is thank you! I coudln't get my nvidia graphics to work in gutsy but I could in Feisty. I couldn't use my wireless in Feisty but I could in gutsy. You have given me the best of both worlds.

THANK YOU!!

Hardware: dv6500t 2.0 ghz core two duo, nvidia geforce 8400 gs, 120 GB hdd, 2 gigs of ram.

Good to hear :)

---

### Post by walkerk on 2007-08-03
> **duydaniel said:**
> ```

root@daniel-laptop:~# dpkg -i libwnck22_2.19.6-0ubuntu1_i386.deb
dpkg: error processing libwnck22_2.19.6-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libwnck22_2.19.6-0ubuntu1_i386.deb
root@daniel-laptop:~# 

```

everything screws me up :)

ok.. try this:
```
sudo apt-get install libwnck18 --reinstall
```

---

### Post by duydaniel on 2007-08-03
> **walkerk said:**
> ok.. try this:
```
sudo apt-get install libwnck18 --reinstall
```

```
daniel@daniel-laptop:~$ sudo apt-get install libwnck18 --reinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libwnck18: Depends: libwnck-common (< 2.19) but 2.19.6-0ubuntu1 is to be installed
E: Broken packages
```

I better either reinstall Ubuntu or leave it along for awhile.
:(
Do you think I should give SUSE a try? I don't know if it gonna work with Dell wireless.

---

### Post by walkerk on 2007-08-03
> **duydaniel said:**
> ```
daniel@daniel-laptop:~$ sudo apt-get install libwnck18 --reinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libwnck18: Depends: libwnck-common (< 2.19) but 2.19.6-0ubuntu1 is to be installed
E: Broken packages
```

I better either reinstall Ubuntu or leave it along for awhile.
:(
Do you think I should give SUSE a try? I don't know if it gonna work with Dell wireless.

suse has the same issues with wireless..

```
cd /var/cache/apt/archives
ls | grep libwnck
```

remove those two files:
```
sudo rm file1 file2
```

```
sudo apt-get update
```

reinstall
```
sudo apt-get install libwnck libwnck-common --reinstall
```


give that a go. apt is using those same (and possibly broken packages that you have archived.)

---

### Post by duydaniel on 2007-08-03
It did not work.... :(
Please, give me the last shoot before I reinstall it... the system seems messed up to me. Not because it does not run Compiz...  :(

Btw, I am glad if you know how to wirelessly connect my Desktop (winXP) with my laptop (Ubuntu) so I can backup my files from the laptop to the desktop using wireless. :)

---

### Post by walkerk on 2007-08-03
> **duydaniel said:**
> It did not work.... :(
Please, give me the last shoot before I reinstall it... the system seems messed up to me. Not because it does not run Compiz...  :(

Btw, I am glad if you know how to wirelessly connect my Desktop (winXP) with my laptop (Ubuntu) so I can backup my files from the laptop to the desktop using wireless. :)

Other than your Compiz Fusion not working whats messed up? The libwnck package seems to be broken therefore you are unable to use Compiz.. not an earth shattering problem, but still an issue. There has to be a fix.. 

I can't seem to re-create you issue on my vbox.. :/

This doesn't work.. right?
```
sudo apt-get update -f
```
```
sudo apt-get -f install libwnck18 --reinstall
```

---

### Post by duydaniel on 2007-08-03
> **walkerk said:**
> Other than your Compiz Fusion not working whats messed up? The libwnck package seems to be broken therefore you are unable to use Compiz.. not an earth shattering problem, but still an issue. There has to be a fix.. 

I can't seem to re-create you issue on my vbox.. :/

Honestly, if you could still remember, I said that I could adjust the brightness better (more brightness level)... but after some update... it came back as before the kernel upgrade. Further more, it also automatically and unexpectedly increase the brightness to maximum a few mins after I decrease the brightness level. Such senario repeateds over and over...

Now... after rebooted the system... I can not login any more. After typed username and password... the screen just stuck there... nothing happens (mouse can move).

I am now trying to recuse my files by the Live CD now... the system can't login. :(
There was nothing that I have ever given such patient to as Linux... since I would have to learn it anyway. :(

---

### Post by walkerk on 2007-08-03
> **duydaniel said:**
> Honestly, if you could still remember, I said that I could adjust the brightness better (more brightness level)... but after some update... it came back as before the kernel upgrade. Further more, it also automatically and unexpectedly increase the brightness to maximum a few mins after I decrease the brightness level. Such senario repeateds over and over...

Now... after rebooted the system... I can not login any more. After typed username and password... the screen just stuck there... nothing happens (mouse can move).

There was nothing that I have ever given such patient to as Linux... since I would have to learn it anyway. :(

Wow. These are serious issues. I don't believe its the new kernel as you said you have the same problems with your older kernels.. right? 2.6.20-15 & 16-generic?

What kind of Video card do you have?

---

### Post by duydaniel on 2007-08-03
> **walkerk said:**
> Wow. These are serious issues. I don't believe its the new kernel as you said you have the same problems with your older kernels.. right? 2.6.20-15 & 16-generic?

What kind of Video card do you have?

I have I945 GM and yes. I have the old kernel as you said.
I am backing up some file via the thumb drive now.
Actually, I convert the Ubuntu into Ubuntu CE... then... problem started to happens since then...  never again.:(

---

### Post by walkerk on 2007-08-03
> **duydaniel said:**
> I have I945 GM and yes. I have the old kernel as you said.
I am backing up some file via the thumb drive now.
Actually, I convert the Ubuntu into Ubuntu CE... then... problem started to happens since then...  never again.:(

Ahh.. that could be the problem. I have no idea what Ubuntu CE changes in you system so I won't be able to be of any help.. Sorry.

A clean install of Ubuntu will obviously fix it... I hope you don't shy away from this upgrade due to this issue.. but I would understand if you did.

I have the same video as you and the kernel, compiz-fusion, and libwnck are all functioning well..

Good luck friend. :)

---

### Post by duydaniel on 2007-08-03
I have problem with permission now...
After login from the live CD as nautilus...
blah blah blah... you don't have permission... :confused:to copy some files to the USB

after tried:
sudo nautilus
I tried to change the permission but it report the disk is read only

---

### Post by walkerk on 2007-08-03
> **duydaniel said:**
> I have problem with permission now...
After login from the live CD as nautilus...
blah blah blah... you don't have permission... :confused:to copy some files to the USB

where does your usb thumb drive mount? /mnt/usb?

you could copy stuff using recovery mode on one of your kernels. just press esc at grub stage 1.5 and boot into one of the kernels loaded recovery mode.

from there use the command line to copy the files: (for example)
```
sudo cp /location/of/your/files /mnt/usb
```

---

### Post by duydaniel on 2007-08-03
I have other NTFS partitions under Vista's control...
and it block me to copy stuff to because there are some DVD image too big for the USB.

it report "read only" disk... there seems no way to change it even as root. :confused:

---

### Post by duydaniel on 2007-08-03
It has been the third times I reinstall Ubuntu...[COLOR="Red"]**VS**[/COLOR]. >25 times I had reinstalled Windows ME around 2001-2002.

---

### Post by jamieplucinski on 2007-08-03
Tried this, it completely hosed my install, and when I say completely... I mean completely... installing the extra libs means nothing works, gnome won't boot, and trying to remove them results in apt-get telling me I am about to do something stupid by removing over 3GB of packages.

So I am now stuck with a system that will only boot to a terminal since GDM won't load.... fun. I had to do this post from a Windows box I have in the house.

---

### Post by walkerk on 2007-08-03
> **jamieplucinski said:**
> Tried this, it completely hosed my install, and when I say completely... I mean completely... installing the extra libs means nothing works, gnome won't boot, and trying to remove them results in apt-get telling me I am about to do something stupid by removing over 3GB of packages.

So I am now stuck with a system that will only boot to a terminal since GDM won't load.... fun. I had to do this post from a Windows box I have in the house.

Did you update stuff other than the kernel? (as in: the Automatic Upgrade icon in the systray?) In my original post I said not to do this. In fact it was bold and red. I've done this on 3 seperate machines with out problems. Eveyone else had 0 issues. What extra libs? you mean libc6? It only upgrades from 2.5 to 2.6.. No other packages will be installed. 

I'm a bit confused how you got here..

---

### Post by duydaniel on 2007-08-03
> **walkerk said:**
> Did you update stuff other than the kernel? (as in: the Automatic Upgrade icon in the systray?) In my original post I said not to do this. In fact it was bold and red. I've done this on 3 seperate machines with out problems. Eveyone else had 0 issues. What extra libs? you mean libc6? It only upgrades from 2.5 to 2.6.. No other packages will be installed. 

I'm a bit confused how you got here..

What you meant by not updating other stuff? Does it mean we should not run any update while we are running the new kernel?

---

### Post by jamieplucinski on 2007-08-03
yes the libc6 upgrades hosed my install, I didn't install any other libs through updates or the systray icon, as per your instructions.

---

### Post by walkerk on 2007-08-03
> **jamieplucinski said:**
> yes the libc6 upgrades hosed my install, I didn't install any other libs through updates or the systray icon, as per your instructions.

ok.. reboot and at grub press esc. now boot into recovery mode and do the following:
[B]
first try this:[/B]
```
sudo apt-get -f install libc6 --reinstall
```

[B]
if that didn't work.. try this:[/B]
```
sudo apt-get -y remove libc6
```

delete it from your archives:
```
cd /var/cache/apt/archives
```

find the libc6 package filename:
```
ls | grep libc6
```

remove the deb file:
```
sudo rm name_of_file.deb
```

```
sudo apt-get update
```

now reinstall it from the feisty repos:
```
sudo apt-get -y install libc6
```

Let me know please.

---

### Post by jamieplucinski on 2007-08-03
> **walkerk said:**
> ok.. reboot and at grub press esc. now boot into recovery mode and do the following:
[B]
first try this:[/B]
```
sudo apt-get -f install libc6 --reinstall
```


For this step I get: Reinstallation of libc6 is not possible, since it cannot be downloaded. And yes I am online :(

> [B]
if that didn't work.. try this:[/B]
```
sudo apt-get -y remove libc6
```

delete it from your archives:
```
cd /var/cache/apt/archives
```

find the libc6 package filename:
```
ls | grep libc6
```

remove the deb file:
```
sudo rm name_of_file.deb
```

```
sudo apt-get update
```

now reinstall it from the feisty repos:
```
sudo apt-get -y install libc6
```

Let me know please.

That step I'm not even going to run with -y since that removes literally everything in the Ubuntu install... so much so that apt-get wants me to type "Yes do as I say" since it removes so much that the install would be hosed beyond repair.

---

### Post by realo on 2007-08-03
Hello,

Just to report on the happy ending of my kernel upgrade...

The reason why the 2.6.22-9 kernel was stopping at boot was because, for some reason, the ata_piix module was not specified in the modules file (/etc/initramfs-tools/modules, and in /etc/modules as well)

I found that one out simply by waiting for 90 seconds at boot time.  The kernel is not crashed, it just timesout after 90 seconds into a busybox shell.  It complained that it could not see the disk devices, which was true indeed.  At that point I simply did a modprobe ata_piix , and quit the shell.  Magic:  the boot completed fine.  That is where I simply added ata_piix to the modules, and did an update-initramfs -u -k 2.6.22--9-generic and all has been fine since then.

Thanks.

Real

---

### Post by walkerk on 2007-08-03
> **jamieplucinski said:**
> 
That step I'm not even going to run with -y since that removes literally everything in the Ubuntu install... so much so that apt-get wants me to type "Yes do as I say" since it removes so much that the install would be hosed beyond repair.

more hosed than it already is? you are going to re-install libc6 (to 2.5 which is default in Feisty) immediately after..

---

### Post by walkerk on 2007-08-03
> **realo said:**
> Hello,

Just to report on the happy ending of my kernel upgrade...

The reason why the 2.6.22-9 kernel was stopping at boot was because, for some reason, the ata_piix module was not specified in the modules file (/etc/initramfs-tools/modules, and in /etc/modules as well)

I found that one out simply by waiting for 90 seconds at boot time.  The kernel is not crashed, it just timesout after 90 seconds into a busybox shell.  It complained that it could not see the disk devices, which was true indeed.  At that point I simply did a modprobe ata_piix , and quit the shell.  Magic:  the boot completed fine.  That is where I simply added ata_piix to the modules, and did an update-initramfs -u -k 2.6.22--9-generic and all has been fine since then.

Thanks.

Real

Glad you found the issue :)

---

### Post by jamieplucinski on 2007-08-03
> **walkerk said:**
> more hosed than it already is? you are going to re-install libc6 (to 2.5 which is default in Feisty) immediately after..

yep, try typing that without -y in your own console and look at the huge list of stuff it's going to remove... the list is endless... if I am going to be removing over 3GB of packages I might as well just re-install.

Isn't there a way I can forcibly remove libc6 ignoring it's dependancies, and then install the version from the feisty repos?

---

### Post by walkerk on 2007-08-03
> **jamieplucinski said:**
> yep, try typing that without -y in your own console and look at the huge list of stuff it's going to remove... the list is endless... if I am going to be removing over 3GB of packages I might as well just re-install.

Isn't there a way I can forcibly remove libc6 ignoring it's dependancies, and then install the version from the feisty repos?

what does this output?
```
sudo apt-get install libc6 --no-upgrade
```

---

### Post by walkerk on 2007-08-03
you can do this. it should ignore the dependencies.. download but don't install is what the -d option does:
```
sudo apt-get -d install libc6
```

if that didn't work no worries.. this package should still be in your archives.. just move to your package achive:
```
cd /var/cache/apt/archive
```

find libc6 version 2.5:
```
ls | grep libc6
```

now try to install it:
```
sudo dpkg -i filename.deb --ignore-depends
```

---

### Post by jamieplucinski on 2007-08-03
Skipping libc6, it is already installed and upgrade is not set.

---

### Post by walkerk on 2007-08-03
> **jamieplucinski said:**
> yep, try typing that without -y in your own console and look at the huge list of stuff it's going to remove... the list is endless... if I am going to be removing over 3GB of packages I might as well just re-install.

Isn't there a way I can forcibly remove libc6 ignoring it's dependancies, and then install the version from the feisty repos?

yea.. i know what the -y option does.. i've been up every road.. including upgrading libc6 and gcc (which added a bunch of packages.. all of which i removed and restored gcc)

---

### Post by jamieplucinski on 2007-08-03
> **walkerk said:**
> you can do this. it should ignore the dependencies.. download but don't install is what the -d option does:
```
sudo apt-get -d install libc6
```

if that didn't work no worries.. this package should still be in your archives.. just move to your package achive:
```
cd /var/cache/apt/archive
```

find libc6 version 2.5:
```
ls | grep libc6
```

now try to install it:
```
sudo dpkg -i filename.deb --ignore-depends
```

Tried this, got this:
libc6 is already the newest version. DEB file wasn't downloaded or in my archives :(

---

### Post by walkerk on 2007-08-03
> **jamieplucinski said:**
> Tried this, got this:
libc6 is already the newest version. DEB file wasn't downloaded or in my archives :(

yea.. you need to remove libc6 first.. then re-install it.. now it'll be from the feisty archive.. 

can't hose your box anymore than it currently is.

---

### Post by jamieplucinski on 2007-08-03
Yeah but, I'll have to re download all of those libs... which is going to take forever and a day based on the speed of the mirrors.

Before I go and remove all those, is there a way for me to remove libc6 without removing all of the packages that depend on it?

Thanks for the help thus far

---

### Post by walkerk on 2007-08-03
> **jamieplucinski said:**
> Yeah but, I'll have to re download all of those libs... which is going to take forever and a day based on the speed of the mirrors.

Before I go and remove all those, is there a way for me to remove libc6 without removing all of the packages that depend on it?

Thanks for the help thus far

This is what I'm doing.. perhaps you'll see something I don't.. I'm not sure why you are even having this issue.. I update libc6.. ah well.. give these a look. Help me out

```
man apt-get
```

and
```
man dpkg
```

---

### Post by jamieplucinski on 2007-08-03
I've read through them whilst trying the things you suggested on here, I can't find anything that seems to be of use.

Apt-get seems to assume removing packages requires you to hose your system, even if those packages are problematic.

I'm just going to re-install... apt-get won't let me do anything of use without removing 99.99% of my Ubuntu install... which is helpful.

Thanks anyways.

---

### Post by walkerk on 2007-08-03
> **jamieplucinski said:**
> I've read through them whilst trying the things you suggested on here, I can't find anything that seems to be of use.

Apt-get seems to assume removing packages requires you to hose your system, even if those packages are problematic.

I'm just going to re-install... apt-get won't let me do anything of use without removing 99.99% of my Ubuntu install... which is helpful.

Thanks anyways.

Sorry to hear this. BTW I've changed my recommendation on scripts in my original post to point to the normal kernel.sh. Hopefully no one else runs into these problems. I only added it because several people couldn't boot until they had libc6 upgraded..

---

### Post by jamieplucinski on 2007-08-04
> **walkerk said:**
> Sorry to hear this. BTW I've changed my recommendation on scripts in my original post to point to the normal kernel.sh. Hopefully no one else runs into these problems. I only added it because several people couldn't boot until they had libc6 upgraded..

Well I'm all reinstalled, I'm going to try the new kernel through the update script later on, at least that will be easy to reverse. It's just disappointing that for the wealth of features Ubuntu has it's not possible to revert a package upgrade with ease... just for laughs I removed the library and all of it's dependencies... and yes it left my system totally hosed, so hosed in fact that simple commands like ls didn't work anymore... they were removed.

Ah well live and learn, I'll post back with my results of the upgrade :)

---

### Post by jamieplucinski on 2007-08-04
Well I downloaded the kernel.sh script and ran it and it returned:
```
The following extra packages will be installed:
  libc6 libc6-i686 linux-restricted-modules-common
Suggested packages:
  glibc-doc linux-doc-2.6.22 linux-source-2.6.22 nvidia-glx nvidia-glx-legacy
  nvidia-glx-new avm-fritz-firmware-2.6.22-9
The following NEW packages will be installed:
  linux-backports-modules-2.6.22-9-generic linux-headers-2.6.22-9
  linux-headers-2.6.22-9-generic linux-image-2.6.22-9-generic
  linux-restricted-modules-2.6.22-9-generic
  linux-ubuntu-modules-2.6.22-9-generic
The following packages will be upgraded:
  libc6 libc6-i686 linux-restricted-modules-common

```

So either way it looks like libc6 is going to be thrown in... since I just re-installed I'm going to try it anyway... nothing to loose, working ACPI in Ubuntu for the first time EVER to again :)

**Update: Well it installed fine on a 30 minute old Ubuntu install that was fully updated, the only thing I did different is not install Automatix... so I guess that shafted my install somewhere along the line. Sadly ACPI is still bugged on my laptop... but at least I have some of the new kernel features. Thanks for your help earlier!**

---

### Post by walkerk on 2007-08-04
> **jamieplucinski said:**
> Well I downloaded the kernel.sh script and ran it and it returned:
```
The following extra packages will be installed:
  libc6 libc6-i686 linux-restricted-modules-common
Suggested packages:
  glibc-doc linux-doc-2.6.22 linux-source-2.6.22 nvidia-glx nvidia-glx-legacy
  nvidia-glx-new avm-fritz-firmware-2.6.22-9
The following NEW packages will be installed:
  linux-backports-modules-2.6.22-9-generic linux-headers-2.6.22-9
  linux-headers-2.6.22-9-generic linux-image-2.6.22-9-generic
  linux-restricted-modules-2.6.22-9-generic
  linux-ubuntu-modules-2.6.22-9-generic
The following packages will be upgraded:
  libc6 libc6-i686 linux-restricted-modules-common

```

So either way it looks like libc6 is going to be thrown in... since I just re-installed I'm going to try it anyway... nothing to loose, working ACPI in Ubuntu for the first time EVER to again :)

**Update: Well it installed fine on a 30 minute old Ubuntu install that was fully updated, the only thing I did different is not install Automatix... so I guess that shafted my install somewhere along the line. Sadly ACPI is still bugged on my laptop... but at least I have some of the new kernel features. Thanks for your help earlier!**

I see it's automatically update libc6 now.. I guess I can remove the seconds script.. 

Also, here is the offical deb package for automatix 2: [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.12-7.04feisty_i386.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.12-7.04feisty_i386.deb)

---

### Post by lemurian on 2007-08-04
The script that installs libc6 worked for me!  I've had *no* problems at all after using the script.

My machine is a Compal IFL90 branded as a Sager NP2090.  The kernel running now is 2.6.22-9-generic.

---

### Post by lemurian on 2007-08-04
Walkerk, I'm going to point people to your script but right now it is impossible to download it without being a registered user of the forum.  I'm sure some of the people who could benefit from it might not be interested in registering to the forum right away.  So my question is:

- Is there a way to make that script available to guests?

Thanks

---

### Post by ericzb on 2007-08-04
well, if the author agreeded, why not just paste it out, and let the guest do the copy and paste thing.:)

---

### Post by renerey on 2007-08-04
awesome script... i've run it effortless and now my wifi works flawless. well not exactly because the lights aren't on but its working. i think i just need to upgrade the iwlwifi and mac8 with the newest version on the website. thanks guys.

---

### Post by pashashome on 2007-08-04
Walkerk, thanks for the script. Took less than 10 minutes to run, it ran flawlessly and quickly looking at the stuff I normally use everything is working well. Thanks again.

---

### Post by fooman on 2007-08-04
just to update,  my desktop is an abit fatality an8sli, x2 4200, 2 gigs ocz pc3200, nvidia 7950,  hauppauge pvr250....no wireless.

used the libc6 script....everything running perfectly.  

my notebook is a gateway mx6453....ati x1150,  sound and wireless working flawlessly.

tried the script,  but it did not work.  used the manual method....installed without a problem.

thanks again  :)

---

### Post by walkerk on 2007-08-04
> **fooman said:**
> just to update,  my desktop is an abit fatality an8sli, x2 4200, 2 gigs ocz pc3200, nvidia 7950,  hauppauge pvr250....no wireless.

used the libc6 script....everything running perfectly.  

my notebook is a gateway mx6453....ati x1150,  sound and wireless working flawlessly.

tried the script,  but it did not work.  used the manual method....installed without a problem.

thanks again  :)

what part didn't work? perhaps apt-get got hung up..?

---

### Post by walkerk on 2007-08-04
> **lemurian said:**
> Walkerk, I'm going to point people to your script but right now it is impossible to download it without being a registered user of the forum.  I'm sure some of the people who could benefit from it might not be interested in registering to the forum right away.  So my question is:

- Is there a way to make that script available to guests?

Thanks

> **ericzb said:**
> well, if the author agreeded, why not just paste it out, and let the guest do the copy and paste thing.:)

You can point the people to this post. Tell them to open up their favorite text editor paste the following into it and save it as **kernel.sh**.

Now they need to make it executable:
```
chmod +x kernel.sh
```

Here's the script:
```

#!/bin/bash
# This script was created by walkerk @ubuntuforums.org)
# For use w/ Ubuntu 7.04 (Feisty Fawn)
# Purpose: Upgrade to Gutsy's current kernel.

# Intro
echo
echo
echo "Kernel Upgrade."
echo "Written for Feisty Fawn users."
echo "Purpose: Upgrade to the current Gutsy kernel."
echo
echo "Attempting to upgrade from kernel version " && uname -r
echo

read -p "Do you wish to continue? (y/n) " answer;

# Continue the install?
case "$answer" in

	y)
		# Back up /etc/apt/sources.list
		sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

		# Add the Gutsy Repository to /etc/apt/sources.list
		echo -n "Adding Gutsy repository: "
		echo 'deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted' | sudo tee -a /etc/apt/sources.list
		sleep 1
		sudo apt-get update

		# Install the kernel packages from the repository.
		echo
		echo "Installing the new kernel..."
		echo "This will take several minutes..."
		echo

		sleep 2
		sudo apt-get -y install linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
		
		echo	
		echo "Install complete. Updating your repositories."
		echo

		# Restore /etc/apt/sources.list	
		sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
		sudo rm /etc/apt/sources.list_backup
		sleep 1
		sudo apt-get update

		# Need to reboot.
		echo
		echo "A reboot is necessary for changes to take effect. "
		read -p "Do you wish to reboot now? (y/n) " restart;

		case "$restart" in
			y) echo "Rebooting."; sudo reboot;;
			*) echo "Reboot necessary to complete installation. Aborting.";;
		esac

	;;

	
	n) echo "Aborting the install.";;
	

	*) echo "Invalid entry. Aborting.";;
esac

```

---

### Post by walkerk on 2007-08-04
> **lemurian said:**
> The script that installs libc6 worked for me!  I've had *no* problems at all after using the script.

My machine is a Compal IFL90 branded as a Sager NP2090.  The kernel running now is 2.6.22-9-generic.

> **renerey said:**
> awesome script... i've run it effortless and now my wifi works flawless. well not exactly because the lights aren't on but its working. i think i just need to upgrade the iwlwifi and mac8 with the newest version on the website. thanks guys.

> **pashashome said:**
> Walkerk, thanks for the script. Took less than 10 minutes to run, it ran flawlessly and quickly looking at the stuff I normally use everything is working well. Thanks again.

> **fooman said:**
> just to update,  my desktop is an abit fatality an8sli, x2 4200, 2 gigs ocz pc3200, nvidia 7950,  hauppauge pvr250....no wireless.

used the libc6 script....everything running perfectly.  

my notebook is a gateway mx6453....ati x1150,  sound and wireless working flawlessly.

tried the script,  but it did not work.  used the manual method....installed without a problem.

thanks again  :)

Glad to hear it worked well for you all :)

---

### Post by siralphred on 2007-08-04
I used the script and everything went well, but after a reboot, my xserver crashed, i was using the new nvidia driver and had removed the one in restricted driver in Feisty, so i went back to the old kernel and everything works, i think i might have to reinstall the nvidia driver or if anyone knows how to modify the script so i dont have to reinstall it i would appreciate it. Also  will Compiz Fusion work after upgrading the kernel?

Hp dv6000 || Turion x2 || Nvidia Geforce 6150 Go ||

---

### Post by josys36 on 2007-08-04
Tried this and was able to upgrade just fine, but VMWare give me huge amounts of grief. I was able to get it compiled and installed, but for some reason the network section does not appear to be working. My WinXP guest has no network. Has anyone else experienced this?

Jason

---

### Post by walkerk on 2007-08-04
> **siralphred said:**
> I used the script and everything went well, but after a reboot, my xserver crashed, i was using the new nvidia driver and had removed the one in restricted driver in Feisty, so i went back to the old kernel and everything works, i think i might have to reinstall the nvidia driver or if anyone knows how to modify the script so i dont have to reinstall it i would appreciate it. Also  will Compiz Fusion work after upgrading the kernel?

Hp dv6000 || Turion x2 || Nvidia Geforce 6150 Go ||

I'll write a quick script for you. Did you remove the restricted modules for 2.6.22-9? The script that I'll post up in a few minutes will download the nvidia-glx-new or nvidia-glx-legacy modules from the Gutsy repos..

**edit: **Now that I look into the Gutsy repos there are way too many options for the nVidia driver and I personally don't have an nVidia card.. So I'm not the one to do this. The easiest method would be for you to add the Gusty repos and then use Synaptic to decided which one you need. I can get you to that point though

in a terminal window:
```
echo 'deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted' | sudo tee -a /etc/apt/sources.list
```

now update:
```
sudo apt-get update
```

now check Synaptic:
```
gksudo synaptic
```

Find your module and then install it. **Remember not to install anything else that might pop up with the automatic updates feature.**

now remove the Gutsy repo by removing it from /etc/apt/sources.list
```
gksudo gedit /etc/apt/sources.list
```

remove the following line (it'll be the last line of the file):
```
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
```

Sorry I couldn't finish the script. I had it all done and then look a look at the Gutsy repos and realized there are too many options and I wasn't sure which would work..

**edit 2:** If you let me know exactly which modules you needed to get it working I'll post up the nvidia script (using your instructions) to my main post.. to help out others with this issue.

---

### Post by walkerk on 2007-08-04
> **josys36 said:**
> Tried this and was able to upgrade just fine, but VMWare give me huge amounts of grief. I was able to get it compiled and installed, but for some reason the network section does not appear to be working. My WinXP guest has no network. Has anyone else experienced this?

Jason

Another user had issues with VMWare but he was able to fix the issues easily. Read back several pages and perhaps PM him. I didn't experiance any issues the VirtualBox..

---

### Post by jamieplucinski on 2007-08-04
hmm, since installing the new kernel I lost the ability to handle direct rendering, I looked at the feisty repos to install the updated fglrx package (I have an ATI card) but it wanted to install some more libraries that I was a little dubious of, so I'm going to try and roll my own package from ATI's installer and see where that takes me.

I've noticed that 2.6.22 actually boots more reliably, less hanging when probing hardware etc... boy am I am glad I opted to re-install and try this again :)

---

### Post by walkerk on 2007-08-04
> **jamieplucinski said:**
> hmm, since installing the new kernel I lost the ability to handle direct rendering, I looked at the feisty repos to install the updated fglrx package (I have an ATI card) but it wanted to install some more libraries that I was a little dubious of, so I'm going to try and roll my own package from ATI's installer and see where that takes me.

I've noticed that 2.6.22 actually boots more reliably, less hanging when probing hardware etc... boy am I am glad I opted to re-install and try this again :)

Glad you gave it a go again. I was pleased when I upgraded as well. Unfortunately my laptop has Intel 945GM so I'm not much help to you ATI and NVIDIA users. When you find the fix please post it just in case someone else is having the same problem :)

---

### Post by fooman on 2007-08-04
> **walkerk said:**
> Glad you gave it a go again. I was pleased when I upgraded as well. Unfortunately my laptop has Intel 945GM so I'm not much help to you ATI and NVIDIA users. When you find the fix please post it just in case someone else is having the same problem :)

i used envy on my gateway mx6453....ati x1150  :redface:

---

### Post by siralphred on 2007-08-04
> **walkerk said:**
> I'll write a quick script for you. Did you remove the restricted modules for 2.6.22-9? The script that I'll post up in a few minutes will download the nvidia-glx-new or nvidia-glx-legacy modules from the Gutsy repos..

**edit: **Now that I look into the Gutsy repos there are way too many options for the nVidia driver and I personally don't have an nVidia card.. So I'm not the one to do this. The easiest method would be for you to add the Gusty repos and then use Synaptic to decided which one you need. I can get you to that point though

in a terminal window:
```
echo 'deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted' | sudo tee -a /etc/apt/sources.list
```

now update:
```
sudo apt-get update
```

now check Synaptic:
```
gksudo synaptic
```

Find your module and then install it. **Remember not to install anything else that might pop up with the automatic updates feature.**

now remove the Gutsy repo by removing it from /etc/apt/sources.list
```
gksudo gedit /etc/apt/sources.list
```

remove the following line (it'll be the last line of the file):
```
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
```

Sorry I couldn't finish the script. I had it all done and then look a look at the Gutsy repos and realized there are too many options and I wasn't sure which would work..

**edit 2:** If you let me know exactly which modules you needed to get it working I'll post up the nvidia script (using your instructions) to my main post.. to help out others with this issue.


Thanks for the prompt respond, i am goin to try what you suggested and let you know what happens, one thing is i am using the new nvidia driver which i downloaded from the nvidia website, [http://www.nvidia.com/object/linux_display_ia32_100.14.11.html]("http://www.nvidia.com/object/linux_display_ia32_100.14.11.html") when i look in synaptic it is not listed so i am thinking i will just have to reinstall it by following this instruction its pretty straight forward [http://ubuntuforums.org/showthread.php?t=514161&highlight=latest+nvidia+driver]("http://ubuntuforums.org/showthread.php?t=514161&highlight=latest+nvidia+driver") so maybe u can incorporate this instruction in the script for those using the latest nvidia driver (or u can do a generic one and the user will have to enter what ever nvidia driver they are using), but i am not master ubuntu user so i dont know if that is possible :). Also in his instructions he refered to the driver as  NVIDIA-Linux-x86_64-100.14.11-pkg2.run   but should be  NVIDIA-Linux-x86-64-100.14.11-pkg1.run  thanks

---

### Post by jamieplucinski on 2007-08-04
Weirdness ensues... the ati installer for my graphics card reports an unsupported architecture when trying to build packages...

```
Generating package: Ubuntu/gutsy
./packages/Ubuntu/ati-packager.sh: 175: dpkg-architecture: not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install.Zb7622
```

This occurs when generating any package, even Ubuntu/feisty I'll keep playing around with it, has anyone else had this problem with the ATI packages?

I'm getting this show up too which is a little disheartening... seems the fglrx module isn't being loaded at least not in it's entirety... fun fun :)
```
jamie@maplesyrup:~$ dmesg | grep fglrx
[   37.620000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   37.624000] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[   37.624000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   40.576000] [fglrx:firegl_unlock] *ERROR* Process 4666 using kernel context 0

```

---

### Post by jamieplucinski on 2007-08-04
> **fooman said:**
> i used envy on my gateway mx6453....ati x1150  :redface:

I tried envy too, but it won't install... requires build-essential which in turn requires some new packages from gutsy...

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

```

I think I'm just going to bite the bullet and install those dev libs and the build tools from the gutsy repo.

[b]Update: This is potentially going to be painful...
> The following extra packages will be installed:
  cpp cpp-4.1 dpkg dpkg-dev g++ g++-4.1 gcc gcc-4.1 gcc-4.1-base gcc-4.2-base
  libc6-dev libgcc1 libstdc++6 libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  cpp-multilib cpp-doc gcc-4.1-locales lzma debian-keyring g++-multilib
  g++-4.1-multilib gcc-4.1-doc gcc-multilib manpages-dev autoconf automake1.9 libtool
  flex bison gcc-doc gcc-4.1-multilib glibc-doc libstdc++6-4.1-doc
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 gcc-4.2-base libc6-dev libstdc++6-4.1-dev
  linux-libc-dev
The following packages will be upgraded:
  cpp cpp-4.1 dpkg gcc gcc-4.1 gcc-4.1-base libgcc1 libstdc++6
We'll soon see, I'l leaving it installing while I go watch the simpsons movie, wish me luck.[/b]

---

### Post by walkerk on 2007-08-04
> **jamieplucinski said:**
> I tried envy too, but it won't install... requires build-essential which in turn requires some new packages from gutsy...

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

```

I think I'm just going to bite the bullet and install those dev libs and the build tools from the gutsy repo.

[b]Update: This is potentially going to be painful...

We'll soon see, I'l leaving it installing while I go watch the simpsons movie, wish me luck.[/b]

LOL. Good luck man. :)

And let me know how the movie is. I'll have to wait several more weeks until we get it over here.

---

### Post by aaaantoine on 2007-08-04
Nifty.  The latest kernel supports my Targus bluetooth dongle (it even says so in the release notes).  Thanks for the guide!

---

### Post by jamieplucinski on 2007-08-04
> **walkerk said:**
> LOL. Good luck man. :)

And let me know how the movie is. I'll have to wait several more weeks until we get it over here.

Best. Movie. Ever. It's been out here a while, but I wanted to avoid the crowds and sat in a relatively quiet theater, quiet until the movie started that is... hilarious, exactly what a Simpsons movie should be.

Anyways I am up and running with direct rendering, yay! Here's my howto for the 200M chipset:

[LIST=1]
[*]Install the kernel as per this guide
[*]Re-add the gutsy repos and then do apt-get update
[*]Do apt-get install build-essential and install all of the required libs (just answer Y)
[*]Remove the gutsy repo and do apt-get update again.
[*]Install Envy and do what you will with it
[*]Reboot when prompted by Envy, et voila, direct rendering enabled for your graphics :)
[/LIST]

So yay, success for me, thanks again, and be sure to go see the movie! :popcorn:

---

### Post by josys36 on 2007-08-04
> **walkerk said:**
> Another user had issues with VMWare but he was able to fix the issues easily. Read back several pages and perhaps PM him. I didn't experiance any issues the VirtualBox..

I did review the posts first. The problem is not getting the VMWare product installed. The problem is that no matter what I do I don't have network support in my guest networks. 

Has anyone else experienced this? If so let me know how you fixed it.

Thanks!

Jason

---

### Post by flyinraptr on 2007-08-05
> **walkerk said:**
> Glad to hear it guys :) Did you guys use the script of did you do it manually? Just curious to see if anyone is using the script or not..

I tried the script .... didn't seem to work - the new kernel did not show up in the menu list.  I then followed the manual instructions and it worked.  The only thing that appears to be broken is the sound from the tv card ... the music player is working.

---

### Post by walkerk on 2007-08-05
> **flyinraptr said:**
> I tried the script .... didn't seem to work - the new kernel did not show up in the menu list.  I then followed the manual instructions and it worked.  The only thing that appears to be broken is the sound from the tv card ... the music player is working.

Glad it worked. As for the script I added a few timeouts between updating and installing.. hopefully this will prevent it from getting hung up. The script does exactly what the manual instructions say. I just left it up to each user because I know some people aren't trusting (understandable.. even though you can open the sript up :))

---

### Post by walkerk on 2007-08-05
> **jamieplucinski said:**
> Best. Movie. Ever. It's been out here a while, but I wanted to avoid the crowds and sat in a relatively quiet theater, quiet until the movie started that is... hilarious, exactly what a Simpsons movie should be.

Anyways I am up and running with direct rendering, yay! Here's my howto for the 200M chipset:

[LIST=1]
[*]Install the kernel as per this guide
[*]Re-add the gutsy repos and then do apt-get update
[*]Do apt-get install build-essential and install all of the required libs (just answer Y)
[*]Remove the gutsy repo and do apt-get update again.
[*]Install Envy and do what you will with it
[*]Reboot when prompted by Envy, et voila, direct rendering enabled for your graphics :)
[/LIST]

So yay, success for me, thanks again, and be sure to go see the movie! :popcorn:

Glad to hear it's all working. I've added a link to this post on the main post so that others can follow. Thanks for the movie review. Looking forward to seeing it..

---

### Post by obavjestenja on 2007-08-05
thanks again , my wireless work great ,laptop run faster,laptop temperature much lower.

---

### Post by bluknight on 2007-08-05
Thank you! It works for me even tho Feisty kernel 2.6.20-16 never booted my system. I had to boot the Feisty install with the Edgy kernel 2.6.17-12, using your kernel.sh, and now running Gutsy kernel 2.6.22-9:

Spec: Dell-Optiplex-Intel GX620 (Pentium 4-HT)-WD800JD(ATA)-ST980815(SATA)-IOZip250,Philips 170B2 Monitor, USB Keybrd
BCM5700-Intel-IC4-7(AC97Sound)-AcctonWirelessChip-Intel82-945G Display USB-PS2 & USB Ext.HDs (Samsung and Cypress AT2LP)

Software: Ubuntu CE-3.3 on USB ExtHD Maxtor booted with Edgy kernel
Win on SATA master :(, PCL on IDE-HD,

Now I don't have to wait for another Ubuntu 3.2 kernel :)

---

### Post by walkerk on 2007-08-05
> **bluknight said:**
> Thank you! It works for me even tho Feisty kernel 2.6.20-16 never booted my system. I had to boot the Feisty install with the Edgy kernel 2.6.17-12, using your kernel.sh, and now running Gutsy kernel 2.6.22-9:

Spec: Dell-Optiplex-Intel GX620 (Pentium 4-HT)-WD800JD(ATA)-ST980815(SATA)-IOZip250,Philips 170B2 Monitor, USB Keybrd
BCM5700-Intel-IC4-7(AC97Sound)-AcctonWirelessChip-Intel82-945G Display USB-PS2 & USB Ext.HDs (Samsung and Cypress AT2LP)

Software: Ubuntu CE-3.3 on USB ExtHD Maxtor booted with Edgy kernel
Win on SATA master :(, PCL on IDE-HD,

Now I don't have to wait for another Ubuntu 3.2 kernel :)

Glad to hear it :)

---

### Post by bowens44 on 2007-08-05
I didn't use the script but followed your manual instructions instead Everything appears to have  worked perfectly!

Athlon XP 3800
Kubuntu 7.04
GeForce 7600

Thanks!!

---

### Post by walkerk on 2007-08-05
> **bowens44 said:**
> I didn't use the script but followed your manual instructions instead Everything appears to have  worked perfectly!

Athlon XP 3800
Kubuntu 7.04
GeForce 7600

Thanks!!

No problem. Glad all is well :)

---

### Post by Gremlinzzz on 2007-08-05
Love this kernel solid as a rock hope too get 2.6.23
:guitar:

---

### Post by exploder on 2007-08-05
I followed the manual install instructions and all is well! Thanks for the "How to"!

Athlon XP 1800+
Radeon 7200
Biostar VIA Mainboard
Vinal AC 97onboard  sound
Phillips CD-RW 24x
Pioneer DVD-ROM
VIA onboard nic

LinuxMint 3.0 Cassandra

---

### Post by Specter043 on 2007-08-05
Followed the manual instructions and worked fine for me too, (after xorg reconfigure thing, which my graphics card needs for some reason, or it won't give me gnome)  but anyways

Pentium 4 3.06 HT
1 GB RAM
Geforce FX 5200 256 MB
Ubuntu 7.04

---

### Post by walkerk on 2007-08-05
> **exploder said:**
> I followed the manual install instructions and all is well! Thanks for the "How to"!

Athlon XP 1800+
Radeon 7200
Biostar VIA Mainboard
Vinal AC 97onboard  sound
Phillips CD-RW 24x
Pioneer DVD-ROM
VIA onboard nic

LinuxMint 3.0 Cassandra

> **Specter043 said:**
> Followed the manual instructions and worked fine for me too, (after xorg reconfigure thing, which my graphics card needs for some reason, or it won't give me gnome)  but anyways

Pentium 4 3.06 HT
1 GB RAM
Geforce FX 5200 256 MB
Ubuntu 7.04

Good to hear :) Enjoy the new kernel.

---

### Post by ugm6hr on 2007-08-05
Script installation - dead easy :)

Was a bit worried after the reboot - Grub error 17!  Turns out the auto grub update had put hdo,6 instead of hd0,5 on all the Ubuntu entries... not sure why!  Anyway - a manual edit (10 secs) later, and I'm now up and running.

Many thanks.
Acer Aspire 5051AWXMi (laptop).

PS: will this cause problems when I upgrade to Gutsy?  Is it going to be sensible to remove the new kernel prior to upgrade?  If so - I'd better remember to do it!

---

### Post by walkerk on 2007-08-05
> **ugm6hr said:**
> Script installation - dead easy :)

Was a bit worried after the reboot - Grub error 17!  Turns out the auto grub update had put hdo,6 instead of hd0,5 on all the Ubuntu entries... not sure why!  Anyway - a manual edit (10 secs) later, and I'm now up and running.

Many thanks.
Acer Aspire 5051AWXMi (laptop).

PS: will this cause problems when I upgrade to Gutsy?  Is it going to be sensible to remove the new kernel prior to upgrade?  If so - I'd better remember to do it!

Not sure why it did that with your Grub (It's the package that alters the Grub menu.lst) .. You're the first user to have that issue, although it was an easy fix.

Also, It shouldn't cause any problems when you upgrade as it is the same kernel currently being developed in Gutsy. Glad it worked for you :)

---

### Post by fooman on 2007-08-05
forgot to mention that on my desktop... my xp raid array and my suse hard drive entries were removed from the grub menu after the kernel upgrade.

not a problem as i keep a backup for just such an occasion.  a quick copy and paste took care of that.   :-D  

btw...those drives were not attached when i installed kubuntu.  they were added manually a few days after the install.

maybe thats why they were removed?

grub on my dual boot laptop (xpmce-kubuntu) was not altered except for the new kernel addition.

---

### Post by HarshReality on 2007-08-05
I did this to try and get my ENE Cardreader going on my laptop, suprise! still doesnt work.

---

### Post by walkerk on 2007-08-05
> **HarshReality said:**
> I did this to try and get my ENE Cardreader going on my laptop, suprise! still doesnt work.

Sorry your card reader doesn't work but thats not really the point of this thread. If you had a problem upgrading the kernel thats one thing. Please don't spam this thread with nonsense.

BTW. Enjoy the new kernel.

---

### Post by obscur156 on 2007-08-06
Worked for me, i have used your script.

Thanks a lot.=D>

---

### Post by walkerk on 2007-08-06
> **obscur156 said:**
> Worked for me, i have used your script.

Thanks a lot.=D>

Of course. Enjoy :)

---

### Post by Depressed Man on 2007-08-06
I think I'm going install Gutsy just to see if my battery life is longer (right now I get about 2 hours 25 minutes). 

But I'm curious about this message. 

Do not upgrade any packages while you have the Gutsy repository open. PLEASE DO NOT DO THIS. It's hosed one users box already..

Does this mean if I go back to Feisty and I have Gutsy's repos added to my sources.list and I automatically update it would hose my system?

---

### Post by walkerk on 2007-08-06
> **Depressed Man said:**
> I think I'm going install Gutsy just to see if my battery life is longer (right now I get about 2 hours 25 minutes). 

But I'm curious about this message. 

Do not upgrade any packages while you have the Gutsy repository open. PLEASE DO NOT DO THIS. It's hosed one users box already..

Does this mean if I go back to Feisty and I have Gutsy's repos added to my sources.list and I automatically update it would hose my system?

If you upgrade to Gutsy you'll be OK but it's not good practice to mix programs compiled for different versions. I'm not convinced that this ONE users box was hosed this way as I upgraded gcc and libwnck (from 18 to 22) which upgraded like 900 packages.. all without problems. Honestly that warning is just to stop new users from doing this.. they might not be able to recover easily..

---

### Post by walkerk on 2007-08-06
**I cleaned up the script a bit.**

---

### Post by Depressed Man on 2007-08-06
Ah ok, I'm just asking because right now I have Feisty working on my laptop. With suspend, and other things working. And the main reason I want to upgrade is to see if I can get more then 2 hrs and 25 minutes with the battery (it should be lasting around 3-4 hours). But Power Top needs a higher kernal. 

But in case I upgraded and suspend wasn't working I could retreat back to my previous kernal. But if I upgrade everything then it'd be a toughy. So what should I do?

---

### Post by walkerk on 2007-08-06
> **Depressed Man said:**
> Ah ok, I'm just asking because right now I have Feisty working on my laptop. With suspend, and other things working. And the main reason I want to upgrade is to see if I can get more then 2 hrs and 25 minutes with the battery (it should be lasting around 3-4 hours). But Power Top needs a higher kernal. 

But in case I upgraded and suspend wasn't working I could retreat back to my previous kernal. But if I upgrade everything then it'd be a toughy. So what should I do?

Of course you can. This doesn't remove your other kernels. If you're unhappy you can just boot into your old kernel (reboot and press esc at grub 1.5) and follow the uninstall instructions..

I'm sure you will not be disappointed..

---

### Post by walkerk on 2007-08-07
> **Depressed Man said:**
> Ah ok, I'm just asking because right now I have Feisty working on my laptop. With suspend, and other things working. And the main reason I want to upgrade is to see if I can get more then 2 hrs and 25 minutes with the battery (it should be lasting around 3-4 hours). But Power Top needs a higher kernal. 

But in case I upgraded and suspend wasn't working I could retreat back to my previous kernal. But if I upgrade everything then it'd be a toughy. So what should I do?

Did you give it a try?

---

### Post by bluknight on 2007-08-07
Just a small matter for those using CE with Dansguardian- after rebooting to Gutsy kernel the browser will not connect, even network is up (synaptic ok, ping ok, etc). To connect open a terminal and do: sudo danguardian
and all's well.

---

### Post by walkerk on 2007-08-07
> **bluknight said:**
> Just a small matter for those using CE with Dansguardian- after rebooting to Gutsy kernel the browser will not connect, even network is up (synaptic ok, ping ok, etc). To connect open a terminal and do: sudo danguardian
and all's well.

Good to know..

---

### Post by sebbouckaert on 2007-08-07
> **walkerk said:**
>  2 lines in the terminal to configure it to work with the new kernel.. shouldn't be tough w/ VMWare.

If anyone would have happened to have found these 2 lines I'd be most grateful. I upgraded the kernel (using the script) without any problems but getting VMware Server to work again has got me puzzled all night, without succes :confused:

Would liek to fix this, have done quite some tweaking in my virtual Windows XP box

EDIT: FIXED the problem: uninstalled VMWare server from repositories. Then re installed it with tar package from their site, that worked halfway but compiling the kernel module failed. Then I ran the VMware-any-any-update113, which went through the configuration again,after that everything worked again.

---

### Post by fenario on 2007-08-08
HOWTO not so simple kernel upgrade without internet connection on 
ubuntu 7.04. I can get kernels via windows.
how do I install it manually. Hopefully avoiding the dependency nightmare.Would appreciate help.Thanks friends.
fen

---

### Post by walkerk on 2007-08-08
> **fenario said:**
> HOWTO not so simple kernel upgrade without internet connection on 
ubuntu 7.04. I can get kernels via windows.
how do I install it manually. Hopefully avoiding the dependency nightmare.Would appreciate help.Thanks friends.
fen

Go to the Gutsy repos from you Windows machine and download the following packages:```

libc6
linux-restricted-common-modules 
linux-backports-modules-2.6.22-9-generic 
linux-headers-2.6.22-9
linux-headers-2.6.22-9-generic
linux-image-2.6.22-9-generic
linux-restricted-modules-2.6.22-9-generic
linux-ubuntu-modules-2.6.22-9-generic
```

Now you need to copy those from your NTFS partition to /var/cache/apt/archives:

The quickest way woulf be to open up nautilus as root and do this
```
gksudo nautilus
```

or you can use mv in the terminal (you'll need to use sudo to copy to /var/cache/apt/archives

alright.. now that you've moved the files, in termnial:
```
cd /var/cache/apt/archives
```
```
sudo dpkg -i libc6.deb
sudo dpkg -i linux-restricted-common-modules.deb
sudo dpkg -i linux-backports-modules-2.6.22-9-generic.deb
sudo dpkg -i linux-headers-2.6.22-9.deb
sudo dpkg -i linux-headers-2.6.22-9-generic.deb
sudo dpkg -i linux-image-2.6.22-9-generic.deb
sudo dpkg -i linux-restricted-modules-2.6.22-9-generic.deb
sudo dpkg -i linux-ubuntu-modules-2.6.22-9-generic.deb
```

You may need to double check those filenames..

This should do the trick. Let me know if you have troubles..

---

### Post by yopnono on 2007-08-08
Just like to say that I did try this on a ubuntu Edgy... and it's running the latest gutsy kernel on this 6.10 edgy.

---

### Post by gav616 on 2007-08-08
i edited your script to get the kernel meta packages, so looking for and emending the script when a new kernel is out will not be needed, just checking once a week will do :)

thanks anyways.

---

### Post by walkerk on 2007-08-08
> **yopnono said:**
> Just like to say that I did try this on a ubuntu Edgy... and it's running the latest gutsy kernel on this 6.10 edgy.

Glad to hear. I added a note on the original thread that it works with Edgy.

> **gav616 said:**
> i edited your script to get the kernel meta packages, so looking for and emending the script when a new kernel is out will not be needed, just checking once a week will do :)

thanks anyways.

Good call. I've updated the script. Just testing it on my own system before I post it up. Thanks

---

### Post by walkerk on 2007-08-08
**Ok. I've updated the script to call for the linux kernel meta packages.**

It seems that -10 is just about to be released. For those users that have used this script before, and want to be able to continue upgrading, you'll  need to use the new script that I've just posted.

Thanks

---

### Post by colo505 on 2007-08-08
What difference in performance/ stability do you notice after the upgrade?

---

### Post by walkerk on 2007-08-08
> **colo505 said:**
> What difference in performance/ stability do you notice after the upgrade?

Given from the other users responses:

ACPI functioning better.
Wifi working flawlessly (where it was buggy but working w/ 2.6.20-16)


With my personal machine, ACPI and wireless worked well already. You'd need to research the new functions of kernel version 2.6.22 (which there are quite a few)..

---

### Post by yopnono on 2007-08-08
> **colo505 said:**
> What difference in performance/ stability do you notice after the upgrade?

In my case I did not need a newer kernel. Since the only thing that really did not work was suspend but...  I did give it a try with the new kernel, and now the suspend work aswell.

Running Edgy with Gutsy kernel.

Ah other thing in th processes monitor (System monitor) the memory values seems well of the chart :)

---

### Post by gav616 on 2007-08-08
when it askes to install a higher gutsy version of libc6, (obviously because the newer kernel depends on it) do you need to keep upgrading libc6 ?

because newer versions are coming out of libc6, is sticking with the version you used when upgrading the kernels recommended?

---

### Post by walkerk on 2007-08-08
> **gav616 said:**
> when it askes to install a higher gutsy version of libc6, (obviously because the newer kernel depends on it) do you need to keep upgrading libc6 ?

because newer versions are coming out of libc6, is sticking with the version you used when upgrading the kernels recommended?

libc6 needs to be upgraded for the new kernel..

I've upgraded libc6 each time its asked me to and without any issues.... I honestly don't see any issues. 

If I ran into a problem I would let you guys know before you ran into the same problem. I upgrade everyday (if possible)

---

### Post by arrrghhh on 2007-08-08
ok... so i updated using your script.  all went well, and the new gusty kernel runs great.  however, i use vmware server - and evidently this new kernel is not up to running it.  maybe i need to update vmware?  

i open vmware server, click "connect" on local host like i always do.  then when i click on the "power on virtual machine" it flashes to the black screen as if it's booting, then goes back to the main screen and gives me a blank error... literally.  if i boot back into the old kernel vmware works great.  any ideas?  thanks.

---

### Post by Gremlinzzz on 2007-08-08
According to this Kernel Performance Test there's not much of a difference between the old and the new.
[http://www.phoronix.com/scan.php?page=article&item=797&num=1](http://www.phoronix.com/scan.php?page=article&item=797&num=1)
:guitar:

---

### Post by vikrant82 on 2007-08-08
I too successfully did the upgrade without any issues.

Any fix for weird memory numbers in system-monitor?? However its cute to see Xorg and Mozilla taking up 0 bytes.:)

---

### Post by walkerk on 2007-08-08
> **vikrant82 said:**
> I too successfully did the upgrade without any issues.

Any fix for weird memory numbers in system-monitor?? However its cute to see Xorg and Mozilla taking up 0 bytes.:)

LOL. None that I know of. Run the script again in a few days and it should pull version 2.6.22-10 (perhaps that release will address this minor issue)

Glad it worked well for you :)

---

### Post by DagMan on 2007-08-08
Is this a safe thing to do?  It seems to me that Gutsy being in development, things are going upstream and the kernel may at some point, if not already, be compiled against libraries that aren't compatible to be safely running on Feisty.  How much do you know about what's happening with Gutsy and how carefully are you checking this out and staying abreast... for example I was running it a short time ago and I think I remember a compiler update though it wasn't a large upstream step.

Wouldn't it be much safer to just download the source packages and compile them on a computer running Feisty Fawn, or even just try to let prevu do it automatically if it's able to?

---

### Post by walkerk on 2007-08-08
> **DagMan said:**
> Is this a safe thing to do?  It seems to me that Gutsy being in development, things are going upstream and the kernel may at some point, if not already, be compiled against libraries that aren't compatible to be safely running on Feisty.  How much do you know about what's happening with Gutsy and how carefully are you checking this out and staying abreast... for example I was running it a short time ago and I think I remember a compiler update though it wasn't a large upstream step.

Wouldn't it be much safer to just download the source packages and compile them on a computer running Feisty Fawn, or even just try to let prevu do it automatically if it's able to?

Ubuntu isn't actually developing the kernel (2.6.22).. the are revising it to work "better" and more "secure" with Ubuntu.. The real developed kernel is now 2.6.23...

Now thats out of the way..

I am the front runner on this. I preform the update every morning on 3 seperate systems. If I come across any problems I will alter the original thread. Up until now there haven't been any issues.. to include an upgrade of libc6.

edit: As far as Gusty, I have a machine running it as well.

**And everything is easliy reversed.** If you don't want to try thats all fine and well...

---

### Post by pedbsktbll on 2007-08-08
Hey, err um what happens if you forget to remove the package? I upgraded the kernel, and all worked fine. But then synaptic told me I had like 600 upgrades and I was like wtf.. didn't pay attention, and I installed them all.. I booted up to a surprise lol.. Anyway, is there any way to uninstall gusty? To downgrade the distribution?

---

### Post by sebbouckaert on 2007-08-08
> **arrrghhh said:**
> ok... so i updated using your script.  all went well, and the new gusty kernel runs great.  however, i use vmware server - and evidently this new kernel is not up to running it.  maybe i need to update vmware?  

i open vmware server, click "connect" on local host like i always do.  then when i click on the "power on virtual machine" it flashes to the black screen as if it's booting, then goes back to the main screen and gives me a blank error... literally.  if i boot back into the old kernel vmware works great.  any ideas?  thanks.

Had the same issue, see my previous post in this thread

---

### Post by walkerk on 2007-08-08
> **sebbouckaert said:**
> Had the same issue, see my previous post in this thread

This is a VMWare issue.. not a kernel issue. A good step would be to re-install VMWare.

---

### Post by walkerk on 2007-08-08
> **pedbsktbll said:**
> Hey, err um what happens if you forget to remove the package? I upgraded the kernel, and all worked fine. But then synaptic told me I had like 600 upgrades and I was like wtf.. didn't pay attention, and I installed them all.. I booted up to a surprise lol.. Anyway, is there any way to uninstall gusty? To downgrade the distribution?

Uninstall Gutsy? You didn't install Gutsy Gibbon.. only the kernel and it's dependencies and libs.. (I used this script today.)

Is it not working for you? Let me know.. I'll alter the script. I changed it today to use the meta packages.. no real difference from the original script..

Please let me know

---

### Post by DagMan on 2007-08-08
> **walkerk said:**
> Ubuntu isn't actually developing the kernel (2.6.22).. the are revising it to work "better" and more "secure" with Ubuntu.. The real developed kernel is now 2.6.23...

Now thats out of the way..

I am the front runner on this. I preform the update every morning on 3 seperate systems. If I come across any problems I will alter the original thread. Up until now there haven't been any issues.. to include an upgrade of libc6.

edit: As far as Gusty, I have a machine running it as well.

**And everything is easliy reversed.** If you don't want to try thats all fine and well...

My question is not who writes kernels or what the current development version is, but whether or not it is safe to run a kernel compiled for gusty on a feisty or edgy system and if you are staying abreast of the packages used in gutsy that go into the simple compilation of the packages in the tutorial in relation to their compatibility with the OS version the rest of us are running?
Your answer wasnt clear.  You are the front runner in the Gutsy kernel development and perform an update every morning on 3 machines as part of the development team, or you mean that you are maintaining the thread by trial and error on your own systems using the packages that the developers put out?


**pedbsktbll**, did you install upgrades before removing any lines in /etc/apt/sources.list refering to gutsy?  You should take out the line or other lines if you have them, and update the repo using apt-get update or reload in synaptic before installing any updates.

---

### Post by walkerk on 2007-08-08
> **pedbsktbll said:**
> Hey, err um what happens if you forget to remove the package? I upgraded the kernel, and all worked fine. But then synaptic told me I had like 600 upgrades and I was like wtf.. didn't pay attention, and I installed them all.. I booted up to a surprise lol.. Anyway, is there any way to uninstall gusty? To downgrade the distribution?

Oh man.. Did you accidentally install Gutsy upgrades from update-manager? ([COLOR="Red"]like i said not to[/COLOR])?

Not to sure how the reverse this.. let me look at a solution..

---

### Post by pedbsktbll on 2007-08-08
> **walkerk said:**
> Oh man.. Did you accidentally install Gutsy upgrades from update-manager? ([COLOR="Red"]like i said not to[/COLOR])?

Not to sure how the reverse this.. let me look at a solution..Yes, exactly how you said not to. I rebooted with the new kernel, and went on for a bit.. but then the update-manager informed me of updates, and I clicked to install without paying any attention at all... So yup, I'm running Gutsy now.. Has a nice new look an feel, but It's rather buggy, and I'd like to know how to undo this... I'd greatly appreciate any help.

---

### Post by DagMan on 2007-08-08
Don't know if this works.

I haven't done this or have heard of the results of anyone doing it.  It seems to be the way it's done in Debian as well and is described as having glitches.

I don't have the /etc/apt/preferances file on my machine so I'm guessing it needs to be created.

[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

It looks like that for every line in the /etc/apt/sources.list file that says gutsy you want a duplicate one as well but that says feisty.  Then apt-get update and the /etc/apt/preferances file hopefully pins the version down to feisty so you would then apt-get update and apt-get upgrade.
In the Wiki, the file /etc/apt/preferances uses hoary and breezy but you would want to substitute feisty and gutsy respectivley.

If this works, then afterwards take out all the lines that say gutsy in them and again do an apt-get update once again.  Then take out what you entered into the /etc/apt/preferences file or just remove the file if you had to create it from scratch.


Good luck.
Ask if this is unclear and you need a step by step, before you start.

---

### Post by mavila on 2007-08-08
Ive been fumbling with SMP support fro some time... Just couldn't find the answer. It was working fine when I upgraded to Feisty, and I noticed a few weeks ago that the machine was simply dragging but. I tried most everything out there - this thread as well (upgrading to a development kernel) to no avail.

What I recall changing about a month ago was physically putting 4Gig of RAM in the box, and making TWO changes in the BIOS, 1) cacheable BIOS, and 2) cacheable Video. - I turned BOTH off, rebooted and viola! Im seeing both cores again.

Not sure what the issue really was, but that change makes this machine run like a bat out of hell again!

---

### Post by pedbsktbll on 2007-08-08
Awesome thanks. I've been searching everywhere for an article like this. I'll tell ya how it turns out..

---

### Post by pedbsktbll on 2007-08-08
> **DagMan said:**
> Don't know if this works.

I haven't done this or have heard of the results of anyone doing it.  It seems to be the way it's done in Debian as well and is described as having glitches.

I don't have the /etc/apt/preferances file on my machine so I'm guessing it needs to be created.

[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

It looks like that for every line in the /etc/apt/sources.list file that says gutsy you want a duplicate one as well but that says feisty.  Then apt-get update and the /etc/apt/preferances file hopefully pins the version down to feisty so you would then apt-get update and apt-get upgrade.
In the Wiki, the file /etc/apt/preferances uses hoary and breezy but you would want to substitute feisty and gutsy respectivley.

If this works, then afterwards take out all the lines that say gutsy in them and again do an apt-get update once again.  Then take out what you entered into the /etc/apt/preferences file or just remove the file if you had to create it from scratch.


Good luck.
Ask if this is unclear and you need a step by step, before you start.
I did exactly what you said, but I think there is probably something that needs to be changed with the preferences file.

When I try to run sudo apt-get dist-upgrade, I get the following error:
E: Invalid record in the preferences file, no Package header

[edit]Should I just pull a 'windows', and reinstall?

---

### Post by DagMan on 2007-08-08
I honestly don't know.. perhaps try apt-get upgrade rather than dist-upgrade but that's all I can think of, that perhaps the computer is still assigning itself as Feisty since it wasn't a full upgrade and dist-upgrade is not working.  I can't find anything in google that's helpful right now.

You did swap out the hoary and breezy for feisty and gutsy though I hope.

If nothing else works, Gutsy is only a couple months away from it's planned release date and you're forced to choose between upgrading entirely or reinstalling... or keeping it as it is now that I think of it.

To put things back... whatever you choose, you want to delete the /etc/apt/preferances file when you're done with the downgrade or attempted downgrade.  

I'm really curious if the apt-get ugrade does it though btw, so if can post what ended up happening that would be great.
Don't feel bad btw, I've done this before on accident and have heard worse stories from people who know too well what they're doing.


Remember that your sources.list file will need to be edited to have whatever you go with, just feisty, just gutsy, or if you pull the wacky thing I did a while back, keeping both.

---

### Post by pedbsktbll on 2007-08-08
> **DagMan said:**
> I honestly don't know.. perhaps try apt-get upgrade rather than dist-upgrade but that's all I can think of, that perhaps the computer is still assigning itself as Feisty since it wasn't a full upgrade and dist-upgrade is not working.  I can't find anything in google that's helpful right now.

You did swap out the hoary and breezy for feisty and gutsy though I hope.

If nothing else works, Gutsy is only a couple months away from it's planned release date and you're forced to choose between upgrading entirely or reinstalling... or keeping it as it is now that I think of it.

To put things back... whatever you choose, you want to delete the /etc/apt/preferances file when you're done with the downgrade or attempted downgrade.  

I'm really curious if the apt-get ugrade does it though btw, so if can post what ended up happening that would be great.
Don't feel bad btw, I've done this before on accident and have heard worse stories from people who know too well what they're doing.


Remember that your sources.list file will need to be edited to have whatever you go with, just feisty, just gutsy, or if you pull the wacky thing I did a while back, keeping both.Alright, thanks for your help. I did substitute feisty and gutsy btw ;) Hmm.. I tried just deleting that preferences file, and everything seemed to work better. This is what happens, maybe it makes more sense to someone what the problem is:

josh@josh-Ubuntu:~$ sudo apt-get update
[sudo] password for josh:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Get:3 [http://mirror.noreply.org](http://mirror.noreply.org) feisty Release.gpg [189B]
Ign [http://mirror.noreply.org](http://mirror.noreply.org) feisty/main Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://mirror.noreply.org](http://mirror.noreply.org) feisty Release
Ign [http://mirror.noreply.org](http://mirror.noreply.org) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Ign [http://mirror.noreply.org](http://mirror.noreply.org) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://mirror.noreply.org](http://mirror.noreply.org) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://mirror.noreply.org](http://mirror.noreply.org) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Fetched 7B in 18s (0B/s)
Reading package lists... Done
josh@josh-Ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  gnome-orca libcairo-java libglib-java libgtk-java libgtk-jni vlc vlc-nox
  wlassistant
The following packages will be upgraded:
  apache2-utils apt apt-utils binfmt-support bum gstreamer0.10-ffmpeg
  gstreamer0.10-plugins-ugly hibernate liba52-0.7.4 libcompizconfig0
  libdvbpsi4 libdvdnav4 libdvdread3 libportaudio0 libqt4-core libqt4-dev
  libqt4-gui libqt4-qt3support libqt4-sql libvlc0 libwxbase2.6-0 libwxgtk2.6-0
  ndisgtk privoxy qt4-designer sun-java6-bin sun-java6-jre sun-java6-plugin
  tor tsocks uswsusp vnc-common wine wireshark wireshark-common xchat
  xchat-common xvncviewer
38 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
4 not fully installed or removed.
Need to get 0B/102MB of archives.
After unpacking 63.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
josh@josh-Ubuntu:~$


I hope that isn't too long.. anyway, I'd like to get this resolved b/c for some reason tzdata doesn't work and I can't upgrade any other programs.. It's strange..

I get this error in synaptic:
E: tzdata: subprocess post-installation script returned error exit status 10
E: util-linux: dependency problems - leaving unconfigured

---

### Post by holdennutta on 2007-08-08
Thank you very much for this guide. 

I used the manual way of doing it and it worked great. Fixed some issues I was having with laptop not noticing it had a battery et al.

Cheers!

---

### Post by DagMan on 2007-08-09
I don't know myself **pedbsktbll**,

I think maybe a thread up in the general help area would be warranted now.  Deleting the preferance file you'de be grabbing gutsy packages now.  Looks like it was the thing to do though since it was just producing the error.  I'de try doing a dist-upgrade at this point but keep in mind that doing so will delete packages that aren't implemented in gutsy.  When I did mine I came back to feisty because although compiz was installed by default in gutsy and looked great, it didn't work 100% on my system so I went with beryl but emerald and heliodor didn't work so I used aquamarine which pulled in Kwin and all kinds of KDE dependancies for it that I could have done without.  I also got really tired of updating.

My advice is to go ahead with dist-upgrade with just gutsy lines in your source.list and hope that it solves the dependancy problem but first maybe try simple stuff like **apt-get install -f** but that's just me.

Also maybe make a thread though first if you want to get more opinions and throw a link down here to what hasn't worked or explain it well.  If you do a make a thread though, I wouldn't mind if you posted a link from here up to is so I can find it if I have anything further and **walkerk** hopefully hasn't given up on you either once hefinds extra time to get behind the computer in his part of the world.

---

### Post by leo_rockway on 2007-08-09
uname -r
2.6.22-9-generic

thanks for posting this guide :-D

---

### Post by walkerk on 2007-08-09
> **pedbsktbll said:**
> Yes, exactly how you said not to. I rebooted with the new kernel, and went on for a bit.. but then the update-manager informed me of updates, and I clicked to install without paying any attention at all... So yup, I'm running Gutsy now.. Has a nice new look an feel, but It's rather buggy, and I'd like to know how to undo this... I'd greatly appreciate any help.

Yea, this is why I put the script part first on the original thread (it automatically removes the gutsy repos before you can upgrade anything else..)

> **DagMan said:**
> I don't know myself **pedbsktbll**,

I think maybe a thread up in the general help area would be warranted now.  Deleting the preferance file you'de be grabbing gutsy packages now.  Looks like it was the thing to do though since it was just producing the error.  I'de try doing a dist-upgrade at this point but keep in mind that doing so will delete packages that aren't implemented in gutsy.  When I did mine I came back to feisty because although compiz was installed by default in gutsy and looked great, it didn't work 100% on my system so I went with beryl but emerald and heliodor didn't work so I used aquamarine which pulled in Kwin and all kinds of KDE dependancies for it that I could have done without.  I also got really tired of updating.

My advice is to go ahead with dist-upgrade with just gutsy lines in your source.list and hope that it solves the dependancy problem but first maybe try simple stuff like **apt-get install -f** but that's just me.

Also maybe make a thread though first if you want to get more opinions and throw a link down here to what hasn't worked or explain it well.  If you do a make a thread though, I wouldn't mind if you posted a link from here up to is so I can find it if I have anything further and **walkerk** hopefully hasn't given up on you either once hefinds extra time to get behind the computer in his part of the world.

Haven't forgotten about him. I have to get my newborn a passport today and then I'll have some spare time to help out.

---

### Post by walkerk on 2007-08-09
> **leo_rockway said:**
> uname -r
2.6.22-9-generic

thanks for posting this guide :-D

> **holdennutta said:**
> Thank you very much for this guide. 

I used the manual way of doing it and it worked great. Fixed some issues I was having with laptop not noticing it had a battery et al.

Cheers!

Great to hear :)

---

### Post by qwerty1212 on 2007-08-09
uname -r
2.6.22-9-generic

Thanks for the guide

---

### Post by walkerk on 2007-08-09
> **qwerty1212 said:**
> uname -r
2.6.22-9-generic

Thanks for the guide

Of course :)

---

### Post by st33med on 2007-08-10
Ummm... Where's the attachment? I can't find the kernel.sh attachment!

---

### Post by oberoc on 2007-08-10
Does anybody know how to get the kernel options of a running kernel? I really don't want to recompile if I don't have to.

Thanks,
Tino

---

### Post by walkerk on 2007-08-10
> **oberoc said:**
> Does anybody know how to get the kernel options of a running kernel? I really don't want to recompile if I don't have to.

Thanks,
Tino

This doesn't require you to re-compile a kernel by yourself. This downloads (upgrades) the current kernel being developed in 7.10. Much like you might have automatically upgraded from 2.6.20-15 to -16 in Feisty.

---

### Post by walkerk on 2007-08-10
> **st33med said:**
> Ummm... Where's the attachment? I can't find the kernel.sh attachment!

Sorry. It seemed to of fallen of the thread. I just re-posted it. You can find it at the bottom of my first post. :)

---

### Post by Jim March on 2007-08-11
For me, this was a disaster.  Dunno why, but access to external disks became unstable, copy operations either failed or gave "permission denied" type errors.

Now automount is broken, both in the new kernel and when I revert back to the previous normal Feisty kernel in the menus (2.6.20-16).

I can manually mount via sudo, so it's not the disks.

I'm running an Acer laptop, Marvell/Sky2 Ethernet connection, Intel950 graphics, pretty normal stuff.

Normal Feisty was able to see my SD memory card slot.  The first thing the new kernel did was break access to that slot, requiring a USB2 adapter plug with it's own SD slot to read cards.  And that failure happened with both the new Gutsy kernel and original Feisty kernel.

So listen up folks: this can break things that won't get fixed by pulling the Gutsy kernel!!!  You Have Been Warned.

---

### Post by cor2y on 2007-08-11
Thanks for this guide.
When i upgraded to this new kernel the system slowdowns that i have been recently experiencing in Feisty stopped.
Simply launching a program or playing an audio or video file would bring the system to its knees.
Now that does't happen anymore.
Thank You

---

### Post by walkerk on 2007-08-11
> **Jim March said:**
> For me, this was a disaster.  Dunno why, but access to external disks became unstable, copy operations either failed or gave "permission denied" type errors.

Now automount is broken, both in the new kernel and when I revert back to the previous normal Feisty kernel in the menus (2.6.20-16).

I can manually mount via sudo, so it's not the disks.

I'm running an Acer laptop, Marvell/Sky2 Ethernet connection, Intel950 graphics, pretty normal stuff.

Normal Feisty was able to see my SD memory card slot.  The first thing the new kernel did was break access to that slot, requiring a USB2 adapter plug with it's own SD slot to read cards.  And that failure happened with both the new Gutsy kernel and original Feisty kernel.

So listen up folks: this can break things that won't get fixed by pulling the Gutsy kernel!!!  You Have Been Warned.

Sorry to hear this. You're the first user to have these issues.

---

### Post by walkerk on 2007-08-11
> **cor2y said:**
> Thanks for this guide.
When i upgraded to this new kernel the system slowdowns that i have been recently experiencing in Feisty stopped.
Simply launching a program or playing an audio or video file would bring the system to its knees.
Now that does't happen anymore.
Thank You

Glad it worked well for you :)

---

### Post by bluemarvel on 2007-08-11
Thanks for the tip and script. It worked wonderfully for me on my HP Pavilion dv9030us laptop 

$ uname -r
2.6.22-9-generic


In particular, this seems to have fixed the Firefox & Flash freeze up bug I was experiencing when trying to navigate through YouTube and MySpace video pages. I haven't had a crash since the kernel upgrade.

Thanks!!

---

### Post by el mariachi on 2007-08-11
The installation went fine but it crashed my X server (as one should expect, since I forgot to uninstall it first...) 

I have a nvidia GeForce 6600GT gpu and the drivers were installed with envy (before the kernel upgrade) how should I proceed? reinstall through envy?

EDIT: Fixed it myself. 

everything works now, with an overall faster feeling. What were the major changes in the kernel (in layman's terms)

My specs:
Feisty Fawn
AMD A64 4000+
GeForce 6600GT
1Gb Ram
Audigy SE

---

### Post by walkerk on 2007-08-11
> **bluemarvel said:**
> Thanks for the tip and script. It worked wonderfully for me on my HP Pavilion dv9030us laptop 

$ uname -r
2.6.22-9-generic


In particular, this seems to have fixed the Firefox & Flash freeze up bug I was experiencing when trying to navigate through YouTube and MySpace video pages. I haven't had a crash since the kernel upgrade.

Thanks!!

Glad to hear its solved your issues. :)

> **el mariachi said:**
> The installation went fine but it crashed my X server (as one should expect, since I forgot to uninstall it first...) 

I have a nvidia GeForce 6600GT gpu and the drivers were installed with envy (before the kernel upgrade) how should I proceed? reinstall through envy?

EDIT: Fixed it myself. 

everything works now, with an overall faster feeling. What were the major changes in the kernel (in layman's terms)

My specs:
Feisty Fawn
AMD A64 4000+
GeForce 6600GT
1Gb Ram
Audigy SE

Glad it worked :) As for the kernel changes check out kernel.org

---

### Post by el mariachi on 2007-08-11
just a quick question. were the gutsy repos removed automatically or do I have to remove them myself? thanks, GREAT script :D

---

### Post by walkerk on 2007-08-11
> **el mariachi said:**
> just a quick question. were the gutsy repos removed automatically or do I have to remove them myself? thanks, GREAT script :D

They were removed automatically and immediately after installing the kernel. You don't have to do a thing. :)

---

### Post by el mariachi on 2007-08-11
Roger! Thanks again!

---

### Post by Brachabre on 2007-08-11
I tried upgrading my kernel once. (and it worked flawlessly, btw! Thanks!)

I went back to 2.6.20 because I lost direct rendering on my ati mobility x1400.

Will the ati 200m troubleshooting page help my problem too? (getting fglrx and direct rendering back to working)

---

### Post by walkerk on 2007-08-12
> **Brachabre said:**
> I tried upgrading my kernel once. (and it worked flawlessly, btw! Thanks!)

I went back to 2.6.20 because I lost direct rendering on my ati mobility x1400.

Will the ati 200m troubleshooting page help my problem too? (getting fglrx and direct rendering back to working)

Possibly. You might PM that user. He's a helpful user and I'm sure he'd head you down the right path.

---

### Post by newtothis on 2007-08-12
thanks alot just install using the script everything looks good so far .

---

### Post by walkerk on 2007-08-12
> **newtothis said:**
> thanks alot just install using the script everything looks good so far .

Glad it worked well for you :)

---

### Post by Sporkman on 2007-08-12
Will kernels ever get upgraded mid-Ubuntu release via apt-get upgrade? (i.e. could a new kernel automatically get installed on a currently-installed Ubuntu release, without upgrading to a new Ubuntu release?)

I'm wondering if I should be afraid of my computer no longer working correctly after doing apt-get upgrade... :?

---

### Post by walkerk on 2007-08-12
> **Sporkman said:**
> Will kernels ever get upgraded mid-Ubuntu release via apt-get upgrade? (i.e. could a new kernel automatically get installed on a currently-installed Ubuntu release, without upgrading to a new Ubuntu release?)

I'm wondering if I should be afraid of my computer no longer working correctly after doing apt-get upgrade... :?

ubuntu doesn't upgrade kernels once a they've released a version. the only upgrades are security issues with the original kernel. so no. :P

sudo apt-get upgrade is not like dist-upgrade which upgrades your os.

apt-get update only checks for updates to the sources.list (looking for your repositories).. Not permanent. Once you've downloaded the new kernel the Gutsy repos are removed. All back to normal running the new kernel.

---

### Post by Sporkman on 2007-08-12
> **walkerk said:**
> ubuntu doesn't upgrade kernels once a they've released a version. the only upgrades are security issues with the original kernel. so no. :P


Ah, good to know, thanks. :) I'm more of the stick-with-the-older-&-proven camp, rather than the early-adopter camp.

---

### Post by walkerk on 2007-08-12
> **Sporkman said:**
> Ah, good to know, thanks. :) I'm more of the stick-with-the-older-&-proven camp, rather than the early-adopter camp.

2.6.22 is stable. the only new releases with ubuntu are while the ubuntu devs fix small security issues..


new newest developing kernel within linux is 2.6.23 (which has a freeze date before the Gutsy release.. but the devs won't have time to work small issues.. )

---

### Post by Gremlinzzz on 2007-08-14
What kernel will gutsy end up with?no 2.6.23:confused:

---

### Post by walkerk on 2007-08-14
> **Gremlinzzz said:**
> What kernel will gutsy end up with?no 2.6.23:confused:

Gutsy will be released with 2.6.22.

2.6.23 will be out but it will leave little time for the Ubuntu devs to make security patches and such. There is a Poll thread on the forum that talks about this in length.

---

### Post by Brachabre on 2007-08-14
I love this update, but im suffering the loss of direct rendering (ATI mobility x1400 -- dell inspiron 9400 laptop)

I tried the fix that got it working for a 200M chipset, but had to undo everything. Envy has never worked for me for some reason. I made sure everything is primed and prepared (repositories enabled).

I guess now that Dell has something going with Ubuntu, maybe they can somehow pressure ATI into making better drivers...

Any help is appreciated!

ATM, I am using a fresh brand new install of feisty w/ kernel 2.6.22. That's a start!

---

### Post by BC7333 on 2007-08-14
Manual method worked just fine here and was easy enough to for this newbie to do.  Upgrade seems to have resolved some network problems I was experiencing.  2 weeks now with the new kernel and all ok.

Thanks!

---

### Post by cb474 on 2007-08-14
> **Brachabre said:**
> I love this update, but im suffering the loss of direct rendering (ATI mobility x1400 -- dell inspiron 9400 laptop)

I tried the fix that got it working for a 200M chipset, but had to undo everything. Envy has never worked for me for some reason. I made sure everything is primed and prepared (repositories enabled).

I guess now that Dell has something going with Ubuntu, maybe they can somehow pressure ATI into making better drivers...

Any help is appreciated!

ATM, I am using a fresh brand new install of feisty w/ kernel 2.6.22. That's a start!

I had the same problem with the ATI mobility X1400 on a ThinkPad T60. The 200M fix did work for me, but Envy did one strange thing that I had to correct to fix it. It edited /etc/default/linux-restricted-modules-common file to include fglrx under disabled modules. So I edited the file to remove "fglrx." I also reran several commands from how I first installed fglrx in Feisty, but I don't know if they were necessary:

sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

Once I did these things, direct rendering worked.

However, I then found that the 200M fix had broken direct rending when I booted into my old Feisty 2.6.20-16 kernel. I tried reinstalling fglrx the way I had originally done it and with Envy. Everything looked okay in xorg.conf and appeared to be installed but I couldn't get direct rendering working again on the old kernel.

I would get this info:

$ dmesg | grep fglrx
[ 35.668000] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[ 35.668000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[ 37.272000] [fglrx:firegl_unlock] *ERROR* Process 5130 using kernel context 0

$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

I also got messages like those, when direct rendering wasn't working at first with 2.6.22 (except *ERROR* Process 5536, instead of 5130), but again running Envy fixed things in 2.6.22 (plus editing the restricted modules files).

So, since I couldn't get my 2.6.20 kernel back to normal, as a last resort I just restored my whole parition with a backup image I had made in Acronis TrueImage (from my dual boot XP partition). When I have more time I'll try to get this working some other way. I think people should take note of this. It does appear that this upgrade (at least using the 200M fix) can effect your old install and it's not so easy to just go back or just boot into your old kernel and have everything be how it was.

I see at least a couple other people have had problems where they've had to reinstall. I personally think it's highly recommended if you have the hard drive space to back up your root partition before trying this or other elaborate modifications. I do it with Acronis because I can, I'm familiar with it, and it's easy. But here's a How To for doing this in Ubuntu: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087). It can turn a whole hours long pain reinstall into a five minute simple procedure that takes you right back to where you started before things went bad.

Anyway, that said, for the X1400 you might try the other fix that Walkerk started to outline earlier in this thread: [http://ubuntuforums.org/showpost.php?p=3132572&postcount=137]("http://ubuntuforums.org/showpost.php?p=3132572&postcount=137"). I haven't tried this yet, but it will be my next move.

---

### Post by cb474 on 2007-08-14
A couple other things:

Even when I had the 2.6.22 kernel working with direct rendering, I did notice one funny thing. It took much longer in the Nautilus file browser to access two FAT formated partitions I have that I'm sharing with my XP dual boot. And it didn't seem to remember the file structures for long when I went back to those partitions. Not every time but much more often than with the regular Feisty install (or with my old Edgy install) it would have to reread the whole file structure for several seconds before it could display it. And again, this reading also took longer than it does with my normal Feisty or old Edgy install. Odd.

Also, one other post said they wanted to try this to see if this upgrade improves battery life. I did notice with the 2.6.22 kernel that the battery was discharging at a significantly lower rate around 23W as compare to 26-28W with 2.6.20. On the other had, 23W is what I got with my old Edgy install (forget which kernel that was 2.6.17?). Still, it's an improvement for me over regular Feisty. And since you can run PowerTOP on 2.6.22 I'm hoping to improve on my already better battery life, once I hopefully get everything set straight with the direct rendering.

---

### Post by cb474 on 2007-08-15
Hmm. So I understand a little more about these fglrx drivers now, but I still don't have a solution that I like or understand really what's going on. I turns out that it was appropriate for Envy to blacklist "fglrx" in the disabled modules file. This disables the version of fglrx in linux-restricted-modules file, so that the version that Envy installs in the kernel can run. Of course, that didn't work for me. It only worked after I removed fglrx from the blacklist. So I guess that means that Envy did something that made the version of fglrx in linux-restricted-modules work, even though it wasn't working in the first place. I can only say I'm very preplexed.

After restoring my partition I installed 2.6.22 again and tried installing fglrx manually using method 1 in this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide"). It worked, although I got an error at the "sudo aticonfig --overlay-type=Xv" step. But still, as I said, on reboot, direct rendering with fglrx was working in 2.6.22. However, this messed up fglrx for my old 2.6.20 kernel again, because I guess now xorg-driver-fglrx was a version incompatible with the old kernel.

So back to restoring my parition! Perhaps next I will try installing the latest ATI driver in the kernel on my old version first, 2.6.20, and then do the same on 2.6.22. I'll use method 2 in the link above. That way they won't both be trying to use the same version of xorg-driver-fglrx, which won't work since they need different versions. Does that make sense? I'm not an expert at this stuff.

---

### Post by foureight84 on 2007-08-15
very nice!!! i had compiled one but wireless stopped working. i tried installing new drivers but didn't seem to solve the problem. this is such a better and faster way!! thanks!

---

### Post by foureight84 on 2007-08-15
i was running iwconfig to get readouts for my conkyrc and i just noticed this error message:

> 
Warning: Driver for device eth1 has been compiled with version 22
of Wireless Extension, while this program supports up to version 20.
Some things may be broken...


wireless works fine. but should i update my ipw2200 drivers?

---

### Post by walkerk on 2007-08-15
> **foureight84 said:**
> i was running iwconfig to get readouts for my conkyrc and i just noticed this error message:



wireless works fine. but should i update my ipw2200 drivers?

if its working and not bothering you i'd leave it alone. are you receiving that error in terminal when running conky? if so i wouldn't worry too much about that.

---

### Post by foureight84 on 2007-08-15
> **walkerk said:**
> if its working and not bothering you i'd leave it alone. are you receiving that error in terminal when running conky? if so i wouldn't worry too much about that.

it's not even conky. it's just in terminal when i run iwconfig. other than the message everything is running smoothly. oh btw, suspend finally works on my laptop. it was working with edgy but broke with feisty. however, when i resume after suspend, the lcd backlight doesn't come back on. i get a faint line on the right side of the monitor and it just fades and the screen goes completely black. do you know how to fix this?

---

### Post by arrrghhh on 2007-08-15
ok... so i apologize for bein an idiot, but i still cannot get vmware-server working.

i completely purged it with sudo aptitude purge vmware-server... and then reinstalled it from the repos by doin sudo aptitude install vmware-server.  everything goes fine, but i still cannot open my virtual machine.

i tried to do the vmware-any-any-update-113 thing and i can't get it working... at the end it says /usr/bin/vmware-config.pl doesn't exist.  i checked... and it doesn't.

any help would be greatly appreciated... uninstalling and reinstalling vmware-server several times had no effect.  thanks!

---

### Post by walkerk on 2007-08-15
> **arrrghhh said:**
> ok... so i apologize for bein an idiot, but i still cannot get vmware-server working.

i completely purged it with sudo aptitude purge vmware-server... and then reinstalled it from the repos by doin sudo aptitude install vmware-server.  everything goes fine, but i still cannot open my virtual machine.

i tried to do the vmware-any-any-update-113 thing and i can't get it working... at the end it says /usr/bin/vmware-config.pl doesn't exist.  i checked... and it doesn't.

any help would be greatly appreciated... uninstalling and reinstalling vmware-server several times had no effect.  thanks!

Sorry but I don't personally use VMWare (I use VirtualBox). Hopefully someone has had and solved these same issues.

Can you still boot into your older kernel to use VMWare? I know its not a permanent solution but it might do until you figure out a fix. :/

---

### Post by EXCiD3 on 2007-08-15
I used the manual instructions of updating my kernel and it worked flawlessly. My only problem is that after booting into the new kernel, my wireless can detect wifi networks, but i can never get past "Configuring the network device". It is an Intel® PRO/Wireless 3945ABG card in my HP dv9000. Is it just that a kernel module is not built into the newest kernel? I really don't understand how those work and I would like to use this newer kernel. When i switch back to the older kernel wireless works fine.

---

### Post by arrrghhh on 2007-08-15
yea, i can boot into my old kernel... i have found that new kernel is snappier, so i would like to get it working.  *sigh* i guess i should just wait until gusty is officially released in october!

this virtualbox is interesting tho, i've seen it mentioned several times.  are there any advantages to it over vmware?

---

### Post by walkerk on 2007-08-15
> **foureight84 said:**
> it's not even conky. it's just in terminal when i run iwconfig. other than the message everything is running smoothly. oh btw, suspend finally works on my laptop. it was working with edgy but broke with feisty. however, when i resume after suspend, the lcd backlight doesn't come back on. i get a faint line on the right side of the monitor and it just fades and the screen goes completely black. do you know how to fix this?

Hmm. Not too sure. This kernel fixed my suspend and resume. What kind of machine are you running?

---

### Post by EXCiD3 on 2007-08-15
> **arrrghhh said:**
> this virtualbox is interesting tho, i've seen it mentioned several times.  are there any advantages to it over vmware?

I've heard that it's quite a bit faster than VMWare...

---

### Post by walkerk on 2007-08-15
> **EXCiD3 said:**
> I used the manual instructions of updating my kernel and it worked flawlessly. My only problem is that after booting into the new kernel, my wireless can detect wifi networks, but i can never get past "Configuring the network device". It is an Intel® PRO/Wireless 3945ABG card in my HP dv9000. Is it just that a kernel module is not built into the newest kernel? I really don't understand how those work and I would like to use this newer kernel. When i switch back to the older kernel wireless works fine.

ensure that linux-ubuntu-modules-2.6.22-9-generic and linux-restricted-modules-2.6.22-9-generic are both installed (though I think ubuntu-modules should do.. both should have been installed). you can do this through synaptic or simply through terminal:
```
sudo apt-get install linux-ubuntu-modules-2.6.22-9-generic linux-restricted-modules-2.6.22-9-generic
```

I had the same issue when first doing this (because I missed ubuntu and restricted  modules weren't installed

---

### Post by walkerk on 2007-08-15
> **EXCiD3 said:**
> I've heard that it's quite a bit faster than VMWare...

> **arrrghhh said:**
> yea, i can boot into my old kernel... i have found that new kernel is snappier, so i would like to get it working.  *sigh* i guess i should just wait until gusty is officially released in october!

this virtualbox is interesting tho, i've seen it mentioned several times.  are there any advantages to it over vmware?

I've used both VMWare and VirtualBox (which I prefer). Some people would say VirtualBox is buggy because its younger but I haven't found any faults with it. It's much easier to install OS's using CDs or ISOs imo. Give it a look. :)

---

### Post by EXCiD3 on 2007-08-15
> **walkerk said:**
> ensure that linux-ubuntu-modules-2.6.22-9-generic and linux-restricted-modules-2.6.22-9-generic are both installed (though I think ubuntu-modules should do.. both should have been installed). you can do this through synaptic or simply through terminal:
```
sudo apt-get install linux-ubuntu-modules-2.6.22-9-generic linux-restricted-modules-2.6.22-9-generic
```

I had the same issue when first doing this (because I missed ubuntu and restricted  modules weren't installed

Hey thanks for that, I'll try it tonight, and post my results back for you.

---

### Post by arrrghhh on 2007-08-15
checkin out virtualbox... is there any way to install it from the repo's?

when i do sudo aptitude install virtualbox, i get "No candidate version found for virtualbox"

any help would be greatly appreciated... i'm still kinda retarded when it comes to installing stuff that isn't in the repos...

---

### Post by EXCiD3 on 2007-08-15
I've always install VirtualBox using Automatix... I have heard all this talk about Automatix breaking systems, but until it breaks mine, im gonna keep using it.

You can download a binary for your operating system here: [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

---

### Post by arrrghhh on 2007-08-15
i've heard horror stories from automatix... i tried to use it once to install some drivers for my video card and it just didn't work.  so i'm not sure if i want to use it or not, especially since a lot of people suggest to specifically NOT use it...

oh and thanks for that link to the binaries, although i already tried doin it that way... i followed the instructions in their users manual, but could not get it installed properly.  i haven't even tried installing it on the newer kernel, i'm still running the older feisty kernel because i have to use a virtual machine at work.

update:
ok so i was able to install virtualbox... now i'm wondering, can i use the same virtual machine/drive that i had setup for vmware?  it seems like i should be able to (virtualbox recognizes the files...) but it doesn't work.  something about not having permission?  do i need to setup special permissions for those files/folders?!?

```
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE). 
```is the error i get...

update again:
i'm retarded, if you chmod 666 /dev/vboxdrv it works!

---

### Post by foureight84 on 2007-08-15
> **walkerk said:**
> Hmm. Not too sure. This kernel fixed my suspend and resume. What kind of machine are you running?

i'm running ubuntu on a dell latitude x1. i haven't been able to find a solution.

---

### Post by tll_2k on 2007-08-16
Thanks! The script worked great!!! Except, now I have an entry on the grub menu that is Xen something? What is it? I Wouldn't really care about it, except that it's now my default choice...

Tyler Lane

---

### Post by walkerk on 2007-08-16
> **tll_2k said:**
> Thanks! The script worked great!!! Except, now I have an entry on the grub menu that is Xen something? What is it? I Wouldn't really care about it, except that it's now my default choice...

Tyler Lane

It's your default choice? Thats strange. You can go into your Grub menu.lst ( gksudo gedit /boot/grub/menu.lst ) and change the default number to whatever choice Ubuntu, 2.6.22-9- generic is or you can just swap places (Ubuntu, 2.6.22-9-generic in place of Xen)

Not too sure what Xen is as it didn't install on my machine. I'll run the upgrade again when I get home from work and try to recreate this. I wouldn't worry about it because these are offical Ubuntu upgrades.

---

### Post by muadnu on 2007-08-16
I used the script and it worked perfectly. My only problem is that now I can't access my cdrom drive. I have a new Dell Vostro 1400, and while the cdrom did not work out-of-the box, I could make it work with the old kernel loading the piix driver (I followed the instructions in [http://ubuntuforums.org/showthread.php?t=509408]("http://ubuntuforums.org/showthread.php?t=509408")).
With the updated kernel I can't do this, whenever I try it I get
```

dani@dellinbedo:~$ sudo modprobe piix
FATAL: Module piix not found.

```

I've searched many threads and other forums, but cannot find how to fix it. Just in case, I tried to do it again loading the old kernel and I got a message saying something like "operation not permitted".

Any ideas?

---

### Post by arrrghhh on 2007-08-16
yea i was running virtual box and i noticed the windows vm environment ran well, but linux was too sluggish.  maybe it's the gusty kernel on this machine, it's my work computer and kinda a pos.  i'll just wait for gusty to actually be released.

this is a great thread, i love the script.  it worked like a charm, and i love linux because you can do stuff like this so easily!  but my setup is funky at work, it has to be.  thanks for the work to do this tho, great stuff!

---

### Post by ayu on 2007-08-16
> **muadnu said:**
> I used the script and it worked perfectly. My only problem is that now I can't access my cdrom drive. I have a new Dell Vostro 1400, and while the cdrom did not work out-of-the box, I could make it work with the old kernel loading the piix driver (I followed the instructions in [http://ubuntuforums.org/showthread.php?t=509408]("http://ubuntuforums.org/showthread.php?t=509408")).
With the updated kernel I can't do this, whenever I try it I get
```

dani@dellinbedo:~$ sudo modprobe piix
FATAL: Module piix not found.

```

I've searched many threads and other forums, but cannot find how to fix it. Just in case, I tried to do it again loading the old kernel and I got a message saying something like "operation not permitted".

Any ideas?

Whew... this took me a long time to figure out too.  Seems like piix is no longer used in 2.6.22, and ata_piix is kinda broken.  I think this guy [https://bugs.launchpad.net/redfish/+bug/119905/comments/9](https://bugs.launchpad.net/redfish/+bug/119905/comments/9) has a solution to fixing the ata_piix source, but it is all giberish to me, and I have no clue how to recompile the driver.  In the meantime, you can add ide_generic instead of piix in /etc/modules.  It appears okay to me now.

---

### Post by BadPenny on 2007-08-17
I'm having a problem with the upgrade. I tried to do the full upgrade from feisty to gutsy. However, the kernel upgrade is failing when trying to run depmod. I attempted to apt-get install --reinstall both module-init-tools and initramfs-tools, to no avail. The error I am getting is:

```

Setting up linux-image-2.6.22-9-generic (2.6.22-9.25) ...
Running depmod.
/usr/sbin/mkinitramfs: invalid option -- c
Terminating...
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-9-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.22-9-generic:
---snip---
Errors were encountered while processing:
 linux-image-2.6.22-9-generic
 linux-ubuntu-modules-2.6.22-9-generic
 linux-image-generic
 linux-restricted-modules-2.6.22-9-generic
 linux-restricted-modules-generic
 linux-generic
 linux

```

What am I missing that is causing problems with depmod?

Thanks,
--bp

---

### Post by bmartin on 2007-08-17
walkerk,

Thanks for the HOWTO. I just had one comment.

In your script, you backup sources.list and restore it when you're done. A way to add repositories without modifying the sources.list file is to add a new file of the form **name.list** to the /etc/apt/sources.list.d/ directory. If you don't put .list on the end, I don't think it'll work.

---

### Post by walkerk on 2007-08-17
> **bmartin said:**
> walkerk,

Thanks for the HOWTO. I just had one comment.

In your script, you backup sources.list and restore it when you're done. A way to add repositories without modifying the sources.list file is to add a new file of the form **name.list** to the /etc/apt/sources.list.d/ directory. If you don't put .list on the end, I don't think it'll work.

Thanks. I'm looking at that now.

---

### Post by LordMau on 2007-08-18
If anyone is using Compiz via instructions on this [thread]("http://ubuntuforums.org/showthread.php?t=488385"), were you able to successfully still run compiz after the kernel upgrade?

The acutal upgrade worked well, and I am able to start an X session via ordinary X (specifically XFCE on me) but my Xgl session is unusable. Any tips?

---

### Post by ssmohan on 2007-08-18
Greetings,

  Thank you for the description on upgrading the kernel. Do these scripts work for Dapper (6.06 LTS) as well ?  I am trying to get an inspiron 1420 running on Dapper and the integrated graphics card (965GM intel X3100) and the ethernet card (Broadcom 5906) are not supported in 6.06 LTS.   Hopefully, upgrading to the Gutsy kernel should help.

Thank you!
Mohan

---

### Post by walkerk on 2007-08-18
> **ssmohan said:**
> Greetings,

  Thank you for the description on upgrading the kernel. Do these scripts work for Dapper (6.06 LTS) as well ?  I am trying to get an inspiron 1420 running on Dapper and the integrated graphics card (965GM intel X3100) and the ethernet card (Broadcom 5906) are not supported in 6.06 LTS.   Hopefully, upgrading to the Gutsy kernel should help.

Thank you!
Mohan

I don't see why it wouldn't work. If it doesn't you can follow the instructions at the bottom of the first post to remove 2.6.22-9-generic. 

Let me know :)

---

### Post by muadnu on 2007-08-18
> **ayu said:**
> Whew... this took me a long time to figure out too.  Seems like piix is no longer used in 2.6.22, and ata_piix is kinda broken.  I think this guy [https://bugs.launchpad.net/redfish/+bug/119905/comments/9](https://bugs.launchpad.net/redfish/+bug/119905/comments/9) has a solution to fixing the ata_piix source, but it is all giberish to me, and I have no clue how to recompile the driver.  In the meantime, you can add ide_generic instead of piix in /etc/modules.  It appears okay to me now.

Thanks! It works ok for me to. Do I lose anything by using ide_generic? (I haven't tried burning a CD or DVD).

---

### Post by por100pre1 on 2007-08-18
Works fine here, at this moment at least. Thanks. :)

---

### Post by walkerk on 2007-08-18
> **por100pre1 said:**
> Works fine here, at this moment at least. Thanks. :)

Glad to hear :)

---

### Post by LordMau on 2007-08-18
Well I waded thru my install, and took the jump with Envy following jamieplucinski's instructions. I was hesitant at first as Envy did hose another PC using nvidia driver, but here in an ATI RS458 xpress 200 system all seems well.

I ha hoped that XGL would not be needed in the latest fglrx version but it seems not. Could'nt make compiz work without Xgl. Or is there a way?

Anyway, with the new kernel is an unexpected bonus: my a4tech pk-635m webcam now is properly detected by the various cam applications and skype under vmware/ winxp so yes!

But a minus: the system never finishes a reboot! I need to cycle the power to do now. Any suggestions to solve this?

---

### Post by walkerk on 2007-08-18
> **LordMau said:**
> Well I waded thru my install, and took the jump with Envy following jamieplucinski's instructions. I was hesitant at first as Envy did hose another PC using nvidia driver, but here in an ATI RS458 xpress 200 system all seems well.

I ha hoped that XGL would not be needed in the latest fglrx version but it seems not. Could'nt make compiz work without Xgl. Or is there a way?

Anyway, with the new kernel is an unexpected bonus: my a4tech pk-635m webcam now is properly detected by the various cam applications and skype under vmware/ winxp so yes!

But a minus: the system never finishes a reboot! I need to cycle the power to do now. Any suggestions to solve this?

Hopefully another user can help you with XGL.. I have Intel video some I'm not much use with ATI.. never messed around with it.

As for reboot not finishing.. Where does it hang? Also how are you rebooting?

If your using 
```
sudo reboot
```

you can give the shutdown command with the reboot option
```
sudo shutdown -r 0
```

Let me know.

---

### Post by LordMau on 2007-08-18
walkerk:

I use the X shell log-off screen (xfce/xubuntu) not via the terminal. When I notice there is no hd activity, I switch to tty1 (or some other) and see the terminal notice that the system is going for reboot which I think is the last message issued before the acutal reboot. It stays there forever until the power cycle.

---

### Post by walkerk on 2007-08-18
> **LordMau said:**
> walkerk:

I use the X shell log-off screen (xfce/xubuntu) not via the terminal. When I notice there is no hd activity, I switch to tty1 (or some other) and see the terminal notice that the system is going for reboot which I think is the last message issued before the acutal reboot. It stays there forever until the power cycle.

Right, but can you test these through the terminal to see if they work. Troubleshoot :)

---

### Post by por100pre1 on 2007-08-18
Everything working fine so far. I even tried some tasks like CD burning, no problems.  But when I check the Restricted drivers Manager, a warning about an unsupported driver appears. The driver is lirc_gpio and it is not in use.

[[IMG]http://img154.imageshack.us/img154/411/lircgpiowq1.th.png[/IMG]](http://img154.imageshack.us/my.php?image=lircgpiowq1.png)

Some info and suggestions would be appreciated. Thanks. :)

---

### Post by mpgarate on 2007-08-18
worked well :)

---

### Post by bimmerd00d on 2007-08-18
Made my intel DG33BU work better!  The onboard NIC works!!!

---

### Post by walkerk on 2007-08-18
> **mpgarate said:**
> worked well :)

> **bimmerd00d said:**
> Made my intel DG33BU work better!  The onboard NIC works!!!

Glad to hear it :)

---

### Post by walkerk on 2007-08-18
> **por100pre1 said:**
> Everything working fine so far. I even tried some tasks like CD burning, no problems.  But when I check the Restricted drivers Manager, a warning about an unsupported driver appears. The driver is lirc_gpio and it is not in use.

[[IMG]http://img154.imageshack.us/img154/411/lircgpiowq1.th.png[/IMG]](http://img154.imageshack.us/my.php?image=lircgpiowq1.png)

Some info and suggestions would be appreciated. Thanks. :)

I have the same thing. You can just uncheck the enabled checkbox. :) Or leave it be..

---

### Post by el mariachi on 2007-08-18
> **walkerk said:**
> I have the same thing. You can just uncheck the enabled checkbox. :) Or leave it be..
i also have that
what is it supposed to be?

---

### Post by walkerk on 2007-08-18
> **el mariachi said:**
> i also have that
what is it supposed to be?

Ok. It seems this is a driver for IR devices: [http://ubuntuforums.org/showthread.php?t=524916](http://ubuntuforums.org/showthread.php?t=524916)

If you don't need it you can disable it. I did :)

---

### Post by por100pre1 on 2007-08-18
> **walkerk said:**
> Ok. It seems this is a driver for IR devices: [http://ubuntuforums.org/showthread.php?t=524916](http://ubuntuforums.org/showthread.php?t=524916)

If you don't need it you can disable it. I did :)

Thanks for the info.
:popcorn:

---

### Post by fbusy on 2007-08-18
LOVE IT... working fantastic on my p4 2.66ghz 512ram, everything seems faster.
thanks thanks thanks

---

### Post by walkerk on 2007-08-19
> **fbusy said:**
> LOVE IT... working fantastic on my p4 2.66ghz 512ram, everything seems faster.
thanks thanks thanks

Sure thing. Glad its working well.

---

### Post by isaacj87 on 2007-08-19
AHHH...So close!

I tried out the new kernel...works great, except it breaks my suspend...
My comp doesn't wake up anymore...I was really starting to like the new kernel too :(

---

### Post by tact on 2007-08-19
> **isaacj87 said:**
> AHHH...So close!

I tried out the new kernel...works great, except it breaks my suspend...
My comp doesn't wake up anymore...I was really starting to like the new kernel too :(

Mine went the other way - suspend never worked but now it is such a delicious luxury!  Love it.

---

### Post by LordMau on 2007-08-19
> **walkerk said:**
> Right, but can you test these through the terminal to see if they work. Troubleshoot :)

Both commands is the same as in X; the system appears to go thru the motions of shutting down then stalls at the very last notice ("* Will now restart"). See attached screenshot.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=41082&stc=1&d=1187531314[/IMG]

That's in tty7. X was in tty8 and all I get there is a cursor lol. I'm still stumped ^^

---

### Post by walkerk on 2007-08-19
> **LordMau said:**
> Both commands is the same as in X; the system appears to go thru the motions of shutting down then stalls at the very last notice ("* Will now restart"). See attached screenshot.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=41082&stc=1&d=1187531314[/IMG]

That's in tty7. X was in tty8 and all I get there is a cursor lol. I'm still stumped ^^

Hmm.. not too sure. let me google around and see if this is a known bug for some systems..

---

### Post by r_l on 2007-08-19
Hi,
I just upgraded the kernel with my Dell Inspiron 6000 here.  Below are my observations.

(1) The upgrade fixed the shutdown spinning noise problem - which was the reason for my upgrading the kernel.  Now the clicking and spinning sound upon shutdown does not occur anymore.  

(2) however, suspend does not resume anymore

(3) USB external drive fails to mount.  When the drive pluged in, the icon of the drive shows in the "Computer" folder.  However,  when I try to open the drive, it shows a message saying that I am not "privileged" to mount the drive.  Looking at the property of the icon in the permission tab, it states that the owner is "unknown".  This occurs with both NTFS external drive and also with FAT flash drive.  

_Update: _ I went into the fstab and remove some old entries  pointing to the external drive and now it works.  However, now the machine make a disk spinning sound right after removing the drive that was supposed to be properly unmounted.  A louder sound for the big external harddisk, a smaller sound for the flash drive.

(4) SD card drive mounted OK

(5) CD/DVD drive read OK (have not tried burning yet)

---

### Post by olmari on 2007-08-19
Running 2.6.22-9 with my AMD 4200+ 64-bit and dual Pentium 3 server, both seems to run fine at first glance and lets hope it stays that way :)

---

### Post by isaacj87 on 2007-08-19
Question for all:

When updating, did anyone else notice that libc6, libc6-dev and libc6-686 were also going to updated as well??

I just want to leave fair warning that libc6 is a *very* important package as well as libc6-dev. After removing 2.6.22 and reverting back to 2.6.20-16, I noticed that certain programs were behaving oddly...like Firefox, which doesn't really work anymore. Literally all of my programs are dependent on libc6, but the Fiesty version...not Gutsy, which poses a problem because whenever I try to downgrade, Synaptic tells me all of my programs are going to be removed...So basically I'm stuck...if anyone can help me, I'd really appreciate it.

---

### Post by walkerk on 2007-08-19
> **isaacj87 said:**
> Question for all:

When updating, did anyone else notice that libc6, libc6-dev and libc6-686 were also going to updated as well??

I just want to leave fair warning that libc6 is a *very* important package as well as libc6-dev. After removing 2.6.22 and reverting back to 2.6.20-16, I noticed that certain programs were behaving oddly...like Firefox, which doesn't really work anymore. Literally all of my programs are dependent on libc6, but the Fiesty version...not Gutsy, which poses a problem because whenever I try to downgrade, Synaptic tells me all of my programs are going to be removed...So basically I'm stuck...if anyone can help me, I'd really appreciate it.

Im not a dev but from what I read online libc6 is Linux C Library version 6. I can't imagine what programs would act differently between minor releases within version 6 (feisty uses 2.5 and gutsy uses 2.6). I can say that with 2.6.20-16 (which I just booted into) my programs work ok.

**Do not remove the programs.** One user has tried this and it went bad.

Can I ask what is wrong with 2.6.22-9?

---

### Post by SeanBlader on 2007-08-20
Neat upgrade, I needed to run through the settings file for Compiz but without too many problems I got everything else running just like it was before... except.

With the Fiesty kernel on my inspiron 8500 I was able to suspend, but never wake up. Now I can't even suspend at all. I'm sure my acpi-support file needs some work. I've read about every google page looking for a solution to no avail, but that's probably not for this thread.

Solid upgrade using the manual install method, even upgraded to the gutsy versions of the ACPI packages afterwards hoping it'd fix my suspend, no luck there either. Thanks for the how-to Walkerk.

---

### Post by bmartin on 2007-08-20
How can I attempt to fix my ACPI support in my Acer Aspire 5050 (i.e. what packages or files)? I modified my dsdt.dsl file, recompiled, and so forth, but that had no effect. My ACPI is completely screwed up: the battery's not detected, the laptop overheats, etc.

---

### Post by nowshining on 2007-08-20
hmmm [fbusy]("http://ubuntuforums.org/member.php?u=339804") i also have a P4 2.66ghz 512mb ram computer so I am sorta guessing you have a Dell 4600i like me. :) well if so your post comforts me. :P

anyway it would be nice to know what SIZE everything totals up to when downloades as i couldn't start up the script thru the terminal, so I had to double click on it, well um, right now I am on dialup and its secretly downloading in the background.. :D lolz anyway sine I have only a 3hr session, I do hope like it did last time when I had to disconnect off the net, it re-started after a minute or two.. ;) which is good and I do hope it doesn't re-download the parts it already did... I'll post my successful or unsuccessful  experience after maybe a week or two to give time to test it out..

---

### Post by nowshining on 2007-08-21
Well seems a bit  faster, the script said it downloaded all, BUT it actually didn't when it asked to reboot, I clicked some button, I do not remember and when nothing happened i went thru the start menu, well and then saw an error dialog don't know what it said, but then rebooted, same kernel, then i tried the manual method worked well and was actually easier, it got some because the size is about 53mb or so and it said I needed to download about 20 or so Megs so let it, and then was wondering why in about a minute on the generic kernel it was almost half way done, lolz :P anyway it downloaded to 98 percent and then quit on me, hopefully when I re-issued the command it finished it up from that point but again earlier i did get an dependency or whatever error, ignored and all installed well. ;) so far again it's a bit faster to startup program, BUT again it is a BIT slower to show the desktop, maybe next reboot will faster.. All that ends well.. oh and the generic kernel is about if I didn't say above about 16 megs.

I highly suggest  the MANUAL method more than anything as it's not only quicker but you see what's going on and how much had been downloaded.

So far YES AGAIN 

Dell 4600i
Ubuntu Feisty with nowshining@BOT1NET1GOD1:~$ uname -r
2.6.22-9-generic
Pentium 4 no HyperThreading
512mb RAM with Internal Video which this gutsy upgrade fixed up and also the sound.
This Model came out in about 2003 probably middle of.

:thumbs up:

---

### Post by el mariachi on 2007-08-21
Weird... I just felt like formatting my HD and resintalled Ubuntu and OpenBox (pure).
Now that I upgraded the kernel (last time it worked) I can't get the openbox menu to open (right click on the desktop). the only thing I can open is the browser through a keyboard shortcut... Any ideas? It worked last time I upgraded... Razer Diamondback Plasma
switching between desktops with the scroll-weel doesn't work as well.

---

### Post by walkerk on 2007-08-21
> **el mariachi said:**
> Weird... I just felt like formatting my HD and resintalled Ubuntu and OpenBox (pure).
Now that I upgraded the kernel (last time it worked) I can't get the openbox menu to open (right click on the desktop). the only thing I can open is the browser through a keyboard shortcut... Any ideas? It worked last time I upgraded... Razer Diamondback Plasma
switching between desktops with the scroll-weel doesn't work as well.

Hmm. Not to sure as I have Openbox as well and I run it by itself (w/out Gnome) without problems.. :/

---

### Post by st33med on 2007-08-21
I can't upgrade from 2.6.22-9 to the new *-10 kernel. I always get this error message, even if I use kernel_cli.sh:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-headers-generic: Depends: linux-headers-2.6.22-10-generic but it is not installable
  linux-image-generic: Depends: linux-image-2.6.22-10-generic but it is not installable
                       Depends: linux-ubuntu-modules-2.6.22-10-generic but it is not installable
  linux-restricted-modules-generic: Depends: linux-restricted-modules-2.6.22-10-generic but it is not installable
E: Broken packages

```

Which is broken? Me, or the script?

Also, the current kernel (2.6.22-9) has a bug in it that affects users with dual core processors. The second processor will not wake up after waking up from suspend or hibernation. So, that is why I really want this kernel.

---

### Post by kcleong on 2007-08-21
Got the same warning. I'm running a few days on gutsy. Probably the brand new 2.6.22-10 kernel header and image aren't in the repositories yet.

If the second cpu won't show try running `uname -a` and look if you see 386 or generic after the kernel version. If you see 386 install `linux-generic` and uninstall `linux-386`, this would make your dual core work.

---

### Post by marc28 on 2007-08-21
> **holdennutta said:**
> Thank you very much for this guide. 

I used the manual way of doing it and it worked great. Fixed some issues I was having with laptop not noticing it had a battery et al.

Cheers!
Hi Holdennutta,
Could you tell me how you solved the issue of the laptop not noticing it was on battery?
I'm having exactly the same issue, but no idea how to solve it (i'm very new to ubuntu and linux).
Thanks!

---

### Post by isaacj87 on 2007-08-21
> **walkerk said:**
> Im not a dev but from what I read online libc6 is Linux C Library version 6. I can't imagine what programs would act differently between minor releases within version 6 (feisty uses 2.5 and gutsy uses 2.6). I can say that with 2.6.20-16 (which I just booted into) my programs work ok.

**Do not remove the programs.** One user has tried this and it went bad.

Can I ask what is wrong with 2.6.22-9?

Sorry it took so long to get back to you. I had to revert back to 2.6.20-16 because the suspend was broken in 2.6.22. Other than that it worked great! About my problem, I just went ahead and did a reformat and I currently getting everything back up to speed. Not a big deal really, I didn't have choice, plus I did waaaay too much testing on my everyday use laptop...lol. So it was nice to start fresh.

---

### Post by nowshining on 2007-08-21
hi [st33med]("http://ubuntuforums.org/member.php?u=230176") I believe I got those same errors, I just went ahead and continued the install and all works fine. :)


edit : n/m i noticed it was the new 2.6.22-10

---

### Post by el mariachi on 2007-08-21
I tried to use this script in a server install but apparently it hasn't done anything. How can I upgrade the kernel in this situation?

---

### Post by JeffD on 2007-08-22
> **st33med said:**
> I can't upgrade from 2.6.22-9 to the new *-10 kernel. I always get this error message, even if I use kernel_cli.sh:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-headers-generic: Depends: linux-headers-2.6.22-10-generic but it is not installable
  linux-image-generic: Depends: linux-image-2.6.22-10-generic but it is not installable
                       Depends: linux-ubuntu-modules-2.6.22-10-generic but it is not installable
  linux-restricted-modules-generic: Depends: linux-restricted-modules-2.6.22-10-generic but it is not installable
E: Broken packages

```

Which is broken? Me, or the script?

Also, the current kernel (2.6.22-9) has a bug in it that affects users with dual core processors. The second processor will not wake up after waking up from suspend or hibernation. So, that is why I really want this kernel.


It's not you.  Kind of frustrating.  Looks like it needs to download some headers but is unable to.  Since dependencies are not being met, the new kernel never shows up in my /boot directory, and grub's menu.lst isn't updated (which, since there is no new kernel, is probably a good thing!)

I don't know how the user who said he got these errors, and it worked anyway was able to do so!  :lolflag:


comments or suggestions?

---

### Post by nowshining on 2007-08-22
huh!? where's the 2.6.22-10 version, I can't find it on google as of this post...and i'd wait a day or two before updating anyway to let things fall into place..


edit : n/m but i'd still wait a few days until everything gets undercontrol..

---

### Post by James Little on 2007-08-22
I've upgraded to kernel 2.6.22-10-generic via Update Manager (in Gutsy), but my wireless stopped working; seems like the iwlwifi (intel wireless) modules are missing from 2.6.22-10-generic.

---

### Post by lemurian on 2007-08-22
The iwlwifi drivers are in this package:

linux-ubuntu-modules-2.6.22-10-generic

Did you install it?  It won't get installed unless you specifically ask for it.

---

### Post by el mariachi on 2007-08-22
if I change the -generic part to -server will it work?

---

### Post by James Little on 2007-08-22
> **lemurian said:**
> The iwlwifi drivers are in this package:

linux-ubuntu-modules-2.6.22-10-generic

Did you install it?  It won't get installed unless you specifically ask for it.
That package doesn't seem to be available to me...do I need to add a new repository?

---

### Post by LordMau on 2007-08-22
Posting to say that, without doing anything after my 2.6.22-9 update, that shuwdown/ restart works may 6 out of 10 times. Mind boggling!

Afterwards I tried the suggestion to add > acpi=force at the boot options. This doen't seem to help as the success rate of a shutdown/ restart did not improve.

If someone notices or had the same issue with 2.6.22-9, did 2.6.22-10 help in this aspect?

---

### Post by lemurian on 2007-08-22
> **James Little said:**
> That package doesn't seem to be available to me...do I need to add a new repository?
Probably the repositories need to be refreshed before the package will show up.  If I checked on launchpad, I see that everything needed is built but if I check in the repository, I don't see the package.

I bypassed the whole thing by grabbing the sources packages directly from launchpad and compiling my own because I wanted to test things early.

---

### Post by lemurian on 2007-08-22
> **LordMau said:**
> Posting to say that, without doing anything after my 2.6.22-9 update, that shuwdown/ restart works may 6 out of 10 times. Mind boggling!

Afterwards I tried the suggestion to add  at the boot options. This doen't seem to help as the success rate of a shutdown/ restart did not improve.

If someone notices or had the same issue with 2.6.22-9, did 2.6.22-10 help in this aspect?
I had a problem with suspend and hibernate in 2.6.22-9 but that was due to the closed-source nVidia drivers.  I have not tried with 2.6.22-10.

---

### Post by phocis850 on 2007-08-22
The script worked great, no problems here.

I only upgraded because of my laptops hard drive click problem.
This kernel fixed that issue.

---

### Post by walkerk on 2007-08-22
> **phocis850 said:**
> The script worked great, no problems here.

I only upgraded because of my laptops hard drive click problem.
This kernel fixed that issue.

Yep.. I just worked the script myself to upgrade to -10

---

### Post by walkerk on 2007-08-22
> **James Little said:**
> That package doesn't seem to be available to me...do I need to add a new repository?

you'll need to manually add the gutsy repo and download the needed package through Synaptic, **and then immediately remove the gutsy repo**...

Add the repo:
```
echo 'deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted' | sudo tee -a /etc/apt/sources.list
```

Update
```
sudo apt-get update
```

Search Synaptic for "2.6.22-10" assuming that you've upgraded to 2.6.22-10
```
gksudo synaptic
```

Now that you've installed it remove the repo from /etc/apt/sources.list [ it will be the last line: deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted ]
```
gksudo gedit /etc/apt/sources.list
```

Now update again
```
sudo apt-get update
```

---

### Post by lemurian on 2007-08-22
Hmm... ok linux-ubuntu-modules is present now.  I guess the search interface I was using is not quite up-to-date with what the repositories contain. :-/

---

### Post by walkerk on 2007-08-22
> **lemurian said:**
> Hmm... ok linux-ubuntu-modules is present now.  I guess the search interface I was using is not quite up-to-date with what the repositories contain. :-/

linux-ubuntu-modules is installed via the linux-generic meta package :) doing it in this manner will ensure taht with each new release it will be upgraded as well..

---

### Post by edmondt on 2007-08-22
Script works great :) good job!! :KS

---

### Post by walkerk on 2007-08-23
> **edmondt said:**
> Script works great :) good job!! :KS

Good to hear my friend :)

---

### Post by el mariachi on 2007-08-23
I'm sorry but can't you give me a hint on how to do this upgrade on Ubuntu server?

---

### Post by walkerk on 2007-08-23
> **el mariachi said:**
> I'm sorry but can't you give me a hint on how to do this upgrade on Ubuntu server?

I'm at work so I can't list the necessary packages but you'll need the 2-6.22-10-server related packages.. just as with generic. Here's an idea...

1. Add the Gutsy repo manually.
```
echo 'deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted' | sudo tee -a /etc/apt/sources.list
```

2. Update
```
sudo apt-get update
```

3. Open Synaptic and search for 2.6.22-10-server (or 2.6.22-10 to see all the variations).
```
gksu synaptic
```

4. Mark the necessary packages for installation and click Apply. (Dont reboot!)

5. Remove the Gutsy repo (last line of /etc/apt/sources.list)
```
gksu gedit /etc/apt/sources.list
```

6. Update
```
sudo apt-get update
```

7. Reboot
```
sudo reboot
```

---

### Post by el mariachi on 2007-08-23
one small thing.. in your guide you clearly state that NO PACKAGES SHOULD BE UPGRADED WHILE THE GUTSY REPOS ARE OPEN
I need to upgrade libc6 in order to upgrade linux-headers, should I?

---

### Post by walkerk on 2007-08-23
> **el mariachi said:**
> one small thing.. in your guide you clearly state that NO PACKAGES SHOULD BE UPGRADED WHILE THE GUTSY REPOS ARE OPEN
I need to upgrade libc6 in order to upgrade linux-headers, should I?

yes.. libc6 will automatically update with the script (and meta-packages) so you should be ok.. :)

you've already done it with your other machine.. (when you install -generic)

---

### Post by el mariachi on 2007-08-23
yeah, everything is running just fine.

---

### Post by James Little on 2007-08-23
> **lemurian said:**
> Hmm... ok linux-ubuntu-modules is present now.  I guess the search interface I was using is not quite up-to-date with what the repositories contain. :-/
Yeah they appeared for me too; Update Manager alerted me and the ubuntu generic modules were installed, so wireless is working now :) Thanks for your help guys!

I'm on a laptop too (Santa Rosa platform), and suspend/hibernate seem to work ok in 2.6.22-10.

---

### Post by Xan63 on 2007-08-23
Hi !

I'm trying to upgrade my kernel to Gutsy, but i've a little problem...
It seems the link to download the kernel.sh is dead.

Could somebody help me?

thx!
:D

=> Solved, I've got a great idea and checked the end of the post... stupid!

---

### Post by hippomofatumas on 2007-08-23
ive got a new inspiron 1420 (windows version, dual booting), but cant get wirted or wireless to work. i was pointed to this thread to get my wired working at least and i successfully did the update/upgrade but still no internet.

in network tools i have an eth0 with no info on it and no ability to configure and an eth0:avahi, which displays some info but when i press configure it says the interface does not exist.

please help me get ubuntu working

thanks

---

### Post by walkerk on 2007-08-24
> **Xan63 said:**
> Hi !

I'm trying to upgrade my kernel to Gutsy, but i've a little problem...
It seems the link to download the kernel.sh is dead.

Could somebody help me?

thx!
:D

=> Solved, I've got a great idea and checked the end of the post... stupid!


:)

---

### Post by walkerk on 2007-08-24
> **hippomofatumas said:**
> ive got a new inspiron 1420 (windows version, dual booting), but cant get wirted or wireless to work. i was pointed to this thread to get my wired working at least and i successfully did the update/upgrade but still no internet.

in network tools i have an eth0 with no info on it and no ability to configure and an eth0:avahi, which displays some info but when i press configure it says the interface does not exist.

please help me get ubuntu working

thanks

I'm at work right now but I'll try to give you a hand this evening...

---

### Post by Xan63 on 2007-08-24
Hi,

I'm trying to install envy in my brand new gutsy kernel, but i'm screwed with some dependancies problem... 
When I do
sudo apt-get install linux-headers-`uname -r` build-essential

It tell me that's the newer version, and that build-essential depend of libc6-dev, but it can't being installed.

Same message for g++...

Do you have some idea?

PS: sorry to note post this exact result of terminal, but if I'd do it, it would be in french... i'm not sure this is forumer-friendly :p

---

### Post by lemurian on 2007-08-24
Xan63, I know nothing about forum rules regarding languages other than English but error messages are standardized enough and French is close enough to English that it is possible to infer what an error message says.  Especially if you explain what the message says.

Besides, some of us speak French.

---

### Post by Xan63 on 2007-08-24
Allright then!,

Enclosed the log I obtained, with the translation.

> sudo apt-get install linux-headers-`uname -r` build-essential
linux-headers-2.6.22-10-generic est déjà la plus récente version disponible.
*linux-headers-2.6.22-10-generic  is the most recent version available.*
Certains paquets ne peuvent être installés. 
*Some package can't being installed*


L'information suivante devrait vous aider à résoudre la situation : 
*The following information could help you to solve the problem*

Les paquets suivants contiennent des dépendances non satisfaites :
The following packages contains non-satisfied dependancies: 
build-essential: Depend: libc6-dev but won't be installed
libc-dev

Dépend: g++ (>= 4:4.1.1) but won't be installed 

I hope it will be ok. 

Thanks by advance :)

---

### Post by lemurian on 2007-08-24
Xan63, you already have the latest linux-headers.  The thing you need is libc6-dev.  Can you execute the following 2 commands:

dpkg -l libc6
dpkg -l libc6-dev

And show the output.  (You don't need to translate anything.)  I'm guessing right now that you upgraded to Gutsy's libc6.  The problem now is that if you want to install libc6-dev, the dependency system requires Gutsy's libc6-dev but because the Gutsy repositories are no longer in your /etc/apt/source.list file, apt cannot install it.

---

### Post by Xan63 on 2007-08-24
The outputs:

> xan@vitty:~$ dpkg -l libc6
Souhait=inconnU/Installé/suppRimé/Purgé/H=à garder
| État=Non/Installé/fichier-Config/dépaqUeté/échec-conFig/H=semi-installé
|/ Err?=(aucune)/H=à garder/besoin Réinstallation/X=les deux (État,Err: majuscule=mauvais)
||/ Nom            Version        Description
+++-==============-==============-============================================
ii  libc6          2.6.1-0ubuntu1 GNU C Library: Shared libraries


> Souhait=inconnU/Installé/suppRimé/Purgé/H=à garder
| État=Non/Installé/fichier-Config/dépaqUeté/échec-conFig/H=semi-installé
|/ Err?=(aucune)/H=à garder/besoin Réinstallation/X=les deux (État,Err: majuscule=mauvais)
||/ Nom            Version        Description
+++-==============-==============-============================================
un  libc6-dev      <néant>       (aucune description n'est disponible)


If I put the gutsy repos in /etc/apt/source.list file, could I be able to install libc6-dev?
Or should I try to delete gutsy libc6?

---

### Post by lemurian on 2007-08-24
Yikes!  DO NOT REMOVE libc6!  That will leave you with an unusable system.  Judging by the fact that you are posting in this thread, I'm guessing that you *want* to use Gutsy's kernel.  If that's the case, here's the solution...

You will need to install libc6-dev by yourself.   I would suggest that you follow walkerk's instructions in this post:

[http://ubuntuforums.org/showpost.php?p=3238270&postcount=325](http://ubuntuforums.org/showpost.php?p=3238270&postcount=325)

EXCEPT THAT you need to replace steps 3 and 4 with the following:

3-4. Execute:

```

sudo apt-get install libc6-dev

```

Make sure you do NOT reboot BEFORE performing the steps 5 and 6.  As usual, make sure you do NOT perform any OTHER upgrade during this process.  If anything is unclear, please ask.

---

### Post by walkerk on 2007-08-24
> **lemurian said:**
> Yikes!  DO NOT REMOVE libc6!  That will leave you with an unusable system.  Judging by the fact that you are posting in this thread, I'm guessing that you *want* to use Gutsy's kernel.  If that's the case, here's the solution...

You will need to install libc6-dev by yourself.   I would suggest that you follow walkerk's instructions in this post:

[http://ubuntuforums.org/showpost.php?p=3238270&postcount=325](http://ubuntuforums.org/showpost.php?p=3238270&postcount=325)

EXCEPT THAT you need to replace steps 3 and 4 with the following:

3-4. Execute:

```

sudo apt-get install libc6-dev

```

Make sure you do NOT reboot BEFORE performing the steps 5 and 6.  As usual, make sure you do NOT perform any OTHER upgrade during this process.  If anything is unclear, please ask.

Thanks for helping out lemurian :)

---

### Post by sparckis on 2007-08-24
Hi,
    I updated the kernel above but instead it went to the 2.6.22-10 generic which I assume is fine.  When I rebooted, I lost X windows and said that X could not start successfully.  I made it here by hitting escape and restarting 2.6.20

Any idea what I should do to make this work?  I am new, and I looked at xorg.conf but couldn't find anything kernel dependant.

I am using an nvidia card on a dell e1705....Long long road, trying to fix the 'whiz pop' on the hard drive on shutdown.  Some say kernel fixes issue.

Thanks

---

### Post by walkerk on 2007-08-24
> **sparckis said:**
> Hi,
    I updated the kernel above but instead it went to the 2.6.22-10 generic which I assume is fine.  When I rebooted, I lost X windows and said that X could not start successfully.  I made it here by hitting escape and restarting 2.6.20

Any idea what I should do to make this work?  I am new, and I looked at xorg.conf but couldn't find anything kernel dependant.

I am using an nvidia card on a dell e1705....Long long road, trying to fix the 'whiz pop' on the hard drive on shutdown.  Some say kernel fixes issue.

Thanks

ok.. you probably need the nvidia-glx-new or legacy.. add the gutsy repo again** and do the following:
```
sudo apt-get install nvidia-glx-new
```

i doubt you have a legacy card but if the above doesn't work try:
```
sudo apt-get install nvidia-glx-legacy
```

**now be sure to remove the gutsy repo** and run update..**

** - Refer to the original post for instructions.

---

### Post by Xan63 on 2007-08-24
Yay, thanks for the process!
I will check that right now ^^

---

### Post by sparckis on 2007-08-24
K, so I re-add the repo like the first post says, then get the new nvidia program, then remove the repo like the first post, correct?  Quick question, will this mess up the 2.6.20 nvidia stuff?  I want to make sure I'll still have a functional 2.6.20 system.  

Also, without getting too technical, what is fiesty and all of these other names of Ubuntu referring to?  If you have a link that would be cool.  Is any one better than the others?  Also, why does the repo need to be removed?  Why can't it just stay there?  Or why does fiesty not have a 2.6.22 kernel?

So many Qs

---

### Post by walkerk on 2007-08-24
> **sparckis said:**
> K, so I re-add the repo like the first post says, then get the new nvidia program, then remove the repo like the first post, correct?  Quick question, will this mess up the 2.6.20 nvidia stuff?  I want to make sure I'll still have a functional 2.6.20 system.  

Also, without getting too technical, what is fiesty and all of these other names of Ubuntu referring to?  If you have a link that would be cool.  Is any one better than the others?  Also, why does the repo need to be removed?  Why can't it just stay there?  Or why does fiesty not have a 2.6.22 kernel?

So many Qs

Ok.. perhaps this isn't for you. No need to break your working system for a minor kernel upgrade. Feisty refers to Ubuntu 7.04 and Gutsy refers to Ubuntu 7.10 (still in development)..

This method is a simple way to get a new kernel without compiling it youself. 

The repo would need to be removed because if not you would slowly upgrade from the Stable Ubuntu 7.04 to the developing 7.10..

With the questions you are asking I would suggest you stay with 2.6.20-16... you can remove 2.6.22-10 through synaptic. 
```
gksu synaptic
```

search for 2.6.22-10 and remove all of the installed packages. this will update your grub menu.lst so the next time you reboot 2.6.20-* will come up..

---

### Post by Xan63 on 2007-08-24
> **lemurian said:**
> Yikes!  DO NOT REMOVE libc6!  That will leave you with an unusable system.  Judging by the fact that you are posting in this thread, I'm guessing that you *want* to use Gutsy's kernel.  If that's the case, here's the solution...

You will need to install libc6-dev by yourself.   I would suggest that you follow walkerk's instructions in this post:

[http://ubuntuforums.org/showpost.php?p=3238270&postcount=325](http://ubuntuforums.org/showpost.php?p=3238270&postcount=325)

EXCEPT THAT you need to replace steps 3 and 4 with the following:

3-4. Execute:

```

sudo apt-get install libc6-dev

```

Make sure you do NOT reboot BEFORE performing the steps 5 and 6.  As usual, make sure you do NOT perform any OTHER upgrade during this process.  If anything is unclear, please ask.

So, I performed this, make step 5 and 6.
But I don't see gutsy kernel in the grub, in spite of having the following output > linux-image-2.6.22-10-generic linux-headers-2.6.22-10-generic linux-headers-2.6.22-10 linux-restricted-modules-2.6.22-10-generic linux-ubuntu-modules-2.6.22-10-generic

Just a grub problem?

> oem@vitty:/boot$ ls
abi-2.6.20-15-generic         initrd.img-2.6.20-16-generic
abi-2.6.20-16-generic         memtest86+.bin
config-2.6.20-15-generic      System.map-2.6.20-15-generic
config-2.6.20-16-generic      System.map-2.6.20-16-generic
grub                          vmlinuz-2.6.20-15-generic
initrd.img-2.6.20-15-generic  vmlinuz-2.6.20-16-generic


---

### Post by sparckis on 2007-08-25
Hey,
    installing that nvidia piece did work and it solved the "whiz pop" on shutdown of my laptop, hopefully saving the life of the hard drive.

There is an issue with the upgrade however.  My laptop can not tell when I have headphones plugged into the jack so the speakers are always on, but the headphones are also working when plugged in.  Is there any way to get the onboard speakers to mute when headphones are plugged in?  trying different options under preferences doesn't seem to help.

Thanks

---

### Post by walkerk on 2007-08-25
> **Xan63 said:**
> So, I performed this, make step 5 and 6.
But I don't see gutsy kernel in the grub, in spite of having the following output 

Just a grub problem?

so you've installed all of the kernel packages.. correct? when you do the should automatically change grub/menu.lst. remove the gutsy repository, update, and reboot... what happens?

Also, lets see /boot/grub/menu.lst...

---

### Post by Xan63 on 2007-08-25
yop,



After checking in synaptic, it seemed that > linux-image-2.6.22-10-generic linux-headers-2.6.22-10-generic linux-headers-2.6.22-10 linux-restricted-modules-2.6.22-10-generic linux-ubuntu-modules-2.6.22-10-generic were lacking, so I have installed them, reboot and now it's allright!

I can select gutsy kernel in grub :)

thanks a lot for your help! :D

Now I'm trying to install nvidia driver with envy, because native gutsy support of nvidia made X11 completely hose :(

=> Yay, that's it!! It worked like a charm, thanks Mr Milone for this great script!

---

### Post by nowshining on 2007-08-25
sound working fine for me just upgraded to the latest tonight -just rebooted a bit ago started up rythmbox and all works again like I said fine for now..

Dell 4600i
Internal Video Card used - 82865G Intel Corporation
Stock Sound Card - internal - Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller


altho it just might be me but the music sounds a bit quicker :P I stayed up all night 4am in the morning PST time as of this post also much quicker than the last kernel


now that I think about it editing in this box seems a bit off on the spaces somewhat at times. :P

nowshining@BOT1NET1GOD1:~$ uname -r
2.6.22-10-generic
nowshining@BOT1NET1GOD1:~$


okay had to recompile setup for virtualbox or whatever in root terminal by doing this command

/etc/init.d/vboxdrv setup

anyway have had so far FEW other problems besides auto fix removed the last kernel I believe...anyway..

---

### Post by walkerk on 2007-08-25
> **sparckis said:**
> Hey,
    installing that nvidia piece did work and it solved the "whiz pop" on shutdown of my laptop, hopefully saving the life of the hard drive.

There is an issue with the upgrade however.  My laptop can not tell when I have headphones plugged into the jack so the speakers are always on, but the headphones are also working when plugged in.  Is there any way to get the onboard speakers to mute when headphones are plugged in?  trying different options under preferences doesn't seem to help.

Thanks

> **Xan63 said:**
> yop,



After checking in synaptic, it seemed that  were lacking, so I have installed them, reboot and now it's allright!

I can select gutsy kernel in grub :)

thanks a lot for your help! :D

Now I'm trying to install nvidia driver with envy, because native gutsy support of nvidia made X11 completely hose :(

=> Yay, that's it!! It worked like a charm, thanks Mr Milone for this great script!

> **nowshining said:**
> sound working fine for me just upgraded to the latest tonight -just rebooted a bit ago started up rythmbox and all works again like I said fine for now..

Dell 4600i
Internal Video Card used - 82865G Intel Corporation
Stock Sound Card - internal - Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller


altho it just might be me but the music sounds a bit quicker :P I stayed up all night 4am in the morning PST time as of this post also much quicker than the last kernel


now that I think about it editing in this box seems a bit off on the spaces somewhat at times. :P

nowshining@BOT1NET1GOD1:~$ uname -r
2.6.22-10-generic
nowshining@BOT1NET1GOD1:~$


okay had to recompile setup for virtualbox or whatever in root terminal by doing this command

/etc/init.d/vboxdrv setup

anyway have had so far FEW other problems besides auto fix removed the last kernel I believe...anyway..

Good to hear guys :)

Yea, some people have small issues.. I myself haven't noticed anything thats not working correctly..

---

### Post by arizonagroovejet on 2007-08-25
So anyone done this who is using the nvidia restricted driver?
If I boot up with 2.6.22 then X no longer works. As I expected would be the case. I tried adding the gutsy repo them doing

```
$ sudo apt-get install linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic nvidia-glx-new
```

But then I get
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  gcc-4.2-base gimp gimp-data kdegraphics-kfile-plugins kdelibs-data
  kdelibs4c2a libart-2.0-2 libasound2 libfreetype6 libgcc1 libgimp2.0
  libglib2.0-0 libgnutls13 libgsf-1-114 libgsf-1-common libgtk2.0-0
  libgtk2.0-common libjasper1 libkeyutils1 libkrb53 liblzo2-2 libopencdk8
  libpango1.0-0 libpango1.0-common libpoppler-glib1 libpoppler-qt1 libpoppler1
  librsvg2-2 librsvg2-common libstdc++6 libwmf0.2-7 libxdamage1 libxml2
  linux-headers-2.6.22-10 linux-headers-2.6.22-10-generic
  linux-image-2.6.22-10-generic linux-restricted-modules-2.6.22-10-generic
  linux-ubuntu-modules-2.6.22-10-generic zlib1g
Suggested packages:
  gimp-help-en gimp-help gimp-python libgimp-perl gimp-data-extras gimp-print
  gimp-dbg fam libasound2-plugins libfreetype6-dev gnutls-bin krb5-doc
  krb5-user ttf-thryomanes librsvg2-bin linux-doc-2.6.22 linux-source-2.6.22
  avm-fritz-firmware-2.6.22-10 nvidia-settings nvidia-new-kernel-source
Recommended packages:
  gimp-gnomevfs gimp-libcurl libglib2.0-data
The following packages will be REMOVED
  gtk-qt-engine libpoppler1-qt
The following NEW packages will be installed
  gcc-4.2-base libjasper1 libkeyutils1 liblzo2-2 libpoppler-glib1
  libpoppler-qt1 linux linux-generic linux-headers-2.6.22-10
  linux-headers-2.6.22-10-generic linux-headers-generic
  linux-image-2.6.22-10-generic linux-image-generic
  linux-restricted-modules-2.6.22-10-generic linux-restricted-modules-generic
  linux-ubuntu-modules-2.6.22-10-generic
The following packages will be upgraded:
  gimp gimp-data kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a
  libart-2.0-2 libasound2 libfreetype6 libgcc1 libgimp2.0 libglib2.0-0
  libgnutls13 libgsf-1-114 libgsf-1-common libgtk2.0-0 libgtk2.0-common
  libkrb53 libopencdk8 libpango1.0-0 libpango1.0-common libpoppler1 librsvg2-2
  librsvg2-common libstdc++6 libwmf0.2-7 libxdamage1 libxml2 nvidia-glx-new
  zlib1g
29 upgraded, 16 newly installed, 2 to remove and 707 not upgraded.
Need to get 38.5MB/84.3MB of archives.
After unpacking 192MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```

A bunch of other packages would be updated as a result of nvidia-glx-new for some reason. Anyone actually done this? If so what happened?

I have an Asus mobo and would like 2.6.22 to give me hardware monitoring. lm-sensors doesn't support the sensors on the mobo without 2.6.21 or above.

---

### Post by walkerk on 2007-08-26
> **arizonagroovejet said:**
> So anyone done this who is using the nvidia restricted driver?
If I boot up with 2.6.22 then X no longer works. As I expected would be the case. I tried adding the gutsy repo them doing

```
$ sudo apt-get install linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic nvidia-glx-new
```

But then I get
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  gcc-4.2-base gimp gimp-data kdegraphics-kfile-plugins kdelibs-data
  kdelibs4c2a libart-2.0-2 libasound2 libfreetype6 libgcc1 libgimp2.0
  libglib2.0-0 libgnutls13 libgsf-1-114 libgsf-1-common libgtk2.0-0
  libgtk2.0-common libjasper1 libkeyutils1 libkrb53 liblzo2-2 libopencdk8
  libpango1.0-0 libpango1.0-common libpoppler-glib1 libpoppler-qt1 libpoppler1
  librsvg2-2 librsvg2-common libstdc++6 libwmf0.2-7 libxdamage1 libxml2
  linux-headers-2.6.22-10 linux-headers-2.6.22-10-generic
  linux-image-2.6.22-10-generic linux-restricted-modules-2.6.22-10-generic
  linux-ubuntu-modules-2.6.22-10-generic zlib1g
Suggested packages:
  gimp-help-en gimp-help gimp-python libgimp-perl gimp-data-extras gimp-print
  gimp-dbg fam libasound2-plugins libfreetype6-dev gnutls-bin krb5-doc
  krb5-user ttf-thryomanes librsvg2-bin linux-doc-2.6.22 linux-source-2.6.22
  avm-fritz-firmware-2.6.22-10 nvidia-settings nvidia-new-kernel-source
Recommended packages:
  gimp-gnomevfs gimp-libcurl libglib2.0-data
The following packages will be REMOVED
  gtk-qt-engine libpoppler1-qt
The following NEW packages will be installed
  gcc-4.2-base libjasper1 libkeyutils1 liblzo2-2 libpoppler-glib1
  libpoppler-qt1 linux linux-generic linux-headers-2.6.22-10
  linux-headers-2.6.22-10-generic linux-headers-generic
  linux-image-2.6.22-10-generic linux-image-generic
  linux-restricted-modules-2.6.22-10-generic linux-restricted-modules-generic
  linux-ubuntu-modules-2.6.22-10-generic
The following packages will be upgraded:
  gimp gimp-data kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a
  libart-2.0-2 libasound2 libfreetype6 libgcc1 libgimp2.0 libglib2.0-0
  libgnutls13 libgsf-1-114 libgsf-1-common libgtk2.0-0 libgtk2.0-common
  libkrb53 libopencdk8 libpango1.0-0 libpango1.0-common libpoppler1 librsvg2-2
  librsvg2-common libstdc++6 libwmf0.2-7 libxdamage1 libxml2 nvidia-glx-new
  zlib1g
29 upgraded, 16 newly installed, 2 to remove and 707 not upgraded.
Need to get 38.5MB/84.3MB of archives.
After unpacking 192MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```

A bunch of other packages would be updated as a result of nvidia-glx-new for some reason. Anyone actually done this? If so what happened?

I have an Asus mobo and would like 2.6.22 to give me hardware monitoring. lm-sensors doesn't support the sensors on the mobo without 2.6.21 or above.

If you look back one page there is a user that did this.. give him a PM..

---

### Post by arizonagroovejet on 2007-08-26
> **walkerk said:**
> If you look back one page there is a user that did this.. give him a PM..

So there is. They don't mention that a whole bunch of other packages will get upgraded though. Which seems like a fairly big thing to not mention if it happened.

---

### Post by walkerk on 2007-08-26
> **arizonagroovejet said:**
> So there is. They don't mention that a whole bunch of other packages will get upgraded though. Which seems like a fairly big thing to not mention if it happened.

Exactly why I said you should PM that user. I am sure he'll be more than happy to let you know what was upgraded when he did it.. I can't tell you because I don't have an nvidia card..

---

### Post by Xan63 on 2007-08-26
> So anyone done this who is using the nvidia restricted driver?
If I boot up with 2.6.22 then X no longer works. As I expected would be the case. I tried adding the gutsy repo them doing


I've a nvidia graphic card (8600GT) and I'm using Envy with Gutsy repos.

You can get envy [here]("http://albertomilone.com/nvidia_scripts1.html")

The installation worked like a charm :)

---

### Post by arizonagroovejet on 2007-08-26
> **Xan63 said:**
> I've a nvidia graphic card (8600GT) and I'm using Envy with Gutsy repos.

You can get envy [here]("http://albertomilone.com/nvidia_scripts1.html")

The installation worked like a charm :)

The installation may have worked like a charm, but will you still be so happy come the next kernel update?
When I ran Fedora I had to manually sort out the nvidia driver every time there was a kernel update and it got rather tedious. With Kubuntu that hassle is eliminated. Using the Envy script would re-introduce that hassle. Seems I may as well install the nvidia driver myself off nvidia.com as I did with Fedora as use Envy.

---

### Post by lemurian on 2007-08-26
> **arizonagroovejet said:**
> The installation may have worked like a charm, but will you still be so happy come the next kernel update?
When I ran Fedora I had to manually sort out the nvidia driver every time there was a kernel update and it got rather tedious. With Kubuntu that hassle is eliminated. Using the Envy script would re-introduce that hassle. Seems I may as well install the nvidia driver myself off nvidia.com as I did with Fedora as use Envy.
Envy packages the closed source nvidia driver neatly.  That's the advantage over just grabbing the driver from nvidia's site and installing yourself.

As far as upgrading the kernel, here's the "hassle" you have to go through if you use envy:

1. Upgrade the kernel.
2. Reboot.
3. Wait until Ubuntu detects that X cannot be started.  Reply no to the question about diagnosing the problem and acknowledge the following dialog which says that you will need to restart gdm manually.
4. Once at the console, log in.
5. Execute sudo envy -t
6. Select option 1.
[Envy will do its work.  May take about one minute.]
7. Envy will want you to reboot but there's really no need for that.  Just exit it.
8. sudo /etc/init.d/gdm restart

You're done.  There's nothing in there which is particularly esoteric.  It looks like a lot of steps but it's really pretty trivial.  Takes me 5 minutes max.  That's a "hassle" I can easily live with if it means that I can use the latest nVidia drivers and that the work of packaging them will be done by an automated system.  All other solutions either:

1. Just leave all kinds of files floating everywhere because nVidia did not package their driver for Ubuntu.

2. Or require *me* to do the work that Envy does for me.

3. Or rely on drivers that do not work with my graphic card (e.g. the "nv" drivers) or that do not take full advantage of the capabilities of my card.

I'll take Envy any day, thank you.

---

### Post by st33med on 2007-08-26
> **nowshining said:**
> sound working fine for me just upgraded to the latest tonight -just rebooted a bit ago started up rythmbox and all works again like I said fine for now..

Dell 4600i
Internal Video Card used - 82865G Intel Corporation
Stock Sound Card - internal - Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller


altho it just might be me but the music sounds a bit quicker :P I stayed up all night 4am in the morning PST time as of this post also much quicker than the last kernel


now that I think about it editing in this box seems a bit off on the spaces somewhat at times. :P

nowshining@BOT1NET1GOD1:~$ uname -r
2.6.22-10-generic
nowshining@BOT1NET1GOD1:~$


okay had to recompile setup for virtualbox or whatever in root terminal by doing this command

/etc/init.d/vboxdrv setup

anyway have had so far FEW other problems besides auto fix removed the last kernel I believe...anyway..

I have heard that the card does not produce any sound at start-up. I haven't had that problem... Until I wake it up from suspend, then that is when I notice the lack of sound. I guess it varies by motherboard and other things.

I hope .22-11 comes out soon.

---

### Post by Gremlinzzz on 2007-08-26
Just upgraded thxs 2.6.22-10-generic 
:guitar:

---

### Post by ResumeMan on 2007-08-26
Well I just tried it on my Toshiba Satellite A45 and it *seems* like everything is working right -- including Suspend, which was seriously problematic on the old kernel. Thanks!

---

### Post by kelly.seay on 2007-08-26
Hello.

I did this while using Ubuntu 7.04 , and it worked perfectly.  Then I got bored and loaded Kubuntu 7.04.  I did this for Kubuntu and now my sound doesn't work.  I don't know where to begin to troubleshoot this.  And when I type alsamixer in the terminal, i get snd_ctl_open failed for defautl:  no such device  I am using a Sony VAIO FS-550, and sound has worked for everything else i have put on it from Dapper to Fiesty, just not this upgrade with Kubuntu.  Any help that you guys can give would be great, because my system runs so much better with the new kernel.  I can really tell the difference in speed.

Edit:  Nevermind.  I fixed it.  I uninstalled the updated kernel and re-installed it.  something must not have loaded right when i did it the first time.

WORKS GREAT.  I LOVE IT!!!  Now if i could only get Gutsy to work, i would be happy.  Fiesty will do till the final release of Gutsy.

---

### Post by epidemiks on 2007-08-27
Just did this on my girlfriends Pioneer M66 SE, and all seems to be working fine.. I was hoping it would miraculously fix the VIA Chrome9 issues I'm having, but no such luck!

---

### Post by steam_engenius on 2007-08-27
I upgraded a few days ago and the install went smoothly but for some reason my internet wasn't working. I was able to see my network in network manager but then I couldn't get online. And I would have to determine that it was because of the upgrade seeing that I am able to access the web with the 2.6.20-16 kernel and theres nothing defective with my adapter. Anyone else experience this issue, or have any advice?

---

### Post by walkerk on 2007-08-27
> **steam_engenius said:**
> I upgraded a few days ago and the install went smoothly but for some reason my internet wasn't working. I was able to see my network in network manager but then I couldn't get online. And I would have to determine that it was because of the upgrade seeing that I am able to access the web with the 2.6.20-16 kernel and theres nothing defective with my adapter. Anyone else experience this issue, or have any advice?

Same thing happened when I first upgraded.. Give this a shot..

Add the Gutsy repo
```
echo 'deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted' | sudo tee -a /etc/apt/sources.list
```

Update
```
sudo apt-get update
```

Reinstall the ubuntu and restricted modules
```
sudo apt-get --reinstall install linux-ubuntu-modules-2.6.22-10-generic linux-restricted-modules-2.6.22-10-generic
```

Now remove the repository (last line of sources.list) & save.
```
gksu synaptic
```

Update
```
sudo apt-get update
```

Reboot
```
sudo reboot
```

---

### Post by nowshining on 2007-08-27
A note to others some updates for gutsy make things go quicker and the sound better and booting up and down quicker, BUT be SELECTIVE when updating, when a box comes up asking to do partial click the close button, then right click and select clear all or uncheck all and be selective of the updates to download, but remember some updates CAN affect gameplay such as slowness in some games - unless ur video card doesn't work right now - stay away from the driver updates - just a warning - if not - go to synaptic package mananger and uninstall that update video card driver and do another search for your card and re-install it - esp. warning to Intel card users - uninstall the last one and there should be a double for 800 - 900 users but in the description one has the ubuntu logo and one does not, if you find slowness because of an update - just install the one with the logo next to the title/name..

I higly suggest doing manual updates and not automatic tho............. :) and of course manual checking... Python works fine, the new sudo works fine - now sudo says it wants a password from the certain username - um.. also stuff works fine, and stuff like that.. :) so yes My install is a mutt BUT so far quicker now since I did selective gutsy updates - i skipped stuff such as the grub and iptables install..lolz..anyway go have fun you kids..... :P


edit: oh yeah - update slow - and always reboot even if it doesn't ask because that's the only way some things work is after a reboot in feisty... oh and some things CAN NOT be SELECTED ANYWAY..lolz.. so don't go trying to install the latest rythmbox it won't checkmark..

---

### Post by greew on 2007-08-27
I didn't get this to work.
I did exactly as told in the howto and ended up with X not starting with this error:
> (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

I'm using a Dell Inspiron 6400 with GeForce Go 7300.

Anyone has an idea of what to do? If you would like more info, please say so :)

Best regards,
Jesper

---

### Post by walkerk on 2007-08-28
> **greew said:**
> I didn't get this to work.
I did exactly as told in the howto and ended up with X not starting with this error:

I'm using a Dell Inspiron 6400 with GeForce Go 7300.

Anyone has an idea of what to do? If you would like more info, please say so :)

Best regards,
Jesper

First take a look at this page: [http://ubuntuforums.org/showthread.php?t=511974&highlight=nvidia-glx-new&page=35](http://ubuntuforums.org/showthread.php?t=511974&highlight=nvidia-glx-new&page=35)

The same thing happened to spartikas but adding the nvidia-glx-new package from teh gutsy repos did the trick for him..

Or you can try reconfiguring Xorg:

Boot into 2.6.22-10 recovery mode and do the following from the command line..
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
startx
```

??

---

### Post by toasterboy1 on 2007-08-28
Worked on my Compaq Presario V6133CL Notebook. Hope that helps with the wireless. Also thanks for the wicd post.

---

### Post by walkerk on 2007-08-28
> **toasterboy1 said:**
> Worked on my Compaq Presario V6133CL Notebook. Hope that helps with the wireless. Also thanks for the wicd post.

Sure thing :)

---

### Post by levimax on 2007-08-29
Worked perfectly... too easy!

Lenovo Thinkpad X61s

Thanks!

---

### Post by olavjunior on 2007-08-29
> **walkerk said:**
> ok.. you probably need the nvidia-glx-new or legacy.. add the gutsy repo again and do the following:
```
sudo apt-get install nvidia-glx-new
```

i doubt you have a legacy card but if the above doesn't work try:
```
sudo apt-get install nvidia-glx-legacy
```

**now be sure to remove the gutsy repo and run update..**

You saved my day! :) This worked out great! Have been messing around for hours, until I found your post. Now I have new kernel & fusion running :lolflag:

I have an hp dv 2135

---

### Post by CalvinK on 2007-08-29
> **walkerk said:**
> This should work for Feisty Fawn and Edgy Eft users. This will install the current developing kernel that will be realeased with Gutsy Gibbon.

**[COLOR="Red"]Do not upgrade any packages while you have the Gutsy repository open.[/COLOR]**

[COLOR="Red"]Disclaimer:[/COLOR] This is how I successfully upgraded my kernel without having to compile it myself. A couple of users have had issues with this method so be aware that problems can arise. At this point removing the new kernel using the instructions at the end of the post should do the trick, but if it doesn't I take no responsibility. I will monitor this thread to try to help out anyone thats had issues.

*** With that being said, most users have not had any problems and are enjoying the new kernel. Also, this will not remove your current kernels.***

[SIZE="3"][COLOR="DarkOrange"]**After you've upgraded please reply with your machine Model and specs so that others can benefit :)**[/COLOR][/SIZE]


[SIZE="4"]**You can download the script I've attached and do the following:**[/SIZE]

**[COLOR="DarkOrange"]kernel.sh[/COLOR]** will upgrade to the current kernel using meta packages, meaning if you run this every week or so it will upgrade your kernel if a new version has been released. Current version is **2.6.22-10**
- *if for some reason kernel.sh (using zenity dialogs) doesn't work you can simply download and use kernel_cli.sh instead.*

Move to the directory in which you downloaded the script.. for example:
```
cd /home/your_username/
```

make the script executable:
```
chmod +x kernel.sh
```

run the script:
```
./kernel.sh
```

This installed the new kernel. Enjoy :)



[SIZE="4"]**Or you can do it manually...**[/SIZE]

First you need to add the Gutsy repository (this is only temporary to pull the new kernel):
```
echo 'deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted' | sudo tee -a /etc/apt/sources.list
```

Now that you've added the repository you need to update:
```
sudo apt-get update
```Next you need to install the new kernel:
```
sudo apt-get -y install linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
```Now that you've pulled the kernel you should remove the Gutsy repository from your sources.list:
```
gksudo gedit /etc/apt/sources.list
```Now you can remove the line or simply comment it out: (It'll be the last line of the file)
```
#deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
```
Once again you need to update so that you'll stop pulling updates from the Gutsy repository:
```
sudo apt-get update
```Alright. If you've done all of the above without errors, you've successfully installed 2.6.22-9-generic. Now you need to reboot into the new kernel:
```
sudo reboot
```Enjoy :)[COLOR="Blue"]

**Are having issues with direct rendering and such with ATI video (specifically 200M chipset)?**
*Take a look at jamiepluncinski's post: [http://ubuntuforums.org/showthread.php?p=3136258#post3136258]("http://ubuntuforums.org/showthread.php?p=3136258#post3136258")*
[/COLOR]

[SIZE="3"]**Ok.. Did it hose your box? Too easy.**[/SIZE]

Reboot your computer and at Grub press esc to boot into your last kernel. (probably 2.6.20-16-*)

Remove the installed kernel and then upgrade. 
```
sudo apt-get remove linux-image-2.6.22-10-generic linux-headers-2.6.22-10-generic linux-headers-2.6.22-10 linux-restricted-modules-2.6.22-10-generic linux-ubuntu-modules-2.6.22-10-generic
```
```
sudo apt-get upgrade
```


**Updates**
8/12/2007: *Added GUI (zenity dialogs) to the script*
8/8/2007: *Changed script to look for and install Meta packages*
8/7/2007: *Cleaned up kernel.sh*

Thank you very much. I discovered then that I'll have some problem to use my CD/DVD since I obtain a very strange behavior when trying to use it with the new kernel. I have a Toshiba A200/1-DR laptop.

---

### Post by olavjunior on 2007-08-29
Well, this wasn't so great afterall.. Now nautilus crashes everytime I try to access / without opening in a new window! Any ideas??

---

### Post by tact on 2007-08-29
I followed this guide (the manual process) twice now.  First time to go from the standard feisty kernel 2.6.20-16-generic to 2.6.22-9-generic.  Then to 2.6.22-10-generic on my Dell Latitude D410 laptop.

With both the -9 and -10 kernels found that suspend/hibernate now works perfectly.  It never worked on the standard kernels.  I also find I can burn DVD's again, no more burning coasters as was the case under the standard kernel.

Networking seems to be more reliable, but this is a purely subjective feeling I guess, I never had any networking problems really...  what I am enjoying is what I could not do before when suspend/hibernate never worked -  being able to suspend/hibernate and find networks come back up automatically on resume.

---

### Post by walkerk on 2007-08-29
> **olavjunior said:**
> Well, this wasn't so great afterall.. Now nautilus crashes everytime I try to access / without opening in a new window! Any ideas??

```
sudo apt-get --purge remove nautilus
```
```
sudo apt-get install nautilus
```

might do the trick...

---

### Post by olavjunior on 2007-08-30
> **walkerk said:**
> ```
sudo apt-get --purge remove nautilus
```
```
sudo apt-get install nautilus
```

might do the trick...

Nope, it's still the same :(

---

### Post by nowshining on 2007-08-30
Try this

open up a terminal

sudo apt-get install -f

and post the output here

and also do this

sudo apt-get autoremove

and input the output here..

---

### Post by nowshining on 2007-08-30
edit error on their side - slow, to respond and junk so I thought at first it was me and hit save/quick reply again and it first gave me one post - then later on it did many more duplicates but after  exiting this thread and then returning did it work and only showed a double post.. :/

---

### Post by shearn89 on 2007-08-30
worked like a charm on my old laptop! cheers for the guide...

---

### Post by olavjunior on 2007-08-30
> **nowshining said:**
> Try this

open up a terminal

sudo apt-get install -f

and post the output here

and also do this

sudo apt-get autoremove

and input the output here..

Sorry, after deleting a partition and not getting home back up, I've desided to reinstall everything from scratch! It needs to be done some day anyway, got such a messy partition-table. I think I'll wtay away from the latest kernel after that..

---

### Post by nowshining on 2007-08-30
wow, anyway those commands can be run in the default feisty kernel

let me explain

sudo apt-get install -f

fixes up any dependencies your having = but MAKE SURE there is NOTHING like nautilus,  the calculator, etc.. in there - it can mess up your system that's why i asked u to post.

sudo apt-get autoremove

automatically scans for and removes uneeded files


or download open up start - system - administration -synaptic package manger and find

GtkOrphan

right click click MARK

at the top click APPLY to download and install

Great program :) but be careful it can to mess ur system up, but that's only if you enable to show uninstalled files other than Lib files so keep it there (lib = library files)

it's in the same place as synaptic package manager but named remove orphaned packages

it starts in orphaned packages - and libs Trust me when these babies are left it can impact ubuntu badly - slowness, hiccups, etc..

:)

the safest I learnt to do was in the options

bottom - arrow then word options - click it

Show uninstalled packages with orphaned configuration files

DO NOT check the last option - now that will ruin u, again keep it in the LIB section and you'll be fine.. ;)

edit: on the drop down menu there I believe Guess other libraries and when set to ALL is fine tho.. :)

---

### Post by NewEnough on 2007-08-30
Super!  I did the manual installation, and now my system sounds, and 
Javascript sounds in Firefox work.  A half hour well spent, after several weeks of searching the forums and Google.

I have a 3 GHz Pentium 4 in a Sony VGC-RB30, with 1.5 GB of RAM
My video card is an ATI RV410, Radeon X700 Pro
and my audio card is a Creative Sound Blaster 400 Audigy 2 Value

Thanks, folks.

---

### Post by jpquental on 2007-08-30
Everything ok!

Compaq 2541 EA with 1 Gb of ram & Novatel U740

---

### Post by PmDematagoda on 2007-08-30
New kernel works like a charm:guitar:, the only thing is now I have a ton of updates that are clearly meant for Gutsy Gibbon since Update Manager's telling me that a partial upgrade will be done, do you think that's advisable?

By the way system specs are:

3.2Ghz Hyper-threaded P4 Processor(Intel)
256Mb GeForce 6200 Nvidia
1Gb RAM(DDR)
280 GB SATA
Intel 915GAV motherboard built-in soundcard(Don't know the real name)

---

### Post by Brachabre on 2007-08-30
Atm I have already done the kernel upgrade to 2.6.22 a few weeks ago and my ATI x1400 card on a Dell Inspiron 9400 laptop doesn't have 3D acceleration (Direct Rendering). 

Would it be possible (or help) to re-enable the Gutsy repo and download the newer updated fglrx driver made for gutsy ALSO to install the 2 required packages the fglrx driver needs to update:  "libfreetype6"  and "zlib1g"

Would this help me at all to maybe get my 3D working? Or would it be very UNwise to try something like this..

---

### Post by nowshining on 2007-08-30
i do not know about libfreetype6 but zlib maybe will install, I install many things that work on feisty

iptables
many library files
python i believe

i'll check to see i probably installed libfreetype if not i'll give you the heads up and I already believe i installed zlib tho... please wait..again you got to be very selective of what you want to install or else it could poss mess u up...

but again i do believe library files are fine, i also installed zip latest, etc.. :) just make sure that when the dialog box comes up asking to partial update choose close and the make sure an update is highlighted and right click and uncheck all.. :)


edit: I do not have a need to install them as they are not listed so either I already installed or they never came up, most likely tho i already installed them on the side note for me i downloaded gutsy xserver latest :) well the drivers did when I was trying out both being installed at the same time, so far a bit slowness when quitting and it coming up, but no biggie and installed libdbus i believe and now it suppose to load before GDM so far a bit quickerness.. :)

back on topic Brachabre more than likely the best thing is to TRY :) the updates....


edit 2/3: i noticed that now the colors are just right on my monitor after that.. :D

---

### Post by nowshining on 2007-08-31
update:

installed 19.9 + megabyte library files, x.org stuff, etc.. gnome vfs, etc..  and grub, etc.. all fine from my end so far.. :) and it's getting betters... :D


edit 2/3 : removed bindhost or whatever 9 crud - it updated some things to gutsy (i haven't disabled the check yet) and so far quicker.. ;)

---

### Post by steam_engenius on 2007-08-31
Walkerk I reinstalled those packages and rebooted and the issue still persists. When I open Network Manager and switch the adapter to roaming mode I see my network and even (I'm guessing) my neighbors, I just can't get online.

When I run iwconfig I get this message, along with some info about the adapter:

"Warning: Driver for device rausb0 has been compiled with version 22 of Wireless Extension, while this program supports up to version 20. Some things may be broken..."

---

### Post by BC7333 on 2007-08-31
> **steam_engenius said:**
> 

When I run iwconfig I get this message, along with some info about the adapter:

"Warning: Driver for device rausb0 has been compiled with version 22 of Wireless Extension, while this program supports up to version 20. Some things may be broken..."

I get the same here, but wireless working quite well with upgrade to -10 from -9 using Walkerks updated script - seems even better than with -9.

Am using wifi-radar to get SSID's then fiddling with System -->Administration-->Network settings  to actually get connected.

wlan adapter here intel pro 3945

Have done so much fiddling around though I probably created some kind of networking 'mess' that somehow works.. don't ask me how lol

---

### Post by olavjunior on 2007-08-31
> **nowshining said:**
> wow, anyway those commands can be run in the default feisty kernel

let me explain

sudo apt-get install -f

fixes up any dependencies your having = but MAKE SURE there is NOTHING like nautilus,  the calculator, etc.. in there - it can mess up your system that's why i asked u to post.

sudo apt-get autoremove

automatically scans for and removes uneeded files


Thanks alot for the help, I will note this down, thanx!

---

### Post by walkerk on 2007-08-31
> **PmDematagoda said:**
> New kernel works like a charm:guitar:, the only thing is now I have a ton of updates that are clearly meant for Gutsy Gibbon since Update Manager's telling me that a partial upgrade will be done, do you think that's advisable?

By the way system specs are:

3.2Ghz Hyper-threaded P4 Processor(Intel)
256Mb GeForce 6200 Nvidia
1Gb RAM(DDR)
280 GB SATA
Intel 915GAV motherboard built-in soundcard(Don't know the real name)

You did remove the Gutsy repos and update right? Or did you use the script?

After upgrading the kernel you shouldn't be getting anymore upgrades from the Gutsy repos..

---

### Post by Brachabre on 2007-08-31
wow, I updated to the new driver (w/ the 2 libraries) and for the first time in I don't know how long, I got 3D acceleration. I'm so used to doing fglrxinfo and getting Mesa as the reply.

Everything is much better now. Thanks.

---

### Post by ramjet_1953 on 2007-09-01
Thanks for that tutorial walkirk!

The kernel.sh script worked flawlessly!

[COLOR="Blue"]Acer TravelMate 4101WNLCi[/COLOR]

Pentium M730 CPU 1.6GHz
Intel 915GM/GMS/910 Express Graphics Controller
Ethernet: Broadcom BCM4401 100 Base T
Wireless: Intel Pro/Wireless 2200BG

Regards,
Roger 8)

---

### Post by Kyran on 2007-09-01
Seems that Nautilus doesn´t like me anymore. Updated to 2.6.22-10 from 2.6.22-9 on one computer and from 2.6.20-16 another. It seems that when I updated the the Nvidia driver so it matches the one with the new kernel it updated a bunch of other dependences which causes Nautilus to crash when opening a new folder in the same window. -f and autoremove return nothing. Removing Nautilus doesn´t help either. I´m going to try installing Nautilus from the Gusty repository.

EDIT: Installing Nautilus from the Gusty repositories fixed the problem.

---

### Post by walkerk on 2007-09-01
> **Kyran said:**
> Seems that Nautilus doesn´t like me anymore. Updated to 2.6.22-10 from 2.6.22-9 on one computer and from 2.6.20-16 another. It seems that when I updated the the Nvidia driver so it matches the one with the new kernel it updated a bunch of other dependences which causes Nautilus to crash when opening a new folder in the same window. -f and autoremove return nothing. Removing Nautilus doesn´t help either. I´m going to try installing Nautilus from the Gusty repository.

EDIT: Installing Nautilus from the Gusty repositories fixed the problem.

Very good :) I'm going to type out this process step by step for other users..

**Upgrade Nautilus**

Add the Gutsy repository
```
echo 'deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted' | sudo tee -a /etc/apt/sources.list
```

Update
```
sudo apt-get update
```

Upgrade Nautilus
```
sudo apt-get install nautilus
```

Remove the Gutsy repo from sources.list (The last line of the file)
```
gksu gedit /etc/apt/sources.list
```

Now update again
```
sudo apt-get update
```

That should do the trick.. I don't use Nautilus so I didn't do this myself but it worked for Kyran.

---

### Post by nowshining on 2007-09-01
hey i just went to the gutsy repos and download the nautilus package - double clicked it - hit install - and it downloaded all it needed..awesome last time it never did go out and so I had to try with the libs all by myself - :) overall FASTER FASTER AND FASTER....now for gnome..heheheh :)
 
 
 
 
 
 
edit: somethings changed in nautilus or a lib now I can hear my harddrive crunching away after the GRUB menu automatically goes it away...used to it was REAL QUIET... :P






edit2: n/m on the gnome environment lolz it depends on a boat load of things..so i'll just stay away.. :) (and I have dialup)

---

### Post by darco on 2007-09-01
Im a noob and when I saw this thread I said "dont do this, wait until the Gutsy release, what if something happens, etc.. ". Well just like that saying "why did you climb that Mountain? ...Because its there!!."....So with that being said, I upgraded using this script, worked flawlessly...Excellent work, you should work for Ubuntu since my upgrade from Edgy to Feisty was a horrible. Had to reinstall from scratch...
thanks
Darco

AMD 1750
Epox MB
ATI Rage XL
1gig ram
(this aint my main system :lolflag: )

---

### Post by MorganLowe on 2007-09-01
Well, Dell Latitude D620 with BT/WIfi/Nvidia Quattro NVS110m worked good. Had a lot of Nvidia trouble. I did the upgrade then rebooted, no X. I used nano to open the repository for Gutsy again.

```
nano /etc/apt/sources.list
```

Then I uncommented the Gutsy repo. Once that was open, I did an update.

```
apt-get update
```

once the update was done, I grabbed the new Nvidia, and it seemed to hook a bunch of other stuff with it.

```
apt-get install nvidia-glx-new
```

when that was all done, I typed REBOOT and was at my Gnome login.

Once back into the system, I turned off gutsy repos, and updated. one more reboot and all was good to go.

Everything feels fine, runs good, Beryl still works, even my installation of starcraft. I was logged in as ROOT during this process.

---

### Post by nowshining on 2007-09-01
so far on my end I updated just about all I could so far so far my computer seems just right so I may not upgrade NO MORE, except for of course kernels.. :) gnome menu updated to the latest and like I said quick... if anyone updates or wants to update update manager - UPDATE BOTH THE CORE AND MAIN PROGRAM or else it WILL NOT work if you forget go to the gutsy repos and at the very bottom click to show ALL files / programs, etc.. and find the main program there and download - install and now all should be well and also EVERYONE CLEAN OUT ORPHANED files as this will help fix/speed up your system.. :)
 
 
 
 
 
 
edit: only thing left is a that when a song changes in rythmbox and I am playing a game it skips - well at least supertuxkart... :( edit2 & some games are a bit slow right now - maybe a couple more updates... :P

---

### Post by nowshining on 2007-09-01
wow i think i've pretty much updated to GUTSY with a small percentage of Feisty..lolz :P

---

### Post by karmy on 2007-09-02
I just installed manually on kubuntu 7.04, Latitude D600, ATI Mobility 9000 - as I'm on linux just for a month, I'm really proud on myself! Especially cause everything went smoothly and no problems at all!!!!! Everything works like before, even my compiz fusion! Wireless also works without problems, sound, suspend, well...everything! But I must say that everything worked before too, so I didn't expect less from this kernel upgrade :)
I secretly hoped that my open gl screensavers will finally integrate with superkaramba widgets (as this is the only problem I've had and till today didn't found solution...), but, it'll be to much, wouldn't it? ;)) 

Tnx for the guide!

---

### Post by Kyran on 2007-09-02
Got the 2.6.22-10 working on:
[list][*]ASUS A6KM[*]NVIDIA GeForce 7300 Go[*][*]1.5GB Ram [*]Sempron 3100+[/list][list][*]Gateway 810E[*]Pentium 3 800Mhz[*]256MB Ram[*]GeForce FX 5200 PCI[/list]

---

### Post by rahimveron on 2007-09-02
Got the 2.6.22-10 working on:
P4 2.4 Ghz
512 RAM
Intel 845GVSR motherboard with onboard graphics and sound

---

### Post by nowshining on 2007-09-02
well looks like everything is just about RIGHT for me really i have updated updated gedit, gnome panels apps nautilus, etc.. :) and  everything old seems fine sound sounds good at this moment.. :) I may just stick to what I got for now, and if I do order the Gutsy CD it will only be incase I need to re-install..lolz.. :) less likely tho....

hey  [rahimveron]("http://ubuntuforums.org/member.php?u=322486") is your rig custom built or a DEll? Gateway? other? i'm just curious...

---

### Post by obavjestenja on 2007-09-02
i want to install compiz fusion with this guide [http://ubuntuforums.org/showthread.php?t=488385&highlight=compiz+fusion](http://ubuntuforums.org/showthread.php?t=488385&highlight=compiz+fusion)
can this work after your kernel update ?

---

### Post by walkerk on 2007-09-02
> **obavjestenja said:**
> i want to install compiz fusion with this guide [http://ubuntuforums.org/showthread.php?t=488385&highlight=compiz+fusion](http://ubuntuforums.org/showthread.php?t=488385&highlight=compiz+fusion)
can this work after your kernel update ?

compiz-fusion is unaffected by the kernel upgrade.. it runs perfectly on my laptop..

---

### Post by obavjestenja on 2007-09-02
> **walkerk said:**
> compiz-fusion is unaffected by the kernel upgrade.. it runs perfectly on my laptop..


i installed compiz fusion but when i log i have this is desktop  ?

my card its ATI Xpress 200M

[[IMG]http://img49.imageshack.us/img49/2015/screenshotnq7.png[/IMG]](http://imageshack.us)

any help ?

---

### Post by obavjestenja on 2007-09-02
please  :(

---

### Post by walkerk on 2007-09-02
> **obavjestenja said:**
> please  :(

boot in safe mode and run
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by obavjestenja on 2007-09-02
how to boot in safe mode ?
sorry

---

### Post by walkerk on 2007-09-02
> **obavjestenja said:**
> how to boot in safe mode ?
sorry

reboot and press ESC at Grub 1.5.. then choose recovery mode..

---

### Post by obavjestenja on 2007-09-02
> **obavjestenja said:**
> how to boot in safe mode ?
sorry

same thing,no desktop:(

---

### Post by obavjestenja on 2007-09-02
something else to try ?

---

### Post by obavjestenja on 2007-09-02
please again :)

---

### Post by lemurian on 2007-09-02
obavjestenja, I've also followed walkerk's procedure and run compiz-fusion without any problems being traceable to the kernel upgrade.  (There are problems but I think they are all due to compiz-fusion being unstable.)

I'm thinking your problem is a compiz-fusion problem.

---

### Post by ocrampal on 2007-09-02
Walkerk,

thanks! After running the script, the wireless card finally worked. I have a HP DV6500. I'll world on the problem with the sound. The only problem, is that at boot, it says something about a PCI ... (Same message with the previous kernel) maybe they still have something to fix, but it does not stop the boot.

Thanks again!

---

### Post by LordMau on 2007-09-02
> **obavjestenja said:**
> i installed compiz fusion but when i log i have this is desktop  ?

my card its ATI Xpress 200M

any help ?

you may need to install an updated ati driver as that looks similar to what I went thru. See this: [LINK]("http://ubuntuforums.org/showpost.php?p=3134850&postcount=147").

BTW that tip is also on the first page of this thread.

---

### Post by bluespymaster on 2007-09-03
To get TrueCrypt working on the upgraded kernel, see this post:

[http://ubuntuforums.org/showthread.php?p=3305652#post3305652](http://ubuntuforums.org/showthread.php?p=3305652#post3305652)

---

### Post by greew on 2007-09-04
Wow, thanks walkerk,
Now I got it to work also with my nvidia card.

Now, I've encountered two problems until now:
1. KPDF just doesn't open. When I try opening from terminal, I get this: 
> kpdf: symbol lookup error: /usr/lib/kde3/libkpdfpart.so: undefined symbol: _ZN12GlobalParamsC1EPc

2. I'm running Kubuntu. When I try to open System Settings from the menu, it crashes. I'v added the backtrace:
> (no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found) < this comes up 39 times
[Thread debugging using libthread_db enabled]
[New Thread -1233033008 (LWP 16245)]
(no debugging symbols found) < this comes up 12 times
0xffffe410 in ?? ()
#0  0xffffe410 in ?? ()
#1  0xbffa68a8 in ?? ()
#2  0xb7af0ff4 in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xbffa6894 in ?? ()
#4  0xb7a3de90 in nanosleep () from /lib/tls/i686/cmov/libc.so.6
#5  0xb7a3dcc7 in sleep () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7837ad9 in KCrash::startDrKonqi () from /usr/lib/libkdecore.so.4
#7  0xb784e4de in KCrash::defaultCrashHandler () from /usr/lib/libkdecore.so.4
#8  0xffffe420 in ?? ()
#9  0x0000000b in ?? ()
#10 0x00000033 in ?? ()
#11 0xc0100000 in ?? ()
#12 0x0000007b in ?? ()
#13 0x0000007b in ?? ()
#14 0x080b34e0 in ?? ()
#15 0x08115420 in ?? ()
#16 0xbffa8e58 in ?? ()
#17 0xbffa8e30 in ?? ()
#18 0x00000000 in ?? ()


Does anyone have an idea of what might be wrong here, or have anyone else had the same problem?

---

### Post by atlfalcons866 on 2007-09-05
but isnt gutsy unstable? so would the kernel make feisty unstable then?

---

### Post by walkerk on 2007-09-05
> **atlfalcons866 said:**
> but isnt gutsy unstable? so would the kernel make feisty unstable then?

2.6.22 is already finished. The Ubuntu dev's release security patches only.. your -9, -10 (just like 2.6.20-15, 16)

The current developing kernel is 2.6.23 (kernel.org)

---

### Post by atlfalcons866 on 2007-09-05
why couldnt ubuntu include this kernel in fiesty?

---

### Post by atlfalcons866 on 2007-09-05
also will i still get updates 
i dont mean to ask so many questions

---

### Post by walkerk on 2007-09-05
> **atlfalcons866 said:**
> why couldnt ubuntu include this kernel in fiesty?

Becase the Ubuntu developers on release security patches after a versions been finished. They only upgrade kernels with new versions of Ubuntu..

Fiesty will always have 2.6.20-whatever
Gutsy will always have 2.6.22-whatever

You can alway compile the newest kernel along with the necessary modules to use in any version of Ubuntu.. this is just a simple way to upgrade to 2.6.22 w/out compilng it yourself..

---

### Post by atlfalcons866 on 2007-09-05
i upgraded and my xorg crashed. I have an old nvidia card. I tryed to install the gusty version but i am stuck with fiesty xorg one

---

### Post by walkerk on 2007-09-05
> **atlfalcons866 said:**
> i upgraded and my xorg crashed. I have an old nvidia card. I tryed to install the gusty version but i am stuck with fiesty xorg one

There is a link about nVidia cards in the OP. Take a look [here]("http://ubuntuforums.org/showpost.php?p=3246585&postcount=342")

---

### Post by vaguelyweird on 2007-09-05
Hi -- Tried to manually upgrade kernel, installing the following packages:

linux-backports-modules-2.6.22-10-generic linux-headers-2.6.22-10 linux-headers-2.6.22-10-generic linux-image-2.6.22-10-generic linux-restricted-modules-2.6.22-10-generic linux-ubuntu-modules-2.6.22-10-generic

and also

linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic (just to make sure)

after reboot, wireless no longer was available, and iwconfig no longer lists eth1 (wireless card)

wired ethernet seems to work fine

can you help?
thanks!

---

### Post by vaguelyweird on 2007-09-05
oh.. i have an orinoco_cs card, which is apparently not supported after 2.6.22-8 ):

---

### Post by flyinraptr on 2007-09-06
I ran the script and installed the 2.6.22-9-generic kernel into Feisty .... everything is running awesome  ......  Thank you -  Well Done!!.  

Decided to install Vmware Server .... running the vmware-config.pl and getting the  error ...

[I]"Your kernel was built with "gcc" version "4.1.3", while you are trying to use 
"/usr/bin/gcc" version "4.1.2"."
[/I]

When prompted I proceed anyway until I get 

[I]"What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] "
[/I]

When I look in /usr/src .... I have linux-headers-2.6.22-9  but when I do a uname -r  the result is linux-headers-2.6.22-9-generic ... In any event - the Vmware won't create the modules.  

I tried upgrading to 2.6.22-10 and that worked as far as installing Vmware but I ran into problems with the system crashing everytime I would shutdown or restart - I traced the problem back to the latest Nvidia drivers (found it on one of their forums).  

When I reverted back to the older Nvidia drivers - xserver broke with 2.6.22-10.  Long story short I reverted back to 2.6.22-9 with the older Nvidia drivers and everything is working perfectly  except for the Vmware install issue.  

I tried adding the Gusty repository and looking for the 2.6.22-9-generic source but couldn't find it.  I tried renaming the directory to 2.6.22-9-generic and that didn't work.

Any ideas?

---

### Post by tact on 2007-09-06
This is a bit off topic (sorry OP - it will be brief)....

I compiled VMWare Server on my 2.6.22-9 kernel (installed by following the manual process in this thread).  

It gave a few problems but after googling I found some guides that pointed to the need to patch the VMware server source before you compile it.

The patch is called vmware-any-any-updatexxx  (where xxx= the highest number you find for the latest version).   I used "vmware-any-any-update103"

After applying this patch you still get the version mismatch message regarding GCC but thats safely ignored.

With the vmware server source patched with the any-any patch when I again upgraded kernel to 2.6.22-10 all I had to do was reconfigure vmware server from source.  (as you will have to do with any new kernel you install anyway).

So google for the any-any patch...apply and you are go for vmware server with your new kernel(s)

---

### Post by flyinraptr on 2007-09-06
> **tact said:**
> This is a bit off topic (sorry OP - it will be brief)....

I compiled VMWare Server on my 2.6.22-9 kernel (installed by following the manual process in this thread).  

It gave a few problems but after googling I found some guides that pointed to the need to patch the VMware server source before you compile it.

The patch is called vmware-any-any-updatexxx  (where xxx= the highest number you find for the latest version).   I used "vmware-any-any-update103"

After applying this patch you still get the version mismatch message regarding GCC but thats safely ignored.

With the vmware server source patched with the any-any patch when I again upgraded kernel to 2.6.22-10 all I had to do was reconfigure vmware server from source.  (as you will have to do with any new kernel you install anyway).

So google for the any-any patch...apply and you are go for vmware server with your new kernel(s)

Thanks for the reply .... I had found a couple of Howtos from Googling as well and the patch version I used was "....update109".  As I mentioned when I upgraded the kernel to 2.6.22.10 - the Vmware install worked but because of the other issues I backleveled to 2.6.22.9.  

I think if I could get the right Header files for 2.6.22.9 it will work .... what puzzles me is why uname -r gives me 2.6.22-9-generic but in /usr/src - the directory is 2.6.22-9?

---

### Post by atlfalcons866 on 2007-09-06
is there any difference bewteen a generic kernel and i386?

---

### Post by fjf on 2007-09-07
I need support for my abit uguru3 chip...is there an easy way to get the kernel 2.6.23?.

---

### Post by walkerk on 2007-09-07
> **fjf said:**
> I need support for my abit uguru3 chip...is there an easy way to get the kernel 2.6.23?.

Easy way? No. You'll need to compile 2.6.23 by yourself from kernel.org. If you search this forum you will find a few tutorials on compiling kernels..

---

### Post by lemurian on 2007-09-07
> **walkerk said:**
> Easy way? No. You'll need to compile 2.6.23 by yourself from kernel.org. If you search this forum you will find a few tutorials on compiling kernels..

Right, I don't see 2.6.23 in Launchpad.

However, for people who care about this: 2.6.22-11 has been published.  It might even already be available in the repositories.

I don't know what the changes are.  Anyone knows of a quick and easy way to see the changelog without downloading the darn package???

---

### Post by walkerk on 2007-09-07
> **lemurian said:**
> Right, I don't see 2.6.23 in Launchpad.

However, for people who care about this: 2.6.22-11 has been published.  It might even already be available in the repositories.

I don't know what the changes are.  Anyone knows of a quick and easy way to see the changelog without downloading the darn package???

-11 hasn't hit the repos yet.

---

### Post by overcaffein8d on 2007-09-07
I just ran it on my compaq c500 series. seems to work fine (wireless works, haven't tried wired yet). 

didn't get fixed what i thought would do... the speakers don't mute when you put in headphones.

---

### Post by walkerk on 2007-09-08
> **overcaffein8d said:**
> I just ran it on my compaq c500 series. seems to work fine (wireless works, haven't tried wired yet). 

didn't get fixed what i thought would do... the speakers don't mute when you put in headphones.

Glad it worked :)

---

### Post by tact on 2007-09-08
> **flyinraptr said:**
> I think if I could get the right Header files for 2.6.22.9 it will work .... what puzzles me is why uname -r gives me 2.6.22-9-generic but in /usr/src - the directory is 2.6.22-9?

Not sure if it makes any difference but - were you booted into the 2.6.22-9 kernel when you applied the any-any patch and recompile vmware?

When I do a uname - r I get the same as you (generic kernel).  In /usr/src I have two folders for each kernel.   e.g.   a folder 2.6.22-10 and another 2.6.22-10-generic.  According to conky the version of running kernel is 2.6.22-10-generic.

---

### Post by markp1989 on 2007-09-08
After doing this my computer booted up faster, i dont know why it did, but it cut my boot time from 40sec to 31 sec

But my ATI Remote wonder doesnt work any more. does any one know how i can get it to work? Any help will be appreciated

---

### Post by walkerk on 2007-09-08
I've just upgraded to 2.6.22-11 using the new **kernel.py** included in the OP. :)

---

### Post by Gremlinzzz on 2007-09-08
Thanks just upgrade 2.6.22-11-generic

:guitar:

---

### Post by nowshining on 2007-09-08
[walkerk]("http://ubuntuforums.org/member.php?u=297913") needs to update their signature :)

---

### Post by walkerk on 2007-09-09
> **nowshining said:**
> [walkerk]("http://ubuntuforums.org/member.php?u=297913") needs to update their signature :)

lol.. good call :)

---

### Post by nowshining on 2007-09-09
:) lolz

---

### Post by dippy2323 on 2007-09-09
Just updated to kernel 2.6.22.11-generic.  Python script worked great!  Wireless still doesn't QUITE work (Intel 4965 agn).  For once, it actually acts like it is connecting right after boot (shows great connectivity to my network), but none of the pages will load.  My only guess was the message when running iwconfig:

"Warning: Driver for device wlan0 has been compiled with version 22 of Wireless Extension, while this program supports up to version 20. Some things may be broken..."

Any ideas?  I am new to linux after being annoyed with vista not working...

---

### Post by walkerk on 2007-09-09
> **dippy2323 said:**
> Just updated to kernel 2.6.22.11-generic.  Python script worked great!  Wireless still doesn't QUITE work (Intel 4965 agn).  For once, it actually acts like it is connecting right after boot (shows great connectivity to my network), but none of the pages will load.  My only guess was the message when running iwconfig:

"Warning: Driver for device wlan0 has been compiled with version 22 of Wireless Extension, while this program supports up to version 20. Some things may be broken..."

Any ideas?  I am new to linux after being annoyed with vista not working...

A couple of other users had this issue.. I believe BC7333 and a few others with the same wifi card had similar issues... search back through this thread, perhaps by BC7333's nick...

---

### Post by ResumeMan on 2007-09-09
So I just ran the script (I didn't change to whatever your latest script was, just the one I used a week or two ago).

Now Ubuntu is telling me I have 99 (!) updates, but that only a partial upgrade is possible.

I checked my sources.lst and there is no reference to gutsy in there. But I'm hesitant to run the upgrade in case I end up installing a whole bunch of inappropriate stuff.

Has anyone else encountered this? What's the right approach???

---

### Post by nowshining on 2007-09-09
oh and the initial post needs to be changed 
 
this part under did it hose your system or whatever to the right version number..
 
sudo apt-get remove linux-image-2.6.22-10-generic linux-headers-2.6.22-10-generic linux-headers-2.6.22-10 linux-restricted-modules-2.6.22-10-generic linux-ubuntu-modules-2.6.22-10-generic
 
 
amd ur welcome

---

### Post by lowracer on 2007-09-09
Just upgraded the wife's HP Pavilion dv9410us to kernel 2.6.22-11 using the manual instructions, not the script.  All is well so far...  Got some complaints during the update phase about not being able to reach getautomatix.com, but I ignored these and pressed CTRL-C to abort with no ill effects after it appeared the update was otherwise complete.  Had the video driver issue (system came up in freaky text mode) and the fix for that worked too.  Good job.  Now I will do this on my desktop machine which is about to get a new motherboard that will need the new kernel...
:popcorn:

 edit to add: just upgraded my desktop machine to 2.6.22-11 generic as well, in advance of installing the new motherboard.  Seems to be working fine.  Also needed to do the nvidia driver thing on this one.  Thanks for the writeup.

---

### Post by walkerk on 2007-09-10
> **lowracer said:**
> Just upgraded the wife's HP Pavilion dv9410us to kernel 2.6.22-11 using the manual instructions, not the script.  All is well so far...  Got some complaints during the update phase about not being able to reach getautomatix.com, but I ignored these and pressed CTRL-C to abort with no ill effects after it appeared the update was otherwise complete.  Had the video driver issue (system came up in freaky text mode) and the fix for that worked too.  Good job.  Now I will do this on my desktop machine which is about to get a new motherboard that will need the new kernel...
:popcorn:

 edit to add: just upgraded my desktop machine to 2.6.22-11 generic as well, in advance of installing the new motherboard.  Seems to be working fine.  Also needed to do the nvidia driver thing on this one.  Thanks for the writeup.

The getautomatix.com error has nothing to do with the kernel upgrade. You must have the automatix repositories in your /etc/apt/sources.list and it was unreachable during the apt-get update.. no biggy..

Glad it worked well :)

---

### Post by lowracer on 2007-09-10
> **walkerk said:**
> You must have the automatix repositories in your /etc/apt/sources.list and it was unreachable during the apt-get update.. no biggy..

Glad it worked well :)

Yeah, I figured that might be the case.  The new kernel seems to be working fine.  Bummer though, after a lengthy install, my new motherboard was DOA and a replacement won't arrive until the end of the week...

---

### Post by markoloka on 2007-09-10
This kernel suggested in this topic doesn't boot. Stops at Hid core drivers for usb... On older kernels it will go pass that and they boot.

---

### Post by flyinraptr on 2007-09-10
> **tact said:**
> Not sure if it makes any difference but - were you booted into the 2.6.22-9 kernel when you applied the any-any patch and recompile vmware?

When I do a uname - r I get the same as you (generic kernel).  In /usr/src I have two folders for each kernel.   e.g.   a folder 2.6.22-10 and another 2.6.22-10-generic.  According to conky the version of running kernel is 2.6.22-10-generic.

I tried it both ways - first with 2.6.22-9 - (uname -r = 2.6.22-9-generic) but it fails because it can't find the right header files.  Patch was applied while booted into 2.6.22-9 kernel. 

Because of this - ran the script to upgrade to 2.6.22-10.  Booted into the 2.6.22-10 kernel - re-ran the vmware install ... applied patch and vmware installed and fired up the first time I launched it.  But with the upgrade to the 2.6.22-10 kernel it seemed my orginal nvidia drivers were not working correctly and upgraded to the latest nvidia drivers  using Envy.  Ran into the problem where the machine would freeze when restarting or shutting down - tracked the issue back to the nvidia drivers.  Ended up going back to 2.6.22-9 with the original nvidia drivers to get back to a stable machine.  

Would like to see if I can get Vmware working with 2.6.22-9 kernel because it has been running flawlessly on my pc.  If not - may just wait until nvidia fixes their driver problem.

---

### Post by tact on 2007-09-10
Sorry my experience with vmware server is not deep enough to help you further.  I am sure you have searched the forum for other vmware specific help threads u r more likely to find a vmware guru lurking in them. :)

Keep looking for the answer...  I have had vmware server working on 2.6.22-9-generic, 2.6.22-10-generic, and now 2.6.22-11-generic with no problems.  I need it to work, use it every day in my work.

---

### Post by dippy2323 on 2007-09-10
Thanks for the suggestion walkerk.  I followed your recommendation (post #365 to steam_engenius) of adding gutsy repo, updating, reinstalling the ubuntu and restricted modules.  Internet still didn't work upon reboot, as it didn't for steam_engenius.  

Got wired-radar on computer and tried to make mess of network as BC7333 by fiddling around.  Probably made a mess, but not internet yet.  Anything else worth trying?  Again, I have a 4965 agn on a thinkpad T61, running 2.6.22-11-generic.  Thanks in advance for the help.

---

### Post by flyinraptr on 2007-09-11
> **tact said:**
> Sorry my experience with vmware server is not deep enough to help you further.  I am sure you have searched the forum for other vmware specific help threads u r more likely to find a vmware guru lurking in them. :)

Keep looking for the answer...  I have had vmware server working on 2.6.22-9-generic, 2.6.22-10-generic, and now 2.6.22-11-generic with no problems.  I need it to work, use it every day in my work.

Thanks - I may give 2.6.22.11 a try.  I'm thinking its not a Vmware issue. 

When I installed 2.6.22.10-generic .... the folder linux-headers-2.6.22-10-generic was created iin /usr/src.  

With 2.6.22.9-generic the folder linux-headers-2.6.22-9  was created.  Vmware complains that the header folder does not match the running kernel 2.6.22-9-generic.

---

### Post by cRoW2k on 2007-09-11
After upgrade to -11 sound system stop to work. (Feisty on dv2055ea)

---

### Post by lemurian on 2007-09-11
> **dippy2323 said:**
> Just updated to kernel 2.6.22.11-generic.  Python script worked great!  Wireless still doesn't QUITE work (Intel 4965 agn).  For once, it actually acts like it is connecting right after boot (shows great connectivity to my network), but none of the pages will load.  My only guess was the message when running iwconfig:

"Warning: Driver for device wlan0 has been compiled with version 22 of Wireless Extension, while this program supports up to version 20. Some things may be broken..."

Any ideas?  I am new to linux after being annoyed with vista not working...
What do you use to bring up the wireless interface?  What encryption protocol do you use on your wireless network?  Is your wireless access point broadcasting its SSID?  If it does not broadcast the SSID you will not be able to connect.  (In general (i.e. with other wireless chipsets) it does not matter whether the SSID is broadcasted or not but in the state the driver for the 4965agn is, the SSID MUST be broadcasted.  Talking from experience here...)

I have a 4965agn card, I get the same message you do about version numbers and yet connectivity is fine.

---

### Post by viruzeno on 2007-09-11
Hi, i had an interesting error, where it installed fine, i rebooted into the new kernel, i logged in fine and worked, but i had no menus, i received message boxes saying that my network had logged in, but i had no menus.

i am now back in the old kernel, i think that it may be an issue with my graphics card cause it has been nothing but strife from the start, is there any way that i can remove the new kernel, or do you have any suggestions as too what may be causing it?

thanks

-viruzeno

---

### Post by cRoW2k on 2007-09-11
> **cRoW2k said:**
> After upgrade to -11 sound system stop to work. (Feisty on dv2055ea)

I've read this and now sound r0x: **[HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")**

---

### Post by walkerk on 2007-09-11
> **viruzeno said:**
> Hi, i had an interesting error, where it installed fine, i rebooted into the new kernel, i logged in fine and worked, but i had no menus, i received message boxes saying that my network had logged in, but i had no menus.

i am now back in the old kernel, i think that it may be an issue with my graphics card cause it has been nothing but strife from the start, is there any way that i can remove the new kernel, or do you have any suggestions as too what may be causing it?

thanks

-viruzeno

Not sure which graphics card you have but I linked a few options in the OP.

If you still wish to remove it just to the following in terminal:
```
sudo apt-get remove linux-headers-2.6.22-11 linux-headers-2.6.22-11-generic linux-image-2.6.22-11-generic linux-restricted-modules-2.6.22-11-generic linux-ubuntu-modules-2.6.22-11-generic
```

---

### Post by dippy2323 on 2007-09-11
> **lemurian said:**
> What do you use to bring up the wireless interface?  What encryption protocol do you use on your wireless network?  Is your wireless access point broadcasting its SSID?  If it does not broadcast the SSID you will not be able to connect.  (In general (i.e. with other wireless chipsets) it does not matter whether the SSID is broadcasted or not but in the state the driver for the 4965agn is, the SSID MUST be broadcasted.  Talking from experience here...)

I have a 4965agn card, I get the same message you do about version numbers and yet connectivity is fine.

I have tried using wifi-radar and my network manager to get connected.  Both have shown me connected to my network.  However, when I ran wifi-radar tonight, the terminal in the background is saying:

```
wlan0   Failed to read scan data : Resource temporarily unavailable

```

I use WEP, but I tried taking everything off and running with no encryption and it still doesn't work.  My wireless access point is broadcasting its SSID; I see it when I connect to it.  One other curious fact when using wifi-radar: it says at the bottom that I am connected to the correct SSID, it even gives me an IP address, but there are no networks in the main window.  It doesn't show any wireless networks there, not even the one I am "connected" to, though the network manager can find a few nearby networks as well.  Also, every once in a while, I can get google to load if tried immediately, but after that it cannot load another page, not even the google page again.

---

### Post by ricardoec on 2007-09-11
My XGL session did not work for me. I had to go back.

My setup is a HP nw8440, 2GB mem, ATI x1600 256MB mem, SATA 100GB

I run a sepparate GNOME+XGL session because the ATI binaries do not support CPZ.

Cheers and good luck with Gusty.

---

### Post by kiran_aryan on 2007-09-12
Hi,
 Thanks for the script. I upgraded my kernel to 2.6.22 successfully. However, I am getting Ubuntu Live Update says that there are 4 updates available - linux-headers-2.6.20-16, linux-headers-2.6.20-16-generic, linux-image-2.6.20-16-generic, linux-libc-dev

If I do these 4 updates, isn't it downgrading from 2.6.22 to 2.6.20 again? Is there a way to supress these 4 updates so that the live updater wouldn't ask me to update these 4 packages?

Thank You.

EDIT:: Problem solved. I opened Synaptic and chose "Lock Version" for the 4 packages manually.

---

### Post by walkerk on 2007-09-12
> **kiran_aryan said:**
> Hi,
 Thanks for the script. I upgraded my kernel to 2.6.22 successfully. However, I am getting Ubuntu Live Update says that there are 4 updates available - linux-headers-2.6.20-16, linux-headers-2.6.20-16-generic, linux-image-2.6.20-16-generic, linux-libc-dev

If I do these 4 updates, isn't it downgrading from 2.6.22 to 2.6.20 again? Is there a way to supress these 4 updates so that the live updater wouldn't ask me to update these 4 packages?

Thank You.

EDIT:: Problem solved. I opened Synaptic and chose "Lock Version" for the 4 packages manually.

Go into Synaptic and lock the following packages:
> linux-headers-2.6.22-11
linux-headers-2.6.22-11-generic
linux-image-2.6.22-11-generic
linux-restricted-modules-2.6.22-11-generic
linux-ubuntu-modules-2.6.22-11-generic


This should do the trick. Did you delete 2.6.20-16? Or did you only have 2.6.20-15? I had both -15 and -16 before I installed 2.6.22 and I don't get this update issues..

---

### Post by ptn107 on 2007-09-14
Successfully upgraded to kernel 2.6.22-11.  I followed the manual directions so I understood what was going on.  This was much easier than compiling a custom kernel as I have been doing previously (though I plan to continue to compile test kernels).  I've also removed 2.6.20-15 through synaptic and have 2.6.20-16 around now just in case.  Nice job with the instructions.  I thought the newer kernel was going to fix my integrated Broadcom [bcm4318] wireless card for my laptop, but I guess I heard wrong.   :(

---

### Post by wnelson on 2007-09-15
Found the following for the 4318:


[http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card](http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card)

---

### Post by jobbesat on 2007-09-15
Upgraded successfully manually, no issues for now.
I have a AMD Xp athlon 3200, graphic card ATI Radeon x600, hd ide 250 Gb, ram 1 Gb.

---

### Post by el mariachi on 2007-09-15
Has the script been updated to include server? Or does it still needs to be done manually? thanks

---

### Post by walkerk on 2007-09-15
> **el mariachi said:**
> Has the script been updated to include server? Or does it still needs to be done manually? thanks

Just added the server meta packages.. though you'll need to manually change it..

1. Download the new kernel.py
2. Open it with gedit (or your favorite text editor)
3. Comment out the packages with the normal linux meta packages.
4. Un-comment the other one with the server packages.. 
5. Save it, make it executable, and run it.  :)

---

### Post by jobbesat on 2007-09-15
So maybe it would be better to attach 2 files, one with server and one without, so that every users, newbies included, can have the chance to download the file they want.
What do you think?

---

### Post by walkerk on 2007-09-15
> **jobbesat said:**
> So maybe it would be better to attach 2 files, one with server and one without, so that every users, newbies included, can have the chance to download the file they want.
What do you think?

I haven't done this because the *need* is slim. Surely new users aren't looking to upgrade server kernels.. 

Let me know if I'm wrong..

---

### Post by master_kernel on 2007-09-15
Very interesting method! I did not test this, but your script looks pretty secure! Great job with this!

master_kernel

---

### Post by compubahn on 2007-09-15
Thanks for the script. Works like a charm.

I had tried 7.10 on my z61t but the apps kept crashing so I went back to 7.04. My wireless & sound work better under the new kernel without the apps crashing like in 7.10.

I did have a mysterious unsolicited reboot while adjusting the lcd brightness. Everything else is working fine, though. Thunderbird 2.0 even stopped crashing. That alone is worth the upgrade.

This is my first roll in the hay with linux since redhat 5, which didn't agree with my laptop back in the day. Gotta say I am enjoying Ubuntu, even if you have to roll up your sleeves and tinker under the hood to get some things working.

---

### Post by overcaffein8d on 2007-09-15
> **walkerk said:**
> 

[SIZE="3"]**Ok.. Did it hose your box? Too easy.**[/SIZE]

Reboot your computer and at Grub press esc to boot into your last kernel. (probably 2.6.20-16-*)

Remove the installed kernel and then upgrade. 
```
sudo apt-get remove linux-image-2.6.22-10-generic linux-headers-2.6.22-10-generic linux-headers-2.6.22-10 linux-restricted-modules-2.6.22-10-generic linux-ubuntu-modules-2.6.22-10-generic
```
```
sudo apt-get upgrade
```


You ought to change that code to 2.6.22-11.

---

### Post by el mariachi on 2007-09-15
The script didn't do anything thing in my machine.. absolutely no packages were modified (server install and I did the necessary commenting and uncommenting). I ended up doing it manually.

---

### Post by walkerk on 2007-09-16
> **el mariachi said:**
> The script didn't do anything thing in my machine.. absolutely no packages were modified (server install and I did the necessary commenting and uncommenting). I ended up doing it manually.

sorry about that.. I guess the meta packages for server don't upgrade.. i had it by specific package at first but then thought to call the meta-packages instead so that it could be run again for updates..

---

### Post by walkerk on 2007-09-16
> **overcaffein8d said:**
> You ought to change that code to 2.6.22-11.

Good call.

---

### Post by sp0onman on 2007-09-16
i followed the guide and everything worked, except when i use the kernel running xgl with compiz the screen goes all fudged, sort of fuzzy and i cant read anything, works perfect through gnome though. oh btw im running the fglrx 8.40 drivers

---

### Post by ST.x on 2007-09-16
> **lemurian said:**
> Envy packages the closed source nvidia driver neatly.  That's the advantage over just grabbing the driver from nvidia's site and installing yourself.

As far as upgrading the kernel, here's the "hassle" you have to go through if you use envy:

1. Upgrade the kernel.
2. Reboot.
3. Wait until Ubuntu detects that X cannot be started.  Reply no to the question about diagnosing the problem and acknowledge the following dialog which says that you will need to restart gdm manually.
4. Once at the console, log in.
5. Execute sudo envy -t
6. Select option 1.
[Envy will do its work.  May take about one minute.]
7. Envy will want you to reboot but there's really no need for that.  Just exit it.
8. sudo /etc/init.d/gdm restart

You're done.  There's nothing in there which is particularly esoteric.  It looks like a lot of steps but it's really pretty trivial.  Takes me 5 minutes max.  That's a "hassle" I can easily live with if it means that I can use the latest nVidia drivers and that the work of packaging them will be done by an automated system.  All other solutions either:

1. Just leave all kinds of files floating everywhere because nVidia did not package their driver for Ubuntu.

2. Or require *me* to do the work that Envy does for me.

3. Or rely on drivers that do not work with my graphic card (e.g. the "nv" drivers) or that do not take full advantage of the capabilities of my card.

I'll take Envy any day, thank you.

First I installed using the script, and got the error with X crashing. So I did what you said there(using envy), and now I can boot into 2.6.22-11-generic. But I realised i didn't re-enable the gutsy repos as it says on the first page. Compiz Fusion is working as normal though, so is this fine?

edit: The script also wanted to remove  3 compiz fusion related packages- something about them being added but not being needed (8mb) worth, but  I chose not to remove them just in case. hmm? 

thanks :)

---

### Post by nowshining on 2007-09-16
with my nvidia card & the nvidia drivers from the main website- I have no real MAJOR probs after a kernel update - as they are minor and everything works rather flawlessly - I do it anyway to make sure. :)

---

### Post by jobbesat on 2007-09-16
> **walkerk said:**
> I haven't done this because the *need* is slim. Surely new users aren't looking to upgrade server kernels.. 

Let me know if I'm wrong..
No at all, I was wrong because I thought you attached the version with servers, sorry!

---

### Post by master_kernel on 2007-09-16
walkerk, please visit [http://ubuntuforums.org/showthread.php?p=3376011](http://ubuntuforums.org/showthread.php?p=3376011) and add your program to the list of the best of the Ubuntu community.

---

### Post by master_kernel on 2007-09-16
> **sp0onman said:**
> i followed the guide and everything worked, except when i use the kernel running xgl with compiz the screen goes all fudged, sort of fuzzy and i cant read anything, works perfect through gnome though. oh btw im running the fglrx 8.40 drivers

You have to reinstall the fglrx drivers for that kernel. Visit  [http://ubuntuforums.org/showthread.php?p=3376011](http://ubuntuforums.org/showthread.php?p=3376011) for a script that automatically downloads and installs the fglrx driver.

---

### Post by lemurian on 2007-09-17
> **ST.x said:**
> First I installed using the script, and got the error with X crashing. So I did what you said there(using envy), and now I can boot into 2.6.22-11-generic. But I realised i didn't re-enable the gutsy repos as it says on the first page. Compiz Fusion is working as normal though, so is this fine?

Huh... **re-enable** the gutsy repos???  You are not supposed to reenable them.  The gutsy repos must be enabled **only while** you are doing the kernel upgrade.  After that, they should remain disabled.

> **ST.x said:**
> edit: The script also wanted to remove  3 compiz fusion related packages- something about them being added but not being needed (8mb) worth, but  I chose not to remove them just in case. hmm? 

thanks :)

I've never encountered that situation.  Make sure you do everything as per the instructions walkerk gave.

---

### Post by master_kernel on 2007-09-17
> **lemurian said:**
> I've never encountered that situation.  Make sure you do everything as per the instructions walkerk gave.

That situation sounds like "sudo apt-get autoremove"
It removes packages that are not needed anymore.

---

### Post by ST.x on 2007-09-17
> **lemurian said:**
> Huh... **re-enable** the gutsy repos???  You are not supposed to reenable them.  The gutsy repos must be enabled **only while** you are doing the kernel upgrade.  After that, they should remain disabled.



I've never encountered that situation.  Make sure you do everything as per the instructions walkerk gave.

Oh okay thats good then. I used the script to do this btw. I only thought I had to reenable them from the link in the first post about: ['**[COLOR=YellowGreen]Having issues with your nVidia video cards?'[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=3246585&postcount=342")

But I used envy to do the driver reinstall without entering X so obviously I don't need to enable the gutsy repos again right?

---

### Post by ST.x on 2007-09-17
> **master_kernel said:**
> That situation sounds like "sudo apt-get autoremove"
It removes packages that are not needed anymore.

Well, I didn't let it remove those three packages related to compiz fusion, and CF is still working afterwards so I guess it should be alright, but why did it think they weren't needed?

---

### Post by nowshining on 2007-09-17
there is an update to the .11 kernel headers, etc.. :) so you guys need to redownload the updated headers, etc.. :)

---

### Post by wylie348 on 2007-09-18
Appears to work (18 Sep 2007) on T4210 Fujitsu Lifebook running Feisty, using your script.

For some reason my screen brightness function keys no longer work, while other function keys (like audio volume) work fine?

Thanks!

---

### Post by Captain Köppi on 2007-09-18
Updated my Feisty installation 4 hours ago following the manual procedure (From Kernel 2.6.20-16-generic to 2.6.22-11-generic)

No problems so far, some things changed: 

- booting seems to be much faster now
- the problem with usb_suspend is gone, now all my usb-devices work again, including my canon lide 25 :guitar:

my machine: 
- aopen i945GMm-HL motherboard (intel i945 chipset with GMA 950 integrated graphics core)
- Marvell Yukon 88E8001/8003/8010 PCI Gigabit Ethernet Onboard
- Realtek ALC880 High Definition Audio Onboard
- 2x 1024 MB MDT DDR2 667MHz RAM
- Core 2 Duo (Merom) 1,66 GHz (T5500)

To make it short: machines with intels ICH 7 should work without any problems. :lolflag:


EDIT: I forgot to say THANK YOU! Updating Feisty with a newer Kernel which is even provided by Canonical is a very good idea, and you provided us with a very nice How-To.

---

### Post by walkerk on 2007-09-19
Glad its working well for you guys.. :)

---

### Post by gkak on 2007-09-19
great nfo
worked fine on my pc
running ubuntu feisty
pc details:
fujitsu siemens laptop
cpu pentium 4 3,2
1024 ram
120 g hard drive
ati mobility radeon graphics card 64mb
dual boot linux/windows xp

---

### Post by mb0108 on 2007-09-20
Hi, 

I also did the Upgrade from Feisty doing the manual process. Everything works fine and I have now LAN on my DELL XPS M1330 :-) Now I wanted to install Oracle  10gR2 and installed all the required libraries with 

"sudo apt-get install gcc libaio1 lesstif2 lesstif2-dev make libc6 libc6-i386 libc6-dev-i386 libstdc++5 lib32stdc++6 lib32z1 ia32-libs"

from Gutsy. 

Now the linking process of Oracle has the problem: 

INFO: gcc -m32 -o ctxhx -L/opt/oracle/10g/product/10.2.0/db/ctx//lib32/ -L/opt/oracle/10g/product/10.2.0/db/lib32/ -L/opt/oracle/10g/product/10.2.0/db/lib32/stubs/  /opt/oracle/10g/product/10.2.0/db/ctx/lib/ctxhx.o -L/opt/oracle/10g/product/10.2.0/db/ctx/lib/ -ldl -lm -lctxhx -Wl,-rpath,/opt/oracle/10g/product/10.2.0/db/ctx/lib -lsnls10 -lnls10  -lcore10 -lsnls10 -lnls10 -lcore10 -lsnls10 -lnls10 -lxml10 -lcore10 -lunls10 -lsnls10 -lnls10 -lcore10 -lnls10  `cat /opt/oracle/10g/product/10.2.0/db/lib/sysliblist` 

INFO: /
INFO: usr
INFO: /
INFO: bin
INFO: /
INFO: ld
INFO: :
INFO:  
INFO: skipping
INFO:  incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libgcc.a when searching for -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc

INFO: collect2: ld gab 1 als Ende-Status zur??ck

INFO: make: 
INFO: *** [ctxhx] Fehler 1
INFO: 

Can anyone help me ?!? 

Thanks a lot, 
Michael

---

### Post by nowshining on 2007-09-20
everyone will once AGAIN need to RE_UPDATE - New headers and such were Updated and available for download - again RE-UPDATE if you haven't done so.

---

### Post by nowshining on 2007-09-20
mb0108 did you update more then the kernel - if you updated everything - go into the synaptic package manager nad make sure all is updated - sometimes the update manager wil ls all is updated when they are not. :) in other words if you updated everything in the Update manager - and rebooted - re-run an update check and keep doing that until all is def. updated - then u've not got gutsy.

---

### Post by Peedjay on 2007-09-20
Thanks for the script! Works perfectly. Got even my wireless finally working with it (which is btw  a Intel 4965AGN. No more messing around with drivers!) :-D:-D

My specs
ASUS F3SV, Core2Duo 1.8GHz, HD 160GB, dualboot Vista/Feisty, 2x1GB RAM, NVidia GF 8600 gs 256 MB, Intel Wireless WiFi Link 4965AGN

---

### Post by walkerk on 2007-09-21
> **Peedjay said:**
> Thanks for the script! Works perfectly. Got even my wireless finally working with it (which is btw  a Intel 4965AGN. No more messing around with drivers!) :-D:-D

My specs
ASUS F3SV, Core2Duo 1.8GHz, HD 160GB, dualboot Vista/Feisty, 2x1GB RAM, NVidia GF 8600 gs 256 MB, Intel Wireless WiFi Link 4965AGN

Good to hear :)

---

### Post by Pakini on 2007-09-21
Upgrade to the latest kernel worked like a charm, aside from the new NVidia drivers I had to install.

Now my DWL-G122 c1 wireless usb adapter also works without special drivers!

FYI:
running Feisty on an AMD Athlon64 3200+

---

### Post by emmir on 2007-09-21
> **Peedjay said:**
> Thanks for the script! Works perfectly. Got even my wireless finally working with it (which is btw  a Intel 4965AGN. No more messing around with drivers!) :-D:-D


Which is not my case (Broadcom 4318) any Ideas?

---

### Post by walkerk on 2007-09-21
2.6.22-12 is out. :)

---

### Post by master_kernel on 2007-09-21
Interesting network test, great script :)
Isn't python fun? Here's the script I wrote with it, took me a while -- [http://kcheck.sourceforge.net/pool/latest-stable/kernelcheck-stage2](http://kcheck.sourceforge.net/pool/latest-stable/kernelcheck-stage2)

---

### Post by walkerk on 2007-09-21
> **master_kernel said:**
> Interesting network test, great script :)
Isn't python fun? Here's the script I wrote with it, took me a while -- [http://kcheck.sourceforge.net/pool/latest-stable/kernelcheck-stage2](http://kcheck.sourceforge.net/pool/latest-stable/kernelcheck-stage2)

lol... very *simple* network test :P

your script looks very nice... good work :)

yea, im enjoying python... though i've only just dipped my foot into python...

---

### Post by atlfalcons866 on 2007-09-22
does this make my computer weaker to security exploits?

---

### Post by walkerk on 2007-09-22
> **atlfalcons866 said:**
> does this make my computer weaker to security exploits?

not at all. this will install kernel ver 2.6.22 with ubuntu developer security patches (currently at -12)...

---

### Post by rada on 2007-09-22
> **arizonagroovejet said:**
> So anyone done this who is using the nvidia restricted driver?
I<snip>
A bunch of other packages would be updated as a result of nvidia-glx-new for some reason. Anyone actually done this? If so what happened?

I have an Asus mobo and would like 2.6.22 to give me hardware monitoring. lm-sensors doesn't support the sensors on the mobo without 2.6.21 or above.

Yes, me too. EVGA 680i mobo, want kernel >= 2.6.21 for lm-sensors, but don't want Gutsy yet. Restricted-Drivers Feisy nvidia driver didn't work for me since I am on x86_64 with geForce 8800GTS video card, needed Envy for it to work properly.  

**Edit: Manual upgrade instructions + envy after booting into the new kernel worked smoothly and easily. **  Thank you !!

One small hitch with grub due to my having dual SATA drives with different ubuntu versions on them?
[LIST]
[*]first time ran script chose "no do not reboot now" in kernel-1.py
[*]killed some stuff and rebooted
[*]no new kernel option in grub menu at boot
[*]thought well, should have let kernel.py reboot so ran it again and let it reboot the system
[*]still no grub entry for 2.6.22
[*]sudo vi /boot/grub/menu.lst
[*]!! 2.6.22 listing is right there first entry
[*]tried various edits to menu.lst, rebooting without new entry
[*]ran update-grub
[*]still no 2.6.22 entry
[*]duh - finally looked in /boot/ itself and no vmlinuz-2.6.22-12
[*]followed manual instructions to upgrage kernel
[*]checked that 2.6.22 stuff is in /boot/
[*]reboot
[/LIST]
same thing it's in menu.lst but doesn't show up as an option
     $ uname -r
     $ 2.6.20-16-generic

**Edit:**   Okay... hmm gotta check my partitions  
          recovery mode groot=(hd0,1)    /boot/ has no new kernel
          default boot     groot=(hd0,2)   /boot/ has new kernel

yah... got confused with feisty32 install I'd forgotten about, two weirdly partitioned SATA drives. I'm used [this GRUB overview]("http://users.bigpond.net.au/hermanzone/p15.htm") to sort it out.

---

### Post by nowshining on 2007-09-24
i use the restricted driver - DO NOT REMOVE anything - i did and got meself in some hot water - it needs the glx junk and xorg drivers. :) and linux-commons is needed for the restricted manager - so it's best to leave them.


Oh and Before the BETA there is going to be - might more after this post a new linux header - image, etc.. everyday - so do the gutsy update kernel updates everyday.

---

### Post by maaylix on 2007-09-25
I gave a quick skim through the topic, so I might have missed a solution to my problem.

The tutorial did wonders for, me, I was finally able to run both of my sata drives in ubuntu, many thanks!

Thing is, auto update keeps reminding me to downgrade to Feity's kernel... any way to remove those updates, so I don't have a constant update icon reminder on my taskbar?

---

### Post by DJ_Peng on 2007-09-25
I just ran the upgrade via the script. Before I report on what ahppened, here's my hardware details. I have a custom built box with:

    * Intel D845GLVA mobo with onboard networking
    * Intel Celeron 2.20GHz processor
    * 766MB RAM
    * Nvidia GeForce2 MX/PCI graphics card
    * 1.0-9639 Video drivers installed via Envy
    * Ubuntu 7.06 Feisty Fawn

The starting kernel is 2.6.20-16-generic.

I ran the update script with no problems. I then used Envy to remove the Nvidia driver, then manually added the Gutsy repo and added the Nvidia driver with Envy. Once that was done I manually removed the Gutsy repo, crossed my fingers, and rebooted.

The xserver failed, but I ran Envy from the prompt (text version) and reinstalled the Nvidia driver, rebooting when it was done.

Once I rebooted all was well, and I'm now running the 2.6.22-generic kernel. I did get a notice of 5 KDE updates being available (I run a few KDE apps, including Anorak), including the kdedesktop (from 4:3.5.6-0ubuntu20.2 to 4:3.5.6-0ubbuntu20.4) for some odd reason, but details aren't available yet so I'll hold off on accepting them for now unless someone lets me know they're ok to take.

Boot up seemed a little quicker, but I was getting another cup of coffee and forgot that's the first place I'd see a speed increase so I'll have to post again later to say if I'm noticing a difference. An excellect script, definitely deserving to be in the Best of Ubuntu list. Getting this done makes me even more eager to grabbing the Gutsy upgrade when it hits beta, hopefully on Thursday. :KS

One other note: I hadn't known to set my /home up on a different partition when I first made the switch to Ubuntu and when I was moving it over the weekend I ended up borking things and had to reinstall Feisty so the install is pretty cleaned up from where it was late last week, so any speed improvements from the new kernel may actually not be as noticeable, or at least I may not realize the speed improvements are from the kernel and not just cleaning things up.

---

### Post by ST.x on 2007-09-26
> **maaylix said:**
>  
Thing is, auto update keeps reminding me to downgrade to Feity's kernel... any way to remove those updates, so I don't have a constant update icon reminder on my taskbar?

Yea same here, it wants to get 2 headers, an image , and a libc-dev.

---

### Post by SZF2001 on 2007-09-26
Holy crap I'm not reading through the whole topic, it's huge.

So I'll ask:

Should I remove my restricted nVIDIA driver before rebooting into the new kernel?

---

### Post by DJ_Peng on 2007-09-26
Way back when I saw someone who said they had no driver issues with the new kernel, but I always need to update my driver with a new kernel. I'd say try it without changing your driver, but have Envy handy to run in text mode (sudo envy -t) just in case you need it. Looking back I probably would have done that myself, or maybe just get tyhe new driver in Envy with the Feisty repo before rebooting. Either way, Envy saved my bacon, not to mention some time and frustration. Some people hate it, but I love it.

---

### Post by SZF2001 on 2007-09-26
Well, I tried the script with my driver on. It killed X, so pressed ESC and switched to the old kernel and tried again without the driver installed. Worked out this time, but now I'm afraid to install the driver again because I don't want the White Screen of Death again or anything like that (because I have no idea how to run Envy and I don't know if another kernel switch would fix it)...

What to do...

EDIT: Blargh, that didn't work out. Luckily I could just use the old kernel again, but seriously, I could *really* use this restricted driver right about now. Should I try those other drivers mentioned on the OP? I don't think I'd need legacy, but the computer is a Dell Dimension 4300 and I'm not sure how old the card itself is...

I could just keep doing this GRUB ESC stuff but it's getting annoying. :p

---

### Post by maaylix on 2007-09-26
> **ST.x said:**
> Yea same here, it wants to get 2 headers, an image , and a libc-dev.

Hmm here it only wants two headers and an image

---

### Post by Jasper84 on 2007-09-26
Worked well for me :) Thanks.
Hopefully helps against straight-to-black hard crashes i have been having.

Edit: The kernel was not the problem, i think i am having some hardware problem (with the harddisk or or maybe how it connects to the motherboard or something; livecds did work.) Anyway it does not crash much anymore after disabling swap.

---

### Post by SZF2001 on 2007-09-26
Hey guys, that poster talking about Envy (I can't seem to find it, I'm a little sleepy now) did wonders for me - I think it should be added to the OP for people with the same problems with their nVIDIA cards... I mean, switching to the 'new' or 'legacy' didn't seem to do much for me, but the Envy script built the driver by it's source and all kinds of neat things happened for me.

USE ENVY WOOOT

---

### Post by DJ_Peng on 2007-09-26
Sorry, I should have included a link when I was writing my post. I was actually writing it in Gmail so I could hve it handy to post when I was ready to post it. Envy's great for Nvidia cards, and it should work for ATI cards as well.

[Envy]("http://albertomilone.com/wordpress/?p=107")

---

### Post by walkerk on 2007-09-26
> **DJ_Peng said:**
> I just ran the upgrade via the script. Before I report on what ahppened, here's my hardware details. I have a custom built box with:

    * Intel D845GLVA mobo with onboard networking
    * Intel Celeron 2.20GHz processor
    * 766MB RAM
    * Nvidia GeForce2 MX/PCI graphics card
    * 1.0-9639 Video drivers installed via Envy
    * Ubuntu 7.06 Feisty Fawn

The starting kernel is 2.6.20-16-generic.

I ran the update script with no problems. I then used Envy to remove the Nvidia driver, then manually added the Gutsy repo and added the Nvidia driver with Envy. Once that was done I manually removed the Gutsy repo, crossed my fingers, and rebooted.

The xserver failed, but I ran Envy from the prompt (text version) and reinstalled the Nvidia driver, rebooting when it was done.

Once I rebooted all was well, and I'm now running the 2.6.22-generic kernel. I did get a notice of 5 KDE updates being available (I run a few KDE apps, including Anorak), including the kdedesktop (from 4:3.5.6-0ubuntu20.2 to 4:3.5.6-0ubbuntu20.4) for some odd reason, but details aren't available yet so I'll hold off on accepting them for now unless someone lets me know they're ok to take.

Boot up seemed a little quicker, but I was getting another cup of coffee and forgot that's the first place I'd see a speed increase so I'll have to post again later to say if I'm noticing a difference. An excellect script, definitely deserving to be in the Best of Ubuntu list. Getting this done makes me even more eager to grabbing the Gutsy upgrade when it hits beta, hopefully on Thursday. :KS

One other note: I hadn't known to set my /home up on a different partition when I first made the switch to Ubuntu and when I was moving it over the weekend I ended up borking things and had to reinstall Feisty so the install is pretty cleaned up from where it was late last week, so any speed improvements from the new kernel may actually not be as noticeable, or at least I may not realize the speed improvements are from the kernel and not just cleaning things up.

> **DJ_Peng said:**
> Way back when I saw someone who said they had no driver issues with the new kernel, but I always need to update my driver with a new kernel. I'd say try it without changing your driver, but have Envy handy to run in text mode (sudo envy -t) just in case you need it. Looking back I probably would have done that myself, or maybe just get tyhe new driver in Envy with the Feisty repo before rebooting. Either way, Envy saved my bacon, not to mention some time and frustration. Some people hate it, but I love it.

> **DJ_Peng said:**
> Sorry, I should have included a link when I was writing my post. I was actually writing it in Gmail so I could hve it handy to post when I was ready to post it. Envy's great for Nvidia cards, and it should work for ATI cards as well.

[Envy]("http://albertomilone.com/wordpress/?p=107")

**Use Envy to install nVidia drivers. **Linking this on the OP. :)

---

### Post by mazor on 2007-10-02
I just completed the the kernel upgrade the second method called the manual way. Worked like a dream. Just had a minor glitch whereby I had to change setting in evms.conf as it could not find some device, and kept prompting, slowing down the whole notebook.

Yesterday I tried updated to the full beta Gutsy, which resulted in total chaos. Intel GMA not supported, no sound for toshiba, etc etc. Lucky I have imaged my drive prior so restored back to feisty.

Still testing this new update, but already I find my wireless signal reads double! with the possibility of less random disconnects. Previously in both Edgy and Feisty I have been enduring these wireless problems.

Mazor

---

### Post by corncob on 2007-10-02
I've been using Feisty Fawn for at least a couple months with kernel 2.6.20-16-generic.  I had noticed that there was also a 2.6.20-15-generic on the boot menu and I finally tried it.  As far as I could see it was the same thing.  However, when I went back to -16 I found that the Xserver would no longer start -- saying something about needing to be configured -- and then ending me up at the command prompt.  This same thing happened on two computers.
I followed WalkerK's instructions on upgrading the kernel.  Everything seemed to go smoothly and Kernel 2.6.22-12-generic appeared at the top of the boot menu.  However, booting from it led to the same results as -16  -- no X.  2.6.20-15 is still working so I'm not shut down but I am wondering whats going on.

---

### Post by DJ_Peng on 2007-10-02
It was probably that the display section needs to be updating. Get Envy, install it (even from the command line), and run it in the text version. That should get you back in business with a minimum of hassle.

---

### Post by Gremlinzzz on 2007-10-02
Just changed my system to xubuntu . .its a damn good system to tweak anyways the kernel upgrade works great.:guitar:

---

### Post by Kyran on 2007-10-05
> **corncob said:**
> I've been using Feisty Fawn for at least a couple months with kernel 2.6.20-16-generic.  I had noticed that there was also a 2.6.20-15-generic on the boot menu and I finally tried it.  As far as I could see it was the same thing.  However, when I went back to -16 I found that the Xserver would no longer start -- saying something about needing to be configured -- and then ending me up at the command prompt.  This same thing happened on two computers.
I followed WalkerK's instructions on upgrading the kernel.  Everything seemed to go smoothly and Kernel 2.6.22-12-generic appeared at the top of the boot menu.  However, booting from it led to the same results as -16  -- no X.  2.6.20-15 is still working so I'm not shut down but I am wondering whats going on.

Probably the graphic driver not matching the kernel, look on the first page for the solution.

---

### Post by maaylix on 2007-10-06
Well, for those that are having the annoying downgrade notification after installing gibon's kernel. I solved this problem here by removing completely the packages Ubuntu wanted to downgrade. 

I searched the packages Ubuntu wanted to downgrade with Synaptic, selected them for complete removal and now I'm only getting relevant updated notifications =)

---

### Post by corncob on 2007-10-06
> **Kyran said:**
> Probably the graphic driver not matching the kernel, look on the first page for the solution.

I'm sure you're right.  This seems to happen when I install the restricted nvidia driver which I seem to need to run duel monitors with Twinview.

---

### Post by mazor on 2007-10-07
hmm, looks like my wifi is still buggy. Problems are back, and it is disconnecting again :(

---

### Post by DJ_Peng on 2007-10-07
I spent several hours getting my video back after I took the *.13 kernel. I ended up ripping the new kernel out of my system and I was finally able to get video working again in the *.12 kernel. I don't even want to *try* the *.13 kernel and it's updated Nvidia drivers again since it borked my X so badly.

---

### Post by walkerk on 2007-10-08
Yea, it seems -13 was released a bit to quickly.. There seems to be another kernel update today.. 2.6.22-13.19 (bug fixes)

---

### Post by DJ_Peng on 2007-10-08
Awesome. I'll have to snag it later. My four year old NEC flat panel started trying to die yesterday, and while it was fixable my tech said it's better just to replace it so that's what I did. Now I have two days of stuff to catch up on. :(

---

### Post by walkerk on 2007-10-13
2.6.22-14 has been released...

---

### Post by Lean 946 on 2007-10-16
Does it work on another distros like Debian or Dream Linux??
If it works, please tell me how to install the new kernel.

Thanks, Lean

---

### Post by corncob on 2007-10-16
> **Lean 946 said:**
> Does it work on another distros like Debian or Dream Linux??
If it works, please tell me how to install the new kernel.

Thanks, Lean

Walkerk's kernel.py script from the first post in this thread?  It worked on Linux Mint.

---

### Post by walkerk on 2007-10-17
> **Lean 946 said:**
> Does it work on another distros like Debian or Dream Linux??
If it works, please tell me how to install the new kernel.

Thanks, Lean

> **corncob said:**
> Walkerk's kernel.py script from the first post in this thread?  It worked on Linux Mint.

This method uses Ubuntu repositories to download the kernel packages. It won't work with Dream Linux and I doubt it would work with Debian.

The reason it works with Linux Mint is because LM is based on Ubuntu...

---

### Post by Lean 946 on 2007-10-19
Thanks walkerk, i'll try if i can use the methods on the post or on another forum.

Thanks for your soupport, Lean

---

### Post by Curi0 on 2007-10-26
Now that I have the Gutsy Gibbon Kernel, should I be using the Gutsy repositories instead of Edgy?

---

### Post by DJ_Peng on 2007-10-26
Did you just upgrade your kernel or did you do the full upgrade to Gutsy? If you just have the kernel you should continue using the Feisty repos, otherwise you could bork your computer.

---

### Post by sinaen on 2007-10-26
> **maaylix said:**
> I gave a quick skim through the topic, so I might have missed a solution to my problem.

The tutorial did wonders for, me, I was finally able to run both of my sata drives in ubuntu, many thanks!

Thing is, auto update keeps reminding me to downgrade to Feity's kernel... any way to remove those updates, so I don't have a constant update icon reminder on my taskbar?

How did you do it?
i have tried to upgrade my kernel now for centuries. it still boots 2.6.20.16-server edition. 
even thou i tried to remove som kernels reinstall them and such. but still when i choose them in reboot-grub menu grub says file not found. but i know they are there.... 
even now im looking at your link you followed to sort it out.

vmlinuz and vmlinuz-old points to the 2.6.22-14 kernel...

dont understand that much what i need to do with grub to make it work?
but it seems that maybe a reinstallation of grub should do it?

---

### Post by Curi0 on 2007-10-26
I appreciate everything you've done to teach me how to upgrade my kernel from Edgy to Gutsy!

Thank You

---

### Post by CodeWarMonkey on 2007-10-31
I was using Kubuntu 7.04 and tried your Python script. Everything seemed to be working until I rebooted. When it rebooted, the Kubuntu loading screen showed up fine. Then the desktop showed up briefly from when I rebooted with the top half of the screen garbled and bottom half looking normal. The Kubuntu loading logo shows briefly and then the screen acts like a over-sized console where commands don't execute.

I tried your steps for a "hosed" box, but that didn't help. I used grub to get into recovery mode, remove the 22-14 packages and ran the sudo apt-get upgrade command. This gives the message that there is nothing to upgrade. I am not sure what is wrong, but it appears my KDE is messed up and I am not sure how to fix this.

---

### Post by walkerk on 2007-11-02
> **CodeWarMonkey said:**
> I was using Kubuntu 7.04 and tried your Python script. Everything seemed to be working until I rebooted. When it rebooted, the Kubuntu loading screen showed up fine. Then the desktop showed up briefly from when I rebooted with the top half of the screen garbled and bottom half looking normal. The Kubuntu loading logo shows briefly and then the screen acts like a over-sized console where commands don't execute.

I tried your steps for a "hosed" box, but that didn't help. I used grub to get into recovery mode, remove the 22-14 packages and ran the sudo apt-get upgrade command. This gives the message that there is nothing to upgrade. I am not sure what is wrong, but it appears my KDE is messed up and I am not sure how to fix this.

Sorry for the delayed response but I was working out of town this week. What kind of video card do you have?

---

### Post by tommyp on 2007-11-14
Has anyone else had an issue with NTP not working after the upgrade?  I  can no longer sync to internet time servers.  

If I go into the time GUI and select internet servers, I get an error that says "NTP support is not installed", but when I look in synaptic, the all of the ntp files are installed.  (I tried installing NTP- server, but it doesn't seem to exist).

---

### Post by walkerk on 2007-11-14
> **tommyp said:**
> Has anyone else had an issue with NTP not working after the upgrade?  I  can no longer sync to internet time servers.  

If I go into the time GUI and select internet servers, I get an error that says "NTP support is not installed", but when I look in synaptic, the all of the ntp files are installed.  (I tried installing NTP- server, but it doesn't seem to exist).

I do not use Feisty anymore so I cannot recreate the issue but I don't think the kernel would affect the time protocol..

Try re-installing all of the NTP packages through Synaptic... This may or may not fix the problem...

Sorry I can't help more.

---

### Post by tommyp on 2007-11-14
Thanks.  I tried reinstalling through synaptic, but it didn't seem to fix the problem.  I might update my repositories and try to reinstall nps.  I guess I should also boot the old feisty kernel and see if the problem goes away.  I'll let you know what I find.

---

### Post by walkerk on 2007-11-14
> **tommyp said:**
> Thanks.  I tried reinstalling through synaptic, but it didn't seem to fix the problem.  I might update my repositories and try to reinstall nps.  I guess I should also boot the old feisty kernel and see if the problem goes away.  I'll let you know what I find.

Please do. I'm interested to see whether booting into the old kernel fixes the problem...

---

### Post by nlantz on 2007-11-15
wheres the download for the kernel ??

---

### Post by walkerk on 2007-11-17
> **nlantz said:**
> wheres the download for the kernel ??

i think you're asking where the kernel.py script is that will download and install the kernel... it's at the end of the original post as an attachment..

---

### Post by tommyp on 2007-11-20
I started by booting the old kernel, but it crashed my X, so I just decided to wimp out and go ahead with a full upgrade to Gutsy.  That solved the NTP issue! (It also created some others, but that's besides the point!:))

---

### Post by lemurian on 2007-12-17
walkerk, I see you've edited the first post to announce your intention to get a procedure in place to install a Hardy kernel.  Any progress?  (I searched and found no thread about it.  If I missed something, please correct me.)

I'm thinking I might want to move up to a Hardy kernel because of issues I've been having with kvm preventing my laptop from suspending properly.  Based on what I've read on the kvm-devel list, I think that problem required a change in the kernel itself (rather than in the kvm modules) and that change is present only in kernels 2.6.23 and higher.

---

### Post by walkerk on 2007-12-20
> **lemurian said:**
> walkerk, I see you've edited the first post to announce your intention to get a procedure in place to install a Hardy kernel.  Any progress?  (I searched and found no thread about it.  If I missed something, please correct me.)

I'm thinking I might want to move up to a Hardy kernel because of issues I've been having with kvm preventing my laptop from suspending properly.  Based on what I've read on the kvm-devel list, I think that problem required a change in the kernel itself (rather than in the kvm modules) and that change is present only in kernels 2.6.23 and higher.

I've actually made the script and I am currently testing it... upgrading to 2.6.24-2-generic.

I am starting a new thread right now. :D

---

### Post by Chame_Wizard on 2008-02-21
> **walkerk said:**
> This should work for Feisty Fawn and Edgy Eft users. This will install the current developing kernel that will be realeased with Gutsy Gibbon.



**[COLOR=Red]Do not upgrade any packages while you have the Gutsy repository open.[/COLOR]**

[COLOR=Red]Disclaimer:[/COLOR] This is how I successfully upgraded my kernel without having to compile it myself. A couple of users have had issues with this method so be aware that problems can arise. At this point removing the new kernel using the instructions at the end of the post should do the trick, but if it doesn't I take no responsibility. I will monitor this thread to try to help out anyone thats had issues.

*** With that being said, most users have not had any problems and are enjoying the new kernel. Also, this will not remove your current kernels.***

[SIZE=3][COLOR=DarkOrange]**After you've upgraded please reply with your machine Model and specs so that others can benefit :)**[/COLOR][/SIZE]


[SIZE=4]**You can download the script I've attached and do the following:**[/SIZE]

**[COLOR=DarkOrange]kernel.sh[/COLOR]** will upgrade to the current kernel using meta packages, meaning if you run this every week or so it will upgrade your kernel if a new version has been released. Current version is **2.6.22-14**

Move to the directory in which you downloaded the script.. for example:
```
cd /path/to/file/
```make the script executable:
```
chmod +x kernel.py
```run it:
```
sudo python kernel.py
```This installed the new kernel. Enjoy :)



[SIZE=4]**Or you can do it manually...**[/SIZE]
[COLOR="Blue"]Use  the Kubuntu 64 7.10 Live CD
sudo mkdir /media/sda2
sudo mount /dev/sda2  /media/sda2[/COLOR]

First you need to add the Gutsy repository (this is only temporary to pull the new kernel):
```
echo 'deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted' | sudo tee -a /etc/apt/sources.list
```Now that you've added the repository you need to update:
```
sudo apt-get update
```Next you need to install the new kernel:
```
sudo apt-get -y install linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
```Now that you've pulled the kernel you should remove the Gutsy repository from your sources.list:
```
gksudo gedit /etc/apt/sources.list
```Now you can remove the line or simply comment it out: (It'll be the last line of the file)
```
#deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
```[COLOR="Blue"]
I saved the source.list in   /media(dev)/sda2/boot/grub[/COLOR]

Once again you need to update so that you'll stop pulling updates from the Gutsy repository:
```
sudo apt-get update
```Alright. If you've done all of the above without errors, you've successfully installed 2.6.22-14-generic. Now you need to reboot into the new kernel:
```
sudo reboot
```Enjoy :)

[SIZE=5][COLOR=DarkOrange]Miscellaneous fixes [/COLOR][/SIZE]



[SIZE=3]**Ok.. Did it hose your box? Too easy.**[/SIZE]

Reboot your computer and at Grub press esc to boot into your last kernel. (probably 2.6.20-16-*)

Remove the installed kernel and then upgrade. 
```
sudo apt-get remove linux-image-2.6.22-14-generic linux-headers-2.6.22-14-generic linux-headers-2.6.22-14 linux-restricted-modules-2.6.22-14-generic linux-ubuntu-modules-2.6.22-14-generic
``````
sudo apt-get upgrade
```[COLOR="Blue"]didn't work for me [/COLOR] :confused:
my GRUB.menu.lst:

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=57eaed1c-4908-4e68-b782-991471c9da22 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic
root=UUID=57eaed1c-4908-4e68-b782-991471c9da22 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic
root=UUID=57eaed1c-4908-4e68-b782-991471c9da22 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic
root=UUID=57eaed1c-4908-4e68-b782-991471c9da22 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic
root=UUID=57eaed1c-4908-4e68-b782-991471c9da22 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

