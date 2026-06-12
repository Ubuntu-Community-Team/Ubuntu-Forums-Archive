---
title: "HowTo: Set up a custom image as a Grub splash screen"
date: 2006-08-21
forum: Outdated Tutorials &amp; Tips
---

### Post by stynx9000 on 2006-08-21
Hi Folks,

Long time reader, first time poster.  This HowTo will address using a custom image as a Grub splash screen.  

It’s actually quite easy to take a picture you know and love and convert it into a splash image for Grub to grab. I’m using Ubuntu, but this will work for any linux distro that uses Grub.

First, locate your image. Mine is a screen capture from the movie Seven Samurai. I’ve named it 7samurai1.jpg, which is what I’ll use for this example.

First, we’ll need to download a tool to help us convert images.  Convert is part of the imagemagick suite, so let’s get the whole shebang.

[INDENT]    sudo apt-get install imagemagick[/INDENT]

Let’s make a folder to keep this image in.

    [INDENT]cd /boot/grub
[/INDENT]
 [INDENT]   sudo mkdir images[/INDENT]

Now, let’s make a quick backup of our menu.list file in case we muck it up.

   [INDENT] sudo cp menu.lst menu.lst.bak[/INDENT]

That’s the file that tells Grub what to do on boot.

Let’s move into our images director and do some work.

    [INDENT]cd images[/INDENT]

My image file is located on my desktop, so I’ll copy it into the /boot/grub/images directory I just made.

    [INDENT]cp ~/Desktop/7samurai1.jpg .[/INDENT]

Now to convert this jpg image to the appropriate format.

    [INDENT]sudo convert -resize 640×480 -colors 14 7samurai1.jpg splashimage.xpm

    sudo gzip splashimage.xpm[/INDENT]

Now it’s converted and compressed. We’ll make a quick edit to our menu.lst file to tell it to look for a spash image.

    [INDENT]sudo gedit ../menu.lst[/INDENT]

In the file, just below the initial comments (lines that start with #) add the following line:

    [INDENT]splashimage (hd0,1)/boot/grub/images/splashimage.xpm.gz[/INDENT]

You’ll have to check to see which drive/partition it’s on. If you look at your menu.lst file, you should see several linux kernels. They’ll look something like this:

    [INDENT][I]title Ubuntu, kernel 2.6.15-26-686
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.15-26-686 root=/dev/sda3 ro quiet splash
    initrd /boot/initrd.img-2.6.15-26-686
    savedefault
    boot[/I][/INDENT]

Where you see root (hd0,2) is where you’ll tell grub to look for your splash image above.

Now, save your menu.lst file, exit Gedit, and then reboot!

Cheers!
[http://www.arsgeek.com](http://www.arsgeek.com)

---

### Post by uber noob on 2006-08-23
Nice tip, works perfect!

---

### Post by knives on 2006-08-24
:confused: Unfortunately when I followed this guide I got an error saying that the splashimage could not be read correctly...any ideas?

---

