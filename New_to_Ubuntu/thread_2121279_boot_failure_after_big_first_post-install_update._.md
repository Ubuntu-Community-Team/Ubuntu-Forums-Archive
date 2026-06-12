---
title: "boot failure after big first post-install update. boot-repair created two ubuntus?!"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by emugod on 2013-03-01
After way too much hassle with UEFI settings I got ubuntu 12.04.2 LTS installed and working pretty well; multiple shut-downs and restarts without issue. Windows would not boot from grub2 (and still will not afaik), but it boots from UEFI/BIOS boot menu and that was fine for me for the time being. There was a problem where the grub2/splash screens would sometimes be very distorted, squished into the top 500 or so lines of the screen (making the text illegible), but it only occured intermittently and was always limited to those two screens (not the GUI) so it didn't bother me too much.

I downloaded and installed ~210MB of recommended updates, VLC, Comix, and Steam (all in one session) and shut down (NOT 'restart and apply updates', just shut down; i felt i should switch UEFI/BIO boot order from windows8 to ubuntu first before proceeding?). The only thing that went wrong was I had to kill "Additional drivers" ("jockey"-something, which had been set to download a proper graphics driver) from system resources because I had to shut down and it was not responding (maybe just being slow, though). I didn't think this caused any problems, it certainly didn't at the time? This morning I try to start it back up and I get a failure to boot (windows can still boot just fine through UEFI/BIOS boot menu) reporting a number of problems(?);

firstly right at the top it had:
swapon: dev/disk/by-uuid/*long alphanumeric available on request*: swapon failed: Device or resource busy
mountall: swapon *long alphanumeric available on request*[2760] terminated with status 255
mountall: Problem activating swap: *long alphanumeric available on request*

then a few other things i *think* were not so important (boot sector having a minor difference from backup it declined to automatically fix?), and then at a long list of modem-manager packages/drivers(?) it loaded, and then at the bottom:

AppArmor skipping firefox and rsyslogd profiles, and speech-dispatcher and saned being disabled (i don't know what either of those two are but they sound like they could be important?)
this screen ended immediately thereafter with a blinking cursor unresponsive to any key press. but just tapping the power button initiated a shut-down procedure with many commands flashing up.

I booted the liveusb i had made (and am running to type this), downloaded installed and ran boot-repair (side question: how do i add this permanently? I should have 4gb of persistent space?) twice, because the first time i accidentally told it not to give me the url log (from second run: [http://paste.ubuntu.com/5576462/](http://paste.ubuntu.com/5576462/)), and then restarted. now the previously intermittent graphical distortion is constant (afaik through a few attempts), and boot still fails (i just now can't even read the screen it fails on...). Even worse(?) I now have two Ubuntu boot entries! I have no idea what i'm doing. The instructions on [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) say I should now run boot-repair once more, but i am afriad, after it apparently made my situation so much worse!

edit - update and clarification:

i did decide to go ahead and run boot-repair again ([http://paste.ubuntu.com/5576695](http://paste.ubuntu.com/5576695)), and then spent a while restarting and checking things out. It still does not boot, but the the error messages (which i am not even sure ARE error messages, or if they are just startup processes that hang?) have subtly changed (and seem to now be changing somewhat every time). but it always ends with the same messages about speech-dispatcher and saned being disabled, so i think that is my problem. except for the very first time i retried after boot-repair i got a new block of messages at the bottom which i think was just to do with error reporting;
```
Stopping System V initialization compatibility
Starting System V runlevel compatibility
Starting Auto Crash report
(four more can post if needed, down to:)
Starting anac(h)ronistic cron
(four more, then:)
Stopping anac(h)ronistic cron
```
and then a hanging unresponsive cursor

to clarify i have both a surplus Windows 8 and Ubuntu boot item, and they only appear in the UEFI/BIOS, not grub2.
only one of these ubuntus presents to deformed graphics, the other is fine. i'm not sure if the 'fine' one is actually the old one that was experiencing it intermittently, or what? but it seems to be the one i am stuck with because the alternative is illegible.

I am really tempted to just uninstall and reinstall from scratch at this point; I really want that TF2 hat and the clock is ticking! :lol::o:):(:oops:

edit 2: some more research on 'ubuntu speech-dispatcher/saned disabled' and now i am thinking this may be a graphics driver failure, likely because of my impatient killing the process... which is strange because i was positive it hadn't even finished downloading. i have scribbled down the commands i need in a notebook, and now just have to hope the ctrl-alt-f1/f2 i saw somewhere (to unlock terminal once on 'ugly black screen') works... wish me luck!

---

### Post by oldfred on 2013-03-01
Not sure what you are seeing. You only have one Windows install in sda5. But some systems create another partition with efi boot files which seem to be for recovery. You only can have one efi partition, so it may somehow change boot flag (which makes the efi partition the efi partition) from sda2 to sda3 for recovery. But Boot-Repair sees all the efi files and adds entries to boot them. It also copies as backup, the Windows boot file into the sda5 partition, but then may make an entry for it. And grub has a bug and its entries will not work. So only the Windows enties in grub menu refering to the efi partition sda2 should work. All the others will not boot Windows.

You also have this extracted from UEFI. I do not understand why it shows two. Is one current & the other previous or two different choices in UEFI menu? Second shows boot 00004 which is ubuntu as default.

```
 BootOrder: 0003,2001,0000,0000
Boot0000* Lenovo Recovery System
Boot0001* EFI Network 0 for IPv6 (B8-88-E3-7D-4A-3B)
Boot0002* EFI Network 0 for IPv4 (B8-88-E3-7D-4A-3B)
Boot0003* Windows Boot Manager
Boot0006* EFI USB Device (USB 2.0 SD/MMC Reader)
Boot2001* EFI USB Device
BootCurrent: 0006
Timeout: 2 seconds
BootOrder: [COLOR=#ff0000]0004[/COLOR],0003,2001,0000,0000
Boot0000* Lenovo Recovery System
Boot0001* EFI Network 0 for IPv6 (B8-88-E3-7D-4A-3B)
Boot0002* EFI Network 0 for IPv4 (B8-88-E3-7D-4A-3B)
Boot0003* Windows Boot Manager
Boot0006* EFI USB Device (USB 2.0 SD/MMC Reader)
Boot2001* EFI USB Device
Boot[COLOR=#ff0000]0004[/COLOR]* ubuntu


```

These should work, others are to different UUIDs so not to efi partition.

```
 /dev/sda2       [COLOR=#ff0000] 54D2-9F55[/COLOR]                              vfat       SYSTEM_DRV

menuentry "Windows UEFI recovery bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root [COLOR=#ff0000]54D2-9F55[/COLOR]
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

   menuentry "Windows Boot UEFI recovery" {
search --fs-uuid --no-floppy --set=root [COLOR=#ff0000]54D2-9F55[/COLOR]
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}


```

I think having recovery in the title is a bug in Boot-Repair.
This version includes Boot-Repair.
 [https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by emugod on 2013-03-01
Thank you for your help oldfred, but sorry I couldn't get back in time to say; booting again! by disabling the graphics driver (in jockey-text), which apparently had been partially (corruptly) installed. Also sorry that most of what you wrote there is TOTALLY lost on me. I will try to clarify, though, and maybe you can make some sense of it;
The 'extra' Windows8 and Ubuntu boot options did only appear this morning after I ran boot-repair, and only in the UEFI/BIOS, not grub. they are named exactly the same, but the Ubuntu ones show very clear differences in that only one produces the corrupted graphics I described. I'm not sure if I've actually tried either of the Windows8 ones yet.. don't want to even think about any potential problems there. Aside from that all I can offer is that I have known from the start this laptop came pre-loaded with a lot of funky partitions; two windows recovery and two lenovo recovery partitions, plus two other small partitions of unknown purpose or effect (i am 99% sure one of them is just empty... not going to test it, for the relatively small amount of space). I have already shrunk the major lenovo one way down; it just holds some backup drivers totaling ~1.5gb iirc, but came set to use 30gb!

now i will be gone for a while again, using liveusb partition expansion utility to free up more space (i am just a few gigs short of what I need for tf2, plus i'd of course like to have some extra over that as well) This may require a trip back into windows to uninstall some stuff there (lenovo = bloatware, most of which i've never bothered to uninstall), so i may be able to confirm which of the two windows8 boot options work.

---

### Post by oldfred on 2013-03-01
Do not delete any Windows partitons. For example it has the MSR or Microsoft reserved. That is totally unformatted space which I believe it uses for DRM - Digital Rights Management or other purposes. In MBR it used to use the sectors after the MBR and sometimes we had conflicts with DRM and grub2's core.img.

With 12.10 we had to install the headers to get the video drivers to install correctly. It should update, but I have seen several posts with issues and it seems the new kernel does not automatically intregrate the kernel & video drivers. Did you install nVidia or AMD drivers?

---

### Post by WesternRyno on 2013-03-01
What if one did delete the Windows partitions, as I did?

---

### Post by emugod on 2013-03-01
> **oldfred said:**
> Do not delete any Windows partitons. For example it has the MSR or Microsoft reserved. That is totally unformatted space which I believe it uses for DRM - Digital Rights Management or other purposes. In MBR it used to use the sectors after the MBR and sometimes we had conflicts with DRM and grub2's core.img.
Yeah something crazy like that is what i figured, and why I have never touched it. Will continue my hands-off policy.

> **oldfred said:**
> With 12.10 we had to install the headers to get the video drivers to  install correctly. It should update, but I have seen several posts with  issues and it seems the new kernel does not automatically intregrate the  kernel & video drivers.
I didn't get any of that, but I'll remember to recheck this post later when i even do get to really worrying about it (although actually playing it on Linux is also definitely a goal, launching tf2 to get the tux canteen has a deadline attached). Thanks in advance.

> **oldfred said:**
> Did you install nVidia or AMD drivers?
It's an AMD Radeon 6310 jockey-reccomended stable version, and I can now confirm it just plain doesn't work :mad:.  After reinstalling it (with patience this time), it still produces the same  result. Currently on my liveusb waiting for GParted to finish, and then I  will run a bootrepair just to be safe. And then go through the hassle of  disabling the driver through terminal again... and if i'm interpreting your post right, it sounds like just trying the eperimental version probably won't get any better results. could you elaborate a little more on installing headers and inegrating the driver/kernel?

edit:
What I am really interested in at this moment is how do I work with the supposed persistent element of my LiveUSB? this is the third time I have reinstalled boot-repair TODAY, it would be real nice to just have it. And to be able to customize the environment, store logins/history/bookmarks for firefox, maybe even add steam+GMS+project copy right to this drive if i have the space. etc.

---

### Post by oldfred on 2013-03-01
If you have the secure remix then that includes Boot-Repair.

I think you just add persistent and maybe another partition.
       [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

 With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)

      Large persistent - C.S.Cameron post 6 & 7
[http://ubuntuforums.org/showthread.php?t=2041679](http://ubuntuforums.org/showthread.php?t=2041679)

@WesternRyno
Did you backup before install. Do you also erase the vendor recovery. If so the only remaining alternative is to order a new DVD set from Vendor. Some only charge a nominal shipping fee.

---

### Post by WesternRyno on 2013-03-01
@Oldfred Ok, this is what I thought.  I'm ok wiping it, just wanted to make sure there aren't any hidden surprises from having done so.  Sorry to hijack this thread.

---

### Post by emugod on 2013-03-01
[IMG]http://s11.postimage.org/6vv1ceo3n/victory.png[/IMG]

now to actually get it to run, instead of freezing at the load screen. OldFred would you care to elaborate any more about the driver issue?

---

### Post by oldfred on 2013-03-01
I do not know much about Video drivers other than my nVidia. 

       # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

      
 Update does not rebuild the video kernel interface 3.2.0-38 - and others?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1132092](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1132092)

   Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

      
 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by emugod on 2013-03-02
@oldfred thanks, that is what I will be looking at next, and I'm sure your links will prove a good starting point, when i actually get back on this project later today or tomorrow.

just a quick update: the surplus Windows8 boot option has mysteriously vanished, and Windows boots fine from the other (what I am back to for the time being, victory having been achieved concerning the hat). I don't know whether this was fixed by the third run of boot-repair (after partition resize) or what. The surplus ubuntu option remains. paste.ubuntu.com/5577256

---

### Post by oldfred on 2013-03-02
Boot Repair is saying your Windows is full. Windows needs 30% free space to work well and at 10% free defrag may take forever as there is no working room.

>  /dev/sda5      fuseblk    255G  255G  888M 100% /mnt/boot-sav/sda5



You can edit the entries Boot-Repair creates in 25_custom, so it does not say recovery or remove one's that you do not need.
       sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkup25_custom
gksudo gedit /etc/grub.d/25_custom
Then do:
sudo update-grub

In the grub.d folder all executeable files starting with 2 digits & and _ (underscore) will be processed. So I renamed backup of 25_custom to not start with those rules. You can also turn off execute bit and then it will not run either.
      
 sudo chmod a-x /etc/grub.d/bkup25_custom

---

### Post by emugod on 2013-03-02
> **oldfred said:**
> Boot Repair is saying your Windows is full. Windows needs 30% free space to work well and at 10% free defrag may take forever as there is no working room.

haha thanks for your concern, but i've been running with well under 10% free space for a long while now. I was a bit concerned about potential trouble letting it fall briefly under 4 gigs (3 gigs of memory), but it worked just fine (and i have since deleted some stuff to get it back up to a healthy buffer. I definitely do need to clean this machine up, though.

About the other stuff, i'm not really concerned about the surplus Ubuntu boot item, either, and what you suggest concerning boot-repair seems like an easy way for me to cause myself a lot of troubles by messing with things I don't understand. I'm not sure I want to mark this thread solved yet, as I do still have to get a proper graphics driver working, but for the time being I'm content with the stability of the installation and have other things to work on.

---

### Post by emugod on 2013-03-03
Ok, i'm going to get moving on getting a graphics driver, again. Specifically I think I will follow the advice of
[http://steamcommunity.com/app/221410/discussions/4/864960353822274949/?tscn=1361421411](http://steamcommunity.com/app/221410/discussions/4/864960353822274949/?tscn=1361421411)

Before I do that, though, I want to make sure that, in the event of failure, this driver will be available to deactivation through the jockey-text program? Otherwise how would I disable it and return to basic driver? Or should I just try the 'experimental' driver, first, before leaving the realm of 'jockey'? Is there any chance of it working where the 'update' version seemed not to?

It also just occurs to me that I am not even really certain jockey-graphical did redownload the first driver? As opposed to just reinstalling the same potentially-partial/corrupt version I had already downloaded? It certainly took long enough to complete. Does it always redownload, or not?

---

### Post by oldfred on 2013-03-03
I only know about nVidia drivers and I always install the one's offered by Ubuntu. You may do better in a new thread with correct title.

But with 12.10 and maybe 12.04.2 you need to make sure you have the headers first. And it looks like sometimes with new kernels you have to reinstall headers or video driver, so if after kernel update you have issues that may be the reason.

Do this before installing any video drivers, if you have headers it will just say so.
       # You may need headers first - meta package :
sudo apt-get install linux-headers-generic

    
 Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)


 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

