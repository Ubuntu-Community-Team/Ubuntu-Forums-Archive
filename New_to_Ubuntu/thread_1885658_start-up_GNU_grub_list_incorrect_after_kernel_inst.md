---
title: "start-up GNU grub list incorrect after kernel install"
date: 2011-11-23
forum: New to Ubuntu
---

### Post by wanabegeek on 2011-11-23
I have both windows 7 and ubuntu 11.10 installed on my computer.  I have configured the default operating system using start-up manager.  The computer starts automatically in windows but with a 30s delay on the menu in case I want to change my mind. This has worked perfectly until a new kernel was installed, then the computer automatically starts in the same position in the list but Windows has now been moved down the list.  

1. Ubuntu 2
2. Ubuntu 1
3. Memory Check
4. Windows

1. Ubuntu 3
2. Ubuntu 2
3. Ubuntu 1
4. Memory Check
5. Windows

For example, whereas it was once position 4 it is now in position 5, so  the memory check now starts automatically rather than Windows. Now I can go back into  start-up manager and change it manually, but I wondered if there was a  way to do it automatically so that it always points at Windows.

I admit this is probably sacrilegious to suggest such a thing (like I'd like the default to be windows) but a lot of the programs I've forced to use, I've only got valid licenses in Windows.:(

---

### Post by cariboo on 2011-11-23
If you removed one of the older kernels, your menu should work properly again. You can remove old kernels using the Software Center, Synaptic package manager, and of course the command line.

Ubuntu Tweak is another great tool fro removing unneeded packages.

---

### Post by drs305 on 2011-11-23
StartupManager is an older program not really designed for Grub 2. 

Try installing Grub Customizer and using that GUI app to select the default OS. It should keep Windows as the default even after kernel additions.

You can go to a page I wrote about it with more information by clicking the "Customizer" link in my signature line.

---

### Post by wanabegeek on 2011-11-25
> **drs305 said:**
> StartupManager is an older program not really designed for Grub 2. 

Try installing Grub Customizer and using that GUI app to select the default OS. It should keep Windows as the default even after kernel additions.

You can go to a page I wrote about it with more information by clicking the "Customizer" link in my signature line.

Thanks for your advice. This seems to have worked, I'll marked it solved, though the real test will be when the next kernel install. I'll re-post then.

:)

---

