---
title: "Copying Folders"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by jairom70 on 2008-11-21
ive tried this 
[B]
sudo cp -R /home/jairo/downloads/tronium//usr/share/mplayer/skins[/B]

i get this 

[B]cp: missing destination file operand after `/home/jairo/downloads/tronium//usr/share/mplayer/skins'
Try `cp --help' for more information.[/B]

So i tried this 

**sudo cp -R /home/jairo/downloads/tronium/ /usr/share/mplayer/skins**

and i get this 

**cp: cannot stat `/home/jairo/downloads/tronium/': No such file or directory**

---

### Post by shoot2kill on 2008-11-21
make sure you are being CaSe SenSiTivE

and the second command is correct with a space between source and destination.

---

### Post by jairom70 on 2008-11-21
yup i even edited the folder name to "tronium" and used Copy&Paste and still nuttin  x[

---

### Post by hyper_ch on 2008-11-21
```

ls -al /home/jairo/downloads/tronium

```

---

### Post by scorp123 on 2008-11-21
> **jairom70 said:**
> ```
cp: cannot stat `/home/jairo/downloads/tronium/': No such file or directory
``` Simple: there is no such folder with that name. You probably mistyped the name. cAsE mATters a LoT HeRe!  "downloads" and "Downloads" are _NOT_ the same!

---

### Post by gn2 on 2008-11-21
Or press Alt+F2 then ```
gksudo nautilus
``` to open the file browser with admin privileges and take away all the guesswork and potential for typos.

Remember to close Nautilus when you're finished....

---

### Post by Paqman on 2008-11-21
+1 for using Nautilus.

However, if you are using the CLI, you can use tab autocompletion to remove the risk of typos. Instead of typing the full directory name, just type the first couple of letters then hit tab to have it fill in the rest. If it doesn't autocomplete, you either need to give it more letters or you've misspelled the ones you've used.

---

### Post by newbee70 on 2008-11-21
> **jairom70 said:**
> ive tried this 
[B]
sudo cp -R /home/jairo/downloads/tronium//usr/share/mplayer/skins[/B]

i get this 

[B]cp: missing destination file operand after `/home/jairo/downloads/tronium//usr/share/mplayer/skins'
Try `cp --help' for more information.[/B]

So i tried this 

**sudo cp -R /home/jairo/downloads/tronium/ /usr/share/mplayer/skins**

and i get this 

[B]cp: cannot stat `
/home/jairo/downloads/tronium/': No such file or directory[/B]

take what I say with a grain of salt I'm a noob 2

Question: are your files in your root directory, or are they in your home folder?

/usr/share/mplayer/skins  is obviously in the root directory

/home/jairo/downloads/tronium/   looks like it is in your home folder. if it is put a tilde in front of the path.

 ~/home/jairo/downloads/tronium/

---

### Post by shoot2kill on 2008-11-21
no, /home/jairo/ is the same as ~/

if you have ~/home/jairo/ the system will try to look for the path

/home/jairo/home/jairo/downloads.......
which i very much doubt will work.

---

### Post by newbee70 on 2008-11-22
> **shoot2kill said:**
> no, /home/jairo/ is the same as ~/

if you have ~/home/jairo/ the system will try to look for the path

/home/jairo/home/jairo/downloads.......
which i very much doubt will work.

On my system if I leave the tilde off it go's straight to the root directory.

---

