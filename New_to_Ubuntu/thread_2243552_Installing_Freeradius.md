---
title: "Installing Freeradius"
date: 2014-09-09
forum: New to Ubuntu
---

### Post by John_May on 2014-09-09
I don't know if I'm allowed to post this here or not but being that the freeradius forum I found is read only I figured I'd take a shot.  

Is there a decent newbie setup guide somewhere in the world for setting up freeradius with mysql?  I've been at this for a month and can't get there.  There are guides all over the net that contradict each other and I end up stock at various places so I don't really have a specific problem, but I need help.  The end goal would have been to get daloradius working with it.  I can get freeradius working and authenticating, I can get daloradius up and running, but I can't seem to get past the mysql part of it.  It seems simple enough but every guide I go through nets me a different error message.  I bought a daloradius book from amazon which didn't address anything freeradius related at all.  I'm trying to get this working as my employer gave me a budget of "free" and I don't see any other options.

Can anyone point me in the right direction?  I'm this close, but yet ready to scrap this project and start begging for a bigger budget!  :)

---

### Post by nerdtron on 2014-09-09
Just a month on studying Ubuntu and self study isn't quite enough to understand the whole system. Just the basics of the command line takes time getting used to.

Installing Freeradius is not easy (but it is not that hard as long as you know what you are doing)
Important thing you should know:
command line navigation, folder structure, editing files
what is free radius, and also it can be used without mysql (if you want you can do that)
what is mysql and why is it needed in freeradius (good to use mysql for many users and also good for storing encrypted passwords)
what is daloradius (a nice web gui for free radius so that adding users is easy)

I have a guide here which I personally put up a copy for you. This is how I configured a working freeradius server with mysql database and daloradius as web gui.
I mixed a lot of tutorial from the web and made it as simple as possible. If you are having any problems, you can post questions here.
Link on googledocs: [https://drive.google.com/file/d/0B_YStmUAc8zbYlBwSlVjMndxREk/edit?usp=sharing](https://drive.google.com/file/d/0B_YStmUAc8zbYlBwSlVjMndxREk/edit?usp=sharing)

---

### Post by John_May on 2014-09-10
This looks really detailed thank you!  It may be next week before I have time to tackle this again, but I'll try your guide and post back if I come accrost any issues.  

Quick question, I've been using ubuntu 14, should that make any difference?

---

### Post by nerdtron on 2014-09-11
There is a difference. Most tutorials you'll see will probably install daloradius or some form of other web GUI. Apache configuration is different from Ubuntu 14.04 which I haven't tested yet. It will "probably" work on minor changes on the Web GUI part.
Just use Ubuntu 12.04 for now as this server edition is still supported. It will take some time before the internet will update the tutorials for installing free radius on Ubuntu 14.04.

---

### Post by John_May on 2014-09-12
Maybe that's why I've been having such a tough time with this.  I figured they would be similiar.  I'll try this with v12 and post back my results.  Thanks again!

---

### Post by John_May on 2014-09-15
ugh.  so i wiped out and installed v12.  ran apt-get update and upgrade and get a bunch of 


W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu                                                                         _dists_precise_multiverse_binary-i386_Packages  Hash Sum mismatch

then if I try to install freeradius I get this..



Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 freeradius : Depends: libltdl7 (>= 2.4.2) but it is not installable
              Recommends: freeradius-utils but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by John_May on 2014-09-15
Thanks for the help.  Don't waste time researching this I'm done with it.  This should be simple stuff I don't understand why it's not.  My company can fork out some money for the software we need or just leave it alone.

Thanks again tho for trying to help.

---

### Post by John_May on 2014-09-16
HOLY CRAP!  can i say that?  I got it working!

I went back to ubuntu 14 and re-went through it with a fresh mind.  I was missing a couple of things along the way.  I've actually got a user created and a nas created in daloradius and authenticating!  Sorry for getting all cry baby about it, but thanks for the assistance.  I'm sure I'll have questions along the way as I try to get this working with my canopy network.  The documentation for this stuff could be better tho in my defense.  I'm gonna shut it down and go celebrate for a few!

---

### Post by John_May on 2014-09-17
Quick question.  My canopy network requires certificates for this to work.  I'm not sure I understand the points of certs, but I had it working with the sample certs that were created in the certs folder when freeradius was still using clients.conf and the users file for information.  After setting up radius to use mysql which is working to authenticate computers just fine, but now the same test certs don't work on the canopy hardware when they did just a few minutes before.  I get a message about reading the certificate compatibilty.  Do I need to change anything related to certs when using mysql?

---

### Post by nerdtron on 2014-09-17
No idea. I'm not using certs on free radius. Does those canopy devices have a "master" device? I mean, if they can act as a radius client, they can well be act as a radius server, or they have a model that supports being a radius server.

---

### Post by John_May on 2014-09-19
Basically there is an Access Point which serves any number of wireless subscribers modules.  The Access Point acts as the NAS.  Radius authentication gets turned on, enter IP of the radius server and shared secret.  That's it.  Then on the subscriber side you set the username and password, upload the cert to the subscriber, it uses EAPTTLS and then you can chose pap or chap.  If authentication fails the subscriber does not register to the access point.

I confirmed today that if I re-configure freeradius to use clients.conf and the users file instead of mysql then it authenticates normally under pap or chap.  If I set it up for use with mysql it does not.  The error at the bottom of the debugging output states "EAP session for state (there's a long hex number here) did not finish!  Please read [http://wiki.freeradius.org/certificate](http://wiki.freeradius.org/certificate) compatibility.

I wonder what I'm doing wrong.  I'm using the test cert that was automatically generated in the certs folder.  The only file that my subscriber would let me upload to it is called server.pem.  This is the one that works for me when mysql is not involved.  Am I using the cert in the correct way perhaps?  

Here's a list of the changes I make to get freeradius working with mysql.  Again, this configuration allows laptops that don't use certs to authenticate when testing with ntradping.  I can add users in daloradius and they authenticate, I can then delete them and they do not.  So I seem to have the basics working.





Edit /etc/freeradius/sql.conf ...............Change the password and username to match our database


edit /etc/freeradius/radiusd.conf .........Locate the following line and uncomment it (about line 683)
$INCLUDE sql.conf


edit /etc/freeradius/sites-available/default ..........Locate the following line under the authorize section and uncomment it (about line 159)
sql


edit /etc/freeradius/sql.conf ..............Uncomment the line that reads readclients = yes

---

### Post by John_May on 2014-09-19
Ok I got it working.  I had missed uncommenting SQL in the inner-tunnel file.  Thanks for all your help so far!  I have a couple of general questions for you.

I don't get the point of certs, seems like a username and password should be good enough but the canopy hardware I am using requires it.  Everything states not to use the test cert, but this is a controlled environment I am using.  Our installers go out and install a subscriber and program it at a customer location.  I just need an easy way to make sure employees dont install their friends and we need to be able to kick customers off when they dont pay their bill.  In this scenario how would a cert really help me?  My installers will have access to it anyways.  

The other question I have is capacity.  I'll have around 3000 users on this system.  Will the default settings handle that many simultanouse requests (assuming that ever happened) or do I need to tweak anything for a larger network?

---

### Post by nerdtron on 2014-09-19
> Our installers go out and install a subscriber and program it at a  customer location.  I just need an easy way to make sure employees dont  install their friends and we need to be able to kick customers off when  they dont pay their bill.  In this scenario how would a cert really help  me?  My installers will have access to it anyways.

I don't think there is an added advantage of certs. If they can even have copies of certs to other computers that would be a problem so it basically a username/password. If you need to make sure they don't exceed any quota or billing, you can setup groups, rules and useraccounts on the Web GUI Daloradius. This will ensure, for example, a user on the "guests group" can only connect to the access point by 3 hrs every 24 hrs. Just fiddle with the web GUI and you can control pretty much everything, like disable/suspend an account.

> The other question I have is capacity.  I'll have around 3000 users on  this system.  Will the default settings handle that many simultanouse  requests (assuming that ever happened) or do I need to tweak anything  for a larger network?

The freeradius configuration file explain settings like "how many threads on the server" or "how many simultaneous authentication" or "timeout for failed authentications". You can set options in there. That being said, 3000 users is small. I've seen implementation much more users than that. Network traffic for authentication on freeradius is also small so you don't have to worry about that.

---

### Post by John_May on 2014-09-22
Another question.  When I get ready to deploy this I'd like to have a backup server available since I am still learning all of this.  Is there a cofiguration that would authenticate everyone successfully without having to have the usernames and passwords?  My thought would be to have a standby server that could do this and in the event the main server failed I could put the main servers IP into the backup to buy me some time.

---

### Post by nerdtron on 2014-09-22
> **John_May said:**
> Another question.  When I get ready to deploy this I'd like to have a backup server available since I am still learning all of this.  Is there a cofiguration that would authenticate everyone successfully without having to have the usernames and passwords?  My thought would be to have a standby server that could do this and in the event the main server failed I could put the main servers IP into the backup to buy me some time.

Exactly a good admin would do. Basically, all you do is storing your data in the mysql databases. So the setup would be, install a new server with the same freeradius and the same configuration as the current one. Then you need to setup mysql replication on from the first to this second server. It would be like master mysql on the first server and slave mysql on the second one. When the master server fails, all you have to do is let the second server receive all queries

Setting up MySQL master-slave setup though, you need to do a little research. :)

Or if you don't want to do a mysql master-slave setup, you can create a scheduled script that would dump and backup the current mysql database. Then if something happens on the server, you can later restore the database. Downside on this is that restoration may take time and is not seamless.

---

### Post by John_May on 2014-09-24
Do you use reply attributes for configuring the users?  Once authenticated I can add an attribute which creates a username and password on the connecting device, but none of the other reply attributes such as framed-ip-address seem to be working.  If one attribute works they should all work right?  I'm thinking the problem is with my devices, but to understand this properly to add a reply attribute I don't need a check attribute for that also do I?  The other question is for IP addressing do I need to include PPPoE for this or should radius have the ability to add that IP by itself?

---

### Post by nerdtron on 2014-09-24
> Once authenticated I can add an attribute which creates a username and  password on the connecting device, but none of the other reply  attributes such as framed-ip-address seem to be working.  If one  attribute works they should all work right?  I'm thinking the problem is  with my devices, but to understand this properly to add a reply  attribute I don't need a check attribute for that also do I?

Reply attributes depends on the receiving device. Check the device which attributes it supports.

> The other question is for IP addressing do I need to include PPPoE for  this or should radius have the ability to add that IP by itself?
Can you explain this? If you need to assign IP addresses on the radius client shouldn't you use a DHCP server to assign IP addresses?

---

### Post by John_May on 2014-09-25
I didn't explain this very well.  My subscribers get 2 ip addresses, a private management address that we statically assign and a public address that comes from DHCP.  According to my manual these Canopy devices should accept framed-ip-address in the reply but it doesn't work.  I'm trying to figure out if I need to send another other attributes with framed-ip-address to tell the module to take it.  I've seen some examples where people are also sending framed-user and framed-protocol, but I can't seem to decipher whats required.  I'm gonna wipe my server and start over in case I jacked something up along the way.  I'm also going to try using the test certs that come with my devices instead of the ones that freeradius generates.  Past that I'm not sure what else to try.  Support from my vendor is non-existent with this as they want to sell me their $20,000 version of a radius server.  :(

---

### Post by John_May on 2014-09-29
I got it working! Cambium actually logged in to my server and found I missed a cpuple things in eap.conf.  I needed to set the default to ttls and use tunnel=yes.  I also didnt realize that when tesing in the users file that the tabs befor attribites are impprtant.  This is strange to me but it works.  Thank u for all your help! I may have some more questions when I start messing with accounting but u got me in the rigjt direction.  Thanks again!

---

### Post by John_May on 2014-10-14
Does the site wide search work for you?  On mine I can type in the search box but pressing enter does nothing.  There is no search button.  I wonder what I could have done wrong there.

---

