---
title: "Install Your Own Forum with Ubuntu"
date: 2007-01-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Bruneauinfo on 2007-01-04
Build Your Own Forum with Ubuntu and Simple Machines Forum  

by Bruneauinfo

Want to run your own forum service from your home or office? Tired of paying for web hosting services that don't give you the server and storage specs you want? The following guide will give you a crack at being a newbie web host yourself! And you can do it all with free, open source software. 

This document contains the instructions necessary to bring a Simple Machines Forum into existence on your own personal Ubuntu web server. Don't have a web server? I'll show you how to do that too. 

I will be updating this as needed and as suggestions come in. Please feel free to contribute if you find errors.

*Please note: I'm no Apache guru, nor am I a Linux Ubuntu, MySQL, PHP, or any other kind of computer  guru. The following guide was written by me. It is instended to be a fun way to learn about web hosting. If you are wanting to operate a webserver in a mission critical or production environment please reference the proper resources provided by the Apache Software Foundation for creating a secure webserver environment. I do not offer support in any form for this guide other than I'll do my best to answer questions, and I'll make corrections to the information as I find errors or as they are pointed out to me and I am allowed to make tham. *

*Also note: Unless your server is going to be located on the Internet with its own public, static IP address you will need to get a Dynamic DNS hosting service to host your DNS records. This is very easy to do. I use DynDNS, but there are many DNS hosting services available. If you don't understand in the least bit what I am referring to go to [www.dyndns.com](www.dyndns.com) and do some research. I used their Custom DNS package because I wanted to have a top-level domain for my website. You will need to acquire some knowledge about Dynamic DNS and how to configure it before you will be able to access your web server dependably from the Internet. I talk about about Dynamic DNS in this guide, but understanding how it works requires a seperate How To in itself. But don't let that discourage you. It's a challenge that can easily be overcome on these forums.* 

*Resounding note: I reinstalled 15 times before I got all my 'Penguins' in a row. And I don't mean Apache either, I mean the entire system. So if you're going to build a web server using these instructions you'll be dedicating a machine to this task. If you think you may want to opt out of this later and go back to what your system was used as previously make sure to backup all the data on your machine before beginning your install of Ubuntu If you already own an existing web server and intend to use this forum guide for a produciton server please install this software on a test server first before moving it to a mission critical server. This is a guide for hobbyists and enthusiasts, not necessarily for IT professionals. If you are an IT professional or otherwise proceed at your own risk. *

I installed this software on an AMD Socket A 1.6 GHz Duron computer with a single stick of 512 Meg DDR400 RAM. I used an 80 gig IDE drive and two 40 Gig SATA drives for storage. A powerful GFX card would be a waste, so I just installed an old 2x AGP card to conserve RAM for the software. Low power requirements meant I could go with a cheap 400 watt power supply. I used a standard Lite-On CD-RW drive for installation. I used a PCI NIC that was compatible with my distribution of Linux.

Needless to say this has created a very beefy web server, storage-wise. So far my forum has been up for a week. It took me about three weeks of blood, sweat, and tears to figure this all out. So if you don't get it on the first try I recommend you get up and try again. If you have questions please contact me through the forum. I'd be more than glad to try and share what little I really know about hosting a web server with you. And perhaps we can learn more together. 

(Optional) I also set up a Smoothwall router with three NICs for handling the Dynamic DNS updates and so that I could put my web server in a DMZ. This isn't required. But if you're interested in building a secure firewall router from an old PC check out [www.smoothwall.org](www.smoothwall.org) and download their latest Express 2.0 edition which is what I used. 

(Default) You can just as easily use a standard off the shelf router between your Ubuntu server and your Internet connection. I get more into this later in the guide. 

Now, to your forum.

Here's what you need to do -

After you build your server machine you need to get your operating system installed. 

I used Ubuntu 6.10 Desktop, Alternate Install disk at [www.ubuntu.com](www.ubuntu.com). If you love a different distribution of Linux or you don't like the newest version of Ubuntu and decide to go with something else don't have high expectations of this guide working perfectly for you as written. Your installation may require numerous modifications. For simplicity sake I recommend following these instructions as closely as possible on your first install. Where items are listed as “(Optional)” you may go with the “(Default)” setting instead where I try to describe alternative methods to the best of my ability. I recommend that once you arrive at a working web server/forum following these instructions that you start your experiments and modifications. 

(Optional) Ubuntu 6.10 Desktop notes: This is the Desktop alternate installation disk. I use the desktop version because it is easier for Linux newbies like myself. The alternate install disk can be found under the download section. My server uses the PC i386 version. If you're not familiar with the download section of the Ubuntu website do some exploring. Figure out where on the planet earth you are going to download your copy of the OS. Once you do this you will see the various options available. To get the options I have listed here download the ISO image that allows  other installation options. I use what is called Logical Volume Management – or LVM. This allows for an easier hard drive storage upgrades in most cases. 

The standard desktop install CD does not allow you to use LVM. I like to use LVM because it makes increasing your computer's storage capacity much easier. If you don't want to use LVM then you can go with a standard install disk. The installation instructions for the OS will be different that what I describe here.

To get the downloaded ISO onto a CD properly you need to get a piece of software that burns ISO images. Search on [www.google.com](www.google.com) for ISO Recorder and download and install this piece of software on a Windows based PC. There are other program as well that can burn ISO images available.

Install Ubuntu using the Text Mode. When you get to partitioning let Ubuntu do it for you. However, if you know how to use LVM then create an ext3 partition about 100 to 200 MB in size and mount the /boot directory on it. Also, create a swap partition that is at least twice the size of your RAM. I recommend making it twice the size of the maximum RAM you'll ever expect to install on your server. Then make an LVM group from your remaining disks and create the necessary volumes to mount /  (i.e. That is the root of the file system) to. I also mount /var/www on it's own volume. What this does is allows me to make just the space where the forum will be stored larger or smaller later if I need to using LVM. (If you want to know more about LVM ask.)

(Optional) I also run an ftp server on my machine. So I have a /ftp folder mounted on a 70 gig volume and /var/www mounted on a 60 gig volume. This is handy for backing up and restoring the forum's files over the internet or over the local network. I used vsftpd. However since an ftp server isn't required I won't go into the details of its installation here.

The rest of the Ubuntu installation is pretty much standard. There are enough installation guides available for more details on installing Ubuntu. If you have a specific question please feel free to ask.  

Once Ubuntu is installed log in and open a terminal window. Open the terminal under > Applications > Accessories > Terminal, and then type the following command to install the software required for a LAMP server:

sudo apt-get install mysql-server apache2 php5 php5-mysql libapache2-mod-php5 php5-gd

LAMP server – Linux, Apache, MySQL, PHP. 

(Optional) Go into the folder /etc/php5/apache2 where you will find the php.ini file. This file needs to be edited in two places that sets the maximum size of a post – 'post max filesize' and the maximum size of an attachment – 'upload max filesize'. The specific names of all the required configuration settings are in the general installation requirements listed on Simple Machines Forum homepage at [www.simplemachines.org](www.simplemachines.org). Click on Download, then click on System Requirements. Changing these two settings is required if you want forum members to upload files larger than 2 megs. I set them each for 1000M (which is 1 Gigabyte) because my forum is a closed forum and attachments are easier to controll with the very few members it has. Also, many of the posts are made from a LAN which has considerably faster upload and download speeds than the Internet. If your forum will be public then keeping the default settings may be plenty.

As far as I can tell all other requirements and recommendations by SMF in the PHP and MySQL config files are okay by default for my needs. In any case I address them in this How To. 

Next, in a terminal window type the command 

mysql_install_db 

to configure the root password for the MySQL server. Make sure to read the output that is produced as a result of this command. You will find the instructions for setting the MySQL root password in that output. Since the MySQL server is on the same computer as the forum you use the first of the two methods and type it precisely the same way. (Don't put quotes around your password. And use a real password, not the word 'password'. Write your password down so you don't forget it.)

Using the 6.10 version of Ubuntu allows you to install MySQL Administrator from the Add/Remove... feature integrated into the Ubuntu desktop. Click > Applications > Add/Remove and then do a search for MySQL Administrator. Install this application now so that you can configure the MySQL database.

One of my security failures in this process is that I can't get SMF to install with anything except the root user name and password I specified in the mysql_install_db step. If you know how to give smf a less privileged status that will still work, please let me know. 

Notes: According to the SMF website I do know that the user account the forum uses needs at least the following priviledges:

SELECT, INSERT, UPDATE, DELETE, ALTER, and INDEX. 

And, during installation and conversion:

CREATE and DROP privileges.

However, my ignorance is only a bump in the road towards your forum, and not a roadblock. 

Next, point the server's web browser to SMF's website at [www.simplemachines.org](www.simplemachines.org) and download the most recent version of SMF. You need the .tar version. It downloads very quickly with a broadband connection. There is a readme file in the folder you download that should tell you how to continue with the installation. Go ahead and read that file before proceeding. My 'version' of the instructions follows:

What I do is extract every single file and folder from the download except for that single readme file to the following folder: 

/var/www 

If you get an error open a terminal window and type the following command then try extracting the files and folders again:

sudo chmod 777 /var/www

I do not create a folder called “forum” to extract to, because I don't know much about configuring Apache. If someone has some configuration examples or guides please advise.

Now here's the tricky part. Do not run install.php until my instructions direct you to. 

You presently have a LAMP server with a forum installed on it. But before running the install.php file it is very important to work out a few more steps. It is kind of important to have the server computer located where you intend it to “serve” from. In my case I connected it directly to a Smoothwall firewall router that I built. I plugged the server into the DMZ port for added security for the LAN. However, a standard router port will work on a budget  Linksys type standard issue $50 router just fine. However, if your ISP has not provided you with a static IP is it very handy to have a router that supports Dynamic DNS. A Smoothwall router supports this feature without the need for additional software or modifications. This will be very important for setting up DNS with a Dynamic DNS service so you can get to your web server from the Internet. A Smoothwall router is optional, but there are other options. Some budget routers support Dynamic DNS. Read into your router's configuration documentation to learn how to set this up. Another option was suggested below:

Daniel15 from Simple Machines Community Forums suggests that running ddclient on your server will update your Dynamic DNS host just as well. 

I do not know how this program works and have not tried it myself. So use your favorute search engine to research it if you decide to use this option. 

It is also important that the web server have a static IP on the LAN or DMZ port depending on which one you use. If your router is set up to use DHCP for its clients either turn DHCP off and assign static IPs to your workstations or assign the Web Server an IP outside of the range of the DHCP server. This should be a private IP range address.

So get everything connected and get all the IP information for all parties configured. If you don't know how to configure Network settings on your router or Ubuntu computer take some time to learn how to do this. There are numerour How Tos on the subject, and ask for help on the Ubuntu forums.

From a workstation that is not the server but is connected to the same router and type the IP address of the server in a browser address bar and press “Enter” on your keyboard. If everything is configured right you should now see the forum setup screen for your SMF forum. If you don't then try restarting the server and repeat the instructions in this paragraph. If it still doesn't work then check your services and make sure that Apache and MySQL are running. 

If all went according to plan you should get a message that the permissions of several files and folders need to be changed for the configuration to continue. So open a terminal window on the server computer and make these changes. All of these files and folders are in the folder /var/www. So do the following:

cd /var/www

then use the following commands to change their user permissions so SMF can have permission to read, write, and execute them:

sudo chmod 777 attachments

Use this command for each file and folder listed until all the files and folder permissions are changed as specified in the list. 

Now go back to your workstation and refresh the browser screen. If all goes well you should be at the next page of configuration. It asks you to fill in some information. Name your forum, etc.

Of special importance -

If you've done your homework and set up a Dynamic DNS service online you should have a web address for your web server – like [www.superserver.com](www.superserver.com) or something like that – and you should have your router set up to update their DNS servers when your ISP changes your IP from time to time. 

Make sure you type the web address of your forum in the box requesting the URL for the server and not the LAN IP address or Loopback IP address. Example: [www.superserver.com](www.superserver.com) Typing in the LAN IP is wrong. You will use port forwarding in your router to forward HTTP requests to the router. However, if you use the LAN IP for the URL things just won't work and the forum will get confused and you won't be able to log in. 

Here is some more about where I'm a bit stumped about using MySQL properly. This is the same “bump” in the road I was referring to earlier, and not a roadblock. The next step however is useful for confirming that your MySQL server is indeed working. So you should do it if nothing else to confirm MySQL is up and running and ready to go.

I use MySQL Administrator (start it up under the Applications Menu) and log in from the server machine at localhost, root, and then use my root password that I specified for the MySQL server. If all is well and you can log in then close it and skip the next paragraph.

If you're a MySQL Pro and you want to help me troubleshoot this then here are the details: Once I log in I can create a user accound for the forum and even give it the required permissions. But I'm still having trouble here when I use this login account information  in the install.php forum setup screen. Luckily, I can try this over and over and over till I figure it out. But I finally lost patience after 30 tries.

My workaround is to simply use localhost, root, and the MySQL root password in the SMF configuration form and it just works. However, I'm pretty sure this is a security no-no. 

If you can't figure it out how to do it correctly use my workaround, because it is very effective. However if I ever figure it out – or you do – there is a place in the Forum Admin section where you can change these settings – (no doubt using extreme caution as you do it.)

Finish up configuring your forum and set an administrator username and password. You should be done and you should see the forum on your workstation with a bright red warning telling you to delete the install.php file. My experience is that running install.php causes the config screens to hang from the beginning of SMF configuration. I was not able to get SMF to recognize that the files and folders that need to be chmod'ed to 777 were indeed possessing the proper permissions. So frustrated, I just reinstalled the entire system and tried again. So unless you know a lot more about php and MySQL than I do (I know just about diddly) I recommend avoiding running install.php again at all costs unless you have some knowledgable assistance. 

Workaround: Again according to Daniel15 the data base files can be cleared and install.php can be run again. 

Note: I don't know how to do this so I've left it out of these instructions. Read up on MySQL administration for more information. 

If you need to reconfigure something go into the server folders/files that constitute SMF in the /var/www directory and look at the configuration files. They are plain text and can easily be edited with a text editor such as gedit or vim. Just make sure to start the text editor with su priviledges. And it would be wise to make a backup of a file before you alter it just so you can go back. Linux newbies tend to overlook this precaution. 

cp filename  filename.bakup

Now you need to log in to your router and add an item to the hosts table in your configuration:

[www.superserver.com](www.superserver.com)      192.168.xxx.xxx 

The web address should be your server's web address, and the IP address should be the static IP you gave your web server. This way, users on your LAN will be able to reach your server using the www URL rather than having to type the IP address. And it also gets around your router's anti-spoofing rules should it have any. If you don't find a Hosts table entry then your router probably isn't that sophisticated in which case I would only worry about it if you can't reach your computer with it's web address from inside your LAN.

Also, go to the port forwarding section of your router and set it up to forward all requests for port 80 to your web server's static LAN IP. See your router's configuration documents for more information. My experience has been that port forwarding just works. If it doesn't work for you then the problem is not port forwarding, it's something else.

If your Dynamic DNS is set up correctly in your router then you should be good to go. Get a friend who's not on your LAN to try out your www address and make sure the web server can be reached okay.

Note: It sometimes takes a couple days for Dynamic DNS services to get your DNS records setup. So if it doesn't work right away give them a few days or log in and check on the status of your account. 

Your now a forum owner. Woot!!!

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-01-08
Good Stuff Bruneauinfo! I like! Thanks for such a detailed and thorough instructional breakdown of  directions. I've got my forum up off the ground -- Thanks again for your hard work!

---

### Post by DC@DR on 2007-01-08
Thanks for this guide...It's definitely helpful for me since I'm thinking of moving my forum from web hosting service to my own server :-)

---

### Post by SuperMike on 2007-01-13
Here's some other choices for forums besides SMF.

* vBulletin - the guys at WickedFire know forums REALLY well and they prefer this over other. UbuntuForums.org uses vBulletin.

* phpBB - an earlier form of vBulletin before it was forked

* Vanilla  (*new* and *cool*)

* Orca (*new* and uses some AJAX)

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-01-13
Thanks for some alternative suggestions Mike -- I'll be sure to check them out!

---

### Post by Bruneauinfo on 2007-01-19
> **k|d<FuNkY>FrY said:**
> Good Stuff Bruneauinfo! I like! Thanks for such a detailed and thorough instructional breakdown of  directions. I've got my forum up off the ground -- Thanks again for your hard work!

You're very welcome. It was a challenge and a pleasure. So far my forum has been up for almost a month with few problems. It's been an eye opening experience thus far. 

I'll probably be moving the forum to the Ubuntu Server distro at a later date once I get enough hardware together to build a second system. When I do I'll probably add a guide for that method as well.

---

### Post by Almighty on 2007-01-21
I have been using SMF on a Dapper server for about 6 months now. Even though it was a tough battle getting my FTP set up right, all I can say is it has been awesome! The more I admin the site the more I love Ubuntu and Linux.

I am so glad I went this route.

---

### Post by Bruneauinfo on 2007-01-21
> **Almighty said:**
> I have been using SMF on a Dapper server for about 6 months now. Even though it was a tough battle getting my FTP set up right, all I can say is it has been awesome! The more I admin the site the more I love Ubuntu and Linux.

I am so glad I went this route.

this is good to hear. i had been looking at Invision, but i saw SMF and figured it looked as good and had plenty of options. i was particularly interested in being able to attach large files to posts. having services available so that i could do this to my heart's content was going to cost a lot. Ubuntu made getting a LAMP server set up so easy.

what problems did you have with ftp?

---

### Post by solsie on 2007-01-23
I did basically the same setup as yourself, but am using PHPBB on my site.  I found there are several addons that you can put on their to customize further.  I did have a question.  I was interested in setting up a FTP Server with UBUNTU and was wondering if you had a document on this?  In particular a front end on the server that will allow the creation of the account, folder, password, etc..all from the same front end. Not like in windows, where you have to make the folder, create an account, and then make link for ftp(using several different modules)..Also is it possible to set up ftp accounts that dont actually have access to logging into the server, just ftp folder?

Solsie8-)

---

### Post by Bruneauinfo on 2007-01-24
setting up ftp with ubuntu is actually quite easy. 

sudo apt-get install vsftpd

the way ftp works is that when you log in to the ftp server it gives you access to the /home folder of the username and password you use to log in.

so what i did was this created the group and called it powerftp	

- sudo groupadd powerftp

then i created a folder called /ftp 

- sudo mkdir /ftp

(you can call the folder anything and put it anywhere, but i'm sure there are some exceptions to where you want to do this.)

then i gave the folder 775 access		

- sudo chmod 775 /ftp

(this gave access to the group and it made it so non-group members could see and download files)

i gave the group 'powerftp' ownership of /ftp		

- sudo chown root:powerftp /ftp

then i created users and made them members of powerftp and made /ftp their home	

- sudo useradd -g powerftp -d /ftp username1
- sudo useradd -g powerftp -d /ftp username2
- sudo useradd -g powerftp -d /ftp username3

then i assigned each of these users a password

- sudo passwd username1

[Pressed "return" and then typed in the password per terminal instructions]

(i did this for each username.)

then i created usernames that had /ftp for a home, but did not own /ftp because they were not a member of the group "powerftp"

- sudo useradd -d /ftp guestusername1
- sudo useradd -d /ftp guestusername2
- sudo useradd -d /ftp guestusername3

i assigned them passwords the same way. 

i access my ftp server via windows at work and it is quite easy to do even with the basic Windows Explorer interface. if i want to share a large file with a friend of mine in another state i just give them a username from the second list. then i change the permissions on a specific file or folder i wish to share to 777. 

i don't know how secure this method is, but it works.

another thing you will have to do is change a few settings in the vsftpd.conf file. look for it under /etc

i commented out 

anonymous_enable=YES 

by putting a hash mark in front of it unless you want anonymous users logging into your server

i allowed local users by uncommenting 

local_enable=YES

once i did that i saved the file and restarted the server.

now you should be able to log into the server with any ftp client, IE explorer, etc.

---

### Post by solsie on 2007-01-24
cool deal.  I did that and rebooted the server.  I used [ftp://servername](ftp://servername), but get nasy message in windows saying no access and in dos, host not found.  Any ideas?

S

---

### Post by solsie on 2007-01-24
OK, I have a dns issue.  I can resolve that.  I tried at the server itself adn was able to login as the users.  I noticed that i made a user as in this step
sudo useradd -d /ftp/test1 test1 

When i log in as this user, i am able to do a cd .. and go out of the home folder.  How can i ensure that this user can only see test1 adn not leave that folder?

---

### Post by solsie on 2007-01-26
I installed SMF on my UBUNTU box and everything works fine on the box, but I noticed that connecting from lan pc or wan pc, the screen is not the same as from the server itself.  It is basically a white page with my wording on it.  I posted a ticket on the SMF Forum, was just curious if you might have seen this?

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-01-26
> **solsie said:**
> I installed SMF on my UBUNTU box and everything works fine on the box, but I noticed that connecting from lan pc or wan pc, the screen is not the same as from the server itself.  It is basically a white page with my wording on it.  I posted a ticket on the SMF Forum, was just curious if you might have seen this?

Have you played around with the theme settings at all? What theme do you currently have installed? Default?

---

### Post by Bruneauinfo on 2007-01-27
> **solsie said:**
> I installed SMF on my UBUNTU box and everything works fine on the box, but I noticed that connecting from lan pc or wan pc, the screen is not the same as from the server itself.  It is basically a white page with my wording on it.  I posted a ticket on the SMF Forum, was just curious if you might have seen this?

okay, what folder did you install SMF to? did you follow my instructions or the instructions from SMF? SMF's instructions assume that you already have a web page on your web server and that you are going to have a button somewhere on your webpage that links you to the folder /var/www/forum

in my instructions i assume you have no website at all and are using this server for a forum _only_.

so if you went through the forum configuration steps and gave your forum a web address that was the loopback address you're going to have this problem because the php5 generated pages are absolutely DEPENDENT on having that address be the forums location on the network.

---

### Post by Bruneauinfo on 2007-01-27
> **solsie said:**
> OK, I have a dns issue.  I can resolve that.  I tried at the server itself adn was able to login as the users.  I noticed that i made a user as in this step
sudo useradd -d /ftp/test1 test1 

When i log in as this user, i am able to do a cd .. and go out of the home folder.  How can i ensure that this user can only see test1 adn not leave that folder?

i have another topic on ubuntu forums showing the exact same concern. AFAIK this server config is for trusted users only. i would suggest loggin in as your regular user name and creating a file in the /ftp/test1 folder and seeing if logging in with your user test1 allows you to change, open, or delete that file. 

then run this experiment again except this time create a file in the / folder and see if your test1 user can navigate to that file and read, write, or delete that file.

---

### Post by Daniel15 on 2007-01-28
> **solsie said:**
> I installed SMF on my UBUNTU box and everything works fine on the box, but I noticed that connecting from lan pc or wan pc, the screen is not the same as from the server itself.  It is basically a white page with my wording on it.  I posted a ticket on the SMF Forum, was just curious if you might have seen this?

It sounds like you used 'http://localhost/' as the URL, rather than the IP address. Open your Settings.php file, and check all the URL's. If they have 'localhost' in them, edit them so they're correct.

---

### Post by foy1der on 2007-03-28
Thanks for the awesome guide, Bruneauinfo. It has made setting up my forum a bunch easier. Although I did come across a problem and this time, google wasn't my friend this time and didn't produce anything useful. I am getting this error when I point another computer on my network to my server for the first time.
> The installer was unable to detect MySQL support in PHP. Please ask your host to ensure that PHP was compiled with MySQL, or that the proper extension is being loaded.

Click here to try this step again.

It is my belief that I followed the guide to the letter. Any help is greatly appreciated.

---

### Post by Bruneauinfo on 2007-03-28
if you're using the exact same version of Ubuntu as i am - 6.10 Desktop - and NOT server edition - then...

did you delete the install.php file as the forum software instructed i.e. did you get through the forum installation steps okay? were you then able to log in to the forum on the forum server but not a local workstation?

---

### Post by foy1der on 2007-03-29
I did not install the forum yet. I am at this step
[QUOTE=Bruneauinfo]From a workstation that is not the server but is connected to the same router and type the IP address of the server in a browser address bar and press “Enter” on your keyboard. If everything is configured right you should now see the forum setup screen for your SMF forum. If you don't then try restarting the server and repeat the instructions in this paragraph. If it still doesn't work then check your services and make sure that Apache and MySQL are running.[/QUOTE]

Additionally, I am using Ubuntu Desktop 6.10. I still get the error when I enter the forums address (ie 192.168.0.2) from the forum itself.

---

### Post by Bruneauinfo on 2007-03-29
well, if you note from what i said at the beginning of the guide - i had to install this thing many times before i got it right. 

you may need to try reinstalling MySQL and PHP5

also make sure that you put ALL of the install commands in.

---

### Post by foy1der on 2007-03-29
I am using Ubuntu Desktop 6.10, and I did have a few problems getting php5 mysql apache2 ect to all install at the same time like you did (sudo apt-get install {EVERYTHING}). I had to do it piecewise instead. I will try reinstalling everything tonight and let you know how it goes. Thanks for the response.

---

### Post by stokedfish on 2007-03-29
Just a side-note, for all you guys who think that SMF is an open-source forum...well, it's not.

[http://www.simplemachines.org/about/opensource.php](http://www.simplemachines.org/about/opensource.php)

Its license has never been accepted by the OSI and therefore it should not be considered an open-source software.

Anyway, we use SMF in our community as well and I love it...just some info!  ;)

---

