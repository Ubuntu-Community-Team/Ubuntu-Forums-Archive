---
title: "HOWTO: FreeNX on Dapper LTS 6.06"
date: 2006-08-22
forum: Outdated Tutorials &amp; Tips
---

### Post by rmac on 2006-08-22
(or alternatively how I lost 3 days of my life)

Alright. I started with a base install of Dapper LTS. These steps should also work for a base install of non-server Ubunutu:

0. sudo -s will get you into a su session.
1. apt-get upgrade
2. apt-get install openssh-server
3. apt-get install ubuntu-desktop
4. test ssh with ssh user@<serverIP>
5. startx (to test, and then I just open a terminal and continue)
6. vi /etc/apt/sources.list and enable the universe repositories by uncommenting:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

and add:

deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx
deb-src [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx

save and exit.
7. add the repository key (optional)
wget [http://free.linux.hp.com/~brett/seveas/freenx/1135D466.gpg](http://free.linux.hp.com/~brett/seveas/freenx/1135D466.gpg) -0- |sudo apt-key add -
8. apt-get update
9. install the packages
apt-get install freenx nxclient nxplugin
select custom keys during the install
10 add a new user to use with the freenx login
adduser <remoteuser>
11. setup up the nxserver
nxsetup 
Hit enter to setup
Select yes for custom keys
Type yes quickly during key generation. If you miss it just re-run the nxsetup
12. cd /home/<remoteuser>
13. nxserver --adduser <remoteuser>
14. nxserver --passwd <remoteuser>
15. test the setup locally by running the client 
/usr/NX/bin/nxclient
16. It should bring up a client wizard.
Name the session, enter the IP of the server. Hit the configure button.
On the first tab, select Key and then import. The key is here: /var/lib/nxserver/home/.ssh/client.id_dsa.key
On the advanced tab, check the enable SSL encryption of all traffic.
17. Use only the 1.5 clients, as the 2.0 client don't work unless you mess with the node config file. 1.5 works well and is stable with this server version.

You can find the 1.5 client for windows at [http://www.industrial-statistics.com/info/nxclients](http://www.industrial-statistics.com/info/nxclients)

A few good things to know for trouble shooting:
nxserver --history or --version or --status
logs: /var/log/auth.log or nxserver.log or Xorg.0.log or messages.

Hope this helps!

---

### Post by anantmishra on 2006-08-30
It rocks. I tried it and it worked like charm. I did accept the default ssh key option to make the installation simple and have no issues :)

---

### Post by crhall on 2006-08-30
Hmmm. Nube here. I'm sure I'm doing something wrong....

> crhall@blainethetrain:/usr/lib/nx$ sudo nxsetup
------> You did select no action.
        FreeNX guesses that you want to _install_ the server.
        Type "y" to abort the installation at this point in time.
        "N" is the default and continues installation.
        Use "/usr/sbin/nxsetup --help" to get more detailed help hints.

 Do you want to abort now? [y/N] n
------> It is recommended that you use the NoMachine key for
        easier setup. If you answer "y", FreeNX creates a custom
        KeyPair and expects you to setup your clients manually.
        "N" is default and uses the NoMachine key for installation.

 Do you want to use your own custom KeyPair? [y/N] ySetting up /etc/nxserver ...done
Setting up /var/lib/nxserver/db ...done
Setting up /var/log/nxserver.log ...done
Setting up special user "nx" ...adduser: Warning: The home dir you specified already exists.
Adding system user `nx'...
Adding new user `nx' (110) with group `nx'.
The home directory `/var/lib/nxserver/home' already exists.  Not copying from `/etc/skel'
adduser: Warning: that home directory does not belong to the user you are currently creating
done
Setting up known_hosts and authorized_keys2 ...done
Setting up permissions ...done

----> Testing your nxserver configuration ...
Warning: Invalid value "DEFAULT_X_SESSION=/etc/X11/xdm/Xsession"
         Users might not be able to request a default X session.
Warning: Invalid value "COMMAND_START_KDE=startkde"
         Users will not be able to request a KDE session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
         Users will not be able to request a CDE session.
Warning: Invalid value "COMMAND_SMBMOUNT=smbmount". You'll not be able to use SAMBA.
Warning: Invalid value "COMMAND_SMBUMOUNT=smbumount". You'll not be able to use SAMBA.

  Warnings occured during config check.
  To enable these features please correct the configuration file.

<---- done

----> Testing your nxserver connection ...
Permission denied (publickey,password).
Fatal error: Could not connect to NX Server.

Please check your ssh setup:

        - Make sure "nx" is one of the AllowUsers in sshd_config.
        - Make sure your sshd allows public key authentication.
        - Make sure your sshd is really running on port 22.
        - Make sure your sshd_config AuthorizedKeysFile in sshd_config is set to authorized_keys2.


Any thoughts?

---

### Post by foofightrs777 on 2006-08-30
I wold recommend that you try to recreate your pub key and then attempt to re-add your user and set password by nxserver.  

Also, you may want to be sure you are typing in 'yes' during the setup.  The install will ask you something similar to:  "Do you want to continuing connecting to this server?"  You must type yes quickly and press enter.

Hopefully that will help.

---

### Post by remmelt on 2006-09-07
Same for me. I type yes<enter> and then it waits longer on the "Are you sure you want to...etc" question than if I don't type yes, so something is happening.

It's just that the nxserver isn't running, or so it seems. I can do a nxserver --status and it will say: running, but it doesn't check for a process, just for a file. What's up with that?
ps aux |grep -i nx gives me nothing though. Surely there must be a process with nx or NX somewhere in the name that runs when you start the server?

Then: no connection can be made, which seems logical when the server isn't running.

---

### Post by remmelt on 2006-09-07
Alright, you have to type yes exactly at the moment the question is asked, NOT before! 

I got the thing to set up, the server is seemingly running because I can su nx, but my 1.5 windows client won't connect. The connection times out. This will be the end of that. Warning: nx can't connect to the running x like vnc can. Too bad vnc under KDE is slow as hell.

---

### Post by finferflu on 2006-09-08
Well, I had my go...

```
mmanu@ubuntumachine:~$ sudo wget http://free.linux.hp.com/~brett/seveas/freenx/1135D466.gpg -0- |sudo apt-key add -
wget: invalid option -- 0
gpg: no valid OpenPGP data found.

```

If I don't do that I get:

```
W: GPG error: http://free.linux.hp.com dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run apt-get update to correct these problems

```

Any hint?

Thanks a lot!

--EDIT--

I'm very sorry, it just worked after I copied and pasted the command from the actual website... maybe I mispelled something before... sorry for this useless post...

---

### Post by HAARP on 2006-09-09
2.0 worked PERFECTLY fine for me, with the 2.0 client from any OS, without having to configure anything.

Mini-Howto:

```
wget http://64.34.161.181/download/2.0.0/Linux/FE/nxserver_2.0.0-76_i386.deb
wget http://64.34.161.181/download/2.0.0/Linux/nxnode_2.0.0-100_i386.deb
wget http://64.34.161.181/download/2.0.0/Linux/nxclient_2.0.0-98_i386.deb 
sudo apt-get install openssh-server
sudo dpkg -i *.deb 
```

Re-login. The server is running. Forward port 22 in the router if present. Set the client to encrypt all traffic. Connect.

---

### Post by dabear on 2006-09-10
The wikipedia page say:
> 
If set up as a proxy, NX also tunnels Remote Desktop Protocol (for Windows Terminal Server sessions) and remote VNC sessions (all types of OS platforms) and lets them benefit from some of the same speed improvements. 

[http://en.wikipedia.org/wiki/Freenx](http://en.wikipedia.org/wiki/Freenx)

How can I achive this?

---

### Post by sguart on 2006-09-10
> **HAARP said:**
> 2.0 worked PERFECTLY fine for me, with the 2.0 client from any OS, without having to configure anything.

Mini-Howto:

```
wget http://64.34.161.181/download/2.0.0/Linux/FE/nxserver_2.0.0-76_i386.deb
wget http://64.34.161.181/download/2.0.0/Linux/nxnode_2.0.0-100_i386.deb
wget http://64.34.161.181/download/2.0.0/Linux/nxclient_2.0.0-98_i386.deb 
sudo dpkg -i *.deb 
```

Re-login. The server is running. Forward port 22 in the router if present. Set the client to encrypt all traffic. Connect.


How safe is this?

i also tried version 2.0 and it worked after manually copying the public key to the client.

i was not able to get freenx to work prior to this. it will always failed the authentication even though i have the public key the same between the server and client.

i copy the windows client key and put that into the /home/<remote_user>/.ssh/authorized_keys2

after that, i can login using the windows from xp machine into the ubuntu machine.

thanks,
sg

---

### Post by FastZ on 2006-09-11
Hey guys, I'm having some troubles...

I followed the directions over at [http://www.urbanpuddle.com/articles/2006/08/23/install-nx-server-on-ubuntu-dapper-drake](http://www.urbanpuddle.com/articles/2006/08/23/install-nx-server-on-ubuntu-dapper-drake) and now, when i type the "sudo nxsetup", I get the following output....

```

matt@swint:~$ sudo nxsetup
------> You did select no action.
        FreeNX guesses that you want to _install_ the server.
        Type "y" to abort the installation at this point in time.
        "N" is the default and continues installation.
        Use "/usr/sbin/nxsetup --help" to get more detailed help hints.

 Do you want to abort now? [y/N] n
------> It is recommended that you use the NoMachine key for
        easier setup. If you answer "y", FreeNX creates a custom
        KeyPair and expects you to setup your clients manually.
        "N" is default and uses the NoMachine key for installation.

 Do you want to use your own custom KeyPair? [y/N] nSetting up /etc/nxserver ...done
Setting up /var/lib/nxserver/db ...done
Setting up /var/log/nxserver.log ...done
Setting up known_hosts and authorized_keys2 ...done
Setting up permissions ...done

----> Testing your nxserver configuration ...
Warning: Could not find nxdesktop in /usr/lib/nx. RDP sessions won't work.
Warning: Invalid value "DEFAULT_X_SESSION=/etc/X11/xdm/Xsession"
         Users might not be able to request a default X session.
Warning: Invalid value "COMMAND_START_KDE=/usr/bin/dbus-launch --sh-syntax --exit-with-session startkde"
         Users will not be able to request a KDE session.
Warning: Invalid value "COMMAND_START_GNOME=/usr/bin/dbus-launch --sh-syntax --exit-with-session gnome-session"
         Users will not be able to request a Gnome session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
         Users will not be able to request a CDE session.
Warning: Invalid value "COMMAND_SMBMOUNT=smbmount". You'll not be able to use SAMBA.
Warning: Invalid value "COMMAND_SMBUMOUNT=smbumount". You'll not be able to use SAMBA.

  Warnings occured during config check.
  To enable these features please correct the configuration file.

<---- done

----> Testing your nxserver connection ...
ssh: connect to host 127.0.0.1 port 22: Connection refused
Fatal error: Could not connect to NX Server.

Please check your ssh setup:

        - Make sure "nx" is one of the AllowUsers in sshd_config.
        - Make sure your sshd allows public key authentication.
        - Make sure your sshd is really running on port 22.
        - Make sure your sshd_config AuthorizedKeysFile in sshd_config is set to authorized_keys2.
matt@swint:~$

``` 
I have no idea how to fix that.  I have NXClient installed ok, and NXNode installed as well.  NXServer is installed but when I try nxsetup, that's what I get.  

](*,)  Any help?  Thanks.

---

### Post by rick_1010 on 2006-09-13
Oh man, I am getting the same thing, I'm going on week 3 now of trying to get FreeNX to work on ubuntu / xubuntu (of course, I've only been trying off and on).. anyways it just doesn't seem to be well documented on ubuntu, I am getting this message:

 - Make sure "nx" is one of the AllowUsers in sshd_config.
        - Make sure your sshd allows public key authentication.
        - Make sure your sshd is really running on port 22.
        - Make sure your sshd_config AuthorizedKeysFile in sshd_config is set to authorized_keys2.
matt@swint:~$

(this is right after the install, when I do a manual install it checks it for me so at least I realized that I could do the manual install and it will check now so I have a somewhat better idea of the problem)

However, does anyone know what sshd_config is? When I try to run it as root it does not recognize it as a command. I think this is the last piece to fix this error.. to figure out how to re-configure sshd_config

---

### Post by rick_1010 on 2006-09-13
(By the way: FreeNX does work quite well, at least when you isntall it as an RPM in a distro such as Fedora, as I have been using it in Fedora for a while now and have had no problems, it has awesome performance, unfortunately Fedora does not so I need to get this working on Ubuntu :) )

---

### Post by rick_1010 on 2006-09-13
Ok, so I have found the ssh_config file, it is located at:

/etc/ssh/ssh_config   in the file directory

Now the issue is which changes need to be made to get this to work correctly, it seems it may be trial and error at this point, if anyone else has changed this file before successfully please comment

(I have tried the suggestions made by nxsetup but it still is not working)

---

### Post by TwoWordz on 2006-09-13
If you want to secure ssh, you might want to take a look at my guide located [here]("http://www.ubuntuforums.org/showthread.php?t=254149") (ubuntuforums)

:D

TW

---

### Post by rick_1010 on 2006-09-13
Would securing .ssh probably make FreeNX work correctly?

---

### Post by FastZ on 2006-09-13
Rick, do you mind posting what you did to fix the problem you were having?  Maybe it will work for me as well.

---

### Post by rick_1010 on 2006-09-13
Hi, to clarify: I have not been able to fix the problem to get FreeNX to work on ubuntu, the step I am stuck on is:

- I have followed the error message that says to edit the ssh_config file however when I edit the file making the changes as instructed by the NXserver install I am still unable to get NXclient to work properly, it connects but then never brings up the remote screen, instead giving a long error message.

I will be sure to post here if I am able to figure it out.

---

### Post by moore.bryan on 2006-09-14
[I]after much searching, i think i found the forum i need... long story shorter:
ubuntu 6.06, kernel 2.6.17.11, running openbox --> home pc
windows xp, sp2, running like **** -->work pc
i need to be able to connect to my home pc... my work has t3, home is cable with dns assigned by isp.  is freenx my answer?
[/I]

---

### Post by TwoWordz on 2006-09-14
rick: there is no trial and error just do what the guide says and you'll be all set... 

You might want to post you sshd_config so we can see where you messed up. :)

TW

---

### Post by TwoWordz on 2006-09-14
FastZ:

it seems your /etc/nxserver/node.conf is not setup right, you might want to try the default one. 

message me if you need the original file.

TW

---

### Post by rick_1010 on 2006-09-14
Hi, I did exactly as the instructions specified in editing the sshd_config file. I will go over it once more to make sure it is right, maybe I made a typo or something but I don't think I did..

---

### Post by HAARP on 2006-09-14
Does FreeNX actually **log in** using ssh?

---

### Post by rick_1010 on 2006-09-14
Yes, as far as I am aware FreeNX is essentially an extension of the ssh login which allows visual processes to be run, this is why, for example: you can't watch an existing session displayed on a local machine (the way you can in VNC), also having used FreeNX before in Fedora, it is actually possible to just run 1 process through FreeNX, for example yould run a custom command and run "firefox" and it would only display the firefox window, if you close the firefox window then the session would end.. anyways, I'm almost 100% sure it uses ssh to connect

---

### Post by FastZ on 2006-09-14
> **TwoWordz said:**
> FastZ:

it seems your /etc/nxserver/node.conf is not setup right, you might want to try the default one. 

message me if you need the original file.

TW

I just checked, I don't even have a node.conf in the nxserver directory.  I take it that's a bad thing?! #-o

---

### Post by rick_1010 on 2006-09-15
I wonder if my node.conf file is missing (I'm on a different pc right now), I will check and post if its missing on mine too, I will find where to get the node.conf file maybe that will fix the issue, it seems we are both having almost exactly the same problem.

QUESTION:

Does anyone know if it is possible to connect to FreeNX just using a standard SSH connection, would be done by: "ssh nx@68.3.100.54" for example, I am thinking maybe the fact that the new NoMachine client and the older FreeNX server don't match up could be the issue so if I can just connect through SSH that could solve the problem

---

### Post by ihristov on 2006-09-15
> **FastZ said:**
> 

```

----> Testing your nxserver connection ...
ssh: connect to host 127.0.0.1 port 22: Connection refused
Fatal error: Could not connect to NX Server.

``` 
I have no idea how to fix that.  I have NXClient installed ok, and NXNode installed as well.  NXServer is installed but when I try nxsetup, that's what I get.  

](*,)  Any help?  Thanks.


The line indicates your SSH server is not running.
Make sure your SSH server is started.

After it has been started connect to yourself as root to cache the key, so you don't get the error below

```
$ sudo ssh 127.0.0.1
```

The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
RSA key fingerprint is xx:xx:xx....
Are you sure you want to continue connecting (yes/no)? Fatal error: Could not connect to NX Server.

---

### Post by TwoWordz on 2006-09-15
Hi all, 

I think I am going to take a minute here and try to clarify a few things.

Freenx is no extension of the "ssh login". SSH is an encrypted tunneling protocol that can be used to "pipe" all sort of information thru unsecured networks. AFAIK, freenx only provides compression to the existing X11 protocol that has always been available.

Why I tought crhall had a problem with node.conf:

```

Warning: Invalid value "DEFAULT_X_SESSION=/etc/X11/xdm/Xsession"
Users might not be able to request a default X session.
Warning: Invalid value "COMMAND_START_KDE=startkde"
Users will not be able to request a KDE session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
Users will not be able to request a CDE session.
Warning: Invalid value "COMMAND_SMBMOUNT=smbmount". You'll not be able to use SAMBA.
Warning: Invalid value "COMMAND_SMBUMOUNT=smbumount". You'll not be able to use SAMBA.
```

Theses values appear in node.conf and should be left alone when you start working with freenx. After you can connect, you can try to change them (see documentation) to change the behavior of the server.

I've attached the default node.conf.

TW

---

### Post by pmeunier on 2006-09-15
I'm having a different problems from other posters:

# apt-get install freenx nxclient nxplugin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package nxclient

yet, I am getting info from the added repositories:
# apt-get update
Get:1 [http://free.linux.hp.com](http://free.linux.hp.com) dapper-seveas Release.gpg [309B]
Hit [http://free.linux.hp.com](http://free.linux.hp.com) dapper-seveas Release
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://free.linux.hp.com](http://free.linux.hp.com) dapper-seveas/freenx Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://free.linux.hp.com](http://free.linux.hp.com) dapper-seveas/freenx Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Fetched 5B in 1s (4B/s)
Reading package lists... Done


When I try Synaptic instead, I get:
freenx:
 Depends: nxagent (>=1.4.92+1.5.0) but it is not installable
[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)


If I try the tar packages from nomachine, I get a warning about libstdc++-libc6.2-2.so.3 not being found.  I found some advice to do:
apt-get install libstdc++2.10-glibc2.2 libstdc++5
but then I get:
E: Couldn't find package libstdc++2.10-glibc2.2

[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

Any help would be appreciated!

---

### Post by pmeunier on 2006-09-15
> **HAARP said:**
> 2.0 worked PERFECTLY fine for me, with the 2.0 client from any OS, without having to configure anything.

Mini-Howto:

```
wget http://64.34.161.181/download/2.0.0/Linux/FE/nxserver_2.0.0-76_i386.deb
wget http://64.34.161.181/download/2.0.0/Linux/nxnode_2.0.0-100_i386.deb
wget http://64.34.161.181/download/2.0.0/Linux/nxclient_2.0.0-98_i386.deb 
sudo dpkg -i *.deb 
```

Re-login. The server is running. Forward port 22 in the router if present. Set the client to encrypt all traffic. Connect.


How safe is this?

It's not foolproof:
# sudo dpkg -i *.deb
dpkg: error processing nxclient_2.0.0-98_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing nxnode_2.0.0-100_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing nxserver_2.0.0-76_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 nxclient_2.0.0-98_i386.deb
 nxnode_2.0.0-100_i386.deb
 nxserver_2.0.0-76_i386.deb
# wget [http://64.34.161.181/download/2.0.0/Linux/nxclient_2.0.0-98_amd64.deb](http://64.34.161.181/download/2.0.0/Linux/nxclient_2.0.0-98_amd64.deb)
--13:38:25--  [http://64.34.161.181/download/2.0.0/Linux/nxclient_2.0.0-98_amd64.deb](http://64.34.161.181/download/2.0.0/Linux/nxclient_2.0.0-98_amd64.deb)
           => `nxclient_2.0.0-98_amd64.deb'
Connecting to 64.34.161.181:80... connected.
HTTP request sent, awaiting response... 404 Not Found
13:38:25 ERROR 404: Not Found.

---

### Post by h2o on 2006-09-15
[B]I was also getting this problem but you will see at the end of this msg that it got connected while seting it up.

I am using freenx on xubuntu. local nxclient connects fine but it does not start the window manager, i m running xfce.
[/B]

```
vmware@xubuntu:~$ sudo nxsetup --setup-nomachine-key
------> You did select no action.
        FreeNX guesses that you want to _install_ the server.
        Type "y" to abort the installation at this point in time.
        "N" is the default and continues installation.
        Use "/usr/sbin/nxsetup --help" to get more detailed help hints.

 Do you want to abort now? [y/N] n
Setting up /etc/nxserver ...done
Setting up /var/lib/nxserver/db ...done
Setting up /var/log/nxserver.log ...done
Setting up known_hosts and authorized_keys2 ...done
Setting up permissions ...done

----> Testing your nxserver configuration ...
Warning: Could not find nxdesktop in /usr/lib/nx. RDP sessions won't work.
Warning: Could not find nxviewer in /usr/lib/nx. VNC sessions won't work.
Warning: Invalid value "DEFAULT_X_SESSION=/etc/X11/xdm/Xsession"
         Users might not be able to request a default X session.
Warning: Invalid value "COMMAND_START_KDE=/usr/bin/dbus-launch --sh-syntax --exit-with-session startkde"
         Users will not be able to request a KDE session.
Warning: Invalid value "COMMAND_START_GNOME=/usr/bin/dbus-launch --sh-syntax --exit-with-session gnome-session"
         Users will not be able to request a Gnome session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
         Users will not be able to request a CDE session.
Warning: Invalid value "COMMAND_SMBMOUNT=smbmount". You'll not be able to use SAMBA.
Warning: Invalid value "COMMAND_SMBUMOUNT=smbumount". You'll not be able to use SAMBA.

  Warnings occured during config check.
  To enable these features please correct the configuration file.

<---- done

----> Testing your nxserver connection ...
The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
RSA key fingerprint is bb:ba:9d:ae:8c:55:f5:b4:8b:90:2f:33:27:15:15:f4.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '127.0.0.1' (RSA) to the list of known hosts.
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 quit
Quit
<--- done

Ok, nxserver is ready.

PAM authentication enabled:
  All users will be able to login with their normal passwords.

  PAM authentication will be done through SSH.
  Please ensure that SSHD on localhost accepts password authentication.

  You can change this behaviour in the /etc/nxserver/node.conf file.
Have Fun!
```


[B]
Here is the error after successfully connection and login. Message i get "session startup fail" and here isthe complete trace.[/B]
```

NX> 203 NXSSH running with pid: 11866
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 127.0.0.1 on port: 8888
NX> 211 The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
RSA key fingerprint is bb:ba:9d:ae:8c:55:f5:b4:8b:90:2f:33:27:15:15:f4.
Are you sure you want to continue connecting (yes/no)? 
Failed to add the host to the list of known hosts (/home/vmware/.ssh/known_hosts).
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.4.0
NX> 134 Accepted protocol: 1.4.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: vmware
NX> 102 Password: 
NX> 103 Welcome to: xubuntu user: vmware
NX> 105 listsession --user="vmware" --status="suspended,running" --geometry="1024x768x24+render" --type="unix-application"
NX> 127 Sessions list of user 'vmware' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: vmware
NX> 105 startsession  --virtualdesktop="1" --application="startxfce4" --link="adsl" --backingstore="1" --nodelay="1" --encryption="1" --cache="8M" --images="32M" --media="0" --session="localhost" --type="unix-application" --cookie="******" --geometry="1024x722" --kbtype="pc102/us" --screeninfo="1024x722x24+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: xubuntu-1000-B2F4E0CBC2740CE9CB68CDDC10A6B0BC
NX> 705 Session display: 1000
NX> 703 Session type: unix-application
NX> 701 Proxy cookie: da036326bd40a5acc7bedcf7213871d8
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 879a755746132b1786ef801e2a5c4f88
NX> 704 Session cache: unix-application
NX> 707 SSL tunneling: 1
/usr/lib/nx/nxserver: line 891: 11999 Terminated              ( sleep $AGENT_STARTUP_TIMEOUT; exit 1 )
NX> 105 NX> 504 Session startup failed.
NX> 1004 Error: nxagent failed to start with: Unrecognized option: 1
NX> 1001 Bye.
Killed by signal 15.
```

Thanks

---

### Post by TwoWordz on 2006-09-15
Are you using the client version 1.5?

NX> 1004 Error: nxagent failed to start with: Unrecognized option: 1

I had this error when I tried with the last version. 

TW

---

### Post by FastZ on 2006-09-15
> **ihristov said:**
> The line indicates your SSH server is not running.
Make sure your SSH server is started.

After it has been started connect to yourself as root to cache the key, so you don't get the error below

```
$ sudo ssh 127.0.0.1
``` 
The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
RSA key fingerprint is xx:xx:xx....
Are you sure you want to continue connecting (yes/no)? Fatal error: Could not connect to NX Server.


First of all, thanks TwoWordz for posting the default node.conf file.  I saved it to the nxserver directory and all was good in the world.  However, when I did the sudo ssh 127.0.0.1 command, it asked for a root password which I took to be mine...the one i use when i use the sudo command...but it didnt work.  is there a default password to use?


EDIT:  Ok well, though I never got the sudo ssh 127.0.0.1 to work, i did a sudo nxsetup and it finally completed saying that nxserver was good to go.  Now, next question is how the heck do I set this thing up?  Is there a how-to on configuring the server and client?  I use a WRT-54G wireless router so my IP address for the computer with the NXServer on it is not going to have a "legitimate" ip address, so to speak.  192.168.0.100.  How do I get this thing to be accessible from across the WAN?

---

### Post by TwoWordz on 2006-09-16
FastZ: 

The person saying you should try to connect using sudo ssh 127.0.0.1 is partially wrong. What he wanted to see was if your ssh server what up and listening. You could have done that just by using ssh 127.0.0.1. The password you were asked when using sudo is  your password but the ssh client does not need root privileges to run...

When you ssh to another host (or yourself in this situation) the ssh protocol exchange public RSA key to identify the machine. You have to accept the key the first time. This is used so that no one can put a another machine between you and the server to steal your credentials. If the RSA key of the host you try to connect changes, the ssh client will warn you that the authenticity of the remote host could not be verified.

In the network world, all the 127.0.0.x range is an alias for LOCALHOST which means it is only a loopback to test your services.

The wrt54g has a dynamic DNS client so you can go to [www.dyndns.com](www.dyndns.com) and setup an account then configure your router so  it will update the DNS with your IP adress in case it changes. You will then have a site name like myhouse.dyndns.com to connect. Don't forget to forward port 22 to your computer on the router.

TW

---

### Post by HAARP on 2006-09-16
> **pmeunier said:**
> It's not foolproof:
# sudo dpkg -i *.deb
dpkg: error processing nxclient_2.0.0-98_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing nxnode_2.0.0-100_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing nxserver_2.0.0-76_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 nxclient_2.0.0-98_i386.deb
 nxnode_2.0.0-100_i386.deb
 nxserver_2.0.0-76_i386.deb
# wget [http://64.34.161.181/download/2.0.0/Linux/nxclient_2.0.0-98_amd64.deb](http://64.34.161.181/download/2.0.0/Linux/nxclient_2.0.0-98_amd64.deb)
--13:38:25--  [http://64.34.161.181/download/2.0.0/Linux/nxclient_2.0.0-98_amd64.deb](http://64.34.161.181/download/2.0.0/Linux/nxclient_2.0.0-98_amd64.deb)
           => `nxclient_2.0.0-98_amd64.deb'
Connecting to 64.34.161.181:80... connected.
HTTP request sent, awaiting response... 404 Not Found
13:38:25 ERROR 404: Not Found.
[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)
They claim the've got AMD64-compatible packages, but they don't work. Sorry, I can't help you :/


> **TwoWordz said:**
> Hi all, 

I think I am going to take a minute here and try to clarify a few things.

Freenx is no extension of the "ssh login". SSH is an encrypted tunneling protocol that can be used to "pipe" all sort of information thru unsecured networks. AFAIK, freenx only provides compression to the existing X11 protocol that has always been available.

That's what I thought, too, but I wasn't sure. So basicly, denying login-attempts over ssh wouldn't even secure NX?

---

### Post by TwoWordz on 2006-09-16
HAARP: 

What it means is that NX will be as secure as your SSH implementation.

I was linking to my howto because since you need SSH to use NX, it is a good idea to secure it. The minimum security setting to sshd_config would be "PermitRootLogin no" because that's one of the  only account existing on all servers and attackers know that. They will try entire dictionnaries trying to log with the root account but even if they do have the password, they won't be able to connect using ssh. 

DenyHost looks at connexion attemps and add the IP address of the attacker to the hosts.deny file after (n) failed logins.

TW

---

### Post by HAARP on 2006-09-16
> **TwoWordz said:**
> What it means is that NX will be as secure as your SSH implementation.

I was linking to my howto because since you need SSH to use NX, it is a good idea to secure it. The minimum security setting to sshd_config would be "PermitRootLogin no" because that's one of the  only account existing on all servers and attackers know that. They will try entire dictionnaries trying to log with the root account but even if they do have the password, they won't be able to connect using ssh. 

DenyHost looks at connexion attemps and add the IP address of the attacker to the hosts.deny file after (n) failed logins.

TW

Ok, I agree that securing ssh is a good idea, but that's not quite what I wanted to know.
Your How-to blocks login attempts over ssh after x failed logins. But it won't block login attempts over NX after x failed ones, since NX doesn't **log in** over ssh!
Of course, every attacker will try ssh first and will thus be blocked out. But what if he's bruteforcing my NX server first? There'll be nothing that will stop him.

---

### Post by TwoWordz on 2006-09-16
NX logs in thru SSH.

hehe

Why do you think you have to mess with sshd_config during installation? 

TW

---

### Post by HAARP on 2006-09-16
Well, in that case: Alright :p

---

### Post by FastZ on 2006-09-16
> **TwoWordz said:**
> The wrt54g has a dynamic DNS client so you can go to [www.dyndns.com]("http://www.dyndns.com") and setup an account then configure your router so  it will update the DNS with your IP adress in case it changes. You will then have a site name like myhouse.dyndns.com to connect. Don't forget to forward port 22 to your computer on the router.

TW

Ok I have a dyndns account and the router is set up to use my hostname i chose.  How do I forward port 22 to this computer?  Port Forwarding?  Port Range Forwarding? Port Triggering?  I have a few options here and no decent documentaion on what they are used for and how they are configured for use.

---

### Post by HAARP on 2006-09-16
Port Forwarding. You need your internal IP. Forward 22 to this IP.

---

### Post by rick_1010 on 2006-09-16
Ok, so I figured out at least what I was doing wrong, I skipped over this one small part, like an idiot just expecting everything to work automatically (THIS IS THE POST THAT STARTED THIS THREAD, PAGE 1):
[SIZE="2"]
[B]"11. setup up the nxserver
nxsetup
Hit enter to setup
Select yes for custom keys
[SIZE="4"]Type yes quickly during key generation. If you miss it just re-run the nxsetup[/SIZE]"[/B][/SIZE]

You really do have to watch it and type in yes very fast and press enter. After that everything should work fine as long as you follow everything else (I knew I was making the sshd_config changes correctly :) )

Anyways, maybe this can help someone else, but not sure

(By the way, the tutorial says you should choose a custom key, I have always used the default NX key and it works fine, I would recommend doing this first before trying to set a custom key (just re-install later on if you want a custom key for security purposes as setting the custom key, can by itself cause some problems unless you know what you are doing, from what I have read)

---

### Post by leteci on 2006-09-17
how to solve this error:

NXPROXY - Version 1.5.0

Info: Proxy running in client mode with pid '3836'.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Not using NX delta compression.
Info: Using lan link parameters 16384/8/0/0.
Info: Using pack method '16m-jpeg-9' with session 'unix-gnome'.
Info: Not using ZLIB stream compression.
Info: Not using remote ZLIB stream compression.
Info: Not using persistent cache.
Info: Starting X protocol compression.
Info: Established X server connection.
Info: Using shared memory support in X server.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.

---

### Post by FastZ on 2006-09-17
> **HAARP said:**
> Port Forwarding. You need your internal IP. Forward 22 to this IP.

Alright man, this is what I got.

```

Port Forwarding
Application    Port From   Protocol     IP Address       Port To    Enable
 NxServer        8888         Both     192.168.1.100       22

``` 
I'm thinking that's probably not correct.

---

### Post by leteci on 2006-09-18
When i try to connect with specific user i get this error:
Info: Proxy running in client mode with pid '3252'.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using cache parameters 4/262144/8192KB/8192KB.
Info: Using image cache parameters 1/1/32768KB.
Info: Using adsl link parameters 8192/8/10/50.
Info: Using pack method '16m-jpeg-7' with session 'unix-gnome'.
Info: Using ZLIB data compression level 3.
Info: Using ZLIB data threshold set to 32.
Info: Using ZLIB stream compression level 6.
Info: Using remote ZLIB data compression level 3.
Info: Using remote ZLIB stream compression level 6.
Info: No suitable cache file found.
Info: Starting X protocol compression.
Info: Established X server connection.
Info: Using shared memory support in X server.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.

with different user works ok? How to solve the problem?

---

### Post by moore.bryan on 2006-09-20
[I]having an issue; i know this isn't a windows forum, but i wonder if anyone knows the answer:
i have freenx running properly on my home ubuntu machine and when i log in from my work xp machine, it authenticates and abruptly closes after "starting new x session."  any ideas?
-----------------------------
UPDATE
i've gotten it to work by using the gnome interface, but i run openbox.  i also use gdm, so how would i have it launch openbox; the "custom" choice doesn't work at all.
[/I]

---

### Post by FastZ on 2006-09-24
> **FastZ said:**
> Alright man, this is what I got.

```

Port Forwarding
Application    Port From   Protocol     IP Address       Port To    Enable
 NxServer        8888         Both     192.168.1.100       22

```I'm thinking that's probably not correct.

Alright well, I figured out on my own how to fix my port forwarding on my router.  I just went to [http://www.portforward.com/default.htm](http://www.portforward.com/default.htm) and followed the directions for my router brand and make.

---

### Post by FastZ on 2006-09-25
Does anybody know where I can find a STEP-BY-STEP HOW-TO for installing NXServer on a Ubuntu machine and accessing it from a Windows machine?  I don't know much about Linux and when I find guides on how to do things, it seems like the people writing them always leave out a bunch of stuff that they figure the person reading it would already know how to do.  Well, I dont know how to do all the things that arent shown. 

Now, I have NXServer 2.0 installed on this machine (Ubuntu).  When I do 'sudo nxserver --status' it brings up the following:
```
NX> 100 NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 110 NX Server is running
NX> 999 Bye

```

Now, I take it that is what it needs to say?

I have NXClient (v1.5) installed on here and the NXPlugin also.  On my Windows machine I have NXClient v1.5 installed.  

When I get to the step where I need to test the setup locally ( /usr/NX/bin/nxclient), I get an error saying that the X Authorization Cookie couldnt be created or something.  Then it just sits there try to start the X environment and never does anything else.

On the Windows machine, when I start the client and make sure the password is in correctly and the key is copied over from the '/var/lib/nxserver/home/.ssh/client.id_dsa.key' location, it says that Authentication was successful but then it says "Server not installed or NX access disabled".  

What do I do?  How can I delete everything pertaining to NX and start all over from scratch?

---

### Post by the_jaguar on 2006-09-25
> **HAARP said:**
> 2.0 worked PERFECTLY fine for me, with the 2.0 client from any OS, without having to configure anything.

Mini-Howto:

```
wget http://64.34.161.181/download/2.0.0/Linux/FE/nxserver_2.0.0-76_i386.deb
wget http://64.34.161.181/download/2.0.0/Linux/nxnode_2.0.0-100_i386.deb
wget http://64.34.161.181/download/2.0.0/Linux/nxclient_2.0.0-98_i386.deb 
sudo apt-get install openssh-server
sudo dpkg -i *.deb 
```

Re-login. The server is running. Forward port 22 in the router if present. Set the client to encrypt all traffic. Connect.

Thanks a bunch.. this is exactly what I did.. I also had to manually wget a libc library, but thats it.. no configurations needed..
I downloaded my windows client, and boom :)

---

### Post by moore.bryan on 2006-09-26
> **FastZ said:**
> Does anybody know where I can find a STEP-BY-STEP HOW-TO for installing NXServer on a Ubuntu machine and accessing it from a Windows machine?  I don't know much about Linux and when I find guides on how to do things, it seems like the people writing them always leave out a bunch of stuff that they figure the person reading it would already know how to do.  Well, I dont know how to do all the things that arent shown. 

Now, I have NXServer 2.0 installed on this machine (Ubuntu).  When I do 'sudo nxserver --status' it brings up the following:
```
NX> 100 NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 110 NX Server is running
NX> 999 Bye

```Now, I take it that is what it needs to say?

I have NXClient (v1.5) installed on here and the NXPlugin also.  On my Windows machine I have NXClient v1.5 installed.  

When I get to the step where I need to test the setup locally ( /usr/NX/bin/nxclient), I get an error saying that the X Authorization Cookie couldnt be created or something.  Then it just sits there try to start the X environment and never does anything else.

On the Windows machine, when I start the client and make sure the password is in correctly and the key is copied over from the '/var/lib/nxserver/home/.ssh/client.id_dsa.key' location, it says that Authentication was successful but then it says "Server not installed or NX access disabled".  

What do I do?  How can I delete everything pertaining to NX and start all over from scratch?

[I]i'm not sure there is one... i fell into much of the same problem as you.  what i did to finally get it to work was to run ifconfig, figure out what dns my cable provider was giving me, go to [http://www.dyndns.org](http://www.dyndns.org), sign-up for the free static dns service, get the new address, go into the nx-client, and set it up for that new dns.  i know that's a little sparse on details... if you need me to try and explain better, just pm or email me.
[/I]

---

### Post by FastZ on 2006-09-26
I already have a DNS address from DynDns.org and I'm using it.  Still nothing.  Made some progress somehow yesterday.  I made no modifications to anything since I posted my last post on here and then all of a sudden, when I tried to connect with my windows machine, nxclient would bring up a window with the no-machine logo in the center of it for a split second and then it would close out and say that it couldnt connect.  I don't know whether to just give up or try a different program.

---

### Post by moore.bryan on 2006-09-27
*did you try double-checking your port-settings; default is 22, but many howto's suggest changing it...*

---

### Post by FastZ on 2006-09-27
Yeah, sshd is set to 22, ssh is set to 22, the port forwarding on my router is set to 22....I dont know what else to check.  Oh, node.conf is set to 22.

---

### Post by Aberrix on 2006-10-09
this worked perfect! exactly what I was looking for, thanks for the write up!

---

### Post by HAARP on 2006-10-11
Now what I need is the option to choose a username/password for proxy authentication of the client...
Any ideas? client OS is Windoze, sadly.

---

### Post by robert114 on 2006-10-17
My howto installing freeNX:

Why this howto?
Answer: I had this problem installing FreeNX:
```

---> Testing your nxserver connection ...
Permission denied (publickey,password).
Fatal error: Could not connect to NX Server.

Please check your ssh setup:

- Make sure "nx" is one of the AllowUsers in sshd_config.
- Make sure your sshd allows public key authentication.
- Make sure your sshd is really running on port 22.
- Make sure your sshd_config AuthorizedKeysFile in sshd_config is set to authorized_keys2.
```

**The howto**

    -----------------------
    Step 1 - Download
    -----------------------

    Download "NX Desktop Server DEB for Linux" from:
    [http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

    Download "NX Node DEB for Linux" from:
    [http://www.nomachine.com/download-node.php?os=linux](http://www.nomachine.com/download-node.php?os=linux)

    Download "NX Client DEB for Linux" from:
    [http://www.nomachine.com/download-client-linux.php](http://www.nomachine.com/download-client-linux.php)

    -----------------------
    Step 2 - Install
    -----------------------

    Install the DEB files in this order:

    nxclient
    nxnode
    nxserver

    I just right-clicked on them and installed them...use apt-get if you prefer.

-----------------------
Step 3 - Configure
-----------------------

Load up your /etc/ssh/sshd_config file into an editor:

sudo nano /etc/ssh/sshd_config

Add the following line & save the file
AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2

Restart sshd by typing:
sudo /etc/init.d/ssh restart


Verify nxserver is configured properly by typing:
sudo /usr/NX/bin/nxserver --status

This should return:

NX> 900 Connecting to server ..
NX> 110 NX Server is running.

NX> 999 Bye.

If you get any errors here, then something is wrong with your configuration. If not, then NX Desktop Server should be installed.

Before anyone complains, yes, I'm using the NoMachine server key just because it's easy. If you want to generate your own key, you can. These instructions worked for me on Dapper....YMMV. Let me know if you have trouble.....hopefully my notes were correct.

Good luck!

you can read it from: [http://michigantelephone.mi.org/blog/2006/09/how-to-install-nx-server-and-client.html]("http://michigantelephone.mi.org/blog/2006/09/how-to-install-nx-server-and-client.html")

---

### Post by Aramis on 2006-11-02
Hi y'all,

I just spent my entire afternoon installing FreeNX, I am not going into details but it was far from easy even with the guides! as if, these only work  for the authors :(

I strongly desagree that the Windows Client 1.5 is a stable/good version. My personal experience is this:

- if the remote computer is set for a resolution of 1024*768, and the same is on the client machine, then it is IMPOSSIBLE to see the full remote desktop!

- if the remote computer is set for a resoltuion of 800*600, and the client computer has a resolution of 1024*768, the FIRST time the client is started the full remote desktop appears in a window! brilliant. Now if you try to RESUME the session, then you have a BIG problem because the remote desktop will appear in 800*600 in a maximized window! The huge black bars all around are bearable but you CANNOT STOP the client! pressing "CLOSE" does not bring (or at least I can't see it) the end of session dialog box. And if you chose to use the session admin to close the client, then the sessions dies all your work is wasted!

Hence I am looking for a solution! what is wrong with my setup? is there something to configure on the server to force the client application to use the exact chosen resolution at all times?! or is it something to do with the MS windows application itself.

Finally, what is the manipulation mentioned in the first post regarding the setup of the Windows Client 2.0+ to work with the current version of FreeNX server? do the changes enhance the session resume feature?

Thanks to whomever is able to help me,

keep up the good work.

Ar@mi$

---

### Post by robert114 on 2006-11-02
Never tried the windows client will try freenx on edgy soon

---

### Post by acegolfer on 2006-11-03
After upgrading to Edgy, FreeNX is gone. I had to reinstall it. Unfortunately, there's no version for Edgy so I used Dapper repository, which worked. I didn't have to reconfigure, just reinstall did the job.

---

