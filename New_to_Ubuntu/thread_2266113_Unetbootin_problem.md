---
title: "Unetbootin problem"
date: 2015-02-19
forum: New to Ubuntu
---

### Post by Vitor_Leal on 2015-02-19
Hello people.

I installed Windows 7 so much time before, and now I installed Ubuntu with Unetbootin without erase my Windows 7 file.

For this, i created new partition in Windows 7 and called the partition as a Local Disk E and installed Ubuntu files in this disk.

But now, the problem is: I can go to Ubuntu but i don't can go back to my Windows 7.

In the Unetbootin menu doesn't show the Windows 7 option, only the: Install Ubuntu.

I tryed Default option, but goes to Ubuntu.

I tryed boot from first hard drive, but show so much letter that i don't understand.

How can I disable Unetbootin?

How can i back to Windows 7 without CD? Can I reinstall with USB?

Thanks!

---

### Post by sudodus on 2015-02-20
Welcome to the Ubuntu Forums :-)

Unetbootin is a tool, that is normally used to make a USB pendrive bootable with Ubuntu or another linux distro.

Booting from that USB pendrive it is possible to run a live session, to 'Try Ubuntu' without installing anything. It is also possible (when booted from that USB pendrive) to install Ubuntu into an internal drive or another external drive.

It is not clear to me, what you have actually done.

- Have you installed Ubuntu into the internal drive?

- In that case, can you boot Ubuntu from the internal drive?
- Can you still boot into Windows from the internal drive (when you remove the USB pendrive)?

Please have a look at the following links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

Do you know if your computer boots in UEFI or the old BIOS (alias CSM) mode? There is a good wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and a good tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295").

---

### Post by nerdtron on 2015-02-20
Did you remove your CD or USB drive after the installation?

---

### Post by Vitor_Leal on 2015-02-20
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

Unetbootin is a tool, that is normally used to make a USB pendrive bootable with Ubuntu or another linux distro.

Booting from that USB pendrive it is possible to run a live session, to 'Try Ubuntu' without installing anything. It is also possible (when booted from that USB pendrive) to install Ubuntu into an internal drive or another external drive.

It is not clear to me, what you have actually done.

- Have you installed Ubuntu into the internal drive?

- In that case, can you boot Ubuntu from the internal drive?
- Can you still boot into Windows from the internal drive (when you remove the USB pendrive)?

Please have a look at the following links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

Do you know if your computer boots in UEFI or the old BIOS (alias CSM) mode? There is a good wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and a good tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295").

> **nerdtron said:**
> Did you remove your CD or USB drive after the installation?

I installed my Ubuntu on a disk drive that I created. When I was with Unetbootin in Windows 7, i choosed USB and clicked in Show All Drives and selected the disk drive, but the disk drive is not a USB, this is the problem?

I don`t have any pendrive in my computer.

I think it`s I`ve done ****, but now I can`t resolve... =(


Backing to Ubuntu, yes, I tryed Ubuntu without installation. I`m here with this, because when I try to install Ubuntu in the side of Windows 7, stucks on Detecting system archives...

---

### Post by Vitor_Leal on 2015-02-20
Oh yes, thank you **sudodus**, the problem has been resolved.

I used Boot-Repair and selected Windows 7 loader, thank you man, you saved my day(I can't stay one day without PC).

Have a good day!

---

### Post by sudodus on 2015-02-20
I'm glad you found a solution :KS

Are you happy with your system now?

If you are, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

Otherwise we can continue the conversation in this thread until you have solved your problems, or if the problem is very different from what is described in the title, you can start a new thread with a good descriptive title. In that case you can post a link to that new thread here.

---

