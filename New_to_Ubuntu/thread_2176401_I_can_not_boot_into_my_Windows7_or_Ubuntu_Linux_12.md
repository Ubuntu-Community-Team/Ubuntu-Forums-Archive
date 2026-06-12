---
title: "I can not boot into my Windows7 or Ubuntu Linux 12.04.3, after deleting partitions."
date: 2013-09-24
forum: New to Ubuntu
---

### Post by richardn2 on 2013-09-24
Hi everyone,

    I'm very new to this Forum and begging for help with my problem.

First time trying to install Ubuntu Linux 12.04.3 to dual boot with my Windows7 64bit on an Asus K55A laptop.

After installing the Linux from Live CD, I didn't see dual-boot. It booted to windows7.

I changed the Booting order in the BIOS and booted to Ubuntu, used gparted to partition the Single hard disk with partitioned into two (System and Data). 

In the process, I've damaged both OS's (Windows7 & Ubuntu). Now I cann't boot into any of them.

Attached a snapshoot from the "Try Ubuntu"; I used gparted.

I used Testdisk as recommended in this Forum to recover the Partitions as shown on the attachment.
I've also use "Boot-Repair" as recommended here but still can not boot into Windows or Ubuntu.

Any help will be highly appreciated.

Richardn2

---

### Post by Jonathan Precise on 2013-09-24
(Since you have more than 4 partitions, and no extended partitions, I'm assuming you have a _**G**_[SIZE=1]uid[/SIZE] _**P**_[SIZE=1]artition[/SIZE] _**T**_[SIZE=1]able[/SIZE]) Do you have UEFI or BIOS?

UEFI: Make a fat32 partition 250-MB with a boot flag. (Windows might not be able to boot anymore :()
BIOS: Make an un-formatted partition 1-MB with a bios_grub flag (Windows might boot :))

If no change, please post here.

---

### Post by oldfred on 2013-09-24
Partitions as shown do not exactly make sense. Not typical UEFI nor BIOS install. Did you recover some extra partitions with testdisk?

Post link to BootInfo report from Boot-Repair. It may show more.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by jonathan_bravo2 on 2013-09-24
Man I just had this exact problem happen to me last night actually. And at first I was like OH snap I just F'd this computer up. But yeah samething I was messing with the partitions after I had the dual boot going. I had Win7 and Ubuntu 12.04.3 I think. Anyway I ended up deleting a partition off the space I left for Ubuntu because I wasn't 100% on keeping Win7. So anyway long story short all I ended up having to do was install Ubuntu from my jump drive (using my wifes laptop of course) because when my PC would start up all i would see was a black screen and it would say something about "gnome" or something like that. Anyway I just went to the BIOS and changed the boot from CD to USB as the sequence and then I plugged in my jump drive restarted my PC and boom that was it. Of course once I went through the installing process I just installed Ubuntu on my PC as the main OS. So yeah that's my story. Hope you can figure it out.

---

### Post by richardn2 on 2013-09-24
> **Jonathan Precise said:**
> (Since you have more than 4 partitions, and no extended partitions, I'm assuming you have a _**G**_[SIZE=1]uid[/SIZE] _**P**_[SIZE=1]artition[/SIZE] _**T**_[SIZE=1]able[/SIZE]) Do you have UEFI or BIOS?

UEFI: Make a fat32 partition 250-MB with a boot flag. (Windows might not be able to boot anymore :()
BIOS: Make an un-formatted partition 1-MB with a bios_grub flag (Windows might boot :))

If no change, please post here.



Thanks Jonathan,

I have UEFI; I'm sure that is why my Windows7 can't bot anymore.

You can see from the attachment all the Windows7 files still there from Recovery. I can't see the "Users Folder" where my documents and desktop are stored. How can I recover it?

Any suggestions?

---

### Post by richardn2 on 2013-09-25
Hi there,

PC boot the hard disk in Legacy boot.
Ubuntu installed in the Legacy Mode



I follow all the steps from the below link to fixed my PC but in the end it still can not boot boot into windows or ubuntu.

  [COLOR=#000080]_[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)_[/COLOR]

 

Attached are shoots I took as the repair process was going on.



After the URL, I clicked OK and rebooted the pc; went to the BIOS and changed the booting sequence to start from the Hard disk.

Below is the error messages I got:a


"Windows failed to start. A recent Hardware or Software change might be the cause".

"Status: 0xc0000225"

"Info: the boot selection failed because a required device is inaccessible".




I followed all the steps from this URL: [IMG]http://ubuntuforums.org/image/jpeg;base64,PCFET0NUWVBFIEhUTUwgUFVCTElDICItLy9XM0MvL0RURCBIVE1MIDQuMCBUcmFuc2l0aW9uYWwvL0VOIj4KPEhUTUw CjxIRUFEPgoJPE1FVEEgSFRUUC1FUVVJVj0iQ09OVEVOVC1UWVBFIiBDT05URU5UPSJ0ZXh0L2h0bWw7IGNoYXJzZXQ9dXRmLTgiPgoJPFRJVExFPjwvVElUTEU Cgk8TUVUQSBOQU1FPSJHRU5FUkFUT1IiIENPTlRFTlQ9IkxpYnJlT2ZmaWNlIDMuNSAgKExpbnV4KSI Cgk8U1RZTEUgVFlQRT0idGV4dC9jc3MiPgoJPCEtLQoJCUBwYWdlIHsgbWFyZ2luOiAwLjc5aW4gfQoJCVBSRSB7IGRpcmVjdGlvbjogbHRyOyBjb2xvcjogIzAwMDAwMDsgd2lkb3dzOiAwOyBvcnBoYW5zOiAwIH0KCQlQUkUud2VzdGVybiB7IHNvLWxhbmd1YWdlOiBlbi1VUyB9CgkJUFJFLmNqayB7IGZvbnQtZmFtaWx5OiAiV2VuUXVhbllpIE1pY3JvIEhlaSIsIG1vbm9zcGFjZTsgc28tbGFuZ3VhZ2U6IHpoLUNOIH0KCQlQUkUuY3RsIHsgZm9udC1mYW1pbHk6ICJMb2hpdCBIaW5kaSIsIG1vbm9zcGFjZTsgc28tbGFuZ3VhZ2U6IGhpLUlOIH0KCQlQIHsgbWFyZ2luLWJvdHRvbTogMC4wOGluOyBkaXJlY3Rpb246IGx0cjsgY29sb3I6ICMwMDAwMDA7IHdpZG93czogMDsgb3JwaGFuczogMCB9CgkJUC53ZXN0ZXJuIHsgZm9udC1mYW1pbHk6ICJMaWJlcmF0aW9uIFNlcmlmIiwgIlRpbWVzIE5ldyBSb21hbiIsIHNlcmlmOyBmb250LXNpemU6IDEycHQ7IHNvLWxhbmd1YWdlOiBlbi1VUyB9CgkJUC5jamsgeyBmb250LWZhbWlseTogIldlblF1YW5ZaSBNaWNybyBIZWkiOyBmb250LXNpemU6IDEycHQ7IHNvLWxhbmd1YWdlOiB6aC1DTiB9CgkJUC5jdGwgeyBmb250LWZhbWlseTogIkxvaGl0IEhpbmRpIjsgZm9udC1zaXplOiAxMnB0OyBzby1sYW5ndWFnZTogaGktSU4gfQoJCUE6bGluayB7IHNvLWxhbmd1YWdlOiB6eHggfQoJLS0 Cgk8L1NUWUxFPgo8L0hFQUQ CjxCT0RZIExBTkc9ImVuLVVTIiBURVhUPSIjMDAwMDAwIiBESVI9IkxUUiI CjxQUkUgQ0xBU1M9Indlc3Rlcm4iIFNUWUxFPSJtYXJnaW4tYm90dG9tOiAwLjJpbiI PEZPTlQgQ09MT1I9IiMwMDAwODAiPjxTUEFOIExBTkc9Inp4eCI PFU PEEgSFJFRj0iaHR0cHM6Ly9oZWxwLnVidW50dS5jb20vY29tbXVuaXR5L0Jvb3QtUmVwYWlyIj5odHRwczovL2hlbHAudWJ1bnR1LmNvbS9jb21tdW5pdHkvQm9vdC1SZXBhaXI8L0E PC9VPjwvU1BBTj48L0ZPTlQ PC9QUkU CjwvQk9EWT4KPC9IVE1MPgA=[/IMG]                         [SIZE=2][COLOR=#000080]_[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)_[/COLOR][/SIZE][SIZE=2].[/SIZE] 


[FONT=arial]Attached are also shoots I took during the process.

[/FONT][FONT=arial]What else am I missing?

[/FONT][FONT=arial]Plse help.

[/FONT][FONT=arial]Thanks for you time and attention.

[/FONT][FONT=arial]Richardn2[/FONT]

---

### Post by richardn2 on 2013-09-25
attachments

---

### Post by oldfred on 2013-09-25
Boot-Repair will not fix most Windows issues. It will add a Windows boot loader if required, but that is about all it can do. It may turn on chkdsk flag so Windows will run  chkdsk, but usually you need a Windows repairCD or flash drive to fix Windows.

Post the link (clickable link) to the BootInfo report that Boot-Repair creates so we can see details.

---

### Post by cmcanulty on 2013-09-25
put in windows dvd and boot from DVD then select repair option, and it may boot fine. Worked for me

---

### Post by Mark Phelps on 2013-09-25
Given that Win7 was on a laptop, I'm probably safe in presuming that the OP does NOT have a Win7 installation DVD, or Win7 Repair CD, right?

If that's true, you can purchase the ISO image needed to make a Win7 Repair CD from the following link: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Sorry, but you could have made this same disk for free when Win7 was working, before you installed Ubuntu.

---

### Post by richardn2 on 2013-09-26
> **oldfred said:**
> Partitions as shown do not exactly make sense. Not typical UEFI nor BIOS install. Did you recover some extra partitions with testdisk?

Post link to BootInfo report from Boot-Repair. It may show more.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)


Hi Oldfred,

I did recover all the partitions I created while trying out gparted and palimpsest with testdisk.

I just started trying my hands on Ubuntu Linux and ended up messing my system with the above two partitions tools.

---

### Post by richardn2 on 2013-09-26
> **cmcanulty said:**
> put in windows dvd and boot from DVD then select repair option, and it may boot fine. Worked for me


Sorry my Asus K55A did not came with the Recovery DVD,

---

### Post by richardn2 on 2013-09-26
> **jonathan_bravo2 said:**
> Man I just had this exact problem happen to me last night actually. And at first I was like OH snap I just F'd this computer up. But yeah samething I was messing with the partitions after I had the dual boot going. I had Win7 and Ubuntu 12.04.3 I think. Anyway I ended up deleting a partition off the space I left for Ubuntu because I wasn't 100% on keeping Win7. So anyway long story short all I ended up having to do was install Ubuntu from my jump drive (using my wifes laptop of course) because when my PC would start up all i would see was a black screen and it would say something about "gnome" or something like that. Anyway I just went to the BIOS and changed the boot from CD to USB as the sequence and then I plugged in my jump drive restarted my PC and boom that was it. Of course once I went through the installing process I just installed Ubuntu on my PC as the main OS. So yeah that's my story. Hope you can figure it out.

Thanks for your suggestion. 

How did you prepare your flash drive (USB) before downloading the Ubuntu 12.04.3 os image into it?

I've tried all the suggested solutions to resolve this issue, to no success.

Regards,

---

### Post by oldfred on 2013-09-26
Another Asus:
 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

Some similar ones that would only work in BIOS mode.
      
 Asus K55N just does not boot Ubuntu in UEFI mode. Some things to try, but no solution
[http://ubuntuforums.org/showthread.php?t=2137233](http://ubuntuforums.org/showthread.php?t=2137233)
Asus K55n will not boot in UEFI mode. Boot Parameters? Feb 2013
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)
ASUS-K55N is just not able to boot an EFI linux, converted to BIOS with MBR partitioning - UEFI Windows 7
[http://ubuntuforums.org/showthread.php?t=2061646&p=12635283#post12635283](http://ubuntuforums.org/showthread.php?t=2061646&p=12635283#post12635283)

---

### Post by richardn2 on 2013-09-28
> **oldfred said:**
> Another Asus:
 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

Some similar ones that would only work in BIOS mode.
      
 Asus K55N just does not boot Ubuntu in UEFI mode. Some things to try, but no solution
[http://ubuntuforums.org/showthread.php?t=2137233](http://ubuntuforums.org/showthread.php?t=2137233)
Asus K55n will not boot in UEFI mode. Boot Parameters? Feb 2013
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)
ASUS-K55N is just not able to boot an EFI linux, converted to BIOS with MBR partitioning - UEFI Windows 7
[http://ubuntuforums.org/showthread.php?t=2061646&p=12635283#post12635283](http://ubuntuforums.org/showthread.php?t=2061646&p=12635283#post12635283)


Thanks for your response and suggestions Oldfred. Much appreciated.

Nothing is working as I h[**[COLOR=#C61919][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711")ope. I'm still pondering on what to do next.

I'll get back if I find a solution.

---

### Post by oldfred on 2013-09-28
Have you updated UEFI/BIOS to latest version. Vendors also are making many fixes to their UEFI.

Some with very new systems find the beta 13.10 may work better. But it still is beta, may have breakage and if a consistent issue you should report a bug. But it will be released in Oct and has many kernel & driver updates.

---

### Post by richardn2 on 2013-09-29
> **oldfred said:**
> Have you updated UEFI/BIOS to latest version. Vendors also are making many fixes to their UEFI.

Some with very new systems find the beta 13.10 may work better. But it still is beta, may have breakage and if a consistent issue you should report a bug. But it will be released in Oct and has many kernel & driver updates.

No because I can not boot into either the Ubuntu I installed  alongside the Windows7 OS that was on the system.

I can only use the system now through the Live Ubuntu CD.

---

### Post by oldfred on 2013-09-29
Post the link that Boot-Repair gives.

---

