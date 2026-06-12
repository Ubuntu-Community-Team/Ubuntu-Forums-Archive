---
title: "Ubuntu boots off a USB but not off hard drive"
date: 2016-04-21
forum: New to Ubuntu
---

### Post by Mc_Fow1er on 2016-04-21
I've been attempting to install Ubuntu to properly try it out in every day use for about a month now and I've had no luck what so ever making it boot.
Both my motherboards and laptop have a UEFI boot option *but* do not seem to boot to anything other than windows unless it's on an external device like a USB.
I have managed to semi boot Ubuntu using rEFInd on a flash drive but it kept booting to recovery mode so I didn't really count those as a successful boot.

I'm using Ubuntu 15.10 for this, I had initially planned to use GRUB2 on the drive to multiboot between Ubuntu, Windows 10 and SteamOS,
I tested the idea out in VirtualBox and it worked more or less flawlessly save for the fact of virtual hardware install requirements.
Anywho because I did this all on a bare write to the drive I expected that it might work out if I just popped the drive into the laptop, unfortunately it only booted windows..
I later bare partitioned the drive as a GPT and tried to install the OS directly on the hard drive and the install went flawlessly, save for the the fact of it didn't boot..
No U/EFI entry in boot menu and legacy mode booting didn't work, just blank screen with a non-responsive cursor, any body know what I'm doing wrong here?
Please someone tell me what I'm doing wrong because this is starting to drive me up the wall...Installing another OS, not as easy as I thought it would be...

Boards:
ASUS P5G41t-M LX3 (My current desktop board)
Intel DX8BT (My old desktop board)
Aspire 5750Z (Laptop)

---

### Post by oldrocker99 on 2016-04-21
Most UEFI motherboards I've seen have a "Legacy" option along with UEFI. Some (ASUS, for example), you have to search and find the toggles (I'm running MSI's 970 Gaming mobo, so I can't help you find the toggles--sorry). Some (MSI, Gigabyte) default to Legacy AND UEFI together. Otherwise, you couldn't boot Windows 7.

---

### Post by Mc_Fow1er on 2016-04-21
Well the thing is that all three boards have a dual mode of the boot type, the laptop has an EFI boot priority option for booting any EFI entries it finds first over legacy, other than that there's no toggles that would switch boot type from UEFI to legacy and back. Anyway the point I'm more getting at is why it's not allowing booting of any internal devices to be anything other than windows when there is no secure boot function at all, I actually did a system spec check and secure boot isn't even supported by the Mother boards.

---

### Post by oldfred on 2016-04-21
Microsoft has required vendors to allow users to turn off Secure boot. So every system seems to have a way. But some are just automatic, other require somewhat confusing settings in UEFI/BIOS.
Many now call UEFI Secure boot "Windows", and "Other" as non-secure boot which then can be either UEFI or BIOS/CSM/Legacy. If Windows 7, you have to use the "Other" setting as it does not support Secure boot, but can be UEFI and normally defaults to BIOS install.

Pick one system for this thread.
       But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Mc_Fow1er on 2016-04-22
I'll go with the laptop as I'm most likely to use it compared to the other boards, how ever I'm hopeful that the fix will effect all systems not just the one.
Here's the log boot repair gave me: [http://paste.ubuntu.com/15979773/](http://paste.ubuntu.com/15979773/)

Just bare in mind this was the old install setup I had made then never got around to formatting the drive, it all worked when I stuck it in Virtual Box though so I'm quite confused..I formatted a 250 GB drive and just stuck win10 on it for for the time being, this is a log containing the actual drive I plan on using for the setup though.

---

### Post by Mc_Fow1er on 2016-04-22
I'm planning on doing fresh installs of each OS tomorrow morning with the following in order:
1. SteamOS
2. Windows 10
3. <Maybe some other OSs here>
4. Ubuntu 16.04

If that makes any difference what so ever.

---

### Post by oldfred on 2016-04-22
You show grub in both in gpt's protective MBR and in the ESP - efi system partition. Which says you have tried to install in both UEFI and BIOS boot modes.

You have to be consistent either all UEFI or all BIOS/CSM/Legacy. And with newer hardware UEFI probably is better, but many systems do not make it easy to boot anything other than Windows.

With any Windows after Windows 7, you must make sure fast start up is off, or the Linux NTFS driver will not see it since it is hibernated. Whether UEFI or BIOS. You currently show fast start on.
       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold) 

Also probably better to install Windows first. It still does not recognize other systems. But only use Windows to shrink the NTFS partition and reboot immediately so it can run chkdsk and repair itself to its new size. Do not create partitions with Windows, use only gparted or command line tools.

While you show both steamOS and ubuntu folders in ESP, you do not show entries for either in UEFI.
Boot repair runs this command to see UEFI entries, you should also see if you boot into UEFI/BIOS:
sudo efibootmgr -v

Do you have latest UEFI from Toshiba. And if you install that it will reset to defaults. On my UEFI I have to keep track of many changes and redo them with every UEFI update.

It says Toshiba, many newer Toshiba's violate UEFI spec and use description as part of boot. And of course only valid description is "Windows Boot Manager". But there are multiple work arounds. Most use UEFI's fallback or default drive boot entry or /EFI/Boot/bootx64.efi and make that file really shimx64.efi and boot hard drive entry. You may have to create that, many UEFI auto create after a reboot or two. And Boot-Repair now automatically copies shim to bootx64, but does not create new UEFI entry, but if necessary we can with efibootmgr. Refind is another alternative boot manager. But grub2 is boot manager and UEFI is boot manager. Grub is also the boot loader for Linux.

What model Toshiba?

 Toshiba Satellite - turned Secure boot off in Boot-Repair update
[http://ubuntuforums.org/showthread.php?t=2317643](http://ubuntuforums.org/showthread.php?t=2317643)
Toshiba satellite z930 copy shimx64.efi to /EFI/Boot/bootx64.efi
[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair
[/URL]
 Toshiba Satellite L15W - Boot only Linux rename UEFI Windows or rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2263473](http://ubuntuforums.org/showthread.php?t=2263473)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba Satellite P55-A (UEFI) [SOLVED] Trouble installing Xubuntu 14.04 - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Toshiba shows BCD entry
[http://ubuntuforums.org/showthread.php?t=2259331](http://ubuntuforums.org/showthread.php?t=2259331)
Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)
Toshiba Satellite supergrub to boot to fix things
[http://ubuntuforums.org/showthread.php?t=2240884](http://ubuntuforums.org/showthread.php?t=2240884)
Toshiba C55D-A5163 - Installation of Lubuntu on computer with Windows 8.1 Feb 2015
[http://ubuntuforums.org/showthread.php?t=2267268](http://ubuntuforums.org/showthread.php?t=2267268)
TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T - rEFInd
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742) 

[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]
[/URL]

---

### Post by Mc_Fow1er on 2016-04-22
Okay I'm gonna answer in order to what you've posted just to make things easier and not just post random bits in random spots.


First off I don't know what may have caused that to occur, it may have been SteamOS writing it's own grub, currently SteamOSs' debian GRUB is taking boot priority when booting from within Virtual Box.

I knew of the all UEFI or BIOS rule but I was not aware that the OSs had done their own thing with installation type, I was just assuming that they were all booting to UEFI mode.

I had already disabled that annoying fast startup feature but I remember now that with that procedure you'er also meant to disable hibernation all together in order to kill it.

And I did all the partition work in GParted, I never trust windows with partitioning, it usually cocks it up. I do all my partitioning before installing any OS to my drives.

And it's actually an Acer Aspire 5750Z, no bloody clue what the BIOS is but I know the entire system ain't too recent. And I actually used rEFInd on my USB to boot between GParted and boot repair, I had initially planned on using GRUB2 as the drive boot manager but then discovered rEFInd which seemed like a bit of a better solution to my problems plus it have me access to the UEFI shell which I had in Virtual Box which I sort of but didn't really under stand but it's still a useful thing to have around just in case. In any case external devices boot but internal devices don't, as the title suggests. As for updating BIOS/UEFI updates, I have not clue where to look, searching for the model didn't yield any results for me which left me rather frustrated because I'd rather know that my system is up to date rather than running on software that has had important updates, probably.. If you actually managed to find an update for this thing I'd be both amazed and grateful, and I remember coming across something to do with efibootmgr but at the time I was rather tired and I don't know what happened with the tab I had open.

Anyway as I had said it's actually an Acer Aspire 5750Z, not a Toshiba. (Acer is like the Samsung of phones but for laptops..)
Don't know if that changes/complicates things for this..

Also tell me if you need stuff like BIOS info given that this thing seems to be in shambles..


Oh, and here's some EFI info given by rEFInd if this makes any differance to the matter at hand:
```
Running on:
 EFI Revision 2.00
 Platform: x86_64 (64 Bit); Secure Boot inactive
 Firmware: INSYDE Corp. 4096.01
```

---

### Post by oldfred on 2016-04-22
I have not tried rEFInd, yet. It has been on short list to try for quite a while.

Acer is actually one of the better UEFI, but has a unique requirement that no one else seems to have.
All Acer we have seen need a UEFI password, and then setting "trust" on UEFI/efi boot files. If using rEFInd and SteamOS, you probably have to do that on them also.

I saw this, and why I thought Toshiba, normally Acer has a couple of entries somewhere in Summary Report.
      >  Boot0003* TOSHIBA MK2555GSX  


Was this really another drive?

Make sure you have newest UEFI from Acer:
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)

---

### Post by Mc_Fow1er on 2016-04-22
Well I recommend that you get a spare USB and plonk [rEFInd]("http://www.rodsbooks.com/refind/") onto it because I literally just dumped win10s' installation files (more like just the folders) onto it and moved its efi boot file into the microsoft directiry under EFI, no need for bootmgr at all as well as I stuck the boot repair disk contense on, just fiddle around with the files accordingly mainly just changing and using common sense with renaming boot files, I had to put GParted GRUB config files into the boot directory but other than that it worked flawlessly, sure it's a bit messy but hey, three utilities that are all completely bootable? Being messy is worth it, but you just have to be very VERY careful about file over writes...Like the main EFI/Boot/ folder containing rEFInds' booting EFI files. If anything it makes for a great emergency OS booter as it has a sort of "scan on start" type of thing so if you break something with GRUB by accident you can go and boot which ever OS you need to fix it.

And I'll take a look at the Acer links, and yeah, that was probably the 250 GB "main" drive that I tend to hotswap with the 80GB which is what I'm installing all the OSs to, the 250 is a win10 solo install. I'll tell you my results hopefully come the morrow as I'm currently reinstalling win10 on the 250 under the GPT table and as a UEFI entry because why not. I'll reinstall it on the 80GB as well then do the other OSs accordingly, also that 15 odd GB empty space was meant for some other OS but I never really figured out which other OS I wanted.

---

### Post by Mc_Fow1er on 2016-04-24
Okay so it turns out that the laptops firmware is as up to date as it will ever be. And I've decided that while I read through the threads I'd try doing a fresh, automated install will actually work because as far as I know that shouldn't require any user input for making it work after installation. But that failed to boot as well, no UEFI-boot entry in the POST-boot menu (F12). I tried to install windows then Ubuntu on the 80GB and it only shows under the same menu:
```
Unknown Device: Windows Boot Manager
```
Followed by the "BIOS" devices. If anything I don't think this laptop is gonna be too willing to actually work..Especially given the unhelpful nature of this things' BIOS.....Currently my only work around is to use rEFInd on my USB and boot from it to boot Ubuntu on the laptop, I've tried setting a supervisor pass in the BIOS and nothing new appeared, and as I stated before there's no "boot from EFI" entry anywhere within it. Also it's a 5750Z no an E model, no surprise that this thing is probably too old to load anything other than a signed windows key..Now do you see why I say Acer is like the Samsung of laptops? Always do things differently to everyone else, always make it a pain to do things...Seriously why can't manufacturers just things easy, doesn't do them any good for their reputations..

---

### Post by oldfred on 2016-04-24
The automated install will use unallocated space and give some to swap and rest to / (root).
But how you boot install media, UEFI or BIOS is then how it installs. And then you have to go into your UEFI and set it to boot in that mode.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

---

### Post by Mc_Fow1er on 2016-04-24
No you don't under stand, Ubuntu literally doesn't show up as a boot option in the boot menu and the only options relating to UEFI in the BIOS are "UEFI Boot" and "Boot EFI devices first". Those two and those two alone are the *only* things related to UEFI, no entries for UEFI in the BIOS boot menu only after POST does it actually show UEFI entries in the F12 boot menu even then the only UEFI entries that seem to pop up are that of windows boot manager. I can boot grub and such just fine when I execute them through rEFInd on my USB, but other than that no way to boot directly off the drive into anything other than windows.

---

### Post by oldfred on 2016-04-24
Again which computer.
Acer requires Supervisory password, and setting of trust before it allows Ubuntu/grub entries to work.
Many systems have violated UEFI standard that specifically says not to use description as part of boot, and of course only valid description is "Windows Boot Manager". So we have many work arounds for those systems, but you cannot boot an "ubuntu" entry in UEFI. Usually you boot a hard drive entry that uses /EFI/Boot/bootx64.efi which you make be really shimx64.efi.
Boot-Repair will copy shim to bootx64, but does not add an UEFI entry. Many systems automatically have or add an entry for the hard drive.

Also details in link below in my signature.
 Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

### Post by Mc_Fow1er on 2016-04-25
I've said multiple times it's an Acer Aspire 5750Z, if anything..Once I figure out how to make it work I'm posting a tutorial in here then dubbing it solved. But one thing is certain: I'm gonna be using rEFInd. And I'm gonna at least try to make Ubuntu/GRUB2 work though, if I can't well then I guess I'm posing a tutorial on how to make it work using rEFInd. (Sorry for such a late reply, stuff kept popping up..And I kept on getting side tracked.) Though trying to make a new entry under the NVRAM entries using EFI Shell 2 yeilded no results, reset every time even removing the windows boot entry was reset..

---

### Post by oldfred on 2016-04-25
Many like rEFInd. I have yet to try it, but plan to.

But even with rEFInd, you have to go into Acer's UEFI set supervisory password and enable trust on the rEFInd efi boot files. I think one of the threads on Acer was rEFInd. But multiple threads with Acer have posted details on password & trust.

---

### Post by Mc_Fow1er on 2016-04-26
But the problem with that is that there aren't any entries for EFI file trusting, that's the problem. Even with UEFI enabled under boot and a password set on supervisor there's no additional points of configuration. But I found the problem, the laptop is hard coded to ONLY boot EFI\Microsoft\Boot\bootmgfw.efi. Discovered through trial and error, and the installation of GRUB2 and rEFInd is the exact same process in this case. After I've installed SteamOS I'll post the tutorial though this wont be the typical Ubuntu users walk in the park, though I will admit after about 10 minutes I was having fun playing around with the EFI entries and such.

---

### Post by oldfred on 2016-04-26
You need to review the links on Acer, users have in some cases post details.

I copied on of those here:
[http://ubuntuforums.org/showthread.php?t=2321783&p=13477904#post13477904](http://ubuntuforums.org/showthread.php?t=2321783&p=13477904#post13477904)

---

### Post by Mc_Fow1er on 2016-04-26
I went through them and this laptops BIOS varies *significantly* from other Acer BIOS setup tutorials and images, if needs be I can take a picture for you if that would help you with what this things BIOS is doing, if anything placing any efi file as: ```
EFI\Microsoft\Boot\bootmgfw.efi
```
Makes the boot name of it show as "Windows Boot Manager" under the boot list even though it *clearly* isn't windows boot manager, but they boot just fine. Once this install of SteamOS is done I'll give a full list of actions as well as BIOS pics for you to have a loot and see that there's no way to change what EFI file boots from the internal hard drive.

[SIZE=3]For very basic clarification of what this things BIOS is, imagine a legacy BIOS that was updated to be able to boot UEFI. That's the best way I can describe it in a nutshell.
My old intel board from 2007 wasn't able to boot UEFI until I updated the BIOS to something that I think was released in 2012 which is why I describe it as such.[/SIZE]

---

### Post by oldfred on 2016-04-26
One of the old work arounds was to copy grubx64.efi or shimx64.efi to EFI\Microsoft\Boot\bootmgfw.efi. 
That is generally not recommended with any dual boot as Windows updates overwrite it. But it can work.

Often better if only booting Ubuntu is to rename the "ubuntu" UEFI entry to "Windows Boot Manager". Most systems still think they are booting Windows as the only check description not path of boot files.

Post this:
sudo efibootmgr -v

And every newer UEFI also boots /EFI/Boot/bootx64.efi. That was required way to boot all external drives and both Windows & Ubuntu create bootx64.efi, but with their own actual files. An update to UEFI standard also then specifies that internal drives also can boot from /EFI/Boot/bootx64.efi as fallback or default hard drive entry. This is still another work around for systems that will not boot an ubuntu entry.

Details on work arounds in link in my signature and:
       Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

### Post by Mc_Fow1er on 2016-04-26
I'll give that a test on my dummy drive and see how it goes. As for the \EFI\Boot\bootx64.efi..Yeah I doubt that that's gonna be allowing it work any time soon, every attempt I had done with EFI/Boot has failed, I even tried using my dummy drive to just rename the boot manager files that it had and it failed to pick up windows even though the EFI\boot\bootx64.efi was able to link to the BCD just fine which should have allowed it to kick off, so far the only entry that it seems to accept from a hard drive is that of windows bootmgfw.efi..USB devices boot from \EFI\Boot\bootx64.efi but internal hard drives boot from EFI\Microsoft\Boot\bootmgfw.efi. I'm fairly certain that counts as hard coded. Next I'll try wiping the drive and installing some flavour of linux and then renaming the entry/directory in the ESP to that of windows as a last point check as I'm fairly certain that I have in fact a hard coded laptop that does not use a description boot but a selective Boot path to windows instead. But all of that in the morning.

---

