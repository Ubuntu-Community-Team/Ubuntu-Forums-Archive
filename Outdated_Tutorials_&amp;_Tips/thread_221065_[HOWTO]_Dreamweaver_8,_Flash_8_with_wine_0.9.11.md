---
title: "[HOWTO] Dreamweaver 8, Flash 8 with wine 0.9.11"
date: 2006-07-22
forum: Outdated Tutorials &amp; Tips
---

### Post by kthakore on 2006-07-22
Install dreamweaver 8 and Flash on a seperate winxp partition
This is for all the web developers out there! Peace!
What I find is doing this on a fresh installation of ubuntu 6.06 works best.

Upgrade ubuntu to lastest standards
Iron out and video card issues (especially if you have fglrx)
Than install kerebros and all its required files (this is to give your dreamweaver full support like accessing servers)
make sure libgl and SDL is latest
Install wine 0.9.11 
reboot compy

then follow this guide on this [site]("http://www.zwhlug.nl/content/wine_how_to_get_macromedia_dreamweaver_8_fireworks_8_and_flash_8_working") 

right-click on desktop and create a launcher. Call it dreamweaver 8 
and this is the command 
```
wine "C:/Program Files/Macromedia/Dreamweaver 8/dreamweaver.exe" 
```

right-click on desktop and create a launcher. Call it flash 8
and this is the command 
```
wine "C:/Program Files/Macromedia/Flash 8/flash.exe" 
```

if flash and dreamweaver splash image comes up but the application doesn't start. Get the FF7 crack for it on the internet and apply it through wine.

also try sudo wine on the commands for the launcher

enjoy!!

Tip: Do this on a fresh install of dapper/wine

P.S this is my first how to so if I miss anything than plz let me know.
hopefully I can find a way to make CS2 work.

anyway peace!!

---

### Post by stengah on 2007-01-02
link is dead -anybody up for a new howto ](*,)

---

### Post by flapane on 2007-01-14
bump

---

### Post by andresh on 2007-01-15
I think the broken link could be this one:

[http://blog.publicidadpixelada.com/2006/09/04/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/](http://blog.publicidadpixelada.com/2006/09/04/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/)

---

### Post by loserboy on 2007-01-19
i'm trying to follow the howto on the link u posted, but i can't recode the .reg file, im getting this output.

> mike@mike-desktop:~/Desktop$ recode ucs-2..ascii macromedia.reg
bash: recode: command not found


---

### Post by malinkie on 2007-01-26
Thanks for the info. I did everything apart from copy the reg keys and it works fine for me on Edgy :)

---

### Post by bjhanifin on 2007-02-08
> **kthakore said:**
> then follow this guide on this [site]("http://www.zwhlug.nl/content/wine_how_to_get_macromedia_dreamweaver_8_fireworks_8_and_flash_8_working")

That site is gone, but here is a link to the same HOWTO courtesy of the Internet Archive.

[http://web.archive.org/web/20060505145757/http://www.zwhlug.nl/content/wine_how_to_get_macromedia_dreamweaver_8_fireworks_8_and_flash_8_working](http://web.archive.org/web/20060505145757/http://www.zwhlug.nl/content/wine_how_to_get_macromedia_dreamweaver_8_fireworks_8_and_flash_8_working)

---

### Post by Dylnuge on 2007-02-24
> **kthakore said:**
> Than install kerebros and all its required files (this is to give your dreamweaver full support like accessing servers)

I assume you mean kerberos? Either way, installation requires the removal of the FTP package. I went ahead, but I am assuming that this was correct.

Where is this so called FF7 crack? I am having the exact problem you describe and sudo wine is not helping.

Thanks,
Dylan

---

### Post by Dylnuge on 2007-02-24
Someone please help?????

---

### Post by proalan on 2007-03-01
I've come across a bug where I can't resize dialog boxes 

[ [IMG]http://www.imagehosting.com/out.php/i283550_Untitled.png[/IMG]](http://www.imagehosting.com)

In this case the "site definition" wizard

Is there a known fix for this?

Thanks in advance

---

### Post by proalan on 2007-03-02
I've managed to solve the dialog box resizing issue, it don't look pretty but it works

type in winecfg in a terminal

then go to the graphics tab and uncheck the box that reads 'allow the window manager to control the windows'

this defaults wine applications to their generic windows behavior and ugly blue theme

---

