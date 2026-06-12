---
title: "WUBI Upgrade from 11.04 - Can't get past GRUB?"
date: 2011-09-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by treasonvoice on 2011-09-26
Hi guys. Seeing as you lot are by far the most tolerant and friendly of forum dwellers, maybe you can help me out.

I updated to Beta 2 of Oneiric on a spare PC. It's an oldish rig... Pentium 4, 3 Gigs of RAM with a Geforce FX 5500 or something. It's definitely capable of at least Unity 2D, right? If it could handle KDE in 11.04, it should handle Unity 2D 11.10.

Anyway, the issue is this. As soon as I select the latest Linux Kernel at GRUB (3.0.0.11.12), the screen remains purple. The text goes away, but it remains purple. Forever.

I tried to get around this by selecting an older kernel version, and it worked. Perfectly. So what do I have to do in order to get the latest kernel to work?

I'll supply as much info as I can.

Thanks for reading my superlong message. Sorry if it has already been dealt with before.

---

### Post by lucazade on 2011-09-26
Try to launch both kernels without "quiet splash" arguments in order to see verbose messages. 
When you are in grub press 'e' to edit the current kernel entry, remove those 2 arguments and start system with ctrl+x.
let us know what you get.

---

### Post by effenberg0x0 on 2011-09-26
**EDIT**: Test lucazade suggestion first, as it is far less likely to give you problems than the things I suggested below.

Hey,

> Anyway, the issue is this. As soon as I select the latest Linux Kernel  at GRUB (3.0.0.11.12), the screen remains purple. The text goes away,  but it remains purple. Forever.

I tried to get around this by selecting an older kernel version, and it  worked. Perfectly. So what do I have to do in order to get the latest  kernel to work?- Using "e" at GRUB, do you see different kernel options by the end of each kernel command-line? What are the options there for the working and not working kernel?

- I don't know if you're seeing the purple screen and your system is loading or not behind it (on the "not-working" kernel). Can you switch to a VT (ctrl+alt+F1 to F6)? If you do, do you see any specific error message that could give us a lead? Do you get to a login prompt? If you have the ability to login and networking is working OK, we should proceed to uninstall/reinstall ATI and fully update/upgrade your system. This would be the better option.

- There have been reports that, using ATI VGA, one could get rid of this  purple screen problem by using "e" to edit the kernel line at the  latest GRUB kernel entry and adding the following: nomodeset. I don't know what side-effects that can cause on the system video thou.

- If you can login somehow using the good/working kernel version or if you can use a LiveCD/LiveUSB to mount /dev/sda, please run sudo nano /etc/default/grub, from a command-line, and post its content here. There are some reports of a problem similar to your, in which removing the comment from the "GRUB_TERMINAL=console" line was mentioned as a solution. 

- If it comes to a fresh reinstall, you can use the F4 key to select advanced install options. If you  press TAB you will see some of these options. I know that --xforcevesa  will give you a more reliable VESA mode during install, which works more reliably for everyone. Then once the system is up you can update / upgrade and install proper ATI VGA  drivers.

These are some options. Let us know.

Regards,
Effenberg

---

### Post by treasonvoice on 2011-09-28
Ok. I'm going to try this out today, and I'll let you know as soon as possible. Will try Lucozade's solution first.

Thanks for the help guys.

---

### Post by treasonvoice on 2011-09-28
Ok, so i'm in GRUB, i've pushed e on each of the linux versions... with version 3 i've deleted the small bit of text which said quiet splash etc. and it changed nothing. Trying the 4th method that effenberg suggested, which was deleting GRUB_TERMINAL = console line from grub

edit: There is also no difference between the kernel options

---

### Post by lucazade on 2011-09-28
don't you see any obvious error or warning when you remove those params with the new kernel? does the screen still remain purple and doesn't go on?

---

### Post by treasonvoice on 2011-09-28
Nope. No changes. Editing the parameters in GRUB did nothing whatsoever, and the GRUB_TERMINAL de-commenting only made things black. Which is expected. But nothing further. So next step is to try your other options, especially the nomodeset thing. Where do i need to insert that? At the end of the list of Command line options?

I see that a new linux kernel is out. Going to try that. hold thumbs


Edit:

OK. News. I updated to the latest kernel version (3.0.0-12). I removed the quiet splash parameter. Then I pushed ctrl-x. It quickly went through a list of things, but it stopped with the line [0.329721] [<c1533b7e>] ? kernel_thread_helper+0x6/0x10

After that, it's just a flashing cursor.

What now?

---

### Post by treasonvoice on 2011-09-28
Problem solved. It was an ACPI issue.

I followed the advice at [http://www.absolutelytech.com/2010/11/10/solved-kernel_thread_helper0x70x10-during-ubuntu-boot-process/](http://www.absolutelytech.com/2010/11/10/solved-kernel_thread_helper0x70x10-during-ubuntu-boot-process/)

Thanks for the help anyway, to both of you. It got me to the right point eventually.

---

