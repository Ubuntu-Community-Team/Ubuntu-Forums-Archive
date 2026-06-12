---
title: "Is it illegal to download Xubuntu from a pirated Windows operating system?"
date: 2020-08-20
forum: New to Ubuntu
---

### Post by johnvs99 on 2020-08-20
Hi! The question is because I downloaded Xubuntu from a PC with an operating system that I am not sure if it is properly activated, I made my USB bootable with Xubuntu and then installed it on another computer. So I want to know if this makes Xubuntu illegal on my PC on or something like that. Beforehand thank you very much.

---

### Post by poorguy on 2020-08-20
No it doesn't make your Xubuntu illegal.

Linux is free to download and install on as many computers as you like.

---

### Post by sudodus on 2020-08-20
> **poorguy said:**
> No it doesn't make your Xubuntu illegal.

Linux is free to download and install on as many computers as you like.

+1

If you want to be sure, that your Xubuntu is good (correctly downloaded and free from malware), you should [download the iso file and] check it with [FONT=Courier New]**md5sum**[/FONT] (older versions) or [FONT=Courier New]**sha256sum**[/FONT] (new versions) from the official website.

Standard Ubuntu and the Ubuntu flavours (Kubuntu, Lubuntu ... Xubuntu) can be found via the following link

[releases.ubuntu.com/](https://releases.ubuntu.com/)

Now (August 2020) I would recommend [FONT=Courier New]**xubuntu-20.04.1-desktop-amd64.iso**[/FONT].

```

$ sha256sum xubuntu-20.04.1-desktop-amd64.iso
4a8190b11f97a0ed67932ac4fcf5280107d31db6a6c5d4b4542889fc94ec8031  xubuntu-20.04.1-desktop-amd64.iso

$ sha256sum -c SHA256SUMS
xubuntu-20.04-desktop-amd64.iso: OK
xubuntu-20.04.1-desktop-amd64.iso: OK

```

---

### Post by grahammechanical on 2020-08-20
If it makes you feel better you could always make a donation.

[https://xubuntu.org/donations/](https://xubuntu.org/donations/)

As a user you could contribute by getting involved in the Xubuntu project

[https://xubuntu.org/contribute/](https://xubuntu.org/contribute/)

Every new release has to be tested by someone before it is released. With Linux users are the testers and we all can report bugs. Some of us dual boot a released and supported version of our flavour of Ubuntu with the development version that is on a 26 week development schedule. 

[https://docs.xubuntu.org/contributors/release-cycle-testing.html](https://docs.xubuntu.org/contributors/release-cycle-testing.html)

And of course, making posts on this forum is a way of giving something back to the community that has given us a varied and professional computer operating system.

Regards.

---

### Post by johnvs99 on 2020-08-20
Thank you very much for your answer, I needed to confirm.

---

### Post by johnvs99 on 2020-08-20
Thank you very much for your answer, I think I will

---

### Post by johnvs99 on 2020-08-20
I would like to make a donation, I think at some point I probably will.

---

### Post by sabirsaleem90 on 2021-08-03
[COLOR=#000000]Hi[/COLOR]

[COLOR=#000000]My question is that I was using Pirated version of windows 7 which I do not know so I migrated to Linux OS now from installing .ISO File and made usb bootable via refus the thing is I migrated to Linux via windows 7 pirated version so most of the people says using pirated versions may have maleware and viruses and it automatically save in files and folders so iso file also infected or installing Linux from pirated version is also something illegal for not virus free....[/COLOR]

[COLOR=#000000]it is very confusing can someone please answer and help[/COLOR]

[COLOR=#000000]Thank you[/COLOR]

---

### Post by sabirsaleem90 on 2021-08-03
See my thread here

[https://ubuntuforums.org/showthread.php?t=2465498&p=14051681#post14051681](https://ubuntuforums.org/showthread.php?t=2465498&p=14051681#post14051681)

---

### Post by sabirsaleem90 on 2021-08-03
Because I have many work about 3 Years of work which I need to copy from windows pirated version can I use that files in Linux OS or that files contains any maleware viruses ?

Answer will be highly appreciate.

---

### Post by yancek on 2021-08-04
Using a 'pirated' version of windows is illegal and I would not be posting threads indicating I had done that (too late now).

THe iso you downloaded is a read only filesystem (iso9660) and you can't get viruses or malware on it so downloading the Linux iso would not be a problem. You do need to download from the official Lubuntu site and do an md5 checksum on it.
.

If you want to copy windows files from your other windows system, create a separate partition with  an ntfs filesystem partition on the computer where you install Linux.  Linux has it's own filesystems and windows default can't read them but ntfs filesystem files can be read and written to from Linux.  If you are worried about viruses from windows, there are virus scanner you can run on Linux to detect windows viruses and malware. 

"Viruses" for windows are executable files which do something the user does not intend and executable files from windows will not run on Linux.  Malware, I don't know depends upon what it is.

---

### Post by coffeecat on 2021-08-04
Necromanced and hijacked old thread closed.

---

