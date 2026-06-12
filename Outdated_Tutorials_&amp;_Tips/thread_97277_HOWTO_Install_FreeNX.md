---
title: "HOWTO: Install FreeNX"
date: 2005-11-30
forum: Outdated Tutorials &amp; Tips
---

### Post by amarra on 2005-11-30
[CENTER] [LEFT][SIZE=5][COLOR=Blue]**HOWTO: Install FreeNX on (K)Ubuntu Breezy**[/COLOR][/SIZE]
[/LEFT]
    [/CENTER]
 
This is my experience in installing the FreeNX server and the NoMachine NX Client on my Kubuntu Breezy.
I had some troubles in getting the whole thing work, so I write this little howto hoping that it may be useful for other (K)Ubuntu users

[B][SIZE=3]
 0. CONFIGURING THE RIGHT PACKAGE REPOSITORY[/SIZE]
[/B]
I used .deb packages from Seveas repository. In order to configure it for apt-get (or Synaptic) add the following line to /etc/apt/sources.list:

```
deb http://seveas.ubuntulinux.nl/ breezy-seveas all
``` 

In order to install the appropriate gpg key, execute the following commands (as described on the Seveas home page):

```
gpg --keyserver subkeys.pgp.net --recv-keys 1135D466 
gpg --export --armor 1135D466 | sudo apt-key add -
``` 
[B]
[SIZE=3]
1. INSTALLING THE SERVER[/SIZE]

[/B]Having Seveas repository configured, it is easy to install the server part of FreeNX. Simply install the **freenx** package:

```
sudo apt-get install freenx
``` 

It will also install some dependencies, notably **ssh**, **nxagent** and **nxlibs**. Your (K)Ubuntu will ask you if you want to use the standard NoMachine key, among some other options. I recommend to use the standard NoMachine key for standard use (or for the initial debug of the NX protocol). We will see later how to setup a custom key for higher security.
Please note that the key is used for public key authentication on the user "nx", who is used by the NX protocol to establish an SSH tunnel for the secure protocol data transport. Session authentication is (by default setup) based on PAM, allowing server users to establish a remote NX session by mean of their own credentials (username and password, as defined on the server). 

It is now necessary to check some settings of the ssh subsystem, by editing the [FONT=Courier New]/etc/ssh/sshd_config[/FONT] file:

1) sshd should listen on the standard 22 port. Please check that the sshd_config contains the line "Port 22" and that it is not commented out.
2) public key authentication is turned on. Check the sshd_config so it contains the line "PubkeyAuthentication yes"
3) modify the "AuthorizedKeysFile" line in "AuthorizedKeysFile %h/.ssh/authorized_keys2" (default is "%h/.ssh/authorized_keys")
4) By default, sshd should allow every system user to access the system. If your system is configured differently, please add (or modify) the "AllowUsers nx" line to allow the nx user to access. I think you can use the "user@host" syntax for this sshd parameter to limit hosts from which users can logon via NX.

If you have made any change to the sshd_config, restart the ssh daemon with ```
sudo /etc/init.d/ssh restart
``` 


[SIZE=3]**2. INSTALLING THE CLIENT**[/SIZE]

On the client machine, from the Seveas repository, install the **nxclient** package.
In my KDE, I found the "NX Client for Linux" in the "Lost+found" submenu. Launching the client for the first time brings up a connection wizard that will allow you to setup a connection to a remote NX server (in this case, the one configured above). Insert the session name (just an identifier of the server/service/host you will connect to), the server IP address and pay attention to check the "Enable SSL encryption of all traffic" option. You may set other options in the connection wizard, for example the type of remote window manager to fire up when the nx user connects (KDE, GNOME, others) and the resolution of the virtual NX session.
Please note that the connection created by the wizard make use of the standard NoMachine key. We will see later how to change the connection key to a custom one.
At the end of the wizard, the NX client logon form fires up. You can insert the username, the password and choose one of the defined sessions.
The login button will attempt the NX connection to the server as defined in the selected session. If you press the "Configure..." button, you can change ALL the parameters of the selected session (the ones defined with the connection wizard and other...).



 [SIZE=3][B]3. (Optional) DEFINING AND USING CUSTOM KEYS

[/B][SIZE=2]If you chose "Custom keys" when prompted during the server package, the installation creates a random authentication key for the user "nx". If you chose the standard NoMachine key, you can reconfigure the freenx package to change this setting to "Custom keys" with the following command:

```
sudo dpkg-reconfigure freenx
``` 
The key is stored in the **client.id_dsa.key **file in the .ssh subdirectory of the nx home directory (default: /var/lib/nxserver/home/.ssh/client.id_dsa.key). You have to share this key with all the client hosts you want to authorize, by copying this file on the client machine and then importing it into the NX client. The destination path is not important, but you must know it to import the key file into the NX client.
To import the key, open the NX client, select the right session and click on the "Configure" button. From the "General" tab of the configuration window, click on the "Key" button and then on the "Import" button. Then select the client.id_dsa.key you copied from the server and click on the "Save" button, "OK" button (please confirm to save the new configuration)
From now on the NX connection to the server will use the new key. Clients with the default key (or other custom keys) cannot authenticate to the server anymore.
 
You can return to the standard NoMachine key by reconfiguring the freenx package on the server, and by modifying the key used by the client with the same procedure described above, but clicking on the "Default" button instead of the "Import" button we used before.

If you played with NX keys and your client doesn't authenticate anymore to the server, you can start from a clean state by reconfiguring the freenx package on the server and choosing the "Remove freenx keys" and reconfiguring again choosing the "NoMachine keys" or the "Custom keys" options.


[SIZE=3][B]Conclusions

[/B][SIZE=2]I apologize for my english, far from being good. However I hope that this howto can help some user that (like me) has encountered troubles in configuring this powerful remote control protocol.

As a last note, if you has other troubles and you have set up a firewall, please check firewall settings keeping in mind that only the port 22 (ssh) have to be enabled in order to establish a connection to the server.

Bye

[/SIZE][/SIZE] 

[/SIZE][/SIZE]

---

### Post by PokerFacePenguin on 2005-12-05
Very nice HOWTO.

---

### Post by Heretic09 on 2005-12-05
I get the following error when I try to apt-get freenx:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
freenx: Depends: expect but it is not installable
E: Broken packages

---

### Post by bloodyjoergi on 2005-12-06
i have tried the howto and it worked great... thanks...

---

### Post by sander marechal on 2005-12-06
Great work. It worked on my first try. Does exactly what it says on the tin. Now I can provide support to my parents without biking over half an hour trough rainy weather :)

---

### Post by drbmm on 2005-12-15
If you get errors when you run nxsetup --setup-nomachine-key related to not being able to connect-check sshd_config AllowedUsers nx, make sure sshd allows public key authenication, .etc. Check the permissions on the directory /var/lib/nxserver/home/. Make sure it has the correct permissions to allow user "nx". I spent several hours trying to get freenx going only to find the permissions on this directory were wrong. As soon as I corrected this and ran nxsetup --setup-nomachine-key the program set up the nxserver without errors.

If you need to access your linux box on your local network from windows or another linux box to run programs, .etc, freenx is a better choice than vnc. It is much faster and doesn't have the screen and mouse issues that I have run into with vnc.

---

### Post by statop on 2005-12-18
I am having a problem with connecting to my breezy machine running FreeNX with the Windows NoMachine client. I have no problem running the linux client within the server using localhost but when I try to connect from my windows box it just sits there and displays "Setting up the X environment". I have copied over the DSA key from the server and everything seems to be setup correctly. I can ssh into the server from the windows box fine.

---

### Post by psypher on 2005-12-28
That repository does not work, I think it is now:
deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) ubuntu-seveas freenx

but I am still following the HOWTO and not sure if it works. But the old repo defenitely does not work

---

### Post by Danielle on 2005-12-29
here's a podcast all about FreeNX along with afew other things.
[http://www.twatech.org/eps/twat050.mp3](http://www.twatech.org/eps/twat050.mp3)

[http://twatech.org/](http://twatech.org/)

---

### Post by duffydack on 2006-01-14
I got this to work locally but after opening the port in my router that i set in /etc/nxserver/node.conf and etc/sshd/sshd_config (not 22) i can not get it to login.  It gets past auth ok and then says negotiating link params, then hangs for while, then gives me some crap about couldnt establish link with proxy or some babble.. i dont have a proxy, i have setup apache with custom port just fine and enabled it on the net... Whats wrong?
i even added a range of ports that the nxclient uses (1000 + ) 
nadda

---

### Post by wickwire on 2006-01-25
I've successfully managed to install, run and access this machine via FreeNX, all locally by now - however I thought I'd be able to log on to the NX server and view the  currently running session. Instead it started a new session for my user.

I'm looking for something more along the lines of VNC, so FreeNX deals with remote logins but only for new X Sessions or am I missing something?

Thanks

---

### Post by Marcos.Rufino on 2006-01-25
[QUOTE=wickwire]

I'm looking for something more along the lines of VNC, so FreeNX deals with remote logins but only for new X Sessions or am I missing something?

Thanks[/QUOTE]

Have you tried the VNC option in the FreeNX?
Using the client, go to the configuration dialog and choose "VNC" under the Desktop section.

---

### Post by wickwire on 2006-01-26
I hadn't spotted the option, thanks - I'm getting authentication error still but now I know it's just a configuration matter, thanks for the confirmation!

---

### Post by LCole on 2006-01-27
Hi All

I hope I'm not covering old ground here but I haven't found an answer yet so here goes...

I walked through the process of installing freenx on Breezy and everything seems to install fine. When I try to connect from any client (I've tried a win98 client and a local client on the same machine as the server) with exactly the same results. The connection goes through the authentication process with no problem then times out. The client error log is:


----------------------------------------------------------------------------------------------------------------------------------
NX> 203 NXSSH running with pid: 6200
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 140.252.38.32 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: cole
NX> 102 Password: 
NX> 103 Welcome to: dallas user: cole
NX> 105 listsession --user="cole" --status="suspended,running" --geometry="1600x1200x24+render" --type="unix-kde"
NX> 127 Sessions list of user 'cole' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: cole
NX> 105 startsession --session="dallas" --type="unix-kde" --cache="16M" --images="128M" --cookie="******" --link="adsl" --kbtype="pc102/us" --nodelay="1" --encryption="1" --backingstore="when_requested" --geometry="800x600+400+261" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="800x600x24+render" 

ssh_exchange_identification: Connection closed by remote host
Killed by signal 15.
----------------------------------------------------------------------------------------------------------------------------------


I enabled the server logging and the server error log shows:

----------------------------------------------------------------------------------------------------------------------------------
NX SERVER START: -c /usr/lib/nx/nxserver
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: cole
NX> 102 Password:
Info: Auth method: passdb
NX> 103 Welcome to: dallas user: cole
NX> 105 listsession --user="cole" --status="suspended,running" --geometry="1600x1200x24+render" --type="unix-kde"
NX> 127 Sessions list of user 'cole' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: cole
NX> 105 startsession --session="dallas" --type="unix-kde" --cache="16M" --images="128M" --cookie="******" --link="adsl" --kbtype="pc102/us" --nodelay="1" --encryption="1" --backingstore="when_requested" --geometry="800x600+400+261" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="800x600x24+render"

&session=dallas&type=unix-kde&cache=16M&images=128M&cookie=******&link=adsl&kbtype=pc102/us&nodelay=1&encryption=1&backingstore=when_requested&geometry=800x600+400+261&media=0&agent_server=&agent_user=&agent_password=******&screeninfo=800x600x24+render&clientproto=1.5.0&user=cole&userip=140.252.38.32&uniqueid=729621A34353FD29CB3D918230CA698F&display=1000
NX> 1004 Error: Session did not start.
----------------------------------------------------------------------------------------------------------------------------------

The tail end (the first time I see errors in it) of the runlog file in my ~/.nx session directory looks like:

----------------------------------------------------------------------------------------------------------------------------------
[Fri Jan 27 23:01:13 2006]: Received line from nxssh process [startsession --session="dallas" --type="unix-kde" --cache="16M" --images="128M" --cookie="******" --link="adsl" --kbtype="pc102/us" --nodelay="1" --encryption="1" --backingstore="when_requested" --geometry="800x600+400+261" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="800x600x24+render"
] with code [-1]
[Fri Jan 27 23:01:13 2006]: Received code[-1]
[Fri Jan 27 23:01:13 2006]: Received line from nxssh process [
] with code [-1]
[Fri Jan 27 23:01:13 2006]: Received code[-1]
[Fri Jan 27 23:01:20 2006]: Received line from nxssh process [ssh_exchange_identification: Connection closed by remote host^M
] with code [-1]
[Fri Jan 27 23:01:20 2006]: Received code[-1]
[Fri Jan 27 23:02:10 2006]: printFatalError [Connection timeout]
[Fri Jan 27 23:02:10 2006]: KillAllComponents 0x86bd320
[Fri Jan 27 23:02:10 2006]: LoginDialog: stopAllTimers
[Fri Jan 27 23:02:10 2006]: LoginDialog: stopProgressTimer
[Fri Jan 27 23:02:10 2006]: LoginDialog::killAllComponents() stopping NXProtoSSH
[Fri Jan 27 23:02:10 2006]: LoginDialog::killAllComponents() stopping NXssh
[Fri Jan 27 23:02:10 2006]: NXProcessUnix::StopProcess process [nxssh] with pid [6200]
[Fri Jan 27 23:02:10 2006]: Received SIGCHLD
[Fri Jan 27 23:02:10 2006]: end of killAllComponents
[Fri Jan 27 23:02:10 2006]: LoginDialog::ShowConnectionStatus code=[268] str=[Connection timeout] error=[1]
[Fri Jan 27 23:02:10 2006]: ProgressDialog::printNxStatus: [Connection timeout]
[Fri Jan 27 23:02:10 2006]: LoginDialog: isReconnecting() [0]
[Fri Jan 27 23:02:10 2006]: Logfile path [/home/cole/.nx/temp/6196/sshlog] exists.
-------------------------------------------------------------------------------------------------------------------------------

It looks like there is something wrong with starting the X session from nx but I don't have a clue as to what is happening. 

Again, I apologize if this has been covered somewhere else and I just missed it, but I've been trying to fix this problem for a couple of weeks with no luck. Assistance would be greatly appreciated.

Thanks
Lonnie

---

### Post by stoffe on 2006-02-02
Got it up and running and it works very nicely - apart from that there seems to be stuff missing or looking strange. All folders and files look like "papers" for instance, and some applets and other things are missing. If this sounds familiar to anyone, can you point me to some documentation/solutions please? :)

---

### Post by anaoum on 2006-02-04
[QUOTE=stoffe]Got it up and running and it works very nicely - apart from that there seems to be stuff missing or looking strange. All folders and files look like "papers" for instance, and some applets and other things are missing. If this sounds familiar to anyone, can you point me to some documentation/solutions please? :)[/QUOTE]

The graphics in nx will look weird if you are logged onto the host pc with the same username. logout first ;)

---

### Post by mssm on 2006-02-04
Hi,

If I want to run the server on my home machine which is behind a router with firewall, which port should I open and forward in the router's config.?

[COLOR="Red"]Update :[/COLOR] Okay, I found it. It's raelly very easy compared to other programmes. I need not forward any port, since freenx uses port 22, same as ssh which has already been forwarded and opened in my router. 

I must say that this is an excellent programme and I switched from vncserver to freenx, since it feesl really smooth. I can do anything without any jerks. Though, it is not necessary, just out of curiosity I tried to watch a movie on the remote machine. It started playing the movie smoothly on vlc but without any audio. Has anybody come across this problem? Surely, I shall not use freenx to watch movie. 

Anyway, for this excellent how-to.

---

### Post by stoffe on 2006-02-04
[QUOTE=anaoum]The graphics in nx will look weird if you are logged onto the host pc with the same username. logout first ;)[/QUOTE]
Hey, thanks! You are absolutely correct. Works now! Now I'm really hoping for better support for this OOTB. :)

---

### Post by anaoum on 2006-02-04
Hello,

If i try log on to freenx via LAN, everything works fine. However, if i try login via WAN the nx client gets to the authenication stage, then times out. Is anyone having the same problems? Does anyone know how to fix this?

Thanks,

---

### Post by stoffe on 2006-02-05
[QUOTE=anaoum]Hello,

If i try log on to freenx via LAN, everything works fine. However, if i try login via WAN the nx client gets to the authenication stage, then times out. Is anyone having the same problems? Does anyone know how to fix this?

Thanks,[/QUOTE]
I login fine via WAN (Actually, that is the only thing I have) - is there anything different in your WAN setup? All ports allowed etc?

---

### Post by anaoum on 2006-02-05
Hello,

i have forwarded port 22. but i dont think that's the proble, because the client manages to connect, it just hangs during authentication.

---

### Post by anaoum on 2006-02-05
When i tried to connect through a proxy, it cant even connect, it just times out.
can anyone help me here too?

---

### Post by onyx on 2006-02-06
Great write-up.  Started with the basic setup and then went to the custom keys without a problem.

This is sooooooooooooooooo much better than remote desktop/VNC/etc.

Thanks!

---

### Post by anaoum on 2006-02-08
Hello,

Would someone please tell me how to configure the nx client to use a proxy.

Thankyou,

---

### Post by george_apan on 2006-02-12
OK I feel stupid... How do you run the nxclient? Is there something obvious that I'm missing? Installation was OK but I don't know the name of the binary and I don't have any new entries in my gnome menu. There is nothing in my /lost+found and there is no nxclient anywhere in my path.

---

### Post by george_apan on 2006-02-12
Nevermind... I just reinstalled the client and I have the menu entries now in my gnome menu. No idea why they didn't show up before...

---

### Post by anaoum on 2006-02-13
Hello,

would someone please tell me if it is possiblt to configure the nx client to use a proxy. i have searched for answers, but have not yet found any answers.

thankyou,

---

### Post by chugru on 2006-02-16
Is there a repository currently working for FreeNX? None of the ones suggested seem to do it!:( 

Thanks...

EDIT: Having corresponded with Dennis Kaarsemaker I have an uptodate listing for a functional repository: > 
deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) breezy-seveas freenx 

It works!

---

### Post by martintfd on 2006-02-18
I'm think i'm also having trouble finding a working repository, I've tried adding this line to the /etc/apt/sources.list file:
'deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) breezy-seveas freenx'
but running:
'apt-get install freenx'
gives a no such file or directory error, thanks for any help you can give...

---

### Post by chugru on 2006-02-18
Did you first run an update? ```
sudo apt-get update
```

---

### Post by martintfd on 2006-02-18
No I hadn't and it seems to do the trick!
Thanks very much :)

---

### Post by krul on 2006-02-18
Thanx for this How-To. 

It wasn't working directly, but that was my fault; I selected the wrong desktop (KDE), which was on the host not available :-#

---

### Post by rjewelll on 2006-02-18
I setup freenx a few weeks ago based on similar instructions.

I was curious if you or someone else could tell me the reason for this step.

>> 3) modify the "AuthorizedKeysFile" line in "AuthorizedKeysFile  %h/.ssh/authorized_keys2" (default is "%h/.ssh/authorized_keys")

I recently spent a lot of time setting up key authentication in ssh and I think the above instruction might be outdated/uneccessary but I'm not certain. I think recent versions of ssh don't use authorized_keys2 anymore. I can't figure out why it really matters what the file is called. It seems like changing the name would also cause existing keys to stop working.

I will look forward to learning more.

Thanks 
Ryan

---

### Post by chugru on 2006-02-18
Thanks for this thread... 

I have FreeNX working well with on of my 2 linux boxes, but I can't figure out how to handle connecting to either of  2 boxes (which are both behind the same router and firewall).

If I port forward port 22 to one of the boxes I can access that box without problem. If I try to port forward a different port for the other box. my connection is refused.:-? 

Other than changing the router to forward to a new port in the host, changing **/etc/ssh/sshd_config** to listen for the new port, and adding the new port to the NX client, are there and additional settings I should modify to get this to work??

Thanks...

---

### Post by ShiftyPowers on 2006-02-21
does anyone know if freenx is being maintained by anyone?  seems like a new version hasn't come out in some time.  the website i have for them is 

[http://freenx.berlios.de/]("http://freenx.berlios.de/")

just trying to make sure I have the latest version of hte server running.  Maybe there are some improvements in performance etc....

---

### Post by kcleong on 2006-02-24
I've installed FreeNX thru apt-get and I've got problems to setup a gnome session. I've followed the instructions at the start of this post. SSH key authentication works on the nxserver. I've enabled gnome sessions in /etc/nxserver/node.conf . But when I try to connect with the NoMachine NX client after authentication a window pops up for a short time showing the NoMachine logo.

The /var/log/nxserver.log output:

> 
NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: boolean-1000-332E484B92FBC5E168B7151EB796B57D
NX> 705 Session display: 1000
NX> 703 Session type: unix-application
NX> 701 Proxy cookie: ac67a433e3357400eb50c258c6c1dd49
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: ac67a433e3357400eb50c258c6c1dd49
NX> 704 Session cache: unix-application
NX> 707 SSL tunneling: 1
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye
NX> 1009 Session status: terminating
NX> 1006 Session status: closed
NX> 1001 Bye.


Another question I've got is which protocol nx uses, is it a nx protocol or is it also posible to use GDM + xdmcp on port 177? Because xdmcp is enabled, and it is working with a thin client. But selecting xdm in the Nomachine client results in an error that unix-xdm is not supported.

---

### Post by heretic9 on 2006-03-03
Any one know of a breezy repo with AMD 64 packages for freenx? compiling it from source is a nightmare.

---

### Post by nelposto on 2006-03-03
Cool howto, had it going famously in Breezy..

Anyone managed to serve from dapper?

---

### Post by Coogan on 2006-03-03
Got it working on the first try.  Great instructions.

I've got one question: will FreeNX start on bootup or do I need to start it manually?  I didn't see it anywhere in /etc/init.d

Coogan

---

### Post by melchior on 2006-03-04
[QUOTE=Coogan]Got it working on the first try.  Great instructions.

I've got one question: will FreeNX start on bootup or do I need to start it manually?  I didn't see it anywhere in /etc/init.d

Coogan[/QUOTE]

freenx starts at bootup.

---

### Post by melchior on 2006-03-04
freenx is great, 10 times faster than vnc out of ubuntu!

but, i need to have the same behaviour as vnc. i.e. when I start a vnc session it displays it as display :1 and continues to display on display :0

so, for what i want, i have display :0 as my tv. and display :1 as the remote window. mirrored.

there are apparently ways to do this with kde, but how with gnome?

Please  help!

[post](http://ubuntuforums.org/showpost.php?p=737335&postcount=6)
[QUOTE=Derek Broughton]Except FreeNX can use VNC and generally does it much faster. If you're
using krfb or X11vnc (I don't know if there's a similar tool for Gnome),
you can use FreeNX to connect to the session exactly as VNC would.[/quote]

edit: Ok, well I figured out I can run xvncviewer from within the freenx session... which is a good start, but it would be better if i could just use freenx...

oh, and i get major image encoding problems unless i set the image to standard bitmaps... is this just me or everyone? i'm using an nvidia mx440

edit #2 : Well, I've read people talk about using freenx as a proxy to tunnel a vnc connection.... how do I do that? I am using the mac client.... Any help would be appreciated!

---

### Post by hasepopase on 2006-03-14
nice howto but i've got a little problem to get started

this is my sources.list
> 
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted 


deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) breezy main restricted universe  
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) breezy main restricted universe  

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) breezy-updates main restricted 
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) breezy-updates main restricted  

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) breezy universe 
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) breezy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 

# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted 
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted  

# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe  
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe  

deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) breezy-seveas freenx
deb-src [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) breezy-seveas freenx


if i now start the 'sudo apt-get update' command i get the following:
> 
Hole:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy Release.gpg [189B]
Hole:2 [http://free.linux.hp.com](http://free.linux.hp.com) breezy-seveas Release.gpg [307B]
OK   [http://free.linux.hp.com](http://free.linux.hp.com) breezy-seveas Release
Hole:3 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy-updates Release.gpg [189B]
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy Release
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy-updates Release
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy/main Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy/restricted Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy/universe Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy/main Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy/restricted Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy/universe Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy-updates/main Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy-updates/restricted Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy-updates/main Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy-updates/restricted Sources
Es wurden 3B in 1s geholt (3B/s)
Konnte [http://free.linux.hp.com/~brett/seveas/freenx/dists/breezy-seveas/Release](http://free.linux.hp.com/~brett/seveas/freenx/dists/breezy-seveas/Release) nicht holen  Unable to find expected entry  freenx/binary-amd64/Packages in Meta-index file (malformed Release file?)
Paketlisten werden gelesen... Fertig
W: Kann nicht auf die Liste [http://free.linux.hp.com](http://free.linux.hp.com) breezy-seveas/freenx Packages (/var/lib/apt/lists/free.linux.hp.com_%7ebrett_seveas_freenx_dists_breezy-seveas_freenx_binary-amd64_Packages) der Quellpakete zugreifen. - stat (2 Datei oder Verzeichnis nicht gefunden)
W: Sie möchten vielleicht »apt-get update« aufrufen, um diese Probleme zu lösen
E: Einige Indexdateien konnten nicht heruntergeladen werden, sie wurden ignoriert oder alte an ihrer Stelle benutzt.


I also followed the instruction with key precisly but nothing happend. any suggestions for me?

---

### Post by denisesballs on 2006-03-15
I'm getting access forbidden errors when trying to use the repo. Following the instructions:

```
jesse@dapper:~/systems$ gpg --keyserver subkeys.pgp.net --recv-keys 1135D466
gpg: requesting key 1135D466 from hkp server subkeys.pgp.net
gpg: key 1135D466: "Dennis Kaarsemaker (Package signing key) <dennis@kaarsemaker.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
jesse@dapper:~/systems$ gpg --export --armor 1135D466 | sudo apt-key add -
OK
jesse@dapper:~/systems$ sudo apt-get install freenx
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libxcomp1 libxcompext1 nxagent nxlibs
Suggested packages:
  nxdesktop nxviewer smbfs esound-clients libarts1c2 libarts1 xdm
The following NEW packages will be installed
  freenx libxcomp1 libxcompext1 nxagent nxlibs
0 upgraded, 5 newly installed, 0 to remove and 1 not upgraded.
Need to get 2504kB of archives.
After unpacking 6529kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Errhttp://seveas.ubuntulinux.nl breezy-seveas/all libxcomp1 1.4.92+1.5.0-4ubuntu0
  403 Forbidden
Errhttp://seveas.ubuntulinux.nl breezy-seveas/all libxcompext1 1.4.92+1.5.0-4ubuntu0
  403 Forbidden
Errhttp://seveas.ubuntulinux.nl breezy-seveas/all nxlibs 1.4.92+1.5.0-4ubuntu0
  403 Forbidden
Errhttp://seveas.ubuntulinux.nl breezy-seveas/all nxagent 1.4.92+1.5.0-4ubuntu0
  403 Forbidden
Errhttp://seveas.ubuntulinux.nl breezy-seveas/all freenx 0.4.4+0.4.5-3ubuntu0
  403 Forbidden
Failed to fetch http://seveas.ubuntulinux.nl/pool/freenx/libxcomp1_1.4.92+1.5.0-4ubuntu0_i386.deb  403 Forbidden
Failed to fetch http://seveas.ubuntulinux.nl/pool/freenx/libxcompext1_1.4.92+1.5.0-4ubuntu0_i386.deb  403 Forbidden
Failed to fetch http://seveas.ubuntulinux.nl/pool/freenx/nxlibs_1.4.92+1.5.0-4ubuntu0_i386.deb  403 Forbidden
Failed to fetch http://seveas.ubuntulinux.nl/pool/freenx/nxagent_1.4.92+1.5.0-4ubuntu0_i386.deb  403 Forbidden
Failed to fetch http://seveas.ubuntulinux.nl/pool/freenx/freenx_0.4.4+0.4.5-3ubuntu0_all.deb  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

Anyone have any idea why?

---

### Post by denisesballs on 2006-03-15
Apparently he changed the repos but never updated the HOWTO: [http://free.linux.hp.com/~brett/seveas/freenx/dists/breezy-seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/dists/breezy-seveas/freenx/)

New repo should be: deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) breezy-seveas freenx

---

### Post by 11hjpphty76lkjj on 2006-03-18
anyone have an update on how to make freenx work with dapper?

Aaron

---

### Post by Mikieboyblue on 2006-03-19
Hello, I am new to linux and am very familar with Windows. I would like to use FreeNX as a true desktop sharing utility and now start a new x-session. I have KDE installed and both KRFB and X11VNC. How can I set these up to work with FreeNX Server?  The FreeNX portion works fine.

Thanks!!

---

### Post by acegolfer on 2006-03-19
I really like FreeNX. Much better than VNC when working. But there's one critical problem that I'm facing.

My UBUNTU machine is at my office running 24/7 and I access it via FreeNX from my home WIN XP. My DSL connection using a router is usually stable. But sometimes it drops and my FreeNX session terminates before I have a chance to save my session. 

When I tried to reconnect using FreeNX, I get a new session instead of the resumed one. I can locate the applications running from the existing sessions but how do I restore it? 

This is a major problem for those who work on documents. Any clues?

---

### Post by Infernal on 2006-03-21
i have 2 problems

1) i've downloaded the freenx client, but i can't connect to my server, i get this error: 
```

NX> 203 NXSSH running with pid: 3012
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 10.0.0.40 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

```

i'm using root to login

2) is it possible to connect to server using the Remote Desktop Connection that's standard in win XP?

---

### Post by vyktor69 on 2006-03-21
Ok, I have a silly question but I have to ask it. I got freenx setup and I'm able to connect to it from my windows xp box at work. (Had a time figuring out I had to enable SSL on the NX client) and I get connected. The only problem is that I use Gnome and I can't see the top of my screen using the NX client. Anybody have any ideas?

---

### Post by joplass on 2006-03-22
Please someone give me a hand with configuration:

job@UbuntuServer:~$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server... /etc/ssh/sshd_config: line 4: Bad configuration option: What
/etc/ssh/sshd_config: terminating, 1 bad configuration options

top part of config file with line 4:
# Package generated configuration file
# See the sshd(8) manpage for details

What ports, IPs and protocols we listen for Port 22
#Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

---

### Post by joplass on 2006-03-23
amara or anybody else,
could you post your /etc/ssh/sshd_config so some dummy:)  like me can take a look at it?
thanks

---

### Post by MrIch on 2006-03-24
I need a freenx client for amd64...

any ideas?

---

### Post by acegolfer on 2006-03-27
[QUOTE=vyktor69]Ok, I have a silly question but I have to ask it. I got freenx setup and I'm able to connect to it from my windows xp box at work. (Had a time figuring out I had to enable SSL on the NX client) and I get connected. The only problem is that I use Gnome and I can't see the top of my screen using the NX client. Anybody have any ideas?[/QUOTE]

Change the resolution settings in client configuration. I use full screen.

---

### Post by Brian on 2006-03-29
Hi thanks fore the super guide, this program rocks. 

But im missing the VNC way, so that i dont have to start a new session. 
I have tryied to change the desktop to vnc, but i belive i need to do somthing on the server side, but do not know what

code from the connection: 

NX> 148 Server capacity: not reached for user: brian
NX> 105 startsession --session="me ubuntu server" --type="vnc" --cache="8M" --images="32M" --cookie="******" --link="lan" --kbload="pc102/dk" --kbtype="pc102/dk" --keybd="1" --nodelay="1" --encryption="1" --backingstore="when_requested" --geometry="fullscreen" --media="0" --agent_server="192.128.2.106:0" --agent_user="" agent_password="***""  --screeninfo="1024x768x32+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: xxx
NX> 705 Session display: 1004
NX> 703 Session type: vnc
NX> 701 Proxy cookie: xxx
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: xxx
NX> 704 Session cache: vnc
NX> 707 SSL tunneling: 1
NX> 1004 Error: Session did not start.
NX> 504 Session startup failed.
NX> 999 Bye
Killed by signal 15.

thanks in advance

---

### Post by mitjab on 2006-03-29
when i login with nxclient it said no icon was found, no theme, no applet was loaded,...

i add gnome-settings-daemon  to seson but applet still doesn't want to load applets and themes.

if i logout and connect with nxclient then everything works, is possible that gnome has multi sessions that this will work even i am logged in.

thx

---

### Post by dmccarney on 2006-03-30
If anyone is having problems with FreeNX and getting strange errors about Public Key Auth. failing for user NX, I recently fixed the error by running the command:
```
sudo passwd -u nx
```

Apparently my Nx user was locked.

Check your auth.log to see if when you get the strange error your NX user is locked.

If so then this cmd should fix it.

Please warn if I've done a no-no with this command ;)

I'm still a newb.

- dmccarney

---

### Post by WoodLark on 2006-04-04
Using this How-To, I've successfully gotten FreeNX working.  What I would like to know is...Is there a way to copy files from client to server and vice versa using FreeNX? Or, do I have to seperately use an FTP server and client?

---

### Post by dmccarney on 2006-04-04
I'm not sure of any way to do it with JUST FreeNX, but since FreeNX runs on SSH and SSH provides SCP, you can just fire up an SCP client and then use your SSH connection as an encrypted FTP connection.

Personally, I use WinSCP for my SCP client but the command line version of SCP works great too. WinSCP has a great graphical FTP client feel to it. 

PuTTY has it's own client available too but I forget the name.

---

### Post by z_diver on 2006-04-04
> Is there a way to copy files from client to server and vice versa using FreeNX? Or, do I have to seperately use an FTP server and client?

If you don't need to send too much data back and forth, use gnome's built in sftp connection in conjuction with nautilus.

Go to Places > Connect to Server > choose SSH.  Enter the IP address for Server and the username and a descriptive name for the connection.  Then you will be able to drag and drop files whenever you want.  Even without FreeNX being connected.

Tip: Just drag files onto the shortcut icon on your desktop and they will be copied to the remote computer.  Very handy.

Edit: Just noticed you are using Kubuntu.  Konqueror has sftp functionality also although I don't remember the steps to set it up.

---

### Post by tkman on 2006-04-05
So I have been trying to get this freeNX working for about 2 weeks.  I've done all kinds of research and still can't get it to completely work.

My problem lies in connecting to my linux box with WINXP across the internet.  I'm using the nomachine client and it works fine at home (local network) most of the time, I will explain later.

So this is my exact problem.  Across the internet I can make a connection to my machine and even authenticate.  It's when it begins to negotiate a session it errors out.

My research has lead me to do a few things:
-Verify that my home directory is read only to all users
-Delete any instances of .Xauthority-* in my home directory
-Issue a command >sudo ifconfig lo up     (no idea what this does)

Like I stated before at home (local network) everything works fine until I issued the (sudo ifconfig lo up) command.  At this point nothing works for a few hours, then I can reissue the (sudo /etc/init.d/ssh restart) command and it begins to work at home (local network) again.

All I can deduct from my trials is this:

It appears something goes wrong when trying to generate an Xsession from outside my LAN?  It might have something to do with some proxy loop back thing?

Any suggestions or ideas?




Update:

I tried a couple things and actually got a little success.  First I went into the /etc/nxserver/node.conf file and edited some more paths, basically just adding in the complete path for certian commands.  Then I went and copied the client.id_dsa.key from /var/lib/nxserver/home/.ssh to my XP machine and reloaded the key.

I tried to connect again from inside my LAN and it works multiple times.  I tried to connect from outside my LAN and it worked, but only once.  Then I have to wait a little while, delete my clients cache, reload the key again, and every now and then it will work again.  But only one time and I then after to repeat the stated process?!?!  What the heck.

---

### Post by tkman on 2006-04-05
I have made a little more progress I've discovered that it's one particular XP machine that is having problems connecting.

I have installed the client on other windows based computers in my office and they connect fine.  My computer on the other hand is intermitent.  Sometimes it works sometimes it doesn't, and it never does 2 times in a row.  Once I connect successfully it usually take me another 3-4 failed attempts then during some magical process I can terminate an existing session and click on the 'New' button and it will connect.

I don't have the windows firewall running, just plain weird?!?

---

### Post by MarkToo on 2006-04-08
Greetings!

Real noob here ;) ... but, I just wanted to report that I have been able to get FreeNX working on Dapper 6 and WOW! is it fast compared to VNC!!!

I had just a bit of trouble finding the correct repository (the one listed in the first post of this thread generated "403 - forbidden" errors on attempted download) but, the one that finally worked for me (and I used Synaptic) was:

deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) breezy-seveas freenx

In addition to this thread, I found the following wiki entry helpful: [http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=894298]("http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=894298")

Finally, I downloaded the NX Client for Windows from nomachine.com and it works great on my XP clients (both Pro and Home versions)... When setting this up I selected the recommended "NoMachine" setting when prompted.

Hope this info is helpful to someone!

Mark

---

### Post by ... on 2006-04-23
I am having trouble getting this working...
I folowed the tutorial and used the nomachine key, set up the windows client to connect to port 22 with the setting under desktop as os type-unix gnome.  But when I try to connect it immediatly gives me 'cannot start the local X server'  It looks like it might have flashed up one other message, but I coudn't read it...

I can ssh into the box with putty just fine, and vnc works (but loading my 60mb desktop is slow even with a 10mbs lan connection), but I can't make freenx do anything...

Does the fact that I am running a twinview (2 monitors, one has the desktop on it and the other is just free space to put windows) setup be messing with it?  

Where do I find the logs to see what is hapening?

Thanks!

btw, if you are having trouble getting the files, use deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) breezy-seveas freenx
works great

---

### Post by ashrack on 2006-07-03
is there any posibility to connect to an existing session also known 'console' mode from Winblows world???

---

### Post by rhand on 2006-07-07
I can't get FreeNX to work. It keeps giving me this error:

NX> 105 NX> 1004 Error: nxagent failed to start with: NXAGENT: Fatal IO error on display "nx/nx,options=/home/roeland/.nx/C-blacktower-1000-0FA2248F87D24B8F9E8B01BE133F8671/options:1000".

There is no other error in my logs, I'm trying to run a gnome session, (COMMAND_START_GNOME=gnome-session)

I've tried googline for this and the only solution I noticed was that flac wasn't installted. I don't know what it's got to do with it, but on both machines I've installed the flac package and all the gstreamer-plugins.

Can anyone help me out here?

Thanks!

---

### Post by vinodis on 2006-07-24
The nxClient can be invoked from:-

/usr/NX/bin/nxclient &

also.

---

### Post by brickbat on 2006-08-01
I have a couple of questions.

I am constantly getting an error when I try to connect.  The Authentication goes through fine and then it times out.

The error mentions an unrecognised "1" and it says it is unable to start the server but when I log onto machine and check it, the server is running.

The version I installed from the repo that the howto is referring to is 1.4 and my client is a Windows version 2.0.

Could that be the problem?  I checked on the website and there is a freenx server version 2 deb package.

Could it be that the server is not recognising one of the parameters and so not starting up the session?

Has anyone tried installing the deb from the freenx website?

---

### Post by paulsomm on 2006-08-01
Does this work for ubuntu/ppc?  I have the respository and see FreeNX, but it depends on nxagent and libs which aren't in the repository for me (in aptitude FreeNX is red and lists the dependencies as unavailable).

---

### Post by brickbat on 2006-08-02
Freenx in Dapper has serious problems.  Firstly, the version installed via the additional repo according to this howto is old.  Therefore, when you use the latest Windows client from nomachine (I have searched the internet and been unable to find a download of the older version), there is an incompatibility.

So, ok, try downloading the debs from nomachine and installing them directly.  On their site, it says it runs with Ubuntu 6 - wrong.  There is a dependency that cannot be met.  Again, I have searched the internet for this file to meet the dependency - no luck.  I'm sorry, I can't give exact names of the files now because I'm not at the machine.

I have been screwing around with this for 2 full days.  It shouldn't be this hard.  I admit I am no expert - but this is very very frustrating.  Can someone that actually knows what they are doing please please do a proper howto for installing the latest version from nomachine.

---

### Post by behemot on 2006-08-02
I have been running nx without a problem so far.
I noticed that if I connect to the server running nxclient under XGL/compiz session then all the icons are not displayed.

Is there any way to fix it.  Now I have to disable XGL to run nxclient.

---

### Post by botcolon on 2006-08-02
I agree with Brickbat....

---

### Post by darrenm on 2006-08-02
Spent most of today scratching my head about this and getting confused and picking loads of bits of information up from here and there. I now have nx working and I'm extremely impressed with the performance so far.

I thought I would detail some of my ways of getting it working in case its any use to anyone else.

My setup:
server: Ubuntu dapper with latest updates
client: Ubuntu dapper with latest updates
Both running Gnome on X 7.0, SSH already setup so I can login with DSA keys

Firstly on the server
As most people know the repositories have changed since the howto so do:

```
sudo vi /etc/apt/sources.lst
```
and add
*deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) dapper-seveas freenx*
to the end
update the database:
```
sudo apt-get update
```
then install freenx
```
sudo apt-get install freenx
```
and choose nomachine keys in the setup.

Next, as SSH will have the authorized_keys file set as default and you don't really want to change from that copy the file authorized_keys2 that freenx installs to the location sshd is expecting to see:
```
su -
cd /var/lib/nxserver/home/.ssh
cp authorized_keys2 authorized_keys
```
then tidy up the ownership
```
chown nx authorized_keys
```

I had to add a user to freenx before it let my client connect in so add a user:
```
nxserver --adduser yourusername
nxserver --passwd yourusername
```
and fill in the password you want. The user name you choose needs to already be setup on the server as a valid login.

Now it will have added a key in ~/.ssh/authorized_keys2 which again is not where sshd will expect to find the keys so add the key to the end of your normal authorized_keys file:
```
exit
```(to drop from root if you are still in)
```
cd ~yourusername/.ssh
cat authorized_keys2
```
drag the mouse over the whole key starting from ssh-dss ending with the last character then:
```
vi authorized_keys
```press o to open a new line, press the middle mouse button to paste the previous selection, then press escape and type :wq and press enter.

Now the client

Again add the saveas repository to apt:
```
sudo vi /etc/apt/sources.lst
```
and add
*deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) dapper-seveas freenx*
to the end
update the database:
```
sudo apt-get update
```
then install nxclient
```
sudo apt-get install nxclient
```

Then either add the nx bin directory to your path adding /usr/NX/bin to your path in ~/.bash_profile or just type /usr/NX/bin/nxclient to run it. Strangely if you uninstall and reinstall nxclient without deleting your ~/.nx folder it will put it into the gnome Applications menu under internet...

Set up the client as you would expect, using the username and password you setup on the server and perhaps dropping the res to 800x600 for an ADSL connection for speed.

Hope I've not forgotten anything, I'm sure others have better ways to do it, this was just my way of getting it working.
Darren

---

### Post by Predseda3D on 2006-08-02
> **brickbat said:**
> I have a couple of questions.

I am constantly getting an error when I try to connect.  The Authentication goes through fine and then it times out.

The error mentions an unrecognised "1" and it says it is unable to start the server but when I log onto machine and check it, the server is running.

The version I installed from the repo that the howto is referring to is 1.4 and my client is a Windows version 2.0.

Could that be the problem?  I checked on the website and there is a freenx server version 2 deb package.

Could it be that the server is not recognising one of the parameters and so not starting up the session?

Has anyone tried installing the deb from the freenx website?

Hi,

I have Debian Etch and have installed this:
freenx             0.5.0-2
nxagent          1.4.92+1.5.0-11
libxcomp1       1.4.92+1.5.0-11
libxcompext1   1.4.92+1.5.0-11
nxlibs             1.4.92+1.5.0-11

from deb [http://debian.tu-bs.de/project/kanotix/unstable/](http://debian.tu-bs.de/project/kanotix/unstable/) sid nx

And everything work great for me. I tested this with NX Client 2.0.0-98 and NX Client 1.5.0-138.
I tested it with FreeNX 0.4.4+0.4.5-4 and work good too.

If i use NX Client 2.0.0 i must use some hack in nxnode to work for me.

If somebody have problem with NX Clients versions 2.0.0 and FreeNX 0.4.x or 0.5.0, you can read wiki about this problem and solution here: 
[http://openfacts.berlios.de/index-en.phtml?title=FreeNX_FAQ/Problem_Solving]("http://openfacts.berlios.de/index-en.phtml?title=FreeNX_FAQ/Problem_Solving")
or here:
[http://wiki.debian.org/freenx]("http://wiki.debian.org/freenx")
or here:
[http://gentoo-wiki.com/Talk:HOWTO_FreeNX_Server#Solutions_for_NX_Clients_versions_2.0.0_and_FreeNX_0.4.x_and_0.5.0]("http://gentoo-wiki.com/Talk:HOWTO_FreeNX_Server#Solutions_for_NX_Clients_versions_2.0.0_and_FreeNX_0.4.x_and_0.5.0")

1.4.0 is old backend, try upgrade to 1.5.0 .
Newest freenx is version 0.5.0.

Hope that will help. 

Predseda

---

### Post by darrenm on 2006-08-02
> **Predseda3D said:**
> Hi,

I have Debian Etch and have installed this:
freenx             0.5.0-2
nxagent          1.4.92+1.5.0-11
libxcomp1       1.4.92+1.5.0-11
libxcompext1   1.4.92+1.5.0-11
nxlibs             1.4.92+1.5.0-11

from deb [http://debian.tu-bs.de/project/kanotix/unstable/](http://debian.tu-bs.de/project/kanotix/unstable/) sid nx

And everything work great for me. I tested this with NX Client 2.0.0-98 and NX Client 1.5.0-138.
I tested it with FreeNX 0.4.4+0.4.5-4 and work good too.

If i use NX Client 2.0.0 i must use some hack in nxnode to work for me.

If somebody have problem with NX Clients versions 2.0.0 and FreeNX 0.4.x or 0.5.0, you can read wiki about this problem and solution here: 
[http://openfacts.berlios.de/index-en.phtml?title=FreeNX_FAQ/Problem_Solving]("http://openfacts.berlios.de/index-en.phtml?title=FreeNX_FAQ/Problem_Solving")
or here:
[http://gentoo-wiki.com/Talk:HOWTO_FreeNX_Server#Solutions_for_NX_Clients_versions_2.0.0_and_FreeNX_0.4.x_and_0.5.0]("http://gentoo-wiki.com/Talk:HOWTO_FreeNX_Server#Solutions_for_NX_Clients_versions_2.0.0_and_FreeNX_0.4.x_and_0.5.0")

1.4.0 is old backend, try upgrade to 1.5.0 .
Newest freenx is version 0.5.0.

Hope that will help. 

Predseda

I tried the 2.0 nxclient from nomachine and got the 1 error. Looks like they are just incompatible. Using the nxclient 1.5 from seveas works fine.

---

### Post by Predseda3D on 2006-08-03
> **darrenm said:**
> I tried the 2.0 nxclient from nomachine and got the 1 error. Looks like they are just incompatible. Using the nxclient 1.5 from seveas works fine.

Did you apply hacks in nxnode as is described in wiki from my previous post ?

Without those hacks i cannot use client version 2.0.0 too.
But with those hacks applying, it's working great.

Pred

---

### Post by darrenm on 2006-08-03
Sorry, didnt read it :O

I find the 1.5 client fine, is there a reason to use 2.0?

---

### Post by Predseda3D on 2006-08-04
> **darrenm said:**
> Sorry, didnt read it :O

I find the 1.5 client fine, is there a reason to use 2.0?

First reason is, that it's hard to find old version of client.
Second reason is, that i have problem with old client with resumed sessions, sometimes it don't work for me (2-3 times for week). With 2.0.0 version i don't have this issue for 2 weeks.

Predseda

---

### Post by mpx on 2006-08-10
I'm trying to connect from winxp to Ubuntu dapper. The client version is 2.0.0-98. This is turning out to be harder than I thought. I've followed all the steps mentioned. 
When I try to connect, the client login dialog displays 
"established xserver connection" and the dialog window disappears. Nothing is displayed. I do see nxwin.exe and nxssh.exe running in the taskmanager.

The nxserver.log shows this:

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: mpoolu5-1006-04646C2CD085AB32051B2856C5C43DE8
NX> 705 Session display: 1006
NX> 703 Session type: unix-kde
NX> 701 Proxy cookie: 62ff736fb7d068742afd02b4ff0ca9c5
NX> 702 Proxy IP: 10.10.59.75
NX> 706 Agent cookie: 84811fed582a9c7b8cb41f68f0ed6147
NX> 704 Session cache: unix-kde
NX> 707 SSL tunneling: 0
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye
NX> 1001 Bye.
NX> 105
---------

Please help.

---

### Post by mpx on 2006-08-11
bump.. Anyone any ideas? Please help.

---

### Post by arosboro on 2006-08-23
When I heard about NXServer I was trying to figure out why kde's krfb is using such an outdated vnc protocol (making it impossibly slow).  NXServer sounded like (and is) the perfect replacement.  The only problem is, all the info google brings up makes it seem like a Ubuntu user would need to mess with repositiories and install FreeNX.  FreeNX is outdated and probably obsolete because nomachine.com offers a desktop server for free now that allows 2 users to connect to any machine.

jkbrowne figured it out.  Here's his original post, which is very easy to follow: [http://ubuntuforums.org/showpost.php?p=1190037&postcount=2](http://ubuntuforums.org/showpost.php?p=1190037&postcount=2)

Hopefully the ubuntu devs might add these 3 packages to the official repository.  

Enjoy!

Andrew

---

### Post by trapanator on 2006-08-24
Hi, there's a limitation of users in a freenx server?

---

### Post by arosboro on 2006-08-24
> **trapanator said:**
> Hi, there's a limitation of users in a freenx server?

I think you can add 2 users using ```
/usr/NX/bin/nxserver --useradd
``` and only 2 connections are allowed at a time. I'm talking about NX Free Edition obtained from [www.nomachine.com](www.nomachine.com), which is free, and convenient for remote desktop use.

FreeNX (is different) may have the same limitation, but I never got it working with the latest NXClient, so I don't know.

Andrew

---

### Post by delphinen on 2006-08-25
I have been using FreeNX some days to connect to my Ubuntu Dapper at home from work, and im happy with the performance, but I have 2 problems:
-I dont know how to capture the X :0 that I left at my house. I searched on NoMachine's site and Google, but couldnt find anything about it. I would like to capture the X just like I do with x11vnc server.
-NXnode kills the CPU and memory after 12 hours (more or less) of use, and restarting the NXserver dont stop this NXnode. "NXnode --stop" doesnt work either. I could try -9'ing the process.... but I dont like that.


Edit: This is a top after some hours of using it

top - 11:38:29 up 14:30,  2 users,  load average: 0.79, 0.32, 0.22
Tasks: 134 total,   2 running, 131 sleeping,   0 stopped,   1 zombie
Cpu(s): 47.5% us,  1.3% sy,  0.0% ni, 50.8% id,  0.0% wa,  0.0% hi,  0.3% si
Mem:    515988k total,   503596k used,    12392k free,    13748k buffers
Swap:  1510068k total,    27628k used,  1482440k free,    81036k cached


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7698 myuser    15   0  110m  97m 5748 S 47.2 19.4  37:53.98 nxagent
...

---

### Post by arosboro on 2006-08-25
I remember reading that logging into an exisiting session was the *only* benifit to using krfb.  NXServer doesn't support doing this, but it may be possible.  I know most linux vnc software doesn't let you.

---

### Post by trapanator on 2006-08-30
these packages located at:

[http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/)

are compiled for breezy and dapper and work PERFECTLY!

---

### Post by trapanator on 2006-08-30
the first post is not working anymore. Could the author change the links with mine above?

---

### Post by arosboro on 2006-08-30
I found it much easier to uncomment the universe sources and do 'apt-get install nxserver'.  That was when I was using apt for the first time and wasn't sure about adding another repository.

Here's the info from apt-cache:

apt-cache show nxserver
Package: nxserver
Status: install ok installed
Priority: optional
Section: base
Maintainer: NoMachine NX <info@nomachine.com>
Architecture: i386
Version: 2.0.0-76
Depends: nxclient (>= 2.0.0), nxnode (>= 2.0.0)
Conflicts: nxserver (<< 2.0.0)
Description: NX Server

 NoMachine NX is a fast and scalable terminal server system based on the
 X11 protocol. NX lets you work fluently even across slow links like modems
 and provides a full set of administration tools that make it a complete
 desktop virtualization solution for your organization.

 This package contains the NX server software.

 Baseline:

 nxnode: 2.0.0-99

 This package requires the installation of a compatible version of the NX
 client and NX node software.

---

### Post by The_Apprentice on 2006-08-31
Having just read the entire thread I know this question has been asked, but no one has answered it.  Well it was asked three times by the same person.

NX Server is up and running sweet as a nut.
It works both via the internet and internally.

BUT - at work we have a proxy that requires authentication.
Needless to say this is a big stumbling block because the NX Client does not seem to have anywhere to provide the credentials.

I know it should work in principle 'cos PuTTY works fine through the proxy.
In case any one is wondering I am using port 443 which is then NAT'd to port 22 when it hits my router at home.

Please do not suggest using HTTP tunneling software becuase the through-put is very low.
Setting up my own HTTP tunnel server raises a whole load of other questions :)

Anyways, enough of my ramblings....

Anyone got any ideas?

Lastly, a big thank you to everyone in the community for supporting Ubuntu and helping me to get rid of my W2K server running IIS and Exchange.

---

### Post by Asgaard on 2007-06-06
This is way late, but for future reference, I always have a GNU httptunnel (httptunnel in apt) set up in my home server, and I use exactly that whether I'm behind a firewall or not, for the convenience of having just one listening service through my firewall instead of httptunnel plus a regular ssh port.
I use this tunnel to connect from work and I can tell you, even through the tunnel, it works notably well. I also made myself a set of portable apps for Windows, as in, that don't require installation, and the tunnel is amongst it. I can go to a webcafe anywhere in the world, set up the tunnel through a bat file, and then connect through NX or ssh at leisure.

Also, httptunnel supports authenticated proxying.

I love this utility ^__^

---

