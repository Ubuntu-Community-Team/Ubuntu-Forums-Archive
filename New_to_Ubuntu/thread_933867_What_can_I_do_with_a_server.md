---
title: "What can I do with a server?"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by adamogardner on 2008-09-29
This probably sounds stupid and I kinda get that servers are what delivers websites and...?  But what does the ubuntu server distro do?  what can I conceivably do with something like that?

---

### Post by ScreWe on 2008-09-29
Ok now I have never tried it but this is from personal experiences with Windows Server...


It should be mostly Command line/Terminal. But what it offers is hosting of websites such as Apache oriented to handle PHP, Perl, RoR, and others. Also it can host gaming servers for people if you can find the proper files to do such. 

That is all I've ever used a server for besides just hosting files.

---

### Post by jerome1232 on 2008-09-29
Really a server is just a computer that provides services for other computers.

Common things an Ubuntu server might be used for:

Fileserver, using nfs, sshfs, ftp, sftp, samba: This would function as a central place for computers to store files. If you've ever uploaded a file to a server on the internet then you've used a file server before.

Print Server, using cups, samba, basically what it sounds like, a computer that has printers attached to it and allows other computers on the network to print to those printers over the network

Webserver using Apache2, this is probably the most common type of server, they allow other computers to view webpages stored on the server.

another less common example I have Ubuntu server installed on one of my computers, I downloaded the teamspeak server program to it and it hosts voice services for me and my friends (we can all connect to it and talk to each other)

---

### Post by OutOfReach on 2008-09-29
File server, media server, audio server there are a lot of possibilities

---

### Post by ScreWe on 2008-09-29
After reading other people's posts the best way to sum it up is by saying this...


It is a computer that shares data/files with other computers and is dedicated to that service.

---

### Post by adamogardner on 2008-09-30
So other computers view websites from servers. and servers upload files to other computers upon request (or illegally?)  So if I wanted to maintain a website I would need to get a server?  Or..?  It sounds like something to do.  Is it fun?  Or is it dreadfully tedious?  I'm not afraid of the command line and want to learn it well, but I am not proficient with it.   Is this something worth pusuing?  I have a great idea for a website.

---

### Post by abeisgreat on 2008-09-30
> **adamogardner said:**
> So other computers view websites from servers. and servers upload files to other computers upon request (or illegally?)  So if I wanted to maintain a website I would need to get a server?  Or..?  It sounds like something to do.  Is it fun?  Or is it dreadfully tedious?  I'm not afraid of the command line and want to learn it well, but I am not proficient with it.   Is this something worth pusuing?  I have a great idea for a website.

Well there is more to running a website then having a good idea and a server. Are you proficient in html, css, php, asp, and other languages used for web development? Also just having a server doesn't give you a website you need a domain name correctly configured to your IP, also your router needs to be configured correctly. 
If your interested in making a website I highly suggest using a free service like Geocities, or buy a cheap server (so your files are hosted elsewhere), its alot less hassle.
Also if you run a server from your house your server pc needs to be on 24/7 so people can go to your website. You gotta think about things like energy consumption, it is really not practical.

---

### Post by Krupski on 2008-09-30
> **adamogardner said:**
> This probably sounds stupid and I kinda get that servers are what delivers websites and...?  But what does the ubuntu server distro do?  what can I conceivably do with something like that?

Ubuntu desktop is a full operating system with a graphical user interface and lots of GUI apps included.

Ubuntu SERVER is a stripped down Linux install with a command line interface (CLI) only.

It also handles memory allocation differently and it has a different tick speed.

Server is optimized to be... a server. It's meant to put disk storage on the network, as well as FTP and HTTP access to the files.

Some people have the notion that a "server" version of an OS is better or faster or more expensive that the "desktop" version.

This is not true. The real difference is that Server is optimized to be a stand alone "black box" that works behind the scenes... sometimes without even a keyboard or monitor.

This is as opposed to Desktop where you would have a monitor, keyboard, mouse and all the things a traditional "user computer" has.

You can take Server, install the X window system and your favorite desktop (KDE or Gnome) and end up, essentially, with the desktop version... but why?

Hope it makes sense...

-- Roger

---

### Post by adamogardner on 2008-09-30
> **abeisgreat said:**
> Well there is more to running a website then having a good idea and a server. Are you proficient in html, css, php, asp, and other languages used for web development? Also just having a server doesn't give you a website you need a domain name correctly configured to your IP, also your router needs to be configured correctly. 
If your interested in making a website I highly suggest using a free service like Geocities, or buy a cheap server (so your files are hosted elsewhere), its alot less hassle.
Also if you run a server from your house your server pc needs to be on 24/7 so people can go to your website. You gotta think about things like energy consumption, it is really not practical.

It doesn't sound practical, but I'm intriqued.  I don't know html, css, pphp, asp etc.  but I want to implement this.  I have to look into geocities. Can a server pay for itself by say, renting space for client websites?  How do servers make money?

---

### Post by abeisgreat on 2008-09-30
> **adamogardner said:**
> It doesn't sound practical, but I'm intriqued.  I don't know html, css, pphp, asp etc.  but I want to implement this.  I have to look into geocities. Can a server pay for itself by say, renting space for client websites?  How do servers make money?

Well if you want to make websites check out w3schools.org great resource 

It could, if you set up your own server there wouldnt be an issue except the limit of your internet, because everyone who goes to your site is using your internet and it will slow it down.

Servers make money by people paying them to host sites or websites make money by having ads and/or product placement.

---

### Post by superprash2003 on 2008-09-30
yes you could.. for this you have to start it professionally.. you could host one website at home with a home server That is very much practical..But setting up a web hosting company from home isnt.. it requires a lot of planning etc. the right kind of hardware, the right internet connection.. and you have to provide 99.9%uptime.. a single downtime without prior information could cost you a lot!!

---

### Post by AndyCooll on 2008-09-30
At it's most basic the moment you share a file with another computer that pc is in essence acting as a "server" to that other computer.

Of course you can go much further as has already been mentioned (file server, print server, web server etc) and you can optimise your pc by using the server edition. You could perhaps make the pc headless, where it would sit on your network without a mouse, keyboard or monitor and you'd ssh into it. You can even buy specialised server type hardware.

You can do as little or as much as you want, the choice is yours.

:cool:

---

### Post by adamogardner on 2008-10-01
w3schools is a very good website.  I spent the rest of the day yesturday learning xhtml.   I have so much t learn yet.  from the last post I gather I can use another computer as a server and screw around with a personal website through it via my primary computer(ssh).  I install ubuntu server into second computer > put it on my network > and serve up some xhtml!  I can do that8-)

---

### Post by Kellemora on 2008-10-01
Hi Adam

Although I'm a total Noob when it comes to using Linux myself, I used it in my business for years, even though other outside companies set it up and maintained it for me.  I was afraid to touch that box, hi hi.........

Here is a scenario that could not be performed from Windows, don't know if it could be performed by a standard Distro or not either.
But setting up a computer solely as a print server (it was also used as one of the redundant back ups as well) is how we did large print jobs FAST using cheap ink jets.
Don't ask me HOW it was done, but it cost $1,600.00 to make it happen, hi hi.....  And required some software to be written, which was the biggest part of the expense I think.  Been a while back now.

We had 12 printers connected to the print server.
From ANY computer, we could send a print job as a single copy to PS1 (the name of the print server).
A screen would pop up asking how many copies we needed, plus other common features of most printers.
Let's say we needed 300 copies of the documents, we would enter 300.
But, what the print server did, was send only 25 documents to each of the 12 printers.
If one of the printers was offline, it would add those pages to the other printers, or if it had several separate documents to handle, it may only give you 6 of the 12 printers for that run.
In any case, they would start running, not instantly, but more like down the line, one would start, then the next, then the next, etc.
In other words, we would have 300 copies DONE in the time it takes to print 25 copies.  Actually faster than that, because the printing was faster using a server than from a PC.

FWIW:  We DID own a high speed crash printer.  When it was broken (which was quite often) we were out of business until it was fixed.
Going with the multiple ink jet printers was a wise move on our part.  We never had downtime after that due to a printer failure.
We HAD to use waterproof inkjet and no lasers because our printing services were for keepsake books that only get opened once every 10 years or so, and you know what happens with bound laser printed pages!
We also did printing for companies that had sleeved presentations, again lasers would not work for this application either.  
So we had quite a few customers and were always busy.
Then like other technoogy advancements, they came out with soy based crash printers that worked similar to offset and our customer base slowly dwindled back down again to short order stuff.

So, this is just one example of how a SERVER became a necessity!

TTUL
Gary

---

