---
title: "Home Server setup advice and questions?"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by 30SomethingGeek on 2008-09-29
Good Morning. First let me say thank you for any help on my questions about setting up my little home server. Sorry for the long post I just want to be detailed in my expectations and clear.

I am interested in setting up a home server for a few different things and 75% sold on Linux (Ubuntu) but still looking at WHS which cost approx: $150 at the egg. I have a decent RIG Core2Duo (E6600) 2gigs of RAM a 160gig drive in it (which I&#8217;ll be adding a new 500gig drive too) and well; it is my current gaming PC. However I&#8217;m going to be building a new one (WinXP for gaming and daily MSOffice, and digital photography stuff) and figure I can get some good use and setup a server at home with the current PC.

I&#8217;m looking to have a headless &#8220;home server&#8221; under my desk (after initial install) I&#8217;m trying to avoid having to use a KVM. I&#8217;m tired of all the cables. This would mean Remote administration is highly important (both on my network and via the internet). I&#8217;m a geek and always played with Linux in one way or another, but it&#8217;s been a while and I&#8217;m starting from the beginning here. Ideally what I want from my home server is the following:

* I want to store, backup, and share my family digital photos, music, videos, files, you name it within my home (from any PC or Mac) and online via my own little private secure website. I have a domain name already. I use Lightroom for pictures, and iTunes for music. Not sure if this makes any difference.

* I want to be able to do some sort of redundancy setup up with my 500gig, and 160 gig, drives. I also have an external 320gig USB drive for extra back up of the server that I can use.

* Have a shared network printer for all my PC&#8217;s and Mac's at home.

Can I do this with Ubuntu and save my money?

From what I see WHS makes this easy and does all this out of the box. One feature I really like in WHS is the drive setup. Adding drives of different sizes is not a problem to my home server.

I&#8217;m all for getting my hands dirty, learning some Linux, and having some fun with getting things up and running. If this is the way to go (and MS-WHS is out) does it make a difference if I use the Desktop version (with server components)or Server version of Ubuntu? I dont mind the command line... But I need the GUI; I love the GUI&#8230; :) Lastly any recommendations for a GOOD Ubuntu book for learning and reference to get me started would be greatly appreciated.

---

### Post by hyper_ch on 2008-09-29
> **30SomethingGeek said:**
> I’m looking to have a headless “home server” under my desk (after initial install)
That's how most server on linux work. Get the server install cd, install it, add openssh-server ```
sudo apt-get install openssh-server
```maybe also get fail2ban or denyhosts (depending on your network structure...)

Then loggin from another computer (use Putty on windows) or on another linux machine just:```
ssh user@SERVERIP
``` and you can administrate it.

> **30SomethingGeek said:**
> * I want to store, backup, and share my family digital photos, music, videos, files, you name it within my home (from any PC or Mac)
Install a samba server for that.

> **30SomethingGeek said:**
> and online via my own little private secure website.
Not quite sure what you mean here.


> **30SomethingGeek said:**
> * I want to be able to do some sort of redundancy setup up with my 500gig, and 160 gig, drives. I also have an external 320gig USB drive for extra back up of the server that I can use.
That can be simple done... probably using rsync for that job - but I need more info from where you want to backup what.

> **30SomethingGeek said:**
> * Have a shared network printer for all my PC’s and Mac's at home.
Printer sharing through a linux server is possible, but I've never done it. You just need a printer that runs on linux.

---

### Post by superprash2003 on 2008-09-29
printer sharing via samba is possible...

---

### Post by 30SomethingGeek on 2008-09-29
1. Forgive me when I said private website I simply meant via the internet using my own domain name and a dyndns service to get to my home server. Also share pictures with family via the web like flickr from my home server.

2. I see you mention Putty but this would only be command line right? Is there a GUI remote desktop option?

3. In my homeserver I&#8217;m going to have: 2 drives internally of different sizes. 1x:160gig and 1x 500gig I wanted to use both. The external would be just a dump drive I can do weekly. Not sure if Ubuntu or Linux had an option like WHS

> &#8220;Drive Extender

Windows Home Server Drive Extender is a file-based replication system that provides three key capabilities:

    * Multi-disk redundancy so that if any given disk fails, data is not lost
    * Arbitrary storage expansion by supporting any type of hard disk drive (Serial ATA, USB, FireWire etc.) in any mixture and capacity&#8221;

Good to read sharing is not an issue for the printer Thanks superprash2003 for the &#8220;samba&#8221; sharing for my printer. Again I&#8217;m sure out of the box things just don&#8217;t work in Linux but for the most part the options are there. Other than the simplicity of WHS I&#8217;m just trying to see what benefits I would be losing out going Ubuntu if any.

Regards

---

### Post by cariboo on 2008-09-29
Disk Extender = LVM which can be setup during installation.

I don't think anybody mentioned it, the Ubuntu Server doesn't install a gui. You can administer the server using Webmin or ebox. Have a look here for Webmin:

[http://www.webmin.com/](http://www.webmin.com/)

Ebox is in the repositories.

Jim

---

### Post by gregnbaker on 2008-11-18
I have done something similar to what you seem to be looking for, have a read and feel free to leave a comment asking any questions you may have:
[Family Home Server Setup]("http://tinyurl.com/66rl25")

---

### Post by trukker on 2009-03-16
Do you really need to map a user to a particular windoze machine?

Can you allow more than one user to log into the ubuntu server from more than one windoze machine? Any ideas how?

Thanks.

---

### Post by gregnbaker on 2009-03-16
> **trukker said:**
> Do you really need to map a user to a particular windoze machine?

Can you allow more than one user to log into the ubuntu server from more than one windoze machine? Any ideas how?

Thanks.

I'm not quite sure what the questions is...the reason I map each user to a windows machine is so each client can only access their own backup folder.
As for mapping each SAMBA user to an Ubuntu user, I just found this the easiest method.

---

### Post by trukker on 2009-03-16
Thanks Greg,

I was wondering, because at home, we have a (windoze) laptop which is used by my wife and my kids. If I map one windoze computer to one samba user on linux, then they will not be able to have different backup folders on the ubuntu server.

---

### Post by gregnbaker on 2009-03-16
My solution would be to set up separate accounts on the laptop for your wife & kids, mapping each username to an identical Samba (and Ubuntu) user. This of course depends on whether your kids are old enough to be able to log on and off the Windows laptop...
Ideally you would have WinUser1, SambaUser1 and UbuntuUser1, WinUser2 etc.

---

### Post by trukker on 2009-03-17
Thanks Greg, that seemed to work!

My smbusers file now looks something like this:

joseph = joseph dell1525
corinne = corinne

What I can't understand is that dell1525 is the machinename on my windows machine, whilst joseph is my ubuntuusername and sambausername.

---

