---
title: "anyone link me to a good lamp guide start to finish?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Corrupter on 2008-05-02
Hey guys, i've been having a LOT and by a lot i mean TONS of little glitches and such... to be rather honest with you im new (like its no obvious) to linux however i atleast know how to manipulate the terminal fairly well and such however permissions still get me scratching my head and some of the .confs can be a tad confusing...

was googling a few guides and found some / most of them to be great starters but they either go so far and stop or they skip some things i found (perhaps unique to my installation).  Was wondering if anyone in the Ubuntu community found any really good start to finish LAMP guides that also possibly include vsftpd installation and configuration.

I'll end with this.  My goal for all of this was to simply make a web and ftp server that mimics the paid ones you might subscribe to, i dont currently have the money to put the 3 websites live that i am working on for my family, my game and my business and thought what better way to get started then converting my old game system into a LAMP server.  I still use windows for my main system although seeing some of these things that Ubuntu is capable of and the pure genius of most of the menu's and features i may be converting full time.  This would be a great way for me to familiarize myself with Linux in general for this application.

Thanks in advance guys, this is such a great community of people!

---

### Post by tyroeternal on 2008-05-02
Howtoforge.com has always been pretty good about talking through the setup of systems like that.  I'm not sure it will be the magic bullet for you, but here you go

[The Perfect Server - Ubuntu Hardy Heron (Ubuntu 8.04 LTS Server)]("http://howtoforge.com/perfect-server-ubuntu8.04-lts")

---

### Post by kwacka on 2008-05-02
The quick & easy way to install: Open Synaptic Package Manager, click 'edit' then 'mark packages by task' & select "LAMP server' & apply.

For documentation on MySQL see: [http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)

---

### Post by Corrupter on 2008-05-05
that guide was quite good however didnt touch on the configs entirely for features like user permissions and permissions for php to create folders etc.  It has everything else.  And in response to Kwacka if it was that easy i wouldnt have asked for a guide =P  sure it "works" right out of the box so to speak ( as in to say it works right from installation ) but there are some configurations that no ones really touched on yet and im wondering if anyone has.  All im saying is every time i've installed a lamp server from scratch i get it all the way to hosting a webpage but not all the webpages i create on it work properly like they do on my webhost i pay for.

Things like having to manually create folders for scripts that usually make the folders on their own or information on how to create sql databases using myphpadmin  (as for the databases i know how to do that myself but thought that would be something you'd find in a guide)

just some thoughts, if anyone knows of an all inclusive complete guide let me know it would be something i'd like to cross reference to see what im missing.

---

### Post by hyper_ch on 2008-05-05
the howtoforge howto and the ispconfig install will take care of all that...

---

### Post by Corrupter on 2008-05-05
so i have to use another package (ispconfig) in order to serve a website when it seems like the standard lamp with the correct configurations would do all but the same.  I dont want to have to use a bunch of extras on a server that im using on a local network to do a simple task.  But if its the only way then so be it.

---

### Post by hyper_ch on 2008-05-05
do you want an all-in-one solution or not?

---

