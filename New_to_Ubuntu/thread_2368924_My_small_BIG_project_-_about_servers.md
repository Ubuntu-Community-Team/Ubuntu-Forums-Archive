---
title: "My small BIG project - about servers"
date: 2017-08-16
forum: New to Ubuntu
---

### Post by tweetybirdbrain on 2017-08-16
Hey Folks,

I'm hoping someone can help me out with some information. I've installed Ubuntu desktop 16.04. 

SO maybe I have it all wrong. 

What I wanted to create was: A PRIVATE web server (i think i can use apache), but maybe ubuntu comes with one.  So I can use it to display my web page development projects to myself, while coding on my mac. So if I opened up a browser window, and directed it to that webserver site, I'd get the work I was saving on the server. Then as development some javascript functions need a server call. So would I use that same server? Or have a 2nd server that Node.JS files would sit on? So ti bounces from DOM to [ATTACH=CONFIG]276423[/ATTACH]

See above....also I'm trying to mimic what a bank system may look like. From web page to transaction to databases. 

If anyone can help me understand how these work together, or maybe I'm looking at the wrong things...need to use opensource stuff. 

thanks

---

### Post by cariboo on 2017-08-16
You can install Ubuntu 16.04 server on a spare computer, be aware that it is a command line system, so there isn't a gui. All of what you want will run on the server. The only exception is the mail server, if you plan on opening it up to the world, I'd suggest running it on a separate server. If the system you plan on using has enough resources, you can run the mail server as a VM.

Have a look at the Ubuntu Server Guide [here]("https://help.ubuntu.com/lts/serverguide/")

---

### Post by oldfred on 2017-08-17
Desktop includes the gui and many applications, and there are many flavors.

But you can install server apps to any Ubuntu.
 Some do install a gui, but not the full desktop with all the desktoop gui apps.
Some just 

 Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel
sudo apt install ubuntu-server
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel) 

Normally command line only in server. Some install just the 

[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

Some basics on a server type install. (I save these for my future server)
[https://ubuntuforums.org/showthread.php?t=2364817&p=13660695#post13660695](https://ubuntuforums.org/showthread.php?t=2364817&p=13660695#post13660695)
[http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)
[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)
[http://blog.jdpfu.com/2016/10/04/lamp-server-security](http://blog.jdpfu.com/2016/10/04/lamp-server-security)

---

### Post by sed_faster on 2017-08-17
I suggest use a raspberry pi to this task. The base it is linux and you will have the opportunity the create a more really environment about web server!

---

### Post by mastablasta on 2017-08-17
you can install server on desktop as mentioned before. 

but to avoid the GUi overhead in CPU and GPU usage i suggest:
install ubuntu server
install OpenSSH
install whatever else you might need (Apache, Mysql, PHP = LAMP stack?!)

now you can connect to server via SSH to install whatever other things you need.

you can also install in virtualbox and do develppment there (server will do fine with 256 or 512MB ram and 6-8 GB disk image size). it is easier since you can just take a snapshot and then restore it when things go wrong. using BTRFS or ZFS for linux file system should be able to do the same.

---

### Post by SeijiSensei on 2017-08-17
You can install Apache on your Mac, too, and avoid a second server.

For instance, [https://jason.pureconcepts.net/2014/11/install-apache-php-mysql-mac-os-x-yosemite/](https://jason.pureconcepts.net/2014/11/install-apache-php-mysql-mac-os-x-yosemite/)

---

### Post by 1clue on 2017-08-17
Just use your mac. Apache2 installs fine on that. Mac OS X is a BSD UNIX underneath. Only the GUI and a few other services are apple-specific.

To ensure that your apache is truly private you can reject all port-80 traffic which is not from localhost, or you can create one or more Windows/Linux VMs and have your mac only take port 80 from localhost and your VM network, to test various other operating systems.

I strongly recommend using some sort of source code control like git, and be sure to do individual features using feature branches. It gives you a lot better history management than just randomly changing whatever and hope it all works.

---

### Post by 1clue on 2017-08-17
Typically developers have a copy of the website checked out in git, or something similar. They're working on the development branch, and they check out/create a feature branch to make a specific change.

You work on your workstation whatever it is, with a web server or application server running to make it functional. You have a browser or five, possibly from multiple operating systems, to choose from.

You work on your project to get it functional, then commit and issue a pull request so that a teammate can review your changes and pull them into the development branch. Once that happens, a company-internal development server automatically pulls changes from git (because they were merged to the common development branch) and the company-local test server is updated with your changes and the changes of whoever else committed and merged since the last time.

Once the development work is stable or nearly so, you branch make a new stable branch. This branch only gets fixes for problems, not changed features. Once the testers have found the site to be good, the production server pulls that new stable branch and you're on to developing the next changes again.

So what I'm getting at is there's usually only one computer necessary per developer. Everything can be done with just that.

---

### Post by tweetybirdbrain on 2017-08-18
So if I'm reading the threads correclty...I need to...

Please NOTE: my definition of server - may not be common - or accepted standard definition. I use the TERM server for lack of the proper name. According to a friend of mine, server is the actual physical box, but what exactly is Apache or server sitting on if not a server? the program itself, i mean its not really an OS, maybe it is. I'm not quite sure of terminology. So what is the term used for "Apache web server", because its not the box, its the software driving it / hosting it. 

1. Over-write Ubuntu Desktop with Ubuntu server (this hopefully will speed up boot time, it seems to boot slower than windows 10, i5-2500 with 8GB of RAM, installed on a 120SSD, with GT210(1GB) GPU)
- notes - I maybe getting things confused***** so do please correct me if my logic is erroneous. 
a)I need a server to host a database - mySQL (opensource) and MongooseDB (opensource) - I did some checking and apparently financial institutions only use 1 massive database, although data is grouped into tables, sorted and so on
b)I need a web server (Apache - unless someone can think of a different one) - development, now would I put ALL of the following on 1 web server, or 1 server per function (see roman numerials below)
(i) development server (Apache ?)- housing ASP.net / .NET / react / angular / bootstrap (maybe)
(ii)development server (Apache ?)- housing - Android emulator
(iii)development server (Apache?)- housing - iOS emulator
c)an accessible server for published portfolio [Apache?](development additions hidden, only finalized - or maybe accessible - desirability of this function to be determined)
d)CLOUD servers (TORRID?) Since we live in an age where there are spikes in demand for access to web sites, copying server into a cloud environment for a period of time, the appending data and deleting un-needed servers would save on bandwidth(no?)...but would coping the DB server into cloud make it faster? (this notion is to emulate real life) - so do I also copy all the development servers into cloud (I think I can use TORRID - unless someone knows a better open source one)
e) EMAIL - it would be nice if the email server could be in the same box. 

So theoretically I would 6 - 8 server (software) running doubled via cloud so 12 - 16, all in 1 box. But I also want to mirror them, so it mitigates data loss, or have any array rebuild itself, should a drive fail. While program software would be housed on a 120GB SSD, data would be housed on 7200rpm HDD's. The question becomes, black / red / enterprise - seagate / ironwolf - seagate. 

I should also mention: Currently I have 3 TB of space available (WD digital 2TB black / 1TB black), I have been asking for the goods on HDD's, and I'm thinking of replacing the 1TB with a 2TB, I have 6 Sata ports available. Maybe I should pull out the 120GB SSD, and replace with 6 x 2TB Blue's / Red's / Black's all at 7200 rpm. 3 working 3 for mirror back up. which would allow for 6TB's each. Splice the drives by server function 1TB each or so. 

Your thoughts?

Thanks a bunch.

---

### Post by mastablasta on 2017-08-18
linux might boot slower because windows 10 hybernates by default and doens't really shuts itself off. if you hybernate linux it will also "boot fast". still server does boot a lot faster than desktop.

if the services you intend to run are not too demanding you can run them on same server (i mean OS here) or you can also cretae virtual servers to separate them. if they are of more demanding sort then you might need separate hardware.

server computers are specific hardware made with servers in mind. servers are also programs that offer/serve services (e.g. Apache)

mirroring is not backup. corrupted file will result in corrupted mirrored file, so you will end up with 2 bad files. how does that help? using ZFS or BTRFS (both can take snapshots)+ mirror is a different story. but RAID does protect against disk failure.

but you've asked for a development server. for that you can just use virtual machines (such as virtualbox) no need to get 20.000 EUR of server hardware just to develop the applications. just mnake sure you have a descent CPU and plenty of RAM.

---

### Post by 1clue on 2017-08-18
Definitions:
[LIST]
[*]Server
[LIST]
[*]A computer (hardware or VM) whose primary purpose is to provide services to applications or users on remote systems.
[*]An application designed to provide some sort of useful information.  (apache web server, mysql database server)
[/LIST]

[*]Service
[LIST]
[*]An application which is configured to run without a GUI interface, typically started on system boot and stopped on shutdown.
[*]Apache web server and mysql database server are typically run as services, although some servers can also be run as regular applications for debugging purposes.
[/LIST]

[*]Desktop or workstation or laptop
[LIST]
[*]A computer whose primary purpose is to allow a human to perform tasks.
[/LIST]
[/LIST]

Under normal circumstances your web application would use a server (hardware system or VM which emulates a hardware system) to host the web site you're developing.

Ubuntu server is the same core functionality as Ubuntu Desktop, without the GUI and a lot of other stuff, but adding some different stuff. There is no reason why you can't have Apache and Mysql running on Ubuntu Desktop, or on Windows 10, or on Mac OS X. 

Developers typically use a single box (could be a desktop, laptop, Raspberry Pi or whatever) to host their "server" applications. You can install a LAMP stack (Linux, Apache, Mysql, PHP) right on top of Ubuntu Desktop and nothing will break. You could install tomcat and grails and java if your development uses that sort of thing. Or Node.js.

The difference between a desktop and a server is the intended use and the software installed on it.  A system can be a server and a desktop at the same time, the only real problem with that is if the user reboots or fills up the hard drive with junk while other people are trying to use the services that system provides.

---

### Post by 1clue on 2017-08-18
Backups:

Generally for development you don't use backups or replication unless the backups and replication are part of what's being tested.

Generally speaking production servers have multiple types of backups for different purposes.
[LIST=1]
[*]Database backups save the state of your database at a certain time in a restorable fashion. This is necessary because just backing up files risks that the database be copied during some sort of commit, which means your data is going to be corrupted.
[*]Another backup might save the state of your web site. In a truly production setting this will be done with a source code repository like git. The git 'server' (e.g. github.com) will probably have backups, but the fact of the site pages and schema existing on some other system is a real backup.
[*]Another backup might archive files that the application references.  For example, if you have a photograph or video archive then a database will likely be used for metadata but the actual binary images will be stored in flat files on the drive.
[*]If you have web hosting, then very likely your host provider (linode.com, armor.com, etc) will take nightly snapshots of your VM. This is a last-ditch backup in case something horrible goes wrong or all your other backups failed for some reason. It will restore the machine state as of the time of the backup. I always thought this was ridiculous until I actually needed it. There is no analog of this backup for real hardware.
[/LIST]

At any rate, your production box and your development box will be two separate pieces of hardware, and depending on your project size or speed requirements the database server may not be on your application server.

---

### Post by tweetybirdbrain on 2017-08-19
so.....just out of curiosity.....and this may not be an ubuntu question, maybe more of a server question. can I put the servers on a 120gb SSD, and use 2x HDD's in raid for data? or would I use 5x HDD's in raid (with consideration that the raid can rebuilt itself).

---

### Post by mastablasta on 2017-08-21
> **tweetybirdbrain said:**
> so.....just out of curiosity.....and this may not be an ubuntu question, maybe more of a server question. can I put the servers on a 120gb SSD, and use 2x HDD's in raid for data? or would I use 5x HDD's in raid (with consideration that the raid can rebuilt itself).

sure. you can do what you want.

just remember, RAID is not a backup.

---

### Post by 1clue on 2017-08-21
> **tweetybirdbrain said:**
> so.....just out of curiosity.....and this may not be an ubuntu question, maybe more of a server question. can I put the servers on a 120gb SSD, and use 2x HDD's in raid for data? or would I use 5x HDD's in raid (with consideration that the raid can rebuilt itself).

You seem to still have a misunderstanding of what a server is.

In pure networking terms, a network connection consists of two applications communicating with each other across a socket. There a side that listens for connections and a side that asks for a connection.  The side that listens is the server. The side that asks is the client.

Any computer which supports networking can be either a client or a server, or both at the same time.

A Raspberry Pi, which is a credit-card sized computer, is way more than enough to be a server. I built a stratum 1 time server from one, it has only a SDHC card as a disk, nothing else but a network connection. I'm only bringing it up because it's the cheapest commonly known computer with everything you need built-in. You can buy one for $20.

Speaking with respect to your project, absolutely anything you have with a keyboard, monitor and mouse, which can run a GUI version of Linux, can be your Linux development box. For development purposes you will only have yourself as a client, which means you're making one or two clicks every few minutes, and everything that supports networking can handle that.

---

### Post by 1clue on 2017-08-21
And I'd not bother with raid for data. If your data is worth tons of money then you put in RAID and have regular backups. If you're on a dev box then your data is a few megabytes of stuff you cooked up to exercise all of your code, and you can rebuild it as often as you like with a script.

---

### Post by sp40140 on 2017-08-22
Ubuntu desktop edition: Is os with gui and commonly used to install on many types of machines.
Ubuntu server edition: Is os without gui but with almost all or the rest of the ability of desktop version. Reasoning is simple, servers just need to run application. People don't touch them unless they are doing maintenance (as opposed to desktop where people actually perform their daily tasks all day). 
The meaning of term "server" changes quite a bit depending on context. However, generally it means a computer with OS optimized for server tasks. And runs large applications which serve lots of people/other applications, like sql server. 
Most of the applications can be run on desktop version. And in your case it wouldn't make much difference. However, when you are talking about enterprise workloads every little bit matters. So, the more load you put on a machine a more tailored server you should have.

So, for you, you can run either desktop or server editions of Ubuntu on your hardware. The reason people here suggest you run server is that it will free up resources (by not running gui) and make them available to other applications you want to run.
You can run RAID (or other file systems) on either desktop or server edition.
Hope this clears up "server" thing to you.

---

