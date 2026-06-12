---
title: "Ubuntu for large school"
date: 2006-12-14
forum: Programming Talk
---

### Post by evolvedlight on 2006-12-14
I was thinking about how a school might indeed initiate a large switchover to Ubuntu.

Let me give you an example.

Large school, just over 1k pupils in 7 year groups. Around 5 rooms of computers plus around 60 laptops. So 200ish computers. They want to run them as full clients, not thin clients, and want each pupil to be able to work from any computer. Windows is just too slow and the pupils keep getting around the restrictions. 

Stakeholders: The pupils need to be able to use the internet and an office suite. They also need to be able to access their work from home, with an ftp site or through a conventional http site. They need their own home directory where they can store work. 

The teachers want to be able to use office/internet. They want to be able to get work out of a pupils home directory, and be able to put course material inside that directory. They want to be able to show their screen on all the screens in a classroom, exhibit a certain pupils screen to the rest of the class, lock the screen (so all attention is on the teacher, not the computer), annotate on the screen, watch a screen in the room or display a number of them in a grid. They want to be able to allow/block internet access, to all sites or just to a single site. They want to be able to launch a process on all the computers in a classroom, eg, make all the computers go to the same website. 

Administrator: Wants really easy setup. Possibly wants to remotely turn all computers in the school on. Remote management (install/uninstall software) or update computer. Wants to have automated backup solution, and wants management to be trouble free. Wants internet blocking/unblocking and a filtering solution. Wants to be able to see who's on each computer at any time, etc.

How the installation process should work:
[LIST=1]
[*]Admin puts server cd in drive
[*]Admin chooses network option, or leaves them as defaults
[*]Admin chooses what services the server should offer to the school
[*]Admin imports users and defines permissions (in groups), with sensible defaults
[*]Chooses applications that users should be able to use
[*]Applications downloaded
[*]Client cds put in workstations
[*]Client Cd installs basic ubuntu, then finds the server and sets itself up
[*]All the packages are distributed P2P through the network to reduce strain on server
[*]System is ready!
[/LIST]

I don't think there is any existing solution that does all of that

Does anybody have any comments on this? Would this be useful? Does this already exist?

Steve

---

### Post by Tomosaur on 2006-12-14
This can all be done with the server install CD for Ubuntu, and the client can be any linux distro you choose. The user setup stuff can be done fairly easily through some clever scripting, and the remote operations (screen locking, process launching etc) can also be done with a script or two. Shouldn't be too hard to set up for yourself really.

---

### Post by Hendrixski on 2006-12-14
I thought of a business model recently where one would set up a non-profit organization with the aim of offering Edubuntu to a less financially fortunate school district, and local community organizations.   One could apply for grants, and could install Ubuntu CE for local church groups, or Edubuntu for families, and tell them what the long term goal is, and that they could donate (and use it as a tax write-off).  With early donations give one computer with Edubuntu to a school, for them to evaluate it, and you can write about the great results on further grant applications.  Then install it on a few computers.

Then do the same for local community groups (many of which you will have gotten in contact with by installing Ubuntu CE, and Edubuntu).  And after a year or so re-register as a for-profit company with a resume.

Sorry it's not technical, but it fits the thread.

---

### Post by evolvedlight on 2006-12-14
> **Tomosaur said:**
> This can all be done with the server install CD for Ubuntu, and the client can be any linux distro you choose. The user setup stuff can be done fairly easily through some clever scripting, and the remote operations (screen locking, process launching etc) can also be done with a script or two. Shouldn't be too hard to set up for yourself really.

True, but not the remote control stuff.

What I really want to stress would be the absolute ease of setting up the system. I mean, for all the client computers, you put the CD in **and thats it**

Basically, it would people with no experience of Ubuntu (sys admins at schools) install a "perfect" ubuntu system.

---

### Post by pmasiar on 2006-12-14
> **evolvedlight said:**
> Large school, just over 1k pupils in 7 year groups. Around 5 rooms of computers plus around 60 laptops. So 200ish computers. They want to run them as full clients, not thin clients, and want each pupil to be able to work from any computer. 

[http://www.edubuntu.org/](http://www.edubuntu.org/) was designed **exactly **for this. Using thin clients and student's directories on the server (easier to admin and backup). Boot from network, no disk or any other media on client. To upgrade stations, change boot inage and reboot - all clients upgraded.

Ask them: What is the business reason to run PC as full clients? Tell me **what needs be done**, not how to accomplish it: I am paid to figure out how to make it happen, right? :-)

> 
Stakeholders: The pupils need to be able to use the internet and an office suite. They also need to be able to access their work from home, with an ftp site or through a conventional http site. They need their own home directory where they can store work. 

The teachers want to be able to use office/internet. They want to be able to get work out of a pupils home directory, and be able to put course material inside that directory. 

Yes, all the above. Using ssh and putty from home to upload homework. You did not seriously thought about plain unsecured ftp, did you?

> They want to be able to show their screen on all the screens in a classroom, exhibit a certain pupils screen to the rest of the class, lock the screen (so all attention is on the teacher, not the computer), annotate on the screen, watch a screen in the room or display a number of them in a grid. 

They want to be able to allow/block internet access, to all sites or just to a single site. They want to be able to launch a process on all the computers in a classroom, eg, make all the computers go to the same website. 

This is tricky. Is it a deal breaker? Some kind of screencast or shared editor. Does it exist for Windows? How much it costs?

You may want to re-ask this in server/admin section. The only part to ask in programming forum what application allows sharing screens and screencast - and I am sure edubuntu people are aware of this need, look like common feature request.

---

### Post by firebadger on 2006-12-14
Vnc ?

---

### Post by evolvedlight on 2006-12-14
Hey

I think that I gave out the wrong impression in the initial post.

**There is no school. I am proposing a new software project**

There are several reasons why a thin client is not suitable for a school such as mine
[LIST]
[*]The school does not want to purchase more hardware (server to handle the thin clients)
[*]The machines are powerful generally, they will run better locally
[*]The wireless network could not handle the traffic for all the laptop thin clients
[/LIST]

However, if you disagree, please do.

The aim of the software project is EASE OF USE.

That means all point and click, and no custom scripts, etc. Just a **really easy transition**

pmaisar: "Yes, all the above. Using ssh and putty from home to upload homework. You did not seriously thought about plain unsecured ftp, did you?"

I am talking about 11 year olds. I would not really expect them to know how to use ssh and putty. But, as part of the package they would be allowed to select which methods they wanted to enable. 

With the screen sharing part, it does exist for Windows, there are several solutions, some better than others.

Comments? Flames?

S

---

### Post by gummibaerchen on 2006-12-14
Hey,

I think an alternative to the Thin-Client solution would be great :)

Many schools have computers which are quite capable for Linux.

In my school we have at least 1 Ghz and 256 + 128 MB RAM which runs acceptable with Windows 2000. It would be a waste of the clients power and of money for a server to centralize all this.

What I would suggest to this, a possibility to put your profile on an USB-Stick, for example when you want to take the Notebook somewhere in the forest or to an external presentation.

> **evolvedlight said:**
> I am talking about 11 year olds. I would not really expect them to know how to use ssh and putty. But, as part of the package they would be allowed to select which methods they wanted to enable.
Sorry, but I think they should just learn! With WinSCP it's fairly easy to open a file-transfer connection to a server. I don't think it's any more difficult than a normal FTP-Client.
You could write all the instructions on an A6 page with Arial 14px.

BTW: I wouldn't know how to open such a connection with Putty, but can't be that hard either :)

---

### Post by pmasiar on 2006-12-14
Some kind of secured access. Look at old good tools like midnight or gnome commander. They can be used for other things (like file management) and with menu, to do custom commands. 

One of the little rascals will find out how to sniff out passwords of the others, and will go on rampage. Don't tell I did not warned you. :-)

**UPDATE:**  Sniffing from unsecured ftp of course. ssh, sftp, scp are fine. Obviously.

To access your data anywhere without server? Put them on USB Flash Stick and don't lose it. :-)

---

### Post by gummibaerchen on 2006-12-14
> **pmasiar said:**
> One of the little rascals will find ut how to sniff out passwords of the others, and will go on rampage. Don't tell I did not warned you. :-)

Is this still so easy? I remember this hole from my school :) (win2k + some linux)

---

### Post by dwblas on 2006-12-14
Check TightVNC to see if it will do what you want [http://www.tightvnc.com](http://www.tightvnc.com)

---

### Post by gummibaerchen on 2006-12-14
> **dwblas said:**
> Check TightVNC to see if it will do what you want [http://www.tightvnc.com](http://www.tightvnc.com)

What for? Obviously he doesn't want every Client to create a VNC Session to the Server, and for File-Transfer? No.

---

### Post by pmasiar on 2006-12-14
> **gummibaerchen said:**
> 
In my school we have at least 1 Ghz and 256 + 128 MB RAM which runs acceptable with Windows 2000. It would be a waste of the clients power and of money for a server to centralize all this.

I thought about your post a little (what a concept: "thinking before posting" :-P) and tried to see the big picture.

I believe we have it wrong. We are shooting ourselves in the foot **by being reasonable**. Of course we know that PC with 1GH/256MB RAM is able to run full Linux client. But year or two from now it is between Linux and Vista. Year from now is pretty  soon, comparing to speed which school board can learn, make decisions, and change :-) Did you checked how much memory Vista requires? 1GB, better 2GB for eyecandy and multiple applications. MS has no problem with forcing all users to upgrade machines. Why it is a taboo for us? If we restrict our options by being "reasonable", competition without those restriction will win, and users will suffer.

Question is not **if** they want to upgrade: **they have to upgrade anyway**. Choice is between 10 servers with 4-6GB RAM, or 150 "fat desktops" with 1GB RAM. And Vista is more secure ==> harder to administer.

But I do not see why you want all network be wireless. Desktop are not moving anywhere, why not connect them by wire to gain speed?

---

### Post by evolvedlight on 2006-12-14
> **pmasiar said:**
> But I do not see why you want all network be wireless. Desktop are not moving anywhere, why not connect them by wire to gain speed?

Sorry, the 200+ desktops are wired, its around 70 laptops that are wireless

---

### Post by Pobega on 2006-12-14
The only problem is that schools need computers for one thing that Linux doesn't have; Photoshop! Most schools that have computer have typing classes, programming classes, and graphic design classes. The problem here is I'm not sure how well Photoshop emulates in Wine, or if a school would really be devoted to trying to teach groups of kids to run Photoshop through Wine (most people who take computer classes in schools are highly retarded.)

But other than that, this does seem very useful for a school setting. So long as you're in a computer-oriented school, that is.

---

### Post by dwblas on 2006-12-14
> What for? Obviously he doesn't want every Client to create a VNC Session to the Server, and for File-Transfer? No.Why not?  Your post says nothing that is useful.  Here is what I found on the web site.> What is TightProjector?

TightProjector is a software that can transmit the screen of a particular computer to other computers in the same local-area network. The data is transmitted continuously, in real time.

Usage examples:

    * broadcasting a presentation to multiple networked computers
    * showing a class of students operations performed by a teacher> Automatic SSH tunneling on Unix.
 File transfers in Win32 version. You can updload files from your local machine to the TightVNC server, and download files from the server to you computer.I am no expert but even if it doesn't suit the needs, it is a starting point for what are reasonable expectations to be able to use existing software.

---

### Post by macogw on 2006-12-14
[http://yhspatriot.yorktown.arlington.k12.va.us/](http://yhspatriot.yorktown.arlington.k12.va.us/)
Yorktown High School in Arlington, VA is all Edubuntu, I believe.  I'm going over there tomorrow for YHSLUG [http://yhslug.tux.org/](http://yhslug.tux.org/)  It seems like it's working well for them.

---

### Post by dwblas on 2006-12-14
> one thing that Linux doesn't have; Photoshop!Has anyone here tried GimpShop.  From the web page Gimpshop 2.2.11 deb package for Ubuntu Linux [http://plasticbugs.com/?page_id=294](http://plasticbugs.com/?page_id=294)  Even if it's sort of close, it would be useful for many, including me.

---

### Post by slavik on 2006-12-14
A sysadmin should not know anything about Ubuntu to be able to install it perfectly?

At work, we are moving ALL windows computers to Active Directory, the people in charge of the AD server know things of which I never heard of. Even to deploy windows with good/secure control requires you to know Windows, it isn't just put in a WindowsXP cd then install and you're done, you have to know what you are doing.

As for what was described with the monitor locking and such ... When I went to HS, there was this program called Syncroeyes. We as students were able to quickly notice that the teacher was monitoring our screen (mouse pointer would come to a crawl and the icon in the tray would change).

This can be achieved with VNC and SSH, along with some specialty software (putting messages on the screen and such). As for students saving work, a big ol' server with NFS. :)

---

### Post by Ben Sprinkle on 2006-12-15
> **evolvedlight said:**
> and the pupils keep getting around the restrictions. 


Eheheheh, what can I say? :P
(Windows 2000 laptop right now at school)

---

### Post by evolvedlight on 2006-12-15
Yes, TightProjector could definately be part of the software. It is however only for windows currently, but that can change

I'm going to do some mockups over the weekend on what the whole software package would look like and work like

Steve

---

### Post by gummibaerchen on 2006-12-15
> **dwblas said:**
> Why not?  Your post says nothing that is useful.  Here is what I found on the web site.I am no expert but even if it doesn't suit the needs, it is a starting point for what are reasonable expectations to be able to use existing software.

Ahh ok, you meant VNC for Teacher -> Pupils, yes, there VNC is probably the easiest solution.

So maybe YOU should have also told us what for :) I thought for connection from Home etc

But as evolvedlight said, it's only for Windows, so it's not any use at the moment here :(

---

