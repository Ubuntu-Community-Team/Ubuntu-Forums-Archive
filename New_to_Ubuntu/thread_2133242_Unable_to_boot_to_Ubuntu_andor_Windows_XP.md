---
title: "Unable to boot to Ubuntu and/or Windows XP"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by astrophunq on 2013-04-07
Hello everyone!

Complete newbie here! I'm attempting to install a triple boot on an old computer with a 550+ mhz VIA Samuel C2 processor with 480mb of RAM. It had Windows XP installed on it already, so the next step was to install Ubuntu. I installed Ubuntu 10.04 and it all went smoothly. However, when I attempted to boot to Windows XP, I got the black screen with the blinking cursor. I started googling around and it said that I needed to delete the boot.ini, ntldr and ntdetect.com, which already seems to me like the worse idea ever. I proceeded to attempt to fix the windows installation by running the repair option on the windows XP installation CD. When I did that, it messed up GRUB. So I attempted to fix it as well. I googled and got some directions on how to do it. I followed the directions to the T, and attempted to boot again. When I did, what I got was the GRUB editor screen.

At this point, I don't know what to do. I'm contemplating on formatting the hard drive and starting from scratch. I'm really looking for other options, namely, not having to format the hard drive and being able to fix GRUB so that I can use both operating systems.

Any assistance/advice/ideas are welcomed. I thank you all in advanced for your time.

---

### Post by oldos2er on 2013-04-07
Try [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Ubuntu 10.04 desktop version will reach its end-of-life soon, which means it will no longer receive updates. You might want to look into installing Xubuntu or Lubuntu versions 12.04 or newer; they have smaller RAM requirements than Ubuntu.

---

### Post by slooksterpsv on 2013-04-07
Yeah never delete boot.ini, ntldr, or ntdetect.com - those are required to boot into Windows. With that, you may need to restore them from your XP CD; with Ubuntu, if grub crashed, you can reinstall Ubuntu over the top of itself and it should fix the grub issue. If it were me personally, I'd probably just remove Windows and just install Xubuntu or Lubuntu (memory requirements).

---

### Post by -@23%^yu* on 2013-04-07
try easyBCD it must help to manage multiple boot options [http://neosmart.net/EasyBCD]("http://neosmart.net/EasyBCD/")

---

### Post by astrophunq on 2013-04-08
Thank you for your prompt responses.

I'd like to point out that the version that I installed in the old computer is Ubuntu 10.04 (LinuxCNC version). I think the proper course of action in this case would be for me to format the entire drive and start from scratch again. I'm not sure if anyone could provide another solution to this particular problem. If so, I'd appreciate it.

---

### Post by Mark Phelps on 2013-04-08
> **abdieltatpati said:**
> try easyBCD it must help to manage multiple boot options [http://neosmart.net/EasyBCD]("http://neosmart.net/EasyBCD/")
EasyBCD only works with Vista and newer -- as those actually have BCDs.

---

### Post by astrophunq on 2013-04-11
I ran Boot-Repair, and that helped me boot up Ubuntu. So I'm kinda back to square one, which was the fact that I wasn't able to boot up Windows XP in the first place. I ran the Boot-Repair script and that generated a file.

Please check it out, and if possible, provide me with ideas on how to get this to work. 


[LIST=|INDENT=1]
[*][FONT=inherit] Boot Info Script 0.61.full + Boot-Repair extra info      [COLOR=#666666][FONT=inherit][[/FONT][/COLOR]Boot-Info November 20th 2012[COLOR=#666666][FONT=inherit]][/FONT][/COLOR][/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit][COLOR=#666666][FONT=inherit]=============================[/FONT][/COLOR] Boot Info Summary: [COLOR=#666666][FONT=inherit]===============================[/FONT][/COLOR][/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit] [COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]> Windows is installed in the MBR of /dev/sda.[/FONT]

[*][FONT=inherit] [COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]> Syslinux MBR [COLOR=#666666][FONT=inherit]([/FONT][/COLOR]3.61-4.03[COLOR=#666666][FONT=inherit])[/FONT][/COLOR] is installed in the MBR of /dev/sdb.[/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit]sda1: __________________________________________________________________________[/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit]    File system:       ntfs[/FONT]

[*][FONT=inherit]    Boot sector [COLOR=#008000][FONT=inherit]type[/FONT][/COLOR]:  Windows XP: NTFS[/FONT]

[*][FONT=inherit]    Boot sector info:  No errors found in the Boot Parameter Block.[/FONT]

[*][FONT=inherit]    Operating System:  Windows XP[/FONT]

[*][FONT=inherit]    Boot files:        /boot.ini /ntldr /NTDETECT.COM /ntdetect.com[/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit]sda2: __________________________________________________________________________[/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit]    File system:       Extended Partition[/FONT]

[*][FONT=inherit]    Boot sector [COLOR=#008000][FONT=inherit]type[/FONT][/COLOR]:  Unknown[/FONT]

[*][FONT=inherit]    Boot sector info: [/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit]sda5: __________________________________________________________________________[/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit]    File system:       ext4[/FONT]

[*][FONT=inherit]    Boot sector [COLOR=#008000][FONT=inherit]type[/FONT][/COLOR]:  -[/FONT]

[*][FONT=inherit]    Boot sector info: [/FONT]

[*][FONT=inherit]    Operating System:  Ubuntu 10.04.4 LTS[/FONT]

[*][FONT=inherit]    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img[/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit]sda6: __________________________________________________________________________[/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit]    File system:       swap[/FONT]

[*][FONT=inherit]    Boot sector [COLOR=#008000][FONT=inherit]type[/FONT][/COLOR]:  -[/FONT]

[*][FONT=inherit]    Boot sector info: [/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit]sdb1: __________________________________________________________________________[/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit]    File system:       vfat[/FONT]

[*][FONT=inherit]    Boot sector [COLOR=#008000][FONT=inherit]type[/FONT][/COLOR]:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E[COLOR=#666666][FONT=inherit]}[/FONT][/COLOR].u......[/FONT]

[*][FONT=inherit]    Boot sector info:  Syslinux looks at sector 751048 of /dev/sdb1 [COLOR=#008000][FONT=inherit]**for **[/FONT][/COLOR]its [/FONT]

[*][FONT=inherit]                       second stage. SYSLINUX is installed in the  directory. [/FONT]

[*][FONT=inherit]                       No errors found in the Boot Parameter Block.[/FONT]

[*][FONT=inherit]    Operating System:  [/FONT]

[*][FONT=inherit]    Boot files:        /syslinux.cfg /ldlinux.sys[/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit]sdb2: __________________________________________________________________________[/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit]    File system:       [/FONT]

[*][FONT=inherit]    Boot sector [COLOR=#008000][FONT=inherit]type[/FONT][/COLOR]:  Unknown[/FONT]

[*][FONT=inherit]    Boot sector info: [/FONT]

[*][FONT=inherit]    Mounting failed:   mount: unknown filesystem [COLOR=#008000][FONT=inherit]type[/FONT][/COLOR] [COLOR=#BA2121][FONT=inherit]''[/FONT][/COLOR][/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit][COLOR=#666666][FONT=inherit]============================[/FONT][/COLOR] Drive/Partition Info: [COLOR=#666666][FONT=inherit]=============================[/FONT][/COLOR][/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit]Drive: sda _____________________________________________________________________[/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit]Disk /dev/sda: 41.1 GB, 41110142976 bytes[/FONT]

[*][FONT=inherit]255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors[/FONT]

[*][FONT=inherit][COLOR=#19177C][FONT=inherit]Units[/FONT][/COLOR] [COLOR=#666666][FONT=inherit]=[/FONT][/COLOR] sectors of 1 * [COLOR=#19177C][FONT=inherit]512[/FONT][/COLOR] [COLOR=#666666][FONT=inherit]=[/FONT][/COLOR] 512 bytes[/FONT]

[*][FONT=inherit]Sector size [COLOR=#666666][FONT=inherit]([/FONT][/COLOR]logical/physical[COLOR=#666666][FONT=inherit])[/FONT][/COLOR]: 512 bytes / 512 bytes[/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit]Partition  Boot  Start Sector    End Sector  [COLOR=#408080][FONT=inherit]*# of Sectors  Id System*[/FONT][/COLOR][/FONT]

[*][FONT=inherit][/FONT]

[*][FONT=inherit]/dev/sda1    *             63    46,866,495    46,866,433   7 NTFS / exFAT / HPFS[/FONT]

[*][FONT=inherit]/dev/sda2          46,868,478    80,291,839    33,423,362   5 Extended[/FONT]

[*][FONT=inherit]/dev/sda5          46,868,480    78,800,895    31,932,416  83 Linux[/FONT]

[*][FONT=inherit]/dev/sda6          78,802,944    80,291,839     1,488,896  82 Linux swap / Solaris[/FONT]



[*]
[/LIST]

---

