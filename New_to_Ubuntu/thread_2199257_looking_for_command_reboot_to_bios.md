---
title: "looking for command: reboot to bios"
date: 2014-01-13
forum: New to Ubuntu
---

### Post by sunil_ic on 2014-01-13
I have install Ubuntu server 12.04 in my Samsung Ultrabook series 5. I have some problem with my laptop and not able to go to bios setting by pressing any keys: F2, F10, F12, Del, F etc... Please don't give suggestion to go to bios setting with this option. 
I am looking for command in Ubuntu such that my laptop reboot to bios setting directly. without pressing any keys. Thanks.

---

### Post by claracc on 2014-01-13
As far as I know, there is not such a linux command to enter into BIOS.

There are combination keys given by computer manufacturer in order to enter into BIOS.

Here, [http://www.pendrivelinux.com/how-to-access-bios/](http://www.pendrivelinux.com/how-to-access-bios/) there are some of them, you will be to look for the specific key combination given by samsung for your laptop: [http://linux.seindal.dk/2013/03/31/samsung-series-5-ultrabook-np530u3c-a08it-debian-wheezy-installation/](http://linux.seindal.dk/2013/03/31/samsung-series-5-ultrabook-np530u3c-a08it-debian-wheezy-installation/)

---

### Post by fantasyleague0629 on 2014-01-13
IMO it has nothing to do with Ubuntu itself.

---

### Post by sunil_ic on 2014-01-13
I have windows 8 installed and I was able to boot with bios setting by just using some option in Windows 8. If Windows 8 can configure the boot directly to bios, then I was guessing Ubuntu may have similar procedure.

---

### Post by Topsiho on 2014-01-13
Maybe you can do an "apropos bios" (without the quotes), in the terminal, and see what commands pertinent to the BIOS exist on your computer.
On my computer (not a laptop, not a Toshiba) apparently exists

toshset (1)          - manipulate bios and hardware settings of Toshiba laptops

If you are lucky, you may have luck, who knows :)

Topsiho

---

### Post by sunil_ic on 2014-01-13
Topsiho, thanks for help. this is what I got when type "apropos bios"
[I]
biosdecode (8)       - BIOS information decoder
check-bios-nx (1)    - determine if BIOS has blocked CPU's NX capabilities
intel_bios_dumper (1) - Saves the Intel video BIOS contents to a file.
intel_bios_reader (1) - Parses an Intel BIOS and displays many of its tables
lmhosts (5)          - The Samba NetBIOS hosts file
nmbd (8)             - NetBIOS name server to provide NetBIOS over IP naming ...
nmblookup (1)        - NetBIOS over TCP/IP client used to lookup NetBIOS names
nmblookup.samba3 (1) - NetBIOS over TCP/IP client used to lookup NetBIOS names
toshset (1)          - manipulate bios and hardware settings of Toshiba laptops
vbetool (1)          - run real-mode video BIOS code to alter hardware state[/I]

next what should I do ? I am really beginner. :)

---

### Post by Topsiho on 2014-01-13
This is what I get, too. So I guess there is no luck here...

I never (for what that is worth) have seen a computer in which could not enter the BIOS somehow. Sometimes you have to press the right button at exactly the right time, or you are too late or too fast. Some perseverance helps here. *** Knowing *** which button to press helps in such a case. You can find that in the manual, the manual of the mother board, or so. If you don't have the manual of the mother board, you might try and find this on the internet (google, or duckduckgo or so). You must know what mother board you have then. One possibility is opening up your computer and try and find the name somewhere on this board, you also might try what (in a terminal) you get when you do "sudo lshw | less" (without quotes), and try and find line(s) with Mother board (or Motherboard) in it. In one computer I have I could thus find the name of the mother board (and what buttons to press), on this computer I use now i can't.

You can also (opening up a laptop is not advisable if you don't know exactly what you are doing) google (duckduckgo) on the computer's name and see what info you get. But: you have a computer manual, don't you?

Other than this, I am afraid i can not help you.

Topsiho

---

### Post by Topsiho on 2014-01-13
I found (I think) the manual you need on [http://www.samsung.com/uk/support/model/NP530U3B-A01UK-downloads#](http://www.samsung.com/uk/support/model/NP530U3B-A01UK-downloads#),

In it, it says:

1 Turn the computer on.
Immediately press the F2 key several times.

2 After a moment, the BIOS setup screen appears.
The items in the BIOS setup may differ depending on the
product.

So, that must help you :)

Topsiho

---

### Post by sunil_ic on 2014-01-14
All, Thanks for reply. Finally I went to Samsung service center and he re-install the bios. Now F2 and all other bios related keys are working :)
But Still my question is, can we enter into bios setting without pressing any keys ? Like Windows 8 has some setting such that the computer restart directly to bios setting.

---

### Post by oldfred on 2014-01-15
Do you have UEFI and this entry in grub menu? That should boot into UEFI.

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
	fwsetup
}

---

