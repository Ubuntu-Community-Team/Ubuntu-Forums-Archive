---
title: "Need help with Grub"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Google Spider on 2008-04-22
Hi all,:)

 So I just installed fedora and now I'm not able to boot into Ubuntu. Probably grub is not recognizing Ubuntu partition.

I have 

[B]Windows XP on /dev/sda1
Fedora 8 on /dev/sda4 (previously this was occupied by mint)
Ubuntu on /dev/sda7  [/B]

When I was installing fedora it automatically recognized windows but not ubuntu. So I clicked 'Add' and added (Ubuntu on /dev/sda7)

Ubuntu appears on the Grub menu(the one which comes up and lets me select which OS to boot) but when I try to boot into it, it says(on a black screen):
> 
Booting 'Ubuntu'
rootnoverify(hd0,6)
chainloader +1
Error 13:Invalid or Unsupported executable format
Press any key to continue...

When I press a key it will go back to Grub menu.
I can boot fedora and windows fine.

I hope I've been able to present the problem clearly. Waiting for some elite replies now...

Thanks for your time reading this long post. Please suggest a possible solution.

---

### Post by hums07 on 2008-04-22
Probably you installed Ubuntu grub on MBR, now Fedora has written the MBR. Using Desktop CD, try to reinstall Ubuntu grub to the **respective partition** (e.g. (hd0,6))
```
sudo grub
root (hd0,6)
setup (hd0,6)  #not setup (hd0)
quit
```

Now restart. Sorry this is not an ellite reply, just 2 pence.

---

### Post by Google Spider on 2008-04-22
> **hums07 said:**
>  Using Desktop CD, try to reinstall Ubuntu grub to the 

What's a desktop CD? Do you mean the Live CD?
 Should I boot from the live cd and run these commands that's what you mean? (sorry I'm dumb)

> Sorry this is not an ellite reply, just 2 pence.

That's ellite for me :)

---

### Post by matey3 on 2008-04-22
i think its sudo -e grub?
not sure i am a newbie lol.. but i had similar problem before and usually the problem is that the grub doesnt read the right file. you have to find the name of the kernel file (you probably have more than 1, I have a few some start with vmlinuz and some xen since I run the xen..).in the /boot directory.

what I did was hit the e for edit the line of the menu.lst and then manually pointed to the files then hit b to boot from if it does not work I go to the next file and so on..

once you find out which file by hitting the e and b keys then you can edit the menu.lst later and point to the right file (permanently) ! the thing is since i am new at this i do not remember all those long linux file names so i write them down cuz u have to be exact.
In any case there are usually 3 item that menu boots from beside the title which means nothing.
the root which points to the right sector of the hard drive i.e hd0,2
the kernel which i mentioned
initrd which is a file in /boot and starts with initrd.img...


my 2 cents worth...2

---

### Post by Google Spider on 2008-04-22
> **hums07 said:**
> Probably you installed Ubuntu grub on MBR, now Fedora has written the MBR. Using Desktop CD, try to reinstall Ubuntu grub to the **respective partition** (e.g. (hd0,6))
```
sudo grub
root (hd0,6)
setup (hd0,6)  #not setup (hd0)
quit
```

Now restart. Sorry this is not an ellite reply, just 2 pence.

[COLOR="Blue"]Thanks! That fixed it.[/COLOR]\\:D/

**EDIT: Looks like that option to mark threads [solved] is not there.**

---

### Post by hums07 on 2008-04-22
> **Google Spider said:**
> 
**EDIT: Looks like that option to mark threads [solved] is not there.**

Yeah, this is a backward change. I used to view my previous posts from "Search" - "Find all your posts" to trace back what I have posted before. We dont have it now.

---

