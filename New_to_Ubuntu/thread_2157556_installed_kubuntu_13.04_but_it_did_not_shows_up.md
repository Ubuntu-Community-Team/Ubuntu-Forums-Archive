---
title: "installed kubuntu 13.04 but it did not shows up"
date: 2013-06-25
forum: New to Ubuntu
---

### Post by Sultan101 on 2013-06-25
[COLOR=#000000][FONT=sans-serif]hi [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]i have installed successfully[/FONT][/COLOR][COLOR=#FF0000][FONT=sans-serif] kubuntu-13.04-desktop-amd64[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif] and at the end i pressed restart now as it says then black screen asked me to remove the disc then press enter but at this point the system freezes and nothing happened. [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]so i had to press the restart button but the system goes directly to windows 7 and did not recognize kubuntu [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]what should i do ?? [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]------ [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]i have windows 7 x64 on c drive [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]16gb ram [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]1TB hdd ( 400gb c drive + 80gb kubuntu )[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]MB: GA-Z77X-D3H gigabyte[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]-------[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]P.S.[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]i have installed kubuntu and ubuntu on my old pc desktop with xp pro 2 years ago no problems[/FONT][/COLOR]

---

### Post by cincinnatus13 on 2013-06-25
Does GRUB even come up or does it go straight to Windows?
Boot repair might be the answer if so.

---

### Post by Sultan101 on 2013-06-25
system goes straight to windows 7 as if kubuntu  never existing.

please then tell me how to do a boot repair in few and specific steps?

---

### Post by cincinnatus13 on 2013-06-25
Check the boot repair thread in the Installation and Upgrades subforum. It has more info than I could ever give you (especially since I've never had to use it...yet.)

---

### Post by Sultan101 on 2013-06-25
i have read some threads there and got panic

 i am not an expert since it did not work out of the box then i am going to delete the 2 partitions (kubuntu + the swap are ) and forget all about linux 
 
but will this affects windows anyhow?

---------------------------------------- update ---------------

i just delete the 2 linux partitions  and joined them to c drive (thank god no problems at all )

[SIZE=1][COLOR=#DD4814][COLOR=#000000][cincinnatus13]("http://ubuntuforums.org/member.php?u=499792")       [/COLOR][/COLOR][/SIZE]thak you for quick replies

---

### Post by cincinnatus13 on 2013-06-26
With Windows 7 (assuming you don't have a UEFI BIOS), there shouldn't be much of an issue with installing Kubuntu.

I would recommend trying again but first, check the MD5 of the ISO before putting it on a USB/CD. Then check it for defects before installing.
If you need help, post back.

---

### Post by Sultan101 on 2013-06-27
this is my MB : GA-Z77X-D3H gigabyte and and it has a UEFI Bois.

I did little search on UEFI and linux to find out that the reason of linux not booting is the UEFI.

right now the only linux [COLOR=#000000][FONT=sans-serif]distributions[/FONT][/COLOR] support the UEFI are : [COLOR=#0000cd]Fedora 18 , Ubuntu 12.10 and  OpenSuse 

[/COLOR][COLOR=#000000]i hope you verify my info[/COLOR][COLOR=#0000cd][/COLOR]

---

### Post by deadflowr on 2013-06-27
First try [boot repair]("https://help.ubuntu.com/community/Boot-Repair").
Follow the instructions, there very straight forward.
Option #2 works best, IMHO.

And second, I think you're confusing UEFI with secure boot.
Look over oldfred's UEFI installing tips tutorial for more on the issue

[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

