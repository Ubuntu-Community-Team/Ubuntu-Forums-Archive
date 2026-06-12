---
title: "How To: tidy up your boot menu screen"
date: 2009-03-30
forum: Outdated Tutorials &amp; Tips
---

### Post by letmekilluplz on 2009-03-30
[COLOR="RoyalBlue"][CENTER]How to tidy up your boot menu screen[/CENTER] [/COLOR]
Time: Takes 5-10m
Difficulty level: Medium
Danger to system level: Medium

[COLOR="Red"][SIZE="3"]PLEASE NOTE: This tutorial will have to be adapted for your setup and booting situation. Try this at your own risk![/SIZE][/COLOR] 

This tutorial will explain how to change you boot screen from a jumbled mess to a clean cut more organized display, and can even incorporate
a welcome message!

[LIST=1]
[*]Open the terminal and type: ```
gksudo gedit /boot/grub/menu.lst
```

[*]Scroll down to the portion of the text that says: "END DEFAULT OPTIONS" [/LIST]


What you will be doing is making everything that you don't want to show on the menu a comment. To do this you will need to put a "#" before each line(The comment will end at a new line). 

[LIST=3]
[*]Put a "#" in front of everything except the first Ubuntu option(You may also want to change the title of the first one to make it look better)
[/LIST]

It should look like this:

## ## End Default Options ##

title		Ubuntu 8.10
uuid		d88d6e92-209b-4671-b5a6-cf1f99168f55
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d88d6e92-209b-4671-b5a6-cf1f99168f55 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

#title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
#uuid		d88d6e92-209b-4671-b5a6-cf1f99168f55
#kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d88d6e92-209b-4671-b5a6-cf1f99168f55 ro  single
#initrd		/boot/initrd.img-2.6.27-11-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid		d88d6e92-209b-4671-b5a6-cf1f99168f55
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d88d6e92-209b-4671-b5a6-cf1f99168f55 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		d88d6e92-209b-4671-b5a6-cf1f99168f55
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d88d6e92-209b-4671-b5a6-cf1f99168f55 ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		d88d6e92-209b-4671-b5a6-cf1f99168f55
#kernel		/boot/memtest86+.bin
#quiet

Now that will make it so that only the first Ubuntu option is Visible. (If you ever want to boot into another version come back and uncomment each line and reboot to see it again)

Now this is where it gets tricky depending on which OS you are dual-booting with it will change what you have to do here so you will have to use your brain to figure it out. 

If you are using Vista like I am you will want to comment the XP/NT/2000 part. 

Mine looks like this:

### END DEBIAN AUTOMAGIC KERNELS LIST



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

# title		Windows NT/2000/XP
#root		(hd0,0)
#savedefault
#makeactive
#chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1

[COLOR="Blue"]Now you should notice that I change the Vista title so all it says is "Windows Vista" nothing about a loader or any other confusing things.[/COLOR]

Now you are done! Save and reboot! (Hopefully you did it correct and it worked)


[CENTER][COLOR="Blue"]Part 2: How to display a welcome message( Sort of)[/COLOR][/CENTER]


If you would like to display a welcome message or instructions or whatever follow these directions.

[LIST=4]

[*]Type this directly under the words "END DEFAULT OPTIONS": 
[/LIST]
Title: (Here you would put whatever you want your message to be)
Root

I wanted my message to say: "Hello Sean(That's my name), what operating system would you like to use?

So I would input this:

title		Hello Sean, which operating system would you like to use?
root

After you input that you're done!!! Reboot to see your changes!

[COLOR="Lime"][SIZE="5"]GOOD LUCK![/SIZE][/COLOR]

---

