---
title: "Quick question on boot loader install"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by onthefence on 2008-11-03
I had a windows laptop crash at work. So I am installing ubuntu (with alternate cd) on a separate partition to recover some files that were not backed up.  FYI, i've tried using the Live CD but get errors, and i've also tried installing to a USB drive, but the computer is so old, it does not give the option to boot from USB. the install went smoothly except for the fact that I'm getting an error on the GRUB install. see image:
[IMG]http://jeannewolfshollywood.com/forumimages/grub_install_error.jpg[/IMG]

for those who are very familiar with this installer, you already know what the various options are. i have not tried to install lilo ever so do not know what the best way to proceed is.

question: if i install lilo on the new ubuntu partition, will the computer recognize that upon restart, or does it require additional configuration of the master boot record? If it does, can someone please explain how?

Just to recap i do not care if i ruin the MBR, because all i need to do is recover some of the files from the ntfs partition once inside ubuntu.

Any help is appreciated, thanks.

---

### Post by caljohnsmith on 2008-11-03
Did the install fail at about 94% completion with that Grub error? If so, that is unfortunately a known bug, but fortunately at least a few workarounds exist. Try this and see if it works for you:

[http://ubuntuforums.org/showthread.php?t=893156](http://ubuntuforums.org/showthread.php?t=893156)

Let me know if that solves your problem.

---

### Post by onthefence on 2008-11-03
> **caljohnsmith said:**
> Did the install fail at about 94% completion with that Grub error? If so, that is unfortunately a known bug, but fortunately at least a few workarounds exist. Try this and see if it works for you:

[http://ubuntuforums.org/showthread.php?t=893156](http://ubuntuforums.org/showthread.php?t=893156)

Let me know if that solves your problem.

Thanks a lot.

I must admit i was doing a few things while installing, so i can only say that i know it was past the 90% mark, but i believe it is what you are suggesting, if that is a known bug. Strange thing is that i chose ext2 to format the ubuntu partition.

i just tried putting LILO on the MBR, but that didn't work either.

Are there any other workarounds? I've heard of putting GRUB on a CD and using it to boot from like a Live boot manager.

---

### Post by caljohnsmith on 2008-11-03
I'm not familiar with the alternate CD installer, but does it actually give you a choice to install Lilo, or do you mean manually installing Lilo after the installation is done? If it is the latter case, I would suggest installing Ubuntu without a boot loader at all, and then if you want, I can help you manually install Grub afterwards if the installation completes successfully. But if the alternate CD does give you the option to use Lilo, I would go for that. :)

---

### Post by onthefence on 2008-11-03
i'm still in the install wizard. it does offer you a couple boot laoder options, grub doesn't work at all and my options for lilo are to install to:
1. MBR - already tried, not working
2. my new ubuntu install partition - i'm not sure how to do this correctly
3. other (advanced) - you get to choose the path.

Or, I can choose to "continue without boot loader" or "finish the installation". 
[There are many other options in this menu, like detect disks, partition disks, configure the clock, etc. , but none of them seem to apply to the boot loader problem.]

---

### Post by caljohnsmith on 2008-11-03
Try the second option you listed, and see if Lilo will install to the boot sector of the Ubuntu partition. If it asks you which partition, just specify the Ubuntu partition. And if that doesn't work, I would try the "continue without boot loader" option.

---

### Post by onthefence on 2008-11-03
sorry, accidental double post, read below...

---

### Post by onthefence on 2008-11-03
ok, so none of the lilo options worked either.

so, i chose to continue without boot loader.

the installation says it was successful, but now i get an "error loading operating system" message on bot up. this makes sense, but where do i go from here?

---

### Post by caljohnsmith on 2008-11-03
Does the alternate CD have a bash command line that you can go to in order to run commands? When you said the Live CD gave errors, can you at least boot into it and pull up a terminal (Applications > Accessories > Terminal)? The only way I know of to install Grub afterwards is through the command line, so sorry I forgot to mention that sooner. If you can get a command line, please first post:
```
sudo fdisk -lu
```
And also let me know if you have an internet connection while using the command line.

---

### Post by onthefence on 2008-11-03
here's where my ignorance of linux is really exposed.
i was able to get to the main menu for the Live CD, but i didn't see an option for command line, so pressed F6 for other options, then hit escape to get out, the system then asked if i wanted to leave the graphical user interface and enter text-mode. now i have a prompt that says "boot:". Is that a bash prompt?

---

### Post by caljohnsmith on 2008-11-03
> **onthefence said:**
> here's where my ignorance of linux is really exposed.
i was able to get to the main menu for the Live CD, but i didn't see an option for command line, so pressed F6 for other options, then hit escape to get out, the system then asked if i wanted to leave the graphical user interface and enter text-mode. now i have a prompt that says "boot:". Is that a bash prompt?
The "boot:" prompt isn't quite what we're looking for. The typical bash prompt on the Live CD will look like:
```
ubuntu@ubuntu:~$ 
```
Or if you somehow get a root (superuser) bash prompt, it will look like:
```
ubuntu@ubuntu:~#
```
When you boot the Live CD, try the first option in the menu that says something like "try Ubuntu without making any changes to your computer". Hopefully that will boot you into the Ubuntu desktop, and then you can open a terminal from the menu Applications > Accessories > Terminal. Give that a shot and let me know how it goes. :)

---

### Post by onthefence on 2008-11-03
okay, so when i try to boot into the live cd is when i get the error, so that option doesn't work. if there is a way to get to the command prompt from the main menu, that should work.

alternatively, here is the message i received after installation:
[IMG]http://jeannewolfshollywood.com/forumimages/boot_manual_info.jpg[/IMG]

it seems that i may be able to enter the path to the linux kernel from this "bott:" prompt. 
i tried entering: /dev/sda2/vmlinuz
but i get a message: "Could not find the kernel image: /dev/sda2/vmlinuz"

can you help me on this path, or are we out of ideas?

thanks

---

### Post by caljohnsmith on 2008-11-03
Unfortunately I don't think that "boot:" prompt is going to help you. I'm thinking that maybe your best option would be to simply download some other Live CDs, such as earlier Ubuntu versions, maybe Fluxbuntu (it's lighter on resources), or even other distros. If one of them boots just fine, it will save trying to figure out how to get your present Live CD to work. Does that maybe sound like an option you could consider?

---

### Post by onthefence on 2008-11-03
sorry for the delay,
i tried replying but it seems the servers were down.
i've since installed windows again and am in the process of recovering the files. 
i was trying to convince the individual i was helping to switch to linux on this machine. but for obvious reasons, that is not going to happen.

again,
thanks a ton for troubleshooting caljohnsmith.

---

### Post by ptsubin on 2008-11-11
I also have the same problem. I managed to get around without a boot loader and added the entry to my LinuxMint bootloader. But what i am missing is the initrd for 2.6.27 kernel. The one i copied from /casper in live cd doesnt give me a high resolution splash screen. Is there any way to make an initrd image like compiling the kernel with makemenuconfig? Can any one give me the right command?

---

