---
title: "Virtual Box help !"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Drakkor on 2008-05-27
I have done a search for answers,but none of them seem to work, getting these errors, there a about 30 different modules to install,also how would I make an iso image of XP, Thanks :)

---

### Post by sayakb on 2008-05-27
To create an XP image, insert the XP setup disk, open Brasero, select Disk Copy and set the destination drive as "File Image"
Also, install the gues module for the kernel version you are currently using. Check by:
```
uname -a
```

---

### Post by wolfen69 on 2008-05-27
no need for all that. uninstall what you have and go [HERE]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI") . one click install. plus this version has usb support.

---

### Post by Sinkingships7 on 2008-05-27
For the virtualbox problems, you only need to do two things:

Install the proper kernel module (there's only one you need to install) and add your name to the list of vboxusers.

To get the proper module (and I'm assuming that you're using the default generic kernel), use this command:
```
sudo apt-get install virtualbox-ose-modules-2.6.24-16-generic
```
To add yourself to the vboxusers group:

System -> Administration -> Users and Groups
(after unlocking, if you're using 8.04) Click on "Manage Groups"
Scroll to the bottom. Double click on "vboxusers"
Check your name and close your way out.


There you go.

---

### Post by sayakb on 2008-05-27
> **wolfen69 said:**
> no need for all that. uninstall what you have and go [HERE]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI") . one click install. plus this version has usb support.
+1.. Works like charm :D

---

### Post by Drakkor on 2008-05-28
OK,got the Sun Virtual box setup, but I can't seem to get mouse control,The mouse on the virtual windows installation is frozen !

---

### Post by bumanie on 2008-05-28
I had that problem on versions 1.5.6 and 1.6.0, but version 1.5.4 works fine for me. I have used 1.5.4 on both gutsy and hardy without issue. By the way, other users have put bug reports in to sun/innotek about the inability to grab the virtual mouse - so it is not only you and I that have had problems.

---

### Post by Drakkor on 2008-05-28
Yeah, bumanie, I have v. 1.6.0, is there anyway to get v. 1.5.4 ? I checked 
the Sun page,but it seems they only have the new version.

---

### Post by Drakkor on 2008-05-28
*bump*

---

### Post by bumanie on 2008-05-28
I typed virtualbox 1.5.4 into a search engine. 99% of the sites which said they had that version, in fact didn't and sent you back to the sun site. I eventually found it on a japanese site I came across. Basically, patience and lots of searching, but it can be found.

---

### Post by Drakkor on 2008-05-28
You couldn't possibly post a link ? Would save me alot of time,lol :)

---

### Post by bumanie on 2008-05-28
Unfortunately I'm at work, but I will have a quick search and see if I can find the site again.

---

### Post by Sinkingships7 on 2008-05-28
Why don't you try installing the real virtualbox and follow my directions? It's not hard...

---

### Post by bumanie on 2008-05-28
Try this one and get the gutsy version, it should work on hardy.
[http://blog.pixnet.net/copact/post/5289913](http://blog.pixnet.net/copact/post/5289913) or try this one 
&#35831;&#36755;&#20837;&#20851;&#38190;&#23383; or here (gutsy version) [http://www.lug.or.kr/home/bbs/board.php?bo_table=talk&wr_id=124](http://www.lug.or.kr/home/bbs/board.php?bo_table=talk&wr_id=124)
Sorry can't do any better as I have to work again.

PS: You could try a torrent site someone may be still sharing the older version.

---

### Post by bumanie on 2008-05-28
> **Sinkingships7 said:**
> Why don't you try installing the real virtualbox and follow my directions? It's not hard...

The ose version doesn't give usb support. The binary, free for home use version, does provide usb support.

---

### Post by Drakkor on 2008-05-28
Actually, I did want to say that I also searched for v. 1.5.4, but like as you said,they all lead back to v.1.60,that being said , I'm dling the japanese gusy version, will post back. Thanks :)

---

### Post by bodhi.zazen on 2008-05-28
It is not *that* hard to find old versions of virtualbox. A google search turns up several sites on the first page :

[http://www.google.com/search?q=download+virtualbox+1.5.4&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=download+virtualbox+1.5.4&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

[http://www.filehippo.com/download_virtualbox/3136/](http://www.filehippo.com/download_virtualbox/3136/)

[http://www.filehippo.com/download_virtualbox/3821/](http://www.filehippo.com/download_virtualbox/3821/)

[http://www.filehippo.com/download/file/a635c8195a3f1562f95718f219ca357296f192689dd3c3c6839836d0e6ce7142/](http://www.filehippo.com/download/file/a635c8195a3f1562f95718f219ca357296f192689dd3c3c6839836d0e6ce7142/)

---

### Post by Drakkor on 2008-05-28
SUCCESS !! Thanks, bumanie got the japanese gutsy version of 1.5.4 and it's good to go ! :)

---

