---
title: "how do I mount a CD image?"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by B34ST1Y on 2008-11-14
How do I mount a CD/DVD image? The windows equivalent would be using alcohol 120% or daemon tools to emulate a drive and mount the image...

what's the linux equivalent of that??

---

### Post by bcd87 on 2008-11-14
I used two scripts that I found on [this](http://ubuntuforums.org/showthread.php?t=87369) page to mount ISO files. Works great :)

---

### Post by Pconfig on 2008-11-14
You could use this one:

[http://en.wikipedia.org/wiki/AcetoneISO](http://en.wikipedia.org/wiki/AcetoneISO)

I don't know if it's in the repo's (at school atm) but i guess it is ;)

---

### Post by B34ST1Y on 2008-11-14
I went to their sourceforge site for the repository...but i'm a little confused. how do I add it to my repository...or how do I get it? (acetoneiso2)

---

### Post by Sirron on 2008-11-14
Debs are available at:

[http://www.getdeb.net/app/AcetoneISO](http://www.getdeb.net/app/AcetoneISO)

Scroll down, and select the package you need. If you're unsure whether you need 32 bit or 64 bit, the chances are you need the 32 bit.

---

### Post by dmizer on 2008-11-14
No need for a script, or to insall anything.

Just make a directory to mount in.

For example:
```
mkdir mount
```
Then you can mount the iso with this command:
```
sudo mount -o loop file-name.iso mount/
```

The iso will appear on your desktop.

Edit:
To unmount the iso, use this command:
```
sudo umount mount/
```

---

### Post by B34ST1Y on 2008-11-14
WONDERFUL! thank you!

---

### Post by lucasl on 2008-11-14
In Intrepid, you can just right click, open with archive mounter.

---

### Post by Sprocket_dk on 2008-11-14
Also there is gmount-iso (GUI app.)

```
sudo apt-get install gmountiso
```

---

### Post by faraz_k86 on 2008-11-14
Now this is why I love the ubuntu community. So much help is available here :). Mandriva community, compared to ubuntuforums is almost dead..

k so trying to understand this code:

> sudo mount -o loop file-name.iso mount/

-what does the -o mean?

-if i created the mount folder in desktop the  will i have to navigate to desktop to mount?
like sudo mount -o ~/Desktop/image.iso mount/


where image is the image file, so is the above command correct?

edit: i forgot the loop.

-what does loop mean in the command?

---

### Post by dmizer on 2008-11-14
> **faraz_k86 said:**
> Now this is why I love the ubuntu community. So much help is available here :). Mandriva community, compared to ubuntuforums is almost dead..

k so trying to understand this code:



-what does the -o mean?

-if i created the mount folder in desktop the  will i have to navigate to desktop to mount?
like sudo mount -o ~/Desktop/image.iso mount/


where image is the image file, so is the above command correct?

edit: i forgot the loop.

-what does loop mean in the command?

-o equals "option"

loop means loop ... since there is no physical device (like a cdrom drive), the computer has to create a software loop to emulate a drive.

more information can be found in:
```
man mount
```
(to exit "man" type the letter 'q')

in this code:
```
sudo mount -o loop ~/Desktop/image.iso [COLOR="Navy"]mount/[/COLOR]
```
The [COLOR="Navy"]mount/[/COLOR] is a physical location on your computer. You can use any empty directory of your choice for this.

It might simply be easier to do use this line:
```
sudo mount -o loop ~/Desktop/image.iso /media/cdrom
```

To break this down a bit further, what this code does is take the ~/Desktop/image.iso and place it in /media/cdrom (or in my previous example mount/)

---

