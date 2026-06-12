---
title: "Connecting android phone, using AceStream, uncomfortable  feeling with Ubuntu 14"
date: 2014-08-11
forum: New to Ubuntu
---

### Post by guccimucci on 2014-08-11
I had some problems installing windows 8 updates and I actually never really enjoyed its new display at all. Instead of it I googled Ubuntu and found many good articles about it and I was quite satisfied by the fact that it is free to use and there are many freeware programs around it.

I have been using Ubuntu 14 for a week now but unfortunately I've only experienced problems and difficulties with the new OS. I would like to list my problems here to get help or inspiration to really enjoy Ubuntu and make myself feel at home with it.[B]
1.Connecting Sony Xperia Z1 Compact (Android 4.4) with Ubuntu for file transfer[/B] - I almost uninstalled Ubuntu and tried to reinstall Windows 8 because of this problem (details in part 2). I read about the program called go-mtpfs and tried to install it or make it work somehow but I kept having errors in terminal and Ubuntu still did not recognize my device at all. I used the guide I found in here: [http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html](http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html) but I already get stuck when I enter 
sudo add-apt-repository ppa:webupd8team/unstable
sudo apt-get update
sudo apt-get install go-mtpfs

[FONT=arial]in terminal it says: > W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
And then it says the grub-pc package is being upgraded. 
How can I connect my Android phone with Ubuntu as I know that Sony doesn't support Ubuntu (which is a shame)? I also read that AirDroid could be a solution but isn't it slower than actual connection?
[B]
2. Installing Windows instead Ubuntu or dual-boot[/B]
So as I mentioned I was quite unsatisfied by the fact that I had to spend hours on making only one of my devices work and the result was not what I wanted to achieve. I had windows 8 on DVD and USB but every time I wanted to boot it from either of them nothing happened. It seemed as my computer didn't recognize .iso files anymore although I had made bootable USB using rufus. Installing Ubuntu instead of Windows was very easy, but it didn't work the other way around. I changed the boot priority several times and tried to disable Ubuntu so I could choose USB or CD-ROM when I turned my computer on but nothing happened. I also tried my windows 7 DVD but the result was same. What could be causing a problem like this? 
[B]
3. Programs I used in Windows and I would like to use in Ubuntu
[/B]AceStream - Ialready have VLC Media Player but can I use AceStream with Ubuntu? 
Spotify - I installed it with Wine, but is there a Linux version coming?
Office programs - I am a student so .docx, .ppt and Excel files are very important for me. Could there be any problems by using Microsoft Office programs and LibreOffice? For example when one of my professors send me files that have been made with Microsoft Office programs and I open them with LibreOffice and also the other way around. Also how different these two programs are? I have been doing research papers with Office 2010 and there are quite strict rules about its display.

[B]4. Different Windows functions that I've been used to but I can't find in Ubuntu 
[/B]'Viewing all my installed programs at the same time' - I read something about Debian, but didn't really realize what does this app do. I want to see the programs, how much space they are using and uninstall the ones that I don't need.
'Installing and uninstalling software' - I've tried using Terminal, but I find it quite hard to remember the commands and I don't want to google every time I need to install a program. I do not like Software Center and I can not find most of the programs that I want from there. I also installed Synaptic Package Manager, but I also find it quite difficult to use, so if there's a good guide for it then feel free to share it with me.

These are the biggest problems I have had since I installed Ubuntu. I am not really a 'computer person' and I really use computer for basic every day activities: watching movies, listening music mostly via Spotify, school tasks, surfing the web and social life (which is why I desperately try to connect my Sony Xperia with Ubuntu :) ). This is why I do not like to spend hours of my free time on programming or resolving problems. I just want to keep things simple and user-friendly.

I hope that my problems can be solved and I don't really need to go back to Win8.  

Feel free to ask questions, I try to get more specific when needed.

Waiting for your response,

Karl

  
[/FONT]

---

### Post by Jonathan Precise on 2014-08-11
Hi karl15, Welcome to the ubuntu forums comunity!

Yes, it can be very difficult to make that change, especially that you installed ubuntu and wiped windows. It would have been better if you set up a dual-boot in the first place. That way, when you start the PC, you can choose between ubuntu and windows. If you're on ubuntu, but then the professor gives you a document to edit, you can reboot and select windows.

As for your questions:

1) ^ See the ups. Since ubuntu (and linux in general) doesn't have good support of mtp, it would have been better to dual boot. EDIT: You can change the connection settings in your xperia to "Mass storage mode". Now you can connect your phone without problems. Since I also have an Xperia, I  can tell you where to find the setting. :) I have an Xperia E, though, so instructions may slightly vary:[INDENT]a) Open settings.
b) Under "Device" open "Xperia[SUP]TM[/SUP]"
c) Open "Connectivity"
d) Open "USB connection mode"
e) Select "Mass storage mode (MSC)"[/INDENT]

2) Seems something with the UEFI settings. Open a terminal, copy this code:
```
[ -d /sys/firmware/efi ] && echo "Installed in EFI mode" || echo "Installed in Legacy CSM mode"
```
and paste it into the terminal. Once posted the results from the command, we might better identify the problem. ;)

3) Acestream/Spotify: Try them under Wine, but if they don't work, make sure you posted the result of the above command, so we might help you with windows issues. Microsoft Office 2010/LibreOffice, yeah, there are notable differences. Since you professor is strict about it, you should dual-boot with windows. Again, ^ see the ups.

4) Let me clear things up a bit: Debian is another free OS. It is NOT a way to view installed programs. In fact, Debian is the base of Ubuntu. However, Ubuntu is easier to use than Debian, so I recommend to stick with Ubuntu.
Some general app commands:
```
# Update the list of packages (use this before installing or updating the system)
pkexec apt-get update
###
# Install ***[COLOR="#FF0000"]xyz[/COLOR]*** package:
pkexec apt-get install ***[COLOR="#FF0000"]xyz[/COLOR]***
###
# Update the system:
pkexec apt-get upgrade
```

List of installed packages in software center by clicking "Installed". Is sorted into categories. As of synaptic, it's kind of advanced, so I recommend you use Software Center. However, if you're absolutely sure you want to use it: Search for a package. Click the white box next to the package. Click "Mark for installation". Repeat until you found all packages you want to install. Click "Apply changes". Confirm the changes. Wait for it to install. You are done!

Hope it's of help! :)

---

### Post by guccimucci on 2014-08-11
Thank you Jonathan!

I really appreciate your fast reply to my thread. 

_1._ I have been scrolling the web for days to find the solution to my problem and your post finally made the day for me. I can now easily access my SDCard. Only problem is that I can't access Internal Storage with this option as I have significantly more space in there, but I can do it with AirDroid (which I found out today is a great tool and would reccommend it to others).

I can say that this problem is _solved_.

2. After entering this command I receive the following: 'Installed in EFI mode'. I didn't think about it when I made my USB bootable with Rufus. I'm not really sure which settings I used back then, but they probably affected the booting process.

If I solve the problem with Windows installation then I probably can solve the other problems as well. Does dual-booting make my computer slower? Since format, it has become quite smooth and I wouldn't want to ruin it. I'm running on 2,3ghz dual-core processor, 4GB RAM and 750GB HDD hard  drive. Do I have access to my personal files on both Windows and Ubuntu?

Edit: Oh and what do you mean by '^ See the ups' :D

---

### Post by Mark Phelps on 2014-08-11
> Office programs - I am a student so .docx, .ppt and Excel files are very important for me. Then sorry, you need to consider staying with MS Windows.  While LibreOffice CAN read SOME Office files, it is not a clone of MS Word or MS Excel, especially with the newer xml format files. I've read reviews that say that WPS office (the new name of Kingston office) is a closer match to MS Office, but haven't personally tried that.

Being a daily user of Linux distros for over ten years, and still using MS Windows daily as well, my advice is to use what works best for you.  What good is spending hours and hours hacking away if, when done, the results are unsatisfying?

---

### Post by Jonathan Precise on 2014-08-11
See the ups: see the explanation above / preform the requested action above

---

### Post by Jonathan Precise on 2014-08-11
How much drive capacity does your HDD have? That could determine if it's too risky to dual-boot.

Edit: I see now. [SIZE=1](How could I have missed it?)[/SIZE]

The files in ubuntu will not be accessible in windows. Do you have too many files in ubuntu? If so, back up, format the whole drive to ntfs, install windows, use the windows partition re-sizer once installed to shrink the partition by approx. 300 MB, reboot twice, and post so we can guide you to installing ubuntu on the free space through manual partitioning.

---

### Post by JKyleOKC on 2014-08-11
> **karl15 said:**
> I'm running on 2,3ghz dual-core processor, 4GB RAM and 750GB HDD hard  drive. Do I have access to my personal files on both Windows and Ubuntu?With these specs, your hardware is quite capable of running a virtualization program that can give you access to both Windows and Ubuntu at the same time. What I'm about to suggest may sound quite scary, however, since you're just starting to learn a whole new system that's quite different from Windows in many ways. My wife, for an example, has never really accepted the whole premise of "virtualization" since it sounds so much like magic -- but she's able to use it, nevertheless, once I set it up for her.

There's a program that you can find either through the Software Center or through Synaptic, called VirtualBox (the capitalization is essential when you search for it; unlike Windows, Linux treats uppercase and lowercase characters as being totally different). This program allows you to create what are called "virtual machines" or VMs, which then for all practical purposes are additional brand-new (and empty) computers completely separate from your original or "host" machine, but can commuinicate with it.

If you install this program and create a new VM, giving it perhaps 768 MB of RAM and a 10-GB virtual drive, you can then install Windows on that new VM together with all the Office software you need. You'll still have your entire Ubuntu system, in addition to the new VM, and you can switch between them with a few clicks of the mouse.

That's exactly what I do here, with almost a dozen different VMs installed on a host Xubuntu 12.04 system (same as Ubuntu but with a different window manager program), on hardware that's almost identical to yours. I run only one of the VMs at a time; the rest remain suspended and inactive, only taking up disk space. When I need Office, I start the VM that contains it; I can transfer files between the host and the VM easily, so I have the best of both worlds.

I realize that this all sounds magical, but it DOES work and might solve your problem without the hassle of reformatting and rebooting frequently. A number of us here on the forum can help you through the installation and setup process, if you want to try this idea. There's even an entire forum here devoted to "virtualization" with additional information.

Using VMs is not for everyone; they ARE slightly slower than "native" installation and this makes them unsuitable for high-end game play, but my experience has been that no slowdown is noticeable in everyday use of Word or Excel. The versions available through Software Center/Synaptic are almost always slightly obsolete, but up-to-date versions are readily available through the publisher's own website -- and the repository versions are plenty good enough to get anyone started.

If you want to know how such a thing is possible just ask; we can explain it, but the details are a bit much to try to set forth in this initial message. It's not magic, just strict logic that goes back to the days before computers even existed.

Hope this helps -- and doesn't just introduce a new element of confusion for you!

---

### Post by whitesmith on 2014-08-11
The entire Windows Office suite can be installed under Wine (but you're in for some hacking) or with a paid variant of Wine called cxoffice from a company called CodeWeavers. I can attest that a 100.0% compatible installation is trivially possible under cxoffice. Cheers!

---

### Post by guccimucci on 2014-08-11
Thank you for your replies! I now see why Linux communities are praised. 
I am back on Windows 8.1 and Ubuntu is gone. I've thought about VirtualBox and it does seem like sci-fi for me at first, but I could give it a try. I found a decent guide for setting up VirtualBox from here [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox). At the moment the biggest problem as Jonathan already mentioned was that I rushed to Ubuntu and forgot about my technical abilities. If I had had both Windows and Ubuntu I could've saved a lot of time. 
I'll read the forum and do some research and get back to you if I have any problems.

---

### Post by mooreted on 2014-08-11
I'm pretty sure you can run Office 365 in Linux. It is a full-featured Office 2013 implementation on the web so you can use and share MS Office documents for your classes.

---

### Post by guccimucci on 2014-08-12
I've decided to use Ubuntu and Windows by dual-booting, but I can not boot from my USB to install Ubuntu back on. It seems as I've messed up my boot somehow, because when I disable secure boot, have fast BIOS enabled and try to boot from USB nothing happens. I get to 'boot menu' and I have following options there: my hard drive, Cd-rom, Ubuntu (although I don't have it in my system anymore?) and Windows Boot Manager. It won't boot from any of these and sometimes my memory stick is included in there, but it doesn't boot from there either. I have to enter BIOS again and disable 'fast boot', then it'll just boot windows 8.1. I read that it might be problem with Samsung laptops. 

At the moment I have set 'fast boot disabled and selected CSM or UEFI OS' when I selected 'UEFI' it'll take me to boot menu and doesn't boot from any of the devices listed there and if I choose 'CSM' then it'll start Windows Setup.

I've had the same problem for days now as I tried to boot from Windows DVD and USB both when I had Ubuntu on, but nothing happened. Now I have the same problem when I try to do it the opposite way (have win 8.1 and want to install Ubuntu). When I got windows back on it sort of 'happened somehow' as I had boot problems and then I accidentally entered to Windows setup.

I probably messed it up somehow as I've changed win 8, ubuntu, win 8.1 several times last week.

---

### Post by Jonathan Precise on 2014-08-12
Hello karl15!

Did you shrink the windows partition by 300 MB? Ubuntu's re-sizer sometimes tends to break windows, so it's better to re-size from windows itself to avoid any errors. Reboot twice and run chkdsk.

Please do NOT boot USB disk in UEFI mode, as it may cause PERMANENT failure on some Samsung laptops. The only way to fix this is buying a new motherboard, or have your warranty fix it (if you still qualify for warranty).

Burn a 64-bit ubuntu DVD, from [ubuntu.com/download]("http://www.ubuntu.com/download"). Make sure your computer is in CSM mode, and change the boot priority in the BIOS to boot from DVD first. You should boot to Ubuntu Live DVD. Once there post to let us guide you through the manual partitioning.

---

### Post by guccimucci on 2014-08-12
Edit: Managed to install Ubuntu. Both OS seem to work fine. I'll make new topic about more specific questions about dual-booting.

---

### Post by guccimucci on 2014-08-13
> **whitesmith said:**
> The entire Windows Office suite can be installed under Wine (but you're in for some hacking) or with a paid variant of Wine called cxoffice from a company called CodeWeavers. I can attest that a 100.0% compatible installation is trivially possible under cxoffice. Cheers!

MS Office 2010 works as a charm! I was also able to set it my default text editing program, so I can easily open .docx and other file types. Thanks!

---

