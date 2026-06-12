---
title: "How to get a Wacom tablet working with linuxwacom working in Ubuntu 6.10 (Edgy Eft)"
date: 2006-11-20
forum: Outdated Tutorials &amp; Tips
---

### Post by euchrid on 2006-11-20
**_Introduction_**
After many, many hours trying to follow the [linuxwacom How-to]("http://linuxwacom.sourceforge.net/index.php/howto/main"), I finally got my Wacom Volito graphics tablet to work in Ubuntu 6.10 (Edgy Eft). My installation was brand-new, not an upgrade, and it was on a new hard-drive with absolutely nothing else on it. This should have meant it was an optimum environment.

The other guides that I followed either didn't work for me or didn't make any sense as a 'newbie' to both Linux and Ubuntu. When you first power up Ubuntu, the first thing you're going to want to do is make sure your hardware works. I don't have a mouse, so I *had* to get my pen to work.

This, then, is a guide for people who are either new and unused to Ubuntu/Linux, or for people who could not get their tablet to work by following any of the other guides. This is by no means a replacement for those other guides; it is intended as a helpful addition. Many of the points below may be helpful with other versions and flavours of Ubuntu and Linux, and possibly with installing other tablets.

Sometimes, it may look like I really hate linuxwacom or the How-to on the site. I don't. Once I understood it, I found it was actually helpful, informative, thorough and ultimately essential. The program itself is such a brilliantly useful thing that I could kiss the creator. What I express below are my frustrations at trying to understand what was going on and how to make it work. I think parts of the How-to are unnecessarily confusing, but on the whole it works very well. After all, *I* got it to work by following it. However, I have included my frustrations so that anyone in the same position can see that they are not alone and that it isn't 'them'.

**_1._** First of all, we will assume you have tried the advice at [https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom"). This was the first thing I tried, and it appears to be an easy solution for many people. It did nothing for me. I tried various permutations, and installed, as suggested, wacom-tools, xserver-xorg-input-wacom and also, after my initial failure to make this work, wacom-kernel-source. I installed through Synaptic and, when that didn't work, again through the terminal. Neither got the tablet working.

However, I discovered later on that editing the xorg.conf file can lead to some minor complications; editing the file with Gedit, I found another copy of xorg.conf was left in the /etc/X11 folder, but it was titled 'xorg.conf**~**'. That little '~' makes all the difference! Sometimes, the cursor was jumpy after restarting the computer, but deleting this extra xorg file stopped the jumpiness. I found that Ctrl+Alt+Backspace was not sufficient in this instance; I had to completely reboot. Once you are finished editing the xorg.conf file, check that /etc/X11 folder and make sure there is only the one in there!

****IMPORTANT NOTE HERE****: **_*DO NOT*_**_*UNDER ANY CIRCUMSTANCES*_ comment out the 'wacom' lines in your xorg.conf as instructed on the linuxwacom How-to. This completely killed my X-server, and, being a 'newbie', I was left having to work out how to sort things out using on ly the terminal (which I had little experience with). ***Leave the damn 'wacom' lines alone!*** It didn't cause me any problems leaving them in; but commenting them out meant I had to re-load Windows on my separate hard-drive in order to find out the solution on the internet. That was fun. Then I had to use 'nano -w /etc/X11/xorg.conf' to open up a terminal-based text editor to sort the xorg file out (a handy tip to remember - jot it down). Leave the xorg.conf alone now until you're instructed to alter it later on.

**_2._** Changing the lines in the xorg.conf file from 'wacom' to 'eventX' did nothing for me.  (Even when I definitely had the correct event number). 

I tried [linuxwacom]("http://linuxwacom.sourceforge.net/"). Partly because I was unfamiliar with Linux and Ubuntu, I simply installed the linuxwacom package as instructed on the site's How-to, and was dismayed to find, after many, many hours, that it simply didn't work. There are several possible reasons for this. I found that going in to Synaptic Package Manager and searching for 'wacom' brought up all the other Wacom packages I had installed. I removed them all **completely**. It also removes one of the xserver-xorg packages, but this did not matter; it was not essential. I suggest you do this first if you are having trouble getting linuxwacom to work.

Once wacom-tools, wacom-kernel-source and xserver-xorg-input-wacom are removed (having tried your best to make things work with step 1 above), **then** download linuxwacom, [as instructed on the site]("http://linuxwacom.sourceforge.net/index.php/howto/download").

**Do not**, at this stage, go any further than '2.2 Downloading the code'. This was where I went into _Newbie Hell_.

**_3._** It was not obvious to me, being new to Linux, that I had to install other packages, how to do it, or where to get them from, and I assumed that linuxwacom would simply 'work'. Certainly, the impression given on the site is *generally* one that 'this is all you need'. **It is *not*.** 

I have since found that it was not necessary, but I found some advice (which I can't find now) that suggested that a solution to one of the many problems I encountered trying to use linuxwacom was to download and compile the latest kernel. I would like to repeat here that **it is not necessary to download and compile a new kernel** in order to get linuxwacom to work - **HOWEVER**, I found it extremely helpful as a Linux 'newbie' to do this anyway. Downloading and compiling a new kernel was much easier than trying to get linuxwacom to work. 

Compiling a new kernel gets you in touch with your system, gives you a feeling of achievement, and gets things bang up to date. But you don't **need** to do it. It is, of course, one of the things I did, and I am sitting here with my Wacom Volito *working better than it did on Windows*. So stay with me.

I found a great guide for compiling a new kernel at [http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu"), but there are plenty of guides around.

**_4._** Whether or not you compiled a new kernel, there are other things you *will* need. The linuxwacom site tells you, on ['2.3 Configuring the Package']("http://linuxwacom.sourceforge.net/index.php/howto/config"), under the heading 'Library Dependencies - ncurses and XLib', that it needs 'ncurses' and 'XLib' in order to run (it doesn't quite tell you that in plain English, but you can work it out). 

When I first tried to follow the instructions, I did not really understand that I had to install anything else as well. I assumed, from lines like "Most distributions install the ncurses libraries by default, but the header files are often located in a separate package. You will need both. On Redhat 8.0, they can be found in the ncurses-devel RPM" that Ubuntu would already have everything I need.

Of course, one of the nice things about Ubuntu is that it doesn't fill your system up with junk and useless files - but no-one tells you, when you first start everything up, that there **will** be other programs and files you will need to install to get other programs to work. Coming from Windows, it's hard to get your head around this concept straight away.

I found it easiest (for a Linux 'newbie') to use Synaptic Package Manager for this. Open it up and search 'ncurses' and then 'xlib'. I found the easiest thing to do was to download everything that looked like it might possibly do something useful in helping to install linuxwacom, and then get rid of it afterwards. Depending on your own set-up, you may need more or less packages than I did. 

I also installed the 'gcc compiler', and, because it is mentioned in the output of linuxwacom when running, the 'g77 fortran' compiler. You probably have a better idea than I do what any of that stuff is for. I suggest that if, like me, you don't know what you're doing or what any of this stuff is, download everything that looks right. If you really know what you're doing, you probably don't need to read this particular guide anyway.

None of this will make any sense until you start up linuxwacom. We're not 'going there' just yet. I needed more before I could start... The output, when I ran the program, suggested I might need any of the following, all of which I searched for and installed through Synaptic (always the latest version, if there was a choice): mawk, gawk, g++, libtool, tcl, tk and xserver-xorg-input-evdev. Most of these were not with my initial installation of Ubuntu.

I have attached a list of everything installed on my computer (titled 'Synaptic Installations') for anyone who is just tearing their hair out and wants try installing all the same stuff that I have. I don't recommend this, as half of what I have is doubtless unnecessary, but it's there as a last resort.

**_5._**On the linuxwacom How-to, there is this little gem residing under '2.3 Configuring the package header': "For kernel 2.6, you need to configure the kernel modules (wacom and hid) under your kernel source directory before configuring linuxwacom." No, you don't. It took me *hours* to find out what this even meant. Normally, configuring kernel modules under your source directory would involve creating or using a Makefile, and running make with the relevant folder to build the modules. I did not do this. I simply ran the program. It seems to me that the necessary drivers/modules are loaded with the './configure' and 'make' commands anyway. There is nothing special to do here, but it had me trying all sort of things to 'configure kernel modules under my kernel source directory'.

**_6._** **Now** you can unpack and install linuxwacom. I finally unpacked mine under /usr/src, but it doesn't appear to matter too much where it is. It seems as good a place as any, because it's near the kernel, and easier to remember.

Follow the instructions at linuxwacom. They look complicated, but they're actually not as difficult as they look. They're there for every kind of Linux system, and so are not Ubuntu-specific. If you've got the latest kernel (at least later than 2.6, which you will have if you have Ubuntu Edgy (6.10)), then half of the instructions don't apply anyway. The best thing to do is make a nice hot cup of tea, and allow yourself *several hours* **at least**. You *will* make a mistake, there *will* be problems, but you *want* that cool little Wacom tablet to work, don't you?

Really, relax, it just isn't as bad as it looks on the instructions. Once you've unpacked linuxwacom as per '2.2 Downloading the code', you can either carry on reading (but not much will make any sense), or jump on down the instructions to 3.1 Testing tablet detection. Assuming you've remembered to plug your tablet into your USB port (or serial port), the system should detect your tablet OK. No matter how badly I messed things up or misconfigured them, this step always worked for me. It means that at least *something* knows your tablet is there and what it is supposed to do.

Forget all the other stuff and go down to 3.4 Building wacom.c. All you're really doing here is typing ./configure --enable wacom into a terminal. I had to use the '--with-kernel=/usr/src/linux-2.6.18.2' option, as the program did *not* find the correct location of my kernel. If in doubt about your kernel's location, guess. You can always keep re-compiling with other alternatives. At first I thought the kernel was under the /lib folder, and another piece of advice told me to compile just under the kernel headers (whatever they are). /usr/src *should* be, and looks right - but everyone's a little different.

A bunch of weird, incomprehenisble gobledegook will come spilling out after running './configure'. Use shift+PageUp to scroll up the output when it's finished. Check for error messages. I had loads the first few times, for a variety of reasons. If it's looking for something it can't find, I suggest making a note of whatever weird-sounding name it mentions ('gcc compiler' or whatever) and go back to Synaptic and find it or something relating to it. Install whatever looks good and try again. This hideously amateur trial-and-error method worked for me in the end. Try to be logical, and if that doesn't work, try pot luck. And then keep trying. It *will* work eventually.

If you end up without any error messages, then things are going OK. Type 'make' into your terminal as it tells you to in the How-to. If it comes out without errors, you're nearly there (sort of).

**_7._** You may, at some point, get an message when you run 'make' that reads: " ***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built." This made as little sense to me as it does to you. Especially if you spent all that time compiling a kernel. You look increduously at the screen. "_Now_ what?" 

Don't worry about it. It's a load of rubbish. It still spat this sentence at me on my successful set-up. When I first saw it, I thought it meant "Because you haven't enabled drivers as modules in your kernel config, although they have been requested, I will *not* be building them." I don't think it means this. I think it means: "Any drivers that are not enabled as modules in your kernel config that are requested through the configure command will not be built." It's just a case of bad (confusing) English. So, the program will only build driver modules that have been enabled. Who knows what that means? Who cares? As long as you have followed the steps above and at the linuxwacom site closely, you can ignore this message. After all, it is a ***Note***, _*not*_ a WARNING. 

**_8._** I got down to '3.5 Testing if wacom(k).o will load' with no problems. My kernel did not "bomb" (whatever that means). This section (3.5) says that, after running the command 'tail /var/log/messages' the resulting message should look something like:

```
0:34:41 ayukawa kernel: wacom.c: $1.43-0.7.6-2 Vojtech Pavlik <vojtech@suse.cz>
Nov 20 20:34:41 ayukawa kernel: wacom.c: USB Wacom Graphire and Wacom Intuos tablet driver (MODIFIED-DEBUG)
```

It goes on to say: "The correct version should also have the -0.7.6-2 portion as well. Also, future versions of the driver will say "LINUXWACOM-DEBUG" or similar rather than "MODIFIED-DEBUG" as shown above. This is to help differentiate between the stock kernel driver and those available from the Linux Wacom Project." 

The message I got did not have the -0.7.6-2 portion, nor did it say "LINUXWACOM-DEBUG" or 'similar'. All it said was 1.46 instead of 1.43. I still don't know if I got the correct driver or somehow 'got lucky' and accidentally installed one that happened to make everything work. I think, though, that this feature has not been added to the program; so don't worry if it doesn't have the -0.7.6-2 portion or any of the other jazz.

**_9._** If you're still here, then good. Things are going well still. We now move on to '3.6 Installing wacom(k).o'. The most important advice in this section, as far as I was concerned, was: "Installing the driver requires knowing where it belongs. A little research will help here."

I found the little wacom.ko devil (I mean driver) in no less than ***four*** places on my system. Whether this was simply because I have two kernels, or because I tried the wacom-tools route first, or because I tried linuxwacom four times before - who knows? But by this point, I was feeling a little reckless, so I replaced *every driver I could find*. Of course, I kept a backup, just as it advised. 

The kernel I compiled seemed to be in two parts - one labelled '2.6.18.2', the other labelled '2.6.18.2-custom'. The latter was due to the advice given on the site explaining how to compile a new kernel. I also had the old kernel. I've got stuff all over the place, but it doesn't matter as long as my Wacom works. I cannot advise you to replace all of your wacom.ko drivers, but I also cannot see what harm it would do. I found the driver turn up under /lib/modules and under /usr/src/linux-2.6.18.2 *and* in the unbelievably complicated location of: /usr/src/linux-2.6.18.2/debian/linux-image-2.6.18.2-custom/lib/modules/2.6.18.2-custom/kernel/drivers/usb/input/
I have no idea how all those folders got created or what the driver's doing in there. Just wanted to let you know that it might all look complicated and make no sense, but for me, replacing *all* the wacom.ko drivers was one of the things that helped to make my tablet work.

**_10._** If 'depmod -e' went OK, then you're ready for the next problem. I got really stuck on '3.7 Loading the Wacom Driver'. I do not have any modules called 'input' or 'mousedev'. Because they are highlighted in blue, I assumed they were only used in older 2.4 kernels. But I also didn't have any modules called 'usb-uhci' or 'usb-ohci', and no sensible-looking variations, either. This was one of the biggest obstacles to getting the tablet to work.

Eventually, I found a module (or something) called 'uhci-hcd'. It looked close enough. I ran the command 'modprobe uhci-hcd'. It worked. To find this out, by Googling for answers, thinking and scouring forums, took me *hours*. The rest of the commands ran through fine (I just missed out 'mousedev' and 'input', and I guess I was right in that they are only for older kernels).

**_11._** Forget all about building hid.core or usbhid or anything; none of that is necessary if you're on a 2.6 kernel, even though it suggests in the title - '3.9 Building (usb)hid.ko (for kernel 2.6)' - that it would be necessary (and then goes on to say it isn't necessary and then, at the time of writing this, shows a php error, missing out all the instructions.

Running the command 'grep -i 56a /var/log/messages | tail -10' under '3.10 - Unknown Tablet?' did not show me the device identifier, or anything of any use to me. In the end, it didn't matter. Don't worry about it.

Everything else should be OK. Every time I viewed the output of 'tail /var/log/messages' I did not get what the site suggested. (It suggests you will see 'v1.43-0.7.6-2 Vojtech Pavlik' in the output, but I only ever got 'v1.46'. Again, don't worry about it.

wacdump wouldn't work by typing './wacdump', but just 'wacdump' (without the './') worked fine.

**_12._** The next problem for me '5.1 - Adding the InputDevices'. This is where, as I mentioned about six years ago at the top of this How-to, the xorg.conf file might end up getting replicated. ***Check your /etc/X11 folder!***

**_13._** ***THIS IS AN INCREDIBLY USEFUL TIP FOR WACOM VOLITO (1) USERS***: 
In the xorg.conf file, under the 'stylus' section, add this line:   
```
Option 	"Stylus2" 	"3".
```
This is what my xorg.conf file looks like:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mouse0"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/event2"   
						      # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option 	"Mode" 		"Absolute"
  Option 	"Stylus2" 	"3"
  Option	"USB"		"on"
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/event2"  
						      # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option	"USB"		"on"
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/event2"  
						      # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option 	"Mode" 		"Absolute"
  Option	"USB"		"on"
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection
```

What does the magic line 
```
Option 	"Stylus2" 	"3".
```
do? You will love me for this. You will want to kiss me. I almost want to kiss myself. I worked it out all on my own after searching for it for hours with no success.
***It sets the button on your pen to right-click.***

I could not find *anything* **anywhere** that would tell me how to do this. There is a vague kind of nod to it hidden in the depths of the linuxwacom pages, but it doesn't mention this specifically. *Even if you haven't got linuxwacom installed, you can still use this in your xorg.conf file.* There is some other advice out there which suggests you can use "Button2" instead of 'my' "Stylus2" - but that did nothing for me.

Of course, once things are up and running, you can also achieve this through wacomcpl - but I had some problems with that too.

**_14._** In the first four attempts to make this work, everything *looked* OK; 'make' and everything else had worked with no errors - but I couldn't get xsetwacom or wacomcpl to find my pen - even though my Volito was working like a bad mouse and the rest of Ubuntu could relate to it. I think the crucial steps were the loading of the wacom.ko driver(s) in the right place(s) and using 'uhci-hcd' instead of 'usb-uhci/ohci'. Hopefully, if you've followed everything above, you should now also be able to get wacomcpl and xsetwacom up and running. I found wacomcpl much easier and more immediate.

Now I have everything up and running, my tablet works *** better*** than it did under Windows, as I now have more control over it - plus, I have a better idea of how it works.

Everything else in the linuxwacom How-to worked fine for me - I hope it does for you too. The only other thing I found was that it didn't work by just restarting X - in fact, that has never worked when advised to do so in relation to the Wacom tablet. I have found it necessary to completely re-boot each time, especially in the case of getting rid of the extra xorg.conf file.

As for setting up in Gimp and Inkscape, the guide at [https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom") worked fine for me once everything was working.

I would say that if xsetwacom or wacomcpl are not working but everything else is OK except for one or two annoying things, then either go back to the start or make sure that you've taken out the wacom-tools and related packages and that you've uncovered (and replaced) all the drivers on your system.

Lastly, a massive thank-you to everyone at linuxwacom for doing such a great job, and my apologies if I sounded bitchy above; I really appreciate all the hard work that's gone in to this project, and was impressed enough by the end result to write this guide out for other idiots like me (plus those who are just lost and confused). And a big thankyou to whoever's contributed to the Wacom Wiki guides for Ubuntu (especially the Gimp and Inkscape stuff that was so easy to follow).

If you're still stuck or have some other advice or whatever, then reply to this post or feel free to send me a message. Good luck!

---

### Post by anacron on 2006-12-12
I today tried to plug my wacom into my linux, and whoops what is this.. it didn't work.. hmm but it did work in dapper? :-k

so with few seconds of googling I ended up in here and well it seemed like you dond't really know what's the solution to fix this, because you have such  much text... (it did look so long that I was too lazy to even read it :-D )

it seems that edgy has somekind of bug with wacom, but people are only advising to get new module for wacom if you have volito2, I have the version 1, but it didn't matter, I tried it anyway and it **did work!**

so what I think you need to do is to do this:

FOR LAZY PEOPLE:
```
wget -c http://librarian.launchpad.net/4936142/wacom.ko && sudo modprobe -r wacom && sudo mv /lib/modules/2.6.17-10-generic/kernel/drivers/usb/input/wacom.ko /lib/modules/2.6.17-10-generic/kernel/drivers/usb/input/wacom.ko_backup && 
sudo cp wacom.ko /lib/modules/2.6.17-10-generic/kernel/drivers/usb/input/ && sudo modprobe wacom
```

and then maybe restart x? (i didn't have to)

for people with more time ;) 

get the new wacom driver for your kernel
```
wget -c http://librarian.launchpad.net/4936142/wacom.ko
```

then we unload the old driver with:
```
sudo modprobe -r wacom
```

I wanted to do backup of it, in case something goes wrong and i want it back, so i did:
```
sudo mv /lib/modules/2.6.17-10-generic/kernel/drivers/usb/input/wacom.ko /lib/modules/2.6.17-10-generic/kernel/drivers/usb/input/wacom.ko_backup
```

then i copyed the new driver to right path with:
```
sudo cp wacom.ko /lib/modules/2.6.17-10-generic/kernel/drivers/usb/input/
```

load the new driver with:
```
sudo modprobe wacom
```

in this part it did work with me withouth rebooting x, but you might have to? also if you already don't have wacom tools, you should get them with
```
sudo apt-get install xserver-xorg-input-wacom wacom-tools
```
but i beleve those are installed by default in edgy

well good luck guys, I hope this saves your time, as it did for me ;)

---

### Post by euchrid on 2006-12-15
I can concur with the above; for Edgy Eft, you SHOULD NOT need my lengthy instructions (which I wrote before the current update problems and new advice came to light) - you should only need to replace the module as advised by anacron above. If only I'd known sooner... Anyway, I will leave this page here in case future updates cause yet more problems!

---

### Post by H4rm0ny on 2006-12-15
Just posting thanks for this How To and a note to anyone else who found that the latest upgrade broke their wacom installation. I don't know why or how this happened, but after the last update with Synaptic that brought down a new kernal, my Wacom Volito2 tablet was dead. None of the usual How To's fixed it, but the non-lazy approach above got it working again, without even having to restart X.

Cheers!

-H.

---

### Post by MetalMusicAddict on 2006-12-15
euchrid. I wished you would have worked with me to improve my longstanding [HOW-TO]("http://www.ubuntuforums.org/showthread.php?t=25151"). :)

---

### Post by Highlag on 2006-12-17
Upgraded from Daper to Edgy and trying to make my Volito 2 working. 
I tried "slow" version upgrade and got  the following error:

cannot stat `/lib/modules/2.6.17-10-generic/kernel/drivers/usb/input/wacom.ko': No such file or directory

I found out that folder 2.6.17-10-generic is actually 2.6.17-10-386 and am now getting error 
wacom.ko permission denied. 

I tried changing permissions: chmod a=rwx  wacom.ko but no avail. 

Any ideas?

---

### Post by xscd on 2006-12-17
**Bravo** Euchrid, for not only having the patience and perseverance to accomplish your goal despite numerous confusing and frustrating obstacles, but for writing about it to help others who wish to follow the same path, and with a sense of good humor.
:)

I think I can add a few comments as a normal Linux user (not a programmer) that may help to demystify some of the terminology and concepts that new users can find very difficult and frustrating, based on my 10 years of Linux use so far.

Regarding Wacom tablets, there are three bits of software that pertain:
[LIST=1]
[*]the kernel module (wacom.ko on 2.6 kernels)
[*]the Xorg driver (wacom_drv.so (for newer Xorg server) or wacom_drv.o (for older Xorg server))
[*]the udev rules to create the 'device node' for the system to read data from (this is what the 'wacom-tools' package installs)
[/LIST]

The kernel module is a program that the Linux kernel "attaches" to itself any time it senses a need for it, because it discovers new hardware for example and needs some way to communicate with that hardware and make it usable and useful for the various higher-level programs that a user typically runs. It is the kernel's primary responsibility to "understand" the hardware attached to the computer and to be able to shuffle data to and from that hardware. If that "understanding" for any particular hardware is not built into the kernel, it needs to be available as a module that can be dynamically loaded into (attached to) the kernel at any time.

There are many, many kernel modules available for all kinds of hardware, and because there are so many different hardware devices on the market, and because any typical Linux user will only have a small number of those inside or attached to his or her computer, the software to be able to use those hardware devices is usually provided as a module instead of being included within the Linux kernel itself. If all that functionality **were** to be included within the kernel, it would be staggeringly huge and perhaps cumbersome, so the idea of having little bits of kernel code that would be incorporated into the running kernel **as** it ran and **only** when the kernel needed it, was a very good idea and resulted in the creation of kernel modules.

The second thing in the list above is the Xorg driver. Xorg (or the older XFree86) is what supports the GUI (graphical user environment) for Linux, whether that GUI is Gnome, KDE, Fluxbox or whatever. Xorg uses the Wacom tablet driver to **interpret** the raw data provided by the Wacom kernel module, so that the movement of the stylus and pressure on the tablet and pushing of buttons on the stylus and tablet will actually **do** something within Gnome or KDE and the programs a user runs, such as the Gimp or Inkscape.

Remember, the Linux kernel is only responsible for recognizing hardware and shuffling data to and from hardware. The kernel typically simply makes the data from the hardware **available** for other programs to read. The kernel doesn't do much else (well, it does a lot, but that's a long story that I know very little of, and I'm trying to keep my comments simple and easy for new Linux users to understand).

Now, an important concept in Linux (and in FreeBSD and in all computer operating systems descended from or influenced by the original Unix) is this: the way that data goes from anywhere or to anywhere, within a Linux system, is for the Linux kernel to "read" from or "write" to a **file**, a simple data file. This is an abstraction agreed to from the very beginning, that all hardware should be made to look and act like a simple file within an operating system. The data is directed to or received from a certain file (explained in the next sentence), and it is the kernel's job to know which physical device to send the data to or read it from. The way the kernel does this is to associate each piece of hardware, such as a hard disk, with one of the special "files" in the /dev directory within Linux.

When a program such as OpenOffice saves a document to a hard disk, it is actually directing the data to a "file" (a device file in the /dev directory), and the kernel knows, by association, exactly which specific hard disk to send that data to. It's actually more complicated, because a hard disk, although treated like a file in many respects, has been formatted with a filesystem (like ext3) to keep track of many user-created files within the one large general file that the hard disk is viewed as, from one point of view, by the kernel.

Bearing the above in mind, the third thing on the list above is the wacom-tools package, which attempts to automatically create the **device file** as explained above, for the Xorg Wacom driver to read data from. Wacom-tools attempts to do this by examining what the kernel is doing, finding what actual device has been created to communicate with the Wacom tablet (such as /dev/input/event2), and then dynamically create a "symbolic link" to that device (another name for the same device) called /dev/input/wacom. In that way, regardless of what the real device is, if one refers to the device (in the xorg.conf file, for example) as /dev/input/wacom, then the Xorg Wacom driver will be able to read data from the real device file, because /dev/input/wacom will always (or **should** always) point straight to the real device file (/dev/input/event2 or whatever). Remember, the link is just another name (that stays constant and consistent) for the actual device file that the Wacom is being represented by (which can vary, but which the user can find out, of course).

OK--that was a **lot** of explanation! I hope it cleared up to some extent a few basic Linux concepts that confuse new users.

The other thing I noticed that Euchrid had some difficulty with is the process of compiling source code. the LinuxWacom project produces source code, which is the program(s) as written by humans in a programming language such as C++. That code needs to be compiled by the Linux user into a binary code that his kernel can understand and execute. This process in Linux has become fairly standardized and streamlined to a degree, using the configure script and the GNU "make" utilities that typically come with the unpacked source code. However, when programs are compiled, they often must look at the running system and other programs that are installed on the running Linux system in order to make good decisions about how to be compiled on that specific computer. This means that the Linux user must usually have certain other source code installed on their computer in order for the compilation of the code they wish to install to be successful.

The linuxwacom project's code wants to create both the kernel module (item number 1 in my list above) and the Xorg driver (item 3 in the list). But it can only compile the kernel module if it can examine the source code of the kernel that the user is running at the time. The trouble is, most Linux users just have an already-compiled kernel running; they did not download the kernel source code and configure and compile and install it themselves.

So, for the sake of the linuxwacom project's source code, a user must download the source code for the kernel he or she is using at the time, or install it using apt-get or (more easily) synaptic. The kernel source code is (by convention) deposited into the directory /usr/src/. But it is usually a bzipped tar file (a compressed archive) which needs to be manually unzipped by the user (decompressed with the program bunzip2), then extracted from the resulting decompressed tar archive using the tar command.

This whole process is somewhat confusing for new Linux users. As Euchrid mentioned, it was **not** necessary to compile a new kernel. It was only necessary to have the source code for his running kernel and the kernel headers, unpacked into /usr/src for the linuxwacom configure script to be able to find and examine.

I hope these few comments will be helpful to others. And once again Euchrid, your "voyage of discovery" regarding this issue, with all of the reading, research and discriminating thought it required, is very impressive and admirable.
:)

By the way, if you had had the kernel and kernel-headers source code for the kernel that your system is using already installed and unpacked into /usr/src, the wacom-kernel-source package, installable via synaptic or apt-get, would have been able to install itself correctly in the first place, and I believe that the latest version of the wacom-kernel-source package available from the Ubuntu repositories is the same, up-to-date version that you downloaded from the linuxwacom project and installed manually.

The thing to remember, if one wishes to take the easy way and install the three Wacom-tablet related packages (wacom-kernel-source, wacom-tools and xserver-xorg-input-wacom) using synaptic, is to **first** use synaptic to install the kernel source code (or perhaps just the kernel headers source code) **for the kernel version one is actually using** (type the command: uname -a in a terminal window to find out what that version is), and make sure that source code is unpacked (using bunzip2) and extracted from its archive (using tar) in an appropriate location (usually /usr/src).
:)

---

### Post by Hoshimaru on 2007-01-29
I've followed all the steps from linuxwacom's website and built a working wacom.ko
The tablet is working, but not with tablet functionality. It is as if I'm using a regular mouse.
I also replace wacom_drv.so with linuxwacom's prebuilt version.

Now, when I open gimp and go into the preferences, I don't have any extended device.
xsetpointer -l also doesn't show stylus, eraser and cursor as it should following the howto on their website.

```
$ xsetpointer -l
"pointer"       [XPointer]
"keyboard"      [XKeyboard]

```

/var/log/message contains this output:
```
Jan 29 21:03:13 naruto kernel: [17180697.504000] usbcore: deregistering driver wacom
Jan 29 21:03:27 naruto kernel: [17180712.432000] input: Wacom Volito as /class/input/input5
Jan 29 21:03:28 naruto kernel: [17180712.496000] usbcore: registered new driver wacom
Jan 29 21:03:28 naruto kernel: [17180712.496000] /home/jcapraro/Source/linuxwacom-0.7.6-4/src/2.6.16/wacom_sys.c: v1.46:USB Wacom Graphire and Wacom Intuos tablet driver

```
That last line is worrying me a little. Why does it make a reference to that .c file? (that directory has been removed after installation)

My xorg.conf looks like this. It's not very different from other people's isn't it?
```

```

And the Xorg log...
```
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.6-4 $
(**) stylus: always reports core events
(**) stylus device is /dev/input/event3
(**) stylus is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) stylus: reading USB link
(**) WACOM: PressCurve 0,5,95,100
(**) Option "BaudRate" "9600"
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/event3
(**) eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) eraser: reading USB link
(**) WACOM: PressCurve 0,5,95,100
(**) Option "BaudRate" "9600"
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/event3
(**) cursor is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) cursor: reading USB link
(**) Option "BaudRate" "9600"
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(azerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+be+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
Synaptics DeviceInit called
SynapticsCtrl called.
(**) Option "Device" "/dev/input/event3"
stylus Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Volito tablet speed=9600 maxX=5104 maxY=3712 maxZ=511 resX=50 res
Y=37 suppress=2 tilt=enabled
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=5104 bottom Y=3712
(==) Wacom device "eraser" top X=0 top Y=0 bottom X=5104 bottom Y=3712
(==) Wacom device "cursor" top X=0 top Y=0 bottom X=5104 bottom Y=3712
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event1
(**) Option "Device" "/dev/input/event1"
(--) Synaptics Touchpad touchpad found

```

Any idea what I might be doing wrong? I've gotta say that Ubuntu is harder for me than Gentoo Linux for this kind of stuff ^^'

---

### Post by Bartje on 2007-02-01
I've followed the short list to configure my wacom. My system seems to find the tablet, when using dmesg | grep wacom, it tells the drivers are loaded. In the hardware menu of Ubuntu Edgy, my wacom seems to be found at 'event3'. Previously it switched input when I changed it in xorg.conf, now it doesn't anymore, so I guess that's an improvement. Using 'cat eventx' gives no result when I try the pen on the tablet.... In Gimp extended input device gives a result, but when I change from eraser to stylus, the options dissapear. No movement on the screen either.

---

### Post by Bartje on 2007-02-02
perhaps someone is something with this info to help me enabling my wacom?

When I do:
bart@bart-desktop:~$ more /proc/bus/input/devices

I get this:

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=056a Product=0060 Version=0142
N: Name="Wacom Volito"
P: Phys=
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0 
B: EV=f
B: KEY=1c43 0 70000 0 0 0 0 0 0 0 0
B: REL=100
B: ABS=100 3000003

I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse1 event3 ts1 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103


In the wacom section behind:
P: Phys=
comes nothing.
What does it stand for, and could that mean that there is no physical input assigned to 'event2'?
If it is, how can I change that?

---

### Post by Bartje on 2007-02-03
another thing:

in the file Xorg.0.log there are some lines

(**) stylus is in absolute mode
**(**) WACOM: suppress value is 2**
(**) Option "Tilt" "on"
(**) Option "USB" "on"
(**) stylus: reading USB link
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in absolute mode
**(**) WACOM: suppress value is 2**
(**) Option "USB" "on"
(**) cursor: reading USB link
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
**(**) WACOM: suppress value is 2**
(**) Option "Tilt" "on"
(**) Option "USB" "on"
(**) eraser: reading USB link
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600

What does this 'suppress 'value' mean? Apparently the tablet is being configured, and found by the system.

---

### Post by Bartje on 2007-02-08
I'm a bit confused right now. I have reïnstalled Ubuntu from scratch, downloaded the sourcecode of the kernel, and installed wacom-tools. First I had no effect at all, but when I copied the new wacom.ko, and had changed the xorg.conf file, I immediatly had a reaction. 

sudo cat /dev/input/wacom 

wow, so much signs appearing on the screen.
Wow, it worked!

Untill I fired up Gimp, and tried to configure it.  changing from eraser to stylus or cursor only made the options disappear from my screen, and my tablet seems to work as a regular mouse.

So it doesn't work at all....
sigh....
what now?
Reading xscd reply, I should have 3 things:
wacom.ko
wacom_drv.o
and the udev rules.

I searched for them, and apparently wacom_drv.so seems not to be present in my system.
Why is it not installed?
Where should it be?

If someone could help me, I'm struggling about a month now to get this thing working....
And nobody replied yet on my previous messages either....

---

### Post by xscd on 2007-02-08
Hello Bartje--

Let's try to make this simple, in a step-by-step fashion, OK?

1 ) download the linuxwacom project's software, which at present is here (just click the link below):
[http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.7.6-4.tar.bz2]("http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.7.6-4.tar.bz2")
Download it to somewhere in your home directory.

2 ) Decompress and unpack the tar archive with the commands:
bunzip2 linuxwacom-0.7.6-4.tar.bz2
tar -xvf linuxwacom-0.7.6-4.tar

3 ) Change directory into the unpacked linuxwacom directory:
cd linuxwacom-0.7.6-4/

4 ) Change into the "prebuilt" directory inside the linuxwacom directory and list the files:
cd prebuilt/
ls -l

5 ) You will see several Xorg drivers, already prebuilt for you so that they can merely be copied to where they should go within your Ubuntu installation. There are Xorg drivers for both 32- and 64-bit machines:
wacom_drv.o
wacom_drv.o_x86-64
wacom_drv.so
wacom_drv.so_x86-64

6 ) Copy either the 32-bit or 64-bit drivers, depending on your machine's CPU, to the appropriate place where  the Xorg server expects to find them. First find out exactly where the Xorg server **does** expect to find these drivers by using the locate command (part of the findutils package (make sure findutils is installed using synaptic, for example):
sudo updatedb
locate -i "*/xorg/modules/input/*"

On my Edgy Eft Ubuntu installation, the Xorg drivers are in:
/usr/lib/xorg/modules/input/

7 ) Copy the Xorg wacom drivers to that location:
sudo cp -v wacom_drv.o wacom_drv.so /usr/lib/xorg/modules/input/
  -or, for 64-bit machines-
sudo cp -v wacom_drv.o_x86-64 wacom_drv.so_x86-64 /usr/lib/xorg/modules/input/

8 ) Now, after confirming that you have the kernel driver available also on your machine--
locate wacom.ko
--then configure your xorg.conf file as discussed in this discussion thread and elsewhere on ubuntuforums.org, then plug your Wacom tablet into a USB port, logout of your GUI (KDE or Gnome) environment, restart the Xorg server with CONTROL-ALT-BACKSPACE or reboot your machine, and see what happens.
:) 

Examine your Xorg log file to see if it loaded the wacom_drv.so (or wacom_drv.o) driver, by viewing the log file at:
/var/log/Xorg.0.log
Look for the word "wacom" in that logfile, in order to be sure that Xorg loaded it OK.

Best wishes,

Steve/xscd

---

### Post by Bartje on 2007-02-09
Xscd,

I tried your approach, but it still doesn't work... here's what I did, and what I got as a result:

using **dmesg** really lots of lines appeared, and those about wacom would be these:
[17179590.804000] input: Wacom Volito as /class/input/input2
[17179590.812000] usbcore: registered new driver wacom
[17179590.812000] /usr/src/linuxwacom-0.7.6-1/src/2.6.16/wacom_sys.c: v1.46:USB Wacom Graphire and Wacom Intuos tablet driver

I downloaded the driver, and went into the 'prebuilt' folder, then used findutils as you described (just copied and pasted the line) and I got this:

/usr/lib/xorg/modules/input/elographics_drv.so
/usr/lib/xorg/modules/input/evdev_drv.so
/usr/lib/xorg/modules/input/kbd_drv.so
/usr/lib/xorg/modules/input/keyboard_drv.so
/usr/lib/xorg/modules/input/mouse_drv.so
/usr/lib/xorg/modules/input/synaptics_drv.so
/usr/lib/xorg/modules/input/wacom_drv.o
/usr/lib/xorg/modules/input/wacom_drv.so

My system is a dualcore intel processor, and I'm running a 32bit version of Ubuntu Edgy on it, because it was pre installed by the shop, to try if linux would run properly on it, having a new motherboard, and processor (E6700). I don't have enough download anymore to download a 64bit version this month.

Since the Ubuntu is a 32bit version, I guess it are the 32bit drivers of wacom that I should use.

so the drivers are there already. But I did replace them with the others from the 'prebuilt' folder anyway. 

I did restart the computer, complete reboot, not only the X-server, just to be sure...and checked the Xorg.0.log file, witch gave me this about the ServerLayout section:

(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb  9 13:43:51 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"

and further on:

(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.6-4 $

It all seems ok, for as much as I know about it, but when I fire up Gimp, nothing seems to have changed. Trying to configure the extended device, still makes the options disappear when I change from eraser to stylus or cursor. And the pen moves, yes it does, but still as a regular mouse.

I do use a mouse, but it's not a USB mouse.

Greets,
Bartje

---

### Post by xscd on 2007-02-09
Just to be clear Bartje, you have installed both of these packages (using synaptic or whatever), right?
wacom-tools
xserver-xorg-input-wacom

If so, then temporarily change from the GUI environment to a text-only terminal, using:
CONTROL-ALT-F1
-or
CONTROL-ALT-F2 (or F3, F4, F5)

Then type the following commands:
sudo su
wacdump /dev/input/event3
  -- (or whatever event the kernel has assigned to the Wacom tablet. Try /dev/input/wacom (which is a symbolic link dynamically created by a udev rule) if you have installed the wacom-tools package)

Then use your Wacom tablet and see if the wacdump program correctly reports what you are doing with the stylus and the tablet. When you are done with the wacdump program, type CONTROL-C to quit it, then ALT-F7 to get back to your GUI (Gnome or KDE).

If the results of experimenting with your tablet and the wacdump program look good to you, please copy your xorg.conf file and paste it here in ubuntuforums. Perhaps someone will see something that you ought to add, edit or delete from your xorg.conf file.

Best wishes,

Steve / xscd

---

### Post by Bartje on 2007-02-09
On my system:
wacdump /dev/input/event3 ==> no reaction
wacdump /dev/input/event2 ==> coordinates appear and touchdown is read, as it should I guess.

wacdump /dev/input/wacom ==>coordinates appear and touchdown is read, as it should too, i think.

wow, some things start to work as they should I guess... :-)

Here is my Xorg.conf -file:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "be"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "Mode" "absolute"
    Option         "USB" "on"
    Option	   "ForceDevice" "ISDV4"
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "Mode" "absolute"
    Option         "USB" "on"
    Option	   "ForceDevice" "ISDV4"
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "Mode" "absolute"
    Option         "USB" "on"
    Option	   "ForceDevice" "ISDV4"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by Bartje on 2007-02-10
Maybe this might be a hint to find the source of the problem... 

Doing:
sudo wacdump /dev/input/event0

I get response too... from my keyboard.... ?????

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=24947&stc=1&d=1171115798[/IMG]

Or is this normal?

---

### Post by xscd on 2007-02-10
Is your keyboard a USB keyboard? Each /dev/input/event<number> is a different device. If you ask wacdump to monitor /dev/input/event0--

wacdump /dev/input/event0

--then the wacdump program will monitor whatever data the kernel sends to /dev/input/event0. If that happens to be your USB keyboard, that is the data that wacdump will see. That's why you need to determine which /dev/input/event<number> your wacom tablet is on, so that the data from **that** device (which can change between reboots) will be monitored. This is one thing that the wacom-tools package does for you automatically. It monitors the hardware attached to your system, then creates a symbolic link ( /dev/input/wacom ) that will always point to the correct /dev/input/event0 (or event1 or event2 or event3, etc.). The wacom-tools package is very helpful in this regard.

Bartje, about your **xorg.conf** file--

Unless your Wacom Volito tablet uses a special and unusual data transmission and communication protocol that a "TabletPC" uses, then you might want to "comment-out" the option that forces  the xorg wacom driver to use that protocol. Just edit your xorg.conf file as the the administrative user:

sudo gedit /etc/X11/xorg.conf

and put a hash (number symbol) in front of the ISDV4 options. Change these lines--

Option "ForceDevice" "ISDV4"

to this--

# Option "ForceDevice" "ISDV4"

--then save the xorg.conf file, exit gedit (or whatever text editor you are using), then log out of the GUI (KDE or Gnome), then use CONTROL-ALT-BACKSPACE  (NOT control-alt-delete! :) ) to restart the Xorg server, which will cause Xorg to read its newly edited configuration file, xorg.conf, again.

I hope this helps, and I do hope you get your Volito working well with the Gimp and Inkscape or whatever else you use it for. A graphic tablet is so much nicer than a mouse. I have an Intuos, and although not all the extra buttons on the Intuos work in Linux (not yet, anyway) the tablet works great in the Gimp and Inkscape, etc.

Once you get the tablet to work well in absolute mode in KDE or Gnome, then you can work on the specific problems that you may have with the tablet and Gimp or Inkscape, etc.

The steps I take to get the tablet to work, I do in this order:

[list=1]
[*] Make sure the linux kernel can see the wacom tablet and is sending the tablet's data to a device file (make sure the kernel driver module (wacom.ko) is present and test it by using the program wacdump in a text terminal (not within KDE or Gnome, but in a text-only terminal as mentioned in a previous post) to find, monitor and test the device file (/dev/input/event<number>) that the kernel is sending the tablet's data to).

[*] Make sure that the best and most current Xorg driver module is installed (the latest version of wacom_drv.so (or wacom_drv.o for older Xorg versions), and make sure that the xorg.conf file is correctly edited for the tablet, then restart the Xorg server (or reboot the machine).

[*] Make sure that the tablet works in KDE or Gnome in "absolute" mode, by making sure that when the stylus is moved across the tablet, the cursor on the monitor screen can go all the way from one side of the screen to the other and from top to bottom if the stylus is moved from one side of the tablet to the other and from the top of the tablet to the bottom, and making sure that buttons and widgets on the screen can be clicked using the stylus and tablet.

[*] Configuring the tablet for use within the Gimp or Inkscape (or whatever) and solving any specific issues or problems regarding the tablet and those programs.
[/list]

best wishes,

Steve / xscd

---

### Post by Bartje on 2007-02-11
Hi,

enabling, or disabling this 'ForceDevice' in xorg.conf doesn't seem to have any effect at all on my wacom, so I had it restored in it's original ISDV4 state. But I did comment it out as you proposed... I don't see no difference in how the device works....

So, I did an experimenent, and changed the input device, just for seeing what would happen. 
Surprise, surprise, my wacom still worked!!!
Well the pen moved the cursor on my screen correctly, and I could draw, but pressure sensitivity seemed to have been gone... but the pen moved....on an event on which nothing happens using 'cat /dev/input/event1.... Choosing an extended device in Gimp had become inpossible though... that makes sense, indeed, so I put it back on /dev/input/wacom as explained... I just wanted to try it, to see the system really follows the rules in xorg.conf.....
Does it?

I plugged the cable of my wacom out of the USB-port, and then back....

aparrently my system always hangs when I hotplug the wacom....it took a couple of seconds, but it hangs eventually. There must be a conflict somewhere....

---

### Post by Seven.issimo on 2007-02-13
Hi there,
your thread reminded me my Volito2, lost somewhere on my desk ...

However,** I get it working, in about five minutes, compiling last driver**:
[LIST=1]
[*]Just for care, I followed [official testing tips]("http://linuxwacom.sourceforge.net/index.php/howto/testtablet")¹
[*]downloaded and extracted latest unstable (:D ) drivers from [here]("http://linuxwacom.sourceforge.net/index.php") (actually version 0.7.7-4)
[*]configured and compiled only the necessary:
```
$ ./configure --enable-wacom --enable-libwacomxi=no --enable-libwacomcfg=no --enable-xidump=no

```in order to get rid of all X extras (that, besides, don't want get compiled: missing -lXi, also with fixed dependencies),
and so, simply:
```
$ make
```
[*]got sure of what I've done:
```
$ lsmod | grep wacom
wacom                  18432  0 
usbcore               134912  7 usb_storage,usbhid,**wacom**,libusual,ehci_hcd,uhci_hcd

$ sudo modprobe -r wacom
$ sudo insmod ./src/2.6.16/wacom.ko 

```...and...Tada!™** ...my Tablet reliefs!**

[*]final steps:
```
$ locate wacom.ko
/lib/modules/2.6.17-11-generic/kernel/drivers/usb/input/wacom.ko

$ cd /lib/modules/2.6.17-10-generic/kernel/drivers/usb/input/
$ sudo mkdir backups
$ sudo mv wacom.ko ./backups/
$ sudo cp ~/.devel/linuxwacom-0.7.7-4/src/2.6.16/wacom.ko ./

```
according with [this]("http://linuxwacom.sourceforge.net/index.php/howto/installwacom").
[*]reboot (just for safety)[/LIST]


[1] @Bartje: I don't understand why your /proc/bus/input/devices output is so different, also if we all have same kernel.. :-k

---

### Post by Bartje on 2007-02-14
> **Seven.issimo said:**
> 
$ sudo modprobe -r wacom


makes my computer hang immediatly...

---

### Post by Bartje on 2007-02-16
It seems like I've ran out of resources here to get my wacom Volito to work properly. 

I've tried all your suggestions, even reinstalled my complete system a couple of times. Using the 'unstable' version works best, simply because Gimp doesn't crash anymore. There are some problems though:

-I still can't adjust the settings of the Wacom using Gimp (options keep disappearing).

-Using the regular mouse (not an usb mouse, but ps), I can't use the tools in Gimp, but I can activate them. Once in the window of my drawing, the tool doesn't do anything. For example, I can activate the zoom-tool with my mouse, but I can't zoom in my drawing using the mouse. With my wacom I do can use all the tools properly.

-In Krita I can adjust the settings of the tablet, but they affect the mouse, not the wacom. In Krita the situation is the opposite of in Gimp. I just can't use the wacom in Krita because the tools don't affect the drawing. For example, I can activate the 'draw' tool, but in the window of the drawing, I can't draw with my wacom-pen.

What I've told all along, during this long, tiresome search to get it working, is that there must be a conflict somewhere between the different input-devices. 
-I've got my drivers, in the right place
-I've got motion of the wacom
-I've got pressure sensitivity
-I've got my xorg.conf configured as everyone says it should be.
The only thing I don't have, is that it works properly.

Conclusion... : Waiting for another Linux release, perhaps Ubuntu, perhaps an other, that can be installed on my 965G chipset machine (yes Ubuntu is the only one so far, even Debian won't start the installation-DVD, so I can't experiment with others right now), and continue with a half working wacom, unless someone else knows what the conflict can cause.

Greets, and thanks for all the help that I've had.

---

### Post by graigsmith on 2007-02-16
it looks like your xorg is configured wrong.

Option "Device" "/dev/input/mice"

this is the problem. using the mice device will always conflict with the wacom tablet. 
you must either use mouse1 or mouse0.  depending on what device your mouse is on.

you can sudo cat /dev/input/mouse0 and move your mouse and see if it's on mouse0.  you should get gibberish. If you need more info on the cat command and how to figure out what mouse device your mouse is on.. check the howto here.
[http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom+howto](http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom+howto)

heres how i have my xorg configured.
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
	Option		"XkbVariant"	"dvorak"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"[COLOR="Red"]
	Option		"Device"		"/dev/input/mouse0"[/COLOR]
	#Option		"Protocol"		"ExplorerPS/2"
	#Option		"ZAxisMapping"		"4 5"
	#Option		"Emulate3Buttons"	"true"
	Option		"Emulate3Buttons"	"false"
	Option		"Buttons"		"7"
	Option		"ButtonMapping"		"1 2 3 6 7"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"     [COLOR="Red"]   "/dev/input/wacom"    [/COLOR]      
  Option        "Type"          "stylus"
  Option 	"Mode" 		[COLOR="Red"]"Absolute"[/COLOR]
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        [COLOR="Red"]"/dev/input/wacom"[/COLOR]         
  Option        "Type"          "eraser"
  Option 	"Mode" 		[COLOR="Red"]"Absolute"[/COLOR]
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        [COLOR="Red"]"/dev/input/wacom"[/COLOR]
  Option        "Type"          "cursor"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200]"
	Driver		"ati"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"NEC LCD1712"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV280 [Radeon 9200]"
	Monitor		"NEC LCD1712"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	[COLOR="Red"]InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"[/COLOR]
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Bartje on 2007-02-16
Graigsmith,

here is my Xorg.conf file, tell me what's different. I followed your advice. For my my mouse ist's now mouse1, tested, and proved correct useing cat/dev/input/mouse1.

Sorry, but I don't think the xorg.conf file is the problem, because the problem _is not solved_.
thanks for trying to help though.


# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "be"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mouse1"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
                                                     
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"          
    Option         "Type" "stylus"
    Option	   "Mode"	"absolute"
    Option 	   "USB"	"on"
EndSection

Section "InputDevice"

    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"           
    Option         "Type" "eraser"
    Option	   "Mode"	"absolute" 
    Option	   "USB"	"on"
EndSection

Section "InputDevice"

                                                     
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"           
    Option         "Type" "cursor"
    Option	   "Mode"	"absolute"
    Option	   "USB"	"on"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by graigsmith on 2007-02-16
> The only thing I don't have, is that it works properly.

well, if you still wanna try to fix it. ill try to help. but if not that's ok too.

what exactly is it doing now?  did you set up your gimp input devices?  did you set the 3 input devices to screen?

---

### Post by Bartje on 2007-02-17
I do appreciate someone else to help ofcourse... all help is welcome.

What Gimp is concerned, as I told in the previous posts (if you'd read them you'd know that I probably have tried everything already), the wacom is not configurable in Gimp (options disappear when I switch from eraser to stylus or cursor), nor in Inkscape. In Krita it is, but then it affects the mouse, not the wacom.

I can draw though, have pressure sensitivity, but not in Krita, because as I explained before, the tools don't do anything in the drawing window when using the wacom in Krita.

The opposite happens in Gimp. I do can use my wacom as I should, just can't configure it, but the mouse has no effect on what I do in the drawing window, although I can select the tools with it.

And you've seen the xorg.conf -file, I'm not gonna put it here again.

Here is a list of what I have tried allready, so you won't come up with something I've already done:
-Everything from this entire thread (read it, then you'll see how many work arounds there are).
-https://help.ubuntu.com/community/Wacom

I've been through all this:
-https://help.ubuntu.com/community/Install_linuxwacom_driver
-https://help.ubuntu.com/community/WacomTroubleshooting

There is many, many more that I've read, and tried, but I can't list them all, they all end up at the same thing... just replace wacom.ko, with the one they provide.

---

### Post by bren21 on 2007-03-29
Edit: Okay, I managed to get the tablet to work correctly, but the scroll bar on the tablet doesnt work.  Anyone know how to fix this?

---

### Post by smilingfrog on 2007-03-31
Hi, I am new to Ubuntu, and to Linux. I am having a fairly (fun) time with the learning curve. The one thing that I want to get work is my Graphire tablet. I have followed the documentation on line as best as I can, and I m still stuck.
The pen and mouse work, both as mice. There is no pressure sensitivity, and GIMP does not recognize the stylus as an extended device.

I am using 6.10(Edgy), with the most recent kernel 2.6.17-10. I compiled the driver, but I don't think that made much of a difference, since the tablet is working pretty much the same before as after.

here is the xorg.conf file:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"          
  Option        "Type"          "stylus"
  Option        "USB"           "on"   
  Option        "PressCurve" "0,0,100,100"              
                
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"        
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  
  Option        "PressCurve" "0,0,100,100"
 
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"          
  Option        "Type"          "cursor"
  Option        "USB"           "on"                  
  Option        "ForceDevice"   "ISDV4"             
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL D1226H"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor		"DELL D1226H"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
   	InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    #For non-LCD tablets only
EndSection

Section "DRI"
	Mode	0666
EndSection
```

 
Any help or suggestions appreciated.
G

---

