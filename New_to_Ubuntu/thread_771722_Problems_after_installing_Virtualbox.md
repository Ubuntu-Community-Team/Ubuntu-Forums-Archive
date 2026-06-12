---
title: "Problems after installing Virtualbox"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by mity on 2008-04-27
I had installed Virtualbox. Tried it out and decided to stick to Dual boot. I have removed Virtualbox through Add/Remove menu and purged Virtualbox through terminal.

However, i am having trouble getting to my desktop now. Right before my desktop should appear, the reboot stops. i get a bright yellow screen with my mouse working. However, none of the icons appear. 

when i hard reboot, i noticed that it tells me that it can not find the kernel for the virtualbox. 

What should i do? i thought i had deleted virtualbox completely ( but why is it still searching a the kernel then?). 

or do i need to install a different kernel? 

Thanks

---

### Post by mity on 2008-04-28
quick update.

i am able to get to my desktop when i choose "generic" ubuntu from my grub menu. 

however, this is very annoying. is there a way for me to fix it or do i need to reinstall ubuntu?

---

### Post by batooh on 2008-04-28
Hello mity,

I guess you installed the package virtualbox-ose-modules-2.6.24-16-386 instead of the required virtualbox-ose-modules-2.6.24-16-generic.

By doing so there were two new entries added to your /boot/grub/menu.lst, both ending with "-386" (or similar, depending on the installed virtualbox-ose-modules-2.6.24-16-* package).

In order to remove these entries, you must open the menu.lst for editing by using this command:

```
gksu gedit /boot/grub/menu.lst
```

After you opened the file search for the following line (near the end of the file):

```
## ## End Default Options ##
```

Below that line there should be the two paragraphs that were added when installing the package. The first starts with:

```
title		Ubuntu 8.04, kernel 2.6.24-16-386
...
```

And the second starts with:

```
title		Ubuntu 8.04, kernel 2.6.24-16-386 (recovery mode)
...
```

Comment these two paragraphs completely out by using "#"-signs. But please be carefull not to remove the entries with "-generic" as these are the original ones.

As soon as you reboot, GRUB will again use the correct entry by default and everything should be fine.

Regards.

---

### Post by mity on 2008-04-28
> **batooh said:**
> 



Comment these two paragraphs completely out by using "#"-signs. 

what does it mean to "comment these paragraphs"? 

does that mean to place # sign at the beginning and the end of the paragraph? 

thanks so much your help, btw.

---

### Post by Vadi on 2008-04-28
Yes, place the # sign in front.

I'd recommend just searching for "virtualbox" in synaptic and removing everything that comes up related to it, that should work nicer.

---

### Post by mity on 2008-04-28
I've gone through synaptic and removed everything that mentioned virtualbox. 
That didnt help. 

I will try again tonight with batooh's instructions.

---

### Post by Vadi on 2008-04-28
Alright. File a bug report also, providing as many details as you can about this so that they can fix the package.

---

### Post by batooh on 2008-04-28
The problem with this package seems to be that it will write its entries to the GRUB menu.lst, but won't undo this as soon as the package is removed. This would not be that bad if the new entries weren't added to the beginning of the list and thus become the default.

It should, however, be noted that the package virtualbox-ose-modules-2.6.24-16-generic that matches the kernel version works exactly as it is supposed to do. And it does so without adding anything to the menu.lst (probably because the entries are already there).

And mity, if you don't want to comment anything out and if the additional entries in the GRUB menu don't bother you it should also be sufficient to change the default entry to 2. You can do this by simply replacing the folowing line in your /boot/grub/menu.lst (at the beginning of the file):

```
default		0
```

Into this:

```
default		2
```

This approach should be less error prone than the whole commenting thing, but please take a look at the entries at the end of the file and count the "title" lines to make sure that the number 2 is correct. The counting starts with 0 and you need the entry that has the title "Ubuntu 8.04, kernel 2.6.24-16-generic".

---

### Post by mity on 2008-04-29
thank you for all your help. i will try it tonight.

---

### Post by mity on 2008-04-30
looks like i do not have a permision to make changes to the menu file. does that mean i need to log in a root?

---

### Post by mity on 2008-05-04
I have finally able to figure out how to carry out batooh's original instructions ( ubuntu would not give me permission to do it batooh's way). 

If you open a terminal, and type

Code:

sudo nano /boot/grub/menu.lst

a text editor program will open in the terminal (similar to Ed in ms-dos). Make the necessary changes to the file highlighted by Batooh, then press Ctrl and O to save, then Ctrl and X to exit.

---

