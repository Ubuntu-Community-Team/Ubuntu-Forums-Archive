---
title: "Help me to run XP proprietary software please. 2.6.24-19-386"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Rorke on 2008-06-20
I'm new to Ubuntu - but I'm not an idiot, I've programmed in machine language on the ZX81, reconfigured Dos memory maps and managed small labs of linux machines.

BUT I've read in several forums phrases like 'Why would anyone need XP, its totally useless and Linux does everything you need.'

Since installing Ubuntu 8.04, I've had daily problems trying to get it to do what XP does out of the box. I have tried 3 different ways to run Conferencing software from AT&T called Interwise ([http://www.interwise.com/](http://www.interwise.com/) if anyone wants to try for themselves) including wine (couldn't configure it) Crossover (just didn't do the job) and VirtualBox (Seems to keep being crashed by Kernel updates).
I'm now looking at back installing XP as a dual boot - something that I've read is dangerous and tricky, OR just scrubbing the linux altogether. BTW, this feels like going back to confession (church) after I've just told everyone I'm an atheist!

The only thing I need my PC for is Interwise with a working mic, speaker and preferably some decent screen resolution. (OK, some surfing, bit of music, some WP and a spreadsheet, occasional Youtube - but I got all these working in about a week)

Oh, and all of you who will reply RTFM - I just ordered one from Amazon and its due today.

If anyone can help, you'll probably save my sanity.

Thanks in advance.
Simon

---

### Post by bgoody on 2008-06-20
Hi.  I use Vmware Workstation for those times when no Linux equivalent is available or the amount of time it takes to configure something is just to wasteful.  It costs money but so does time.

Vmware has a free trial so you can figure out if it will handle your program.  There is also a free (I think) Vmware Server version in the repos but I have the impression it is behind a bit and there is no support included in the non-box.  Brian

---

### Post by hyper_ch on 2008-06-20
you could still setup winXP in a virtual machine like vmware and use it that way...

---

### Post by forestpixie on 2008-06-20
I can't help with much of that tbh - but I have had no problems with vbox and kernel updates. I think that is because I don't use the version in the repos but use the version from the vbox site - I have had to reinstall it but that takes less than a minute.

If the problem you have is because that you are using the repo version and the ose packages aren't keeping up wait until they have before you let it update - you don't have to accept any of the updates.

So perhaps try using that one instead and see if it is a bit more stable for you.

I doubt if you'll get any rtfm and if you do I'd report it.

---

### Post by Dynaflow on 2008-06-20
Making your computer dual boot Windows and Linux is neither dangerous nor tricky.  Hell, two of my three computers dual-boot Windows and Ubuntu, even though the primary reason I log into either of the Windows partitions lately is to update Windows.

As for AT&T's proprietary software and a lot of other business apps (Quickbooks, argh!), they were built specifically for Windows on the theory (becoming more of a mere historical bias now) that Linux users represented a miniscule and utterly insignificant market, simply not worth bothering with. Until enough software companies start responding to the pleas of their would-be users to make interoperability a primary development concern, it'll be good to keep a Windows-running machine around somewhere.

I would restore Windows on the computer you're using, assuming you have the system-restore disks, or installing a copy of XP and letting it set itself up on your disk however it sees fit.  After you've run all the updates and such, use the Ubuntu installer.  It will create a partition for itself and install itself so it will dual-boot if you choose that option during installation.

Then you can use Ubuntu for the bulk of your "real" computing and just reboot into Windows when you need to use Interwise.

---

### Post by RomeReactor on 2008-06-20
Hi. When you say that running it with Wine you couldn't configure it, do you mean configure Wine to install/run the program, or configure the program once it's installed? Is this the program?

---

### Post by Rorke on 2008-06-20
WOW! I must say I'm very impressed!
I couldn't work out how to configure wine at all. I just about managed to run IE6 in it, but that didn't help.
After running AT&T, I need to run Firefox apparently from Windows, then when I click on the tutorial, it is expecting to see Windows OS. In Windows, I'd already run the setup program and the URL starts the AT&T software automatically.

I've reloaded VirtualBox on one of my machines, but I can't get the mic to work. But then I don't think it works in Ubuntu either. (Not a HW problem, the mic is fine on the XP machine I have in the spare room).

---

### Post by Rorke on 2008-06-20
Well, I already have Ubuntu installed, so presumably it didn't leave room to put XP on afterwards. I'm worried about over writing the partition table with XP and losing my Ubuntu setup and everything I've done over the last 5 weeks.

---

### Post by Dynaflow on 2008-06-20
> **Rorke said:**
> Well, I already have Ubuntu installed, so presumably it didn't leave room to put XP on afterwards. I'm worried about over writing the partition table with XP and losing my Ubuntu setup and everything I've done over the last 5 weeks.

Burn the latest gparted-live-stable from [here]("http://sourceforge.net/project/showfiles.php?group_id=115843") to a disk, run it as a liveCD, and it will let you safely resize, create, and move partitions.  Create a new partition for XP and install it to that.  You may end up having to reinstall or reconfigure GRUB so that it plays nice with the updated partition table, but that's easy enough to do manually (there are any number of threads here on how to do just that), or you could just use [Super Grub Disk]("http://www.supergrubdisk.org/") to get your bootloader up to par again.

If Windows insists on taking the whole disk (it's been so long since I installed Windows on anything, I've forgotten the particulars of its installer), then abort, do a backup of the valuable stuff on your Ubuntu partition (including exporting browser bookmarks, etc.), then let Windows do its thing.  Once it's done installing itself, you'll be able to reinstall Ubuntu on a new partition it will create for itself. 

You may end up having to reinstall or reconfigure GRUB so that it plays nice with a updated partition table, but that's easy enough to do manually (there are any number of threads here on how to do just that), or you could just use [Super Grub Disk]("http://www.supergrubdisk.org/") to get your bootloader up to par again.

I wouldn't worry about paving over your current Ubuntu partition, if that's what it comes down to, so long as you've backed up everything important and remember where online you found the instructions and advice that got you this far.  I've personally found that, every time I install or reinstall Ubuntu, I do it faster and better.  You can probably redo what you did in this installation in a few hours, and do it better than before, with fewer awkward artifacts scattered about from missteps and false starts.

---

### Post by RomeReactor on 2008-06-20
Can you tell us in more detail what problems you have installing the program with Wine? Please post the errors you get in the terminal, if any.

---

### Post by Rorke on 2008-06-20
Your advice seems really good so far, but it is way beyond my current expertise.
I tried getting 'Super grub' from your link, and have so far got this error:

./configure



checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for intltool >= 0.35.5... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for uuid_generate in -luuid... no
configure: error: *** uuid library (libuuid) not found

jackie@jackie:~/Desktop/gparted-0.3.7$ make
make: *** No targets specified and no makefile found. Stop.
jackie@jackie:~/Desktop/gparted-0.3.7$ make install
make: *** No rule to make target `install'. Stop.

---

### Post by PmDematagoda on 2008-06-20
You are trying to build the program, what the others are talking about is the GParted Live CD found [here]("http://downloads.sourceforge.net/gparted/gparted-live-0.3.6-7.iso?modtime=1208153087&big_mirror=0"). After downloading the CD, burn the image onto a CD and boot the PC using it and make the necessary partition changes.

---

### Post by Dynaflow on 2008-06-20
Oh, no, not at all.  Just get the liveCD disk images of each and burn them to disk.  Both projects have their source code and unpackaged programs up, but what you want are the liveCDs.

---

### Post by Rorke on 2008-06-20
I don't know how to get errors in a terminal from Wine.
I just realised that I need another copy of Mozilla - the Windows version to run that from Wine, and then to install the Setup.exe of Interwise from Wine. I don't think it worked in exactly the same way as when I'd done it in XP. I can now download the .vcm file, but I can't seem to play it.
I can't find any other way of playing a .vcm - I've only ever found reference to it from Interwise site.
On the other machine I'm moving the partitions and going to try a dual boot. (It also has graphics problems and I figure start again will take less time - but I think my GF is about to divorce me!)

---

### Post by RomeReactor on 2008-06-20
If the program made a shortcut in your desktop, right-click on it, select 'Properties', go to the 'Launcher' tab and copy the command entry. Then open a terminal and paste the command there; if it starts leaving error messages, please post them.

If you don't have a shortcut in the desktop, write in the terminal:
```
wine 
```
(note: that's **wine** followed by a space). Then go to 'Applications->Wine->Browse C:\ Drive', go to the Interwise folder, find the executable you want and drag it into the terminal.

---

### Post by Rorke on 2008-06-21
OK, I think the answer is a couple of DLLs, but I'll paste the remainder too, just incase.

err:module:import_dll Library MFC42.DLL
err:module:import_dll Library IwReg.dll

I ran it all from firefox:
 env WINEPREFIX="/home/simon/.wine" wine "C:\Program Files\Mozilla Firefox\firefox.exe"

And, when I tried to open the .vcm file from the open window, the output went like this:

fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
preloader: Warning: failed to reserve range 00000000-60000000
fixme:shell:SHAppBarMessage msg=5, data={cb=36, hwnd=0x10022, callback=63, edge=8192, rc=(0,2132932108)-(2076711558,2132932108), lparam=7f21f63c}: stub
preloader: Warning: failed to reserve range 00000000-60000000
fixme:shell:IPersistFile_fnSaveCompleted (0x7f057630)->(L"C:\\windows\\profiles\\simon\\Recent\\Rec_Math_C1_T2_Group2_050608A.vcm.lnk")
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Interwise\\Participant\\IwReg.dll") not found
err:module:import_dll Library IwReg.dll (which is needed by L"C:\\Program Files\\Interwise\\Participant\\STUDENT.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Interwise\\Participant\\STUDENT.exe") not found
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Interwise\\Participant\\STUDENT.exe" failed, status c0000135
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented




Also (the unimplemented line repeats many times)





fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:resource:GetGuiResources (0xffffffff,0): stub

fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented

Thanks for your interest :-)

---

### Post by Rorke on 2008-06-21
OK, I have now burtn the GParted disk, repartitioned, installed XP, edited the GRUB to boot 18 by default, and XP as an option.
I loaded the software I need for XP, along with virus and firewall (yawn!).
I have everything perfect - except I still don't know how to get high res graphics in Ununtu 8.04 on any kernel.
(For some reason, on my other PC GParted failed with an error. I lost confidence and have shelved that idea for now.)

---

### Post by RomeReactor on 2008-06-21
> **Rorke said:**
> OK, I think the answer is a couple of DLLs, but I'll paste the remainder too, just incase.

err:module:import_dll Library MFC42.DLL
If you haven't done so, you can get MFC42.DLL [here]("http://www.dll-files.com/dllindex/dll-files.shtml?mfc42").

> err:module:import_dll Library IwReg.dll
And IwReg.dell [here]("http://www.datajett.com/windchill/Interwise/Student/IwReg.dll").

Copy both to **~/.wine/drive_c/windows/system32**.

---

### Post by PmDematagoda on 2008-06-21
About the graphics problems, what are the specifications of the PC having those problems?

---

### Post by Rorke on 2008-06-21
OK, now you're asking. I'm assuming in Ubuntu there are a suite of command line tools that answer this question.
I've discovered a few lspci so far:
jackie@jackie:~$ more lspci.txt 
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology
 Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

---

### Post by Rorke on 2008-06-21
OMG!!!
You are a STAR!
This so far seems to work better than VirtualBox!!!
Is it protected against Kernel updates, or does wine get screwed occasionally too?
Many thanks!
Simon

---

### Post by RomeReactor on 2008-06-21
Can you please elaborate? Is the program running now? If that's the case, Wine updates shouldn't cause you problems; it's possible, but not likely.

---

### Post by Rorke on 2008-06-21
Yes - the program is running fine! Thanks. On my girlfriend's PC the program fails because it won't run in 800*600! So I need to sort that next!

---

### Post by RomeReactor on 2008-06-21
In case you want to keep Wine from updating, you can go to Synaptic, search for Wine, highlight it when it shows up, and from the menu bar go to 'Package->Lock Version'.

---

### Post by PmDematagoda on 2008-06-21
Ok, you have Nvidia, about the resolution, on what kernel do you get those issues?

---

### Post by Rorke on 2008-06-21
Well, I first got it when I loaded 19, but I think I somehow switched from generic to i386. I now get the issues in all kernels. I can probably get round it by installing the graphics driver again, but I don't know how to do this. The Nvidia accelerated graphics card shows as 'not in use'. I'll post this first, but I'm pretty sure if I get it into use and re-boot, I get hi-res for the login screen and then no signal when Ubuntu boots properly.

---

### Post by Rorke on 2008-06-21
OK - I now have a machine with sound and no display. Panic!?!

---

### Post by Rorke on 2008-06-21
OK, I got the display back by booting into 18 recovery mode and doing 'xserver repair'. Any thoughts anyone? Useful analysis tools? Command line suggestions? RTFM with a page number or link even?

---

### Post by Rorke on 2008-06-23
I've been reading extensively about similar graphics problems involving nvidia and drivers, but I haven't found a solution yet. 

In a thread it suggests modifying 'Screen and Graphics' from a menu, but I don't have this option.
My LCD monitor is not inthe list of monitors in the manual setup of the graphics, but it did work just fine when I first installed Ubuntu from DVD.
I really want to avoid re-inatalling from scratch, but compared to how long I've been trying to fix this, it would be about a tenth of the time.
Can you suggest anything?
My monitor is I-Inc, AG191D and I have Nvidia ghraphics card.

---

### Post by issih on 2008-06-23
Screens and graphics can be enabled by right clicking on the main menu and editing it. It can then be found under Applications->Other, jsut tick it to enable it in the menu.

I doubt that will really help though if you have no graphics at all.

Have you tried using envy?

---

### Post by Rorke on 2008-06-23
Strangly, I'd already tried adding it by editint the main menu, but I couldn't find it! I just had a break and now I've found it, so thanks!
When I load it, I'm told I'm using a Plug n Play monitor with 800*600 at 60Hz.
[I]'ve had a better resolution running before with Ubuntu.
The graphics card is NVIDIA, with driver 'none'.
If I add the driver NVIDIA, Geforce 6 series - (which is already black, suggesting it is the prefered choice - the others are grey) then I get an unviewable screen when I press 'Test'.

I looked at ENVY following another link, but I don't want to go so far down the route of guessing with drivers when I (possibly) just need to click in a box to fix this.

If I run from DVD my graphics are fine. I really don't even care if I can use the 3D acceleration - I just want a bigger screen size for web viewing!

---

### Post by Rorke on 2008-06-23
Cool, I did that. Thanks

---

### Post by Rorke on 2008-06-23
Also I found:
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
in a log file and a lot of:
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
for a whole load of screen sizes.

---

### Post by issih on 2008-06-23
I'd really consider reinstalling the graphics drivers...just download envy and let it do its job. Its very simple, and if it gets you out of this mess it will be well worth it.

assuming you are running hardy heron its even in the repositories just search synaptic for envy and install either the gtk(if on gnome) or qt (KDE) metapackage.

Then run envy and tell it to install the nvidia driver..Then go make a cup of tea.

Its worth trying.

---

### Post by Rorke on 2008-06-23
Well, now I have a permenantly black screen!
Don't know why. Its all fine booting from CD, Live, but just a black screen on plain Ubuntu boot.
I tested envy on the PC that didn't have a problem, and it didn't seem to install Nvidia at all.
Looks like I'll have to reinstall Ub8.04.

---

### Post by issih on 2008-06-23
Envy's sole purpose in life is to install graphics drivers, be that ati or nvidia.....So I suspect you did something wrong.

You want to install either envyng-gtk or envyng-qt (gnome and kde respectively).

e.g. "sudo apt-get install envyng-gtk" in a terminal.

You then launch envy from the main menu and tell it what driver to install (nvidia or ati, and if you want what version). Envy is by far the easiest way to get that done, it really is.

Hope that helps

---

### Post by Rorke on 2008-06-23
Well, I got the default screen going. (!phew!)
I couldn't see what menu to launch envy from. I ran it from a command line.

---

