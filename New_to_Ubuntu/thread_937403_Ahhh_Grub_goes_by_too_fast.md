---
title: "Ahhh Grub goes by too fast"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Dthorton15 on 2008-10-03
I bought a server from my friend and I need to reset the root password and I cant access grub because it goes by really fast. is there a way to slow it down?

---

### Post by pah99 on 2008-10-03
Try pressing random keys on keyboard. Grub automatically loads in a couple seconds unless you "disturb" it. Try that. Hope it works.

---

### Post by drs305 on 2008-10-03
Normally hitting ESC during the early part of the boot process will bring up the grub menu. Press it repeatedly until the grub menu displays.

---

### Post by Dr Small on 2008-10-03
After the system POST screen, spam the ESC key until Grub appears.

---

### Post by Dthorton15 on 2008-10-03
ugh okay so i spam the esc button and the square box pops up for like .7 seconds and then goes poof

---

### Post by Dr Small on 2008-10-03
> **Dthorton15 said:**
> ugh okay so i spam the esc button and the square box pops up for like .7 seconds and then goes poof
Press the up/down arrow keys to disable the timer, then.

---

### Post by Dthorton15 on 2008-10-03
> **Dr Small said:**
> Press the up/down arrow keys to disable the timer, then.just tried it -- didnt work

i want to make a clean install, is there a way to do it via the bios?

---

### Post by Dr Small on 2008-10-03
> **Dthorton15 said:**
> just tried it -- didnt work

i want to make a clean install, is there a way to do it via the bios?
No. You have to insert the disc and boot from it.

---

### Post by enriqueaf on 2008-10-03
For do a clean install you just need to insert the cd with the image of ubuntu and follow the promts, It is very easy. If you insert the cd of ubuntu and It doesn't run, It is very possible that you have to setup your BIOS and change the *"boot device order"*, If you don't know how to you can try searching, It is very easy.

And If you want to change the time of the grub for allow you to change it. Open the document *"/boot/grub/menu.lst"* first make a backup of it and later change the parameter:

```
timeout 10 #Seconds that the screen is on
```

And if the parameter:

```
hiddenmenu
```

is unquoted, quote it putting an '#' before it:

```
#hiddenmenu
```

And save it.

I hope that this information helps you.
Enriqueaf

---

### Post by hackerseraph on 2008-10-03
cant he edit it from a live cd instead of having to do a clean install? Ordinarily Id recommend a clean wipe but since he got the ubuntu from a friend, its already configured and ready to go... so?

---

### Post by enriqueaf on 2008-10-03
Yes he can edit the file using the live cd, if I am not wrong because He can get the permisions using the command *sudo* with his favourite editor, but just try, the only thing is that you must know wich one it is the partition or the volume in which the OS is and the correct file of the grub. 

I hope that resolve your question.
enriqueaf

---

### Post by Dthorton15 on 2008-10-03
Boot Device Priority
1. ATAPI CD-ROM Drive
2. Hard Drive
3. Removable Devices
4. Intel(R) Boot Agent Version 4.0

I tried and it didnt work. But I figured out that I was using windows to burn the iso... failureeee okay so now im using Infrarecorder thanks for all the help.

So basically when I install ubuntu it will ask me if I want to format the drives or something?

---

