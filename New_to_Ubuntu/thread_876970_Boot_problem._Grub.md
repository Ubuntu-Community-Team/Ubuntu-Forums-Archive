---
title: "Boot problem. Grub?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Mytth on 2008-08-01
After installing mp3 codecs automatically when i boot ubuntu instead of counting 5,4,3,2,1 then booting it goes into grubfordos,Does anyone know a solution for this? :confused:

---

### Post by mikewhatever on 2008-08-01
Hi, what's Grub for DOS?
Can you post the output of <cat /boot/grub/menu.lst>.

---

### Post by Mytth on 2008-08-01
Ok, hold on,i think it is a loader for linux?
EDIT
When i type that in the console it gieves: ERROR 15:file not found
When i press escape it gives me a all list of commands, none are usefull, however ther is one simmilar to the command you gave me: display ubuntu/install/boot/grub/menu.lst . when i press enter on it it just displays the amount of ram the console is using and codeEnd:0x41a38

---

### Post by Diabolis on 2008-08-01
Solution: [http://ubuntuforums.org/showthread.php?p=5499528#post5499528](http://ubuntuforums.org/showthread.php?p=5499528#post5499528)

---

### Post by mikewhatever on 2008-08-01
Mytth, the command I posted is fine. Don't type it, copy/paste instead.
**cat /boot/grub/menu.lst**

Can you explain in details what grubdos or linuxdos means.

---

### Post by Mytth on 2008-08-01
Sorry, but it didnt work, commands such as sudo or general ubuntu commands dont work in the grub console,
Heres the format
grub>
And i can type a command afterwards.If i type boot it tells me i have to load kernal first.
@ mikewhatever:i canc acess ubuntu,or its system, i cant even acess termininal ,linux doesnt load, just grub,when i type your command in grub it gives error15:fille not found.Im not on ubuntu right now im dualbooting xp and ubuntu.
I didint even know about grubfordos untill it didint boot ubuntu,On my boot selector i choose ubuntu it,after 3 secounds grub starsts and it has loaded noting but a black screen with white writin, and i can type commands for grub in it.

---

### Post by Diabolis on 2008-08-01
If you manage to enter to the grub console, you are already in sudo mode.

You HAVE to reinstall grub, there is no other way around it. Follow the steps that I linked to.

---

### Post by Mytth on 2008-08-01
Sorry,but im just getting Error 27:unrecognised command in the grub console from those commands.You do know that i can acess my boot menu but when i choose ubuntu it just loads grub right?

---

### Post by philinux on 2008-08-01
I would use the live cd and reinstall grub.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

or use the supergrub disk.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Mytth on 2008-08-01
And that will make ubuntu boot when i select it instead of grub?

---

### Post by Diabolis on 2008-08-01
> **Mytth said:**
> Sorry,but im just getting [COLOR="Red"]Error 27:unrecognised command[/COLOR] in the grub console from those commands.You do know that i can acess my boot menu but when i choose ubuntu it just loads grub right?

The error message is exactly telling you what went wrong. An unrecognised command means that you typed something wrong. You tried to execute a command that does not exist.

---

### Post by Diabolis on 2008-08-01
This must work:

Steps to reinstall grub:
```

find /boot/grub/stage1    It will find all the places **from where** you can install grub.
root (hd?,?)              Select **from where** you want to install grub
setup (hd?)               Select the drive **in which** you want to reinstall grub
reboot
```

So the output of the **find** command is the input of **root**.

:-({|= 516

---

### Post by Mytth on 2008-08-01
Im going to try that through the live cd.

---

### Post by Diabolis on 2008-08-01
Yeah it would be easier through the live-cd because you can quickly look up the commands while issuing them.

---

### Post by jualin on 2008-08-01
> **Mytth said:**
> And that will make ubuntu boot when i select it instead of grub?

That will reinstall the Grub (bootloader) and it will let you log in back into Ubuntu.

---

### Post by Mytth on 2008-08-01
Well iv started terminal through the live cd and when i get to this command <find /boot/grub/stage1> it tells me Error 15:File not found 
Any ideas?

---

### Post by jualin on 2008-08-01
did you run > sudo grub first?

---

### Post by Diabolis on 2008-08-01
uh oh!

That is strange.

try this first
```
 sudo apt-get --reinstall install grub
```

---

### Post by Mytth on 2008-08-01
Yes.

---

### Post by Mytth on 2008-08-01
Ok, here is exactly what iv done, i selected try ubunto without installing on the live cd and diabolis i have done that and i still recieve Error 15:file not found,
If it affects anything i installed my ubuntu through wubi.

---

### Post by Diabolis on 2008-08-01
You could have a typo in your menu.lst file or a corrupted file.

Error message information: [http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by Mytth on 2008-08-01
I have to do somthing, can you help me in an hour?

---

### Post by Diabolis on 2008-08-01
Yeah, I'll be around.

---

### Post by Mytth on 2008-08-01
Alright, im back can anyone help?Im thinking that reinstalling linux is my only option.

---

### Post by unutbu on 2008-08-01
So we can have a better idea of what is going on, would you please post the output to
```

sudo fdisk -l
```

(The last part is a minus lowercase L).

---

### Post by Mytth on 2008-08-01
Ok,
Invalid option -- 1
I think i should just reinstall ubuntu,But thanks for the help guys!

---

### Post by Diabolis on 2008-08-01
You shouldn't give up yet, its worth to keep trying, since from what I've seen most of the problems come from typos.

Stay on the safe side by just copy/pasting.

---

### Post by jualin on 2008-08-01
> **Mytth said:**
> Ok,
Invalid option -- 1
I think i should just reinstall ubuntu,But thanks for the help guys!

You have a typo in there, you typed a one "1" when it was an "l" (letter before "m" in the alphabet)

---

### Post by Mytth on 2008-08-01
Thanks diabolis,but i only installed ubuntu 2 days ago and i had no files stored on it yet, i just was hoping that this was a common error which is easily fixed,im going to make my linux partiton larger now anyway as i know now that its a good os :)
Again, thanks for the help everybody,Il probobly be needing it again soon lol! ;)

Oh, ill try that first.
The command worked, but im just going to reinstall jualin, i appretiate the help.

---

### Post by jualin on 2008-08-01
No problem dude, we are here to help!

---

