---
title: "HOW-TO Secure Remote Access - Hamachi+VNC"
date: 2006-02-23
forum: Outdated Tutorials &amp; Tips
---

### Post by KingOfNowhere on 2006-02-23
Secure Remote Access with Hamachi and VNC
---------------------------------------------

----
Update: 4/19/06 - Added 'Single User' configuration instructions for Hamachi and installation of gHamachi (Hamachi gtk GUI). 
----

By KingOfNowhere

This is a How-To for setting up a secure VNC server by tunnelling it through a Hamachi virtual private network. By setting up VNC this way, it allows you to access your machine securely (using Hamachi's encryption) and makes your machine accessable from anywhere on the net. Before I jump right in, here is some background:

[Hamachi]("http://www.hamachi.cc/") is a zero-config VPN client for Windows and Linux (currently Beta for Mac). It allows you to, very easily, create a virtual private network that can be logged into and accessed for all over the net. It does this by creating IP tunnels to each VPN client, making them directly accessable to all the other clients on the VPN. Hamachi also encrypts the connections it creates to allow for secure access.

[VNC]("http://www.realvnc.com/") is a widely used, cross-platform application that allows for remote desktop access.

Together, these apps can allow for secure, remote access to you machine from anywhere.

Lastly, before I begin the guide, I would like to give credit to those I referenced for this guide:

[HOWTO: Hamachi Linux Guide (2.4.x and 2.6.x)]("http://forums.hamachi.cc/viewtopic.php?t=3523") By Kamel

and

[HOWTO: Set up VNC server with resumable sessions]("http://ubuntuforums.org/showthread.php?t=122402") By Tichondrius

thx guys. Anyway on to the guide.
---------------------------------------------

**Part 1: Hamachi**

1.A) The 'tun' Module

The very first part of the Hamachi installation is to enable IP Tunnelling support in your kernel. This can be done like this:
```
sudo modprobe tun
```
then open your /etc/modules file and add tun to the list of modules:
```
 sudo gedit /etc/modules
``` 

If you are using a standard Ubuntu kernel, this should be all you need to do. However, if you compiled your own kernel, you made need to recompile it with IP Tunnelling support (only if you recieve an erro with 'modprobe'). If anyone needs help installing the module, see [HOWTO: Hamachi Linux Guide (2.4.x and 2.6.x)]("http://forums.hamachi.cc/viewtopic.php?t=3523") By Kamel

1.B) Installing Hamachi

Okay, now on to the actual Hamachi software. But first, we need to make sure that a valid tunnelling node has been created in /dev. This is done like this:
```
ls /dev/net/tun 
```

If you get a "No Such File or Directory" error, you need to create a new node like this:
```
sudo mkdir /dev/net
sudo mknod /dev/net/tun c 10 200
```

Okay, now that we have a valid IP Tunnel node, time to install Hamachi. 

Download the latest version of Hamachi from [http://www.hamachi.cc/download]("http://www.hamachi.cc/download").

Enter the directory where you downloaded it and here is how to install it:
```

#Extract the archive
tar -zxvf hamachi-0.9.9.9-x.tar.gz
cd hamachi-0.9.9.9-x/

#install Hamachi
sudo make install
sudo tuncfg

#Hamachi is installed
```

1.C) Setting User Permissions

For security sake, we are going to set the permissions of Hamachi so that it can only be started by members of the 'hamachi' group. This is done like so:
```

#Create the 'hamachi' group
sudo groupadd hamachi

#Add your user to the group
sudo gpasswd -a user hamachi

#Add root to the group
sudo gpasswd -a root hamachi

#Set socket permissions
sudo chmod 760 /var/run/tuncfg.sock

#Finally, changing the group of the file
sudo chgrp hamachi /var/run/tuncfg.sock
```

Now that permissions are done, on to configuration.

1.D) Hamachi Configuration - System Service

Follow this section if you want Hamachi to run as a system service (in the background). I chose to list this method of configuration first because it seemed most relivant to the guide. If you want to have Hamachi run as a user application and install the gtk frontend, skip to section '1.E'. 

1.D.1) Base Configuration

Creating an initial configuration can be done like so:
```

sudo hamachi-init -c /etc/hamachi
```

the result should be something like this:
```

Initializing Hamachi configuration (/etc/hamachi). Please wait ..

  generating 2048-bit RSA keypair .. ok
  making /etc/hamachi directory .. ok
  saving /etc/hamachi/client.pub .. ok
  saving /etc/hamachi/client.pri .. ok
  saving /etc/hamachi/state .. ok

Authentication information has been created. Hamachi can now be started with
'hamachi start' command and then brought online with 'hamachi login'.

```

Okay, next is to start Hamachi:
```

sudo hamachi -c /etc/hamachi start
```

Now that we are up and running, you need to set your nickname:
```

sudo hamachi -c /etc/hamachi set-nick "YourNickHere"
```

Next, we need to login to Hamachi and then either login to an existing network or create a new one. Like this:
```

#Login to Hamachi
sudo hamachi -c /etc/hamachi login

#To join an existing network
sudo hamachi -c /etc/hamachi join network password

#Or to create a new network
sudo hamachi -c /etc/hamachi create network password

#Lastly, to go online to the network you joined
sudo hamachi -c /etc/hamachi go-online network

```

*NOTE ABOUT NETWORK PASSWORDS*
I would recommend visiting [http://grc.com/passwords]("http://grc.com/passwords") for a random string password. They are very strong passwords and adds to the security of your setup.

Now your machine is up and running on it's own Hamachi VPN. The last part of the installation is a script written by Kamel that will allow Hamachi to run on startup.

1.D.2) Hamachi Startup Script

Open gedit and save the following as /etc/init.d/hamachi
```

#!/bin/sh

hamachi_start() {
  echo "Starting hamachi..."
  /sbin/tuncfg
  /usr/bin/hamachi -c /etc/hamachi start
  /bin/chmod 760 /var/run/tuncfg.sock
  /bin/chgrp hamachi /var/run/tuncfg.sock
}

hamachi_stop() {
  echo "Stopping hamachi..."
  killall tuncfg
  /usr/bin/hamachi -c /etc/hamachi stop
}

hamachi_restart() {
  hamachi_stop
  sleep 1
  hamachi_start
}

case "$1" in
'start')
  hamachi_start
  ;;
'stop')
  hamachi_stop
  ;;
'restart')
  hamachi_restart
  ;;
*)
  hamachi_start
esac

```

Lastly, you need to make the script executable and add it to startup:
```

sudo chmod +x /etc/init.d/hamachi
sudo update-rc.d hamachi defaults
```

1.E) Hamachi Configuration - User Application

Follow this section if you want Hamachi to run as a user application and to use the pretty gtk frontend. If you want to have Hamachi run as a system service in the background, go back to section '1.D'. 

1.E.1) Base Configuration

Creating an initial configuration can be done like so:
```

hamachi-init 
```

the result should be something like this:
```

Initializing Hamachi configuration (/home/user/.hamachi). Please wait ..

  generating 2048-bit RSA keypair .. ok
  making (/home/user/.hamachi directory .. ok
  saving (/home/user/.hamachi/client.pub .. ok
  saving (/home/user/.hamachi/client.pri .. ok
  saving (/home/user/.hamachi/state .. ok

Authentication information has been created. Hamachi can now be started with
'hamachi start' command and then brought online with 'hamachi login'.

```

Okay, next is to start Hamachi:
```

hamachi start
```

Now that we are up and running, you need to set your nickname:
```

hamachi set-nick "YourNickHere"
```

Next, we need to login to Hamachi and then either login to an existing network or create a new one. Like this:
```

#Login to Hamachi
hamachi login

#To join an existing network
hamachi join network password

#Or to create a new network
hamachi create network password

#Lastly, to go online to the network you joined
hamachi go-online network

```

*NOTE ABOUT NETWORK PASSWORDS*
I would recommend visiting [http://grc.com/passwords]("http://grc.com/passwords") for a random string password. They are very strong passwords and adds to the security of your setup.

Now your machine is up and running on it's own Hamachi VPN. The last part of the installation is to install the GUI for Hamachi. Here is how that is done.

1.E.2) Hamachi GUI (gHamachi) Installation

First, visit the Hamachi forums and download the most recent version of the gHamachi frontend for either gtk 2.0 or gtk 1.2 (whichever you prefer).

[gHamachi can be found here.]("http://forums.hamachi.cc/viewtopic.php?t=2488")

Second, simply unpack the gHamachi tarball, copy the binary to /usr/bin, and give it permission to run (chmod +x).

```

tar xfz gHamachi_gtk2.tar.gz
sudo mv ghamachi /usr/bin/
sudo chmod +x /usr/bin/ghamachi
```

Once that is done, the Hamachi GUI is completely installed.

Start the GUI like this:
```
ghamachi
```

Hamachi is all set up now, now on to VNC.

**Part 2: VNC**

This section of my guide is largely based on [Tichondrius' Guide]("http://ubuntuforums.org/showthread.php?t=122402"), nice guide man. This part of the guide is currently intended only for those using the Gnome desktop. For those of you using KDE or something else, please refer to other threads on this forum or the [VNC Homepage]("http://www.realvnc.com/").

2.A) Enabling XDMCP in Gnome

There are a few settings that need to be set inside Gnome before we begin:

System -> Administration -> Login Screen Setup
Security Tab -> Enable XDMCP
XDMCP Tab -> Disable "Honor Indirect Requests"

Next we need to install the required packages.

2.B) Installing VNC and xinetd

First, make sure you have the Universe repository added to your apt.sources. If you dont know how to do that, look [here]("http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories").

Next, install VNC and xinetd:
```

sudo apt-get install vnc4server xinetd

```

Next, set a VNC password:
```

sudo vncpasswd /root/.vncpasswd

```

Then, open gedit and save the following as /etc/xinetd.d/Xvnc:
```

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}

```

Lastly, restart xinetd and it is all setup:
```

sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo /etc/init.d/xinetd start

```

You can test the VNC server with this:
```

vncviewer localhost:1

```

At this point, both Hamachi and VNC have been installed and configured on your machine. Next are some recommended firewall settings to keep you secure and keep everything runing smoothly.

**Part 3: Settings and Usage**

3.A) Firewalls

To keep your machine secure with these newly installed services, I recommend these additional settings in your firewall:

For XDMCP -> only allow incoming connections from 5.x.x.x (Hamachi subnet) to Ports 6000-6009

For VNC -> only allow incoming connections from 5.x.x.x (Hamachi subnet) to Port 5901

Filtering these ports this way, will only allow Hamachi connections to connect to these services. 

*NOTE FOR FIRESTARTER USERS*
If you use the Firestarter firewall, then you must add these two lines to your '/etc/firestarter/user-pre' file to accept connections on the Hamachi interface:
```

$IPT -A INPUT -i ham+ -j ACCEPT
$IPT -A OUTPUT -o ham+ -j ACCEPT

```

Then restart Firestarter:
```

sudo /etc/init.d/firestarter restart

```

I do not know if there are similar configuration changes required by iptables. If anyone can comment, please do.

3.B) Usage

Now that your machine is all setup and configured, accessing your machine remotely becomes as easy as a few simple steps.

- On the Connecting Machine -

You need to install [Hamachi]("http://www.hamachi.cc/download") on the connecting machine and join the network your destination machine is on.

Then, you need to install a [VNC Viewer]("http://www.realvnc.com/cgi-bin/download.cgi") on the connecting machine. 

Once Hamachi is setup and VNC Viewer is installed on the connecting machine, all you need to do now is open a VNC connection to your destination machine's Hamachi IP address (ex. 5.x.x.x) on display 1 (ex. 5.x.x.x:1).

For Example:

Server = 5.18.36.109:1

*Do not forget to specify the ':1' after the IP address, otherwise you won't connect.

Then, all you have to do is enter your VNC password, then login as your user.

Now that you are logged into your machine remotely, my guide is done here.

----------------------------------------------
I hope everyone finds this informative. Any corrections are welcome. And thanks again to Kamel and Tichondrius for their guides, they really helped me out.

- KingOfNowhere

---

### Post by KingOfNowhere on 2006-03-04
Hamachi Update:

The developers of hamachi are currently working on Hamachi for Mac OS X, with the completion of this, hamachi will work across all platforms (Win, Lin, Mac).

-KingOfNowhere

---

### Post by nemesa on 2006-03-28
Hi!

Nice work! You should add the following command at the end:

```

sudo update-rc.d hamachi defaults

```

---

### Post by mitjab on 2006-03-29
cool howto

what is the passwd for network
#To join an existing network
sudo hamachi -c /etc/hamachi join network password

it said
```
Creating network .. failed, network name is already taken

```

if i want to delete it said that i am not an owner

---

### Post by Rizado on 2006-03-29
The hamachi start script will not work unless you run it as root. And if you run hamachi as root there's no need to change tuncfg.sock to writable for hamachi group.

---

### Post by Rizado on 2006-03-29
[QUOTE=mitjab]cool howto

what is the passwd for network
#To join an existing network
sudo hamachi -c /etc/hamachi join network password

it said
```
Creating network .. failed, network name is already taken

```

if i want to delete it said that i am not an owner[/QUOTE]
You have to replace network with the name of the network you want to join, if you didn't know.

So you have to create your own network or join an existing one. 
To create do "sudo hamachi -c /etc/hamachi create network password" and replace network with the name you want and password with the password you want.

---

### Post by mitjab on 2006-03-29
so i can skip this ans continuoe with howto

---

### Post by Rizado on 2006-03-29
To use hamachi you have to either create a network or join an existing one. You don't need hamachi at all to use vnc. Quote from [http://www.hamachi.cc/](http://www.hamachi.cc/)
> What it is
With Hamachi you can organize two or more computers with an Internet connection into their own virtual network for direct secure communication.

Hamachi is fast, secure and simple. It is also free.

What's in it for me
Think - LAN over the Internet.

Think - Zero-configuration VPN.

Think - Secure peer-to-peer.

Access computers remotely. Use Windows File Sharing. Play LAN games. Run private Web or FTP servers. Communicate directly. Stay connected. 
Hamachi is a way of creating a "lan" over internet. Everyone that joins a network get a ip that the others can use to connect to. ex you can start a lan game and others in your network can join your game with that ip just like they where directly connected to you.

---

### Post by sidd-tx on 2006-04-11
Namesa and KingOfNowhere...

Is it necessary to issue the command:

sudo update-rc.d hamachi defaults

And at what point should I enter it?

Thanks
Sidd....

---

### Post by KrisWood on 2006-04-17
Thanks for the great tutorial! :) I'd tried to get hamachi working on ubuntu before but it wouldn't play nice with firestarter. Now it works like a charm and my entire network can get on it. Thanks much!

---

### Post by souled on 2006-04-18
Nice HOWTO. It worked perfectly. How can I see my Hamachi IP address?

---

### Post by KingOfNowhere on 2006-04-19
Update
--------

I just added the instructions for using the gHamachi frontend for Hamachi. I think many of you will prefer it to the command line interface. I also added separate configuration instructions for those who only want Hamachi to run as an application (not a system service).

Also thanks for the positive feedback and if anyone wants a more in-depth explaination of how Hamachi works and why it is a good VPN solution, you should listen to [Security Now! with Steve Gibson:]("http://www.grc.com/SecurityNow.htm") [Episode 18 - Hamachi]("http://media.grc.com/sn/SN-018.mp3").

---

### Post by Rizado on 2006-04-19
You might want to add that there's a problem using ghamachi with composite enabled in xorg.conf
If it's enabled the buttons will be corrupted. It took me some time to figure that out.

---

### Post by stani on 2006-04-22
When I do hamachi start it refuses, although I am member of the hamachi group:
> stani@ibmx30:~/Data/Downloads/hamachi-0.9.9.9-17-lnx$ hamachi start
22 20:02:43.637 [19319] tap: connect() failed 13 (Permission denied)

When I do it with sudo, it of course works. Do I need to do everything with sudo?

Stani

---

### Post by stani on 2006-04-22
```
sudo chmod 777 /var/run/tuncfg.sock

```
...solved my problem.

Stani

---

### Post by outoforder on 2006-04-23
hello, ubuntu community. this is my first post, and is to post a problem :( . anyone has a clue as to why i get the following error message?

[FONT="Courier New"]Copying hamachi into /usr/bin ..
Creating hamachi-init symlink ..
Copying tuncfg into /sbin ..
install: cannot run strip: No such file or directory
install: strip failed
make: *** [install] Error 1[/FONT]


NOTE: i believe things should work after i install gcc.

---

### Post by NXArmada on 2006-04-24
I skipped the hamachi step sense security wasn't a big deal but when i connect to the VNC server all i get is the mouse thats an X and the pattern background.  How do i start up the GUI.

---

### Post by KingOfNowhere on 2006-04-24
Rizado,

thx for pointing out that ghamachi is not stable, it is just a little GUI for use as an alternative to the cmd line interface. 

Rizado reports ghamachi has problems running if you are using "composite" enable in your xorg.conf, so keep that in mind.

NXArmada,

for my vnc configuration to work, make sure you are using GDM (GNOME graphical login) and that you have XDMCP setup accordingly (section 2.A of my guide). give that a try.

---

### Post by NXArmada on 2006-04-24
thats the one step i forgot thanks all works.

---

### Post by trivialpackets on 2006-04-27
@outoforder

Did you install build-essential?

---

### Post by slk230mb on 2006-05-01
Hey, this is my first post, and I am a new Ubuntu user. I use hamachi on my windows machines and want to install on my liunx configuration. In following the how to, I get hung up on the sudo make install, it returns "sudo: make: command not found". What am I doing wrong? Help please.

edit - i installed the make command, now I'm stuck initializing using this command sudo hamachi-init -c /etc/hamachi

---

### Post by zenobia on 2006-05-02
I followed this HOW-TO, and everything seems to be working, except for one problem.  This problem also occurs when I am just VNC'ing into the PC on the local network without Hamachi.

For some reason, every now and then, I will fire up VNC and attempt to connect to the host PC.  VNC never gets as far as asking for the password, and just seems to hang. The last time this happened, I grepped for Xvnc and it appeared to be running, but I believe it may have been running/stuck from the last VNC session.

I am not able to duplicate this consistently but it happens frequently.  One morning, I fire up the PC and attempt to login remotely, and it does not work.  The next morning, I fire up the PC and attempt to login remotely, and it works on the first go.

Today, everything was running smoothly, until I logged off earlier when going out for lunch.  Upon my return, I can no longer VNC into the remote PC anymore.

Anyone have any ideas on what this could be?  I am running Ubuntu Breezy on an Athlon XP 2800, with 1 gig of ram, using the latest versions of vnc and Hamachi (the presense of Hamachi seems irrelevant).  Also worthy of note is that the same problem happens on my other Ubuntu box as well.

---

### Post by Gaimlz on 2006-05-03
Very good howto. It worked fine for me :D

---

### Post by KingOfNowhere on 2006-05-05
slk230mb -> if you just successfully "sudo make install" on hamachi, you now need to 'sudo tunecfg' and then follow sections (1.C) and (1.E) of my guide. that should help you through the rest of the setup and help you install a nice GUI to use with Hamachi.

zenobia -> for my  guide, vnc is setup to work with gnome and GDM (gnome graphical login). so you have to make sure your are using GDM and have XDMCP enabled (section 2.A of my guide), this allows vnc to use GDM to login. so make sure of that and also double check your vnc server settings, and also make sure your firewall is not blocking incoming connections to the server.

i hope this helps you guys.

- KoN

---

### Post by zenobia on 2006-05-05
King of Nowhere -> Thanks for the response.  However, let me clarify what the problem is.  I have XDMCP enabled, and everything is setup exactly per the HowTo instructions.  The issue is that sometimes it will work, sometimes it will not.  I can not find any rhyme or reason as to why one day it will work perfectly when the PC is started up, the next day it wont, or it will work part of the day then fail later on during the same day.  I have also re-verified the vnc server settings.  There is no firewall running on that linux box as I have a router/firewall combination handling everything - in addition to that, I will have these problems when trying to connect from the same LAN, nevermind trying to connect remotely from another location on the Internet. :-) 

For instance, just this morning, I fired up the PC and went in to work.  I attemped to connect from here, and VNC just fails with no errors.  I ssh'ed into the box, stopped xinetd, did a killall for Xvnc, restarted xinetd, and this time VNC worked.  Any ideas?

---

### Post by zenobia on 2006-05-05
It is also worth noting that when VNC fails, Xvnc starts to use 99% of the cpu according to top.  In the other thread about setting up resumable VNC sessions, another individual has the same problem that I do, and is stuck as well.

---

### Post by lanceo on 2006-10-01
Hi,
Great howto.  I'm having problems - when connecting to the vncserver locally, I get challenged to input my vnc password, and once i do, i just get a grey screen with a cursor that looks like an X.  Googling around gives a suggestion that I alter my ~/.vnc/xstartup file to add the window manager that I want, but I don't seem to have one.

I have just installed the latest Ubuntu 6.01 that comes with Xfce as the window manager.  Does anyone know what i should edit in order to allow me to log in via VNC?

Apparently I have GDE installed (dunno how to utilize it) and kde, but xfce is on by default.

cheers,
Lance

---

### Post by lanceo on 2006-10-02
> **lanceo said:**
> Hi,
Great howto.  I'm having problems - when connecting to the vncserver locally, I get challenged to input my vnc password, and once i do, i just get a grey screen with a cursor that looks like an X.  Googling around gives a suggestion that I alter my ~/.vnc/xstartup file to add the window manager that I want, but I don't seem to have one.

I have just installed the latest Ubuntu 6.01 that comes with Xfce as the window manager.  Does anyone know what i should edit in order to allow me to log in via VNC?

Apparently I have GDE installed (dunno how to utilize it) and kde, but xfce is on by default.

cheers,
Lance


Ok, after I rebooted, the login screen for xbuntu finally showed it's beautiful face!  And I could log in - i didn't need to mess with the xstartup file (not that I could find it!).  It just worked.  And then intalling hamachi 9.9.9 onto my windows XP box, I was able to connect using the realVNC 4 viewer client and using the hamachi ip address - the hamachi gui in windows shows the ip addresses of every computer in your network quite clearly!  So now I am a happy camper!  

Thanks for the great howto, KingofNowhere!

Cheers,
Lance

---

### Post by edblah on 2006-10-02
hi. im getting the following errors when i run sudo apt-get install vnc4server xinetd

edblah@linux:~$ sudo apt-get install vnc4server xinetd
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vnc4server: Depends: xserver-common but it is not going to be installed
E: Broken packages

how do i fix this?

---

### Post by imaiden22 on 2006-10-02
i got myself a little problem myself too, i tried getting ghamachi to start up, and the gui comes up but then gives me a message saying that hamachi could not be started. the first few times this happened so i gave up with the gui and went on to sucessfully install vnc or so i think because testing it locally gives me that gray screen that lanceo was reffering to with the X as the cursor, any suggestions?

btw, im running ubuntu dapper with gnome, not xfce

---

### Post by SlugO on 2006-10-05
I'm not exactly sure of everything that Hamachi can do so maybe it's better to ask here first :)

We're setting up Plone CMS for a friend's old computer that has Ubuntu 5.10 server installation. Would it be possible to remotely access the shell and transfer files to and from a directory under /opt on the server with Hamachi? Or should we just put an SSH server there? There's no graphical desktop at the moment.

---

### Post by ceng1984 on 2006-11-18
Need some help!!

I am trying to set up Hamachi + VNC on my Dapper machine by following the HowTo KingofNowhere has listed in this thread. Hamachi is installed fine and is working. The problem is with trying to set the vnc password with "sudo vncpasswd". I receive the following error message

vncpasswd: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

Any help would be appreciated.  If I need to supply other info, just let me know.

ceng1984

---

### Post by indigoshift on 2006-11-19
I'm having a lot of trouble with this, as well.

When I type in:

sudo hamachi -c /etc/hamachi start

I get this message:

tap: connect() failed 2 (No such file or directory)

I wish I knew what that meant--I mean, "tap"?  I'm confused.

This is a little frustrating...reminds me of when I first started using Ubuntu, and couldn't figure anything out.  ;)

---

### Post by AvWijk on 2006-12-11
I have installed Ubuntu 6.06 LAMP with the Hamachi VPN service that works great (followed the tutorial here: [http://www.ubuntuforums.org/showthre...hlight=Hamachi](http://www.ubuntuforums.org/showthre...hlight=Hamachi)) So, on my Ubuntu box I have the hamachi service running which works fine itself, I can acces my web site hosted there and approach it via PuTTY / SSH.

Also, I can browse my network shares via hamachi. This only works on my local area network (very well, actually), but not on a remote location! When remote computing (at work/school but not at home), I can do everything except browsing for network folders on my Ubuntu box.

I am behing a NAT router (Speedtouh DSL router), and openened all ports from 6000 to 6009, to 10.0.0.190, which is ofcourse my Ubuntu box.

What to do?

---

### Post by Sebastral on 2006-12-19
I can't get past section 1.D.1 :( . The command 'sudo hamachi-init -c /etc/hamachi' gives me; 'Illegal instruction (core dumped)'. I got this on dapper so I did a clean up-to-date edgy install but that didn't help.  Any thoughts?

---

### Post by indigoshift on 2006-12-19
I get the feeling this thread's been abandoned, and apparently my forum-searching kung fu isn't good enough to find a similar thread still watched.

If you guys find one, please reply here...I'm subscribed to this thread, and will see the note.  ;)

---

### Post by vintage-vinnie on 2007-01-03
How can I port map hamachi through my wireless firewall? I followed the first part of the directions to have it run as a service not as a user


so where is my config?

---

### Post by MystaMax on 2007-01-23
> **indigoshift said:**
> I'm having a lot of trouble with this, as well.

When I type in:

sudo hamachi -c /etc/hamachi start

I get this message:

tap: connect() failed 2 (No such file or directory)

I wish I knew what that meant--I mean, "tap"?  I'm confused.

This is a little frustrating...reminds me of when I first started using Ubuntu, and couldn't figure anything out.  ;)

run **tuncfg** before you run hamachi start.

I'm not sure if you ever found a resolution to this, but I found [this post]("http://www.ubuntuforums.org/showpost.php?p=1465809&postcount=6") and decided to share. It worked great for me. I started to google about it, and found [this article]("http://www.command-tab.com/2006/08/13/hamachi-on-mac-os-x/") (for Mac OSX) which stated the following:

> **command-tab.com]
I should note that when your computer is restarted, you&#8217 said:**
> Hamachi OS X ReadMe[/URL] has a listing of commands to delete networks, evict members, and other useful features that are worth a look.



I hope this all helps.... it helped me! My only problem now is that the GUI does not appear properly.  All I see is text, and no images. Any ideas?

---

### Post by jonjonz on 2007-01-28
I am trying to follow the howto and everything works up to this point: When I try to type:

sudo hamachi-init -c /etc/hamachi

I get "Illegal instruction" in reply.

I am on Dapper Drake 6.06

Any ideas?

---

### Post by AvWijk on 2007-02-11
Hamachi won't work over my local LAN, in other words I can't acces my PC via hamachi with \\(hamachi-network-adress). Without Hamachi this goes fine.

---

### Post by Matthamilton23 on 2007-02-16
when I try to install hamachi on my xubuntu (6.6)machine ( meets requirements of hamachi)
I get as far as unpacking the tar file
after that when I try to sudo make install I get this message.
sudo: make: command not found
can any body help or tell me what I am doing wrong?

---

### Post by handband2 on 2007-03-14
Something I did to the Hamachi Startup Script to go-online:

```
#!/bin/sh

hamachi_start() {
  echo "Starting hamachi..."
  /sbin/tuncfg
  /usr/bin/hamachi -c /etc/hamachi start
  /bin/chmod 760 /var/run/tuncfg.sock
  /bin/chgrp hamachi /var/run/tuncfg.sock
[COLOR="Red"]  /usr/bin/hamachi -c /etc/hamachi go-online MYNETWORKNAME[/COLOR]
}

hamachi_stop() {
  echo "Stopping hamachi..."
  killall tuncfg
  /usr/bin/hamachi -c /etc/hamachi stop
}

hamachi_restart() {
  hamachi_stop
  sleep 1
  hamachi_start
}

case "$1" in
'start')
  hamachi_start
  ;;
'stop')
  hamachi_stop
  ;;
'restart')
  hamachi_restart
  ;;
*)
  hamachi_start
esac
```

As you can see I added:    /usr/bin/hamachi -c /etc/hamachi go-online MYNETWORKNAME to have the machine automatically login.

---

### Post by bobwdn on 2007-05-17
In following this excellent HOW-TO, I have run into a problem.  This is the second machine I am setting up.  The first machine is working just fine.  This machine hangs at "sudo hamachi -c /etc/hamachi login".  I get a response to the login as follows:  "Logging in . . ." and that is as far as it advances.  Any ideas?

---

### Post by komputes on 2007-05-18
Is there any way someone can automate this package to install on its own and simply prompt you for a password. I can see I'm not the only one here who's frustrated... ](*,)

---

### Post by amlucent23 on 2007-05-19
Great guide. Works perfect on Feisty! Alot easier than an Open VPN server thats for sure!

Has anyone been able to use this software with NX client and server as opposed to VNC? (VNC is just slow man) I am trying to enable just that. Ill keep playing with it. any help is appreciated,

---

### Post by zedpol on 2007-05-23
I'm having difficulties also.  I've installed hamachi, i'm able to create a network, log in etc.  I have also installed hamachi on a XP box so I'm not a network of 1.  From ubuntu i can ping the windows box but i can't ping or browse my samaba share from xp on my ubuntu box.  Supremely frustrating as I haven't been able to figure this out.  Any thoughts?

---

### Post by handband2 on 2007-05-31
zedpol,

Can you browse your samba share on your Ubuntu box through a LAN?  I'm thinking there might be an issue on how samba is setup not hamachi.

Good guide to setup samba:  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server")

handband

---

### Post by weedenbc on 2007-06-02
Hi guys got a problem with Hamachi.  I have a Hamachi network setup with 2 windows boxes and my ubuntu laptop.  All are running hamachi and are logged in just fine with little green icons to my hamachi network.  The windows machines can browse each other's shares.

The problem is that I can't connect to either windows pc from ubuntu using the hamachi ip.  If I run vncviewer and use my 10.0.1.x lan address it works fine.  Using the 5.x.x.x hamachi ip I get a "No route to host" error.  Using vnc through gHamachi doesn't work either, nor does ping or browse.

I think there is something wrong with my settings but I don't know where to start.

BTW, normal network shares work just fine - the problem is with the hamachi interface even through all 3 machines show "green" in hamachi.

Thoughts?

---

### Post by handband2 on 2007-06-04
weedenbc,

What method did you use to install hamachi?  Are you installing it as a service or as a user application?

---

### Post by kfries6 on 2007-06-29
I keep getting "Destination Host Unreachable" when trying to use Hamachi on a Linux desktop to ping a Linux server.

If I do a
$ hamachi list

it shows my group, and shows my server, with an asterisk next to it to show its online.  Yet any attempts to contact that machine (ssh, ping, etc) fails.  Ping returns "Destination Host Unreachable".

Both computers set up with Feisty, one with the traditional GNOME desktop, the other is the server version.  Hamachi was set up by following the instructions at the beginning of this thread.  The server is set up using the "as a service" method in 1D, while the desktop was set up via the user application method in 1E.

Both machines behave the same exact way.

Any ideas?

---

### Post by toocoldimtold on 2007-07-06
I have the same problem where my server is recognised as being online by hamachi, but all attempts to connect to it result in a timeout. My VNC works with localserver but it cannot use the hamachi address. What's going on is there a way to fix this. It looks like I have 2 hamachi IP's running at once how did this happen!!

---

### Post by jazzysmith on 2007-07-08
I can't run tuncfg after running "make install" the error is: 
bash: /sbin/tuncfg: No such file or directory

I've tried running it as root and via sudo neither works. Any ideas?

JS

---

### Post by Rever75 on 2007-07-10
Hi,

  I have the latest hamachi installed but I cannot seem to connect to any of the systems on the network. When I try to ping it I get this,....
```
 From 5.x.x.x icmp_seq=2 Destination Host Unreachable
 From 5.x.x.x icmp_seq=3 Destination Host Unreachable
 From 5.x.x.x icmp_seq=4 Destination Host Unreachable
```
 I have tried it installed as a service and as a user application. I can connect perfectly fine with my Windows Box to all my other systems. However my Ubuntu box does not. I have  modprobed tun and have /dev/net/tun I also have tuncfg running. However nothing seems to be working. 
```
$route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
5.0.0.0            5.x.x.x         255.0.0.0       UG    0      0        0 ham0    (I added this)
5.0.0.0            0.0.0.0            255.0.0.0       U     0      0        0 ham0
0.0.0.0           192.168.1.1     0.0.0.0         UG    0      0        0 eth1
```

I have also shutdown firestarter and still no go any help would be greatly appreciated.

---

### Post by Rever75 on 2007-07-10
Ok,
Judging from what I have read on the Hamachi forums I am going to assume my issue is my Corporate Firewall. I have 3 machines running 2 at work and 1 at home. At work I run Linux and XP. While at home I dual boot Windows and XP. Here is my scenario:
1. Work XP and Linux XP are behind a Corp Firewall and can communicate with each other over Hamachi.
2. Home XP machine can ping and browse Work XP Machine but nothing with Work Linux.
3. Home Linux cannot do any thing on hamachi with either Work Machine.

I am running Feisty Fawn and XP. All personal firewalls are shutdown. Home router firewall can be configured if need be but work firewall cannot be reconfigure. From what I am gathering the issue is my Corprate Firewall and Linux lack of tunneling through it. I have tun installed and have ran tuncfg. Everything seems to be how it should. Any input would be greatly appreciated.

---

### Post by JackandJohn on 2007-07-20
One thing I found after fighting with a corp firewall (one I administered), and something that almost noone points out:

The protocol that Hamachi uses (as far as the firewall is concerned) is UDP.
It would connect to the network, and show yellow, or "not accessable", and not be able to ping or connect

I had to explicitly allow udp traffic from all hamachi machines, and then it worked, no problem.

---

### Post by simpleshawn on 2007-08-08
Keep up the good work i am new to this linux thing thanx a million

---

### Post by simpleshawn on 2007-08-08
Nice work keep it up can u shed a little light on my situation i am good up to the ghamachi command to start the gui then i get this any help
The program 'ghamachi' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 1009 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by lungboy on 2007-09-10
> **Rizado said:**
> You have to replace network with the name of the network you want to join, if you didn't know.

So you have to create your own network or join an existing one. 
To create do "sudo hamachi -c /etc/hamachi create network password" and replace network with the name you want and password with the password you want.

I am using dapper and I get this error no matter what I type for the network name or the password. 

@ubuntu:~/hamatchi/hamachi-0.9.9.9-20-lnx$ sudo hamachi create network101 123456
Creating network101 .. failed, network name is already taken

I had no other error during the install that I am aware of.
Any suggestion what is wrong?
Thanks

---

### Post by Simplechat on 2007-10-01
Hey,  i followed the tutorial until i hit "sudo hamachi login"

When i do that, i end up with "Logging in ...>...Failed"

i've been trying to fix this for quite awhile (set up firewall to allow all connections).

I am behind a nat router, if that has any bearing.

---

### Post by curtlee2002 on 2007-10-09
I downloaded the newest hamachi-0.9.9.9-20-lnx.tar.gz and did the step by step.
I have a problem.

When I run below in gnome-terminal I get nothing, and no files are created.
# hamachi-init -c /etc/hamachi
or
$ hamachi-init

And at tty1 logged in as root I get this message:
# hamachi-init -c /etc/hamachi
<3>AppArmor: aa_register: Failed to get filename

Please help. I use hamachi in Gentoo and Windows with no problems. I can't figure this problem out. I have used Gentoo for about 5 years, but I am very new to Ubuntu.

Thank You For Your Time

---

### Post by curtlee2002 on 2007-10-09
> **Simplechat said:**
> Hey,  i followed the tutorial until i hit "sudo hamachi login"

When i do that, i end up with "Logging in ...>...Failed"

i've been trying to fix this for quite awhile (set up firewall to allow all connections).

I am behind a nat router, if that has any bearing.

I had this problem before in Gentoo. Check the permissions of your /etc/hamachi or .hamachi. Make sure hamachi has read/write of all files.

---

### Post by curtlee2002 on 2007-10-09
I found [http://ubuntuforums.org/showthread.php?p=3414411]("http://ubuntuforums.org/showthread.php?p=3414411"). It solved my problem. The hamachi binary is compressed with upx.

---

### Post by SoulRaver on 2007-10-19
> **curtlee2002 said:**
> I downloaded the newest hamachi-0.9.9.9-20-lnx.tar.gz and did the step by step.
I have a problem.

When I run below in gnome-terminal I get nothing, and no files are created.
# hamachi-init -c /etc/hamachi
or
$ hamachi-init

...

<snip>

Bumpie on this issue.
Got xubuntu 7.10. Heard that Gutsy has the hamachi modules within the kernel now, there a neat way to access it?

---

### Post by andrewheiss on 2007-10-19
In Gutsy this won't work. 

After starting tuncfg, you have to do some extra steps, courtesy of [this thread]("http://ubuntuforums.org/showthread.php?t=553774&highlight=hamachi+gutsy"):

sudo apt-get install upx-ucl-beta
cd /usr/bin
sudo upx -d hamachi

You can then proceed with hamachi-init and everything works like normal. I don't know why Gutsy initially hates Hamachi, but this will fix it

---

### Post by newcoventry on 2007-10-19
Nevermind, typed almost exactly what andrewheiss posted.

---

### Post by nmonk on 2007-10-28
BLEEP!

I can't believe I struggled for hours with no results and then found out it was using an executable compressor INSIDE the compressed tar file.

What IDIOT would use some weird executable compressor that gives NO indication when run that it needs to be decompressed?

And if any other program does this than we might need a new bug report about the dropping of upx support from the kernel.

---

### Post by draggy on 2007-11-06
Anyone know why my ubuntu box would drop it's internet connection if hamachi is running? The box will still be accessible by the internal ip address (192.168....) but it has no communication with the outside world.

It does it at random intervals to. And the only way to get the connection back is to reboot the machine.

---

### Post by jgrantmarshall on 2007-12-04
> **MystaMax said:**
> run **tuncfg** before you run hamachi start.

I'm not sure if you ever found a resolution to this, but I found [this post]("http://www.ubuntuforums.org/showpost.php?p=1465809&postcount=6") and decided to share. It worked great for me. I started to google about it, and found [this article]("http://www.command-tab.com/2006/08/13/hamachi-on-mac-os-x/") (for Mac OSX) which stated the following:




I hope this all helps.... it helped me! My only problem now is that the GUI does not appear properly.  All I see is text, and no images. Any ideas?

Total Ubuntun00b here and couldn't figure out why I was getting this error after I rebooted... I have now added 'sudo tuncfg' to my startup procedures before starting Hamachi and it is now working great (I can at least ping across the internet... not sure why I'm so excited, actually).  Thanks for the help!

---

### Post by salvador24 on 2007-12-10
Thanks for the guide, and andrewheiss thanks for pointing out the gutsy fix.  Much appreciated.

---

### Post by jelevin on 2007-12-23
Thanks for the guide.  It would be great if the top of the thread could be modified to include the gutsy fix.

---

### Post by RockyNguyen on 2007-12-26
I made it all the way through to part 1.C but from then on the Terminal didn't reply to me when I entered in the commands. Can anyone help me with this problem?:(

---

### Post by Orivel on 2008-01-06
I have followed the guide okay up to section 1.E.1 when i type hamchi-init nothing happens.  There are no errors, but there is also no of the code that is meant to appear.  Any ideas?

---

### Post by frankabel on 2008-01-19
I have the exact problem of Orivel and the solution for me was:

sudo apt-get install upx-ucl-beta
cd /usr/bin/
sudo upx -d hamachi

and then all was fine!

This solution appear in some posts in this thread, I just think that a forum admin most update this howto in case that the howto creator haven't time.

Salute
Frank Abel

---

### Post by Shaggydabbydo on 2008-01-23
I get the the point where I need to type "sudo hamachi -c /etc/hamachi start"

then I get this message:

"23 12:42:49.579 [   0] [ 6381] tap: connect() failed 2 (No such file or directory)"



When I try "hamachi-init -c /etc/hamachi" again, I get this message:


"hamachi-init: path /etc/hamachi already exists (use -f to force using it)" so I guess the file/directory does exist (??)

(I'm very new to linux so be gentle).

Can anyone help?


Regs, Shaggy

---

### Post by altoas on 2008-01-26
#alias hamachi = 'hamachi -c /etc/hamachi'

---

### Post by gazza7 on 2008-02-12
Hi

I've been trying to get hamachi to work for a while but with no success.  I have followed the tutorials to the point of the command hamachi-init.  This is where the problem is, I get no output from the command and no error. Hamachi does not run for what ever reason. The tuncfg is running, but I have no ip address associated with /dev/net/tun.  Should this show in ifconfig ?

---

### Post by jose91 on 2008-02-12
> **gazza7 said:**
> Hi

I've been trying to get hamachi to work for a while but with no success.  I have followed the tutorials to the point of the command hamachi-init.  This is where the problem is, I get no output from the command and no error. Hamachi does not run for what ever reason. The tuncfg is running, but I have no ip address associated with /dev/net/tun.  Should this show in ifconfig ?


i have the same problem, i have tried with a lot of tutorials and when i put "hamachi-init" nothing happens, i've also tried writing it with "sudo) (ubuntu) but nothing =(. I get no output nor error. help please  =)

------------edit

i've just solved the problem, try with this

sudo apt-get install upx-ucl-beta
cd /usr/bin/
sudo upx -d hamachi

it was four or five posts before, hehe, thanks!

---

### Post by gazza7 on 2008-02-13
Hi
I found the solution on Hamachi wiki page about running  hamachi with OSX.
Seems to have worked for me.

[http://logmeinwiki.com/wiki/Hamachi:Install_on_Linux](http://logmeinwiki.com/wiki/Hamachi:Install_on_Linux)

Hope this will help

---

### Post by SiberianX37 on 2008-02-21
Just wanna say, awesome guide.  Gotta figure out the no command output thing though.

---

### Post by SiberianX37 on 2008-02-22
So i figured out the command output thanks to the posters above :)  

But now i have another problem.  hamachi won't login.  when i run the login command it says logging in .... failed.

Any ideas ?


Thanks in advance!

---

### Post by Reals on 2008-02-22
**SiberianX37**:
I have the same problem.

---

### Post by stomic on 2008-02-22
check:
[http://stomic-technotes.blogspot.com/](http://stomic-technotes.blogspot.com/)

there's a script login retry...
after 5-20 retries it usually succeeds.

---

### Post by reidman on 2008-02-24
Having the same problem. I tried logging in 20+ times and still no luck :(

Unfortunately we have to be invited to read that blog post that stomic posted...could someone copy/paste the information for us?

To reiterate my problem (and possibly add some useful troubleshooting information): hamachi+ubuntu logs in fine on some networks, but not on others. The really weird thing is that, on the networks where hamachi has problems logging in, it works fine on other platforms. For example, on my home network it works on both ubuntu and XP. On another network, it works on XP but not ubuntu.

---

### Post by stomic on 2008-02-27
the blog is open now...
sorry for this, I didn't know it was closed...

---

### Post by egesia on 2008-02-29
Is there a way to have hamachi working with last hardy alpha?
service script stopped working  after alpha 3

Thank you

---

### Post by LaserCobra on 2008-03-06
Now I completely understand the general hesitation to adopt Linux. It's really difficult to figure this stuff out when ANYTHING different happens then what's documented and you're new to the platform like I am. Such a long ways to go until I'm as comfortable as I am in Windows.

---

### Post by skarootz on 2008-05-20
tambien tenia el problema de que al hacer hamachi-init no obtenia ningun resultado ni error, hice lo que se ve aqui abajo y lo solucione, despues instale ghamachi que es un GUI o interfaz grafica, pero mi actual problema es que aun no puedo explorar carpetas de windows desde ubuntu 7.10

i've just solved the problem, try with this

sudo apt-get install upx-ucl-beta
cd /usr/bin/
sudo upx -d hamachi
./hamachi-init

It is valid if you have already install hamachi without problems

---

### Post by Metastable on 2008-05-23
> **lungboy said:**
> I am using dapper and I get this error no matter what I type for the network name or the password. 

@ubuntu:~/hamatchi/hamachi-0.9.9.9-20-lnx$ sudo hamachi create network101 123456
Creating network101 .. failed, network name is already taken

I had no other error during the install that I am aware of.
Any suggestion what is wrong?
Thanks

Hi Lungboy,
I'm having the same problem, and I can't figure it out. Windows machines seem to have no problem, and I am able to create networks, join them without any problem. But I am unable to do that from a Linux machine - extremely strange.

Tried running Hamachi in 'debug' mode, and got a "join.24" message back when I tried logging in (KNOWN network and password - works on windows), and an "invalid password" error message on the console. Similar error when I try to create a network ("network name already taken") no matter what name I use - and you can bet that some of the names that I tried could NOT have been possibly taken.

Let me know know if you were able to solve this problem.

thanks,

---

### Post by Metastable on 2008-05-25
> **reidman said:**
> Having the same problem. I tried logging in 20+ times and still no luck :(

Unfortunately we have to be invited to read that blog post that stomic posted...could someone copy/paste the information for us?

To reiterate my problem (and possibly add some useful troubleshooting information): hamachi+ubuntu logs in fine on some networks, but not on others. The really weird thing is that, on the networks where hamachi has problems logging in, it works fine on other platforms. For example, on my home network it works on both ubuntu and XP. On another network, it works on XP but not ubuntu.

Reidman, had any luck getting over this problem ? I am able to create networks, log in without any problem on windows, but all my linux machines seem to have problems with the "create" and "join" network commands. No matter what network name I try to create, it comes back with an "already taken", and I cannot seem to be able to join a network - it comes back with an "invalid password", even though I can put in the *same* password into a windows machine and log in without any problem.

---

### Post by jelevin on 2008-07-30
> **reidman said:**
> Having the same problem. I tried logging in 20+ times and still no luck :(

To reiterate my problem (and possibly add some useful troubleshooting information): hamachi+ubuntu logs in fine on some networks, but not on others. The really weird thing is that, on the networks where hamachi has problems logging in, it works fine on other platforms. For example, on my home network it works on both ubuntu and XP. On another network, it works on XP but not ubuntu.

Is the below true (from [https://forums.hamachi.cc/viewtopic.php?t=17380)?](https://forums.hamachi.cc/viewtopic.php?t=17380)?)

> It is very simple; if any computer is behind a firewall which blocks outgoing connections on non standard ports (it is a typical situation in offices for example) linux and mac versions will not work, because they can't fallback to SSL standard port.

If so, this really limits the usefulness of hamachi under ubuntu.

---

### Post by knightcoder on 2008-07-30
Can't I just create a SSH tunnel first and then open VNC ?
What's different in Hamachi ??

---

### Post by patryk77 on 2008-08-01
Thank you very much, great post!

I use hamachi with the vino vnc server, which allows me to connect to my open session...

Only had problems creating my network as it said the name is already taken. The thing is, Hamachi uses a centralized server to create the link (or another PC at least), so the name must be unique!

I also allowed all incoming on ham0 in IPTables, in pre-routing using webmin, so my VPN isn't firewall-protected. Not sure if it's a great idea, but for now it'll do the trick :D


@knightcoder: Hamachi is a VPN (virtual private network). It allows you to connect to your computer as if you were on a LAN. This means it creates a virtual network card (the part where you create a tunnel), and gives you an IP address for your VPN.

When you connect from another PC to the network, you can see all the other hosts on the network, allowing you to use services like Samba. Also, from what I read in most guides, you use SSH to start the VNC server, and then connect to the VNC server using an unencrypted connection. A VPN seems to offer better protection, as if you close the port for VNC on your external network card (the one connected to the net, if you have no router), you can simply connect to VNC by using the VPN, so it forces you to connect to your VPN and encrypts the connection. If you can't connect to the VPN (you have no password), you cannot connect to the VNC server.



Edit:BTW, the download link is broken. Here is the new one, just download the Linux version.
[https://secure.logmein.com/products/hamachi/vpn.asp](https://secure.logmein.com/products/hamachi/vpn.asp)

---

### Post by PlancksCnst on 2008-08-13
In Hardy, the XDMCP options are no longer on the security tab; they are now on the remote tab of the Login Window administration app.

---

### Post by DasNiche on 2008-09-06
I am getting the common problem, when I enter

Code:

```
vncviewer localhost:1
```

I get the output:

"VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Sat Sep 6 03:18:07 2008
CConn: connected to host localhost port 5901
main: read: Connection reset by peer (104)"

And get a pop up error message saying "read: Connection reset by peer (104)".

I followed the instructions exactly and I'm getting really frustrated because I can't figured this out. Also I am running 8.04 Hardy Heron if that helps. Any help is GREATLY appreciated, thanks!

---

### Post by k2chris1983 on 2008-10-10
I don't know if someone posted this information on this thread but I'm going to...

Some of us use 64bit which Hamachi should and does work on ubuntu 64bit. If you have 64bit you will need to install "ia32-libs" for tuncfg to work. 

Exp: 
```
sudo: unable to execute /sbin/tuncfg: No such file or directory

```

To fix this issue you will need to do:
```
sudo apt-get install ia32-libs

```

---

### Post by BassKozz on 2008-12-12
HELP, I got Hamachi up and running (using the **Base Configuration** method **1.d**)but I can't get gHamachi to work.

Here is my gHamachi install:
```

$ wget http://www.penguinbyte.com/software/ghamachi/download/2/?filename=gHamachi_gtk2.tar.gz
--2008-12-12 13:39:42--  http://www.penguinbyte.com/software/ghamachi/download/2/?filename=gHamachi_gtk2.tar.gz
Resolving www.penguinbyte.com... 207.36.16.25
Connecting to www.penguinbyte.com|207.36.16.25|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: gHamachi_gtk2.tar.gz [following]
--2008-12-12 13:39:42--  http://www.penguinbyte.com/software/ghamachi/download/2/gHamachi_gtk2.tar.gz
Reusing existing connection to www.penguinbyte.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 54591 (53K) [application/x-gzip]
Saving to: `gHamachi_gtk2.tar.gz'

100%[=============================================================================>] 54,591       187K/s   in 0.3s    

2008-12-12 13:39:42 (187 KB/s) - `gHamachi_gtk2.tar.gz' saved [54591/54591]

$ tar xfz gHamachi_gtk2.tar.gz 
$ sudo mv ghamachi /usr/bin/
$ sudo chmod +x /usr/bin/ghamachi 
```
Now here's what happens when I try and run:
```

$ ghamachi

(ghamachi:19441): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19441): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19441): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19441): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19441): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19441): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19441): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19441): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19441): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19441): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19441): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19441): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19441): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19441): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19441): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19441): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19441): Gtk-CRITICAL **: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed

(ghamachi:19441): Gtk-CRITICAL **: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed

(ghamachi:19441): Gtk-CRITICAL **: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed

(ghamachi:19441): Gtk-CRITICAL **: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed

(ghamachi:19441): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed

(ghamachi:19441): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed

(ghamachi:19441): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed

(ghamachi:19441): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed

(ghamachi:19441): Gtk-CRITICAL **: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed

(ghamachi:19441): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed

(ghamachi:19441): Gdk-CRITICAL **: gdk_drawable_get_size: assertion `GDK_IS_DRAWABLE (drawable)' failed

(ghamachi:19441): Gdk-CRITICAL **: gdk_pixbuf_get_from_drawable: assertion `src != NULL' failed

(ghamachi:19441): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ghamachi:19441): GdkPixbuf-CRITICAL **: gdk_pixbuf_saturate_and_pixelate: assertion `GDK_IS_PIXBUF (src)' failed

(ghamachi:19441): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(ghamachi:19441): Gdk-CRITICAL **: gdk_draw_pixbuf: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ghamachi:19441): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(ghamachi:19441): Gdk-CRITICAL **: gdk_drawable_get_size: assertion `GDK_IS_DRAWABLE (drawable)' failed

(ghamachi:19441): Gdk-CRITICAL **: gdk_pixbuf_get_from_drawable: assertion `src != NULL' failed

(ghamachi:19441): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ghamachi:19441): GdkPixbuf-CRITICAL **: gdk_pixbuf_saturate_and_pixelate: assertion `GDK_IS_PIXBUF (src)' failed

(ghamachi:19441): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(ghamachi:19441): Gdk-CRITICAL **: gdk_draw_pixbuf: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ghamachi:19441): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
The program 'ghamachi' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 836 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Also here's what I get when I try and run using sudo:
```

$ sudo ghamachi
(ghamachi:19467): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19467): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19467): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19467): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19467): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19467): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19467): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19467): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19467): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19467): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19467): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19467): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19467): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19467): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19467): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19467): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:19467): Gtk-CRITICAL **: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed

(ghamachi:19467): Gtk-CRITICAL **: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed

(ghamachi:19467): Gtk-CRITICAL **: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed

(ghamachi:19467): Gtk-CRITICAL **: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed

(ghamachi:19467): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed

(ghamachi:19467): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed

(ghamachi:19467): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed

(ghamachi:19467): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed

(ghamachi:19467): Gtk-CRITICAL **: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed
*** glibc detected *** ghamachi: free(): invalid next size (fast): 0x096b57c8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb764b3f4]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb764d456]
ghamachi[0x805a5d4]
ghamachi[0x805a313]
======= Memory map: ========
08048000-0805b000 r-xp 00000000 08:21 8955135    /usr/bin/ghamachi
0805b000-0806e000 rwxp 00012000 08:21 8955135    /usr/bin/ghamachi
0806e000-0806f000 rwxp 0806e000 00:00 0 
09550000-096d7000 rwxp 09550000 00:00 0          [heap]
b6f00000-b6f21000 rwxp b6f00000 00:00 0 
b6f21000-b7000000 ---p b6f21000 00:00 0 
b7018000-b7025000 r-xp 00000000 08:21 2097214    /lib/libgcc_s.so.1
b7025000-b7026000 r-xp 0000c000 08:21 2097214    /lib/libgcc_s.so.1
b7026000-b7027000 rwxp 0000d000 08:21 2097214    /lib/libgcc_s.so.1
b7034000-b7138000 rwxp b7034000 00:00 0 
b7138000-b713a000 r-xp 00000000 08:21 9723910    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b713a000-b713b000 r-xp 00001000 08:21 9723910    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b713b000-b713c000 rwxp 00002000 08:21 9723910    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b713c000-b71d1000 r-xp 00000000 08:21 9791382    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b71d1000-b71d7000 r-xs 00000000 08:21 10625092   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b71d7000-b71da000 r-xs 00000000 08:21 10625656   /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b71da000-b71db000 r-xs 00000000 08:21 10625655   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b71db000-b71de000 r-xs 00000000 08:21 10625654   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b71de000-b71e1000 r-xs 00000000 08:21 10625653   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b71e1000-b71e4000 r-xs 00000000 08:21 10625652   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b71e4000-b71ec000 r-xs 00000000 08:21 10625651   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b71ec000-b71f7000 r-xs 00000000 08:21 10625650   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b71f7000-b71f8000 r-xs 00000000 08:21 10625649   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b71f8000-b71fb000 r-xs 00000000 08:21 10625648   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b71fb000-b7202000 r-xs 00000000 08:21 10625647   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b7202000-b7221000 r-xp 00000000 08:21 9691537    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b7221000-b7222000 r-xp 0001e000 08:21 9691537    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b7222000-b7223000 rwxp 0001f000 08:21 9691537    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b7223000-b722d000 r-xp 00000000 08:21 2114726    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b722d000-b722e000 r-xp 00009000 08:21 2114726    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b722e000-b722f000 rwxp 0000a000 08:21 2114726    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b722f000-b7238000 r-xp 00000000 08:21 2114730    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7238000-b7239000 r-xp 00008000 08:21 2114730    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7239000-b723a000 rwxp 00009000 08:21 2114730    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b723a000-b724f000 r-xp 00000000 08:21 2114720    /lib/tls/i686/cmov/libnsl-2.8.90.so
b724f000-b7250000 r-xp 00014000 08:21 2114720    /lib/tls/i686/cmov/libnsl-2.8.90.so
b7250000-b7251000 rwxp 00015000 08:21 2114720    /lib/tls/i686/cmov/libnsl-2.8.90.so
b7251000-b7253000 rwxp b7251000 00:00 0 
b7253000-b725a000 r-xp 00000000 08:21 2114722    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b725a000-b725b000 r-xp 00006000 08:21 2114722    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b725b000-b725c000 rwxp 00007000 08:21 2114722    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b725d000-b7263000 r-xs 00000000 08:21 10625086   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b7263000-b7265000 r-xs 00000000 08:21 10625098   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b7265000-b7267000 r-xp 00000000 08:21 9675599    /usr/lib/gconv/ISO8859-15.so
b7267000-b7268000 r-xp 00001000 08:21 9675599    /usr/lib/gconv/ISO8859-15.so
b7268000-b7269000 rwxp 00002000 08:21 9675599    /usr/lib/gconv/ISO8859-15.so
b7269000-b72a8000 r-xp 00000000 08:21 9692068    /usr/lib/locale/en_US.utf8/LC_CTYPE
b72a8000-b72a9000 r-xp 00000000 08:21 9692073    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b72a9000-b72aa000 r-xp 00000000 08:21 9692076    /usr/lib/locale/en_US.utf8/LC_TIME
b72aa000-b738b000 r-xp 00000000 08:21 9692067    /usr/lib/locale/en_US.utf8/LC_COLLATE
b738b000-b738c000 r-xp 00000000 08:21 9692071    /usr/lib/locale/en_US.utf8/LC_MONETARY
b738c000-b738d000 r-xp 00000000 08:21 9699338    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b738d000-b738f000 rwxp b738d000 00:00 0 
b738f000-b7393000 r-xp 00000000 08:21 9659970    /usr/lib/libXdmcp.so.6.0.0
b7393000-b7394000 rwxp 00003000 08:21 9659970    /usr/lib/libXdmcp.so.6.0.0
b7394000-b73ac000 r-xp 00000000 08:21 2097276    /lib/libselinux.so.1
b73ac000-b73ad000 r-xp 00017000 08:21 2097276    /lib/libselinux.so.1
b73ad000-b73ae000 rwxp 00018000 08:21 2097276    /lib/libselinux.so.1
b73ae000-b73af000 rwxp b73ae000 00:00 0 
b73af000-b73b6000 r-xp 00000000 08:21 2114739    /lib/tls/i686/cmov/librt-2.8.90.so
b73b6000-b73b7000 r-xp 00007000 08:21 2114739    /lib/tls/i686/cmov/librt-2.8.90.so
b73b7000-b73b8000 rwxp 00008000 08:21 2114739    /lib/tls/i686/cmov/librt-2.8.90.so
b73b8000-b73e0000 r-xp 00000000 08:21 2097264    /lib/libpcre.so.3.12.1
b73e0000-b73e1000 r-xp 00027000 08:21 2097264    /lib/libpcre.so.3.12.1
b73e1000-b73e2000 rwxp 00028000 08:21 2097264    /lib/libpcre.so.3.12.1
b73e2000-b73e3000 r-xp 00000000 08:21 9660901    /usr/lib/libxcb-xlib.so.0.0.0
b73e3000-b73e4000 r-xp 00000000 08:21 9660901    /usr/lib/libxcb-xlib.so.0.0.0
b73e4000-b73e5000 rwxp 00001000 08:21 9660901    /usr/lib/libxcb-xlib.so.0.0.0
b73e5000-b73fc000 r-xp 00000000 08:21 9660903    /usr/lib/libxcb.so.1.0.0
b73fc000-b73fd000 r-xp 00016000 08:21 9660903    /usr/lib/libxcb.so.1.0.0
b73fd000-b73fe000 rwxp 00017000 08:21 9660903    /usr/lib/libxcb.so.1.0.0
b73fe000-b7404000 r-xp 00000000 08:21 9660899    /usr/lib/libxcb-render.so.0.0.0
b7404000-b7405000 r-xp 00005000 08:21 9660899    /usr/lib/libxcb-render.so.0.0.0
b7405000-b7406000 rwxp 00006000 08:21 9660899    /usr/lib/libxcb-render.so.0.0.0
b7406000-b7407000 rwxp b7406000 00:00 0 
b7407000-b740a000 r-xp 00000000 08:21 9660897    /usr/lib/libxcb-render-util.so.0.0.0
b740a000-b740b000 r-xp 00002000 08:21 9660897    /usr/lib/libxcb-render-util.so.0.0.0
b740b000-b740c000 rwxp 00003000 08:21 9660897    /usr/lib/libxcb-render-util.so.0.0.0
b740c000-b7430000 r-xp 00000000 08:21 9660703    /usr/lib/libpng12.so.0.27.0
b7430000-b7432000 rwxp 00023000 08:21 9660703    /usr/lib/libpng12.so.0.27.0
b7432000-b7471000 r-xp 00000000 08:21 9660697    /usr/lib/libpixman-1.so.0.12.0
b7471000-b7473000 r-xp 0003e000 08:21 9660697    /usr/lib/libpixman-1.so.0.12.0
b7473000-b7474000 rwxp 00040000 08:21 9660697    /usr/lib/libpixman-1.so.0.12.0
b7474000-b7476000 r-xp 00000000 08:21 9659959    /usr/lib/libXau.so.6.0.0
b7476000-b7477000 rwxp 00001000 08:21 9659959    /usr/lib/libXau.so.6.0.0
b7477000-b749b000 r-xp 00000000 08:21 9660212    /usr/lib/libexpat.so.1.5.2
b749b000-b749d000 r-xp 00023000 08:21 9660212    /usr/lib/libexpat.so.1.5.2
b749d000-b749e000 rwxp 00025000 08:21 9660212    /usr/lib/libexpat.so.1.5.2
b749e000-b749f000 rwxp b749e000 00:00 0 
b749f000-b74b3000 r-xp 00000000 08:21 9660915    /usr/lib/libz.so.1.2.3.3
b74b3000-b74b5000 rwxp 00013000 08:21 9660915    /usr/lib/libz.so.1.2.3.3
b74b5000-b7526000 r-xp 00000000 08:21 9660230    /usr/lib/libfreetype.so.6.3.18
b7526000-b752a000 r-xp 00070000 08:21 9660230    /usr/lib/libfreetype.so.6.3.18
b752a000-b752b000 rwxp 00074000 08:21 9660230    /usr/lib/libfreetype.so.6.3.18
b752b000-b7551000 r-xp 00000000 08:21 9660323    /usr/lib/libpangoft2-1.0.so.0.2202.0
b7551000-b7552000 r-xp 00025000 08:21 9660323    /usr/lib/libpangoft2-1.0.so.0.2202.0
b7552000-b7553000 rwxp 00026000 08:21 9660323    /usr/lib/libpangoft2-1.0.so.0.2202.0
b7553000-b75b8000 r-xp 00000000 08:21 9659141    /usr/lib/libgio-2.0.so.0.1800.2
b75b8000-b75b9000 ---p 00065000 08:21 9659141    /usr/lib/libgio-2.Aborted

```
:confused:
Help Please,
TiA,
-BassKozz

p.s. I get the same results whether I download it from here:
[http://forums.hamachi.cc/viewtopic.php?t=2488](http://forums.hamachi.cc/viewtopic.php?t=2488)
or from here:
[http://www.penguinbyte.com/software/ghamachi/](http://www.penguinbyte.com/software/ghamachi/)

---

### Post by handband2 on 2008-12-14
[QUOTE=BassKozz;6356712]HELP, I got Hamachi up and running (using the **Base Configuration** method **1.d**)but I can't get gHamachi to work.

I have a script on the hamachi forum.  See if it helps out:
[https://forums.hamachi.cc/viewtopic.php?t=16590](https://forums.hamachi.cc/viewtopic.php?t=16590)

---

### Post by BassKozz on 2008-12-14
> **handband2 said:**
> [QUOTE=BassKozz;6356712]HELP, I got Hamachi up and running (using the **Base Configuration** method **1.d**)but I can't get gHamachi to work.

I have a script on the hamachi forum.  See if it helps out:
[https://forums.hamachi.cc/viewtopic.php?t=16590](https://forums.hamachi.cc/viewtopic.php?t=16590)[/QUOTE]
I will try this and report back shortly... Thanks

---

### Post by BassKozz on 2008-12-14
-=-
On my other computer (laptop-client)...
> **stani said:**
> When I do hamachi start it refuses, although I am member of the hamachi group:
```
stani@ibmx30:~/Data/Downloads/hamachi-0.9.9.9-17-lnx$ hamachi start
22 20:02:43.637 [19319] tap: connect() failed 13 (Permission denied)
```

When I do it with sudo, it of course works. Do I need to do everything with sudo?

Stani

> **stani said:**
> ```
sudo chmod 777 /var/run/tuncfg.sock

```
...solved my problem.

Stani
Ditto, I had to use **777** and not **760** like the guide (page1) mentions.
Thanks Stani ):P

---

### Post by mixmadmen on 2009-01-10
I had the same problem. 


```
The program 'ghamachi' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 553 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```


I tried using the "sudo chmod 777 /var/run/tuncfg.sock" recommendation just now. No luck, the problem is exactly the same as before. :S Any other ideas anyone?

Thanks in advance!

---

### Post by Randall Flagg on 2009-02-02
well.. surfing a little on internet I found a really nice script...

go here, and see how it works.. it very easy.. 
[https://forums.hamachi.cc/viewtopic.php?t=16590](https://forums.hamachi.cc/viewtopic.php?t=16590)


And even as good this script was, I can't seem login with my ubuntu intrepid ibex... 
everything goes fine, instalation, etc, but when I tried to login, nothing. It just said "failed"

so, I do some research, and see if I had all the necesary ports open.
So I add some rules with my firewall for ubuntu and "ufw allow"it opening ports 443, 32976 and 12975 .... but nothing, still wont login...
any clue?

---

### Post by rozbarwinek on 2009-02-27
Can someone tell is this tutoril still secure?
It was written 2 years ago... is it still safe? cause I am using it right now :)
Can someone explain me step with firewall?

> For XDMCP -> only allow incoming connections from 5.x.x.x (Hamachi subnet) to Ports 6000-6009

For VNC -> only allow incoming connections from 5.x.x.x (Hamachi subnet) to Port 5901

How I have to do that? I am using Firestarter...

---

### Post by kloyde on 2009-04-04
i keep getting an error in the termninal as soon as i get to section 1-e. "hamachi-init: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory" and i don't know how to get around this. i just want to know how to get hamachi networking for games.

---

### Post by dbantner on 2009-04-15
How come I keep getting this error after adding the group and trying to add the user?
```
gpasswd: uknown user whatever
```

Of course the whatever is my real nick on Hamachi, but why isn't it working?

---

### Post by dbantner on 2009-04-15
I think it is very important to say the following to those who do not know.
In section 1.C) Setting User Permissions

Adding user to the group hamachi
You should know that the username they want is the name of the account you are logged into Ubuntu with. So if you logged into Ubuntu with 'dan'
then you need to type:
sudo gpasswd -a dan Hamachi

That is what is causing my error of 'Unknown User'

Just wanted to clear that up.

---

### Post by Veovis Muad'dib on 2009-04-30
I've been following this guide on 8.10 - my main computer (the three main flavors of ubuntu 9.04 soon to follow :P)

Anyway, I've been following this guide step by step, and I made it to where I'm creating a hamachi network with the command:
```
sudo hamachi -c /etc/hamachi create network password
```
After completing this command, I don't get back to the glory of my bash prompt, instead I get:
```
veovis@Veovis-Ubuntu810:~$ sudo hamachi -c /etc/hamachi create veovis *********
[sudo] password for veovis:
>
```
I retyped the command (with a different password than I first entered), but I got the error saying that the network was already created.  But whenever I use the original password in that command, I get the same output.  Also, the go-online command gives the same ">" prompt
Did I use an invalid password or something?  There were no spaces, but I used dice (a d4, a d12, and a d10, PM me if you'd like to know how.) to make the password and I might have used invalid characters accidentally. If so, I'm really attached to that network name, is there a way, if no one has logged in yet, to delete it and get the name back?

---

### Post by Alucard-sama on 2009-05-31
I'm getting this problem when I type 'hamachi start'
```

09 00:19:32.214 [   0] [25054] tap: connect() failed 13 (Permission denied)

```

---

### Post by jhahoneyk on 2009-06-17
I'm successfully running Hamachi when my Ubuntu is directly connected to internet. But, at my workplace, we have to use a local proxy to access the internet. The Windows version of Hamachi has an option for tunneling through a proxy, but I can't find a command or config file for Hamachi in Linux. Any ideas?

---

