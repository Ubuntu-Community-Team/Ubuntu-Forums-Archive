---
title: "[SOLVED] Exploring Linux for a Lab - Newb questions"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Atagegan on 2008-09-07
Hello,

I am exploring Linux options for our laboratory and would appreciate any input / advice.  I have been tasked with updating our current data collection methods in the lab.  I have a decent amount of time and have always wanted to learn more about Linux.
 
The Situation:
We currently have 2 (soon to be 3)laptops running windows xp sitting at each lab station.  We are lucky to be able to connect to the internet (bad university wireless connection in the basement).  Data is stored independently on each laptop, rarely getting backed up.  We usually burn DVD's of data to move the files to our own laptops when we need to do write ups or number crunch.  Grad student 1 usually doesn't know about grad student 2's data and vice versa.
You get the picture.  Its a mess, inefficient, unorganized, non-centralized and in danger of losing data.

The Vision:
We will have 3 lab computers hooked on a network to a main server station.  The server stores data from each as well as having a backup system.  This computer is also connected to the internet.  We have the option of getting a dedicated IP for this computer as well so it would host a website for our research group.  Finally, each student (3) and the professor (1) has their own personal laptops.  It would be nice to set up a VPN(?) so that we could dial into the lab server from either the home, office or from a conference and access the data.

Questions:
1)  Overall is this possible with Ubuntu.

2)  Is it possible for the Lab computers to have Windows XP and the server be linux?  I know Matlab and Labview have versions for each OS, but I also know our professor likes Excel.  Or would it be better for all the lab computers to be Linux?  Since most of it is Data files that are exported into excel anyway.

3)The personal computers connecting via VPN are Mac, Windows and Linux systems.  Is it possible to connect all of these to the server?

4) Specifically the lab computer / server interface.
a)  Is it better to have the lab computers store data locally and the server goes and 'fetches' this data when making backups.

or b)  Is it better to have the lab computers store data directly on the server, and then that gets backed up periodically.

This (4) is probably my main concern right now.  How to best connect the 3 lab station computers to a server that is central and holds all the data, as well as the ability to back it up.  Any advice would be greatly appreciated as far as setup, linux versions, backup structures and any links that might be useful.

Also, how painful is it connecting all the personal computers with different OS to the server to access data?

Helpful info:
Data is usually from oscilloscopes or files holding large amounts of data on voltages/currents/Temp as well as Image files from digital cameras.

We don't need to do any heavy computational analysis.  Its enough to just access the data files and copy it to our personal laptops to make graphs, etc.

Thanks for reading, and sorry for the length.
~B

---

### Post by Xiong Chiamiov on 2008-09-07
I don't have extensive knowledge of any of this, but I'll see what I can contribute.

> **Atagegan said:**
> 
1)  Overall is this possible with Ubuntu.

Yes.

> **Atagegan said:**
> 
2)  Is it possible for the Lab computers to have Windows XP and the server be linux?  I know Matlab and Labview have versions for each OS, but I also know our professor likes Excel.  Or would it be better for all the lab computers to be Linux?  Since most of it is Data files that are exported into excel anyway.

Yes to the first, and you could use OpenOffice.org instead of MSOffice.  Better to have the lab computers be Linux or Windows?  Depends on how much sysadmining you want to do.

> **Atagegan said:**
> 
3)The personal computers connecting via VPN are Mac, Windows and Linux systems.  Is it possible to connect all of these to the server?

You should be able to.  No experience with this, though.

> **Atagegan said:**
> 
4) Specifically the lab computer / server interface.
a)  Is it better to have the lab computers store data locally and the server goes and 'fetches' this data when making backups.

or b)  Is it better to have the lab computers store data directly on the server, and then that gets backed up periodically.

I would tend to have the server share a folder via Samba, then have the clients write directly to that as a network drive.  Otherwise, the lab computers always have to be on, for the server to get info from them.

> **Atagegan said:**
> 
Also, how painful is it connecting all the personal computers with different OS to the server to access data?

You'll be using [Samba]("http://delicious.com/xiong.chiamiov/samba") to transfer information.

You could also consider using the laptops as [thin-clients]("http://en.wikipedia.org/wiki/Thin-client"), although I recently was considering that in my home (yes, I have enough computers to make this feasible), and decided I just didn't want to deal with it.

---

### Post by panhandle on 2008-09-07
1) yes
2) Different OSs are fine
3) yes
4) b

---

### Post by RequinB4 on 2008-09-07
I can't really walk you through setting up the server, but here are a few answers to your questions (comments in bold):

> **Atagegan said:**
> 
Questions:
1)  Overall is this possible with Ubuntu.

**Let's just say yes.**

2)  Is it possible for the Lab computers to have Windows XP and the server be linux?  I know Matlab and Labview have versions for each OS, but I also know our professor likes Excel.  Or would it be better for all the lab computers to be Linux?  Since most of it is Data files that are exported into excel anyway.
[B]
Sure... If i've understood what you've described the server would be mostly storing your files and perhaps hooking some up to the internet, so it wouldn't matter what type of file it was (think: most servers on the internet are linux...).  If you are going to be doing work/data collection on the "server" then you would need to make sure the file formats for Matlab and Labview are compatible for different operating systems, as well as compatibility for whatever input device you are using.  If you like excel, use excel - thats kind of independent of data storage.[/B]

3)The personal computers connecting via VPN are Mac, Windows and Linux systems.  Is it possible to connect all of these to the server?

Yes - see above.

4) Specifically the lab computer / server interface.
a)  Is it better to have the lab computers store data locally and the server goes and 'fetches' this data when making backups.

or b)  Is it better to have the lab computers store data directly on the server, and then that gets backed up periodically.

[b]Depends on the function of the server and how secure you want to be.  In an ultra secure setup you would have the "working, in progress files" stored on the laptop, then every arbitrary time interval (day? week?) have everything backup.  Then in a longer time interval do a double backup on the server, etc.  The problem with (a) is that its feasible for the server to overwrite good backups with not so good "in progress" files.
The problem with (b) is that you don't have a copy on the laptops.[/b]

Also, how painful is it connecting all the personal computers with different OS to the server to access data?

**Ever gone to an internet website?**

Helpful info:
Data is usually from oscilloscopes or files holding large amounts of data on voltages/currents/Temp as well as Image files from digital cameras.

We don't need to do any heavy computational analysis.  Its enough to just access the data files and copy it to our personal laptops to make graphs, etc.

**More reason for the "in progress" backup system I mention above**

Thanks for reading, and sorry for the length.
~B

---

### Post by DGortze380 on 2008-09-07
Please forgive the brief suggestion. If this sounds like a feasible solution for you let me know and I can do a more detailed write-up tonight.

If it were me, I would do the following. A simple, easy to administer flat network.

Linux on all laptop work stations. (could modify this to work with windows if there is specific software you need).

One Server to be used for data storage/backup.

You'll need to layout the network and decide if wireless is necessary or if you can hardwire each workstation. If it were me, I would use a router and static IPs, although you could potentially use a simple switch.

Server would need a static IP and certain ports forwarded to it from your IT dept. if applicable.  Set up SSH on the server, along with valid user accounts for each user in the lab (or a single user account).

Workstations need two accounts each. One admin type account with full sudo access and one user account.

Users can log into any workstation on the single user account. If you are only using one user account on the server, you can set up each workstation to automatically connect via ssh and you will have a folder on the desktop that is similar to "Network Places" in windows. The anything stored in this folder (or subfolders) will be on the server. Users can also ssh into your server remotely, this is were multiple user accounts is useful for security purposes.

That was a little all over the place, I'm just kind of thinking "out loud". But it will give you some ideas, if it seems feasible, let me know I'll put something clearer and more specific together for you.

---

### Post by Atagegan on 2008-09-07
Thanks for the speedy responses!

Xiong Chiamiov:

Thanks for the tip with samba, that seems pretty feasible.  I also hadn't thought about the lab comps having to be on all the time.  That would pretty much suggest option a) with samba.
Also looked into the thin-clients.  Interesting but not required in this case.

RequinB4:
I'll have to consider this 'work in progress' more closely as far as our needs are concerned.  We certainly don't need to be ultra-secure, however.
Thanks for the input.  I'm certainly not looking for detailed instructions how to set this up.  More of an overview and suggestions on different approaches that I can look up to see if they meet what we are looking for.

DGortze380:
I don't remember if we have window's specific software or not.  Ill have to ask bossman, as it is really up to him if he wants linux or xp on the workstations.  

I know we can get a Static IP and ports opened from IT as other groups have it currently set up.  So thats not a problem.

You did raise a question for the network layout that I hadn't thought of.  Wireless would be the prefered connection.  Dear god we have enough cables already.  I also know there is a hardwired box in one of the rooms to access the internet.

1) Is it just a matter of connecting the 4 comp's wirelessly to a router?  and then the router to the internet box?

2)  Or do you need to have the 3 workstations connect to a router, connected to the server then another connection out of the server to the internet?

~B

---

### Post by DGortze380 on 2008-09-07
> **Atagegan said:**
> Thanks for the speedy responses!

Xiong Chiamiov:

Thanks for the tip with samba, that seems pretty feasible.  I also hadn't thought about the lab comps having to be on all the time.  That would pretty much suggest option a) with samba.
Also looked into the thin-clients.  Interesting but not required in this case.

RequinB4:
I'll have to consider this 'work in progress' more closely as far as our needs are concerned.  We certainly don't need to be ultra-secure, however.
Thanks for the input.  I'm certainly not looking for detailed instructions how to set this up.  More of an overview and suggestions on different approaches that I can look up to see if they meet what we are looking for.

DGortze380:
I don't remember if we have window's specific software or not.  Ill have to ask bossman, as it is really up to him if he wants linux or xp on the workstations.  

I know we can get a Static IP and ports opened from IT as other groups have it currently set up.  So thats not a problem.

You did raise a question for the network layout that I hadn't thought of.  Wireless would be the prefered connection.  Dear god we have enough cables already.  I also know there is a hardwired box in one of the rooms to access the internet.

1) Is it just a matter of connecting the 4 comp's wirelessly to a router?  and then the router to the internet box?

2)  Or do you need to have the 3 workstations connect to a router, connected to the server then another connection out of the server to the internet?

~B

Your network is going to be a small part of a larger one. Your server will be connect via static IP to IT's network which connects to the internet. For wireless internet you're probably going to want to look at a switch connected, connected to a Wireless Access Point and connect the server to the switch. Although, in that set up, I'm not sure how port forwarding would work to the server.

---

### Post by Atagegan on 2008-09-07
One other thing i just thought about.  We already have the workstation laptops, but would need to acquire the server computer.  I assume we don't need anything really fancy for the server job, just a mid range processor and a couple big hard drives.  Any recommendations on the makeup of the server would be appreciated.  Especially if there is something I may have overlooked.

~B

---

### Post by hyper_ch on 2008-09-07
the server doesn't need to be powerful at all for just 3-4 clients... I guess you could go with a P4 1Ghz, 256 ram, and then harddisk as much as you need...

---

### Post by Atagegan on 2008-09-07
> **hyper_ch said:**
> the server doesn't need to be powerful at all for just 3-4 clients... I guess you could go with a P4 1Ghz, 256 ram, and then harddisk as much as you need...
Thanks hyper_ch,

Thats what I was expecting, just wanted to be sure.

---

### Post by hyper_ch on 2008-09-07
of course it doesn't hurt to have a more powerful machine ;)

---

### Post by anewguy on 2008-09-07
One thing that needs a little clarification:

Are you manually entering the data from all this equipment, or is it automated?  If it's automated, do you use a specific piece of software to do the communications/capturing?  

This is important, since you may want to leave Windows on the equipment that is acquiring the data unless you can prove via testing that all of the data can be captured by an application in Linux.

I used to work in IS for a VERY large medical laboratory, and all of the interfacing to the equipment there was via in-house written programs, using syntax, etc., very specific to the computer and OS it was running on.  If this is the case for you, may I suggest installing Linux as a dual-boot on one of the machines for now so you can try to get your application(s) working first.

Dave :)

---

### Post by Atagegan on 2008-09-07
Dave,

We don't do anything automated thats in-house programing, as far as I know.  Most of the manual stuff is just Word and Excell, which I know OpenOffice can handle.  Sometimes, however, we port in a lot of data to an excel spreadsheet and run some pretty complicated functions on the data.  Last time I tried OpenOffice Calc, it just didnt have the capabilities for that.  Has that changed?

The rest of the data collection is via Labview on photomultiplier tubes and the software provided with the Tektronics Oscilloscope, which Im almost sure is supported for linux.  Matlab is also used, mostly for plotting.

Anyway, thanks for the point.  Even if I suspect we dont need to worry to much about this, I'll definately be asking just in case.

~B

---

### Post by Atagegan on 2008-09-07
Yah, I hear ya.


We just always have old comps floating around the University that people wanna get rid of.  If we can use one of those and not be too picky, even better.  Just don't wanna have it so slow that its unbearble to work on.

~B

---

### Post by Xiong Chiamiov on 2008-09-07
It's amazing what you can do with old machines.  For instance, I have a gateway machine (the 2nd newest computer in this house, actually) that's got an 800MHz P4 and 384 MB RAM.  Right now I've only got it acting as a fileserver and running torrents (rtorrent ftw!), but I've had it also hooked up to my TV to play my anime.  It stuttered a bit too much with H264 stuff, but plain old DivX it did just fine.  And that was on Xubuntu, too, so I'm sure I can get better performance out of it with lighter stuff.

Linux has made my local Craigslist *way* dangerous for me.

---

### Post by anewguy on 2008-09-08
Oops - don't now if what I just did on my computer passed through - a big mess up.  Oh well.  At any rate, while off topic to some degree, I thought I'd add that I'm running 8.04, compiz, wireless, a old HP scanner and a HP printer on a generic 500mhz PIII with 512mb and an ATI 9250 video card.  It's no speed demon on anything - I log of times on line I get the gray "I'm a little busy" screen effect.  Anything I do off-line is minor but all seems to work fine without delay.

Dave :)

---

