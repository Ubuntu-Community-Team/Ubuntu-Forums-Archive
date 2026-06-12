---
title: "Edubuntu without thin clients in school lab"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by fourthofjuly on 2008-10-24
[COLOR="RoyalBlue"]hi all...

at the outset, let me state that i have become a huge fan of ubuntu and now wish to promote it further... its too good an OS to be ignored for sure...

i would like our school kids to start using edubuntu in their computer lab, and i can convince my superiors to atleast use it for the pre-primary kids on a pilot basis... you see, the teachers are already facing severe virus problems with the newly installed XP on our brand new compaq machines and have to spend considerable time in the admin work... we have total 35 systems for the primary section...

the problem is we do not have a server machine and only a peer-to-peer network of the 35 systems (all exactly identical)

1) now, if i install and configure edubuntu on 1 of them, how can i replicate this on other machines?

2) also, what happens when i update / install new software on 1 machine? can i transfer the updates to the other 34 as well? 

3) is there some way to automatically store all user files to a specific location on the LAN so that it can be accessed from any of the machines? in fact all our machines have 250 GB HDD, but hunting for files sometimes is very difficult as teachers are also using these machines & they tend to forget the file location.  

the machine configuration:- Compaq make CPU with Intel Dual core 1.6 GHz, 1 GB RAM, 250 GB HDD, DVD writer, Benq 15" widescreen monitors - all machines are running XP Professional on a peer-to-peer network with CAT6 cabling connected to 2 switches with 24 & 16-ports.

any help will be appreciated...

thanks...[/COLOR]

---

### Post by Crandom on 2008-10-24
1) Canonical (the parent, for profit company of ubuntu) offers Landscape, a tool to manage many ubuntu pcs as one but it is not free. See these:
[http://www.canonical.com/projects/landscape](http://www.canonical.com/projects/landscape)
[http://www.ubuntu.com/news/landscape](http://www.ubuntu.com/news/landscape)

Landscape has a free 60 day trial and is free if you sign up for canonical's professional support service.

You could just dd the entire hard drive of one pc to a file then dd the file onto every other computer. It would work, but is more advanced and would take a long time.

2) See Above

3) Sounds possible, don't know how though.

---

### Post by Kellemora on 2008-10-24
Hi FOJ

I'm just now getting my feet wet with Edubuntu too........

So my answers might not be entirely accurate, but it's what I've learned so far.

#1 - Edubuntu is a Server, there is NO replication to do to the other machines.  They can be treated as Dumb Terminals by programming the network card to boot from the Server, OR you can install the instructions to boot from the server on each terminal using a floppy, a CD or the hard drive if it has one.  Since they are currently Doze machines, they probably have a hard drive in them.

#2  You install ONE update to the Server, all the other machines obtain their data from the server so they need no updates.

#3 Is the issue I'm working on right now myself, but have not quite got it all worked out properly yet.  Since Linux is quite a bit different than the Doze, a hard drive on ANY machine can appear to be right on the machine you are working at.  Which to me means that if all the machines looked to the SERVER for their data, it shouldn't matter WHERE the physical hard drive is located.  In other words, if all the hard drives of the other computers were MOUNTED on the Server, all of the machines should see these hard drives as being ON the server itself.

Each users file is in a /home/user directory, WHERE this /home directory is located don't matter.  It could be on any computer or in the server.  But it should be pointed to by the server.
In this way, from the server, all you have to do is backup /home and all users data is backed up, regardless of where or on what hard drive it is in the building.

Like you, I can't see using up Server resources that are duplicated on all the computers already.  And this is what I am currently studying myself.
Let the programs RUN on the individual machines, but let the SERVER handle the File Storage so everyone can look to ONE PLACE for Data!

Again, I've only been studying and playing with Edubuntu now for less than two weeks and so far, everything I want it to do, it will.  Even if I don't understand what it is I did yet, hi hi

TTUL
Gary

---

### Post by fourthofjuly on 2008-10-25
> **Crandom said:**
> 1) Canonical (the parent, for profit company of ubuntu) offers Landscape, a tool to manage many ubuntu pcs as one but it is not free. See these:
[http://www.canonical.com/projects/landscape](http://www.canonical.com/projects/landscape)
[http://www.ubuntu.com/news/landscape](http://www.ubuntu.com/news/landscape)

Landscape has a free 60 day trial and is free if you sign up for canonical's professional support service.

You could just dd the entire hard drive of one pc to a file then dd the file onto every other computer. It would work, but is more advanced and would take a long time.

2) See Above

3) Sounds possible, don't know how though.
i have heard about landscape, but i guess the support cost may not be approved as such...

dd command is used to copy entire disk, which is what i understand... can be done the first time

but for updates, after i copy the entire disk of  user A to that of user B, won't it overwrite all the personal files of user B in his home folder?

---

### Post by fourthofjuly on 2008-10-25
> **Kellemora said:**
> Hi FOJ

I'm just now getting my feet wet with Edubuntu too........

So my answers might not be entirely accurate, but it's what I've learned so far.

#1 - Edubuntu is a Server, there is NO replication to do to the other machines.  They can be treated as Dumb Terminals by programming the network card to boot from the Server, OR you can install the instructions to boot from the server on each terminal using a floppy, a CD or the hard drive if it has one.  Since they are currently Doze machines, they probably have a hard drive in them.

#2  You install ONE update to the Server, all the other machines obtain their data from the server so they need no updates.

#3 Is the issue I'm working on right now myself, but have not quite got it all worked out properly yet.  Since Linux is quite a bit different than the Doze, a hard drive on ANY machine can appear to be right on the machine you are working at.  Which to me means that if all the machines looked to the SERVER for their data, it shouldn't matter WHERE the physical hard drive is located.  In other words, if all the hard drives of the other computers were MOUNTED on the Server, all of the machines should see these hard drives as being ON the server itself.

Each users file is in a /home/user directory, WHERE this /home directory is located don't matter.  It could be on any computer or in the server.  But it should be pointed to by the server.
In this way, from the server, all you have to do is backup /home and all users data is backed up, regardless of where or on what hard drive it is in the building.

Like you, I can't see using up Server resources that are duplicated on all the computers already.  And this is what I am currently studying myself.
Let the programs RUN on the individual machines, but let the SERVER handle the File Storage so everyone can look to ONE PLACE for Data!

Again, I've only been studying and playing with Edubuntu now for less than two weeks and so far, everything I want it to do, it will.  Even if I don't understand what it is I did yet, hi hi

TTUL
Gary
as i said, we cannot have a client-server environment since we do not have a server machine...

then will all our machines act as a server? 

ok, even if we do manage to get a server, what do we do with the hard disk space and processing power of our 35 machines if they are going to be dumb terminals? its a very big investment...

> Each users file is in a /home/user directory, WHERE this /home directory is located don't matter. It could be on any computer or in the server. But it should be pointed to by the server. In this way, from the server, all you have to do is backup /home and all users data is backed up, regardless of where or on what hard drive it is in the building.

did not understand, please re-explain

---

### Post by Duck2006 on 2008-10-25
> dd command is used to copy entire disk

No you can use the dd commands to copy a part of the disk or all of the disk, it just a bit messy to do it that way, as you have to know what the starting block is and the ending block is.

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by Nepherte on 2008-10-25
Edubuntu is not a server version. It is just the educational version of ubuntu, hence the name. The server version of ubuntu is simply ubuntu server edition.

I know it is possible for one computer to download all the updates and let that computer roll out the updates to the other computers. That way you only have to download them once.

It should also be possible to use another home. You only have to specify that other home in /etc/fstab

---

### Post by namdung on 2008-11-04
> **fourthofjuly said:**
> [COLOR="RoyalBlue"]hi all...

at the outset, let me state that i have become a huge fan of ubuntu and now wish to promote it further... its too good an OS to be ignored for sure...

i would like our school kids to start using edubuntu in their computer lab, and i can convince my superiors to atleast use it for the pre-primary kids on a pilot basis... you see, the teachers are already facing severe virus problems with the newly installed XP on our brand new compaq machines and have to spend considerable time in the admin work... we have total 35 systems for the primary section...

the problem is we do not have a server machine and only a peer-to-peer network of the 35 systems (all exactly identical)

1) now, if i install and configure edubuntu on 1 of them, how can i replicate this on other machines?

2) also, what happens when i update / install new software on 1 machine? can i transfer the updates to the other 34 as well? 

3) is there some way to automatically store all user files to a specific location on the LAN so that it can be accessed from any of the machines? in fact all our machines have 250 GB HDD, but hunting for files sometimes is very difficult as teachers are also using these machines & they tend to forget the file location.  

the machine configuration:- Compaq make CPU with Intel Dual core 1.6 GHz, 1 GB RAM, 250 GB HDD, DVD writer, Benq 15" widescreen monitors - all machines are running XP Professional on a peer-to-peer network with CAT6 cabling connected to 2 switches with 24 & 16-ports.

any help will be appreciated...

thanks...[/COLOR]


Edubuntu can be used as a standalone desktop or as a LTSP Server. Since you do not have a Server machine, LTSP is out of the question. I'd still recommend going the LTSP way in the future for all its benefits.

Replicating a standalone desktop to other PCs may not be an easy task and I'd surely want to know how.

An Ubuntu Update Server similar to WSUS is possible. Use our best friend - Google
[http://ubuntuforums.org/showthread.php?t=857749](http://ubuntuforums.org/showthread.php?t=857749)

You may consider building a NAS server to centrally store your files.
[http://www.freenas.org/](http://www.freenas.org/)

If you want AD authentication then consider likewise-open. A graphical version is also available from Add/Remove Programs
[https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html](https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html)

Use Untangle to help protect your n/w.
[http://www.untangle.com/](http://www.untangle.com/)

Good luck!!!

---

