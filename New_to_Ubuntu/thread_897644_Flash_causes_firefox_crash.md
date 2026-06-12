---
title: "Flash causes firefox crash?"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Accordionista on 2008-08-22
Hello!
 I've had Ubuntu for a couple of weeks. I don't know what version or anything sorry, I think the latest one. Anyway it's lovely. Apart from this annoying thing whereby I'll open up a page which has some sort of flash on it and firefox will just vanish! It's not everytime, but most times, especially sites like youtube. 

I was reading something on the internet about changing the screen depth? It doesnt really say how to do that though. 

I was wondering if anyone had experienced anything similar or could offer any advice?  

Cheers

---

### Post by nikobor on 2008-08-22
If the flash player is the problem then just run:
$ sudo apt-get remove flashplugin-nonfree
$ sudo apt-get install flashplugin-nonfree

---

### Post by Thelasko on 2008-08-22
> **nikobor said:**
> If the flash player is the problem then just run:
$ sudo apt-get remove flashplugin-nonfree
$ sudo apt-get install flashplugin-nonfree

That's a start, but I would go a step further, and use the command "purge" to ensure even the configuration files are removed.

```
sudo apt-get purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

```

---

### Post by Kinst on 2008-08-22
Bug with Flash 9. I just live with it.

The flash 10 beta doesn't have this problem, but I didn't like beta2 much.

---

### Post by Accordionista on 2008-08-24
Thanks for the help. I followed the steps and restarted, thought it had worked but then youtube crashed on me again. I tried getting flash 10 from adobe for linux, but it didnt seem to install? When i click on flash player installer it doesnt really do anything, and in the terminal it says 

chmod: cannot access `/home/jen/.mozilla/plugins/libflashplayer.so': No such file or directory

Even though the file is there in my downloads ugh. How do I properly install flash 10? There were some instructions on this other place on the internet but I didn't really understand-or trust- them.

---

### Post by t0p on 2008-08-24
> **Accordionista said:**
>  How do I properly install flash 10? There were some instructions on this other place on the internet but I didn't really understand-or trust- them.

Instructions on how to install flash 10 and stop the crashes is at this link - [http://ubuntuforums.org/showpost.php?p=5587712&postcount=472]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472")

---

### Post by Accordionista on 2008-08-24
How do I know if i'm 64 or 32 bit?

---

### Post by natirips on 2008-08-24
Try "Galeon" instead of Firefox. I found it being much faster and more stable (with flash). Galeon is based on the same engine as Firefox, but it is native to Gnome.

---

### Post by natirips on 2008-08-24
> **Accordionista said:**
> How do I know if i'm 64 or 32 bit?
Type "uname -a" in the Terminal (without the quotes). It shoud say x86_64 somewhere along the line if you are 64-bit, or i386 or x86 or such if you are 32-bit.

---

### Post by philinux on 2008-08-24
I'd try first running firefox in safe mode. To see if any of your addons are making FF unstable.

In a terminal use

firefox -safe-mode

I can access youtube with no crash.

---

### Post by Accordionista on 2008-08-24
> **t0p said:**
> Instructions on how to install flash 10 and stop the crashes is at this link - [http://ubuntuforums.org/showpost.php?p=5587712&postcount=472]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472")

I followed the steps but don't seem to have flash... was i meant to have it installed before I did that?

---

### Post by t0p on 2008-08-24
> **Accordionista said:**
> I followed the steps but don't seem to have flash... was i meant to have it installed before I did that?

Did you update your repository list?  You need to do that before you do the apt-get update and upgrade

---

### Post by Accordionista on 2008-08-24
I thought those were the instructions to do that oops. I don't know how to update my repository lists- nor, what they are ehehe.

---

### Post by natirips on 2008-08-24
In terminal:```
sudo aptitude update
sudo aptitude upgrade
```This will update your repository and upgrade your system.

---

