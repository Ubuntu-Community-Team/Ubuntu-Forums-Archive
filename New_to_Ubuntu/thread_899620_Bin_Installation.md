---
title: "Bin Installation"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by AnIndian on 2008-08-24
I am trying to install one Binary File that does not supported by Ubuntu (I am using 8.04), Can any body help me to install through Binary File.

---

### Post by rockerphil on 2008-08-24
i'm guessing that you downloaded a program that came as a .bin file such as RealPlayer or somthing of the like, which means you need to make the file executable, which can be done by running this:

sudo chmod +x <filename>

be sure to replace <filename> with the name of the file you downloaded. once thats done you should be able to simply double click the file to install it, hope this helps,

Phil

----------------
Now playing: [ICP - ICP , Twiztid & Dark Lotus - Pass The Axe](http://www.foxytunes.com/artist/icp+-+icp+%2c+twiztid+%26+dark+lotus/track/pass+the+axe)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by sbszulu on 2008-09-13
I've downloaded the RealPlayer11GOLD.bin to my desktop. How do I refer to it.

Below is what I've attempted this and this is what I got:

[COLOR="Blue"]dundubala@dundubala-laptop:~$ sudo chmod +xRealPlayer11GOLD.bin
[sudo] password for dundubala: 
chmod: missing operand after `+xRealPlayer11GOLD.bin'
Try `chmod --help' for more information.
dundubala@dundubala-laptop:~$ sudo chmod +xDesktop/RealPlayer11GOLD.bin
chmod: missing operand after `+xDesktop/RealPlayer11GOLD.bin'
Try `chmod --help' for more information.
dundubala@dundubala-laptop:~$ 
[/COLOR]

---

### Post by Too Late on 2008-09-13
Put a space after the +x thing.
```
sudo chmod +x RealPlayer11GOLD.bin
```

---

### Post by iaculallad on 2008-09-13
After giving the file an executable attribute (sudo chmod +x RealPlayer11GOLD.bin), you can also run it using your terminal by:

```
./RealPlayer11GOLD.bin
```

---

### Post by Harisz750 on 2008-09-13
if having problem with terminal... just right click on the file.. propreties... permissions... and click on allow execute file as program. then open terminal.  browse in the folder of the bin file and give: ./RealPlayer11GOLD.bin

---

