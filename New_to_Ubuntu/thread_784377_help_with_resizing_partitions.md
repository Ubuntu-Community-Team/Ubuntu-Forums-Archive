---
title: "help with resizing partitions"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by paul101 on 2008-05-06
hi

i have a dual booted machine with Windows vista and ubuntu, i wish to resize both partitions to about 50/50 each...

---

### Post by herbster on 2008-05-06
The GParted LiveCD is probably the way to go here.

---

### Post by paul101 on 2008-05-06
there seems to be something happening and making it so i cant resize my vista partition :confused:

---

### Post by prshah on 2008-05-06
> **paul101 said:**
> hi

i have a dual booted machine with Windows vista and ubuntu, i wish to resize both partitions to about 50/50 each...

Why do you have 5 (!!) swap partitions? One is enough, delete the rest. Delete the ones closer to the "Emptyness".

Then MOVE your linux partition forward into the emptyness.

Then RESIZE/MOVE your extended partition; when asked the option, choose "space before" and enter the amount of space you want added to the vista partition.

Then RESIZE your vista partition.

Please back up before doing anything.

From the looks of the "keys" icon, you are not running the live CD. Use the live CD, and unmount active partitions and "swapoff" all swap before attempting moving/resizing.

If any of this is confusing, post back for more details.

---

### Post by paul101 on 2008-05-06
forgot to add, i'm using the xubuntu live cd

---

### Post by paul101 on 2008-05-06
i cant seeeeem to resize the vista partition :confused:

---

### Post by tjwoosta on 2008-05-06
vista is very protective of its partitions,

your going to want to boot into vista and go to the start menu and type in computer management and hit enter 

then on the left side you will see disk management toward the bottom of the list (under storage)

this is the default vista partition editor, use it to resize your vista partiton


(also about the 5 linux swap partitions,   you only need one!)

---

### Post by paul101 on 2008-05-06
well: my dad screwed up the computer yesterday (by deleting xp partition), and i cant boot into vista. (i get error 22)


edit: so go with above screenshot, and then fix vista... then increase vista partition??

---

### Post by paul101 on 2008-05-06
when i try to move / resize the ubuntu partition i get:

---

### Post by tjwoosta on 2008-05-06
> so go with above screenshot, and then fix vista... then increase vista partition?? 
yea i think that should work  (also you will want to make sure that ubuntu is using the swap partition that you left and not one that was deleted)

i think this should work(not sure if it works like this in ubuntu or not)
```

sudo swapon dev/sda(whatevernumberisswap)
```

for instance if swap is sda3, do swapon dev/sda3

whats wrong with vista, it just dont boot?

do u get the grub boot loader or the windows boot loader?


EDIT:
> when i try to move / resize the ubuntu partition i get:

well it seems to me that your having way too many of problems with the way your harddrive is setup

i would recommend just backing up all of your important data to some dvds or something and reformating everything and start from scratch

(install windows first then partition with vista partitioner then install ubuntu , that way the grub boot loader will be set up automatically, same with swap) and everything will be in the right order(
for instance the first partition will be sda1 then second will be sda2 and so on)

but thats just me.. also it will be alot of work to get windows and ubuntu all setup again

---

### Post by paul101 on 2008-05-06
i have the grub bootloader which loaded up the windows / xp bootloader (my dad deleted xp this morninng)

---

### Post by tjwoosta on 2008-05-06
sry please disregaurd that last post


the reason you cant move or resize ubuntu partition is because the drive is mounted (your using it)

just boot the live cd and use the gparted that is under System-Administration-PArtition Editor



as for the problem booting vista 

please post what is in your menu.lst file

(by the way this is a lowercase L not a #1)
```

gedit /boot/grub/menu.lst

```

---

### Post by paul101 on 2008-05-06
ubuntu@ubuntu:~$ gedit /boot/grub/menu.lst
The program 'gedit' is currently not installed.  You can install it by typing:
sudo apt-get install gedit
bash: gedit: command not found

hmmmmmm :(


i'm using the live cd btw :)

---

### Post by tjwoosta on 2008-05-06
hmmm... that is strange


ubuntu cd is supposed to come with gedit (mine did)

but anyway gedit is simply a text editor (like notepad)

go up to Applications and search for a text editor (probably under Accessories)

after you find the text editor open it and tell me what it says in the title bar

---

### Post by prshah on 2008-05-06
> **paul101 said:**
> ubuntu@ubuntu:~$ gedit /boot/grub/menu.lst
The program 'gedit' is currently not installed. 
i'm using the live cd btw :)

Since you're using xubuntu, you have to replace gedit with mousepad, eg ```
mousepad /boot/grub/menu.lst
```

As mentioned in my earlier post, UNMOUNT all partitions (right click partition in parted, then choose unmount) and swapoff all partitions (right click each swap ["red"] partition, choose "swapoff". you can leave the last one active if you like)

---

### Post by paul101 on 2008-05-06
the title says:

> menu.lst

---

### Post by tjwoosta on 2008-05-06
ahh... yes xubuntu

sry i forgot you said you were using xubuntu


prshah has it right

just open the menu.lst file and post the contents


(the only reason i asked what was in the titlebar was to determine the name of the text editor, prshah has already figured out that you have mousepad)

---

### Post by paul101 on 2008-05-06
i get:

---

### Post by paul101 on 2008-05-06
> **prshah said:**
> As mentioned in my earlier post, UNMOUNT all partitions (right click partition in parted, then choose unmount) and swapoff all partitions (right click each swap ["red"] partition, choose "swapoff". you can leave the last one active if you like)

it's still not working :confused::confused::confused: :lolflag:


ok, now atleast try and get vista working lol, i dont have a vista disk to hand :S

---

### Post by tjwoosta on 2008-05-06
sry im stupid

if your using the live cd right now you will need to go to the menu go to Places then click the one with a picture of a harddrive and it should say Filesystem or Volume (its your xubuntu partition that your looking for)

in the xubuntu filesystem (not the live cd filesystem)double click boot then double click grub then double click menu.lst

post that

---

### Post by paul101 on 2008-05-06
hmmmm, when i click on "filesystem" it only shows the live cd's files :comfused:



ive decided just to re-format, and install xubutu for now (i dont really have anything on vista... (besides my dad installed it, so its likely to be a dodgey copy lol )

is there anything particular to do when formatting??...

i'm getting a new laptop that will come with vista, will i be able to use the disk to put vista on my desktop as well??

---

### Post by paul101 on 2008-05-06
right, do i need to do anythig else to re-format (ive never re-formatted lol)


edit: will it delete grub aswell so that i can do a fresh install of it

---

### Post by tjwoosta on 2008-05-06
> 
hmmmm, when i click on "filesystem" it only shows the live cd's files :comfused:


its not called filesystem i guess it would have said blahh blahh volume
for instance if it were 50 gigs it would say 50GB volume

there should have been two one vista and one xubuntu in the Places menu (directly under computer)

but i see now that youve already deleted the partitions


> ive decided just to re-format, and install xubutu for now (i dont really have anything on vista... (besides my dad installed it, so its likely to be a dodgey copy lol )

if your just going to reinstall to the entire disk you dont even need to erase anything or format partitions, all you have to do is put in the live cd and click the install icon on the desktop

when it asks just select "Guided Install:use entire disk"

this will format everything and install automatically

---

