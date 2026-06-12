---
title: "HowTo: Install NX Server on Ubuntu Server 7.04"
date: 2007-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Ashex on 2007-05-12
This guide shows you how to install FreeNX on Ubuntu Server Feisty Fawn 7.04 and also how to install the client.


First up, we need to grab the packages from NoMachine (This first time around I tried to use the Seveas repositories, but I had some trouble getting it to work, so we'll just use the .deb packages from Nomachine).

First up, lets create a directory to drop these all into:

```

mkdir freenx && cd freenx
```

Now to grab the required packages:

[NX Node](http://www.nomachine.com/download-node.php?os=linux)
```
wget http://64.34.161.181/download/2.1.0/Linux/nxnode_2.1.0-22_i386.deb
```

[NX Client](http://www.nomachine.com/download-client-linux.php)
```
wget http://64.34.161.181/download/2.1.0/Linux/nxclient_2.1.0-17_i386.deb
```

[NX Server](http://www.nomachine.com/select-package.php?os=linux&id=9)
```
wget http://64.34.161.181/download/2.1.0/Linux/AS/nxserver_2.1.0-22_i386.deb
```

Now that we have all our packages, lets install them.

```
sudo dpkg -i nxclient_2.1.0-17_i386.deb && sudo apt-get -f install
```

```
sudo dpkg -i nxnode_2.1.0-22_i386.deb nxserver_2.1.0-22_i386.deb
```

*Note: we install NX Client first since NX Node and NX Server depend on it*

We now have our packages installed, next up we want to install the desktop environment, I'm a Kubuntu user, so we'll use KDE.

```
sudo apt-get install kde
```

Apt will now install a whole swatch of packages, so go make some tea :)

When that completes, we're going to open up the nx configuration file to make some tweaks.

```
sudo /usr/NX/etc/node.cfg
```

Locate the following line:

> #SSHD_PORT=22

Uncomment it to look like this:

> SSHD_PORT=22

This configures NX Server to tunnel through ssh for security.

Next, we're going to locate this line:

> #COMMAND_START_KDE=startkde

and uncomment it to look like this:

> COMMAND_START_KDE=startkde

We have now enabled a KDE connection.

Now that we have modified the configuration file to what we desire, we're going to run the nxsetup process.

> sudo /usr/NX/scripts/setup/nxserver --install debian
*thanks to beemer for that note*



Congratulations! We have now setup NX Server! to test it out, we can connect to it from another computer.

I used the NX Client from the [Seveas Repositories](https://wiki.ubuntu.com/SeveasPackages).

To setup the nx client, add the following repositories to your sources.list file.

```
sudo nano /etc/apt/sources.list
```

> 
deb [http://mirror2.ubuntulinux.nl/](http://mirror2.ubuntulinux.nl/) feisty-seveas freenx
deb-src [http://mirror2.ubuntulinux.nl/](http://mirror2.ubuntulinux.nl/) feisty-seveas freenx


now install nxclient

```
sudo apt-get update && sudo apt-get install nxclient
```

now start nxclient by hitting alt+f2 to bring up the run dialoug box and type in 'nxclient' then hit enter.

I believe the NX Connection Wizard will appear, choose a hostname and specify the IP of your server

[img]http://img512.imageshack.us/img512/1834/nxclientsettings1xk0.png[/img]

Click Next, and then check the box to enable SSL encryption. Click Next again then finish.

Enter your login credentials, and the NX client will now connect and present you with a login session!

[img]http://aycu05.webshots.com/image/15284/2002701077315542473_rs.jpg[/img]

---

### Post by SteveGodfrey on 2007-05-15
I've followed your guide but "nxsetup" is nowhere to be found on my system!

I assume it should be in '/usr/NX/bin'?

---

### Post by stoneattic on 2007-05-15
Same deal here.  No nxsetup to be found.

---

### Post by beemer on 2007-05-15
Here's what I did to get the server portion installed and running (on Kubuntu Feisty):

Setup the 'work' path to get it installed
$ mkdir freenx;cd freenx

Get the necessary deb's to install
$ wget [http://64.34.161.181/download/2.1.0/Linux/nxnode_2.1.0-22_i386.deb](http://64.34.161.181/download/2.1.0/Linux/nxnode_2.1.0-22_i386.deb)
$ wget [http://64.34.161.181/download/2.1.0/Linux/AS/nxserver_2.1.0-22_i386.deb](http://64.34.161.181/download/2.1.0/Linux/AS/nxserver_2.1.0-22_i386.deb)
$ wget [http://64.34.161.181/download/2.1.0/Linux/nxclient_2.1.0-17_i386.deb](http://64.34.161.181/download/2.1.0/Linux/nxclient_2.1.0-17_i386.deb)

Found out that nxclient needed a certain lib to install (skip if you already have) so I grabbed that
$ sudo apt-get install libstdc++2.10-glibc2.2

Now I installed the packages in the order listed by Ashex
$ sudo dpkg -i nxclient_2.1.0-17_i386.deb
$ sudo dpkg -i nxnode_2.1.0-22_i386.deb 
$ sudo dpkg -i nxserver_2.1.0-22_i386.deb

Found the node.cfg file in a different location than what Ashex specified, but edited that per his instructions
$ sudo vi /usr/NX/etc/node.cfg

Ran the install of nxserver telling it to use debian
$ sudo /usr/NX/scripts/setup/nxserver --install debian

Grabbed the status to make sure it was running
$ sudo /usr/NX/bin/nxserver --status
NX> 900 Connecting to server ..
NX> 110 NX Server is running.
NX> 999 Bye.

From there I went to my win box and installed the nx client for windows from NoMachine.com

It ran perfectly for me.  I haven't tried installing the nx client for linux.

Beemer

---

### Post by Ashex on 2007-05-15
my mistake guys, I edited the guide reflecting beemer's steps. I'll double check when i get to my house.

---

### Post by SteveGodfrey on 2007-05-17
Fantastic, now working a treat.

Thanks

---

### Post by Brazilian Joe on 2007-05-25
I have installed kubuntu 7.04 on a VMWare guest. 

I haven't found the package I need to fix the broken dependency.
Any advice is welcome...

I have received the following error:

root@rainforest-kubuntu-vm:/home/tfreire/nxclient# apt-get -f install nxclient
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nxclient: Depends: libstdc++2.10-glibc2.2 but it is not installable

---

### Post by milkyspit on 2007-05-25
Got the server installed fine, I think... it seems to be running without incident.

On my client Windows machine, however, whenever I try to connect to the server I get the authentication successful message, then get the desktop window with 'MX' logo, then the logo disappears... then after quite a while a single box of what appears to be the desktop background appears, and that's it. I can terminate the session correctly but have found no way of correcting the above problem. My NX connection is completely unusable due to this issue.

With the same client I can connect to NX on a CentOS machine just fine.

Has anyone reported something like this, and if so, could somebody kindly point me in the right direction? What the heck is going on!?!

Please excuse if this is a dumb question as I'm a Ubuntu newbie... but quite truthfully, if I can't get NX working it will make Ubuntu a lot less desirable for me. Can someone please help? Thanks in advance!

:confused:

---

### Post by Quietlife on 2007-05-28
**[COLOR="Red"][SIZE="2"]ALERT[/SIZE][/COLOR]**

The "FREE" no-machine node software is not FREENX.

This install will get you the "free of cost" "nx server desktop" edition NOT the unlimited open source FREENX.

---

### Post by dasbooter on 2007-05-29
I have just come from Suse and KDE and am now trying Ubuntu and gnome so I am wondering how you would avoid installing kde and start a gnome session instead. Initially installing NX was a pain in the butt on 
Suse (that was a couple of years ago) but lately it has been very simple using the packages in the Suse repos and I had no problem generating and sharing my own keys, I hope Ubuntu will be as simple. I was also wondering what happened that caused the initial thread starter to use the nomachine packages instead? I was sort of planning on using the Seveas packages I have read they have less bug and are more secure.

---

### Post by kevdog on 2007-05-29
To discover my problems using only the seveas repositories consult this thread:
[http://ubuntuforums.org/showthread.php?t=457633](http://ubuntuforums.org/showthread.php?t=457633)

I cant make it work, the details are thoroughly documented in the post above!

---

### Post by dasbooter on 2007-05-30
Hmmm right off the hop in the other thread I can see that you are taking steps that I did not have to undertake concerning the user NX. I know the user NX is created and involved in the process but I never had to manually alter anything in ssh to get it to work on Suse. I can see on my suse configuration that ssh is using pam for authentication. I remember having some issues when trying to add other users to freenx, ones that were not created when the system was set up. Other issues I have had in the past were with trying to install both freenx and the No machine packages on  my system. When one doesn't work you naturally try the other. At that time No machine had made parts of the system open source and so freenx installations were sort of a hacked together assortment of scripts to get things going with the nomachine technology. Incompelete removal of the packages may conflict or there may be conflicts due to the changes each package makes to your system. Sorry I cant be more helpful...I do have a working suse configuration with freenx if you want me to have a look at anything on my system.

---

### Post by Eazy© on 2007-06-06
Great guide, but I think you did not finish it ;)

> **Ashex said:**
> Click Next, and then check the box to enable SSL encryption. Click Next again then finish.

Enter your login credentials, and the NX client will now connect and present you with a login session!
How do I know what to put in there? How do I create a password and user? I tried with my user "eazy" and my pass but it don't work. Why is it always so difficult to find out how to create a user and set a pass on remote desktop-apps?

Edit:
Don't know what the problem was, suddenly it just worked with my user and pass. I find this to be very slow even on a lan but maybe that is my old laptop (with windows 2000) that I run the client on that are slow.

---

### Post by gilesrsmith on 2007-06-14
Hi, I am having the same problem as milkyspit, if I use gnome i just see the nx logo for a few seconds then just the desktop background, no toolbars/anything 

I don't want to try kde as I am only on a 512k connection at the moment and I haven't got the patience to wait for over 300mb to arrive (getting 24mb next week!) 

any help or ideas would be greatly appreciated!

EDIT No problems in KDE

---

### Post by sefs on 2007-07-21
How can we get this to work if ssh is set up for RSAAuthentication & PubKeyAuthenticaton with 

usePam and PasswordAuthentication turned off.

When i do this i get 

```

NX> 203 NXSSH running with pid: 15980
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 127.0.0.1 on port: 2828
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

```

It only works if i turn userPam and Passwordauthentication back on.  Which defeats the purpose of having ssh server authenticate on keys only.

I am usering the ver 3 packages from nomachine.com and i noticed that there no longer is an nx user in the users dialog window.  Did they remove a need for this starting v3?

---

### Post by zed.roeder on 2007-07-26
> **sefs said:**
> How can we get this to work if ssh is set up for RSAAuthentication & PubKeyAuthenticaton with 

usePam and PasswordAuthentication turned off.

When i do this i get 

```

NX> 203 NXSSH running with pid: 15980
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 127.0.0.1 on port: 2828
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

```

It only works if i turn userPam and Passwordauthentication back on.  Which defeats the purpose of having ssh server authenticate on keys only.

I am usering the ver 3 packages from nomachine.com and i noticed that there no longer is an nx user in the users dialog window.  Did they remove a need for this starting v3?

Hello sefs!

That's exactly what i'm waiting for a long time.

Did you managed to get this (usePam and PasswordAuthentication turned off; only ssh server authenticate on keys) working with NX V.3.0? How?

---

### Post by aggiemarine07 on 2007-07-30
Howdy! I had a problem in the initial install. I followed the instructions to the T but when I got towards the end I received this message when I tried to "--install debian" at the end.
aggiemarine07@aggiemarine07-desk:~/freenx$ sudo dpkg -i nxserver_2.1.0-22_i386.deb
(Reading database ... 145817 files and directories currently installed.)
Preparing to replace nxserver 2.1.0-22 (using nxserver_2.1.0-22_i386.deb) ...
Unpacking replacement nxserver ...
Setting up nxserver (2.1.0-22) ...
NX> 701 Updating: server at: Mon Jul 30 18:19:03 2007.
NX> 701 Autodetected system: debian.
NX> 701 Update log is: /usr/NX/var/log/update.
NX> 701 Checking NX server configuration using the
NX> 701 /usr/NX/etc/server.cfg file.
NX> 701 ERROR: Output: chown: `nx:root': invalid user.
NX> 701 ERROR: Cannot set ownership attributes for '/usr/NX/etc' to 'nx:root'.
dpkg: error processing nxserver (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 nxserver


Later I came up with this error msg:


aggiemarine07@aggiemarine07-desk:~/freenx$ sudo /usr/NX/scripts/setup/nxserver --install debian
NX> 701 Updating: server at: Mon Jul 30 18:23:24 2007.
NX> 701 Autodetected system: debian.
NX> 701 Update log is: /usr/NX/var/log/update.
NX> 701 Checking NX server configuration using the
NX> 701 /usr/NX/etc/server.cfg file.
NX> 701 ERROR: Output: chown: `nx:root': invalid user.
NX> 701 ERROR: Cannot set ownership attributes for '/usr/NX/etc' to 'nx:root'.


Any ideas of what I did wrong? It also says that nxserver is not running when I run a  "--status" command. Any help would be greatly appreciated! Thanks!

---

### Post by superuser2 on 2007-08-15
I've been trying all day to get this installed...

I encounter the following error:
```

jacob@jacob-desktop:~/Desktop/freenx$ sudo /usr/NX/scripts/setup/nxserver --install debian
NX> 701 Updating: server at: Wed Aug 15 17:16:47 2007.
NX> 701 Autodetected system: debian.
NX> 701 Update log is: /usr/NX/var/log/update.
NX> 701 Checking NX server configuration using the
NX> 701 /usr/NX/etc/server.cfg file.
NX> 723 Cannot start NX statistics:
NX> 709 NX statistics are disabled for this server.
NX> 701 WARNING: Error when trying to connect to NX server, error is:
NX> 701 WARNING: NX> 203 NXSSH running with pid: 4510
.sh: connect to host 127.0.0.1 port 22: Connection refused
NX> 701 WARNING: nxsetup cannot validate the sanity of the current installation:
NX> 701 WARNING: the current system or NX configuration could be broken.
NX> 701 WARNING: If difficulties arise (for example sessions cannot be started),
NX> 701 WARNING: it is advisable that you try to uninstall the NX server and the
NX> 701 WARNING: NX client packages then install them again.
NX> 701 WARNING: Search also the NoMachine Knowledge Base at the URL below:
NX> 701 WARNING: http://www.nomachine.com/kb
NX> 701 WARNING: for common errors encountered when performing a software update
NX> 701 WARNING: and the related hints on how to solve them..
NX> 701 Update of NX server has been completed with warnings: please review the
NX> 701 update log ('/usr/NX/var/log/update') for details.
NX> 701 Bye.

```

Can I change the SSH port for it somehow? From what I gather the one in the config file mentioned by the OP is a reference, not the actual ssh config, but maybe I'm wrong? How should I deal with this error?

EDIT: Here is the file referenced (the update log)

```

 

NX> 701 Updating: server at: Wed Aug 15 17:16:47 2007.
NX> 701 Autodetected system: debian.
NX> 701 Update log is: /usr/NX/var/log/update.
NX> 701 Checking NX server configuration using the
NX> 701 /usr/NX/etc/server.cfg file.
NX> 701 Running: touch '/usr/NX/etc/users.db'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/keys'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/keys/node.localhost.id_dsa'.
NX> 701 Result: OK.
NX> 701 Running: chown -R nx:root '/usr/NX/home/nx'.
NX> 701 Result: OK.
NX> 701 Running: chmod 0700 '/usr/NX/home/nx'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/var'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/var/db'.
NX> 701 Result: OK.
NX> 701 Running: chown -R nx:root '/usr/NX/var/db/closed'.
NX> 701 Result: OK.
NX> 701 Running: chown -R nx:root '/usr/NX/var/db/running'.
NX> 701 Result: OK.
NX> 701 Running: chown -R nx:root '/usr/NX/var/db/failed'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/passwords.db'.
NX> 701 Result: OK.
NX> 701 Running: chmod 0600 '/usr/NX/etc/passwords.db'.
NX> 701 Result: OK.
NX> 701 Running: touch '/usr/NX/etc/passwords.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/passwords.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/users.db'.
NX> 701 Result: OK.
NX> 701 Running: chmod 0600 '/usr/NX/etc/users.db'.
NX> 701 Result: OK.
NX> 701 Running: touch '/usr/NX/etc/users.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/users.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/guests.db'.
NX> 701 Result: OK.
NX> 701 Running: chmod 0600 '/usr/NX/etc/guests.db'.
NX> 701 Result: OK.
NX> 701 Running: touch '/usr/NX/etc/guests.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/guests.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chmod 0600 '/usr/NX/etc/administrators.db'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/administrators.db'.
NX> 701 Result: OK.
NX> 701 Running: touch '/usr/NX/etc/administrators.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/administrators.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chmod 0600 '/usr/NX/etc/profiles.db'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/profiles.db'.
NX> 701 Result: OK.
NX> 701 Running: touch '/usr/NX/etc/profiles.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/profiles.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chown nx /usr/NX/etc/nodes.db.
NX> 701 Result: OK.
NX> 701 Running: chown nx /usr/NX/var/db/broadcast.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/server.lic'.
NX> 701 Result: OK.
NX> 701 Running: chmod 0400 '/usr/NX/etc/server.lic'.
NX> 701 Result: OK.
NX> 701 Running: chown root:root '/usr/NX/scripts/restricted/nxwtmpadd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod 744 '/usr/NX/scripts/restricted/nxwtmpadd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod u+s '/usr/NX/scripts/restricted/nxwtmpadd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chown root:root '/usr/NX/scripts/restricted/nxwtmpdel.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod 744 '/usr/NX/scripts/restricted/nxwtmpdel.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod u+s '/usr/NX/scripts/restricted/nxwtmpdel.sh'.
NX> 701 Result: OK.
NX> 701 Running: chown root:root '/usr/NX/scripts/restricted/nxpasswd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod 744 '/usr/NX/scripts/restricted/nxpasswd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod u+s '/usr/NX/scripts/restricted/nxpasswd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chown root:root '/usr/NX/scripts/restricted/nxconfigure.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod 744 '/usr/NX/scripts/restricted/nxconfigure.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod u+s '/usr/NX/scripts/restricted/nxconfigure.sh'.
NX> 701 Result: OK.
NX> 701 Running: chown root:root '/usr/NX/scripts/restricted/nxgroupadd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod 744 '/usr/NX/scripts/restricted/nxgroupadd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod u+s '/usr/NX/scripts/restricted/nxgroupadd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chown root:root '/usr/NX/scripts/restricted/nxquotaadd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod 744 '/usr/NX/scripts/restricted/nxquotaadd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod u+s '/usr/NX/scripts/restricted/nxquotaadd.sh'.
NX> 701 Result: OK.
NX> 701 Statistics db not found in: /usr/NX/var/db/nxstat/statistics.db.
NX> 701 Cannot start NX statistics: NX> 701 NX statistics are disabled for this server.
NX> 701 Running: /bin/rm -f '/usr/NX/home/nx/.ssh/authorized_keys2'.
NX> 701 Result: OK.
NX> 701 Running: /bin/cp -p '/usr/NX/home/nx/.ssh/default.id_dsa.pub' '/usr/NX/home/nx/.ssh/authorized_keys2'.
NX> 701 Result: OK.
NX> 701 WARNING: Error when trying to connect to NX server, error is:
NX> 701 WARNING: NX> 203 NXSSH running with pid: 4510

ssh: connect to host 127.0.0.1 port 22: Connection refused
.
NX> 701 WARNING: nxsetup cannot validate the sanity of the current installation:
NX> 701 WARNING: the current system or NX configuration could be broken.
NX> 701 WARNING: If difficulties arise (for example sessions cannot be started),
NX> 701 WARNING: it is advisable that you try to uninstall the NX server and the
NX> 701 WARNING: NX client packages then install them again.
NX> 701 WARNING: Search also the NoMachine Knowledge Base at the URL below:
NX> 701 WARNING: http://www.nomachine.com/kb
NX> 701 WARNING: for common errors encountered when performing a software update
NX> 701 WARNING: and the related hints on how to solve them..
NX> 701 Update of NX server has been completed with warnings: please review the
NX> 701 update log ('/usr/NX/var/log/update') for details.
NX> 701 Bye.
 

NX> 701 Updating: server at: Wed Aug 15 17:19:01 2007.
NX> 701 Autodetected system: debian.
NX> 701 Update log is: /usr/NX/var/log/update.
NX> 701 Checking NX server configuration using the
NX> 701 /usr/NX/etc/server.cfg file.
NX> 701 Running: touch '/usr/NX/etc/users.db'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/keys'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/keys/node.localhost.id_dsa'.
NX> 701 Result: OK.
NX> 701 Running: chown -R nx:root '/usr/NX/home/nx'.
NX> 701 Result: OK.
NX> 701 Running: chmod 0700 '/usr/NX/home/nx'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/var'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/var/db'.
NX> 701 Result: OK.
NX> 701 Running: chown -R nx:root '/usr/NX/var/db/closed'.
NX> 701 Result: OK.
NX> 701 Running: chown -R nx:root '/usr/NX/var/db/running'.
NX> 701 Result: OK.
NX> 701 Running: chown -R nx:root '/usr/NX/var/db/failed'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/passwords.db'.
NX> 701 Result: OK.
NX> 701 Running: chmod 0600 '/usr/NX/etc/passwords.db'.
NX> 701 Result: OK.
NX> 701 Running: touch '/usr/NX/etc/passwords.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/passwords.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/users.db'.
NX> 701 Result: OK.
NX> 701 Running: chmod 0600 '/usr/NX/etc/users.db'.
NX> 701 Result: OK.
NX> 701 Running: touch '/usr/NX/etc/users.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/users.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/guests.db'.
NX> 701 Result: OK.
NX> 701 Running: chmod 0600 '/usr/NX/etc/guests.db'.
NX> 701 Result: OK.
NX> 701 Running: touch '/usr/NX/etc/guests.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/guests.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chmod 0600 '/usr/NX/etc/administrators.db'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/administrators.db'.
NX> 701 Result: OK.
NX> 701 Running: touch '/usr/NX/etc/administrators.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/administrators.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chmod 0600 '/usr/NX/etc/profiles.db'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/profiles.db'.
NX> 701 Result: OK.
NX> 701 Running: touch '/usr/NX/etc/profiles.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/profiles.db.lock'.
NX> 701 Result: OK.
NX> 701 Running: chown nx /usr/NX/etc/nodes.db.
NX> 701 Result: OK.
NX> 701 Running: chown nx /usr/NX/var/db/broadcast.
NX> 701 Result: OK.
NX> 701 Running: chown nx:root '/usr/NX/etc/server.lic'.
NX> 701 Result: OK.
NX> 701 Running: chmod 0400 '/usr/NX/etc/server.lic'.
NX> 701 Result: OK.
NX> 701 Running: chown root:root '/usr/NX/scripts/restricted/nxwtmpadd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod 744 '/usr/NX/scripts/restricted/nxwtmpadd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod u+s '/usr/NX/scripts/restricted/nxwtmpadd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chown root:root '/usr/NX/scripts/restricted/nxwtmpdel.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod 744 '/usr/NX/scripts/restricted/nxwtmpdel.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod u+s '/usr/NX/scripts/restricted/nxwtmpdel.sh'.
NX> 701 Result: OK.
NX> 701 Running: chown root:root '/usr/NX/scripts/restricted/nxpasswd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod 744 '/usr/NX/scripts/restricted/nxpasswd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod u+s '/usr/NX/scripts/restricted/nxpasswd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chown root:root '/usr/NX/scripts/restricted/nxconfigure.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod 744 '/usr/NX/scripts/restricted/nxconfigure.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod u+s '/usr/NX/scripts/restricted/nxconfigure.sh'.
NX> 701 Result: OK.
NX> 701 Running: chown root:root '/usr/NX/scripts/restricted/nxgroupadd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod 744 '/usr/NX/scripts/restricted/nxgroupadd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod u+s '/usr/NX/scripts/restricted/nxgroupadd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chown root:root '/usr/NX/scripts/restricted/nxquotaadd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod 744 '/usr/NX/scripts/restricted/nxquotaadd.sh'.
NX> 701 Result: OK.
NX> 701 Running: chmod u+s '/usr/NX/scripts/restricted/nxquotaadd.sh'.
NX> 701 Result: OK.
NX> 701 Statistics db not found in: /usr/NX/var/db/nxstat/statistics.db.
NX> 701 Cannot start NX statistics: NX> 701 NX statistics are disabled for this server.
NX> 701 Running: /bin/rm -f '/usr/NX/home/nx/.ssh/authorized_keys2'.
NX> 701 Result: OK.
NX> 701 Running: /bin/cp -p '/usr/NX/home/nx/.ssh/default.id_dsa.pub' '/usr/NX/home/nx/.ssh/authorized_keys2'.
NX> 701 Result: OK.
NX> 701 WARNING: Error when trying to connect to NX server, error is:
NX> 701 WARNING: NX> 203 NXSSH running with pid: 4726

ssh: connect to host 127.0.0.1 port 22: Connection refused
.
NX> 701 WARNING: nxsetup cannot validate the sanity of the current installation:
NX> 701 WARNING: the current system or NX configuration could be broken.
NX> 701 WARNING: If difficulties arise (for example sessions cannot be started),
NX> 701 WARNING: it is advisable that you try to uninstall the NX server and the
NX> 701 WARNING: NX client packages then install them again.
NX> 701 WARNING: Search also the NoMachine Knowledge Base at the URL below:
NX> 701 WARNING: http://www.nomachine.com/kb
NX> 701 WARNING: for common errors encountered when performing a software update
NX> 701 WARNING: and the related hints on how to solve them..
NX> 701 Update of NX server has been completed with warnings: please review the
NX> 701 update log ('/usr/NX/var/log/update') for details.
NX> 701 Bye.

```

---

### Post by superuser2 on 2007-08-15
I now see that I didn't have SSHD installed. Just had to run sudo apt-get install opensshserver and I got it running.

---

### Post by superuser2 on 2007-08-16
I got pas that by installing SSHD, but now I have a different problem. If I connect locally it's slow to get started but it works... but over the LAN, past "Using auth method: publickey" I get the error:

```

NX> 286 Failed to set IPTOS_LOWDELAY on descriptor: 13
HELLO NXSERVER - Version 2.1.0-22 - LAS Evaluation
NX> 105 Hello NXCLIENT - Version 2.1.0
NX> 595 ERROR: an error occurred when serving the request, check the log file for details
NX> 999 Bye.
NX> 280 Ignoring EOF on the monitored channel
Killed by signal 15

```

---

### Post by Coollest on 2007-09-13
just finished installing nxserver in 7.04, i had some problems which i discovered were related to have SSH previously installed with a non-default port. 
The nxinstaller seems to need default port 22 in order to make its 1st connection to the server, after which one can change the portnumber in sshd_conf, node.cfg and server.cfg.
This made me beeing around for 3 days untill i found the solution, hope this can help someone !!

---

### Post by felixnine on 2007-10-30
so this is cute:

```
NX> 618 Your evaluation period has expired. Please visit
NX> 618 the NoMachine Web site at [http://www.nomachine.com/](http://www.nomachine.com/)
NX> 618 to acquire a valid subscription.
NX> 999 Bye.

```
great. so if these packages aren't freenx, where do you get them?

---

### Post by daflame on 2007-11-18
If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

---

### Post by netboy541 on 2008-08-08
i have been trying to get nomachine to work on my box for months, and i just can't get it to go.  i get some internal error with nomachine, but i have not tried freenx.  I looked at it, and once it said compile this, grab that, etc, i said "this is more work than what it's worth"

daflame, if you have debs for 8.04, i sure would like to get my hands on those!

---

