---
title: "Safely uninstalling a linux distro? Confused"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by gingerj on 2008-09-09
Hi All,

I am trying to uninstall Open Suse, to try out Kubuntu 8.4 and get that working alongside my happy XP partition.

I was wondering what is the safest way of doing this? I currently have a dual boot setup with GRUB booting into windows first.

I put the Kubuntu 8.4 CD in and had a quick play with LIVE CD and then clicked on the desktop icon to "install". During the partition setup by default it seems to want to create a **fourth** patition something I do not want.

So my question is, how can I uninstall Open Suse, Install Kubuntu, whilst retaining my priority number one XP partition and keep 2 partitions with GRUB booting into windows first? 

I have a fear of in MS-DOS reformatting the Open Suse partition, and finding that GRUB cannot find the Suse partition and not letting me do anything. Or even worse finidng out that GRUB is on the reformatted drive and my laptop doens't boot up into any operating system.

Any help/tips/advice would be greatly appreciated!

---

### Post by cdtech on 2008-09-09
I would use the Live CD and open "gparted" to format the partition in question this will remove the Suse install. The install will reinstall the GRUB bootloader for you. As far as the added partition, would this be the swap, or what is the install calling it?

---

### Post by cariboo on 2008-09-09
Just use the manual partition option and set up the partitions the way you want.

Jim

---

### Post by gingerj on 2008-09-09
> **cariboo907 said:**
> Just use the manual partition option and set up the partitions the way you want.

Jim

Yeah I am not smart enough for that :s

---

### Post by Znupi on 2008-09-09
> **gingerj said:**
> Yeah I am not smart enough for that :s
Just format the current opensuse partition (it's the only one with the "ext3" type, most probably) and set its mountpoint to ' / '. That should do the trick, Kubuntu will probably reinstall GRUB so you'll have to configure it again to boot Windows by default, but that's a trivial task which you can find on the net how to do or ask anyone around here :)

---

### Post by Gonz_91 on 2008-09-09
I would recommend restoring the windows MBR before formatting the partitions, so that, just in case, you can always boot into windows.
IMHO   :)

---

### Post by gingerj on 2008-09-09
I have installed Kubuntu thanks for the help, a couple of points:
[LIST]
[*]how do i put windows back to the top of the grub menu?
[*]how do i uninstall suse, i have used the auto settings on the kubuntu wizard. I now have three distros installed :p
[*]can I make the GRUB menu pretty? The suse one is great, the Kubuntu one is a DOS menu :(
[/LIST]

---

### Post by skymera on 2008-09-09
Uninstall Ubuntu?

It's not a program. You need to format your drive.

---

### Post by Znupi on 2008-09-10
> **gingerj said:**
> I have installed Kubuntu thanks for the help, a couple of points:
[LIST]
[*]how do i put windows back to the top of the grub menu?
[*]how do i uninstall suse, i have used the auto settings on the kubuntu wizard. I now have three distros installed :p
[*]can I make the GRUB menu pretty? The suse one is great, the Kubuntu one is a DOS menu :(
[/LIST]
1) Edit the /boot/grub/menu.lst file. The file is pretty much self-explanatory, but make a backup first to be sure. If you just need Windows to be the default selected entry in the grub menu, you can simply change the "default" directive in that file to whatever your Windows entry is. Or change it to "saved" and, for each entry, add a "savedefault" line after the "root" line.
2) As I said, you should've used the manual option. Ubuntu won't remove any operating systems without you telling it explicitly to do so. Install GParted and reformat the OpenSuSE partition (or delete it directly, and expand your other partitions). Then, in the menu.lst file you can remove the lines describing the OpenSuSE entries. Don't just be like "I don't know how to handle partitions, so I'm not going to do it". Don't be afraid! Just install GParted and you'll see it's a piece of cheese cake :)
3) You probably can, but I don't know. Why do you need it pretty anyway? Ubuntu is pretty enough :P

---

