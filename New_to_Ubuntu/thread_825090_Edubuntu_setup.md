---
title: "Edubuntu setup"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by EXCiD3 on 2008-06-10
So I'm setting up a school's computer lab with Edubuntu. Each machine is 1.2ghz AMD Athlon with 256mb of ram. I also have a server i would like to setup to store the user account's /home folders via NFS. Now, ive installed Ubuntu on a couple of the computers and it is running awfully slow. Hardy lags LOTS and Firefox 3 uses lots of ram. Should I go with Xubuntu and install the Edubuntu add-on cd over top of that since they no longer offer a separate distro, just an addon? The server has a 400mhz processor, 512mb ram and 65gb hard drive and shouldnt be much of a problem to get setup, i mainly need help getting the individual computers running faster.

The apps they are looking to run are Google Earth, Open Office and typing tutors. I have installed Google Earth 4.2 and 4.3 and they both run ridiculously slow and do not display the globe correctly, everything is shoved into the top section of the view. Any tips would be great, its just my first time doing a network of computers, and my laptop has no issues so this is a step into the wilderness for me. ;)

---

### Post by gr4nf on 2008-06-10
Yes, Xubuntu would run a bit faster, so you could try that. If you wanted to be even less system intensive, though, you could get Debian. As for the web server, just get apache2*
```
sudo apt-get install apache2
```
and you will have a file in /var/www called index.html, which should be accessible by entering the server's ip address (find this with the command "ifconfig") in any of the computer's browsers. You can put links to files through there.

*Two things:
1. This wont allow you to get things from home.
2. do this ONLY if you have a secured firewall.

---

### Post by JoshuaRL on 2008-06-10
Are you wanting to run those computers as stand alone, but with /home on the server, or as thin clients?

If thin clients, you'll need to upgrade the server a bunch.  But if you want to run OO.o and Google Earth from the client side computers you'll need to upgrade their RAM.  I sincerely doubt that 256MB is enough for those applications, especially Google Earth.

---

### Post by gr4nf on 2008-06-10
Also, if planning to run as thin clients (computers that do nothing but log into a server, basically. Like terminals.) you will need to run:
```
sudo apt-get install openssh-server
```
in your server computer, and run
```
sudo apt-get install openssh-client
```
on all of your other computers.

---

### Post by TJCIB on 2008-06-10
I was doing the same thing about 6 months ago with about the same system specs you have.  Here's what I ended up doing:

I installed Ubuntu 7.10 on all the computers (I haven't switched to 8.4 because everything is perfect, so I don't need to)

I used apt-cacher to make updating the networked computers easier, that way I only download the updates once for 15 computers. The link looks more complicated than it is.  I actually wrote a small script to automate it
[http://ubuntuforums.org/showthread.php?t=564301](http://ubuntuforums.org/showthread.php?t=564301)

I use NIS for the login. [http://www.debian-administration.org/articles/36](http://www.debian-administration.org/articles/36)

I use NFS for mounting the /home directory at boot up.  This part isn't the easiest, it will lock up sometimes if you don't find the right settings for your network, but it can work.  I'm a noob and I got it to work.  The kids love the fact that they change their desktop on one computer and it changes on every computer.
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)
That ubuntu geek tutorial will get it working, but here is a more complete guide that can help you secure it and troubleshoot.
[http://tldp.org/HOWTO/NFS-HOWTO/server.html](http://tldp.org/HOWTO/NFS-HOWTO/server.html)

I hope this helps.

Agreeing with the other posters 256MB RAM might be a little small for what you're trying to do.  I would recommend 512MB on the clients, and close to 2GB on the server if you want it to be perfectly smooth.

Peace

**EDIT**
I would forget Edubuntu and just install the packages you need into the regular distro.  Unless the cute icon sets are important, but I'm sure you can get that too.

---

### Post by EXCiD3 on 2008-06-10
Thanks guys for all the help. I definitely am going to be pretty much doing exactly what TJCIB mentioned. The computers are currently running XP and they all run fairly fast. I don't really understand what the "thin client" means. There isn't a very good description of it that i could find. Anyone care to explain? That would be great. I don't think I have much of a need for that anyways. Since edubuntu isn't a separate distro anymore, im going to run Xubuntu and install the educational software on it individually. Unfortunately I dont think the school has a budget for upgrading RAM...Google Earth only uses about 50MB of RAM and runs just fine in WinXP on them currently. They also use Office 2003 and its fairly snappy. I think I just need to try to minimize everything that is running as much as i can. And yes I am planning on using the server just to store /home for everyone. 65gb will be plenty.

---

### Post by JoshuaRL on 2008-06-11
Well, you won't have a /home for XP.  You can store their My Documents folder there, but we all pretty much assumed that you would be running Ubuntu of some sort on the computers the kids used.  That would actually maximize the ability of the computers you do have.

[http://en.wikipedia.org/wiki/Thin_client](http://en.wikipedia.org/wiki/Thin_client)

Pretty much, consider the server/thin client relationship like the old mainframe computers that did most of the computing and all the file storage, while the terminals were just login boxes for the mainframe.  That's the idea, you have one big daddy and all the others are small and lean, costing much less.  That way, you can maximize the use of one really good computer through the use of a bunch of little dumb ones.

---

### Post by TJCIB on 2008-06-11
Do you plan on wiping out all of XP, or doing dual boots on all of them?

I do dual boot (but with two hard drives) on one computer, since our Library Catalog software does not work in Linux yet (I almost have it).

Let me know how it goes.

---

### Post by EXCiD3 on 2008-06-11
Thanks guys, well i was hoping not to use the server for anything more than storing each user's /home. I plan on having each computer separate from the server so as not to rely on it for anything else since these computers should be fast enough to handle anything, plus once school gets started i will be 2 hours away and will have to do tech support over the phone unless i setup something for me to login later on after i get this all setup.

I do plan on dual booting a couple of the computers for teacher's use because like everything, theres always one little problem holding you back and they do have some software that they need windows with.

---

### Post by JoshuaRL on 2008-06-11
I would suggest setting up SSH on the server so you can be able to fix it remotely.  Have you tried using Wine for the programs they need from Windows?

---

### Post by EXCiD3 on 2008-06-11
I'm not even sure of the software they need for windows at the moment. whats funny is i was just going to use XP which they had already setup on all of them but each computer is stuck on xp sp1 because they seem to have invalid copies of windows for some reason...nobody knows how the copies got on there. So we are converting to linux. Two of them were donated recently and I'm just going to dual boot those, but once they give me the software that they need i will try them in wine.

I am definitely going to setup ssh for them so that i can remote access later, since nobody else seems to know anything about linux around here. lol

I'll let you guys know if i run into any problems or need some ideas. Thanks for the help so far!

---

### Post by JoshuaRL on 2008-06-12
Cool man, I like it.  "Invalid copies of Windows?  I've got a solution for you, Linux."

I'll keep this thread subscribed to help if I can.

---

### Post by EXCiD3 on 2008-06-12
Thanks! Right now im just burning off more copies of xubuntu so that i can get the installs going faster. Unfortunately it looks like im going to have to take the server apart. The cd rom drive doesnt want to open...it lights up and pretends like its going to open but sure doesnt do anything. lol

I'm sure ill have some more questions in a little while once i get the server going. Shouldnt be awfully hard, my only worry right now is getting Google Earth for them, they may have to do without. I installed 4.3 on one of the computers and it runs pretty nice in windows surprisingly but in Ubuntu it doesnt want to work. Just crashes after about 15 sec. :( Thats a problem to be fixed later on i guess.

---

### Post by JoshuaRL on 2008-06-12
Yeah, try to run it in the terminal to see the error.  Google Earth needs 3D if I remember right, so keep in mind it may just be a driver issue.

Here's another good idea.  If you have a bunch of the same computer, work on one until you get it exactly right.  Then use remastersys to copy down the configuration and just do an install across the board to all of them.  Pretty sweet.  Plus, if one gets hosed you can always take that disk and get a nice fresh copy.

---

### Post by EXCiD3 on 2008-06-12
Yep thats exactly what im doing! :D Remastersys is a great tool for that. We have at least 15 of the same computer plus like 10+ random ones haha schools always get donated the most random pc's ;)

unfortunately i think the graphics cards are SiS 630/730's and they dont have too great of linux drivers as far as i know, not even sure if they are capable of 3D :(

---

### Post by EXCiD3 on 2008-06-12
Btw, just ran Google Earth 4.3 in a fresh install of Xubuntu on one of the computers, no output in terminal of the crash. :(

---

### Post by JoshuaRL on 2008-06-12
Does glxinfo return anything about the direct rendering?

What type of video cards do they have?

---

### Post by EXCiD3 on 2008-06-12
Check post 15 for the video card model. We are looking to upgrade them if we can find some place to buy 12 or so AGP cards for cheap, know of any place by chance? Google Earth did end up spitting out an error eventually, not enough texture memory. The video cards just dont have enough ram, but I do think glxinfo did say DRI was enabled although i played with glxgears just to get a taste of their speed (i know its not a benchmark) and was only getting 100fps. The SiS drivers are pretty much 2D only for linux and we never really intended for use on Debian since SiS's website offers only rpm's. I don't know if another distro would be a better idea or what, but we are still looking to upgrade the computers if we can find a place cheap enough.

---

### Post by JoshuaRL on 2008-06-13
Then that would probably be your issue.  I'm almost positive that Google Earth needs direct rendering and 3D.  And if nether DRI nor the proprietary drivers can get it where you need, then another card is probably best.  If you can find a good driver from SiS, even if it is RPM, get it.  You can use alien to convert those.

I would search out the common sites like CompUSA, Newegg, and Tigerdirect to see if they have anything on clearance.  I would also check out dealspl.us to see if there's anything good there.  But your best bet may be good old eBay.  Look for lots of 15-20 so that if a couple are bad or go bad you have some backups.  And while you're at it, look for some lots of RAM to upgrade them.

And you probably already know this, but if you have a choice go with nVidia instead of ATI on the older AGP stuff.  Much better chance of a happy ending.  And it would probably be a good idea to research here the cards you're looking at to see how they stack up.

---

