---
title: "[SOLVED] How do I install these drives? (Network card)"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Melindrea on 2008-06-21
Hi,

I have just installed Xubuntu on an old computer, and am trying to install the Dynex networkcard. I have the CD, but am... idly confused on how to get things to work =)

I have a makefile. I have dxe201.c and I have kern_compat.h ...So, how do I do to get this to an installation file so I can get my network card up and running?

Thanks! =)
Melindrea

---

### Post by pytheas22 on 2008-06-21
I don't have experience with the Dynex card, but if you have source files on the CD, then you probably need to compile the driver using 'make.'  In most cases there's a readme file that will explain what to do.  If not, in general you'd need to first install a compiler and related things with the command:
```

sudo apt-get install build-essential
```

then change to the directory where the source files and makefile are located, and type:
```

make
```

to build the driver, and if that succeeds:
```

sudo make install
```

to install it onto your system.

But as I said, look for a readme first explaining what to do.  If you can't figure anything out, you can post the files you have here and I'll try to take a look.

Also what is a Dynex card?  Is it just a normal ethernet card?  If so, are you sure it doesn't already work in Ubuntu?  The vast majority of ethernet cards should just work out of the box.

---

### Post by Melindrea on 2008-06-21
It is just a normal ethernet card, but no, it's not found automatically.

When I try to use apt-get it tells me that it can't find the package, I assume because I can't get online. =)

Still trying to get used to Xubuntu, not to mention the fact that my mouse keeps lagging >.<

---

### Post by pytheas22 on 2008-06-21
Do you know the model of the card?  If you don't, type "lspci" in a terminal and look for the line relating to your ethernet card.  If you post that line here it would be helpful.

---

### Post by Melindrea on 2008-06-21
It's a Dynex DX-E201, PCMCIA Card. Quite cheap one, but I was hoping it'd still work! =) (and I think it will, once I figure out how to get it to)

---

### Post by pytheas22 on 2008-06-21
I downloaded the drivers for your card myself and had a look.  The Linux part is a mess...there are instructions on what to do (inside a folder called TXT) but many parts of them are plainly wrong, and even after sorting through what I could, I still couldn't get anything to compile.  I don't think that the people who wrote them really know anything about Linux.  They also have a file ostensibly containing directions for compiling on Unix systems, which I thought might help figure out how to make this compile on Ubuntu; unfortunately, it's empty.  What a joke.

I did however discover that your card should have an rtl8129 chipset (this is the part of the card that actually matters; Dynex just sells it), which is good to know.  I've had no luck so far, but I'm hoping that if I look more I'll be able to find some other way to get the driver for this chipset installed, or directions that actually work.

Short of that, there's an email address in the source file (dex201.c) that we can use as a last resort to try to get someone to help, or someone in the programming forum might be able to look at the source and tell us what to do.  I'm not really qualified to read source code myself.

Before I keep working on finding a way to compile, however, I want to make absolutely sure that the driver for your card definitely doesn't exist on your system.  It could be the case that it's there but the card just isn't working for some reason.  Please run these commands:
```

dmesg | grep eth
dmesg | grep rtl
lspci | grep -e thernet -e rtl
```

and if it's not too hard, please copy any output that you get here.

Also, if you type:
```

ifconfig -a
```

do you see anything?  This will let us know if the driver already exists or not (I'd be really surprised if it isn't built into the kernel, since the source code has been available under the GPL since 2000, according to what I downloaded).

---

### Post by pytheas22 on 2008-06-21
I've got some more things to try; everything I read says that the driver should already be in the kernel, but there are lots of reports of people having trouble getting this kind of card to work.  Please give these things a try and let me know if any of them makes your card work:

1. type:
```

sudo rmmod 8139cp
sudo modprobe 8139too
sudo ifconfig eth0 up
```

then try to connect

2. type:


```

sudo rmmod 8139too
sudo modprobe 8139cp
sudo ifconfig eth0 up
```

any luck now?

3. type:
```

sudo -s
mii-tool -F 10baseT-HD
sudo /etc/init.d/networking restart
mii-tool -R
```

then try to connect

4. type:

sudo mousepad /boot/grub/menu.lst

scroll towards the bottom and look for the line that says:

## ## End Default Options ##

Right below this you should see an entry that looks similar to:
```

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b5725877-5158-4c5f-b858-e0f6eededc1e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

At the end of the line that begins with "kernel" (in the example above this line says /boot/vmlinuz-2.6.24-19-generic root=UUID=b5725877-5158-4c5f-b858-e0f6eededc1e ro quiet splash), add this:

NOAPIC

then save the file and reboot your computer.  Does it work?

Hopefully one of these options will solve the problem.  By the way, which version of Xubuntu are you running (8.04 or something earlier)?

---

### Post by Melindrea on 2008-06-22
Right. I'd spent ten minutes typing up the output. Then I decided to go back to the "1-2..." that you suggested. Since I no longer got the error message, but it still wasn't working... I grabbed the cord from my other laptop, and i now have a working network card.

(I'm fairly certain it was the second option that fixed it, because I know it wasn't working yesterday, even with another network cable.)

Thank you a lot!
*marks as solved*

---

### Post by pytheas22 on 2008-06-22
I'm glad it worked out and ended up being a lot simpler than compiling that C code.  Linux comes with drivers for as much stuff as possible built in, so it's very rare that you have to install drivers for normal devices.  Some wireless cards, scanners and web cams do sometimes require additional drivers, but it's extremely rare to have to do that for an ethernet card.  In your case, the driver was pre-installed, but it wasn't being loaded properly for some reason.

Also, if you find yourself having to enter those commands after every reboot to get the Internet working, let me know and we can make them run automatically, if you're interested.

---

### Post by Melindrea on 2008-06-23
Rebooted it a few times, and it still works, so everything's okay. Thanks again =)

---

