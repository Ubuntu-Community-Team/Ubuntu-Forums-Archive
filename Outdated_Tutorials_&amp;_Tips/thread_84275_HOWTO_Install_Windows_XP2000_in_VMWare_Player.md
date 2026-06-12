---
title: "HOWTO: Install Windows XP/2000 in VMWare Player"
date: 2005-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by dryandplain on 2005-10-30
This guide will allow you to install Windows XP or 2000 solely with the VMWare Player. For the uninitiated, VMWare released a free application that allows users to run, but not create virtual machines. Using QEMU, we will create an environment suitable for use with the player.

As a side-note, I'd like to point out that VMWare makes quality software. If you require additional functionality, consider upgrading to Workstation. For those curious, these actions are condoned by the developers as per this quote:

"We&#8217;re well aware of what people could potentially do, and we&#8217;ll live with the consequences. As you observe, Workstation has a lot of features that no amount of vi and dd hacking will replicate and these are what make Workstation worth buying (eg: Teams as you mention, or snapshots). I suspect that most people who go to the trouble are one&#8217;s who haven&#8217;t bought or wouldn&#8217;t buy Workstation anyway."

Installing the player itself involves some patience. Get the Linux tar from [this page]("http://www.vmware.com/download/player/"). Most of my instructions will be shamelessly ripped from [this lovely tutorial]("http://www.ubuntuforums.org/showthread.php?t=65638"). Fire up a root terminal and do:

```
apt-get install build-essential
uname -r
apt-get install linux-headers-'kernel version'
apt-get install gcc-3.4
apt-get install g++-3.4
```

Now that the initial dependencies have been met, let's continue.

```
tar xvzf VMware-player-1.0.0-16981.tar.gz
cd vmware-player-distrib
export CC=/usr/bin/gcc-3.4
./vmware-install.pl
```

The installer has an unusually high number of prompts, all of which can be answered the default "yes" to by hitting enter. After hitting enter a few dozen times and agreeing to the license, everything should install successfully. If you're having problems installing the actual player, that other guy might be more qualified to diagnose it than I am. Moving along...

There are two components to a virtual machine, the hard drive image and a text file that VMWare interprets. First, we'll create an image with QEMU.

I know this sounds a little odd, but I couldn't get the QEMU command used to generate the disk working from the Linux port. Fortunately, the utility works fine with the Windows port under Wine. I can't really bothered to delve into the specifics of installing Wine other than suggesting:

```
apt-get install wine
```

Then download and install the [Windows version of QEMU]("http://free.oszoo.org/ftp/qemu/win32/release/QemuInstall-0.7.2.exe"). Execute it from a command line as follows:

```
wine qemu-img.exe create -f vmdk WindowsXPPro.vmdk 2G Formating 'WindowsXPPro.vmdk', fmt=vmdk, size=2097152 kB
```

This will generate a 320k file which is a usable blank drive. Create a new folder to contain our files and name this guy either WindowsXPPro.vmdx or Windows2000Pro.vmdx accordingly.

You now have the choice to install XP or 2000. On my 1.2ghz/512mb system Windows 2000 runs considerably more responsively; your choice. As per the other tutorial, we should be able to insert our CD and go after the following. But in my case, neither my bootable XP or 2000 CD had any interest in well, booting. I'd suspect I'm not the only one with this concern, so we'll play with ISO images instead.

```
apt-get install gnomebaker
```

After inserting your original Windows disc, load Gnomebaker, choose "Copy Data CD," and tick the "Create ISO only" box. Save the resulting ISO as either WindowsXPPro.iso or Windows2000Pro.iso to the folder we just created. If the processes ever freezes 99%, feel free to "killall gnomebaker" without concern.

Unfortunately, our ISO image will not have the bootable sector intact. We'll instead boot from a series of floppy images. My Windows 2000 disc included them in a "bootdisk" folder, whereas XP did not. For 2000, copy the four img files from it to our created folder.

With XP, you'll need some additional nonsense. Hunt down an appropriate set from Microsoft for your version of XP, and do the following:

```
apt-get install cabextract
cabextract 'nameofarchive.exe' -d 'our working directory'
```

Deleted the non-img extracted files.

Now that we have a matching ISO and floppy set, we're ready to proceed with installation. Paste one of the following to a text editor (gedit/leafpad) and save it as either WindowsXPPro.vmx or Windows2000Pro.vmx to our directory:

Windows XP:

```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "WindowsXPPro.vmdk"
memsize = "192"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "WindowsXPPro.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"
floppy0.fileType = "file"
floppy0.fileName = "cdboot1.img"
floppy0.startConnected = "True"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows XP Pro"
guestOS = "winxppro"
nvram = "WindowsXPPro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
uuid.bios = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
ethernet0.generatedAddress = "00:0c:29:4c:23:7b"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = "WindowsXPPro.vmss"
tools.remindInstall = "TRUE"
```

Windows 2000:

```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "Windows2000Pro.vmdk"
memsize = "192"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "Windows2000Pro.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"
floppy0.fileType = "file"
floppy0.fileName = "CDBOOT1.IMG"
floppy0.startConnected = "True"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows 2000 Pro"
guestOS = "win2000pro"
nvram = "Windows2000Pro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
uuid.bios = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
ethernet0.generatedAddress = "00:0c:29:4c:23:7b"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = "Windows2000Pro.vmss"
tools.remindInstall = "TRUE"
```

Double click on the resulting file, and Windows should start to install. The only screwiness left at this point is that we'll need to swap floppy images. When prompted, click on the floppy icon to "eject" the drive. In Nautilus, rename cdboot1.img to cdboot01.img and cdboot2.img to cdboot1.img, then click the floppy icon again to continue. It may sound a little strange, but you're essentially renaming the images to match that of the first file when it wants it. You'll get the hang of it, promise.

Once the floppies have done their thing, the ISO will take over and Windows will install normally.

Sorry about the length of this. If I had web hosting, I could've posted many of these files and shaved off a few steps. I'll try my best to answer any questions that may come up, but concede that my level of Linux know-how is only intermediate.

[Here's a screeny for encouragement]("http://i24.photobucket.com/albums/c35/dryandplain/ps8.png")! :D

Take care,
-Kyle

---

### Post by sethmahoney on 2005-11-02
Thanks a lot!  Works great, except, is it normal for the part of the install where Windows detects and installs all your hardware to take a REALLY long time?

---

### Post by sethmahoney on 2005-11-03
Any ideas on how to bump the resolution above 640 x 480?  The only video driver included for Windows 2000 is a VGA driver...

---

### Post by yabbadabbadont on 2005-11-03
If you have downloaded the Win2k video driver for your card, try installing it inside the Win2k that is running under VMWare.

I don't know if it will work as I'm currently in the process of setting this up myself.

---

### Post by kaamos on 2005-11-03
Thanks for the howto!

[QUOTE=dryandplain]I'd suspect I'm not the only one with this concern, so we'll play with ISO images instead.

```
apt-get install gnomebaker
```

After inserting your original Windows disc, load Gnomebaker, choose "Copy Data CD," and tick the "Create ISO only" box. Save the resulting ISO as either WindowsXPPro.iso or Windows2000Pro.iso to the folder we just created. If the processes ever freezes 99%, feel free to "killall gnomebaker" without concern.
[/QUOTE]

A bit simpler way to do this: Insert the windows cd and run (no need to be root):
```
cat /dev/cdrom > WindowsXPPro.iso
```

---

### Post by zachtib on 2005-11-03
nice, i assume i can increase the size of the virtual drive by changing this line:
wine qemu-img.exe create -f vmdk WindowsXPPro.vmdk 2G Formating 'WindowsXPPro.vmdk', fmt=vmdk, size=2097152 kB
to make a larger drive?

---

### Post by yabbadabbadont on 2005-11-04
[QUOTE=yabbadabbadont]If you have downloaded the Win2k video driver for your card, try installing it inside the Win2k that is running under VMWare.

I don't know if it will work as I'm currently in the process of setting this up myself.[/QUOTE]
OK, I found in the manual that you have to install the VMWare tools for the guest OS in order to use better (faster, higher resolution) graphics.  I don't know if the vmware player supports this option, but in the 30-day eval of vmware workstation, you choose VM->Install VMware Tools from the menu while the virtual machine is powered on.  Then you can choose a higher screen resolution.  The help files also say that the new SVGA device is faster too.

---

### Post by yabbadabbadont on 2005-11-04
[QUOTE=zachtib]nice, i assume i can increase the size of the virtual drive by changing this line:
wine qemu-img.exe create -f vmdk WindowsXPPro.vmdk 2G Formating 'WindowsXPPro.vmdk', fmt=vmdk, size=2097152 kB
to make a larger drive?[/QUOTE]

If you run "wine qemu-img.exe /?" you will see that only the first part of that string is the actual command.  The last half, everything after "2G" is probably what the command prints out on the screen.  You should just be able to change the "2G" to whatever size in gigabytes you want.

---

### Post by zachtib on 2005-11-04
yep, worked great, now for another question.
i installed samba on ubuntu to share a folder with Windows running in VMWare, in case the virtual hard drive fills up, i can move files onto my main hard drive.  when my laptop is plugged into the network, this works fine, but when i am disconnected, Ubuntu and XP in VMware cannot see each other.  is there a way to create a virtual network incuding the host OS and the guest OS so they will always be connected?

---

### Post by Wombley on 2005-11-04
Most probably the reason you couldn't create the images with linux qemu is that the capability to create VMDK images was only added in 0.71, and ubuntu's version is still at 0.70. 0.72 (binary from [http://fabrice.bellard.free.fr/qemu/download.html]("http://fabrice.bellard.free.fr/qemu/download.html") works fine. You also dont need to do all that with the floppy disks, at least for Windows 2000, at least if you make the cdrom image with the command ```
dd if=/dev/cdrom of=Windows2000Pro.iso
``` (although gnomebaker should work just as well) - just press escape when booting vmplayer and select cdrom to boot from it - you can remove all the floppy related stuff from the config file.

In response to zachtib, I believe what you want is host-only networking - it bridges the hosts connection to the network by default (you may have success just selecting host-only networking from the ethernet submenu under Devices in player, I don't know) - I haven't tried this myself but there's docs for workstation that'll probably give you an idea at [http://www.vmware.com/support/ws5/doc/ws_net.html]("http://www.vmware.com/support/ws5/doc/ws_net.html")

---

### Post by reedlaw on 2005-11-04
I used the defaults for all of the questions in the VMWare Player install, but I can't get networking working in my virtual Windows.  Do I need to assign an IP address to the virtual machine?  If so, what is my gateway IP address?

---

### Post by BLTicklemonster on 2005-11-05
So, I will attempt this later, but in the meantime, allow me to ask the one central question that will determine whether I will actually do this or not:


If I do this, will I be able to run ANY app that windows runs?

---

### Post by BLTicklemonster on 2005-11-05
... like I'd wait for an answer, especially with asshats messing with the server.

So I get this error:

```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Virtual Machine Player is
suitable for your running kernel.  Do you want this program to try to build the
vmmon module for your system (you need to have a C compiler installed on your
system)? [yes]

Using compiler "/usr/bin/gcc-3.4". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.


```

What do I do?


*edit:

Okay, I restarted terminal, sudo mkdir my way to having the /linux/include directory, went at it again, and viola!!!

```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Virtual Machine Player is
suitable for your running kernel.  Do you want this program to try to build the
vmmon module for your system (you need to have a C compiler installed on your
system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Virtual Machine Player cannot work in such configuration. Please either
recompile your kernel with "/usr/bin/gcc" version "4.0.2", or restart
/usr/bin/vmware-config.pl with CC environment variable pointing to the "gcc"
version "3.4.5".

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

bill@ubuntumonster:~/vmware-player-distrib$

```

So I guess I remove 4.0.2, and put in 3.4.5, and start over...


*edit again:

No wait, if I do that, I lose tons of stuff. 

Now what?

---

### Post by Wombley on 2005-11-05
You need to install everything from the initial instructions - linux-headers will provide /usr/src/linux/include, and once you install gcc 3.4.5 (alongside 4.0.2 - they can coexist) and type the export CC=/usr/bin/gcc-3.4 line it'll work.

---

### Post by zachtib on 2005-11-05
just install gcc-3.4 alongside 4.x, then use sxport CC=/usr/bin/gcc-3.4 before installing

---

### Post by Wombley on 2005-11-05
Getting video to work above 640x480/16 colours (tested in 2000):

[LIST=1]
[*]Get the windows vmware tools from [http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=920](http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=920)
[*]Set the ISO image as the cdrom source in the .vmx file
[*]Install the tools. Ignore the warning about the SVGA driver
[*]In add new hardware, select graphics card and select from list, and have disk
[*]Select the video/winnt2k folder under the cdrom drive
[*]Ignore warnings and install
[*]Select a higher resolution from display properties
[*](Hopefully) done
[/LIST]

Also - simple way to get networking working: select NAT from the Ethernet menu in vmplayer

---

### Post by BLTicklemonster on 2005-11-05
> 
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Virtual Machine Player is
suitable for your running kernel.  Do you want this program to try to build the
vmmon module for your system (you need to have a C compiler installed on your
system)? [yes]

Using compiler "/usr/bin/gcc-3.4". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is an existing directory, but it does not
contain a "linux" subdirectory as expected.


well, it tried to use gcc-3.4, but it couldn't find a linux subdirectory. why is it saying I don't have /usr/src/linux/include? Is there something I should have before even doing this that I don't now about?

---

### Post by Wombley on 2005-11-06
You MUST install the linux-headers-386 package to compile the kernel module - this will create the /usr/src/linux/include directory for you, and put all the files you need in it.

---

### Post by BLTicklemonster on 2005-11-06
So far so good. So that may need to be added to the first post, along with adding sudo to:

> tar xvzf VMware-player-1.0.0-16981.tar.gz
cd vmware-player-distrib
export CC=/usr/bin/gcc-3.4
sudo ./vmware-install.pl

because mine wouldn't let me ./vmware~ without it.

---

### Post by BLTicklemonster on 2005-11-06
Okay, what else is there I'm supposed to know about?

> bill@ubuntumonster:~$ wine qemu-img.exe create -f vmdk WindowsXPPro.vmdk 2G Formating 'WindowsXPPro.vmdk', fmt=vmdk, size=2097152 kB
wine: cannot find 'qemu-img.exe'


qemu is installed. Wine is installed. The previous step worked once I was told to have the linux headers. Is there something I'm supposed to have?

*edit:

I tried 

wine c:\Program Files\Qemuqemu-img.exe create -f vmdk WindowsXPPro.vmdk 2G Formating 'WindowsXPPro.vmdk', fmt=vmdk, size=2097152 kB
and

wine c:\Program_Files\Qemu\qemu-img.exe create -f vmdk WindowsXPPro.vmdk 2G Formating 'WindowsXPPro.vmdk', fmt=vmdk, size=2097152 kB

and get errors saying it can't find anything.

I used winefile, and yes, it's there alright. But I can't get it to work. I feel like I'm soooo close.


*edit:

I can browse to most .exe files and double click them and they will open courtesy of wine, but nothing in the Qemu directory will. Do I have to enable Qemu as I had to enable the nvidia drivers (which messed me up bigtime for ever, let me tell you) before it will work? Perhaps killall gnome-panel? Restart? Throw money at it? Sacrifice a burnt offering?

---

### Post by BLTicklemonster on 2005-11-06
Installing with Qemu using the following:

> dd of=hd.img bs=1024 seek=3000000 count=0



qemu -hda /home/bill/hd.img -cdrom /home/bill/Desktop/WindowsXPPro/winxppro.iso -boot d -m 512 -user-net

just to be doing something until someone comes along with an answer lol.

---

### Post by ranf on 2005-11-06
[QUOTE=BLTicklemonster]
wine c:\Program Files\Qemuqemu-img.exe create -f vmdk WindowsXPPro.vmdk 2G Formating 'WindowsXPPro.vmdk', fmt=vmdk, size=2097152 kB[/QUOTE]
```
wine "c:\Program Files\Qemu\qemu-img.exe" create -f vmdk WindowsXPPro.vmdk 2G
```
Note the quotes (") around the pathname.

---

### Post by BLTicklemonster on 2005-11-06
I don't know why, but it usually, on the error messages, leaves out the \ marks. I did put them in originally.

I have seen it come back with no \ marks at all. That one time, it did have some, though. Really odd.

---

### Post by BLTicklemonster on 2005-11-06
[QUOTE=ranf]```
wine "c:\Program Files\Qemu\qemu-img.exe" create -f vmdk WindowsXPPro.vmdk 2G
```
Note the quotes (") around the pathname.[/QUOTE]
:) :) :) okay.



*edit:

Okay, that worked. Now I go to the folder with the image and the floppy image files in it, and I double click on the vmx file, and I get this:


[img]http://www.hawkwinds.com/tickle/novmdk.jpg[/img]

Now my question is, at this point:

[QUOTE=dryandplain]
```
wine qemu-img.exe create -f vmdk WindowsXPPro.vmdk 2G Formating 'WindowsXPPro.vmdk', fmt=vmdk, size=2097152 kB
```

This will generate a 320k file which is a usable blank drive. Create a new folder to contain our files and name this guy either WindowsXPPro.vmdx or Windows2000Pro.vmdx accordingly.
[/QUOTE]


Exactly where was I supposed to create a new folder, and how, and why does this nifty how to not specify stuff for beginners if it is accessible to beginners? 

I have been beating my head against Linux for 3 years because people refuse to give specific information. I dealt with instructors in school who couldn't teach their way out a paper bag, yet they were being paid to be teachers. Janitors should be paid more than instructors, and teachers should be at the top. No wait, Janitors would be better teachers, I bet, than any "instructor" I ever had.

That was my rant for the moment.

Now back to qemu. Yay, it installed. But how do I bring it back up again once I close XP? And if I want to install anything to XP in Qemu, how do I get it to see the cdrom? At present, it's stuck showing the xp installation cd, no matter if I restart xp or not. Of course I won't be able to do anything until I get back to xp, which I can't do because nothing I have found relating to using qemu was written by a non instructor mentality person.

There I go ranting again.

Come on people, be specific. I should not have had to been asking all these questions. Shoot, the entire freaking planet would be using LInux if you all would just be specific.

---

### Post by kashms on 2005-11-06
Why just not run win2000 or winXP using qemu? Are there any performance gains when using the VMware Player?

---

### Post by yabbadabbadont on 2005-11-06
BLTicklemonster
> Come on people, be specific. I should not have had to been asking all these questions. Shoot, the entire freaking planet would be using LInux if you all would just be specific.


<begin rant>No, you shouldn't have had to been asking all of those questions.  If you had read and followed *all* the instructions in the first post, as well as the other messages on the first page, you would realize that most of your questions had already been answered before you posted your first question.  If you have been using Linux for 3 years, and yet still ask questions such as these, then perhaps the problem doesn't lie with those of us who donate our time (and patience) answering questions for those who are less knowledgeable.  If you are going to ask for help, which no one is under any obligation to provide, then you should at least be polite about it.</end rant>

I apologize to everyone else who wasted time reading this post.

---

### Post by Wombley on 2005-11-06
The new folder was to contain all the .vmx, .vmdx and other files vmware creates. This can be made and named anything you want, eg /home/username/win2000 or similar. You then put all the files you need to create in this folder, for example the .vmdx file you create with qemu. The problem you're presently having is that you either copied the wrong .vmx file from the original post (winxp instead of win2000 or vice versa) or you didn't change the filename to Windows2000Pro.vmdx when using qemu (if you're trying to use windows 2000). Create the file with the right name and it should work.

The advantage of using VMWare is that it's significantly faster than qemu (even with the kqemu accelerator module - I've heard figures like 90% of native performance for VMWare, although I can't remember where right now, but it does seem about that fast, whereas I noticed very little difference from normal qemu with kqemu).

---

### Post by BLTicklemonster on 2005-11-06
I made two, one for xp, one for 2000. Neither work.

---

### Post by BLTicklemonster on 2005-11-06
[QUOTE=yabbadabbadont]BLTicklemonster


<begin rant>No, you shouldn't have had to been asking all of those questions.  If you had read and followed *all* the instructions in the first post, as well as the other messages on the first page, you would realize that most of your questions had already been answered before you posted your first question.  If you have been using Linux for 3 years, and yet still ask questions such as these, then perhaps the problem doesn't lie with those of us who donate our time (and patience) answering questions for those who are less knowledgeable.  If you are going to ask for help, which no one is under any obligation to provide, then you should at least be polite about it.</end rant>

I apologize to everyone else who wasted time reading this post.[/QUOTE]

Thank you for your reply. I you assume I've been using linux for 3 years because you read that into it. I've been trying to use linux for 3 years. Big difference. Also, re-read. The answers I've gotten have gotten me this far. 

No apology. And trust me, this is polite. 
Now are you going to help, or sit up in the monkey gallery tossing peanuts?

---

### Post by BLTicklemonster on 2005-11-06
[QUOTE=kashms]Why just not run win2000 or winXP using qemu? Are there any performance gains when using the VMware Player?[/QUOTE]
I installed xp with qemu, and it is nice, but now that I closed it, I cant find how to open it again, nor can I find info on how to install anything with xp in qemu.

I'm just having a ball here.

---

### Post by twowheeler on 2005-11-06
You guys rock!  This is perfect.

---

### Post by Wombley on 2005-11-06
[QUOTE=BLTicklemonster]I made two, one for xp, one for 2000. Neither work.[/QUOTE]

OK, step by step. I'll assume you're making a windows 2000 disk, if not replace all Windows2000Pro references with WindowsXPPro, and the guestOS parameter in the .vmx file to winxppro. Ill also assume you've already got VMWare player installed properly:

Start a terminal, use mkdir to create a folder to keep the files in. Make sure (from synaptic) that the linux version of qemu IS NOT installed. Get the latest version from [http://fabrice.bellard.free.fr/qemu/qemu-0.7.2-i386.tar.gz]("http://fabrice.bellard.free.fr/qemu/qemu-0.7.2-i386.tar.gz") .

```

cd /
sudo tar -zxf /path/to/downloaded/qemu.tar.gz
cd ~/folderyoucreated
qemu-img create -f vmdk Windows2000Pro.vmdk 2G Formating 'Windows2000Pro.vmdk', fmt=vmdk, size=2097152 kB

```

Put your windows cd in the drive (assuming first cdrom drive)

```
sudo dd if=/dev/cdrom of=Windows2000ProCD.iso
```

Create a new text file called Windows2000Pro.vmx in your folder. Copy and paste the following into it:

```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "Windows2000Pro.vmdk"
memsize = "192"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "Windows2000ProCD.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"
floppy0.startConnected = "False"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows 2000 Pro"
guestOS = "win2000pro"
nvram = "Windows2000Pro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
uuid.bios = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
ethernet0.generatedAddress = "00:0c:29:4c:23:7b"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = "Windows2000Pro.vmss"
tools.remindInstall = "TRUE"
```

Save. In your terminal type ```
vmplayer Windows2000Pro.vmx
```
You should now be able to install windows. When you wish to run it again afterwords use the same command.

---

### Post by BLTicklemonster on 2005-11-06
The stuff I did is in red. Trying to show where I tried to follow step by step.

[QUOTE=Wombley]OK, step by step. I'll assume you're making a windows 2000 disk, if not replace all Windows2000Pro references with WindowsXPPro, and the guestOS parameter in the .vmx file to winxppro. Ill also assume you've already got VMWare player installed properly:

Start a terminal, use mkdir to create a folder to keep the files in. [COLOR="Red"]sudo mkdir /home/bill/Windows2000Pro[/COLOR] Make sure (from synaptic) that the linux version of qemu IS NOT installed [COLOR="Red"]done[/COLOR]. Get the latest version from [http://fabrice.bellard.free.fr/qemu/qemu-0.7.2-i386.tar.gz]("http://fabrice.bellard.free.fr/qemu/qemu-0.7.2-i386.tar.gz") .
[COLOR="Red"]I downloaded it to /home/bill/[/COLOR]
```

cd /
sudo tar -zxf /path/to/downloaded/qemu.tar.gz
[COLOR="Red"]sudo tar -zxf /home/bill/qemu-0.7.2-i386.tar.gz[/COLOR]
cd ~/folderyoucreated
[COLOR="Red"]cd /home/bill/Windows2000Pro[/COLOR]
qemu-img create -f vmdk Windows2000Pro.vmdk 2G Formating 'Windows2000Pro.vmdk', fmt=vmdk, size=2097152 kB

```

```
[COLOR="Red"]bill@ubuntumonster:~$ cd /home/bill/Windows2000Pro
bill@ubuntumonster:~/Windows2000Pro$ qemu-img create -f vmdk Windows2000Pro.vmdk 2G Formating 'Windows2000Pro.vmdk', fmt=vmdk, size=2097152 kB
bash: qemu-img: command not found
[/COLOR]
```

[/QUOTE]
See what I mean?


Even going to the ludicrous extreme of extracting qemu to /home/bill/Windows2000Pro, and doing this:

bill@ubuntumonster:~$ cd /home/bill/Windows2000Pro/usr/local/bin/
bill@ubuntumonster:~/Windows2000Pro/usr/local/bin$ qemu-img create -f vmdk Windows2000Pro.vmdk 2G Formating 'Windows2000Pro.vmdk', fmt=vmdk, size=2097152 kB

 I get this:

bash: qemu-img: command not found


So I've tried everything I can think of. I'm stumped.


Huh, shouldn't it have originally put qemu files in /usr/local/bin/? I'm there, and there aren't any.

---

### Post by BLTicklemonster on 2005-11-06
God All Mighty.

I just got through Chowning my way all the way through putting qemu into /usr/local yada yada yada.



*edit:

Arrrrgh:

Network boot from AMD Am79c970A
Copyright (C) 2003-2005 VMware, Inc.
Copyright (c) 1997-2000 Intel Corporation

CLIENT MAC ADDR: blah blah blah
PXE-E53: No boot filename received

PXE-M0F: Exiting Intel PXE ROM.
Operating System not found

... well, at least I got past that part.

---

### Post by BLTicklemonster on 2005-11-07
So what's to stop me from just putting in a cd and pressing CD-ROM from the vmware window and installing from there?

---

### Post by chronusdark on 2005-11-07
how would i configure it so the virtual machine would just use my cdrom instead?

---

### Post by BLTicklemonster on 2005-11-07
Follow this all the way through, and when you get stuck where i was just now, have the cd in the tray, and click cd-rom from the tool bar in vmware, lol. That's what I'm doing now. Probably will blow mine and your machines up though. I'd wait for some answers first before ever following me down the road to destruction, though.


(god it's slow as christmas, but then I'm doing winxp now instead of 2000. seems like the dude who started this thread said 2000 was faster...)

Once I get it on there, I wonder how I'll ever bring it back up? And if I get it back, how do I use it to install stuff? Will it be just like using plain old xp? Will it recognize cds I put in? Will it go online and get infected so I don't feel like its like "not really xp"?
j/k

---

### Post by BLTicklemonster on 2005-11-07
[img]http://www.hawkwinds.com/tickle/xpinlinux.jpg[/img]

Okay, so I'm sloppy, and it says it's Windows 2000 Pro. But it's working. And it goes online.


Okay, I closed it. Where'd it go? lol

I now have t xps. one in qemu, the other one in vmware. Neither one would see what I had put in the cd tray, so other than uploading the entire contents of a cd to my web site, downloading it and installing it like that, (if i can ever get either up again) what do I do?

---

### Post by Wombley on 2005-11-07
[QUOTE=BLTicklemonster]
 I get this:

bash: qemu-img: command not found


So I've tried everything I can think of. I'm stumped.


Huh, shouldn't it have originally put qemu files in /usr/local/bin/? I'm there, and there aren't any.[/QUOTE]

You didn't perform the cd / command at the beginning, therefore it would have extracted the files to the directory you were in at the time. The reason it wouldn't work when you extracted it into your Windows2000Pro directory was that Ubuntu doesn't have the current directory in the search path by default - you'd have to have used ./qemu-img in this case. Sorry about the boot thing, forgot to say press escape when its booting to boot from CD. Bringing it back up is just the same way you installed it, just vmplayer /path/to/Windows2000Pro.vmx - and you can install pretty much any windows application on it and it should work like normal (with the exception of games etc which use a lot of 3d graphics). And yes, it is perfectly capable of being infected :)

To get the CD working, edit the .vmx file and replace these four lines:

```
ide1:0.present = "TRUE"
ide1:0.fileName = "Windows2000ProCD.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"
```

With these three:

```
ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "cdrom-raw"
```

---

### Post by BLTicklemonster on 2005-11-07
[QUOTE=Wombley]Bringing it back up is just the same way you installed it, just vmplayer /path/to/Windows2000Pro.vmx - and you can install pretty much any windows application on it and it should work like normal (with the exception of games etc which use a lot of 3d graphics). And yes, it is perfectly capable of being infected :)

[/QUOTE]
Thanks. When I do that, I get 
Non-System disk of disk error
Replace and press any key when ready.

Im not goiing to have to install it each time I try to use it am I?

---

### Post by mapman on 2005-11-07
I had the same problem too.  Apparently vmware player is looking for your CDBOOT1.IMG, remnants of the install.  To avoid this you could click on the floppy button on the top of the player window to disable the floppy, then enter twice to enter the windows startup....or edit the vmx file from floppy0.startConnected = "True" to floppy0.startConnected = "false".  Hope that helps.  Is there a link for possible vmx options, anyone?;) 

Now I have a question...is their any quick way to increase the resolution?  I tried previous steps of installing the video adapter driver from the vmtools iso but to no avail.   Any suggestions...anybody?;)

---

### Post by BLTicklemonster on 2005-11-07
Thanks, I'll try that this evening. I wonder about higher resolution, too. 


(I deleted what I did this morning, going to start from scratch tonight, see if things go better)

---

### Post by Wombley on 2005-11-07
[QUOTE=BLTicklemonster]Thanks. When I do that, I get 
Non-System disk of disk error
Replace and press any key when ready.

Im not goiing to have to install it each time I try to use it am I?[/QUOTE]

You shouldn't have to reinstall it... - did you change the boot order in the virtual bios? If so change it back, or use escape on each boot and select the hard disk.

---

### Post by BLTicklemonster on 2005-11-07
[QUOTE=Wombley]You shouldn't have to reinstall it... - did you change the boot order in the virtual bios? If so change it back, or use escape on each boot and select the hard disk.[/QUOTE]
I ... um ... look, I'm dumb, so if you would, talk down to me like I'm an idiotard, please? Like honestly, really, when you tell me stuff, if you don't mind, please list actions and methods. I have a gazillion things I'm attempting to do all at the same time, between working on a totally new way of doing things in UT, to mapping for these changes, to trying to get unrealed to work in ubuntu, my mind's scattered and it's tough on me trying to keep up with stuff. I was lucky to remember the chwon stuff I'd not have had to do if I were paying attention, that and remembering to sudo back there in the beginning when I was paying attention, lol.

I'm afraid though, that if windows in vmware won't get me using unrealed, then I'll have to either say g'bye to ubuntu or dual boot. 

Hey, can I run an entire HD in vmware? Like slave my XP drive, and run it in vmware? That would be way easier than what we're doing here. Of course dual booting would be easier, but every time I've asked and been told how to set up dual booting two hard drives, I've not understood it well enough to do it. Once again, it's been "do this", not "go here, and do this here, then that there, moronmonster", which trust me, would be better. I may not be the brightest french fry on the apple tree, but once I get something figured out, I usually raise cain at it. It's just getting there that is the hard part for me.

---

### Post by Wombley on 2005-11-07
I believe it's possible with VMWare Workstation, but I think its a bit complex and I'm not sure if it works with Player. Try the following:

```
vmplayer Windows2000Pro.vmx
```
As soon as it starts booting click inside the window to capture the mouse and press F2
Press the right key 4 times to get to the Boot menu in the BIOS
Use the down key to select the Hard Disk option
Press the + key until the Hard Disk option is at the top
Press F10 to save changes, and press Enter to confirm
Wait as it reboots, and hope that windows comes up...

---

### Post by BLTicklemonster on 2005-11-07
Thanks, I'll give it a go tonight. ;)

---

### Post by kashms on 2005-11-07
[QUOTE=Wombley]Getting video to work above 640x480/16 colours (tested in 2000):

[LIST=1]
[*]Get the windows vmware tools from [http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=920](http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=920)
[*]Set the ISO image as the cdrom source in the .vmx file
[*]Install the tools. Ignore the warning about the SVGA driver
[*]In add new hardware, select graphics card and select from list, and have disk
[*]Select the video/winnt2k folder under the cdrom drive
[*]Ignore warnings and install
[*]Select a higher resolution from display properties
[*](Hopefully) done
[/LIST]

Also - simple way to get networking working: select NAT from the Ethernet menu in vmplayer[/QUOTE]

I downloaded the file and edited the vmx file so it reads:
ide1:0.fileName = "windows.iso"

but how do I actually install the tools?

---

### Post by mapman on 2005-11-07
You can install the tools by entering into the OS through VMPlayer then accessing the ide1 drive or in my case it was D: drive, then proceed from there to install it.

I wasn't able to increase the resolution using these steps after installing the tools however....let me know how you do if you can though.  Thanks.;)

---

### Post by kashms on 2005-11-07
Double clicking the vmware tools in "My Computer" (Drive D:) yields a setup.exe error:

"The application failed to initialize properly (0xc0000006). Click on OK to terminate the application"

Is this normal?

---

### Post by twowheeler on 2005-11-07
Hmm, well, I have hit a roadblock.  Everything seems to work well except for two things: sound and printing.  Both of these are USB devices on my machine.  Sound I can live without, but I gotta have access to the printer.  There are *lots* of "my usb printer won't work" posts on the vmware forums, so I am not alone.  I am still working at it, and will post if I figure it out.
;)

Edit: Ok, I got it.  I had to edit the Windows2000Pro.vmx file to remove the settings that look like this:
> usb.autoConnect.device0 = "path:2/1 autoclean:1"
usb.autoConnect.device1 = "path:1/1/2 autoclean:1"
These were apparently added automatically as I played with the USB device buttons.  The problem appears to be that vmware is *too* smart -- it knows how to access and use the USB hardware directly, but that usually creates a problem for the host device drivers.  In my case, I noticed that after running the vm, I had no sound or printer access until a reboot.  People in the vmware forums seem to be trying to unload their linux printer module before vmware starts, running the vm, and then reloading the host module to get access back to the host.  Life's too short for that.  If you disable direct access to the USB devices, then by default it will use the host drivers.  I was able to install an adobe postscript printer driver in the windows guest, and point it to the samba printer.  It works perfectly.  I have sound back too.

Lesson learned: once you get it going, don't click on any usb device buttons.  It might be even better to change usb.present = "TRUE" to usb.present = "FALSE" if you can live without direct access to usb, although I have not tried that yet.

---

### Post by BLTicklemonster on 2005-11-07
[QUOTE=mapman]I had the same problem too.  Apparently vmware player is looking for your CDBOOT1.IMG, remnants of the install.  To avoid this you could click on the floppy button on the top of the player window to disable the floppy, then enter twice to enter the windows startup....or edit the vmx file from floppy0.startConnected = "True" to floppy0.startConnected = "false".  Hope that helps.  Is there a link for possible vmx options, anyone?;) 

Now I have a question...is their any quick way to increase the resolution?  I tried previous steps of installing the video adapter driver from the vmtools iso but to no avail.   Any suggestions...anybody?;)[/QUOTE]
woot woot. Now on to resolution... yikes!!!

BTW, how do I install from a cd in this?

---

### Post by BLTicklemonster on 2005-11-08
Wow, just change resolution. lmao.

and here's me using msn messenger in xp in ubuntu:

[img]http://www.hawkwinds.com/tickle/msninxpinubuntu.jpg[/img]


Now my only problem is... I have to start over again!!! 

There's not enough room on here for installing UT.

---

### Post by Caboto on 2005-11-08
[QUOTE=BLTicklemonster][...]
There's not enough room on here for installing UT.[/QUOTE]
I hope you don't mean Unreal Tournament. As far as I know, there's no 3D Acceleration (which already mentioned someone).

---

### Post by Wombley on 2005-11-08
[QUOTE=mapman]You can install the tools by entering into the OS through VMPlayer then accessing the ide1 drive or in my case it was D: drive, then proceed from there to install it.

I wasn't able to increase the resolution using these steps after installing the tools however....let me know how you do if you can though.  Thanks.;)[/QUOTE]

Force the display adaptor to install - choose the "select from list" option after selecting install driver for it in device manager, then the "have disk" option, then show it the directory on the disk, select vmware driver and ignore the warnings... :)

---

### Post by BLTicklemonster on 2005-11-08
[QUOTE=Caboto]I hope you don't mean Unreal Tournament. As far as I know, there's no 3D Acceleration (which already mentioned someone).[/QUOTE]

Yeah. But I was hoping against hope that the editor would work in XP/vmware.

I suppose it's time to see how one daul boots with two drives.

---

### Post by twowheeler on 2005-11-08
In case it helps anyone here, this is my fully functional Windows2000Pro.vmx file:

> 
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "Windows2000Pro.vmdk"
memsize = "192"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "cdrom-raw"
ide1:0.autodetect = "TRUE"
floppy0.fileName = "/dev/fd0"
floppy0.startConnected = "FALSE"
ethernet0.present = "TRUE"
usb.present = "FALSE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows 2000 Pro"
guestOS = "win2000pro"
nvram = "Windows2000Pro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d c3 67 77 20 86 54-d0 ec 04 8b aa ce 79 73"
uuid.bios = "56 4d c3 67 77 20 86 54-d0 ec 04 8b aa ce 79 73"
ethernet0.generatedAddress = "00:0c:29:ce:79:73"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = "Windows2000Pro.vmss"
tools.remindInstall = "FALSE"
fileSearchPath = "/home/dan/vmware/Windows2000;."


---

### Post by BLTicklemonster on 2005-11-08
***displayName = "Winbuntu 2000 Pro"***


... tempting..

---

### Post by mapman on 2005-11-08
[QUOTE=Wombley]Force the display adaptor to install - choose the "select from list" option after selecting install driver for it in device manager, then the "have disk" option, then show it the directory on the disk, select vmware driver and ignore the warnings... :)[/QUOTE]


:smile: Thanks Mr.Wombley.  It worked as you said it would.:cool:

---

### Post by Wombley on 2005-11-08
[QUOTE=Caboto]I hope you don't mean Unreal Tournament. As far as I know, there's no 3D Acceleration (which already mentioned someone).[/QUOTE]

There is actually an (experimental) option for this - see [http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d.html]("http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d.html"). However its still marked as experimental, and I'm not sure how it'd work with the version of vmware tools we've been using...

---

### Post by Caboto on 2005-11-08
[QUOTE=Wombley]There is actually an (experimental) option for this - see [http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d.html]("http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d.html"). However its still marked as experimental, and I'm not sure how it'd work with the version of vmware tools we've been using...[/QUOTE]
Yes. But like the text (and you) said, it's for the workstation. That could work eg. for the UnrealED, but probably it won't be really good for playing (new) 3D-Games.

---

### Post by BLTicklemonster on 2005-11-08
[QUOTE=Caboto]Yes. But like the text (and you) said, it's for the workstation. That could work eg. for the UnrealED, but probably it won't be really good for playing (new) 3D-Games.[/QUOTE]
Shoot, ut plays great in linux, I just need to be able to map in the editor. I'll check it out after I redo all this with like twice the space on the virtual drive.

---

### Post by BLTicklemonster on 2005-11-08
Setting up a 10 gig virtual drive, and going at it again. Thank you so much for putting up with me and being so helpful you all. My apologies to everyone but... bah, yeah, him too.

Now to get it installed again, and try to install that 3d thing.

Huh, I wonder how well it networks. I can just share a cdrom from one of the other machines, and install UT from there instead of waiting for the files I uploaded to download from ftp.... 

First things first, I gotta get it running first, lol.


HECK YEAH, it worked. Instead of having to have floppies, just (yeah, I know, why go to the trouble of making an iso) when it says it can't find a bootable disk, click on the cdrom icon, and it boots from the cd. Now if I were a smart man, I'd figure out how to make the thing boot from it already, but well, I think I already blew any credibility I'd have in that department. Installing now.


*edit:

for some reason, if I try to change the size from 2 gig to a larger size, and change both values, it messes up. I wanted a 10 gig, because I'm a hog, so I tried this and it worked:

```
qemu-img create -f vmdk WindowsXPPro.vmdk 10G Formating 'WindowsXPPro.vmdk', fmt=vmdk
```


```
bill@ubuntumonster:~/WindowsXPPro$ qemu-img create -f vmdk WindowsXPPro.vmdk 10G Formating 'WindowsXPPro.vmdk', fmt=vmdk
Formating 'WindowsXPPro.vmdk', fmt=vmdk, size=10485760 kB
bill@ubuntumonster:~/WindowsXPPro$

```

---

### Post by twowheeler on 2005-11-08
> **BLTicklemonster]
```
qemu-img create -f vmdk WindowsXPPro.vmdk 10G Formating 'WindowsXPPro.vmdk', fmt=vmdk
```
[/QUOTE]

I'm sorry to have to repeat old information, but it was explained previously in this thread that the command ends after the "10G".   The rest is output mistakenly included in the quoted text.  At best, it will be ignored said:**
>  -- that would be "2G" or "10G" or whatever size you want.

[QUOTE]QEMU-IMG(1)                                                        QEMU-IMG(1)

NAME
       qemu-img - QEMU disk image utility

SYNOPSIS
       usage: qemu-img command [command options]

OPTIONS
       The following commands are supported:

       create [-e] [-b base_image] [-f fmt] filename [size]
       commit [-f fmt] filename
       convert [-c] [-e] [-f fmt] filename [-O output_fmt] output_filename
       info [-f fmt] filename

I just don't want more people to be confused about this.

---

### Post by BLTicklemonster on 2005-11-08
Thanks Two, but I stay confused anyway.

I installed the vmware video drivers the slacker way.

I installed winace, and extracted the contents of the iso and installed from there.

Oh, and check this out:

[img]http://www.hawkwinds.com/tickle/unrealedinubuntu.jpg[/img]


I can finally kick the windows out now. I have no reason to keep it on the other drive.

THANKS TO YOU ALL FOR YOUR HELP.

---

### Post by Snorrie on 2005-11-09
Did someone tried this for windows 98? I wanted to install that but the floppy-thingy is not clear to me. What do I have to put on that? or make it boot from what file from a normal win-98-boot-floppy?

Thnx in advance,

Snorrie

---

### Post by Wombley on 2005-11-09
[QUOTE=Snorrie]Did someone tried this for windows 98? I wanted to install that but the floppy-thingy is not clear to me. What do I have to put on that? or make it boot from what file from a normal win-98-boot-floppy?

Thnx in advance,

Snorrie[/QUOTE]

You should be able to install straight from the windows 98 CD, although I haven't tried it myself. The floppys aren't really required unless you have a bad CD image.

---

### Post by yabbadabbadont on 2005-11-09
My Win98SE full install CD wasn't bootable.  The CD came with a win98 boot floppy.  I just booted from the floppy and then ran the setup on the CD.  I did this using the evaluation version of vmware workstation though.  I used the eval version to create base installs of win98, win2k, and winXP.  I created copies of these files and then installed my other software in the copies.  That way I always have a clean install from which to start if I want to try something different.  I use vmplayer with the images though.

There is a tool on the CD to create the boot disk, but is has to be run from DOS  (might work with Wine, I'll try it in a little while and see what happens).  It is in the tools/mtsutil/fat32ebd directory.  There is a text file that explains how to create the disk.

EDIT: I couldn't get it to work with Wine, it would probably work with either DosEmu or DosBox though.

For those who are interested, I found this link with some useful information about the contents of the vmx files.  [http://blog.lorenzoferrara.net/pivot/entry.php?id=73#body](http://blog.lorenzoferrara.net/pivot/entry.php?id=73#body)

---

### Post by yabbadabbadont on 2005-11-09
[QUOTE=Snorrie]Did someone tried this for windows 98? I wanted to install that but the floppy-thingy is not clear to me. What do I have to put on that? or make it boot from what file from a normal win-98-boot-floppy?

Thnx in advance,

Snorrie[/QUOTE]

I don't think that I answered the question you asked with my previous post.  If you have the Windows 98 boot floppy, then you can install win98 without creating the CD and floppy images.  I have just done this using qemu-img and vmplayer to be sure that it can be done.  (it took a few tries to find the right settings).  Follow the original post's instructions on creating the hard drive image file using qemu-img.  I called my image file w98.vmdk.  Here is the vmx file that I used to install win98.  ```
#!/usr/bin/vmplayer
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "w98.vmdk"
ide0:0.redo = ""
memsize = "128"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "/dev/hdc"
ide1:0.deviceType = "atapi-cdrom"
ide1:0.startConnected = "TRUE"
floppy0.fileName = "/dev/fd0"
floppy0.startConnected = "True"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows 98 test image"
guestOS = "win98"
nvram = "w98.nvram"
MemTrimRate = "-1"
uuid.location = "56 4d 4e f4 6e 1c 68 77-97 68 c5 8f 84 8d 00 c6"
uuid.bios = "56 4d 4e f4 6e 1c 68 77-97 68 c5 8f 84 8d 00 c6"
tools.syncTime = "FALSE"
uuid.action = "create"
checkpoint.vmState = "w98.vmss"
tools.remindInstall = "FALSE"
ethernet0.addressType = "generated"
ethernet0.generatedAddress = "00:0c:29:8d:00:c6"
ethernet0.generatedAddressOffset = "0"

```

If you called your image file something other than w98, then change w98 to whatever you used everywhere it appears in this file.  Also, you will need to modify the ide1:0.fileName line to point to the device for your cdrom.  In my case it is /dev/hdc, you will need to change it to the correct value for your system.  Once you have done all that, insert your boot floppy and win98 CD.  Run vmplayer using the vmx file you have just created.  You should see the boot floppy start up and then complain about the hard drive not being partitioned or formatted.  Use fdisk to create a partition.  I just created one for the whole virtual disk.  You will have to restart the virtual machine now.  From the vmplayer menu, choose Player->Troubleshoot->Reset.  This will reboot the virtual machine.  Once the floppy has booted again, format the virtual disk you just partitioned.  Now you can run the setup.exe program off of the win98 CD and do a normal win98 setup.


I know that I have repeated many of the instructions from earlier posts, but I just wanted to be clear on the steps I took to install win98 in my virtual machine.

---

### Post by Snorrie on 2005-11-10
Oh yeah! it worked! :D

It's a shame though that it (win 98 SE) is terribly slow on my laptop (750mhz, 512mb)

Is there a possibility to make it quicker with some tools?

thnx,

Snorrie

---

### Post by Wombley on 2005-11-10
Have you installed the VMWare tools mentioned in previous posts? These should work with Windows 98 (theres a win9x folder for the graphics drivers, and its one of VMWare's supported OS's), and at least on Windows 2000 I found they made it run smoother.

---

### Post by BLTicklemonster on 2005-11-10
So I redid my hard drive to 10 gig and all went well. I am amazed that XP is faster like this than it ever was normally. 


Now for some tough questions:

How do I migrate files between the two? Between the xp vd, and linux?

Can I put a whole hard drive in vm? I have xp on a drive, and it's got like 6 ggs of stuff that I can do without, but sure could use. Can I point vmware player to that drive and run the xp off of it?

---

### Post by ranf on 2005-11-10
[QUOTE=BLTicklemonster]
How do I migrate files between the two? Between the xp vd, and linux?
[/QUOTE]
Samba? Should be lightning fast.
[QUOTE=BLTicklemonster]
Can I put a whole hard drive in vm? I have xp on a drive, and it's got like 6 ggs of stuff that I can do without, but sure could use. Can I point vmware player to that drive and run the xp off of it?[/QUOTE]
I have no idea if that can be achieved.

---

### Post by BLTicklemonster on 2005-11-10
Thanks ranf, I tried that last night, I could get smbclient to show me useful stuff like smbclient -D| does neat stuff, but well, nothing happened when I did it.

I also tried typing in firefox:

smb://localhost:10000

and nothing happened.

I can't (of course I can't because it's probably staring me in the face) find anything useful (as in it says, because you are stupid, mr ticklemonster, we'll draw you a picture, please chose your favorite color of crayon) that gave me even a hint as to how to go from point a to point b. Perhaps my googling skills could use some tweaking...

BUT, I'm not going to rant and rave this time. Self depricating humor maybe, but no ranting.

---

### Post by jackmacokc on 2005-11-10
I keep getting this error:
```
The network bridge on device /dev/vmnet0 is temporarily down because the bridged Ethernet interface is down.  The virtual machine may not be able to communicate with the host or with other machines on your network.
```

Any ideas? Or should this simply be ignored.

---

### Post by Caboto on 2005-11-10
I've tried to transfer files between the Guest OS (WinXP) and my Host OS with no real success.
The first method I've tried was to just drag'n'drop or Copy&Paste. The website says, the Player can handle this (from Linux to Windows and vice versa). It didn't work, of course..
Then i've installed Samba and shared some folders. Then I switch my Ethernet Card to "Host-only" and tried to find these folders with no success. But I did indeed found my PC. It asked for a User/PW, but didn't accept anything...

I've googled a little bit and found out, that the VMWare Workstation can have Shared Folder (like mounting partitions), but that this functionality was removed due to security reasons (when you use an image from someone else, you can't see what things are mounted automatically).

At the moment I'm using my Apache Webserver for transfering files. I've set up a domain at dyndns.org and using this. It's "normal" network speed, but a bit complicated...
I wish, I could just mount my other FAT32 partitions.


Edit:
There's a discussion for this subject in the VMWare Community Boards right [here](http://www.vmware.com/community/thread.jspa?threadID=24795&tstart=0&messageID=300818).

---

### Post by ranf on 2005-11-10
[QUOTE=BLTicklemonster]
I also tried typing in firefox:
smb://localhost:10000
[/QUOTE]
What is that supposed to do? 

Start here [https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29](https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29)
and search this forum for "samba". There should be a bunch of threads.

---

### Post by BLTicklemonster on 2005-11-10
It is a simple command line thing that makes people scratch their heads. Try it on some unsuspecting person sometime. 

Other than that, it was supposed to bring up something about my computer so I could set the xp drive to have a letter and be shared. Or so I was told.

---

### Post by BLTicklemonster on 2005-11-10
I just learned something. If you are running on an athlon machine, and find out about k7 kernel after doing this with vmware, and change, you will have to reinstall vmware. nice. lmao.

---

### Post by BLTicklemonster on 2005-11-12
If the player won't launch, where can I find a log telling me what happened? I see nothing generated presently, and the player will not launch. (perhaps it won't launch because this is the first time I've tried to run with a drive slaved?)


*edit:

Nope, that's not it. Why do I keep loosing the ability to launch player? And when I do, what can I do to get it back? I've tried looking over the vmx file, but it's identical to the one I made in the first place. And there's no log that I can find.

---

### Post by BLTicklemonster on 2005-11-13
> **dryandplain]This guide will allow you to install Windows XP or 2000 solely with the VMWare Player. For the uninitiated, VMWare released a free application that allows users to run, but not create virtual machines. Using QEMU, we will create an environment suitable for use with the player.

As a side-note, I'd like to point out that VMWare makes quality software. If you require additional functionality, consider upgrading to Workstation. For those curious, these actions are condoned by the developers as per this quote:

"We&#8217 said:**
> this page[/URL]. Most of my instructions will be shamelessly ripped from [this lovely tutorial]("http://www.ubuntuforums.org/showthread.php?t=65638"). Fire up a root terminal and do:

```
sudo apt-get install build-essential
uname -r
sudo apt-get install linux-headers-'kernel version'
sudo apt-get install gcc-3.4
sudo apt-get install g++-3.4
```

Now that the initial dependencies have been met, let's continue.

```
sudo tar xvzf VMware-player-1.0.0-16981.tar.gz  [COLOR="Red"]be aware that the version number may change[/COLOR]
cd vmware-player-distrib
CC=/usr/bin/gcc-3.4
export CC=/usr/bin/gcc-3.4
sudo ./vmware-install.pl
```

The installer has an unusually high number of prompts, all of which can be answered the default "yes" to by hitting enter. After hitting enter a few dozen times and agreeing to the license, everything should install successfully. If you're having problems installing the actual player, that other guy might be more qualified to diagnose it than I am. Moving along...

There are two components to a virtual machine, the hard drive image and a text file that VMWare interprets. First, we'll create an image with QEMU.

I know this sounds a little odd, but I couldn't get the QEMU command used to generate the disk working from the Linux port. Fortunately, the utility works fine with the Windows port under Wine. I can't really bothered to delve into the specifics of installing Wine other than suggesting:

```
sudo apt-get install wine
```

Then download and install the [Windows version of QEMU]("http://free.oszoo.org/ftp/qemu/win32/release/QemuInstall-0.7.2.exe") if that does now work, then get it [here](http://daimon55.free.fr/qemu/QemuInstall-0.7.2.exe) (make sure you install it :) . Create a folder in /home/yourname and name it either WindowsXPPro or Windows2000Pro, and  in the terminal go to it:

```
cd /home/yourname/folder you created
```

Then execute qemu from a command line as follows:

```
 wine "c:\Program Files\Qemu\qemu-img.exe" create -f vmdk WindowsXPPro.vmdk 2G Formating 'WindowsXPPro.vmdk', fmt=vmdk

```

(the size driver that makes is 2 gigs, if you want more, change from 2G to whatever size you want)

This will generate a 320k file which is a usable blank drive. Create a new folder to contain our files and name this guy either WindowsXPPro.vmdx or Windows2000Pro.vmdx accordingly.

You now have the choice to install XP or 2000. On my 1.2ghz/512mb system Windows 2000 runs considerably more responsively; your choice. As per the other tutorial, we should be able to insert our CD and go after the following. But in my case, neither my bootable XP or 2000 CD had any interest in well, booting. I'd suspect I'm not the only one with this concern, so we'll play with ISO images instead. [COLOR="Red"]If you want to install from a cd rom, then ignore this part.[/COLOR]

```
sudo apt-get install gnomebaker
```

After inserting your original Windows disc, load Gnomebaker, choose "Copy Data CD," and tick the "Create ISO only" box. Save the resulting ISO as either WindowsXPPro.iso or Windows2000Pro.iso to the folder we just created. If the processes ever freezes 99%, feel free to "killall gnomebaker" without concern.

Unfortunately, our ISO image will not have the bootable sector intact. We'll instead boot from a series of floppy images. My Windows 2000 disc included them in a "bootdisk" folder, whereas XP did not. For 2000, copy the four img files from it to our created folder.

With XP, you'll need some additional nonsense. Hunt down an appropriate set from Microsoft for your version of XP, and do the following:

```
sudo apt-get install cabextract
cabextract 'nameofarchive.exe' -d 'our working directory'
```

Deleted the non-img extracted files.
[COLOR="Red"]
Okay, you can start paying attention again if you are wanting to boot from a cd.[/COLOR]

Now that we have a matching ISO and floppy set, we're ready to proceed with installation. Paste one of the following to a text editor (gedit/leafpad) and save it as either WindowsXPPro.vmx or Windows2000Pro.vmx to our directory:

Windows XP from iso:

```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "WindowsXPPro.vmdk"
memsize = "192"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "WindowsXPPro.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"
floppy0.fileType = "file"
floppy0.fileName = "cdboot1.img"
floppy0.startConnected = "True"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows XP Pro"
guestOS = "winxppro"
nvram = "WindowsXPPro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
uuid.bios = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
ethernet0.generatedAddress = "00:0c:29:4c:23:7b"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = "WindowsXPPro.vmss"
tools.remindInstall = "TRUE"
```

Windows XP from cd:

```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "WindowsXPPro.vmdk"
memsize = "192"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "atapi-cdrom"
ide1:0.autodetect = "TRUE"
floppy0.startConnected = "False"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows XP Pro"
guestOS = "winxppro"
nvram = "WindowsXPPro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d 86 fc d2 c6 27 b7-7d 0a dc c4 9f 36 b9 3f"
uuid.bios = "56 4d 86 fc d2 c6 27 b7-7d 0a dc c4 9f 36 b9 3f"
ethernet0.generatedAddress = "00:0c:29:36:b9:3f"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = "WindowsXPPro.vmss"
tools.remindInstall = "TRUE"
```

Windows 2000:

```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "Windows2000Pro.vmdk"
memsize = "192"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "Windows2000Pro.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"
floppy0.fileType = "file"
floppy0.fileName = "CDBOOT1.IMG"
floppy0.startConnected = "True"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows 2000 Pro"
guestOS = "win2000pro"
nvram = "Windows2000Pro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
uuid.bios = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
ethernet0.generatedAddress = "00:0c:29:4c:23:7b"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = "Windows2000Pro.vmss"
tools.remindInstall = "TRUE"
```

Double click on the resulting file, and Windows should start to install. The only screwiness left at this point is that we'll need to swap floppy images. When prompted, click on the floppy icon to "eject" the drive. In Nautilus, rename cdboot1.img to cdboot01.img and cdboot2.img to cdboot1.img, then click the floppy icon again to continue. It may sound a little strange, but you're essentially renaming the images to match that of the first file when it wants it. You'll get the hang of it, promise.

Once the floppies have done their thing, the ISO will take over and Windows will install normally.

Sorry about the length of this. If I had web hosting, I could've posted many of these files and shaved off a few steps. I'll try my best to answer any questions that may come up, but concede that my level of Linux know-how is only intermediate.

[Here's a screeny for encouragement]("http://i24.photobucket.com/albums/c35/dryandplain/ps8.png")! :D

Take care,
-Kyle

redone a bit

---

### Post by BLTicklemonster on 2005-11-14
question:

If I were to do all the steps up until the part where I click the vmx file to install, then uploaded the folder I made with the vmdk and vmx files in them, downloaded them on another machine, installed vmware player, and double clicked on the vmx file, would it work, even without wine or qemu? I'd think it would, but I don't know exactly whether or not either of them come into play at this point in things.

oh, and I just went through the whole thing again from scratch here on a different machine that is a fresh ubuntu install, and corrected some errors in case anyone tried that I just posted up there and it didn't work... which it wouldn't have, Ron, so pardon me, lol.

---

### Post by drummer on 2005-11-14
the use of wine and qemu is only to create the disk image for vmware (.vmdk file) so once that's done, vmware doesn't use qine or qemu at all, they're purely for the initial setup.

---

### Post by drummer on 2005-11-14
Also, how can I install the vmware tools svga drivers in a Windows XP Pro guest? I installed as per the windows.iso thing, but got errors saying i had to install them manually. I then installed them manually, using the add new hardware wizard as per previous posts, but the drivers seem to be broken. I used the drivers in the win2k folder in windows.iso as there wasn't one for xp. Can anyone help here, the mouse is very laggy and I'd like these drivers to work.

I've attached a screenshot of the device manager. the red arrow marks what i installed and the question mark is something else but i'm not sure what it is. I'll also note that I could up the resolution to 1280*1024 and higher from the clean xp install, if that's any use.

---

### Post by mingus on 2005-11-16
Excellent thread . . . so just fwiw, thought I'd throw in my two cents after installing on two machines . . .

Re post #83, unable to get the display to work - note the video controller that Windows plug-n-pray has detected and for which there is no driver.  That is blocking the display adapter driver from loading.  Uninstall the controller and then reinstall as a new display adapter the vmware svga driver.

Re networking, sharing files, samba, etc. . . . my systems are all on a LAN, one of the two with vmplayer uses wireless, there is also a printer, all hung off a router.   For the wireless system, I found I could not simply specify NAT in the player; could not find the router's DHCP server.  So I config'd vmplayer vmnet0 to wlan0, vmnet8 as NAT, and vmnet1 as host (same as wireline system except vmnet0 there is eth0).  The wireless system needed to be assigned a static IP.  With Samba installed, all the systems can see one another as normal (smb.conf is configured with "netbios-name = <system-name>" and "security = share"). 

Only -minor - hiccup I've got is that I had to change the vmx file in order for the CD device to be recognized but now when a CD is placed in the drive *both* Ubuntu and Windows open it.    :)

So far all is working well.  On my SuSE system I have Xen but have not played with it yet, anyone given that a try for comparison?  Seems to me that virtualization is *the* ticket to putting Windows permanently in the back seat.

---

### Post by BLTicklemonster on 2005-11-16
Reckon how a fella would get a logitech moust to have the forward and back buttons navigate in there?

---

### Post by drummer on 2005-11-16
mingus: thanks for that, but i just deleted the xp install i did :p. I got the drivers working in a windows 2000 install which I like better than xp anyway, much less confusing. XP tries to do to much for you imo, and the settings are easier to find for me in 2k.

Although I have yet to get my tv tuner working. I installed the drivers, but the actual card wasn't detected and I can't see it in the hardware manager.. any ideas?

---

### Post by mingus on 2005-11-16
Re:  Mouse and Tuner . . . sorry, I'm still new to virtualization as well.  The vmplayer documentation only deals with installation.  I would look at the workstation manual to understand which kinds of drivers can be installed, what the limitations are in the built-in virtual machines's hardware layer, etc.  I don't know yet in what ways, if any, the hardware layer differs between the workstation and the player.

---

### Post by yabbadabbadont on 2005-11-20
Drummer: You would have to check the VMware website, but I don't think that their virtual machine emulates a tv tuner.  If their virtual machine doesn't emulate the hardware, then installing drivers for it inside the VM won't do any good.  You should be able to use it in Ubuntu though.  Are you having trouble with it in Ubuntu, or did you just want to play with it in Windows?

---

### Post by drummer on 2005-11-20
I can watch tv in ubuntu fine, but have had problems recording it. I should try again now that I'm using Breezy, but in Hoary programs other than tvtime couldn't see the video stream.

---

### Post by Draaku on 2005-11-21
Hi, I installed VMware following this guide. But I do not need it or want it anylonger. How would I remove it completely from my system?

---

### Post by ranf on 2005-11-21
[QUOTE=Draaku]Hi, I installed VMware following this guide. But I do not need it or want it anylonger. How would I remove it completely from my system?[/QUOTE]
Type `vm' in a terminal, then hit Tab twice.

---

### Post by Draaku on 2005-11-21
[QUOTE=ranf]Type `vm' in a terminal, then hit Tab twice.[/QUOTE]

ok, it just lists some files, is there a command i type to verify it has been removed? I also found this file in /usr/bin/vmware-uninstall.pl

This stepped me through the uninstall and stated it was removed. thanks for the help.
I still would like to know what this command does? `vm'

---

### Post by thermopyl on 2005-11-21
SUperb HOWTO guys!

Followed all the instructions to the letter and up and running first time (with sound, networking & a good resolution too!) :D 

However I now need to expand my image size from the original 2G..can you tell me how I can do this without destroying the work I have done so far?

Many thanks

---

### Post by ranf on 2005-11-22
[QUOTE=Draaku]
I still would like to know what this command does? `vm'[/QUOTE]
There is no command named vm. I just told you to type the first two letters of vmware and then use the auto command completion of the bash (that's what runs the terminal) to find out which programs have vmware in their name.

Clearer now?

---

### Post by sumanjay on 2005-11-22
[QUOTE=sethmahoney]Thanks a lot!  Works great, except, is it normal for the part of the install where Windows detects and installs all your hardware to take a REALLY long time?[/QUOTE]

I'm experiencing the same problem. It's been stuck at the "detecting and installing devices" screen for over an hour now! How long is it supposed to take? Should I try to reset the virtual system & start over?

Trying to install Windows 2000 on an AMD Athlon 1700XP with 1 GB RAM and a 10GB virtual partition.

---

### Post by drummer on 2005-11-22
I had the same problem with Windows 2000, it was stuck on the same screen for ages and didn't move (I left it running overnight). I read somewhere that it was a problem with VMWare being too smart with it's USB detection, so I removed the lines about USB in the .vmx file and restarted the installation. It worked fine after that and I'm pretty sure that that was the actual problem. I still have USB support, VMWare just added some lines back to the .vmx.

---

### Post by sumanjay on 2005-11-22
Thanks for that. I did the same and the installation has completed. However, when I try to install the VGA driver (VMware tools), the Hardware Wizard claims that there is no driver information present in that location. I am pointing the wizard to  the correct location - the Video driver in the CDROM image (win.iso) that I downloaded from VMware's website. I would really like to be able to increase the resolution on my virtual machine, besides making it full screen on my current 1280x1024 desktop.

---

### Post by mdbarton on 2005-11-23
I'm considering giving this a go.  Has anyone used VMWare to run MS Outlook and ActiveSync with a PocketPC?  Evolution is rubbish (sorry, but it is just not there yet) and SynCE just does not work properly....

Would an alternative be to boot Win XP, install VMWAre workstation evaluation copy, create a WinXP image, then run it in VMare player under Ubuntu?

---

### Post by thermopyl on 2005-11-23
[QUOTE=mdbarton]I'm considering giving this a go.  Has anyone used VMWare to run MS Outlook and ActiveSync with a PocketPC?  Evolution is rubbish (sorry, but it is just not there yet) and SynCE just does not work properly....[/QUOTE]

Hi
This is precisely why I followed this thread. I can confirm that active sync with my Ipaq has worked fine through VMWare. I have not tried MSOutlook yet, but as I can use Avantgo and install new apps I am not anticipating any probs.

---

### Post by siorai on 2005-11-30
I'm at a bit of a loss here. I've installed vmware and it looks like everything is working fine. I'm using the .iso and floopy images to install XP Pro. It goes fine until it goes to examine the disks right before copying the files over for the install, then I get this:

```
Windows XP Professional Setup
------------------------------

The following value in the .SIF file used by Setup is
corrupted or missing:

Value 0 on the line in section [SourceDisksFiles]
with key "SP2.cab."

Setup cannot continue. To quit Setup, press F3.
```

I feel like I'm about this: >< close to getting it.

---

### Post by siorai on 2005-12-02
Well I got my problems sorted out. I think it stemmed from the Windows discs that I was using were both slipstreamed with the Service Packs into them. I borrowed a proper disc from work, followed the instructions on how to boot from the cd and booyaa! It worked! :D Now I can finally ditch that Windows install and quit dual booting. 

Thank you to everyone in the thread for all the info.

---

### Post by siorai on 2005-12-02
Oh yeah, one question though. Is it possible to increase the size fo the virtual drive Windows is installed on, or do I have to simply reinstall, creating the virtual drive larger first?

---

### Post by mdbarton on 2005-12-02
[QUOTE=mdbarton]I'm considering giving this a go.  Has anyone used VMWare to run MS Outlook and ActiveSync with a PocketPC?  Evolution is rubbish (sorry, but it is just not there yet) and SynCE just does not work properly....

Would an alternative be to boot Win XP, install VMWAre workstation evaluation copy, create a WinXP image, then run it in VMare player under Ubuntu?[/QUOTE]

Now have it working (activesync and pocketpc) - and I created the WinXP image using a VMWare workstation evaluation copy on windows.  I have one or too niggles to sort out - if I get stuck will post them here.

Thanks for an excellent howto!

---

### Post by vtechstu on 2005-12-02
Hi,

When I run vmplayer <filename> in the terminal, this is printed right before vmware opens:

/usr/lib/vmware/bin/vmplayer: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
*** attempt to put segment in horiz list twice

It then opens.  Do I need to worry about this?  

Also, vmplayer began the install of windows, it loaded everything, and I pressed Enter, then it froze.  Now everytime I go start up vmware for windows, i just get a black screen with an unmoving cursor in the top left, with white lines from where the VM Logo used to be. 

Could anyone please help?  Thanks.

EDIT:  Fixed the second issue.  I went back and recreated the vmdk file and it worked.  I think something had gotten written to it.

---

### Post by ilmw on 2005-12-02
[QUOTE=siorai]Oh yeah, one question though. Is it possible to increase the size fo the virtual drive Windows is installed on, or do I have to simply reinstall, creating the virtual drive larger first?[/QUOTE]

See the example: 

vmware-vdiskmanager -x 36Gb myDisk.vmdk

This will increase the virtual disk size to 36G. It takes awhile though.

This works with vmware workstation. I don't know whether it works with vmware player or not.

It was said that this only increase the disk size, but won't change the the partition. So you need to use another tool to do it. I only have one partition so I did increase the virtual disk size by just running this command. See this page:
[click]("http://www.instant-tech.com/blogs/ctyler.nsf/d6plinks/CTYR-6CWMB4")

---

### Post by mdbarton on 2005-12-03
[QUOTE=vtechstu]Hi,

When I run vmplayer <filename> in the terminal, this is printed right before vmware opens:

/usr/lib/vmware/bin/vmplayer: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
*** attempt to put segment in horiz list twice

It then opens.  Do I need to worry about this?  
[/QUOTE]

I get the same message, but vmplayer doesn't run, I just get the command prompt again.  It will run if I ```
sudo vmplayer <filename>
```Are you running vmplayer as root or normal user?  Jest to see if it is exactly the same problem....

---

### Post by siorai on 2005-12-03
[QUOTE=ilmw]See the example: 

vmware-vdiskmanager -x 36Gb myDisk.vmdk

This will increase the virtual disk size to 36G. It takes awhile though.

This works with vmware workstation. I don't know whether it works with vmware player or not.

It was said that this only increase the disk size, but won't change the the partition. So you need to use another tool to do it. I only have one partition so I did increase the virtual disk size by just running this command. See this page:
[click]("http://www.instant-tech.com/blogs/ctyler.nsf/d6plinks/CTYR-6CWMB4")[/QUOTE]

Awesome. That worked perfectly with vmware player as well. Thanks.

---

### Post by vtechstu on 2005-12-03
Yes I ran sudo vmplayer Win.vmx  Message still there.  Also, I can't seem to run VMplayer any other way but through terminal.  Under Applications, it shows it loading, but then dissapears.  How do i naturally set it so it will run as non root? I think that might be it.  Thanks.

---

### Post by mdbarton on 2005-12-06
[QUOTE=vtechstu]How do i naturally set it so it will run as non root? [/QUOTE]

That's the question I have as well...:confused:

---

### Post by Joeak on 2005-12-07
Thanks for the tips!  Since qemu on Breezy is 0.7.0, the qemu-img command failed, but I downloaded 0.7.2 under Windows, created the vmdk files there, copied them over to Ubuntu, hacked the vmx file to not boot from floppy, pointed it to my ISO image, and I'm installing away!

---

### Post by DarkFlounder on 2005-12-09
Thanks for the howto.  Works great.  Took a little while to get the windows.iso file (wasn't available at the link listed earlier, had to look on p2p).  Works great now.  If only I can use 3d software on it (for testing Java3d applets I'm developing).  But I heard that could be coming in a future edition.

---

### Post by mdbarton on 2005-12-09
[QUOTE=mdbarton]I get the same message, but vmplayer doesn't run, I just get the command prompt again.  It will run if I ```
sudo vmplayer <filename>
```Are you running vmplayer as root or normal user?  Jest to see if it is exactly the same problem....[/QUOTE]

Has anyone got vmplayer running as a normal user - ie not as root?  Can anyone suggest what I need to change to run this as a normal user?

---

### Post by yabbadabbadont on 2005-12-10
Does the install create a vmware group in /etc/group ?  I know it does on other Linux distributions.  If so, make sure that your user is a member of that group.

Example:
id username
(list of groups displayed)

If vmware is not listed and is in /etc/group, then do:
sudo gpasswd -a username vmware

and see if it helps.

---

### Post by mdbarton on 2005-12-10
[QUOTE=yabbadabbadont]Does the install create a vmware group in /etc/group ?  I know it does on other Linux distributions.  If so, make sure that your user is a member of that group.

Example:
id username
(list of groups displayed)

If vmware is not listed and is in /etc/group, then do:
sudo gpasswd -a username vmware

and see if it helps.[/QUOTE]

Thanks for the reply, unfortunately a vmware group has not been created.  I did try adding one but it does not make a difference.  Do I need to change a setting to make vmplayer aware of the group?

---

### Post by mdbarton on 2005-12-10
fixed it!  Have a look at [http://www.vmware.com/community/thread.jspa?messageID=306128&#306128](http://www.vmware.com/community/thread.jspa?messageID=306128&#306128)

just opened a terminal did a chown -R username .vmware and now I can run vmplayer as non-root.
:p

---

### Post by BLTicklemonster on 2005-12-13
Just started vmware, and I was advised that there is an upgrade. ... um, is this going to bonk everything I have done?

---

### Post by dk_pa on 2005-12-14
It looks like the link to the VMWare tools (windows.iso) file was taken down.  Are the VMWare tools n/a anymore or can I get them somewhere else or someone send me them?

---

### Post by Remix_88 on 2005-12-14
I have found an alternate location for the current windows.iso.

[http://www.vmware.com/download/esx/esx2-16515update.html](http://www.vmware.com/download/esx/esx2-16515update.html)

Download the tar.gz file, extract it and then you will have the current windows.iso of VMWare Tools :-) I just installed it and it works fine.

---

### Post by twowheeler on 2005-12-15
Anyone else here having trouble with a cd burner under vmware player?  It is a pioneer DVR-A07 cd/dvd burner.  The software is win2000pro on vmplayer on hoary.  I installed the pioneer drivers in windows, but none of the programs using the burner work.  Nero says it can't identify the type of cd drive.  iTunes coughs up "The attempt to burn a disc has failed.  An unknown error has occurred (3410)."  

I am wondering if it needs scsi emulation on the drive.  I did a modprobe ide-scsi but it did not fix it.  The drive reads and burns perfectly in linux using graveman or similar.

I searched the vmware forums for clues but came up empty.  It must not be a common problem.  :( 

If you have a burner working, what are the settings in your .vmx file?

Thanx...

---

### Post by siorai on 2005-12-15
twowheeler, I've never had any problems with my burner in vmware. I've got a Pioneer DVR-109 and I'm running XP Pro in vmware. Sorry I can't really help, but here's my .vmx file to compare:

```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "WindowsXPPro.vmdk"
memsize = "192"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "cdrom-raw"
floppy0.startConnected = "False"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows XP Pro"
guestOS = "winxppro"
nvram = "WindowsXPPro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = ""
uuid.bios = ""
ethernet0.generatedAddress = ""
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = ""
tools.remindInstall = "FALSE"

ide1:0.autodetect = "TRUE"
```

---

### Post by BLTicklemonster on 2005-12-15
Fascinating. Does dvdshrink work in vmware? I'd never given it any thought.

---

### Post by raha on 2005-12-15
[QUOTE=mapman]:smile: Thanks Mr.Wombley.  It worked as you said it would.:cool:[/QUOTE]

Please somebody help me I cant download the window.iso file to install my 3D graphic.
I need VMWare tools.
Can somebody give it to me.

Thanks

---

### Post by siorai on 2005-12-15
[QUOTE=BLTicklemonster]Fascinating. Does dvdshrink work in vmware? I'd never given it any thought.[/QUOTE]

It works perfectly. I also use DVD Decrypter, Nero, and PSPVideo9 in vmware, all of which work great.

---

### Post by twowheeler on 2005-12-16
[QUOTE=siorai]twowheeler, I've never had any problems with my burner in vmware. I've got a Pioneer DVR-109 and I'm running XP Pro in vmware. Sorry I can't really help, but here's my .vmx file to compare:[/QUOTE]

Thanks siorai.  Also, are you accessing the drive as an ATAPI IDE device or through SCSI drivers?

Edit: I mean in ubuntu not windows.

Edit2: "never mind"  I got it.  The drive was in PIO mode.  The answer was in this thread :
 [http://www.vmware.com/community/thread.jspa?messageID=297033&#297033](http://www.vmware.com/community/thread.jspa?messageID=297033&#297033)

---

### Post by Chris Tucker on 2005-12-16
wow, this seems a lot easier here than where anyone mentioned it to me before, i shall try this when i get home from work... 
do USB devices work in VMware? cameras? disk drives?

---

### Post by siorai on 2005-12-16
[QUOTE=Chris Tucker]wow, this seems a lot easier here than where anyone mentioned it to me before, i shall try this when i get home from work... 
do USB devices work in VMware? cameras? disk drives?[/QUOTE]

Both my PSP and my secure digital card reader work fine. They popup as soon as they're connected or I put a card in.

---

### Post by Chris Tucker on 2005-12-16
awesome, i cant wait then
i could get started now, but id run out of battery power, and i dont have my windows discs here

---

### Post by siorai on 2005-12-16
[QUOTE=Chris Tucker]awesome, i cant wait then
i could get started now, but id run out of battery power, and i dont have my windows discs here[/QUOTE]

My one suggestion is to think ahead about how much space you want for your Windows install. I was shortsighted the first time and had to redo the whole thing. It's easy enough to have the VMWare XP access samba shares, but it's easier to just have enough room in the XP install to begin with.

---

### Post by Chris Tucker on 2005-12-16
yes, i figured id try it with at least 6 gigs

---

### Post by Chris Tucker on 2005-12-16
im booting directly from the CD and VMware closes at the network setup in hardway detection..
i am using wifi as my main connection, the config wizard for vmware created bridges for both my wlan0 and eth0

edit: about to try via ISO

---

### Post by Chris Tucker on 2005-12-16
another note: that was XP.
via ISO it did the same thing.
right now i am trying win2000
later ima try some other linux distros in there :D
long night + me = bored
bored + time = fiddling

---

### Post by dk_pa on 2005-12-17
I have to admit I am totally smitten by this software.  On my Athlon 2500 w/512 Megs of ram Windows 2000 runs nearly flawless.  I'll have to try to edit my vmx file to get it read my DVD burner and DVD rom and then I'll be totally set.  This was super easy to setup and just blows my mind that it can run as fast as it does.  Anway...good walkthrough and great software.  I would say anyone who needs a Windows App under Linux definitely go this route.

---

### Post by kenweill on 2005-12-17
Installing and running windowx xp inside Linux thru vmware player is great.
I can have a windows specific software installed in windows xp inside linux.

But what if i connect to the internet from Windows XP inside vmware?
Can I share that connection outside vmware? Or in the host(on the same machine)? 
Can I share that connection to the other workstations in my LAN?

Actually, thats my problem regarding the internet connection. The accelerator/drivers for my modem is a windows based only. The accelerator won't install and run using wine. The accelerators, Internet Page Accelerator, and Internet over Satellite Accelerator that comes with my modem is windows specific software.

---

### Post by putte30 on 2005-12-17
I have network issues to.. unable to astablish an Internet connection... Anyone knows ?

---

### Post by Chris Tucker on 2005-12-17
ok, ive tried win2000 via CD, winXPhome via CD, WinXP Pro via CD, winXP Pro ISO, and DamnSmall Linux, everything stops and either powers off the virtual machine or just stops when it hits network detection.

WinXP (all) virtual machine powers off abruptly

Win2000 (workstation) hardware detection dialog stops when bar is full. can still move the window around, move the mouse, but buttons are greyed out and system doesnt proceed with install.

DamnSmall Linux (bootable CD) virtual machine powers off abruptly at network detection


Any help?
I'll be trying reinstalling vmware player later today, and doing the network differently.

---

### Post by putte30 on 2005-12-17
Fixed my problem by adding the following line:

ethernet0.connectionType = "nat"

:D 

Now Internet works... next step would be to enable networksharing trough samba... any ideas?

---

### Post by Chris Tucker on 2005-12-17
sudo apt-get samba
man samba
google samba
search ubuntuforums samba

---

### Post by Chris Tucker on 2005-12-18
udpate: windows XP and 2000 AND 98 all stall either during or at the end of hardware detection! other linux's work just fine.. any ideas?

---

### Post by Juzz on 2005-12-19
[QUOTE=mingus]Excellent thread . . . so just fwiw, thought I'd throw in my two cents after installing on two machines . . .

Re post #83, unable to get the display to work - note the video controller that Windows plug-n-pray has detected and for which there is no driver.  That is blocking the display adapter driver from loading.  Uninstall the controller and then reinstall as a new display adapter the vmware svga driver.

Re networking, sharing files, samba, etc. . . . my systems are all on a LAN, one of the two with vmplayer uses wireless, there is also a printer, all hung off a router.   For the wireless system, I found I could not simply specify NAT in the player; could not find the router's DHCP server.  So I config'd vmplayer vmnet0 to wlan0, vmnet8 as NAT, and vmnet1 as host (same as wireline system except vmnet0 there is eth0).  The wireless system needed to be assigned a static IP.  With Samba installed, all the systems can see one another as normal (smb.conf is configured with "netbios-name = <system-name>" and "security = share"). 

Only -minor - hiccup I've got is that I had to change the vmx file in order for the CD device to be recognized but now when a CD is placed in the drive *both* Ubuntu and Windows open it.    :)

So far all is working well.  On my SuSE system I have Xen but have not played with it yet, anyone given that a try for comparison?  Seems to me that virtualization is *the* ticket to putting Windows permanently in the back seat.[/QUOTE]
What static IP did you give the wireless system - because my system is also having problems with the wireless ath0 net.

---

### Post by edemark on 2005-12-19
First of all i just wanted to say that this thread is really nice i could install winxp and everithing works fine but 3d graphics (i new it would not work, in advance)
It is really cool. I can only compare with qemu but vmware seems much more smooth than qemu and easyly connects usb devices.
Now I have a question. One of my friends lended me the install disks of his ibook g4. So my question is if it is possible to install os x on vmware and how to do so. And finally one more question how to install a linux inside vmplayer (i would like to try out some live cd-s etc.

thanks in advance

---

### Post by djjazzy on 2005-12-19
Just to add my 2 cents worth, this howto worked Gr8! I have a Latitude C640 notebook with 512MB RAM and Breezy, I'm running a virtual XP Pro machine with all WindowsUpdates, Symnatec AV and M$ Office 2k3, Outlook running with E2k3 profile. Had to set "Ethernet" to "Bridged" to get connectivity, have sound and reasonably sized screen. Going to try Cisco VPN client next. Thanks to all that contributed :p 

-Jeff

---

### Post by SHare on 2005-12-19
[QUOTE=Chris Tucker]ok, ive tried win2000 via CD, winXPhome via CD, WinXP Pro via CD, winXP Pro ISO, and DamnSmall Linux, everything stops and either powers off the virtual machine or just stops when it hits network detection.

WinXP (all) virtual machine powers off abruptly

Win2000 (workstation) hardware detection dialog stops when bar is full. can still move the window around, move the mouse, but buttons are greyed out and system doesnt proceed with install.

DamnSmall Linux (bootable CD) virtual machine powers off abruptly at network detection


Any help?
I'll be trying reinstalling vmware player later today, and doing the network differently.[/QUOTE]

I get the same, I have a RT2500 wireless card installed and when any win installation gets to hardware detection (usually network) it powers of the vm.  Any help appreciated.



edit
Just disabled the ethernet in the .vmx file and its installing far far quicker this time, will report back.

---

### Post by Wombley on 2005-12-19
I'm sorry but OS X won't work on vmware as it''s based on PowerPC, a completely different architechture to what vmware emulates (x86 - although I suppose it's *possible* it'll be able to in the future, as Apple is moving to x86). For now I think the only real option for this is [PearPC]("http://pearpc.sourceforge.net/"), although I'm not sure how well it works.

You install linux the same way you install windows - see the rest of this thread. If you look at the bottom of the VMWare window as it's booting up you'll see options for going into the BIOS - you'd probably want to do this and change the boot order to cdrom first if you're trying out lots of live cds.

[QUOTE=edemark]First of all i just wanted to say that this thread is really nice i could install winxp and everithing works fine but 3d graphics (i new it would not work, in advance)
It is really cool. I can only compare with qemu but vmware seems much more smooth than qemu and easyly connects usb devices.
Now I have a question. One of my friends lended me the install disks of his ibook g4. So my question is if it is possible to install os x on vmware and how to do so. And finally one more question how to install a linux inside vmplayer (i would like to try out some live cd-s etc.

thanks in advance[/QUOTE]

---

### Post by imagine on 2005-12-19
[QUOTE=Wombley][QUOTE=]Now I have a question. One of my friends lended me the install disks of his ibook g4. So my question is if it is possible to install os x on vmware and how to do so.[/QUOTE]
I'm sorry but OS X won't work on vmware as it''s based on PowerPC, a completely different architechture to what vmware emulates[/QUOTE]
To nitpick a bit: The reason why OS X won't work is because VMware is *no* emulator : ) It cannot emulate a processor which doesn't exist, it only creates virtual machines which can use the processor together at the same time. And with the upcoming virtualisation technologies Vanderpool (Intel) and Pacifica (AMD) this will get even better.

---

### Post by edemark on 2005-12-20
That is really sad that i will not be able to try out os x. :) Thanks anyway and thanks again for the thread :) which i used to set up xp. I now see why vmware is so good to my cpu "as it is not an emulator" so i do not mind that much that os x shall wait and there are possibilities (future) with the qemu (which is an emulator).

So thanks again for the thoughts

pd i have not used wine for creating the image file qemu did the trick and just one more thing new qemu is out have a look and you might not have to download wine (at least for this reason)

---

### Post by anil_robo on 2005-12-21
This is a great how-to, but unfortunately the main author has not updated the information he got from other users! I guess someone should take the initiative of writing a good, newbie-friendly how-to based on this one! Even someone like me should be able to trap windows XP in Ubuntu's cage so that it does not trouble me anymore (and still plays Diablo II) :)

---

### Post by Juzz on 2005-12-21
I was able to use my wireless connection by using this option:

ethernet0.connectionType = "nat"

I hope that this will help other ppl who have woes about their wireless connection.
I think that using that option in the vmx file should be standard for all - as far as I can tell that option just utilizes the network that is available to the host machine.

---

### Post by dryandplain on 2005-12-23
[QUOTE=anil_robo]This is a great how-to, but unfortunately the main author has not updated the information he got from other users! I guess someone should take the initiative of writing a good, newbie-friendly how-to based on this one! Even someone like me should be able to trap windows XP in Ubuntu's cage so that it does not trouble me anymore (and still plays Diablo II) :)[/QUOTE]
Sorry, I was actually discouraged that no one replied, only to return to a fifteen page post. If anyone would like to update with the various changes, I'll be happy to correct the original.

---

### Post by majkmil on 2005-12-24
Can vmware tools be installed in vmplayer? I read a previos post that says you can but I could not quite understand. If someone could walk me through it I would appreciate it .I am runnig XP in vmplayer in Breezy.  Thank You

---

### Post by BLTicklemonster on 2005-12-26
Odd. I tried running it, and it said time had run out. So I just downloaded the new one (hey thread author, you might want to edit your first post to reflece the change to: VMware-player-1.0.1-19317.tar.gz ) and installed it and it works fine, didn't have to change anything.

---

### Post by Gooks on 2005-12-26
Link is broken??

---

### Post by BLTicklemonster on 2005-12-26
[http://download3.vmware.com/software/vmplayer/VMware-player-1.0.1-19317.tar.gz](http://download3.vmware.com/software/vmplayer/VMware-player-1.0.1-19317.tar.gz)


[http://www.vmware.com/download/player/](http://www.vmware.com/download/player/)

---

### Post by Gooks on 2005-12-26
No the link to the Window thing.. Does anybody have the Windows version of QEMU.  So i can upload it to my webhost?

---

### Post by BLTicklemonster on 2005-12-27
[http://fabrice.bellard.free.fr/qemu/download.html](http://fabrice.bellard.free.fr/qemu/download.html) ??? That? (google the word qemu)

---

### Post by Chris Tucker on 2005-12-27
[QUOTE=Juzz]I was able to use my wireless connection by using this option:

ethernet0.connectionType = "nat"

I hope that this will help other ppl who have woes about their wireless connection.
I think that using that option in the vmx file should be standard for all - as far as I can tell that option just utilizes the network that is available to the host machine.[/QUOTE]


OMG!!
YEA!
That worked.. im soooo gratefull... now i can let relatives use real msn messenger and things.. off i go to install xp.. (only tried it with damnsmall linux so far, but that worked so seems like xp should work no prob)

---

### Post by BLTicklemonster on 2005-12-27
And I guess you can't set up to run an entire hard drive in Vmware player, huh? Sure would be nice to run my slaved XP at the drop of a hat.

---

### Post by mdbarton on 2005-12-28
I now get this message when loading a VM image: 

```
This product has expired.
Be sure that your host machine's date and time are set correctly.
There is a more recent version available at the VMware Web site: "http://www.vmware.com/info?id=4".
```

Is this related to the image or to VMPlayer?  Do I just follow the instructions on installing VMPlayer in this howto again?

---

### Post by Chris Tucker on 2005-12-28
[QUOTE=BLTicklemonster]And I guess you can't set up to run an entire hard drive in Vmware player, huh? Sure would be nice to run my slaved XP at the drop of a hat.[/QUOTE]
move your .vmdk to the drive, resize to fit snugly (easy way to resize posted somewhere recently in this thread..) and give your .vmx the new path! done!
depending on the size of the drive and how tightly you made your vmdk fit it, i dont recommend moving your .nvram too.

---

### Post by Chris Tucker on 2005-12-28
anyone up for fullscreen?
i havent finished googling yet but...
the vmware site shows how to set up a hotkey/hotkeycombo to switch between windowed and fullscreen, they mention it runs a lot faster in fullscreen, but they only show the WINDOWS way! using a config.ini in the docs and settings folder..

i'll keep fooling around and see if i get it, but if anyone beats me to it, please post the answer..  im on a laptop at 1280x800, and 1024x768 is even too large to view when i have my panels up and toolbar visable in vmware player..

---

### Post by mdbarton on 2005-12-29
[QUOTE=mdbarton]I now get this message when loading a VM image: 

```
This product has expired.
Be sure that your host machine's date and time are set correctly.
There is a more recent version available at the VMware Web site: "http://www.vmware.com/info?id=4".
```

Is this related to the image or to VMPlayer?  Do I just follow the instructions on installing VMPlayer in this howto again?[/QUOTE]

Seems that the beta versions of the player had an expiry date on them.  Just downloaded the latest 1.0.1 tar file and ran the following:

```
tar xvzf VMware-player-1.0.1-19317.tar.gz
cd vmware-player-distrib
export CC=/usr/bin/gcc-3.4
./vmware-install.pl

```

---

### Post by BLTicklemonster on 2005-12-29
[QUOTE=Chris Tucker]move your .vmdk to the drive, resize to fit snugly (easy way to resize posted somewhere recently in this thread..) and give your .vmx the new path! done!
depending on the size of the drive and how tightly you made your vmdk fit it, i dont recommend moving your .nvram too.[/QUOTE]
No way! Cool! Now I wonder if it being ntfs will be a problem? 

I'll check that out later, thanks!

---

### Post by jeffreyvergara.NET on 2005-12-29
how do you install vmware tools? that windows.iso thing?

---

### Post by Chris Tucker on 2005-12-29
mount it the same way you would your windows CD iso..

---

### Post by jeffreyvergara.NET on 2005-12-30
thanks alot!
I just wish it support 3d rendering for 3d games Y_Y

---

### Post by Chris Tucker on 2005-12-30
what really gets me.. is simple games that use DirectX even complain about no direct rendering in there, even with the 3D mods.. (error pops up at startup saying 3D device will start disconnected) yet when i reboot my computer into windows... they work! and yet there are no DRI drivers for my card in linux!!!! there should at least be a generic one that works. but nope, cant find that info ANYWHERE..
DRI is becoming really close to being the ONLY reason i still dualboot.. vmware can emulate anything i want to to in windows w/o 3d. and if i had DRI modules for my card for linux.. it'd do everything i want.. i suspect all the games i play on this notebook would run smooth in vmware, they arent real 3D games, they just complain about DRI. for real 3d games i run off to my fathers P4 with the nVidia GeForce 5200 FX :)

---

### Post by Chris Tucker on 2006-01-02
I set up VMware player on my fathers computer and just copied over the vmdk and settings file.. then i did the .vmx mod that allowed 3d accell, that computer can handel it. and glxinfo | grep direct shows that opengl sees the card right..
no popup saying that the 3d device is missing on virtual machine startup, tools off windows.iso are installed, but games complain about not having direct rendering... i tried reinstalling DirectX but no luck... what can i do? perhaps a simple OS reinstall on the virtual machine?

---

### Post by rjpa on 2006-01-02
Tired of installing Qemu just to create images? Well I have created some IDE images for you to use with the latest VMWare Player. Read the file below to find out how to get these disks:

[http://vmware.datasys.dk/disks/readme.txt](http://vmware.datasys.dk/disks/readme.txt)

Disks expands from 10 GB to 200 GB.

If you don't have a virtual machine yet, find/create one here:

[http://vmware.datasys.dk](http://vmware.datasys.dk)

---

### Post by ed_d on 2006-01-03
This is great! Now, how can I point my vmware to a specific network card? I wan to have one win2k machine on one network, and another on another network. If I can get this done, well then Ill be the happiest camper around....

---

### Post by flight_master on 2006-01-04
I just thought I'd say thanks - this tutorial helped me a lot. I'd also like to add my $0.02 :D 

For those of you, who try to boot into a CD/DVD-ROM, and can't get VmPlayer to read from the drive, this is for you.

You'll most likely have at least one other CD-RW /DVD-RW, etc drive in your computer. You'll need to unplug the IDE cable (yes, that thing wide cable) from all other CD/DVD/Combo drives. For some reason, VMplayer reads the wrong drive. I even had this problem after trying to un-mount my CD-RW drive.


Regards,
Christian

---

### Post by Mizzou_Engineer on 2006-01-07
How to get Linux QEMU to create the .vmdk file:

Install the Linux version of QEMU and issue the following command:

qemu-img create -f vmdk WindowsXPPro.vmdk 2G

It is the qemu-img command that creates the file. It works on my box!

---

### Post by encoe on 2006-01-09
thank you for the great howto. got it work on the first try :D

---

### Post by linkunderscore on 2006-01-09
[http://www.escapeportal.net/upload/2006-01-09-165351_1280x1024_scrot.png](http://www.escapeportal.net/upload/2006-01-09-165351_1280x1024_scrot.png)

---

### Post by linkunderscore on 2006-01-09
How do I start windows again the next time I want to use it? (after I restart or close the vmware window that it is in) What command do I use?

---

### Post by potrick on 2006-01-21
Windows is installing. I don't know why I'm doing this at 6:30 in the morning, I guess I'm not really sleeping tonight. Oh well, fun night out with friends topped off with random linux fun.

---

### Post by otey on 2006-01-23
Just in case somebody needs it... The VMware tools windows.iso file can be downloaded at [http://public.planetmirror.com/pub/vmware/software/support/?fl=](http://public.planetmirror.com/pub/vmware/software/support/?fl=)

---

### Post by Rouge8 on 2006-01-24
Is there anyway to make VMware detect my printer again?

It's a lexmark, and unfortunately the drivers don't work right for Linux, and I used ot have it working in VMware.

Did a clean install again, and now it isn't working.

Any advice?

---

### Post by hkl8324 on 2006-01-25
Why dont you just download the Vmware workstation trial version (30days trial)
Create a Virtual Machine, than dump the Vmware workstation and starting using Vmware player?

---

### Post by BLTicklemonster on 2006-01-25
[QUOTE=linkunderscore]How do I start windows again the next time I want to use it? (after I restart or close the vmware window that it is in) What command do I use?[/QUOTE]

Open, in your /home/yourname/ directory, the folder that holds everything you just made (AWXP?) and find the *.vmx file, and double click it. If it acts wierd (tries to open in text editor) then right click, and open with "VMWARE PLAYER".

That ought to do it.

---

### Post by thava on 2006-01-25
Hi guys

I try to install windows xp with sp2, with following this guide and its crash (Close the vmware window with installation) after network installations process in windows xp.

I also try installation from disc and with create a iso.
i used this Floppy Boot Install [http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=55820EDB-5039-4955-BCB7-4FED408EA73F](http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=55820EDB-5039-4955-BCB7-4FED408EA73F)

any idea?

/ Thava

---

### Post by mistab1034 on 2006-01-25
All I did to get a Windows install to use in VMWare Player was download the VMWare Workstation and use the 30 free trial to create a Windows Virtual Machine. Once the machine is created you can open it with VMWare Player just fine.

---

### Post by thava on 2006-01-26
Can anyone pls help me

Now i got install windows xp with vm-ware player.

i can go online with my windows xp.

My ubuntu ifconfig:
> thava@abirami ~
$ ifconfig
eth0      
Link encap:Ethernet  HWaddr 00:0E:35:11:14:6F
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe11:146f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22581 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:71619893 (68.3 MiB)  TX bytes:5519927 (5.2 MiB)
          Interrupt:11 Base address:0x2000 Memory:d0001000-d0001fff

lo        
Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:53082 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53082 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4820299 (4.5 MiB)  TX bytes:4820299 (4.5 MiB)

vmnet1    
Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:172.16.180.1  Bcast:172.16.180.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    
Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.100.1  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:

My windows ipconfig:
[IMG]http://thavarajah.dk/file/images/winip.png[/IMG]

my vmx file:
> #!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "WindowsXPPro.vmdk"
memsize = "192"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "atapi-cdrom"
ide1:0.autodetect = "TRUE"
floppy0.startConnected = "False"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows XP Pro"
guestOS = "winxppro"
nvram = "WindowsXPPro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d 66 1a 93 3c d2 20-cd f5 73 2c 13 45 d5 57"
uuid.bios = "56 4d 66 1a 93 3c d2 20-cd f5 73 2c 13 45 d5 57"
ethernet0.generatedAddress = "00:0c:29:45:d5:57"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = ""
tools.remindInstall = "TRUE"

ethernet0.connectionType = "nat"



can anyone tell me, why I can't go online with my windows?
thanks for reading!

/ Thava

---

### Post by RaptorRaider on 2006-01-28
Shouldn't "Default Gateway" be "10.0.0.2"?

Link to screenshot in the startpost is dead BTW.

---

### Post by Pizza the Hutt on 2006-02-18
I don't understand the following::confused: 
> With XP, you'll need some additional nonsense. Hunt down an appropriate set from Microsoft for your version of XP, and do the following:

Code:

apt-get install cabextract cabextract 'nameofarchive.exe' -d 'our working directory'




Please explain what I should hunt down an appropriate set of.

---

### Post by joumon on 2006-02-20
Can anyone help me out of a trouble in installing vmplayer in breezy? I'm just following to install win xp pro on my toshiba a75 laptop, but I got the following error message repeatedly. I don't know what's wrong with it...I'm trying to find any article on the internet for a whole day, but I couldn't find any good resource...Any help would be appreciated.

----------<error message>---------
/usr/lib/vmware/bin/vmplayer: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
*** attempt to put segment in horiz list twice
Unable to continue without a UI.

-----------<log file> -----------------
Feb 20 00:25:28: vmx| Log for VMware Player pid=9415 version=1.0.1 build=build-19317 option=Release
Feb 20 00:25:28: vmx| Command line: "/usr/lib/vmware/bin/vmware-vmx" "-@" "pipe=/tmp/vmware-root/vmx48e6c60d58eed6a6;vm=48e6c60d58eed6a6" "/root/vmware/WindowsXPPro.vmx"
Feb 20 00:25:28: vmx| UI Connecting to pipe '/tmp/vmware-root/vmx48e6c60d58eed6a6' with user '(null)'
Feb 20 00:25:29: vmx| Using system libcrypto, version 90707F
Feb 20 00:25:29: vmx| pcpu #0 CPUID numEntries=5 GenuntelineI
Feb 20 00:25:29: vmx| pcpu #0 CPUID version=0xf34 id1.edx=0xbfebfbff id1.ecx=0x459d id1.ebx=0x20800
Feb 20 00:25:29: vmx| pcpu #0 CPUID id80.eax=80000008 id81.edx=0x0 id81.ecx=0x0
Feb 20 00:25:29: vmx| CPUID id1.edx: 0xbfebfbff id1.ecx: 0x459d id81.edx: 0 id81.ecx: 0
Feb 20 00:25:29: vmx| CPUID id88.ecx: 0 id88.edx: 0
Feb 20 00:25:29: vmx| Removing stale symlink /var/run/vmware/%2froot%2fvmware%2fWindowsXPPro%2evmx
Feb 20 00:25:29: vmx| Setup symlink /var/run/vmware/%2froot%2fvmware%2fWindowsXPPro%2evmx -> /var/run/vmware/root/9415
Feb 20 00:25:29: vmx| ACL_InitCapabilities: here 1 (bug 63252)
Feb 20 00:25:29: vmx| changing directory to /root/vmware/.
Feb 20 00:25:29: vmx| Config file: /root/vmware/WindowsXPPro.vmx
Feb 20 00:25:29: vmx| Unable to find WindowsXPPro.vmss.  Setting vmState to NULL.
Feb 20 00:25:29: vmx| Unable to find WindowsXPPro.vmss.  Setting vmState to NULL.
Feb 20 00:25:29: vmx| LOG failed to remove /root/vmware/vmware-2.log failed: No such file or directory
Feb 20 00:25:29: vmx| VMXVmdbCbVmVmxExecState: Exec state change requested to state poweredOn without reset
Feb 20 00:25:29: vmx| TOOLS delaying state change request to state 3
Feb 20 00:25:29: vmx| PowerOn
Feb 20 00:25:29: vmx| Host ACPI: can't find SRAT
Feb 20 00:25:29: vmx| DISKUTIL: Offline toolsVersion = 0
Feb 20 00:25:29: vmx| UPGRADE: VM is non-painful guest winXPPro: It is alright to upgrade HW with out-of-date tools
Feb 20 00:25:29: vmx| Msg_Hint: msg.upgrade.legacyVM (shown)
Feb 20 00:25:29: vmx| vmdbPipe_Streams: Couldn't read
Feb 20 00:25:29: vmx| *
Feb 20 00:25:29: vmx| * The UI terminated unexpectedly.
Feb 20 00:25:29: vmx| * If you file a bug or support request about this issue,
Feb 20 00:25:29: vmx| * please include log and core file(s) from the UI if
Feb 20 00:25:29: vmx| * available.
Feb 20 00:25:29: vmx| *
Feb 20 00:25:29: vmx| Unable to continue without a UI.
Feb 20 00:25:29: vmx| Backtrace:
Feb 20 00:25:29: vmx| Backtrace[0] 0xbfc48828 eip 0x805a500
Feb 20 00:25:29: vmx| Backtrace[1] 0xbfc48c48 eip 0x80bc23b
Feb 20 00:25:29: vmx| Backtrace[2] 0xbfc48d78 eip 0x81a8c16
Feb 20 00:25:29: vmx| Backtrace[3] 0xbfc48d88 eip 0x80ab46f
Feb 20 00:25:29: vmx| Backtrace[4] 0xbfc48f28 eip 0x8132060
Feb 20 00:25:29: vmx| Backtrace[5] 0xbfc48fa8 eip 0x81f0ecd
Feb 20 00:25:29: vmx| Backtrace[6] 0xbfc48fc8 eip 0x80669e9
Feb 20 00:25:29: vmx| Backtrace[7] 0xbfc49428 eip 0x806669e
Feb 20 00:25:29: vmx| Backtrace[8] 0xbfc49478 eip 0x8065d47
Feb 20 00:25:29: vmx| Backtrace[9] 0xbfc49498 eip 0x8065c29
Feb 20 00:25:29: vmx| Backtrace[10] 0xbfc494b8 eip 0x805578a
Feb 20 00:25:29: vmx| Backtrace[11] 0xbfc494c8 eip 0x805565b
Feb 20 00:25:29: vmx| Backtrace[12] 0xbfc494e8 eip 0x80b68a6
Feb 20 00:25:29: vmx| Backtrace[13] 0xbfc49548 eip 0x80b6b28
Feb 20 00:25:29: vmx| Backtrace[14] 0xbfc49588 eip 0x80b73a2
Feb 20 00:25:29: vmx| Backtrace[15] 0xbfc496e8 eip 0x805fc09
Feb 20 00:25:29: vmx| Backtrace[16] 0xbfc49708 eip 0x805fa0f
Feb 20 00:25:29: vmx| Backtrace[17] 0xbfc8db68 eip 0x81bc619

---

### Post by ifwntrends on 2006-02-20
slight problem:

Error while opening virtual machine /home/ifwntrends/WindowsXPPro.vmdx/WindowsXPPro.vmx: "/home/ifwntrends/WindowsXPPro.vmdx/WindowsXPPro.vmx" is not a valid virtual machine configuration file.

i copied and pasted the directly to the file, any thoughts?

also, the boot disk i found for XP-Pro at [http://www.microsoft.com/downloads/thankyou.aspx?familyId=55820EDB-5039-4955-BCB7-4FED408EA73F&displayLang=en&oRef=http%3a%2f%2fsupport.microsoft.com%2f%3fkbid%3d310994](http://www.microsoft.com/downloads/thankyou.aspx?familyId=55820EDB-5039-4955-BCB7-4FED408EA73F&displayLang=en&oRef=http%3a%2f%2fsupport.microsoft.com%2f%3fkbid%3d310994)
had 6 cdboot#.img's in it, is this correct?

---

### Post by ifwntrends on 2006-02-20
scratch that last post it's opening it now, but now i get the error "File not found: WindowsXPPro.vmdk". this file was supposed to be created with the command "wine QemuInstall-0.7.2.exe create -f vmdk WindowsXPPro.vmdk 2G Formating 'WindowsXPPro.vmdk', fmt=vmdk, size=2097152 kB" but i can't find it and i get the feeling it just wasn't created. any sugestions would be much appreciated.

---

### Post by yabbadabbadont on 2006-02-20
I know that this thread has become very long, so I will post the correct disk image creation command again for easy access:```
wine QemuInstall-0.7.2.exe create -f vmdk WindowsXPPro.vmdk 2G
```
Everything after the "2G" in the original post was the mistakenly included output of the real command I just listed.

I hope that helps.

Edit:  There is a native breezy deb file for qemu 8 that eliminates the need to mess with wine.  See the ubuntu wiki for details and a download link.

[https://wiki.ubuntu.com/VMwarePlayerAndQemu](https://wiki.ubuntu.com/VMwarePlayerAndQemu)

---

### Post by Garyu on 2006-02-24
oh yes. the original howto was a bit messy, but with the following tips I got things to install easily from the CD. nice. not that I will use this at all, but I will install Ubuntu on my parents computer and then use this method to allow them to make an easy transition. :cool:

---

### Post by kamaaina on 2006-02-26
Followed the instructions and everything worked fine.  However, Windows seems to be halting at a certain point in the install process.  VMware has been showing this screen for 8 hours.  Getting the this screen only takes a few minutes.  Is there any way I can diagnose this?  Thanks!
[IMG]http://img151.imageshack.us/img151/5075/screenshot9gy.png[/IMG]

---

### Post by GQed76 on 2006-02-26
i got that on a regular cd..the cd was dirty..i cleaned the cd and it worked

---

### Post by kamaaina on 2006-02-26
I'm doing it off an ISO, I'll try recreating the ISO image.  Thanks

---

### Post by WackToMack on 2006-03-05
Hello everone!  So, I followed this "How To" and everything ran smoothly.  I have a few questions though:

1. Windows has detected my slave CDROM as the master... is there anyway to change this?

2. If/After changing my slave CDROM to slave again, how can I add my second CDROM device?

3. Can/Do I need to change the 192 default RAM size in order to run/play memory intensive programs?

4. Wait... I don't have a 4th...

Thanks in advance! :D

---

### Post by yabbadabbadont on 2006-03-05
[QUOTE=WackToMack]Hello everone!  So, I followed this "How To" and everything ran smoothly.  I have a few questions though:

1. Windows has detected my slave CDROM as the master... is there anyway to change this?

2. If/After changing my slave CDROM to slave again, how can I add my second CDROM device?

3. Can/Do I need to change the 192 default RAM size in order to run/play memory intensive programs?

4. Wait... I don't have a 4th...

Thanks in advance! :D[/QUOTE]
1|2)
ide0:0 -> primary ide controller, master device
ide0:1 -> primary ide controller, slave device
ide1:0 -> secondary ide controller, master device
ide1:1 -> secondary ide controller, slave device

Just adjust your cdrom entries accordingly.

3) It just depends on how much memory your system contains.  The more you have the more you can let vmware use.  Just be aware that you don't want to make more than 256MB available for a win98 image.  Win98 and earlier can't handle more than 256MB.  (I think the official line is 512MB, but I always ran into problems with more than 256MB installed)  Win2k and WinXP have no such problems though.  I have 768MB in my system and I let my Win2k image use 256MB, just as an example.  I wouldn't have any trouble bumping it up to 384MB if it were needed.  Remember though, that windows is going to have its own pagefile *inside* the virtual machine, just like it would if it were running normally.

I hope this helps.

---

### Post by WackToMack on 2006-03-05
Yep!  Thanks for the help, yabbadabbadont! :D

---

### Post by WackToMack on 2006-03-06
OK, now what filename would I have to use for a second HDD?

> ide0:1.present = "TRUE"
ide0:1.filename = "???"

---

### Post by yabbadabbadont on 2006-03-07
Whatever name you used when you created the new vmdk file to use as the second hard drive.

---

### Post by Sirin on 2006-03-07
One question, will this work with Windows OEM restore disks? I have one that came with my AcerPowerF2 that I purchased in 2004.

---

### Post by anil_robo on 2006-03-07
[quote=Sirin]One question, will this work with Windows OEM restore disks? I have one that came with my AcerPowerF2 that I purchased in 2004.[/quote]

I don't think so. I had compaq recovery CDs which failed. The CD is designed in such a way that it will run only on a compaq computer!!! Anyway you can try yours and let us know!

---

### Post by meastp on 2006-03-07
[QUOTE=drummer]I had the same problem with Windows 2000, it was stuck on the same screen for ages and didn't move (I left it running overnight). I read somewhere that it was a problem with VMWare being too smart with it's USB detection, so I removed the lines about USB in the .vmx file and restarted the installation. It worked fine after that and I'm pretty sure that that was the actual problem. I still have USB support, VMWare just added some lines back to the .vmx.[/QUOTE]

Exactly what did you modify/remove in the .vmx-file? I'm having this problem with windows XP (installation, installing devices)...

EDIT: attached two screenshots... as you see, the text will change, but the actual install will not progress any further...

---

### Post by Goochi on 2006-03-09
I had the same, just disable my USB device as VMWare was running and reset my virtual XP. Got past the devices thingy in just a few minutes.

---

### Post by meastp on 2006-03-10
[QUOTE=Goochi]I had the same, just disable my USB device as VMWare was running and reset my virtual XP. Got past the devices thingy in just a few minutes.[/QUOTE]

Thanks! I got it working. However, if I turn on / mount my devices -before- I "turn on" windows, they won't be recognized.

---

### Post by AndyCooll on 2006-03-10
Really looking forward to using this. However having a few problems getting going. When it comes to the stage of double-clicking on the .vmx to begin the XP install I get a permissions error message.

```
 Error while opening virtual machine WindowsXPPro.vmx: Insufficient permissions to access the file
```

What, or whose permissons must I change to enable this to run? :-?

---

### Post by yabbadabbadont on 2006-03-10
Make sure that *all* the files in the directory with your vmx file are owned by your user.  Then make sure of the permissions too.  Example ```
cd directorycontainingfiles
sudo chown youruserhere *
chmod 644 *
chmod 744 *.vmx

```

---

### Post by AndyCooll on 2006-03-11
Thanks very much for taking the time to help.

I found that by following your instructions though I still wasn't able to open the file ...you did point me in the right direction. I solved it in the end by ensuring the owner of the files were me (as you were suggesting) and also that the files were in my group. Previously, both file owner and file group were root.

:cool:

---

### Post by briancrutin on 2006-03-11
big help! thanks!:)

---

### Post by turtlefreak on 2006-03-19
mine runs (Windows 2000) and tries to install but closes when it gets to the "installing network" part (this is the installer part after installing from the disk, just to clarify). Anyone else have this happen? How do i fix it?

---

### Post by Klejs on 2006-03-20
Thanks for the great HOWTO!

---

### Post by bender unit on 2006-03-20
Hey guys,

haven't had the time to read through the whole thread yet, so sorry if someone mentioned it already. But instead of using a text editor to create/modify your VMs by hand, you can just install the complete VMware version and use the main VMware program to create and edit the VMs. At least for me, the only thing the program won't do if it's not registered is actually running any VMs, but it can create and modify them without any problems. Now I find that a bit easier than messing around with text files. 
Of course, buying VMware is still worth it's money, because it'll let you configure some aspects of your VMs while they are running (i.e. swapping the iso in the emulated cd rom drive). With just the player, you have to stop the VM completely, edit the config and start the VM again in order to have a different "cd rom" in your drive.

Anyways, have fun!

---

### Post by xx75 on 2006-03-21
Hi Community

I have just some how suprised myself by getting win xp to work, i have a not-so-slight computing handicap so i'm pretty pumped right now (and the crowd goes wild!). My only dilemma is, and I have skimmed through this thread for answers but if i am repeating something i apologise, it doesn't detect my cd burner and dvd burner. I was thinking of changing the .vmx file to suit a few others i have seen on the thread but don't really want to risk killing what i have so far achieved. Have I missed something?

Any help is greatly appreciated.

Thanks

xx75

Edit: Had a stab and got it working, thanks for looking anyway.

---

### Post by ynef on 2006-03-25
Holy shit, thank you so much for including a working link to the tools ISO!

Now I don't need to worry about getting Photoshop up and running in wine anymore! :D

---

### Post by Petrush on 2006-04-02
removed usb mounting problem, since it was in dapper.

---

### Post by rts on 2006-04-02
Looking through this thread it seems nobody else ran into this, so here goes...

I have an ethernet port and a wireless card (on laptop).  While installing, ethernet was unplugged, and wireless was connected.

When it asked me to about which interface to bridge, I tried both (eth0 and ra0)... what the hell... one for wireless, one for wired eh?

However, when it came time to starting up the vmware services it would hang my machine (a fairly fresh install of Breezy with VMware-player-1.0.1-19317.tar.gz), focing a hard reset.  It would hang while tring to bring up the VMWare bridge for eth0.

Plugging in an ethernet cable and activating both interfaces at the same time got around that problem.

Now I'm on to the actual WinXP install.

---

### Post by PriceChild on 2006-04-08
Hey, installed xp pro perfectly first time.

However, how can i get it onto the net? :S I'm using eciadsl to use my usb modem. Should i have bridged all the connections at the step it asked me to? or just the one?

Running Breezy, please help, ty Pricey

---

### Post by Rahu on 2006-04-08
I also can't get an internet connection working in this.  I kept all the network options at default during the install, but it won't connect :(

---

### Post by Jose Catre-Vandis on 2006-04-08
Here's a link to the "windows.iso" that contains the VmWare Tools you might need to improve many aspects of using the VMPlayer

```
http://rapidshare.de/files/17538196/windows.iso.html
```

What do you do with it?

Edit the vmx file to point to this iso, then run your virtual machine.

Open up the CD contents in your Explorer/Nautilus/Whatever and find the setup file (this iso is for windows!)

Run the setup file and this will install Vmware tools

---

### Post by CornMaster on 2006-04-10
I was going to write my own how to about this...but after a nasty lockup and loosing what I had written (and freezing during the config process) I decided I'd just post my addition.

Pretty much everything is the same, but instead of using qemu to create the images, and manually creating the vmx file, I went to [www.easyvmx.com](www.easyvmx.com) and created my own vmx and image file.  Should save a lot of horsing around. :)  Hope it helps someone. 

Oh...make sure the CD ROM is in the drive before you start up the emulator (if you use a physical CD) or it will just die with no errors or anything.

---

### Post by Jose Catre-Vandis on 2006-04-10
[QUOTE=CornMaster]I was going to write my own how to about this...but after a nasty lockup and loosing what I had written (and freezing during the config process) I decided I'd just post my addition.

Pretty much everything is the same, but instead of using qemu to create the images, and manually creating the vmx file, I went to [www.easyvmx.com](www.easyvmx.com) and created my own vmx and image file.  Should save a lot of horsing around. :)  Hope it helps someone. 

Oh...make sure the CD ROM is in the drive before you start up the emulator (if you use a physical CD) or it will just die with no errors or anything.[/QUOTE]


SPECTACULAR link Cornmaster :-)

---

### Post by CornMaster on 2006-04-10
Yeah..that is a pretty sweet site. :)

I finally got everything configured, had to disable virtually all the emulated hardware to get Windows to install...and then it would still choke with the network when i tried to turn it on.  I had to reconfig the player, and disable bridging and enable NAT.  Although it complains...everything works. :)

Now..if only I could get my files from my real windows to my virtual windows....and of course...I still can't kill windows totally...still play a scatter game or two. :(

---

### Post by PriceChild on 2006-04-12
[quote=PriceChild]Hey, installed xp pro perfectly first time.

However, how can i get it onto the net? :S I'm using eciadsl to use my usb modem. Should i have bridged all the connections at the step it asked me to? or just the one?

Running Breezy, please help, ty Pricey[/quote]

Got it working :D

Just made a new image from easyvmx, used mostly default options and it decided to work this time :)

Go team :)

---

### Post by Muffe on 2006-04-20
I have a broblem with installing Windows XP on the virtual machine. I load all the boot floppies, but when it's time to format the (virtual) hard drive, the windows installer tells me that it is not able to format the hard drive. It is the same with both FAT and NTFS, and quick and normal format.

Does anyone have any experiences with this issue? Thanks.

---

### Post by PriceChild on 2006-04-20
If anyone's having  problems with installing this kernel on a 2.6.16 kernel, then check the thread here:


[http://ubuntuforums.org/showthread.php?t=163133&page=2](http://ubuntuforums.org/showthread.php?t=163133&page=2)

---

### Post by Jose Catre-Vandis on 2006-04-20
Here's the rpm package needed to install the Vmware Tools in a Linux virtual machine, e.g. if you are running a linux distro inside VMware player. You will need all sorts of dependencies in the "inner distro" to make it work, -> make, gcc, kernel headers (the last two must match)

```
http://rapidshare.de/files/18532527/VMwareTools-5.5.1-19175.i386.rpm.html
```

@ 16mb

---

### Post by mschievano on 2006-04-26
I follow all the step, but my try is blocked when I double-click on the file Win2000Pro.vmx
The player started and show me this message:
```

The disk /home/mschievano/win2000/Windows2000Pro.vmdk has one or more internal errors that 
cannot be fixed. The only option is to restore from a backup copy of this disk.
Cannot open the disk '/home/mschievano/win2000/Windows2000Pro.vmdk' or one of the snapshot 
disks it depends on.
Reason: The specified virtual disk needs repair.

```

I generate the vmdk with the command:
```

wine qemu-img.exe create -f vmdk Windows2000Pro.vmdk 2G 

```

and this is my dir:
```

mschievano@ainex:~/win2000$ ls -la
totale 386450
drwxrwxrwx  2 root       root             504 2006-04-25 22:54 .
drwxrwxrwx 41 mschievano mschievano      2256 2006-04-25 22:54 ..
-rwxrwxrwx  1 mschievano mschievano   1474560 1999-12-07 12:00 CDBOOT01.IMG
-rwxrwxrwx  1 mschievano mschievano   1474560 1999-12-07 12:00 CDBOOT02.IMG
-rwxrwxrwx  1 mschievano mschievano   1474560 1999-12-07 12:00 CDBOOT03.IMG
-rwxrwxrwx  1 mschievano mschievano   1474560 1999-12-07 12:00 CDBOOT04.IMG
-rw-r--r--  1 mschievano mschievano     18021 2006-04-25 22:51 vmware-0.log
-rwxrwxrwx  1 mschievano mschievano     18019 2006-04-25 15:20 vmware-1.log
-rwxrwxrwx  1 mschievano mschievano     15909 2006-04-25 15:17 vmware-2.log
-rw-r--r--  1 mschievano mschievano     18021 2006-04-25 22:54 vmware.log
-rwxrwxrwx  1 mschievano mschievano 389335040 2006-04-25 14:26 Windows2000Pro.iso
-rwxrwxrwx  1 mschievano mschievano    340096 2006-04-25 22:54 Windows2000Pro.vmdk
-rwxrwxrwx  1 mschievano mschievano         0 2006-04-25 14:28 Windows2000Pro.vmsd
-rwxrwxrwx  1 mschievano mschievano      3578 2006-04-25 15:20 Windows2000Pro.vmx
-rwxrwxrwx  1 mschievano mschievano      3578 2006-04-25 15:20 Windows2000Pro.vmx~

```

any idea :confused:

---

### Post by n8bounds on 2006-04-27
This is awesome!  It worked (XP Pro in Breezy)!  (I followed Wombley's instructions on using the linux version of QEMU)

Screen shot:

[http://ubuntuforums.org/attachment.php?attachmentid=8817&stc=1&d=1146154529](http://ubuntuforums.org/attachment.php?attachmentid=8817&stc=1&d=1146154529)

Thanks a trillian!

---

### Post by mschievano on 2006-04-27
[QUOTE=mschievano]I follow all the step, but my try is blocked when I double-click on the file Win2000Pro.vmx
any idea :confused:[/QUOTE]

**NOTE - RESOLVED**: 
Find it. Read this 2 topics!

1. how to install the virtual machine
[https://wiki.ubuntu.com/VMwarePlayerAndQemu](https://wiki.ubuntu.com/VMwarePlayerAndQemu)

2. how to install vmware tools
[http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html](http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html)

---

### Post by Nickoladze on 2006-04-29
I installed VMWare **Workstation** and installed Windows XP Professional on VMWare.

My question is, how to I share files between my main OS and the guest OS?
When I installed VMWare Tools on Windows, it said my shared folder is at \\.host\Shared Folders\ or something like that, so I mapped drive letter Z to that folder. I can't find where that is at in my Linux filestructure, and Windows says I don't have write access to that folder.

---

### Post by mschievano on 2006-04-29
[QUOTE=Nickoladze]I installed VMWare **Workstation** and installed Windows XP Professional on VMWare.

My question is, how to I share files between my main OS and the guest OS?
When I installed VMWare Tools on Windows, it said my shared folder is at \\.host\Shared Folders\ or something like that, so I mapped drive letter Z to that folder. I can't find where that is at in my Linux filestructure, and Windows says I don't have write access to that folder.[/QUOTE]

read my sintetys:
[http://sistemist.wordpress.com/2006/04/26/install-a-virtual-machine-on-dapper-6xx/](http://sistemist.wordpress.com/2006/04/26/install-a-virtual-machine-on-dapper-6xx/)

---

### Post by Clazziquai on 2006-05-04
[QUOTE=sethmahoney]Thanks a lot!  Works great, except, is it normal for the part of the install where Windows detects and installs all your hardware to take a REALLY long time?[/QUOTE]

I've got that problem... it's been over an hour now stuck at "Installing Devices" when it looks like it's done.

I hope to get it installed soon enough :(

---

### Post by WillFerrellLuva on 2006-05-12
Hi,

I am trying to set up windows xp pro.  I followed the instructions, but I have a problem :( 

After I go through all of the cdboot.img files it says windows has to restart.  It restarts and then jumps in to the graphical installer.  As soon as this happens I get an error message from the windows installer.  The details of the error follow:

> Error:
Installation Failed: D:\i386\asms. Error Message: The parameter is incorrect.

***

Fatal Error:
One of the components that Windows needs to continue could not be installed.

The parameter is incorrect.

***

Any ideas?

---

### Post by jnev on 2006-05-13
awesome tutorial, thanks!! any way to resize the partition once you get it installed? I did only 2gb and I need close to 10 probably...

EDIT
and if it's not possible to resize, how can I delete the partition (since it's not a "real" partition I'm assuming)?

EDIT2
lol, sorry for all the edits, but I figure this is better than posting 3 in a row..

how can I make it so I can view other harddrives and partitions in my computer? as it is now I can only see the C drive. if I can get it to do that then I probably won't even need to resize because I'm already dual-booting with windows and all my necessary programs are already installed, and I could just link to them...

---

### Post by jnev on 2006-05-13
ok scratch that question, I just made a new 6gb partition, which should be sufficient.

how can I get windows to see a cd though so I can install programs like photoshop?

---

### Post by MartinJ on 2006-05-14
You will need to change the settings in your .vmx file.
I've copied the following from mine: (note: my cd drive is listed as /dev/hde, which is unusual I think.  Your's might be /dev/hdc or /dev/cdrom (?))

```
ide1:0.present = "TRUE"
ide1:0.fileName = "/dev/hde"
ide1:0.deviceType = "cdrom-raw"
ide1:0.autodetect = "FALSE"
```

Hope that helps, or puts you on the right track.

---

### Post by jnev on 2006-05-14
worked perfectly, thanks so much!!

and one last question: how can I view my other hard drives from windows? all it currently sees is its C drive...

thanks

---

### Post by MartinJ on 2006-05-14
To do that I think you'll have to look at sharing your linux directories with samba and viewing them over the local network which the vmplayer sets up.  Windows won't see any other hard drives because it's effectively running on a completely separate system, or so it thinks.  The same goes for Ubuntu not recognising the .vmdk disk as an actual hard drive.

For transferring a few files I've used KDE's public file server taskbar applet.  It lets you set up a simple server, for download only, on your local network.  In Windows, I type in the local IP address and port number and it gives me a list of shared files to download.

Maybe you could share a hard drive using /dev/hda in the .vmx file but this creates a loop and I'm fairly sure it won't work, just thinking out loud.  I'm not sure of any side effects either!

I'd investigate network shares.

---

### Post by jnev on 2006-05-15
ok, I got it working. I had to setup samba to share some folders and then finally managed to get windows to see the folders (god I had setting up networking in Windows!!).

thanks for all the help!

---

### Post by korami on 2006-05-15
[QUOTE=jnev]ok, I got it working. I had to setup samba to share some folders and then finally managed to get windows to see the folders (god I had setting up networking in Windows!!).

thanks for all the help![/QUOTE]

Hi jnev. Could you detail a bit pls how you did this. I also set up samba and shared a folder, but the wxp virtual machine doesn't see my ubuntu in the Network Neighbourhood. I'm using NAT btw (this way I can access the internet also through wxp).

---

### Post by jnev on 2006-05-15
I set a password for samba using sudo smbpasswd -a 'username'. in windows I just went into my network places and the folders I was sharing were there. sorry I'm not much help, when it comes to networking I usually just rely on luck to get it to work ](*,)

---

### Post by lorenzo111 on 2006-05-18
Hey I sound like a broken record I know but have followed the directions vmware working perfectly, made my windows XP folder, installed wine, downloaded the link qemu and installed it via wine but when I give the command qemu it says command not found like the one guy posted on page 4 have the windows xp iso copied to the folder also would really like to know where i went wrong want this to work. I appreciate any help thanks

---

### Post by tuxcantfly on 2006-05-18
folks, vmware server is now free. just fetch it from the official site

just use it, don't fool around with qemu and all to create the disk image

then again, if you're one of those open-source zealots who refuse to use anything non-GPL... well, you still have to do it the old way

---

### Post by lorenzo111 on 2006-05-18
ok got xp loaded but looked through all the links but cant get vmware tools need that and ill be gravy

---

### Post by korami on 2006-05-19
[QUOTE=tuxcantfly]folks, vmware server is now free. just fetch it from the official site

just use it, don't fool around with qemu and all to create the disk image

then again, if you're one of those open-source zealots who refuse to use anything non-GPL... well, you still have to do it the old way[/QUOTE]

What is the difference between VMWare Workstation and VMWare server? Are there any disadvantages (or why is it free)?

---

### Post by MartinJ on 2006-05-19
[QUOTE=lorenzo111]ok got xp loaded but looked through all the links but cant get vmware tools need that and ill be gravy[/QUOTE]

Have you tried the solution on this post?:
[http://www.ubuntuforums.org/showpost.php?p=573533&postcount=118](http://www.ubuntuforums.org/showpost.php?p=573533&postcount=118)

Or this link:
[http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=920](http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=920)

Note: I didn't use these sources.  I'm assuming these images are the correct vmtools installers.

---

### Post by lorenzo111 on 2006-05-19
Just to let everyone know I got it working just used the queimg command via the wine interface and copied it into my windowsxp folder. Then found alot of dead links for the vmware tools .iso but finally found one in here that works. loaded it into my virtual vmplayer cdrom installed all the goodies set my nic to NAt since I'm on wireless and everything is great only question I have left what is the best way to keep this working? I.E. when I do upgrades to ubuntu to ensure I dont break the dependices of it. Used past distros of it and it worked great until I upgraded somethings and bam it just died veryfrustating taking all the time to get it right and one update its all gone. I guess all in all should I just uninstall it prior to upgrading or what other course of action would you recommend to keep it always working

---

### Post by deathbyswiftwind on 2006-05-22
Could someone please help me. I am trying to get internet in winxp. When I configured vmplayer it detected it and said it set everything up fine but in xp I have no net at all.


EDIT: Nevermind Im stupid I figured it out. All I had to do was switch networking from bridged to nat and instantly it worked

---

### Post by Rob Lindsay on 2006-06-15
Hi there,

Am fine with this until I get to the bit where you click on the floppy icon and eject.

I don't seem to hav a floppy icon. How do I load second and successive floppy images?

Thanks,

Rob

---

### Post by OrganicPanda on 2006-06-22
this worked well thank you all, although i feel a bit dirty doing this, rest assured it will only be to use photoshop .... although some of the people here sound like they should just use windows if they want fullscreen desktops / msn type things. the xp installer is like a small child, it craves attention... when its not in focus it stops .. lol

edit: i didnt need the tools package to adjust my res and colour depth which is weird but its probly best to install it anyway as ive seen a massive performance increase, see the attach for pre-tools screenshot (just to show off that it works) lol

edit 2: can anybody suggest a good way to make a menu item to run a certain virtual machine, at the command line:

```

sudo vmplayer /files/virtual/virtual_windowsxp/virtual_windowsxp.vmx

```

works but that no longer works if i put it in the menu (probably because it wants a password) , any help??

---

### Post by beatyou on 2006-06-22
[QUOTE=BLTicklemonster]Thanks. When I do that, I get 
Non-System disk of disk error
Replace and press any key when ready.

Im not goiing to have to install it each time I try to use it am I?[/QUOTE]


VMWare is mounting your floppy images. This happened to me as well. I just disabled the floppy drive by clicking on its icon at the top of VMware and rebooted, it restarted and worked fine.

---

### Post by kloshar on 2006-06-22
I'd really like to know if it's possible to share files between virtual os (WinXP) and host os? (Linux)

---

### Post by jstueve on 2006-06-22
yes you can, through SMB/Samba file shares.

---

### Post by kloshar on 2006-06-22
Is there any howto on Ubuntu forum to install and configure samba? 

Is it possible to share files over vmware server?

---

### Post by joe_lace on 2006-06-23
You are the man, my friend.  I was able to use your tutorial to get a windows XP VM up and running.  It has no lag because my computer is fast enough.  It is a 3E Ghtz Pentium 4 with hyper threading.  It has 1GB of ram and I dedicate 512 of that to the VM.  800MHz FSB.  I was able to get it installed from the CD using this WindowsXPPro.vmx file:

```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "WindowsXPPro.vmdk"
memsize = "512"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "cdrom-raw"
ide1:0.autodetect = "TRUE"
floppy0.present = "FALSE"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows XP Pro"
guestOS = "winxppro"
nvram = "WindowsXPPro.nvram"
MemTrimRate = "-1"

ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d 3d d1 ed 13 d4 7c-b9 4b a3 c8 d3 af 2a aa"
uuid.bios = "56 4d 3d d1 ed 13 d4 7c-b9 4b a3 c8 d3 af 2a aa"
ethernet0.generatedAddress = "00:0c:29:af:2a:aa"
ethernet0.generatedAddressOffset = "0"

tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"

uuid.action = "create"

checkpoint.vmState = ""

tools.remindInstall = "TRUE"
usb.autoConnect.device0 = "path:2/0 autoclean:1"
```
NOTE: if you use this .vmx file remember that I have my memory set to 512.  You may want to change that.

Then after running the VM player I confirmed the bios settings and they were correct.  The only other thing I had to do was click the "connect to CDROM" icon at the top of VMware Player.  Worked like a dream, thanks.

---

### Post by jms830 on 2006-06-27
can anyone tell me how to uninstall the vmware player I installed using this guide? now that vmware-player is in the dapper repos i'd prefer to use that one instead. thanks

EDIT: nevermind, I found it earlier in this thread, command "sudo vmware-uninstall.pl"

---

### Post by kloshar on 2006-06-28
How go get throught this error: Unable to stop VMware Server's services. Aborting the uninstallation.

I get this while installing Vmware Player. I have VMware server installed but I've closed it.

---

### Post by kloshar on 2006-06-28
Please, I need the answer urgently. Google does not help. :roll:

---

### Post by sim-x on 2006-06-29
Heya, thanks for an awesome thread. So everything went smoothly until the floppy part. When windows 2000 install asked me for disk 2, I followed the instructions and changed CDBOOT1 to CDBOOT01 and CDBOOT2 to CDBOOT1. Then everything proceeded fine until the install asked me to insert disk 3... no luck there..any any ideas? thanks in advance

---

### Post by hacky maximus on 2006-07-16
Hello everyone! I'm new to Linux and I have a question about Vmware - can I use my currently installed XP (I have it in dual-boot with Ubuntu) or I have to install it again under Vmware in order to run ? 
  Thx a lot, and soryy if this problem was discussed again ;)

---

### Post by yabbadabbadont on 2006-07-17
> **hacky maximus said:**
> Hello everyone! I'm new to Linux and I have a question about Vmware - can I use my currently installed XP (I have it in dual-boot with Ubuntu) or I have to install it again under Vmware in order to run ? 
  Thx a lot, and soryy if this problem was discussed again ;)

If you purchase a copy if vmware-workstation, then you are supposed to be able set it to use your already installed XP.  With vmware-player, you will have to install it again inside vmware.

---

### Post by hacky maximus on 2006-07-17
Ok, I'll purchase and try it out :-k

---

### Post by yabbadabbadont on 2006-07-17
Before spending more than $100, you should contact VMWare's sales people and verify that what I said it true.  I'm pretty sure it is as I've seen various posts about it on the VMWare forums that indicate it is true but, better safe than out $100...

---

### Post by trmentry on 2006-08-04
Just wanted to post that this worked great.  I did it slightly differently.  I took a fresh install of Dapper x86 which gave me kernel 2.6.15-23.

I then tried to install vmware-player via Synaptic but it wasn't listed.  So I installed nVidia-glx and rebooted and then it was.  Not sure why that was.  

Anyway, I installed vmware-player and dependancies via Synaptic and it worked fine. 

I then did the following to make my iso.

```

dd if=/dev/hdb WindowsXPPro.iso

```

I was able to get qemu for linux working and had it create my vmdk image with the command line that was listed in the first post.  I changed it from 2G to 25G though. :)

I copied over the vmx info listed in the first post and took out the floppy stuff.  

Started up VMWare and it booted the ISO and installed Windows in about 15 minutes. :)  

Thanks you to the original poster for a very well laid out doc.

---

### Post by andy_cowman on 2006-09-06
Hey everyone

I am having some USB problems, I cant get my road angel compact to work through VMplayer.I have had it work in the past but that was a couple of different set ups ago and I am not for the life of me sure what to do next :s

 The log reports this 

ep 06 11:37:18: vmx| USB: Found device [name:Western\ Digital\ Corporation\ Western\ Digital\ USB\ Hard\ Drive vid:1058 pid:0300 path:6/1]
Sep 06 11:37:18: vmx| USB: Found device [name:Future\ Technology\ Devices\ USB\ device vid:0403 pid:efab path:3/1]
Sep 06 11:37:18: vmx| USB: Autoconnecting device "Future Technology Devices USB device" matching pattern [path:3/1 autoclean:1]
Sep 06 11:37:18: vmx| USB: Connecting device 0xe00300020403efab
Sep 06 11:37:18: vmx| VMXVmdbLoadUsbDevices: New set of 2 USB devices
Sep 06 11:37:18: vmx| USBGL: CONTROL failed -1:32:Broken pipe
Sep 06 11:37:18: vmx|        requesttype=80 request=6 value=301 index=904
Sep 06 11:37:18: vmx|        length=202 data=0x85efe80 timeout=186a0
Sep 06 11:37:18: vmx| USBGL: CONTROL failed -1:32:Broken pipe
Sep 06 11:37:18: vmx|        requesttype=80 request=6 value=302 index=904
Sep 06 11:37:18: vmx|        length=202 data=0x85efe80 timeout=186a0
Sep 06 11:37:18: vmx| USB: Found device [name:Western\ Digital\ Corporation\ Western\ Digital\ USB\ Hard\ Drive vid:1058 pid:0300 path:6/1]
Sep 06 11:37:18: vmx| USB: Found device [name:Future\ Technology\ Devices\ USB\ device vid:0403 pid:efab port:1 path:3/1]
Sep 06 11:37:18: vmx| USB: Device [name:Future\ Technology\ Devices\ USB\ device vid:0403 pid:efab port:1 path:3/1] should already be connected
Sep 06 11:37:18: vmx| VMXVmdbLoadUsbDevices: New set of 2 USB devices

---

### Post by BLTicklemonster on 2006-09-14
> Installing the player itself involves some patience. Get the Linux tar from this page. Most of my instructions will be shamelessly ripped from this lovely tutorial.

I guess I missed the part about installing the server itself...

BUT, I'm downloading it now, and will mess around with it later.

---

### Post by eijuli on 2006-09-14
Thanks for a great howto! I got it running and it works fine. I only had one problem with the installation, the freezing at "Installing devices". Thanks to this thread I got past it, by simply disabling the "automatically connect new USB-devices".

---

### Post by student2006 on 2006-09-27
Hello

i've a problem with rename my .vmx if i rename it then the snapshot won't work does some one know how to rename .vmx so that my virtual machine will still work?

---

### Post by dotsi on 2006-11-05
I just ran into this thread and wondered whether it would be possible to run already existing Windows XP installation in vmware player?

---

### Post by yabbadabbadont on 2006-11-05
> **dotsi said:**
> I just ran into this thread and wondered whether it would be possible to run already existing Windows XP installation in vmware player?

No.  vmware-player does not support running an installed instance of windows.  vmware-workstation (you have to buy it) does, but I believe it is not officially supported.  I posted a link to the vmware forums with the information on this.  I'll see if I can find it again.

EDIT: found the information on the vmware forums [here](http://www.vmware.com/community/thread.jspa;?messageID=164934&#164934).

---

### Post by PriceChild on 2006-11-06
> **yabbadabbadont said:**
> No.  vmware-player does not support running an installed instance of windows.  vmware-workstation (you have to buy it) does, but I believe it is not officially supported.  I posted a link to the vmware forums with the information on this.  I'll see if I can find it again.

EDIT: found the information on the vmware forums [here]("http://www.vmware.com/community/thread.jspa;?messageID=164934&#164934").Vmware server does also.

However you have to be VERY careful changing hardware profiles.

There's a howto in these forums.

---

### Post by yabbadabbadont on 2006-11-06
> **PriceChild said:**
> Vmware server does also.

However you have to be VERY careful changing hardware profiles.

There's a howto in these forums.

Thanks, that is good to know.  I knew that player couldn't do it and I didn't think to see if server could.

---

### Post by dklearhos on 2006-11-21
it works just great.I would like to ask if it possible to resize the virtual windows drive after the installation is complete.(i tried to but i probable reformated the whole partition than resizing it.An other question is whether is possible to run faster by using the real memory rather than virtual which slows down the whole universe..

---

### Post by yabbadabbadont on 2006-11-27
> **dklearhos said:**
> it works just great.I would like to ask if it possible to resize the virtual windows drive after the installation is complete.(i tried to but i probable reformated the whole partition than resizing it.An other question is whether is possible to run faster by using the real memory rather than virtual which slows down the whole universe..

You can't resize the virtual drive image as far as I know, but you can add another virtual drive and it will show up just like you added a second harddrive to the virtual machine.  (there is something wrong with that sentence...:))

---

### Post by William Pickett on 2006-12-24
<reply to rant> I am a new to Linux/unix  and Ubuntu, about one year now. I too find the learning curve very frustrating. Even all the books and online tutorials, in my understanding, quite often presume that someone reading the info- "knows" what is discussed, when the reality is, many - myself- do not. So it is up to us consumers, again, which is a good thing, to write a new book, making sure complete descriptions are given for every statement on how to do something, so that all new folks will have a better feeling and interest-in this and any- learning process.

Example- "navigate to the folder, then do mumbo jumbo at the terminal"... Navigate in most dictionaries means and is related to, steering a ship-, so we 'know' this is incorrect context. Movement is assumed here- as in goto the folder- hmmm- go to the folder- too ambiguous... how about something like- in the upper left hand corner -there is a toolbar that says applications, places and system. Click on places (then guide the user where to go-). THis is how it really needs to be, for any real growth to take place where linux/unix et al are concerned. Any reason why many feel a person has to bee a nerd/geek/scientist etc to make sense of all this? And then many folks do not bother to reread their posts to check for typos- I see that a lot as well.

I am starting to give my help in whatever way I am able as well, because we are all together in this life, and we all need/want assistance of some kind at some point in our lives. "Be real careful what you 'say', 'think' and 'do', because you always have an Opportunity to Impact Other's Lives Too!"  - and Now you know the "Rest of the Story"
William "paul harvey aka wild bill" Pickett Albuquerque NM:KS :p

---

### Post by Brian Boyko on 2006-12-30
I'm on 64 bit Ubuntu - is there any way to do this without using Wine, which does not work in 64 bit Ubuntu?

---

### Post by Hanzerik on 2007-01-19
> **Brian Boyko said:**
> I'm on 64 bit Ubuntu - is there any way to do this without using Wine, which does not work in 64 bit Ubuntu?

Update your source.list to allow apps from universe (I think thats where qemu resides)

apt-get update
apt-get install qemu

This will install the linux version of qemu.

As long as you have either a iso or cd of your guest os you can install it, using vmware player, and a little text file creating. You don't need to install wine to get it to work.

---

### Post by Incubusattax on 2007-01-20
When I double click my vmx file and VMplayer starts, I get this error:
```
Cannot open the disk '/home/incubusattax/Windows XP/Windowsxp/WindowsXPPro.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file.
```

Anyone know how I can fix that?

---

### Post by Doug11 on 2007-01-20
.

---

### Post by Hanzerik on 2007-01-20
> **Incubusattax said:**
> When I double click my vmx file and VMplayer starts, I get this error:
```
Cannot open the disk '/home/incubusattax/Windows XP/Windowsxp/WindowsXPPro.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file.
```

Anyone know how I can fix that?

Can you post your WindowsXPPro.vmx file?

---

### Post by Incubusattax on 2007-01-21
Here it is:

```

#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "WindowsXPPro.vmdk"
memsize = "192"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "WindowsXPPro.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"
floppy0.fileType = "file"
floppy0.fileName = "cdboot1.img"
floppy0.startConnected = "True"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows XP Pro"
guestOS = "winxppro"
nvram = "WindowsXPPro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
uuid.bios = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
ethernet0.generatedAddress = "00:0c:29:4c:23:7b"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = "WindowsXPPro.vmss"
tools.remindInstall = "TRUE"

```

---

### Post by GForce0617 on 2007-01-22
Getting an error during the script.

Use of uninitialized value in addition (+) at /usr/bin/vmware-config.pl line 804, <STDIN> line 13.
Unable to install the .desktop menu entry file. You must add it to your menus 
by hand.
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Player is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc-3.4". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

Any ideas. Appears to want to get a compiler installed?

New to this so go easdy on me.

Thanks in advance.

---

### Post by tcashin on 2007-01-29
> **Incubusattax said:**
> When I double click my vmx file and VMplayer starts, I get this error:
```
Cannot open the disk '/home/incubusattax/Windows XP/Windowsxp/WindowsXPPro.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file.
```

Anyone know how I can fix that?

Is your WindowsXP guest running from a physical/raw disk?  If so, VMware needs read and write access to the physical device, /dev/hda or /dev/sda or whatever it may be for your system.  I suggest adding yourself to the 'disk' group to make this work.  (Verify that the disk group has rw permissions for your disk device)

---

### Post by tcashin on 2007-01-29
> **GForce0617 said:**
> Getting an error during the script.

Use of uninitialized value in addition (+) at /usr/bin/vmware-config.pl line 804, <STDIN> line 13.
Unable to install the .desktop menu entry file. You must add it to your menus 
by hand.
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Player is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc-3.4". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

Any ideas. Appears to want to get a compiler installed?

New to this so go easdy on me.

Thanks in advance.

Sounds like you need to install the kernel headers for your running kernel, or if you have the headers installed, the default path that the vmware installer checks is not correct for Ubuntu.  To install the headers, fire up Synaptic (or your favorite package manager) and install linux-headers-generic (if you're running edgy.  I think it's linux-headers-386 or -686 for dapper).  Or from command line, enter
```
sudo apt-get install linux-headers-generic
```

Now, as I said, the default directory that the vmware installer checks, /usr/src/linux/include, does not work with the Ubuntu linux header package.  Ubuntu installs the headers in /usr/src/linux-headers-xxx where xxx is the version number information.  When the vmware installer prompts you for the directory containing the kernel headers, simply enter the appropriate path.  For example, under Edgy I would enter /usr/src/linux-headers-2.6.17-10-generic/include.  (Make sure you add the trailing /include or it won't work.)

---

### Post by Daviey on 2007-01-30
Why not just use [http://www.easyvmx.com/easyvmx.shtml]("http://www.easyvmx.com/easyvmx.shtml")

It allows simple configuration then download the 'machine' in a zip file!!

---

### Post by AusIV4 on 2007-02-03
> **Incubusattax said:**
> When I double click my vmx file and VMplayer starts, I get this error:
```
Cannot open the disk '/home/incubusattax/Windows XP/Windowsxp/WindowsXPPro.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file.
```

Anyone know how I can fix that?

```

$ cd /home/incubusattax/Windows XP/Windowsxp
$ sudo chown incubusattax.incubusattax *

```

All of the files in that directory should now owned by you. If you are trying to run WindowsXP off of a physical partition rather than a virtual disk, you'll also need to add yourself to the "disk" group, which can be done in the Users and Groups administration panel.

---

### Post by eldragon on 2007-02-07
ok, im having the same problem:

Cannot open the disk '/home/eldragon/Desktop/VMWARE/windows.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file.

ive created the group disk as said on another thread. yet i dont know how to give it disk access.
running the player as sudo didnt fix it either.


ive followed the steps described here: 
[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

everything went smooth, except for "dd if=/dev/hda of=windowsxp.mbr bs=512 count=63" which required a sudo before dd ;)

shall i add ive got windows xp pro installed on a raid-0 drive, which has 2 partitions: a NTFS one, and a ext3. so, i replaced /dev/hda with /dev/mapper/nvidia_geaeafee which is my raid-0 drive.

the vmdk fike is the same on that link, except for the modifications to the drive description (sectors, cyls, etc). the vmx file, is the exact same one.

any help, really appreciated.

thanks

---

### Post by tcashin on 2007-02-08
> **eldragon said:**
> 
ive created the group disk as said on another thread. yet i dont know how to give it disk access.



You shouldn't have to create a disk group, it hopefully already existed, and your device nodes should be owned by the disk group.  You need to add the users who will run vmplayer to the disk group.  ls -l /dev/mapper/nvidia_geaeafee and verify that it is indeed owned by the disk group and that group permissions are rw.  Then type 'groups' and verify that you are a member of group disk.  I'm a noob on raid, so maybe that's an issue, but the bottom line is, the physical disk device needs to be readable and writable by the user who runs vmplayer.  That also applies to the windowsxp.mbr file that you created.  Unless you changed the file permissions after creating it with the dd command, it's probably owed and read-only by by root.  Adjust as necessary.  Hope that helps.

---

### Post by eldragon on 2007-02-09
> **tcashin said:**
> You shouldn't have to create a disk group, it hopefully already existed, and your device nodes should be owned by the disk group.  You need to add the users who will run vmplayer to the disk group.  ls -l /dev/mapper/nvidia_geaeafee and verify that it is indeed owned by the disk group and that group permissions are rw.  Then type 'groups' and verify that you are a member of group disk.  I'm a noob on raid, so maybe that's an issue, but the bottom line is, the physical disk device needs to be readable and writable by the user who runs vmplayer.  That also applies to the windowsxp.mbr file that you created.  Unless you changed the file permissions after creating it with the dd command, it's probably owed and read-only by by root.  Adjust as necessary.  Hope that helps.

well, the disk group DID NOT exist. i did create it, my drive nodes were in fact owned by root and belonged to the disk group, yet it didnt exist.

i created the group, but you needed to logout-logon again in order to take effect.

now im having a second issue. which might probably be related to raid

my log goes as follows:

> 
Feb 09 09:14:05: vmx| DISKLIB-FLAT  : "/dev/mapper/nvidia_geaeafee" : failed to open (1638409): Couldn't get device facts.
Feb 09 09:14:05: vmx| DISKLIB-DSCPTR: Failed to open extents for descriptor file in normal mode
Feb 09 09:14:05: vmx| DISKLIB-LINK  : "/home/eldragon/Desktop/VMWARE/windows.vmdk" : failed to open (Inappropriate ioctl for device).  
Feb 09 09:14:05: vmx| DISKLIB-CHAIN : "/home/eldragon/Desktop/VMWARE/windows.vmdk" : failed to open (Inappropriate ioctl for device).
Feb 09 09:14:05: vmx| DISKLIB-LIB   : Failed to open '/home/eldragon/Desktop/VMWARE/windows.vmdk' with flags 0xa (Inappropriate ioctl for device).
Feb 09 09:14:05: vmx| DISK: Cannot open disk "/home/eldragon/Desktop/VMWARE/windows.vmdk": Inappropriate ioctl for device (1638409).
Feb 09 09:14:05: vmx| DISK: Failed to open disk '/home/eldragon/Desktop/VMWARE/windows.vmdk' : Inappropriate ioctl for device (1638409) 3023.
Feb 09 09:14:05: vmx| Msg_Post: Error
Feb 09 09:14:05: vmx| [msg.disk.noBackEnd] Cannot open the disk '/home/eldragon/Desktop/VMWARE/windows.vmdk' or one of the snapshot disks it depends on.
Feb 09 09:14:05: vmx| [msg.disk.configureDiskError] Reason: Inappropriate ioctl for device.


---

### Post by GeoffreyTransom on 2007-02-14
Thanks to those who posted here - especially the last few items on this thread since I also had no disk group and I had to create it and chown /dev/sda to myself to get VMWare to operate.

VMWare then worked perfectly... right up until the XP logon screen, which refused to proceed until I activated Windows. (I'm using a French version of Windows XP Home SP2). And of course because the internet connection was not initialised, windoze could not activate itself over the internet. (the connection is complicated on my machine... shared dialup for upload and satellite for download). 

There is no emoticon to properly express the frustration that WinXP has given me over the years and the chance to dispense as far as possible with Redmond Dross is something I am grabbing with both hands  - I only want the stupid thing on my machine to run two apps that have no Linux variant and which can't run under WINE. The two legacy apps are **TradeStation** - a futures platform - and skyDSL's  satellite connection software that our ISP requires.

Anyone else had this activation requirement? If so, what's the cure (I don't feel like ringing their help line).  {Update - it was my own copy of Windows... 300 Euros worth of trash)

Cheers,


GT
France

++ Update - VMWare is now working very nicely, with no noticeable performance degradation relative to a native desktop implementation of WinXP. Once I have transferred files across to the virtual machine,I will getrid of the WinXP partition for once and for all... ++

---

### Post by Repent on 2007-02-14
Guys I keep getting "are you root" how can I work around this?

Thanks.

---

### Post by yabbadabbadont on 2007-02-14
> **Repent said:**
> Guys I keep getting "are you root" how can I work around this?

Thanks.

Run: sudo -s -H

Then for all intents and purposes, you are root.  Don't forget to exit back to your normal user once you have finished the install.

---

### Post by Repent on 2007-02-15
OK now what?


joe203@joe203-desktop:~$ sudo apt-get install linux-headers-'kernel version'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-kernel version
joe203@joe203-desktop:~$

And how can I find the correct Boot images?

> Unfortunately, our ISO image will not have the bootable sector intact. We'll instead boot from a series of floppy images. My Windows 2000 disc included them in a "bootdisk" folder, whereas XP did not. For 2000, copy the four img files from it to our created folder.



With XP, you'll need some additional nonsense. Hunt down an appropriate set from Microsoft for your version of XP

Thank You

---

### Post by Repent on 2007-02-15
Bump please help!

---

### Post by yabbadabbadont on 2007-02-15
> **Repent said:**
> Bump please help!
Try:
sudo apt-get install linux-headers-`uname -r`

---

### Post by Repent on 2007-02-15
Thank you that helped, now I need to know how to get the boot image 

> Unfortunately, our ISO image will not have the bootable sector intact. We'll instead boot from a series of floppy images. My Windows 2000 disc included them in a "bootdisk" folder, whereas XP did not. For 2000, copy the four img files from it to our created folder.



With XP, you'll need some additional nonsense. Hunt down an appropriate set from Microsoft for your version of XP

Thanks
Edit; Would this be the same image that would be found on the boot disk?  I just downloaded a boot disk image from Microsoft.

---

### Post by Repent on 2007-02-16
Sorry for the BUMP but I really need this info.

---

### Post by zisteph on 2007-02-26
Hi everyone,

I have a dual boot configuration on my laptop, with Windows XP and Ubuntu Edgy running. I'm trying to run my Windows partition under linux using vmware player, but keep having some problems with the activation of Windows. The first time I ran Windows in vmplayer, I had to activate my copy of Windows, and did it on the phone. It worked fine. Then for some reason I booted under Windows directly, and was asked to activate it again! I did, but now it asks me to activate it when I start vmware player...

If I understand well, GeoffreyTransom had and fixed this problem recently (a couple of posts before), but I did not get how he did that... Any advice? I don't want to call Microsoft guys every morning, and I guess they won't activate it for me so many more times... :) 

Thanks!

Stephane

---

### Post by jackack on 2007-03-07
Hey guys...

Noob the boob here...

Great thread...helped me get XP running on Edgy, but then I had a problem with my ethernet card (windows didn't recognize it at all).  I didn't find the answer here or elsewhere and figured it out the hard way so maybe sharing my steps will help someone else avoid my particular pitfalls.

I created my virtual machine using EasyVMX [http://www.easyvmx.com/easyvmx.shtml](http://www.easyvmx.com/easyvmx.shtml) as mentioned in this thread (as opposed to qemu et al, as in the originally posted sugggestion) to allow installation directly from the XP cd.  Works a treat...as the brits would say...but I chose the IntelPro(yada) option for my ethernet card.  To make a long story short...choosing the "vmxnet" option for the virtual network device instead of Intel, and then installing vmware tools inside windows for the driver did the trick, and now after several reinstallations (including wiping the drive and reinstalling both ubuntu and windows) i am online and going through the godawful process of going from XP "the beginning" to SP2.  Good luck to ya! Here's to never booting windows again!

---

### Post by tcashin on 2007-03-08
> **zisteph said:**
> Hi everyone,

I have a dual boot configuration on my laptop, with Windows XP and Ubuntu Edgy running. I'm trying to run my Windows partition under linux using vmware player, but keep having some problems with the activation of Windows. The first time I ran Windows in vmplayer, I had to activate my copy of Windows, and did it on the phone. It worked fine. Then for some reason I booted under Windows directly, and was asked to activate it again! I did, but now it asks me to activate it when I start vmware player...

If I understand well, GeoffreyTransom had and fixed this problem recently (a couple of posts before), but I did not get how he did that... Any advice? I don't want to call Microsoft guys every morning, and I guess they won't activate it for me so many more times... :) 

Thanks!

Stephane

You need to set up separate hardware profiles in Windows for your "native" and "virtual" machines.  See [http://www.vmware.com/support/ws55/doc/ws_disk_hardware_profiles.html]("http://www.vmware.com/support/ws55/doc/ws_disk_hardware_profiles.html")
The VMTN site and forums has lot of good info. Browse around...

---

### Post by zisteph on 2007-03-09
Thanks, I'll look into this! :)

---

### Post by patond on 2007-03-19
OK I've run parted, edited my windows.vmdk file but how do I create windowsxp.mbr?

I have moved my edited copy of windows.vmdk and windows.vmx into a folder but what's windowsxp.mbr and how do I create it or copy it?  Copy it from where?  Help!

---

### Post by (4M)Stephen on 2007-04-13
I've followed the steps... and I went through a lot of pages of posts and I decided to let you guys know this...

for some reason the [http://free.oszoo.org/ftp/qemu/win32/release/QemuInstall-0.7.2.exe](http://free.oszoo.org/ftp/qemu/win32/release/QemuInstall-0.7.2.exe) DOES NOT EXIST!!!! it times out, I even tried eventually found another version... they must of deleted the dub domain... but here is the one I got:
[URL="http://www.oszoo.org/ftp/qemu/win32/release/QemuInstall-0.7.2.exe"]
http://www.oszoo.org/ftp/qemu/win32/release/QemuInstall-0.7.2.exe[/URL]

all that work to find it
PLEASE update the main page so others don't go through this trouble...

thank you

---

### Post by ranf on 2007-04-13
Stephen,

the only purpose for installing a win32 version of QEMU was for the creation of a .vmdk (VMware disk image).

AFAIK current linux versions of QEMU can do this too.

OTOH you can also use something like [http://easyvmx.com](http://easyvmx.com)

---

### Post by Unconscious on 2007-04-25
Since this thread started sooo long ago, and sooo much has changed since then. After reading about the mischigas that people are going through to get this to work, I went straight to the end, and tried to do this with files generated from easyvmx.com. 

When I run vmplayer form the command line, I get an error:

> /usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

but it seems to start up ok anyway. After the VM boots, this is what I get

> Network boot from Intel E1000
Copyright (C) 2003-2005  VMWare, Inc.
Copyright (C) 1997-2000 Intel Corporation

CLIENT MAC ADDR: 00 0C 29 4F 1D 3D   GUID: 564D7651-EBD8-97DF-FEFE-CAFDC34F1D3D
DHCP.._

...and the littel twinkie thing spins for a while. When it finally stops I get 

> PXE-E53: No boot filename received

PXE-M0F: Exiting Intel PXE ROM.

Then I get a warning box which says

> No bootable CD, floppy or hard disk was detected.
To install an operating system, insert a bootable CD or floppy and restart the virtual machine by clicking the Reset button.

Even thought there is a bootable Win 2k pro CD in the CD drive. 

I tried using vmxnet instead of the E1000, but still no joy.

So... Here's my .vmx file form easyvmx.com:

```
#!/usr/bin/vmplayer

# Filename: Win2000Pro.vmx
# Generated 2007-04-25;21:45:36 by EasyVMX!
# http://www.easyvmx.com

# This is a Workstation 5 or 5.5 config file
# It can be used with Player
config.version = "8"
virtualHW.version = "4"

# Selected operating system for your virtual machine
guestOS = "win2000pro"

# displayName is your own name for the virtual machine
displayName = "Win2000Pro"

# These fields are free text description fields
annotation = "Windows 200 Pro"
guestinfo.vmware.product.long = "Windows 200 Pro for vmplayer"
guestinfo.vmware.product.url = "http://www.easyvmx.com/"
guestinfo.vmware.product.class = "virtual machine"

# Number of virtual CPUs. Your virtual machine will not
# work if this number is higher than the number of your physical CPUs
numvcpus = "1"

# Memory size and other memory settings
memsize = "320"
MemAllowAutoScaleDown = "FALSE"
MemTrimRate = "-1"

# Unique ID for the virtual machine will be created
uuid.action = "create"

# Remind to install VMware Tools
# This setting has no effect in VMware Player
tools.remindInstall = "TRUE"

# Startup hints interfers with automatic startup of a virtual machine
# This setting has no effect in VMware Player
hints.hideAll = "TRUE"

# Enable time synchronization between computer
# and virtual machine
tools.syncTime = "TRUE"

# First serial port, physical COM1 is not available
serial0.present = "FALSE"

# Optional second serial port, physical COM2 is not available
serial1.present = "FALSE"

# First parallell port, physical LPT1 is not available
parallel0.present = "FALSE"

# Sound settings
sound.present = "TRUE"
sound.virtualdev = "es1371"

# Logging
# This config activates logging, and keeps last log
logging = "TRUE"
log.fileName = "Win2000Pro.log"
log.append = "TRUE"
log.keepOld = "1"

# These settings decides interaction between your
# computer and the virtual machine
isolation.tools.hgfs.disable = "FALSE"
isolation.tools.dnd.disable = "FALSE"
isolation.tools.copy.enable = "TRUE"
isolation.tools.paste.enabled = "TRUE"

# First network interface card
ethernet0.present = "TRUE"
ethernet0.virtualDev = "e1000"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddressOffset = "0"

# Settings for physical floppy drive
floppy0.present = "FALSE"

# Settings for physical CDROM drive
ide1:0.present = "TRUE"
ide1:0.deviceType = "cdrom-raw"
ide1:0.startConnected = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.autodetect = "TRUE"

# First IDE disk, size 4800Mb
ide0:0.present = "TRUE"
ide0:0.fileName = "Win2000Pro.vmdk"
ide0:0.mode = "persistent"
ide0:0.startConnected = "TRUE"
ide0:0.writeThrough = "TRUE"

# END OF EasyVMX! CONFIG

ide0:0.redo = ""
ethernet0.generatedAddress = "00:0c:29:4f:1d:3d"
uuid.location = "56 4d 76 51 eb d8 97 df-fe fe ca fd c3 4f 1d 3d"
uuid.bios = "56 4d 76 51 eb d8 97 df-fe fe ca fd c3 4f 1d 3d"

```

I also tried configuring the virtual BIOS and changing the boot order so that the CD is first. That didn't work either. It doesn't read the CDROM. Can anybody help me out?

Thanks.

---

### Post by ranf on 2007-04-26
You know the disk image you created is like a brand new hard disk. There is nothing to boot from on it.
That's why VMware tries other boot media, in your case it is PXE (booting over network).

I don't think choosing another NIC makes any difference.

What you should do is access the boot menu (IIRC it is Esc quite early) and then select the CD-ROM.

---

### Post by Unconscious on 2007-04-28
The CD IS set as the boot device in the boot menu. I just checked.

---

### Post by ranf on 2007-05-01
Hmm.

I haven't booted a real CD for months. I usually run directly from ISO files. Try adding this to your vmx file:
```

# Settings for the optional virtual CDROM, ISO-image
ide1:1.present = "TRUE"
ide1:1.fileName = "geexbox-1.0-en.i386.iso"
ide1:1.deviceType = "cdrom-image"
ide1:1.mode = "persistent"
ide1:1.startConnected = "TRUE"

```

The filename needs to match.

---

### Post by DarkGob on 2007-06-03
What should one do in the event that they only have a Windows XP upgrade disc?  Before my switch to Linux I was using a Windows 98 disc to confirm that I qualified for the XP upgrade.  I tried using an ISO of the 98 disc and changing the .vxm file when the install asked for it, but it didn't work, it said it couldn't read the disc.

---

### Post by TheFuzz4 on 2007-06-12
Just thought that I would let everyone know that this worked friggin great.  I need an XP installation so I can use MS Outlook and some other items for work mainly.  Once the day comes around that Linux can run the .NET framework smoothly then my days of MS will go away oh and when they come out with a e-mail client that works like Outlook does.  Other than that Ubuntu here I come :)  I just switched over this weekend and I'm loving it.  Can't get Beryl to work with my vid card but eh I'll live.  Trying to convince the wife that she should switch but she's too loyal to Windows.

---

### Post by tornado89 on 2007-07-22
I wonder if... is it possible to use my laptop's product recovery cd/dvd to install Windows XP and use it with vmware :confused: :confused: :confused:
don't know whether or not vmware is going to provide my original bios information so that the recovery cd/dvd would identify the laptop

---

### Post by bustherh on 2007-10-09
> **dryandplain said:**
>  The only screwiness left at this point is that we'll need to swap floppy images. When prompted, click on the floppy icon to "eject" the drive. In Nautilus, rename cdboot1.img to cdboot01.img and cdboot2.img to cdboot1.img, then click the floppy icon again to continue. It may sound a little strange, but you're essentially renaming the images to match that of the first file when it wants it. You'll get the hang of it, promise.

Once the floppies have done their thing, the ISO will take over and Windows will install normally.

OK I get stuck here, the windows installer is asking me for windows setup disk  #3 and I don't know what to do???

---

### Post by homburg on 2007-10-10
I had this error message as well and got rid of it.

In my case I had moved the appliance from a machine to another.

Seems one of the disk associated with the appliance could not be reached, so I opened the appliance in the server management console gui and removed all disks (harddrives, cd-rom's and floppys) from it, except the primary boot partition ofcourse.

I suppose it was only necessary to remove one of the harddrives, but my main goal was just to get rid of the error message and be able to boot the appliance, which I was.

---

### Post by elec999 on 2007-11-18
I tried installing vmware server, vmware workstation and vmware player and I keep on getting this when trying to install

giant@GiantQ:~/vmware-player-distrib$ sudo ./vmware-install.pl
Setup is unable to find the "more" program on your machine. Please make sure it
is installed. Do you want to specify the location of this program by hand?
[yes]
I checked the permissions. Still doesnt work. I dont even know how to set permission from terminal.
Thanks

---

### Post by jhyatt7823 on 2007-12-10
Does any one know where to get the bootable sector exe file from?

---

### Post by iammeagain on 2008-01-04
[SIZE="3"]I saw a couple problems with increasing screen resolution so the way I fixed mine was:


!. Downloaded vmware workstation

2. Extracted it

3. Went to /ExtractedFolder/vmware-distrib/lib/isoimages

4. Under this there was a file windows.iso This is a cd image of vmware tools. 

5. I edited my virtual system's .vmx and added/replaced ```
ide1:0.fileName = "/ExtractedFolder/vmware-distrib/lib/isoimages/windows.iso"
ide1:0.deviceType = "cdrom-image"
```

6. Then when I booted the virtual system with VMware player I opened the cd under My computer. The cd is labeled VMware Tools. This started an install, i just went with a complete install. Once it was done and it restarted the virtual system everything seemed to work fine.[/SIZE]

[COLOR="Red"]

Side notes:[/COLOR]

I am using VMware Player 2.02 

Guest OS is Windows 2000, installed from iso

host is Ubuntu 7.10

I just used a text editor to edit .vmx

I did not use Qemu (sp?) But downloaded a prebuilt image  and change the virtual hard drive with a blank ide 20GB virtual harddrive also prebuilt
 IDE was important because windows doesn't like installing to SCSI
links for above 
[http://www.vmware.com/appliances/directory/345](http://www.vmware.com/appliances/directory/345)
[http://www.ffnn.nl/pages/articles/linux/vmware-player-image-creation.php](http://www.ffnn.nl/pages/articles/linux/vmware-player-image-creation.php)

The original idea to use an already built system came from [url]http://www.hackaday.com/2005/10/24/how-to-vmware-player-modification/
[/url]

VMware tells you VMware player is not capapble of this, but it is.[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=340](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=340)

Maybe part of this could be placed in OP to help people out with resolution issue.

---

### Post by evfan42 on 2008-01-08
```
michael@michael-desktop:~$ wine qemu-img.exe create -f vmdk WindowsXPPro.vmdk 2G Formating 'WindowsXPPro.vmdk', fmt=vmdk, size=2097152 kB
wine: could not load L"c:\\windows\\system32\\qemu-img.exe": Module not found

```

well this is the error I got when trying to make the file for the 2 gig disk... any suggestions?

---

### Post by kokomonjo on 2008-01-11
Hi, I am new to Ubuntu, I have 7.10 amd64 version. I need to get VMware player installed on it. I am not sure how to if anyone could help that would be great. I tried to add with the Add/Remove program but said i couldnt because it was using a 64-bit version. Also i tried the tutorial at the very beginning of this thread and this is what i got

"matt@kokomonjo:~$ apt-get install build-essential
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

 how do i fix this?

Thanks guys!

---

### Post by Linja on 2008-01-12
That would indicate that you do not have permission to issue administrative commands. Always put  sudo before such commands. Then enter your password when requested.

---

### Post by Squizz on 2008-01-12
Or that you have another program open that is using the lock - such as Symantic.

[HERE]("http://www.simontucker.net/news.php?item.5.3") is my experience of installing VMWare if it helps.

---

### Post by Dirtilus on 2008-01-19
Any info on installing Windows XP Pro if you have an upgrade CD? The installation starts fine, and there is nothing I don't know what to do when it asks for the previous version. I have both cds and both iso's.

Dan

---

### Post by Oblacone on 2008-01-29
Do You have to have a copy of windows XP to use it in VMware?:cry: cause i dont have a copy of windows:(

---

### Post by GamingMazter on 2008-01-29
Thanks so much! I really wanted to install XP in VMware but didn't wanna try until I found a good result. Cheers!

---

### Post by darkline on 2008-01-31
Brilliant how to and all. Without it i would have got Vmware working.
But is it possible to view data on your actual hard drives? (more specifically a NTFS partition i have mounted at /media/sda1). I need to use the files from it on here, they aare part of he reason i wanted VMware in the first place. How can i transfer them?

---

### Post by rakesh20_patel on 2008-02-29
I m using VMware workstation 6.0.2 and i have Xp installed in VMware machine and i want to Uninstall it....plese help

---

### Post by iaretehwin on 2008-05-16
I successfully installed WinXP on VMWare Player using EasyVMX 2.0, and it works relatively well, though it's a little slow. The major issue I'm having is that Windows apparently lacks a network card driver, so I get the little yellow question mark next to the device name. Networking obviously works on Ubuntu, so I'm not sure what's wrong. Networking is set to NAT. Here is the vmx file: ```
#!/usr/bin/vmplayer

# Filename: XP.vmx
# Generated 2008-05-16;05:21:14 by EasyVMX! 2.0 (beta)
# http://www.easyvmx.com

# This is a Workstation 6 config file
# It can be used with Player
config.version = "8"
virtualHW.version = "6"

# Selected operating system for your virtual machine
guestOS = "winxppro"

# displayName is your own name for the virtual machine
displayName = "XP"

# These fields are free text description fields
annotation = "XP for iTunes, USB devices"
guestinfo.vmware.product.long = "Windows XP"
guestinfo.vmware.product.url = "http://www.easyvmx.com/"
guestinfo.vmware.product.class = "virtual machine"

# Number of virtual CPUs. Your virtual machine will not
# work if this number is higher than the number of your physical CPUs
numvcpus = "1"

# Memory size and other memory settings
memsize = "1024"
MemAllowAutoScaleDown = "FALSE"
MemTrimRate = "-1"

# PowerOn/Off options
gui.powerOnAtStartup = "FALSE"
gui.fullScreenAtPowerOn = "FALSE"
gui.exitAtPowerOff = "FALSE"

# Unique ID for the virtual machine will be created
uuid.action = "create"

# Settings for VMware Tools
tools.remindInstall = "TRUE"
tools.upgrade.policy = "upgradeAtPowerCycle"

# Startup hints interfers with automatic startup of a virtual machine
# This setting has no effect in VMware Player
hints.hideAll = "TRUE"

# Enable time synchronization between computer
# and virtual machine
tools.syncTime = "TRUE"

# USB settings
# This config activates USB
usb.present = "TRUE"
usb.generic.autoconnect = "FALSE"

# First serial port, physical COM1 is available
serial0.present = "TRUE"
serial0.fileName = "Auto Detect"
serial0.autodetect = "TRUE"
serial0.hardwareFlowControl = "TRUE"

# Optional second serial port, physical COM2 is not available
serial1.present = "FALSE"

# First parallell port, physical LPT1 is available
parallel0.present = "TRUE"
parallel0.fileName = "Auto Detect"
parallel0.autodetect = "TRUE"
parallel0.bidirectional = "TRUE"

# Sound settings
sound.present = "TRUE"
sound.fileName = "-1"
sound.autodetect = "TRUE"

# Logging
# This config activates logging, and keeps last log
logging = "TRUE"
log.fileName = "XP.log"
log.append = "TRUE"
log.keepOld = "3"

# These settings decides interaction between your
# computer and the virtual machine
isolation.tools.hgfs.disable = "FALSE"
isolation.tools.dnd.disable = "FALSE"
isolation.tools.copy.enable = "TRUE"
isolation.tools.paste.enabled = "TRUE"

# Other default settings
svga.autodetect = "TRUE"
mks.keyboardFilter = "allow"
snapshot.action = "autoCommit"

# First network interface card
ethernet0.present = "TRUE"
ethernet0.virtualDev = "e1000"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddressOffset = "0"

# Settings for physical floppy drive
floppy0.present = "FALSE"

# Settings for physical CDROM drive
ide1:0.present = "TRUE"
ide1:0.deviceType = "cdrom-raw"
ide1:0.startConnected = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.autodetect = "TRUE"

# First IDE disk, size 25Gb
ide0:0.present = "TRUE"
ide0:0.fileName = "XP.vmdk"
ide0:0.mode = "persistent"
ide0:0.startConnected = "TRUE"
ide0:0.writeThrough = "TRUE"

# END OF EasyVMX! CONFIG

extendedConfigFile = "XP.vmxf"
virtualHW.productCompatibility = "hosted"

ethernet0.generatedAddress = "00:0c:29:11:66:af"
uuid.location = "56 4d 2a 9a 12 22 bc 4b-29 ef ae c7 f4 11 66 af"
uuid.bios = "56 4d 2a 9a 12 22 bc 4b-29 ef ae c7 f4 11 66 af"
ide0:0.redo = ""
checkpoint.vmState = "XP.vmss"
ethernet0.pciSlotNumber = "16"
sound.pciSlotNumber = "17"
parallel0.startConnected = "FALSE"
```

Any ideas, previous experiences, things I can try, etc would be appreciated.

---

### Post by rrgv on 2008-06-26
just change ethernet0.virtualDev = "e1000"  by ethernet0.virtualDev = "vlance"

regards
rafael

---

### Post by imjscn on 2008-07-01
iaretehwin,
I had the same problem, solved by change the intelPro1000(default) to vemnet. intelPro1000 is for vista.

---

### Post by imjscn on 2008-07-01
My guest can share internet with host, but can't open host's shared folder.

I setup a new account "sandbox" without login privileges and set a password
sudo smbpasswd -a sandbox

Now the guest can ping host but the host doesn't accept the password. In case I input wrong password, I go to Users and Groups and changed the sandbox's password, but new password doesn't work either.

in Samba's smb.conf , I have the security setting:
bind interfaces only = true
interfaces = vmnet0 vmnet1 vmnet8

what's the problem?

---

### Post by yogibaer on 2008-07-07
hi Guys

this tutorial works almost fine for me.

I created a 10GB vmdk-File and the booting also works.

But after formating the partition and copying the installation files, the WinXPPro Setup restarts the machine. After restarting i got this message:

> 
Non-System disk or disk error
Replace and press any key when ready


What I have to do now?

Can anybody help me?

thanks a lot

yogi

EDIT: Ok i got it. Just have to unmount the floppy ^^

---

### Post by ramaswamyps on 2008-07-11
i got a cd boot image for windows 2000 
the cd boots up ok
how can i replace the floppy part of the VMplayer as i dont have a floppy drive in my laptop tecra9000.
what are changes needed in the .vmx file given in the forum thread for windows2000 installation in vmplayer?
help needed.
i haave done upyo iso creation of win2000.
vmplayer runs and cannot boot any windows right now.

---

### Post by jazzcommunication on 2008-07-17
vmplayer has its own bios setup menue, when starting a virtual machine, you have to push ctrl g and f2 very fast (simply reset the vm a few times), then in the "vm bios setup" you can change boot sequence and so on.... make sure you have a bootable winxp cd (not the same as autostart) visit this link for how to make a bootable winxp cd
 [http://www.nu2.nu/bootcd/](http://www.nu2.nu/bootcd/) 
now you can install xp in your VM :) no problems

Success

---

### Post by Hobo992 on 2008-08-06
I get an error saying 

"File not found: WindowsXPPro.iso

This file is required to power on this virtual machine.  If this file was moved, please provide its new location."

Could you help me?

---

### Post by OisinT on 2008-08-10
I've made it a bit into the steps, but when I get here
```
wine qemu-img.exe create -f vmdk WindowsXPPro.vmdk 2G Formating 'WindowsXPPro.vmdk', fmt=vmdk, size=2097152 kB
```

I get this error:

```
oisint@OisinT1:~$ wine qemu-img.exe create -f vmdk WindowsXPPro.vmdk 2G Formating 'WindowsXPPro.vmdk', fmt=vmdk, size=2097152 kB
wine: could not load L"c:\\windows\\system32\\qemu-img.exe": Module not found

```

---

### Post by Hobo992 on 2008-08-19
Help i'm root but 

hobo992@hobo992-desktop:~$ apt-get install linux-headers-'kernel version'
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
hobo992@hobo992-desktop:~$ apt-get install gcc-3.4
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
hobo992@hobo992-desktop:~$ apt-get install g++-3.4

thanks.

---

### Post by bjhom on 2008-08-21
> **Hobo992 said:**
> Help i'm root but 

hobo992@hobo992-desktop:~$ apt-get install linux-headers-'kernel version'
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
hobo992@hobo992-desktop:~$ apt-get install gcc-3.4
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
hobo992@hobo992-desktop:~$ apt-get install g++-3.4

thanks.

I believe that you need to put a 'sudo' in front of you apt-get

---

### Post by Hobo992 on 2008-08-22
i tried putting the codes in one at a time and it gave me this:

hobo992@hobo992-desktop:~$ sudo apt-get install linux-headers-'kernel version'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-kernel version

---

### Post by fahadsadah on 2008-08-25
Why the hell don't you use VMWare Server? It's free and runs a full VM instantly, no hassle.

---

### Post by patience1312 on 2008-12-29
Hi!

I went the whole thread through, but I can't find a solution for mine. 

I still have the 2 gigabyte limitation problem, even when changing the line from 2GB to 12GB, there is always a file with 1,3 MB created, when installing windows there are only 2GB available. 

With the vmware Player I cannot resize it, qemu isnt opening, the error message is about a wrong path, like it was searching for the program in system 32, where I didnt install it, even when installing qemu in the folder "system32" it doesnt work.

Help! 

Thanks for that, I know, it's an old thread :)

PS: Im a noob

---

### Post by speedygonzalas on 2009-02-21
hey i'm really new to linux and command lining in general, now i downlaoded everything, and i tried to install vmware player, which went well until it said that it had to build a new kernel and failed to (because i didnt do the 
'apt-get install linux-headers-'kernel version''). so i did that got the headers, and now whenever i go to my command line and enter 'cd vmware-player-distrib' it just gives me 'bash: cd: vmware-player-distrib: No such file or directory' even though its on my desktop and my terminal is right now based on my desktop, can anyone help?

---

### Post by speedygonzalas on 2009-02-21
fixed...

---

### Post by speedygonzalas on 2009-02-21
i keep getting this problem whenever it tries to make a new vmmon module for my kernel 

```
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.27-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config3/vmmon-only/./include/x86.h:24,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:84:
/tmp/vmware-config3/vmmon-only/./include/x86paging.h:61:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config3/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:115:
/tmp/vmware-config3/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
make[2]: *** [/tmp/vmware-config3/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module. 
```

then it aborts, i tried matching the compilers mine seems to be gcc-4.3 instead of gcc-3.4 and im installing a different version 2.0.5 do i need to install different compilers or a whole new kernel?

---

### Post by speedygonzalas on 2009-02-21
sorry about the hard core culter

---

### Post by OldManRiver on 2009-02-23
All,

Following this procedure I get to:
```
cabextract 'nameofarchive.exe' -d 'our working directory'
```
and it blows up.

Yes I did understand the two strings above were marker which I needed to sub for.  My subs were:
```
'nameofarchive.exe' ==> '/home/iso-extract/Win2KPro.iso'
'our working directory' ==> '/home/iso-extract/files/'
```


Everything else has gone fine up to that line of code.  Is there a work around for this line or alternate method to extracting the file.

What about just loading from the CD?

OMR

---

### Post by jabeliscious on 2010-04-11
Why do you need to extract WinXpPro?

If you mount the .iso you can see the folder structure and extract what you need.

To mount an Iso, open with archive mounter (on my ubuntu desktop, its a right click option)

---

