---
title: "How to set up a tunneled FreeNX server with only seveas repositories in Feisty Fawn"
date: 2007-06-07
forum: Outdated Tutorials &amp; Tips
---

### Post by kevdog on 2007-06-07
For Hardy, Intrepid, Jaunty, and beyond, an updated version of this guide is contained here: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)  I would suggest users follow the steps to this new guide and use this guide as a reference.

Tutorial inspired by my original post: [http://ubuntuforums.org/showthread.php?t=457633](http://ubuntuforums.org/showthread.php?t=457633) attempting to get working ssh tunneled FreeNX server with only opengl freenx server package supplied by seveas repositories.

There is another how-to guide for setting up FreeNX server under breezy, however installation is with packages supplied by nomachine and to my knowledge are not OpenGL compliant: [http://ubuntuforums.org/showthread.php?t=97277&highlight=freenx](http://ubuntuforums.org/showthread.php?t=97277&highlight=freenx)

Quick Overview of Process
1. Modify /etc/apt/sources.list to include seveas repositories
2. Ensure paths to fonts are correct within xorg.conf
3. Download and install seveas packages
4. Perform some key management functions for ssh server and nx user -- copy authorized_keys2 file to authorized_keys
5. (Optional) - Setup ssh port number on router, sshd_config, and node.conf file
6. Verify the nx user can ssh into server
7. Add users to freenx database
8. Perform key management for individual clients - copy authorized_keys2 file to authorized_keys in user personal .ssh directory
9. Restart nx server
10. Setup client

My server client versions:
FreeNx server: Version 1.5.0-60 OS (GPL)
WindowsXP client: NoMachine Nx Client for Windows Version 2.1.0-17

Assumptions
1. U(K)(X)buntu Feisty Fawn 7.04 distribution (likely to work with earlier ubuntu distros -- however this is untested).
2. Installed and functional ssh server
3. Static IP address for server, or a dynamic IP address that is unlikely to change
4. If behind router, ssh port is port forwarded to router
5. Firewall either disabled, or enabled to allow for ssh communication

The seveas repository provides Nx Client for Linux.  Windows NoMachine Nx clients may be obtained for free from: [http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)

1. [SIZE="4"]Modify /etc/apt/sources.list[/SIZE]

```
gksu gedit /etc/apt/sources.list
```

Add the following at the bottom of the file:
```

#Seveas Repositories [https://wiki.ubuntu.com/SeveasPackages](https://wiki.ubuntu.com/SeveasPackages)
deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) feisty-seveas freenx
deb-src [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) feisty-seveas freenx

```

If for some reason, these seveas mirrors are broken additional repositories may be added. List of additional repositories may be found here: [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/)

These packages can be authenticated using gpg -- which helps to avoid authentication errors.  In order to accomplish this:
```

gpg --keyserver subkeys.pgp.net --recv-keys 1135D466
gpg --export --armor 1135D466 | sudo apt-key add -

```

2. [SIZE="4"]Ensure font paths are correct in xorg.conf[/SIZE]
First backup xorg.conf file:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```

Open, look at, the xorg.conf file
```

gksu gedit /etc/X11/xorg.conf

```

Go to the section entitled "Files" and look at the different Font Paths.  You need to ensure that these font paths are correct.  When I originally installed from the Edgy Live CD these paths were totally incorrect, but caused no problem until the FreeNx server installation.  This was the cause of a lot of headache. My Font Path section is as follows, but rather than blindly copying and pasting, please ensure these are correct for your installation:

```

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1/"
        FontPath        "/usr/share/fonts/X11/100dpi/"
        FontPath        "/usr/share/fonts/X11/75dpi/"
        FontPath        "/usr/share/fonts/X11/misc/"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

```

3.[SIZE="4"]Download and install the seveas freenx packages[/SIZE]

```

sudo aptitude update
sudo aptitude install freenx nxclient

```

The server binaries are installed at: /usr/bin/nxserver
The server configuration files are located at: /etc/nxserver/node.conf
The client binaries are installed at: /usr/NX/bin
The client configuration files are kept at: ~/.nx  (This directory will not be created until using the nxclient for the first time).

Installation of the freenx server creates a new user on the server:nx, with home directory of: /var/lib/nxserver/home.   Inside this home directory is located a .ssh directory, and within this directory are created an authorized_keys2 and client.id_dsa.key.  These keys are setup by the default installation program.

4. [SIZE="4"]Key management for nx server (nx user) - Copy nx server authorized_keys2 file to authorized_keys[/SIZE]

For purpose of this guide we are going to be using the default keys created during the installation of the freenx server.  If you want to create custom keys (optional step), I would suggest doing this now by:
```

sudo dpkg-reconfigure freenx

```
and choosing custom keys.  I have not done this step.

Current ssh servers expect authorization keys to be located in a file known as authorized_keys, and not authorized_keys2.  To verify this is the expected file name:

```

sudo cat /etc/ssh/sshd_config | grep AuthorizedKeysFile

```

For the purpose of this guide, I am assuming all private ssh keys are kept in authorized_keys and not authorized_keys2.

Because the default installation places the nx user keys in authorized_keys2, rather than authorized_keys, we need to copy the nx user's authorized_keys2 file to authorized_keys.  To do this:

```

cd /var/lib/nxserver
sudo su
cd home/.ssh
cp authorized_keys2 authorized_keys
chown nx authorized_keys
exit

```

5. [SIZE="4"]Set port for ssh, nx server (Applicable only to those who are not running ssh over standard port 22).[/SIZE]

By default, both the ssh_server and freenx server are setup to listen on port 22.  If you are using a different port number for ssh, you need to ensure the following:
    a. The ssh port number is forwarded from router to s/erver
    b. The sshd_config file reflects the appropriate port number
            Either add extra port number or modify Port statement in sshd_config to reflect appropriate port number
    c. Edit /etc/nxserver/node.conf file, and change line where it states #SSHD_PORT=22
        to SSHD_PORT=*port_number*.  <--- Insert appropriate number
    d. Restart ssh server
     ```

sudo /etc/init.d/ssh restart
     
```

6. [SIZE="4"]Verify ssh connection using nx user  (DEBUGING STEP) [/SIZE]
Although not necessary, this step will ensure that the nx user can use ssh to connect to the server.  If this step fails, usage of the freenx server will fail also.

```

sudo su
cd /var/lib/nxserver/home/.ssh
ssh -i client.id_dsa.key nx@localhost  

```

Following should result demonstrating that the nx user can log into system via ssh:
```

HELLO NXSERVER - Version 1.5.0-60 OS (GPL)
NX> 105 

```

To get back to normal user:
```

exit
exit

```

7. [SIZE="4"][COLOR="Red"]Do not proceed further if step #6 fails[/COLOR]  Add user to freenx database. [/SIZE]

  Please note that this user must already have an account on the server.

```

sudo nxserver --adduser <user_to_add>
sudo nxserver --passwd <user>

```

For managing user's in the freenx database the following commands are helpful:
sudo nxserver --help
sudo nxserver --listuser
sudo nxserver --restart

Once user or users are added, restart the nx server:
```

sudo nxserver --restart

```

8.  [SIZE="4"]Key management for individual users[/SIZE] 

Have each user on server append created authorized_keys2 file to authorized_keys.
After adding myself as a user to the freenx server database, an authorized_keys2 file was created in my ~/.ssh directory.  Because I already had an authorized_keys file, I needed to append the authorized_keys2 file to my current authorized_keys file:
```

cat authorized_keys2 >> authorized_keys

```

9. [SIZE="4"]Restart nx server[/SIZE]
Setup at this point should be complete for the server.
Please restart freenx server:

```

sudo nxserver --restart

```

10. [SIZE="4"]Client Setup[/SIZE]
For client setup (for example on windows) you need to download the client.  The client needs to be configured to use SSL encryption of all traffic (under Advanced Tab)  If you didnt modify the default ssh nxserver keys during the installation, the client by default should have the correct ssh client key already installed (to verify push the key button and ensure the key listed matches the key found at ~/.ssh/client.id_dsa.key).  If you modified the installation to use custom keys, you will need to add the modified client key.

If you run into trouble:
1. Enable the debugging log in the server.  Modify /etc/nxserver.node.conf to include NX_LOG_LEVEL=3.  May change the number up to 7 to receive more information.  The logs for each session are kept under ~/.nx and then look for a big long number that represents a directory.  Within this directory are kept various logs which may help
2. Even after fixing fonts in the xorg.conf file, I kept getting a font related error.  At least on my nxserver, I had to add the following line to the /etc/nxserver/node.conf file: 
AGENT_EXTRA_OPTIONS_X="-fp /usr/share/fonts/X11/misc/"

***Thanks to Milamb0r for suggesting changes to the guide

---

### Post by dfreer on 2007-07-24
Thanks for this! As soon as things get less hectic around here, I really want to give this a try!

---

### Post by Milamb0r on 2007-07-29
Hi,

big thanks for the great HOWTO! Just tried it out and it worked well here.

Perhaps you might kill some very small failures, probable typos:


> **kevdog said:**
> 

7. [SIZE="4"][COLOR="Red"]Do not proceed further if step #6 fails[/COLOR]  Add user to freenx database. [/SIZE]

  Please note that this user must already have an account on the server.

```

sudo nxserver --adduser
sudo nxserver *user* --passwd

```


For better understanding it should be:
```

sudo nxserver --adduser <user_to_add>
sudo nxserver --passwd <user>

```

and ..

> 
For managing user's in the freenx database the following commands are helpful:
sudo freenx --help (lists all commands available)
sudo freenx --listuser
sudo freenx --restart


These commands should be:
```

sudo nxserver --help
sudo nxserver --listuser
sudo nxserver --restart

```

> 
9. [SIZE="4"]Restart nx server[/SIZE]
Setup at this point should be complete for the server.
Please restart freenx server:

```

sudo nxserver -restart

```


Just forgot a second "-" in front of restart here..

Thanks again, appreciate it!

---

### Post by kevdog on 2007-07-31
Thanks for the suggestions, hopefully the guide is working for you.  Havent received much feedback -- it took me days to figure things out on my own!!

---

### Post by mamnmamn on 2007-08-03
I have set up freenx on CENTOS 5 and it is similar to what you have done here. Can I ask, Is it possible to make the users use different ssh keys or do they use the same. Also I have not added seperate nx users and it seems to just be pulling them from the linux logins. Comments on security would be great.

---

### Post by kevdog on 2007-08-04
Im not exactly sure what you are asking.  I thought each user had to have an account on the server. Each user is assigned a client_id_dsa.key (public key) along with a correlating dss key that must be put in the authorized key.  This combination could in theory be generated randomly for each user.

---

### Post by RealMabu on 2007-08-13
> **kevdog said:**
> 
6. [SIZE="4"]Verify ssh connection using nx user  (DEBUGING STEP) [/SIZE]
Although not necessary, this step will ensure that the nx user can use ssh to connect to the server.  If this step fails, usage of the freenx server will fail also.

```

sudo su
cd /var/lib/nxserver/home/.ssh
ssh -i client.id_dsa.key nx@localhost  

```

Following should result demonstrating that the nx user can log into system via ssh:
```

HELLO NXSERVER - Version 1.5.0-60 OS (GPL)
NX> 105 

```

To get back to normal user:
```

exit
exit

```

Hi,
what if I fail step 6?
I have managed to set up ports to 8888 and here is what I get:
```

root@...:/var/lib/nxserver/home/.ssh# ssh -i client.id_dsa.key nx@localhost -p 8888
Read from socket failed: Connection reset by peer
root@...:/var/lib/nxserver/home/.ssh# 

```

Checking my config against your steps:
1.Repositories: OK
2.I miss the:
```
FontPath        "/usr/share/fonts/X11/misc/"
```
But i guess this isnt my problem...
3.I miss nxclient but I just need the server on my ubuntu box...
4.I edited /etc/ssh/sshd_config adding the line:
```
AuthorizedKeysFile %h/.ssh/authorized_keys2
```
5.I use SSHD on port 8888 and accomplished this by editing both /etc/ssh/sshd_config:
```
Port 8888
```
and /etc/nxserver/node.conf:
```
SSHD_PORT=8888
```

Any ideas?

P.S. *EDIT*
I add the verbose output of the debugging ssh command... maybe you guys find it useful...
```

root@...:/var/lib/nxserver/home/.ssh# ssh -v -i client.id_dsa.key nx@localhost -p 8888
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 8888.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file client.id_dsa.key type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug1: An invalid name was supplied
Configuration file does not specify default realm

debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: An invalid name was supplied
Configuration file does not specify default realm

debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer
root@...:/var/lib/nxserver/home/.ssh# 

```

---

### Post by tekoholix on 2007-08-13
kevdog,

You are THE MAN!!  I've just spent the last 2 days, trying to get the most recent official releases of nomachine's server/node/client up and running, and could not (due to more errors than I'd care to try to remember), thinking that the official releases might be better than the others...

I finally gave up, came back to your thread and followed your instructions explicitly (just as I had done with their's...), and suddenly IT JUST WORX!!!!!!!

I appreciate ya' greatly, and so will many of my customers, once I can show them this!!

Paul Harmor
Tekoholix.Computer.Services

---

### Post by kevdog on 2007-08-14
RealMabu

Im not exactly sure what your problem is, however it is definitely related to the ssh login process (which isnt exactly related to FreeNx).  I would confirm in your sshd_config you are using authorized_keys rather than authorized_keys2 and that inside the nx home directory you have copied authorized_keys2 to authorized_keys.  

I dont understand some of the errors you are getting, I would probably google them and see what comes up.  Im not an expert in troubleshooting ssh errors


tekoholix

Glad the guide worked for you.  Im not getting much feedback about the guide (as you can see).  Im glad at least one person can verify the steps I suggested.

---

### Post by RealMabu on 2007-08-15
Kevdog
I got it running at last!
At least in LAN it's working fine.
I copied the auth...keys2 into auth...keys but it continued not to work...
Then I noticed that even if I restarted sshd issuing ```
/etc/init.d/ssh restart
``` as root, the sshd process was owned by my "normal" user...
As if sshd didnt actually restart so I guess it didn't load the new config file.
I killed the process "by hand" and started issuing ```
/etc/init.d/ssh start
```.
Suddenly FreeNX is working.

Thanks for your guide and your help.

P.S. - re-reading your guide I noticed that in part 2 you have a double line (bold):
> ```
Section "Files"
        **FontPath        "/usr/share/fonts/X11/misc"**
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1/"
        FontPath        "/usr/share/fonts/X11/100dpi/"
        FontPath        "/usr/share/fonts/X11/75dpi/"
        **FontPath        "/usr/share/fonts/X11/misc/"**
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
```
Is that intentional or just a mistake?

Regrards.

---

### Post by kevdog on 2007-08-15
Glad you got it working.  FreeNX is a strange beast, b/c many of the problems are actually related to getting the ssh part of the connection working.  

As far as the double post, I guess you are right.  My xorg.conf file was configured like this when I installed Edgy.  I really never deleted, only changed the lines that were present to update their path.  Ill delete (or comment out) one of the lines to see if it makes a difference.

This section however was posted only as an example.  Your FontPath directories may be different.  I only included it in the instructions to let people know that in at least my default install, the FontPaths were incorrect and needed to me modified to represent the actual location of the various X11 fonts.

Thanks for your input -- I guess that makes 4 people in which this instructions work -- so Im assuming my instructions are generally accurate and reproducible.

---

### Post by dfreer on 2007-08-16
@kevdog
I have yet to get my sister's PC online again, so I have not had a chance to try this out. You may want to consider changing the thread name to something more searchable, like "How to remote desktop using SSH and FreeNX", this might be why you haven't had much feedback.

EDIT: Hmmm... I just tried changing the title of one of my threads, and was unable to do so. Have they changed things around here?
Also, just noticed this:
[http://ubuntuforums.org/showthread.php?t=441496](http://ubuntuforums.org/showthread.php?t=441496)

---

### Post by kevdog on 2007-08-16
Yea -- too late to change the title now -- Just trying to push this tutorial through the forum moderators was a pain in the butt!  It was lost for days, and finally after complaining enough the approved the post.  Im not looking forward to doing that again -- but looking back, Im sure a better title would help.

As far as the link you mentioned -- yea it might work.  The whole point of my tutorial was to expose problems you may encounter along the way, and give the person a chance to debug steps along the way so that when something doesnt work in the end -- They dont ask --- Hmm I wonder what part of all those steps I just did didnt work??

---

### Post by hsalgado on 2007-08-16
Hi, you have a great guide, thanks a lot for the effort!  Even tough, I could not make it work on my notebook.  I have followed your instructions but I can not connect.  This is the message I get:

NX> 203 NXSSH running with pid: 12348
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 192.168.1.101 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.5.0-60 OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: salgado
NX> 102 Password: 
NX> 103 Welcome to: salgado-laptop user: salgado
NX> 105 listsession --user="salgado" --status="suspended,running" --geometry="1024x768x24+render" --type="unix-kde"
/usr/lib/nx/nxserver: line 217: echo: write error: No space left on device
/usr/lib/nx/nxserver: line 218: echo: write error: No space left on device
/usr/lib/nx/nxserver: line 225: echo: write error: No space left on device
/usr/lib/nx/nxserver: line 226: echo: write error: No space left on device
/usr/lib/nx/nxserver: line 260: echo: write error: No space left on device
/usr/lib/nx/nxserver: line 261: echo: write error: No space left on device
NX> 148 Server capacity: not reached for user: salgado
NX> 105 Killed by signal 15.


Obviously, I have checked that the machine has space in the hard drive, I don't have any idea why is it giving me this result.

I would really appreciate if anybody can give me a clue.  Thanks!

---

### Post by RealMabu on 2007-08-16
hsalgado
I am no unix-guru but I have found some information that can help your case.
Since nxserver is a script, here are the lines responsible of the errors you're getting.
_Lines 217-218_
```
echo "NX> 127 Sessions list of user '$1' for reconnect:" > $TMPFILE
	echo >> $TMPFILE
```

_Lines 225-226_
```
		echo "Display Type             Session ID                       Options  Depth Screen         Status      Session Name" >> $TMPFILE
		echo "------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------" >> $TMPFILE

```

_Lines 260-261_
```
	echo "" >> $TMPFILE
	echo "" >> $TMPFILE
```

So i guess for some reason you cannot write to that temp file.
I'm no hacker but I guess the tempfile is:
_Line 216_
```
TMPFILE=$(mktemp /tmp/nxserver_tmp.XXXXXXXXX)

```
So I guess the directory is /tmp :)
Now, if you swear the disk is not empty :lolflag: the "there's no space" message makes me think at two possible causes: writing permissions on the directory OR disk quotas.
Have you checked those?
As for writing permissions, I cant actually help more than this:
-I cant find such a temp file on my system
-I dont know which "user.group" the temp file is supposed to belong to

Hope this helps.

I completely agree with **kevdog**, when he says: > FreeNX is a strange beast, b/c many of the problems are actually related to getting the ssh part of the connection working.
Actually what helped me most out of this guide was the "part 6 - ssh debugging step".
Many guides, howtos and tutorials out there tells you what to do but they never have check-steps nor they tells you what to do if something goes wrong...
THANKS AGAIN KEV

---

### Post by hsalgado on 2007-08-16
Thanks a lot for your help, it looks like it actually was a space problem, because the next time I logged in, the desktop could not initialize and I have to delete vmware from the terminal to be able to login...

BUT... when I was able to log in I couldn't connect!  

It looks like the ssh connection is not connecting.  Now, when I try the step 6 it does not work (it worked yesterday!).  When I try ssh from another machine I got "Permission denied (publickey)"... I don't know how to make nxserver to use the nomachine public key again... I really don't know what is going on.

If anyone can help, please!!!!!!!  This is the only thing I need to get rid of WinXP!!!!

Best,  Hugo.

---

### Post by kevdog on 2007-08-17
Again an ssh problem you are dealing with.  Step 6 is no magic, its just testing the ssh connection using the client.id_dsa.key as the public key, and logging in as the nx user.

I would first try debugging your ssh connection.  Meaning as just a regular use, ensure you you ssh to localhost.  If you have the ssh daemon setup on the server, you could test by just typing (on the server).  

ssh localhost

If this works from localhost, try to ssh into the box as a normal user from a remote box. This will test a few things -- ensure no firewall is blocking port 22, ssh daemon is listening, and that the ssh server is allowing connections.

If this works, I would work on debugging the nx user.  Inside the /var/lib/nxserver/home/.ssh directory - you should have created a file called authorized-keys that contains the nx user's private key.  If you are missing this file then ssh as the nx user will not work.

Again -- test as a normal user first, then proceed to debug the ssh user.  You may need to also to check settings in you /etc/ssh/sshd_config file to make sure port settings are correct, the AuthorizedKeysFile is %h/.ssh/authorized_keys

---

### Post by hsalgado on 2007-08-17
Thanks kevdog for your advise.  I tried ssh localhost and I am getting the same results:  Permission denied (publickey).  This is whay I get when I do a "ssh -v localhost":

```
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22.  
debug1: Connection established.
debug1: identity file /home/salgado/.ssh/identity type -1
debug1: identity file /home/salgado/.ssh/id_rsa type -1
debug1: identity file /home/salgado/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: An invalid name was supplied
Configuration file does not specify default realm

debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: An invalid name was supplied
Configuration file does not specify default realm

debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 136/256
debug2: bits set: 519/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/salgado/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 9
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/salgado/.ssh/known_hosts:9
debug2: bits set: 499/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/salgado/.ssh/identity ((nil))
debug2: key: /home/salgado/.ssh/id_rsa ((nil))
debug2: key: /home/salgado/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/salgado/.ssh/identity
debug3: no such identity: /home/salgado/.ssh/identity
debug1: Trying private key: /home/salgado/.ssh/id_rsa
debug3: no such identity: /home/salgado/.ssh/id_rsa
debug1: Trying private key: /home/salgado/.ssh/id_dsa
debug3: no such identity: /home/salgado/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).
```

It looks to me that it is not looking for the authorized_keys, even when it is in the ssh config file.  This is my sshd_config:

```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
#PermitRootLogin yes
StrictModes yes

#RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	~/.ssh/authorized_keys
AllowUsers nx

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
 PasswordAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
```


 Please help me with this... I really need this working or I will have to go back to winxp!   Some day, I will provide advise to other newbies!

---

### Post by kevdog on 2007-08-17
Im no ssh expert by any means but the error messages are complaining that they cant find your private key id_rsa.  Try regenerating you keys.

---

### Post by RealMabu on 2007-08-17
hsalgado,
in your sshd_config I noticed the line
```
AllowUsers nx
```
I think that line allows _only_ user **nx** to log in.
So you might have the keys problem reported by kevdog **and** this little issue.
Just add your username (salgado) to that line and restart sshd.
Finally, a stupid question (but that was the problem I had...) are you sure your sshd is shutting down when you restart it? Mine didnt... I had to kill it... just type
```
sudo ps -aux | grep sshd
```
write down the PID, then restart, get the PID again and check if they're different.

---

### Post by hsalgado on 2007-08-17
Thanks RealMabu.  I add the other user but didn't work.  I also checked that ssh really restart and it does.  It looks like this is a fundamental problem with ssh but I don't know enough to figure out what it is.  I even tried removing the ssh package and installing it again but didn't work either.  I think I will have to go back to Winxp... so bad!  Any idea for my last try????  Is there any other way of doing remote desktop without ssh? (weird question, I know!).

---

### Post by kevdog on 2007-08-17
Get rid of the AllowUsers line, then restart the ssh server
sudo /etc/init.d/ssh restart

---

### Post by hsalgado on 2007-08-17
Thanks a lot for your advise.... it is finally working!!!!  I had a problem with a ~ instead of %h in my sshd_config file.  This is really the definitive guide to freeNX!  Thanks a lot!!!!

---

### Post by Cappy on 2007-08-30
Useful guide, thanks. The configuration file to change ports at has been changed to ```
/usr/NX/etc/node.cfg
```
in my version.

The only thing I don't like is that it starts a new desktop session. Is there anyway to make it use my CURRENT desktop (aka Screen :0)?

---

### Post by hebetude on 2007-09-01
Okay, I finally got freeNX to work after many hours messing with it.  It was previously failing on

Permission failed 15 (publickey,authentication) or some sort.  

So, I moved my authorized_keys file for normal ssh sessions to a backup and put the one in the nx home directory (var/lib/nx/home/.ssh) in its place.  Now, this fixed the freenx problem, but I can't ssh in b/c of course my key is no where to be found.  Is there some way around this predicament?  

I feel it's somewhat retarded to even having to use a private key that is so easily attainable.

---

### Post by hebetude on 2007-09-01
Okay, despite the previous issue.  I now seem to have developed a problem with my configuration.  I can still login and see my desktop, but the NXclient uses 100% cpu the entire time and stays at "negotiating link parameters" in the window in the background.  Then, about 30seconds later the connection times out and the session closes.

Any ideas?

---

### Post by kevdog on 2007-09-03
Cappy -- just so I understand your discovery, can you list where the old version kept its files compared to the newer version you are using??  I wrote this guide and setup my server about 4 months ago and havent altered it since, so I am unfamiliar if somethings have changed.

To the best of my knowledge there is no way to set the display to :0.  I wish this were a feature.  I know VNC offers this feature but do not think FreeNX allows for this.

hebetude

To sets of keys are generated during the installation process. One for the freenx user in the /var/lib/nx/home/.ssh directory.  Of course you need to change it from authorized_keys2 to authorized_keys.  Also a public key is placed in your "user" .ssh directory when you add the user to the freenx database.  You need to add this public key to the authorized_keys file for each user.  (I hope you understand this).

As far as 100% cpu utilization, make sure that in the ~/.nx directory, you delete all the old sessions (things starting with C and S).  You should also do this on the client machine as well (not sure what architecture you are using as the client)

---

### Post by Pinprick on 2007-09-06
How do I find out the hostname to input when trying to connect through Windows?

Oh nevermind, I figured everything out.

Thanks a bunch, this was a great guide!

---

### Post by paul_rubin on 2007-09-28
Thanks much for this!  I've spent hours screwing with various remote desktop solutions (Win client viewing Ubuntu desktop).  Your instructions were complete and clear, and this worked first time out.

---

### Post by BramKuijper on 2007-10-01
I am trying to get freenx working on Gutsy Gibbon, but I wasn't lucky till so far..

I followed the installation instructions and everything went allright, including verifying the ssh connection using nx server. 

However, after installing nxclient on another Ubuntu machine (a feisty box in this case) and trying to log in on my nxserver, it got into a working X session but then the client aborted:

```
NXPROXY - Version 2.1.0

Copyright (C) 2001, 2006 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '13712'.
Session: Starting session at 'Mon Oct  1 13:33:11 2007'.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using adsl link parameters 512/24/1/0.
Info: Using cache parameters 4/4194304/8192KB/8192KB.
Info: Using image streaming parameters 50/128/1024KB/2048/256.
Info: Using image cache parameters 1/1/32768KB.
Info: Using pack method '16m-jpeg-7' with session 'unix-gnome'.
Info: Using ZLIB data compression 3/3/0.
Info: Using ZLIB stream compression 6/6.
Info: No suitable cache file found.
Info: Listening for font server connections on port '11000'.
Session: Session started at 'Mon Oct  1 13:33:11 2007'.
Info: Established X server connection.
Info: Using shared memory parameters 1/2048K.
Session: Terminating session at 'Mon Oct  1 13:33:41 2007'.
Info: End of NX transport requested by signal '15'.
Info: Waiting the cleanup timeout to complete.
Info: Shutting down the NX transport.
Warning: Parent process appears to be dead. Exiting watchdog.
```

Also, I looked into the nxserver's log files, but this didn't give me any further clues:

```
-- NX SERVER START: -c /usr/lib/nx/nxserver - ORIG_COMMAND=
HELLO NXSERVER - Version 1.5.0-60 OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: bram
NX> 102 Password:
Info: Auth method: passdb
NX> 103 Welcome to: theobio36 user: bram
NX> 105 listsession --user="bram" --status="suspended,running" --geometry="1280x1024x24+render" --type="unix-gnome"
NX> 127 Sessions list of user 'bram' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: bram
NX> 105 startsession  --link="adsl" --backingstore="1" --nodelay="1" --encryption="1" --cache="8M" --images="32M" --media="0" --session="theobio" --type="unix-gnome" --geometry="1280x974" --kbtype="pc105/us" --screeninfo="1280x974x24+render"

&link=adsl&backingstore=1&nodelay=1&encryption=1&cache=8M&images=32M&media=0&session=theobio&type=unix-gnome&geometry=1280x974&kbtype=pc105/us&screeninfo=1280x974x24+render&clientproto=1.5.0&user=bram&userip=145.98.213.240&uniqueid=F1930E33C5ACB1239207772EFC3FD34C&display=1000&host=127.0.0.1
NX> 1000 NXNODE - Version 1.5.0-60 OS (GPL)
NX> 700 Session id: theobio36-1000-F1930E33C5ACB1239207772EFC3FD34C
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 5687642257a7ad1fe8b390b98aecacb5
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 5687642257a7ad1fe8b390b98aecacb5
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye
NX> 1004 Error: NX Agent exited with exit status 1.
NX> 1006 Session status: closed
```

anyone has any pointers on information on solving this problem, or where to find more details what is causing this?

---

### Post by kevdog on 2007-10-01
I can not confirm these instructions, particularly the server installation, will work on Gusty.  I have not tried this, nor has anyone reported a successful or unsuccessful result.  I dont think the client would cause any problems, since its distributed for multiple architectures.  I wish I had a better answer for you.

---

### Post by Chemist on 2007-10-05
hi i've followed this guide and i can log in to my desktop from my laptop from my network but i'm struggling to connect from different locations. Any ideas?

---

### Post by kevdog on 2007-10-05
Youve got to give me more info that that.  Usually its an ssh problem.  Can you connect via ssh from the command line from different locations??

At what stage in the login process is everything choking??

---

### Post by Chemist on 2007-10-05
sorry mate wasn't thinking 

i can only connect from my own network. from other locations it say's - connection refused

NX> 203 NXSSH running with pid: 308
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
ssh: connect to host 192.168.1.122 port 22: Connection refused

---

### Post by kevdog on 2007-10-05
Sounds like an ssh problem or even yet a firewall/router problem.

Again not meaning any insults but:
1. Check that port 22 on the router (if you use one) is forwared to your machine.
2. Turn off firestarter or flush the Iptables on the server for now.  Can add them back in once things are working
3. Make sure openssh server is running (probably is)
4. From remote locations can you telnet to port 22 or ssh into the server?  If you can not, it specifically at this point is not a FreeNx server since it needs to set up an ssh connection first before starting the client visualization package.

---

### Post by Chemist on 2007-10-05
cheers mate will give that a go

---

### Post by markdjones82 on 2007-10-05
Hi all,
   I finally got everything setup with my NX server to where I am able to connect, but once the client connects and opens up, it will promptly crash while trying to open x windows I believe.  

The authentication goes through and I am able to SSH with putty just fine.  Any suggestions on why it is crashing at the graphical portion of loading?  I am running an AMD 64 machine, with an ATI graphics card.


Thanks!

---

### Post by kevdog on 2007-10-05
Ive seen this behaivor on my machine before -- which makes me think freenx is somewhat unstable.  You need to clean out all the old session variables on both server and client. I cant exactly remember where these are located right now but they are prefaced with C or S and then a big long number.  When I get back to the buntu box I will have to check.  This is the only thing that really ticks me off with FreeNx.

---

### Post by markdjones82 on 2007-10-05
> **kevdog said:**
> Ive seen this behaivor on my machine before -- which makes me think freenx is somewhat unstable.  You need to clean out all the old session variables on both server and client. I cant exactly remember where these are located right now but they are prefaced with C or S and then a big long number.  When I get back to the buntu box I will have to check.  This is the only thing that really ticks me off with FreeNx.

If you can point me to the files to delete that would be great, I haven't actually been able to get with it for the first time yet, so would I still have those files?

---

### Post by kevdog on 2007-10-05
Hmm, no those files will not be there since you never have established a session.

For test purposes when I set it up, I simply connected from localhost to the server.  I kept getting a bunch of problems getting the X server to start, so hence in my tutorial the problems with the font settings which eventually solved the problem for me.  Definitely check the font path.  With the server settings there is a way to set the log level to log nearly everything about the connection.  I would definitely up the log level and make sure you consult these, since these eventually gave me hints that I was having a font problem (after hours of taking the information in the logs and looking on the internet).

---

### Post by clever on 2007-10-05
> **Chemist said:**
> sorry mate wasn't thinking 

i can only connect from my own network. from other locations it say's - connection refused

NX> 203 NXSSH running with pid: 308
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
ssh: connect to host 192.168.1.122 port 22: Connection refused

The IP address you're using (192.168.1.122) is for your machine within your own private network.  If you're trying to connect to your machine from somewhere else on the internet, you need to use your public IP.  You can find it by going to [http://ipchicken.com]("http://www.ipchicken.com/").

Use whatever IP it tells you and try to connect SSH or telnet to port 22.  If that works, then you can try NX.  Remember you will need to allow access to port 22 through your firewall & router, if any.

---

### Post by markdjones82 on 2007-10-08
> **kevdog said:**
> Hmm, no those files will not be there since you never have established a session.

For test purposes when I set it up, I simply connected from localhost to the server.  I kept getting a bunch of problems getting the X server to start, so hence in my tutorial the problems with the font settings which eventually solved the problem for me.  Definitely check the font patll h.  With the server settings there is a way to set the log level to log nearly everything about the connection.  I would definitely up the log level and make sure you consult these, since these eventually gave me hints that I was having a font problem (after hours of taking the information in the logs and looking on the internet).

I can't seem to find any issues with the logs from what I can tell. I am using the nomachine windows xp client btw.  Below is a copy of my logs. What do all the parameters like "geometry" etc stand for at the beginning?

-- NX SERVER START: -c /usr/lib/nx/nxserver - ORIG_COMMAND=
HELLO NXSERVER - Version 1.5.0-60 OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: mark
NX> 102 Password:
Info: Auth method: passdb ssh
NX> 103 Welcome to: mark-ubuntu user: mark
NX> 105 listsession --user="mark" --status="suspended,running" --geometry="1280x800x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'mark' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: mark
NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --media="0" --session="Linux" --type="unix-gnome" --geometry="1280x766" --kbtype="pc102/en_US" --screeninfo="1280x766x32+render"

&link=lan&backingstore=1&encryption=1&cache=16M&images=64M&media=0&session=Linux&type=unix-gnome&geometry=1280x766&kbtype=pc102/en_US&screeninfo=1280x766x32+render&clientproto=1.5.0&user=mark&userip=192.168.1.105&uniqueid=522502A1A73AC921C2DF2465AA03867E&display=1000&host=127.0.0.1
mark@127.0.0.1's password:
NX> 1000 NXNODE - Version 1.5.0-60 OS (GPL)
NX> 700 Session id: mark-ubuntu-1000-522502A1A73AC921C2DF2465AA03867E
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 6420099c63dc7b6c35f1f450b57521de
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 6420099c63dc7b6c35f1f450b57521de
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye
NX> 1009 Session status: terminating
NX> 1006 Session status: closed
NX> 1001

---

### Post by kevdog on 2007-10-08
Can you bump up the log level???

Im not sure why its not working with you.  Geometry has to do with the Xserver -- its normal and you shouldnt have to really mess with those settings.

---

### Post by markdjones82 on 2007-10-09
> **kevdog said:**
> Can you bump up the log level???

Im not sure why its not working with you.  Geometry has to do with the Xserver -- its normal and you shouldnt have to really mess with those settings.

Where do I bump up the log level?  Not real familiar witih where to do that.  would it be in nxserver.conf?  What level should I set it to?

---

### Post by kevdog on 2007-10-09
Ive heard rumors that the name of the conf file has changed. 

On my machine my configuration file is at /etc/nxserver/node.conf

Within the file is the line:
NX_LOG_LEVEL=3

I would set it to 5 or 6 and then restart the nxserver.

---

### Post by markdjones82 on 2007-10-09
I had set it to 6 before I just remembered, but I am still getting the same output.  :confused:

---

### Post by kevdog on 2007-10-09
Do you have any old sessions that are stored or are trying to resume a session??

---

### Post by markdjones82 on 2007-10-09
Nope, never been able to actually create a session :/

---

### Post by kevdog on 2007-10-09
As you can see Im not offering much advice since I dont know anything right now.  Im curious about this line:
--status="suspended,running"  

Being no expert it seems to suggest resuming a suspended session.  I think inside the ~/.nx directory on the server there might be a big file that starts with C or S -- its the session that you tried to connect with.  I would manually delete this file or any such files that look like this.  Probe around in the ~/.nx directory if this isnt the exact location.  

Before connecting from your windows XP client, you have confirmed that you can connect from localhost first??

And I dont mean to be redundant but youve modified your iptables (possibly through firestarter) to open port 22 on the server??

---

### Post by markdjones82 on 2007-10-10
Kev,
  I have no firewall turned on and I can SSH in fine.  I have decided to wipe a clean slate and try 7.10.  I will then try nxserver from there.

I think the root of my problem is something with my graphics as I had done some modificaiton to try and get Beryl working.  I will update you with what is going on!

-Mark

> **kevdog said:**
> As you can see Im not offering much advice since I dont know anything right now.  Im curious about this line:
--status="suspended,running"  

Being no expert it seems to suggest resuming a suspended session.  I think inside the ~/.nx directory on the server there might be a big file that starts with C or S -- its the session that you tried to connect with.  I would manually delete this file or any such files that look like this.  Probe around in the ~/.nx directory if this isnt the exact location.  

Before connecting from your windows XP client, you have confirmed that you can connect from localhost first??

And I dont mean to be redundant but youve modified your iptables (possibly through firestarter) to open port 22 on the server??

---

### Post by kevdog on 2007-10-10
It could be -- like I stated so many times I had a problem with the fonts -- who would have thought that would have crashed the nxserver -- but it had something to do with tunneling the X session throught ssh to the client.  Im no expert on the X windowing system, so it took me hours to troubleshoot.  If you had modified your /etc/X11/xorg.conf file in any way, I would start there.  

In fact on your new install, immediately make a backup copy of the xorg.conf file so you can restore it at any time if you need it.  I think likely that is the culprit in your case, as you now remind me about beryl, compiz.

---

### Post by daflame on 2007-10-17
I also am having troubles with setting up freenx server on both my laptop and server.  Both are running amd64 cpus (The laptop is single core and the server is X2).  Both of them stop at the same place when setting up the session.  I can connect to my computer running the i386 edition of ubuntu, but these 64bit editions don't seem to work.  Do I need to install the version 3.0 client for 64bit?

---

### Post by daflame on 2007-10-17
The server log is here.  The key entry is localhost that I'm trying to log into.  Sorry for too much detail I put the log level to 7:

```

[Tue Oct 16 22:11:37 2007]: Setting environment variable 'NX_SYSTEM' to '/usr/NX'
[Tue Oct 16 22:11:37 2007]: Setting environment variable 'NX_ROOT' to '/home/jeremy/.nx'
[Tue Oct 16 22:11:37 2007]: Setting environment variable 'NX_HOME' to '/home/jeremy'
[Tue Oct 16 22:11:37 2007]: Starting font debug
Fixed font was set to: 'Courier' size: '8'
And the result is: 'Courier'
Setting font from nxclient.conf: 'Bitstream Vera Sans,9,-1,5,50,0,0,0,0,0'
Font was set to: 'Bitstream Vera Sans'
And the result is: 'Bitstream Vera Sans'
End of font debug


[Tue Oct 16 22:11:37 2007]: Starting NX Client version 2.1.0-17
[Tue Oct 16 22:11:37 2007]: qtrc: useXft read=1 value=1
qtrc: useXft is set to true
qtrc: enableXft read=1 value=1
qtrc: enableXft is set to true

[Tue Oct 16 22:11:37 2007]: Initializing the login dialog.
[Tue Oct 16 22:11:37 2007]: Config File Name set to: '/home/jeremy/.nx/config/nxclient.cfg'.
[Tue Oct 16 22:11:37 2007]: System NX dir set to: '/usr/NX'.
[Tue Oct 16 22:11:37 2007]: Personal NX dir set to: '/home/jeremy/.nx'.
[Tue Oct 16 22:11:37 2007]: creating SessionSettings=''
[Tue Oct 16 22:11:37 2007]: LoginDialog::loadConfigFiles - number of entries in config dir: 16
[Tue Oct 16 22:11:37 2007]: ComboSession::insertSession: 'Alarmtek Server (Local) - atsserver2 - admin' -> '/home/jeremy/.nx/config/Alarmtek Server (Local) - atsserver2 - admin.nxs'
[Tue Oct 16 22:11:37 2007]: ComboSession::setCurrentSession: 'Alarmtek Server (Local) - atsserver2 - admin'
[Tue Oct 16 22:11:37 2007]: SessionSettings::loadFromFile('/home/jeremy/.nx/config/Alarmtek Server (Local) - atsserver2 - admin.nxs')
[Tue Oct 16 22:11:37 2007]: ComboSession::insertSession: 'Alarmtek Server (Local)' -> '/home/jeremy/.nx/config/Alarmtek Server (Local).nxs'
[Tue Oct 16 22:11:37 2007]: ComboSession::setCurrentSession: 'Alarmtek Server (Local)'
[Tue Oct 16 22:11:37 2007]: SessionSettings::loadFromFile('/home/jeremy/.nx/config/Alarmtek Server (Local).nxs')
[Tue Oct 16 22:11:37 2007]: ComboSession::insertSession: 'Alarmtek Server - andrea' -> '/home/jeremy/.nx/config/Alarmtek Server - andrea.nxs'
[Tue Oct 16 22:11:37 2007]: ComboSession::setCurrentSession: 'Alarmtek Server - andrea'
[Tue Oct 16 22:11:37 2007]: SessionSettings::loadFromFile('/home/jeremy/.nx/config/Alarmtek Server - andrea.nxs')
[Tue Oct 16 22:11:37 2007]: ComboSession::insertSession: 'Alarmtek Server - atsserver2 - admin' -> '/home/jeremy/.nx/config/Alarmtek Server - atsserver2 - admin.nxs'
[Tue Oct 16 22:11:37 2007]: ComboSession::setCurrentSession: 'Alarmtek Server - atsserver2 - admin'
[Tue Oct 16 22:11:37 2007]: SessionSettings::loadFromFile('/home/jeremy/.nx/config/Alarmtek Server - atsserver2 - admin.nxs')
[Tue Oct 16 22:11:37 2007]: ComboSession::insertSession: 'Alarmtek Server - atsserver2 - jeremy' -> '/home/jeremy/.nx/config/Alarmtek Server - atsserver2 - jeremy.nxs'
[Tue Oct 16 22:11:37 2007]: ComboSession::setCurrentSession: 'Alarmtek Server - atsserver2 - jeremy'
[Tue Oct 16 22:11:37 2007]: SessionSettings::loadFromFile('/home/jeremy/.nx/config/Alarmtek Server - atsserver2 - jeremy.nxs')
[Tue Oct 16 22:11:37 2007]: ComboSession::insertSession: 'Alarmtek Server - MS Access - jeremy' -> '/home/jeremy/.nx/config/Alarmtek Server - MS Access - jeremy.nxs'
[Tue Oct 16 22:11:37 2007]: ComboSession::setCurrentSession: 'Alarmtek Server - MS Access - jeremy'
[Tue Oct 16 22:11:37 2007]: SessionSettings::loadFromFile('/home/jeremy/.nx/config/Alarmtek Server - MS Access - jeremy.nxs')
[Tue Oct 16 22:11:37 2007]: ComboSession::insertSession: 'Alarmtek Server - rhonda' -> '/home/jeremy/.nx/config/Alarmtek Server - rhonda.nxs'
[Tue Oct 16 22:11:37 2007]: ComboSession::setCurrentSession: 'Alarmtek Server - rhonda'
[Tue Oct 16 22:11:37 2007]: SessionSettings::loadFromFile('/home/jeremy/.nx/config/Alarmtek Server - rhonda.nxs')
[Tue Oct 16 22:11:37 2007]: ComboSession::insertSession: 'Alarmtek Server - Telemarket Pro - rhonda' -> '/home/jeremy/.nx/config/Alarmtek Server - Telemarket Pro - rhonda.nxs'
[Tue Oct 16 22:11:37 2007]: ComboSession::setCurrentSession: 'Alarmtek Server - Telemarket Pro - rhonda'
[Tue Oct 16 22:11:37 2007]: SessionSettings::loadFromFile('/home/jeremy/.nx/config/Alarmtek Server - Telemarket Pro - rhonda.nxs')
[Tue Oct 16 22:11:37 2007]: ComboSession::insertSession: 'Alarmtek Server' -> '/home/jeremy/.nx/config/Alarmtek Server.nxs'
[Tue Oct 16 22:11:37 2007]: ComboSession::setCurrentSession: 'Alarmtek Server'
[Tue Oct 16 22:11:37 2007]: SessionSettings::loadFromFile('/home/jeremy/.nx/config/Alarmtek Server.nxs')
[Tue Oct 16 22:11:37 2007]: ComboSession::insertSession: 'Alive Software Home (Paula)' -> '/home/jeremy/.nx/config/Alive Software Home (Paula).nxs'
[Tue Oct 16 22:11:37 2007]: ComboSession::setCurrentSession: 'Alive Software Home (Paula)'
[Tue Oct 16 22:11:37 2007]: SessionSettings::loadFromFile('/home/jeremy/.nx/config/Alive Software Home (Paula).nxs')
[Tue Oct 16 22:11:37 2007]: ComboSession::insertSession: 'Localhost (Sigma)' -> '/home/jeremy/.nx/config/Localhost (Sigma).nxs'
[Tue Oct 16 22:11:37 2007]: ComboSession::setCurrentSession: 'Localhost (Sigma)'
[Tue Oct 16 22:11:37 2007]: SessionSettings::loadFromFile('/home/jeremy/.nx/config/Localhost (Sigma).nxs')
[Tue Oct 16 22:11:37 2007]: ComboSession::insertSession: 'NX Testdrive' -> '/home/jeremy/.nx/config/NX Testdrive.nxs'
[Tue Oct 16 22:11:37 2007]: ComboSession::setCurrentSession: 'NX Testdrive'
[Tue Oct 16 22:11:37 2007]: SessionSettings::loadFromFile('/home/jeremy/.nx/config/NX Testdrive.nxs')
[Tue Oct 16 22:11:37 2007]: ComboSession::insertSession: 'Paula - jeremy' -> '/home/jeremy/.nx/config/Paula - jeremy.nxs'
[Tue Oct 16 22:11:37 2007]: ComboSession::setCurrentSession: 'Paula - jeremy'
[Tue Oct 16 22:11:37 2007]: SessionSettings::loadFromFile('/home/jeremy/.nx/config/Paula - jeremy.nxs')
[Tue Oct 16 22:11:37 2007]: Utility::getPreferencesFile: 'nxclient' -> '/home/jeremy/.nx/config/nxclient.cfg'
[Tue Oct 16 22:11:37 2007]: ComboSession::setCurrentSession: 'Localhost (Sigma)'
[Tue Oct 16 22:11:37 2007]: SessionSettings::loadFromFile('/home/jeremy/.nx/config/Localhost (Sigma).nxs')
[Tue Oct 16 22:11:37 2007]: LoginDialog: slotChangeSession [Localhost (Sigma)]
[Tue Oct 16 22:11:37 2007]: LoginDialog: loadUserAndPassword
[Tue Oct 16 22:11:37 2007]: LoginDialog: loadUserAndPassword
[Tue Oct 16 22:11:37 2007]: Settings::flush
[Tue Oct 16 22:11:37 2007]: Settings::flush
[Tue Oct 16 22:11:37 2007]: ComboSession::setCurrentSession: 'Localhost (Sigma)'
[Tue Oct 16 22:11:37 2007]: SessionSettings::loadFromFile('/home/jeremy/.nx/config/Localhost (Sigma).nxs')
[Tue Oct 16 22:11:37 2007]: LoginDialog: slotChangeSession [Localhost (Sigma)]
[Tue Oct 16 22:11:37 2007]: LoginDialog: loadUserAndPassword
[Tue Oct 16 22:11:37 2007]: LoginDialog: loadUserAndPassword
[Tue Oct 16 22:11:37 2007]: Settings::flush
[Tue Oct 16 22:11:37 2007]: Settings::flush
[Tue Oct 16 22:11:37 2007]: LoginDialog: loadUserAndPassword
[Tue Oct 16 22:11:37 2007]: Setting environment variable 'NX_HOME' to '/home/jeremy'
[Tue Oct 16 22:11:37 2007]: Setting environment variable 'NX_ROOT' to '/home/jeremy/.nx'
[Tue Oct 16 22:11:37 2007]: Setting environment variable 'NX_SYSTEM' to '/usr/NX'
[Tue Oct 16 22:11:37 2007]: Setting environment variable 'NX_CLIENT' to '/usr/NX/bin/nxclient'
[Tue Oct 16 22:11:37 2007]: Trying the XAUTHORITY environment variable with value [].
[Tue Oct 16 22:11:37 2007]: Trying the default value [/home/jeremy/.Xauthority].
[Tue Oct 16 22:11:37 2007]: Utility::getXAuthorityFilePath: /home/jeremy/.Xauthority
[Tue Oct 16 22:11:37 2007]: Setting environment variable 'XAUTHORITY' to '/home/jeremy/.Xauthority'
[Tue Oct 16 22:11:37 2007]: Setting environment variable 'LD_LIBRARY_PATH' to '/usr/NX/lib'
[Tue Oct 16 22:11:37 2007]: Setting environment variable 'HOME' to '/home/jeremy'
[Tue Oct 16 22:11:37 2007]: Setting environment variable 'PATH' to '/home/scripts:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/NX/bin:/usr/X/bin'
[Tue Oct 16 22:11:37 2007]: Setting environment variable 'NX_TEMP' to '/tmp'
[Tue Oct 16 22:11:37 2007]: Setting environment variable 'TEMP' to '/tmp'
[Tue Oct 16 22:11:37 2007]: Setting environment variable 'NX_VERSION' to '2.1.0'
[Tue Oct 16 22:11:39 2007]: LoginDialog: login setupGui 1
[Tue Oct 16 22:11:40 2007]: Setting environment variable 'NX_HOME' to '/home/jeremy'
[Tue Oct 16 22:11:40 2007]: Setting environment variable 'NX_ROOT' to '/home/jeremy/.nx'
[Tue Oct 16 22:11:40 2007]: Setting environment variable 'NX_SYSTEM' to '/usr/NX'
[Tue Oct 16 22:11:40 2007]: Setting environment variable 'NX_CLIENT' to '/usr/NX/bin/nxclient'
[Tue Oct 16 22:11:40 2007]: Trying the XAUTHORITY environment variable with value [/home/jeremy/.Xauthority].
[Tue Oct 16 22:11:40 2007]: Utility::getXAuthorityFilePath: /home/jeremy/.Xauthority
[Tue Oct 16 22:11:40 2007]: Setting environment variable 'XAUTHORITY' to '/home/jeremy/.Xauthority'
[Tue Oct 16 22:11:40 2007]: Setting environment variable 'LD_LIBRARY_PATH' to '/usr/NX/lib:/usr/NX/lib'
[Tue Oct 16 22:11:40 2007]: Setting environment variable 'HOME' to '/home/jeremy'
[Tue Oct 16 22:11:40 2007]: Setting environment variable 'PATH' to '/home/scripts:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/NX/bin:/usr/X/bin:/usr/NX/bin:/usr/X/bin'
[Tue Oct 16 22:11:40 2007]: Setting environment variable 'NX_TEMP' to '/tmp'
[Tue Oct 16 22:11:40 2007]: Setting environment variable 'TEMP' to '/tmp'
[Tue Oct 16 22:11:40 2007]: Setting environment variable 'NX_VERSION' to '2.1.0'
[Tue Oct 16 22:11:40 2007]: Trying to write the ssh key into [/home/jeremy/.nx/temp/20744/keylog]
[Tue Oct 16 22:11:40 2007]: SSH key file path [/home/jeremy/.nx/temp/20744/keylog]
[Tue Oct 16 22:11:40 2007]: LoginDialog: startProgressTimer
[Tue Oct 16 22:11:40 2007]: LoginDialog::ShowConnectionStatus code=[240] str=[Setting up the environment] error=[0]
[Tue Oct 16 22:11:40 2007]: ProgressDialog::printNxStatus: [Setting up the environment]
[Tue Oct 16 22:11:40 2007]: LoginDialog: startProgressTimer
[Tue Oct 16 22:11:40 2007]: Showing progress dialog: Setting up the environment
[Tue Oct 16 22:11:40 2007]: Going to get the X authorization cookie on display.
[Tue Oct 16 22:11:40 2007]: Trying the XAUTHORITY environment variable with value [/home/jeremy/.Xauthority].
[Tue Oct 16 22:11:40 2007]: Running command [xauth -f /home/jeremy/.Xauthority nextract - :0.0 | cut -f 9 -d ' ' 1>/home/jeremy/.nx/temp/20744/authlog 2>/dev/null].
[Tue Oct 16 22:11:40 2007]: Command run.
[Tue Oct 16 22:11:40 2007]: Got or created the X authorization cookie.
[Tue Oct 16 22:11:40 2007]: LoginDialog::ShowConnectionStatus code=[241] str=[Connecting to localhost] error=[0]
[Tue Oct 16 22:11:40 2007]: ProgressDialog::printNxStatus: [Connecting to localhost]
[Tue Oct 16 22:11:40 2007]: LoginDialog::connectHost() nxsshline=/usr/NX/bin/nxssh -nx -p 22 -i /home/jeremy/.nx/temp/20744/keylog nx@localhost -x -2 -o RhostsAuthentication no -o PasswordAuthentication no -o RSAAuthentication no -o RhostsRSAAuthentication no -o PubkeyAuthentication yes -B -E
[Tue Oct 16 22:11:40 2007]: Using NX_STDIN flag redirection for [nxssh] process
[Tue Oct 16 22:11:40 2007]: Using NX_STDOUT flag redirection for [nxssh] process
[Tue Oct 16 22:11:40 2007]: Using NX_STDERR flag redirection for [nxssh] process
[Tue Oct 16 22:11:40 2007]: SpawnProcess method has returned [1]
[Tue Oct 16 22:11:40 2007]: Process [nxssh] running with pid [20748]
[Tue Oct 16 22:11:41 2007]: Received line from nxssh process [NX> 203 NXSSH running with pid: 20748
] with code [203]
[Tue Oct 16 22:11:41 2007]: Received code[203]
[Tue Oct 16 22:11:41 2007]: NXProtocol: trying to read ssh pid from ' 20748
' - read '20748'
[Tue Oct 16 22:11:41 2007]: Received line from nxssh process [NX> 285 Enabling check on switch command
] with code [285]
[Tue Oct 16 22:11:41 2007]: Received code[285]
[Tue Oct 16 22:11:41 2007]: Received line from nxssh process [NX> 285 Enabling skip of SSH config files
] with code [285]
[Tue Oct 16 22:11:41 2007]: Received code[285]
[Tue Oct 16 22:11:41 2007]: Received line from nxssh process [NX> 285 Setting the preferred NX options
] with code [285]
[Tue Oct 16 22:11:41 2007]: Received code[285]
[Tue Oct 16 22:11:41 2007]: Received line from nxssh process [NX> 200 Connected to address: 127.0.0.1 on port: 22
] with code [200]
[Tue Oct 16 22:11:41 2007]: Received code[200]
[Tue Oct 16 22:11:41 2007]: Received line from nxssh process [NX> 202 Authenticating user: nx
] with code [202]
[Tue Oct 16 22:11:41 2007]: Received code[202]
[Tue Oct 16 22:11:41 2007]: LoginDialog::ShowConnectionStatus code=[242] str=[Connected to localhost] error=[0]
[Tue Oct 16 22:11:41 2007]: ProgressDialog::printNxStatus: [Connected to localhost]
[Tue Oct 16 22:11:41 2007]: Received line from nxssh process [NX> 208 Using auth method: publickey
] with code [208]
[Tue Oct 16 22:11:41 2007]: Received code[208]
[Tue Oct 16 22:11:42 2007]: Received line from nxssh process [HELLO NXSERVER - Version 1.5.0-60 OS (GPL)
] with code [1000]
[Tue Oct 16 22:11:42 2007]: Received code[1000]
[Tue Oct 16 22:11:42 2007]: Received line from nxssh process [NX> 105 ] with code [105]
[Tue Oct 16 22:11:42 2007]: Received code[105]
[Tue Oct 16 22:11:42 2007]: Received line from nxssh process [hello NXCLIENT - Version 1.5.0
] with code [-1]
[Tue Oct 16 22:11:42 2007]: Received code[-1]
[Tue Oct 16 22:11:42 2007]: Received line from nxssh process [NX> 134 Accepted protocol: 1.5.0
] with code [134]
[Tue Oct 16 22:11:42 2007]: Received code[134]
[Tue Oct 16 22:11:42 2007]: Received line from nxssh process [NX> 105 SET SHELL_MODE SHELL
] with code [105]
[Tue Oct 16 22:11:42 2007]: Received code[105]
[Tue Oct 16 22:11:42 2007]: Received line from nxssh process [NX> 105 SET AUTH_MODE PASSWORD
] with code [105]
[Tue Oct 16 22:11:42 2007]: Received code[105]
[Tue Oct 16 22:11:42 2007]: Received line from nxssh process [NX> 105 login
] with code [105]
[Tue Oct 16 22:11:42 2007]: Received code[105]
[Tue Oct 16 22:11:42 2007]: Received line from nxssh process [NX> 101 User: ] with code [101]
[Tue Oct 16 22:11:42 2007]: Received code[101]
[Tue Oct 16 22:11:42 2007]: LoginDialog::ShowConnectionStatus code=[243] str=[Waiting authentication] error=[0]
[Tue Oct 16 22:11:42 2007]: ProgressDialog::printNxStatus: [Waiting authentication]
[Tue Oct 16 22:11:43 2007]: Received line from nxssh process [jeremy
] with code [-1]
[Tue Oct 16 22:11:43 2007]: Received code[-1]
[Tue Oct 16 22:11:43 2007]: Received line from nxssh process [NX> 102 Password: ] with code [102]
[Tue Oct 16 22:11:43 2007]: Received code[102]
[Tue Oct 16 22:11:43 2007]: Received line from nxssh process [
] with code [-1]
[Tue Oct 16 22:11:43 2007]: Received code[-1]
[Tue Oct 16 22:11:43 2007]: Received line from nxssh process [NX> 103 Welcome to: sigma user: jeremy
] with code [103]
[Tue Oct 16 22:11:43 2007]: Received code[103]
[Tue Oct 16 22:11:43 2007]: LoginDialog::ShowConnectionStatus code=[244] str=[Authentication completed] error=[0]
[Tue Oct 16 22:11:43 2007]: ProgressDialog::printNxStatus: [Authentication completed]
[Tue Oct 16 22:11:43 2007]: Settings::flush
[Tue Oct 16 22:11:43 2007]: Settings::flush
[Tue Oct 16 22:11:43 2007]: LoginDialog: runningInExistingProxy called
[Tue Oct 16 22:11:43 2007]: LoginDialog: customUnixSession is [0], virtualDesktop is [0]
[Tue Oct 16 22:11:43 2007]: LoginDialog: runningInExistingProxy returns sessionID = []
[Tue Oct 16 22:11:43 2007]: Received line from nxssh process [NX> 105 ] with code [105]
[Tue Oct 16 22:11:43 2007]: Received code[105]
[Tue Oct 16 22:11:43 2007]: Received line from nxssh process [listsession --user="jeremy" --status="suspended,running" --geometry="1280x800x24+render" --type="unix-kde"
] with code [-1]
[Tue Oct 16 22:11:43 2007]: Received code[-1]
[Tue Oct 16 22:11:43 2007]: Received line from nxssh process [NX> 127 Sessions list of user 'jeremy' for reconnect:
] with code [127]
[Tue Oct 16 22:11:43 2007]: Received code[127]
[Tue Oct 16 22:11:43 2007]: Received line from nxssh process [
] with code [-1]
[Tue Oct 16 22:11:43 2007]: Received code[-1]
[Tue Oct 16 22:11:43 2007]: Received line from nxssh process [Display Type             Session ID                       Options  Depth Screen         Status      Session Name
] with code [-1]
[Tue Oct 16 22:11:43 2007]: Received code[-1]
[Tue Oct 16 22:11:43 2007]: Received line from nxssh process [------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
] with code [-1]
[Tue Oct 16 22:11:43 2007]: Received code[-1]
[Tue Oct 16 22:11:43 2007]: Received line from nxssh process [
] with code [-1]
[Tue Oct 16 22:11:43 2007]: Received code[-1]
[Tue Oct 16 22:11:43 2007]: Received line from nxssh process [
] with code [-1]
[Tue Oct 16 22:11:43 2007]: Received code[-1]
[Tue Oct 16 22:11:43 2007]: Received line from nxssh process [NX> 148 Server capacity: not reached for user: jeremy
] with code [148]
[Tue Oct 16 22:11:43 2007]: Received code[148]
[Tue Oct 16 22:11:43 2007]: LoginDialog: SlotListSessionMode: autoReconnet[0] settings->isAutomaticReconnect[0]
[Tue Oct 16 22:11:43 2007]: LoginDialog::createNewSession
[Tue Oct 16 22:11:43 2007]: Session name passed to LoginDialog::createStartSessionString is []
[Tue Oct 16 22:11:43 2007]: Info: Server doesn't support image streaming
[Tue Oct 16 22:11:43 2007]: NX Server does not support host url encode
[Tue Oct 16 22:11:43 2007]: Parameters passed to NX server [  --link="adsl" --backingstore="1" --nodelay="1" --cache="8M" --images="32M" --media="0" --session="Localhost (Sigma)" --type="unix-kde" --geometry="1240x760+20+20" --kbtype="pc102/us"
]
[Tue Oct 16 22:11:43 2007]: LoginDialog: createNewSession - trying to reuse running session
[Tue Oct 16 22:11:43 2007]: LoginDialog: runningInExistingProxy called
[Tue Oct 16 22:11:43 2007]: LoginDialog: customUnixSession is [0], virtualDesktop is [0]
[Tue Oct 16 22:11:43 2007]: LoginDialog: runningInExistingProxy returns sessionID = []
[Tue Oct 16 22:11:43 2007]: Start automatically the session with the parameters [startsession  --link="adsl" --backingstore="1" --nodelay="1" --cache="8M" --images="32M" --media="0" --session="Localhost (Sigma)" --type="unix-kde" --geometry="1240x760+20+20" --kbtype="pc102/us" --screeninfo="1240x760x24+render"
]
[Tue Oct 16 22:11:43 2007]: Received line from nxssh process [NX> 105 ] with code [105]
[Tue Oct 16 22:11:43 2007]: Received code[105]
[Tue Oct 16 22:11:45 2007]: Received line from nxssh process [startsession  --link="adsl" --backingstore="1" --nodelay="1" --cache="8M" --images="32M" --media="0" --session="Localhost (Sigma)" --type="unix-kde" --geometry="1240x760+20+20" --kbtype="pc102/us" --screeninfo="1240x760x24+render"
] with code [-1]
[Tue Oct 16 22:11:45 2007]: Received code[-1]
[Tue Oct 16 22:11:45 2007]: Received line from nxssh process [
] with code [-1]
[Tue Oct 16 22:11:45 2007]: Received code[-1]
[Tue Oct 16 22:11:45 2007]: Received line from nxssh process [NX> 1000 NXNODE - Version 1.5.0-60 OS (GPL)
] with code [1000]
[Tue Oct 16 22:11:45 2007]: Received code[1000]
[Tue Oct 16 22:11:46 2007]: Received line from nxssh process [NX> 700 Session id: sigma-1000-0236F26B3A56F7C3CA6BA554A39BF55F
] with code [700]
[Tue Oct 16 22:11:46 2007]: Received code[700]
[Tue Oct 16 22:11:46 2007]: Received line from nxssh process [NX> 705 Session display: 1000
] with code [705]
[Tue Oct 16 22:11:46 2007]: Received code[705]
[Tue Oct 16 22:11:46 2007]: Received line from nxssh process [NX> 703 Session type: unix-kde
] with code [703]
[Tue Oct 16 22:11:46 2007]: Received code[703]
[Tue Oct 16 22:11:46 2007]: Received line from nxssh process [NX> 701 Proxy cookie: a32acee79ab0031dba6286a6a09be075
] with code [701]
[Tue Oct 16 22:11:46 2007]: Received code[701]
[Tue Oct 16 22:11:46 2007]: Received line from nxssh process [NX> 702 Proxy IP: 127.0.0.1
] with code [702]
[Tue Oct 16 22:11:46 2007]: Received code[702]
[Tue Oct 16 22:11:46 2007]: Received line from nxssh process [NX> 706 Agent cookie: a32acee79ab0031dba6286a6a09be075
] with code [706]
[Tue Oct 16 22:11:46 2007]: Received code[706]
[Tue Oct 16 22:11:46 2007]: Received line from nxssh process [NX> 704 Session cache: unix-kde
] with code [704]
[Tue Oct 16 22:11:46 2007]: Received code[704]
[Tue Oct 16 22:11:46 2007]: Received line from nxssh process [NX> 707 SSL tunneling: 0
] with code [707]
[Tue Oct 16 22:11:46 2007]: Received code[707]
[Tue Oct 16 22:11:47 2007]: Received line from nxssh process [/usr/lib/nx/nxserver: line 1190: 20880 Terminated              sleep $AGENT_STARTUP_TIMEOUT
] with code [-1]
[Tue Oct 16 22:11:47 2007]: Received code[-1]
[Tue Oct 16 22:11:47 2007]: Received line from nxssh process [NX> 105 ] with code [105]
[Tue Oct 16 22:11:47 2007]: Received code[105]
[Tue Oct 16 22:11:47 2007]: Received line from nxssh process [NX> 596 Session startup failed.
] with code [596]
[Tue Oct 16 22:11:47 2007]: Received code[596]
[Tue Oct 16 22:11:47 2007]: KillAllComponents 0x861cfe0
[Tue Oct 16 22:11:47 2007]: LoginDialog: stopAllTimers
[Tue Oct 16 22:11:47 2007]: LoginDialog: stopProgressTimer
[Tue Oct 16 22:11:47 2007]: LoginDialog::killAllComponents() stopping NXProtoSSH
[Tue Oct 16 22:11:47 2007]: NXProcessUnix::StopProcess process [nxssh] with pid [20748]
[Tue Oct 16 22:11:47 2007]: end of killAllComponents
[Tue Oct 16 22:11:47 2007]: Error is [Session startup failed.
]
[Tue Oct 16 22:11:47 2007]: messageError: [Session startup failed.]
[Tue Oct 16 22:11:47 2007]: printFatalError [Session startup failed.]
[Tue Oct 16 22:11:47 2007]: KillAllComponents 0x861cfe0
[Tue Oct 16 22:11:47 2007]: LoginDialog: stopAllTimers
[Tue Oct 16 22:11:47 2007]: LoginDialog: stopProgressTimer
[Tue Oct 16 22:11:47 2007]: LoginDialog::killAllComponents() stopping NXProtoSSH
[Tue Oct 16 22:11:47 2007]: NXProcessUnix::StopProcess process [nxssh] with pid [20748]
[Tue Oct 16 22:11:47 2007]: end of killAllComponents
[Tue Oct 16 22:11:47 2007]: LoginDialog::ShowConnectionStatus code=[268] str=[Session startup failed.] error=[1]
[Tue Oct 16 22:11:47 2007]: ProgressDialog::printNxStatus: [Session startup failed.]
[Tue Oct 16 22:11:47 2007]: LoginDialog: isReconnecting() [32]
[Tue Oct 16 22:11:47 2007]: LoginDialog: printFatalError: we were reconnecting and we failed - disabling automatic reconnect
[Tue Oct 16 22:11:47 2007]: Settings::flush
[Tue Oct 16 22:11:47 2007]: Settings::flush
[Tue Oct 16 22:11:47 2007]: Logfile path [/home/jeremy/.nx/temp/20744/sshlog] exists.
[Tue Oct 16 22:11:53 2007]: LoginDialog::ShowConnectionStatus code=[251] str=[Disconnecting...] error=[0]
[Tue Oct 16 22:11:53 2007]: ProgressDialog::printNxStatus: [Disconnecting...]
[Tue Oct 16 22:11:53 2007]: KillAllComponents 0x861cfe0
[Tue Oct 16 22:11:53 2007]: LoginDialog: stopAllTimers
[Tue Oct 16 22:11:53 2007]: LoginDialog: stopProgressTimer
[Tue Oct 16 22:11:53 2007]: LoginDialog::killAllComponents() stopping NXProtoSSH
[Tue Oct 16 22:11:53 2007]: NXProcessUnix::StopProcess process [nxssh] with pid [20748]
[Tue Oct 16 22:11:53 2007]: end of killAllComponents
[Tue Oct 16 22:11:55 2007]: LoginDialog: closeEvent received!
[Tue Oct 16 22:11:55 2007]: LoginDialog::destructor called begin
[Tue Oct 16 22:11:55 2007]: LoginDialog: stopAllTimers
[Tue Oct 16 22:11:55 2007]: LoginDialog: stopProgressTimer
[Tue Oct 16 22:11:55 2007]: Utility::getPreferencesFile: 'nxclient' -> '/home/jeremy/.nx/config/nxclient.cfg'
[Tue Oct 16 22:11:55 2007]: Settings::flush
[Tue Oct 16 22:11:55 2007]: LoginDialog::destructor called end

```

---

### Post by kevdog on 2007-10-18
Seems like things are turning south here:

[Tue Oct 16 22:11:46 2007]: Received code[704]
[Tue Oct 16 22:11:46 2007]: Received line from nxssh process [NX> 707 SSL tunneling: 0
] with code [707]
[Tue Oct 16 22:11:46 2007]: Received code[707]
[Tue Oct 16 22:11:47 2007]: Received line from nxssh process [/usr/lib/nx/nxserver: line 1190: 20880 Terminated              sleep $AGENT_STARTUP_TIMEOUT
] with code [-1]
[Tue Oct 16 22:11:47 2007]: Received code[-1]
[Tue Oct 16 22:11:47 2007]: Received line from nxssh process [NX> 105 ] with code [105]
[Tue Oct 16 22:11:47 2007]: Received code[105]
[Tue Oct 16 22:11:47 2007]: Received line from nxssh process [NX> 596 Session startup failed.
] with code [596]
[Tue Oct 16 22:11:47 2007]: Received code[596]

In your sshd_conf file, are x11 process forwarded??  It starts to complain about ssl tunneling, anything in the sshd_conf file that might lend a clue?  Can you deactivate all firewalls or at least open all ports on the client computer for testing purposes.

---

### Post by markdjones82 on 2007-10-18
Update for all.  I have found that freenx server and the nomachine client past 2.0 can have issues.  I downloaded the 1.5 client and it worked fine.  I ended up switching over to Nomachine's free server, but am having issues with logging in a second time  after disconnecting.  I believe i will switch back to freenx and the 1.5 client.

---

### Post by hiranotaka on 2007-10-18
Hi. I encountered exactly the same trouble.
In my environment, this workaround solved the problem.
[https://bugs.launchpad.net/seveas-packages/+bug/148656](https://bugs.launchpad.net/seveas-packages/+bug/148656)

> **BramKuijper said:**
> I am trying to get freenx working on Gutsy Gibbon, but I wasn't lucky till so far..

I followed the installation instructions and everything went allright, including verifying the ssh connection using nx server. 

However, after installing nxclient on another Ubuntu machine (a feisty box in this case) and trying to log in on my nxserver, it got into a working X session but then the client aborted:

```
NXPROXY - Version 2.1.0

Copyright (C) 2001, 2006 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '13712'.
Session: Starting session at 'Mon Oct  1 13:33:11 2007'.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using adsl link parameters 512/24/1/0.
Info: Using cache parameters 4/4194304/8192KB/8192KB.
Info: Using image streaming parameters 50/128/1024KB/2048/256.
Info: Using image cache parameters 1/1/32768KB.
Info: Using pack method '16m-jpeg-7' with session 'unix-gnome'.
Info: Using ZLIB data compression 3/3/0.
Info: Using ZLIB stream compression 6/6.
Info: No suitable cache file found.
Info: Listening for font server connections on port '11000'.
Session: Session started at 'Mon Oct  1 13:33:11 2007'.
Info: Established X server connection.
Info: Using shared memory parameters 1/2048K.
Session: Terminating session at 'Mon Oct  1 13:33:41 2007'.
Info: End of NX transport requested by signal '15'.
Info: Waiting the cleanup timeout to complete.
Info: Shutting down the NX transport.
Warning: Parent process appears to be dead. Exiting watchdog.
```

Also, I looked into the nxserver's log files, but this didn't give me any further clues:

```
-- NX SERVER START: -c /usr/lib/nx/nxserver - ORIG_COMMAND=
HELLO NXSERVER - Version 1.5.0-60 OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: bram
NX> 102 Password:
Info: Auth method: passdb
NX> 103 Welcome to: theobio36 user: bram
NX> 105 listsession --user="bram" --status="suspended,running" --geometry="1280x1024x24+render" --type="unix-gnome"
NX> 127 Sessions list of user 'bram' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: bram
NX> 105 startsession  --link="adsl" --backingstore="1" --nodelay="1" --encryption="1" --cache="8M" --images="32M" --media="0" --session="theobio" --type="unix-gnome" --geometry="1280x974" --kbtype="pc105/us" --screeninfo="1280x974x24+render"

&link=adsl&backingstore=1&nodelay=1&encryption=1&cache=8M&images=32M&media=0&session=theobio&type=unix-gnome&geometry=1280x974&kbtype=pc105/us&screeninfo=1280x974x24+render&clientproto=1.5.0&user=bram&userip=145.98.213.240&uniqueid=F1930E33C5ACB1239207772EFC3FD34C&display=1000&host=127.0.0.1
NX> 1000 NXNODE - Version 1.5.0-60 OS (GPL)
NX> 700 Session id: theobio36-1000-F1930E33C5ACB1239207772EFC3FD34C
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 5687642257a7ad1fe8b390b98aecacb5
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 5687642257a7ad1fe8b390b98aecacb5
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye
NX> 1004 Error: NX Agent exited with exit status 1.
NX> 1006 Session status: closed
```

anyone has any pointers on information on solving this problem, or where to find more details what is causing this?

---

### Post by Bellesarius on 2007-10-24
I got the same exact behavior on gusty with freenx.

Sean

---

### Post by Bellesarius on 2007-10-24
Bingo.. font paths were at fault!!!

[https://bugs.launchpad.net/seveas-packages/+bug/148656](https://bugs.launchpad.net/seveas-packages/+bug/148656)

Make sure to use the 1.5  NX Client... the latest versions won't.

Sean

---

### Post by kevdog on 2007-10-24
Im glad you guys have figured out the problem with the font paths, that was one of the problems I had way back in the original post.  Is there anything that might be helpful to add to the original instructions that would help other users avoid this problem??

---

### Post by nuzzy on 2007-11-27
Hello,

I'm trying to login to my gutsy server with the 1.5 nxclient with no success.  I'm getting the following:
```
NXPROXY - Version 1.5.0

Copyright (C) 2001, 2005 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '4328'.
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
Error: Lost connection to peer proxy on FD#8.
Error: Connection with remote peer broken.
Error: Please check the state of your network and retry.

-- NX SERVER START: -c /usr/lib/nx/nxserver - ORIG_COMMAND=
HELLO NXSERVER - Version 1.5.0-60 OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: username
NX> 102 Password:
Info: Auth method: passdb
NX> 103 Welcome to: mail.server.com user: username
NX> 105 listsession --user="username" --status="suspended,running" --geometry="1680
x1050x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'username' for reconnect:

Display Type             Session ID                       Options  Depth Screen
        Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------
------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: username
NX> 105 startsession --session="home" --type="unix-gnome" --cache="8M" --images=
"32M" --link="lan" --kbtype="pc102/en_US" --nodelay="1" --encryption="1" --backi
ngstore="when_requested" --geometry="1680x1022" --media="0" --agent_server="" --
agent_user="" agent_password="******""  --screeninfo="1680x1022x32+render"

&session=home&type=unix-gnome&cache=8M&images=32M&link=lan&kbtype=pc102/en_US&no
delay=1&encryption=1&backingstore=when_requested&geometry=1680x1022&media=0&agen
t_server=&agent_user=&agent_password=******&screeninfo=1680x1022x32+render&clien
tproto=1.5.0&user=username&userip=12.16.126.3&uniqueid=A317FFDE09C597D687B69BCE7773
CE58&display=1000&host=127.0.0.1
NX> 1000 NXNODE - Version 1.5.0-60 OS (GPL)
NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 NX> 700 Session id: mail.server.com-1000-A317FFDE09C597D687B69BCE7773CE58
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: ccc8e05c3498813c9abde5cc52ed2de1
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: ccc8e05c3498813c9abde5cc52ed2de1
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
bye
Bye
NX> 999 Bye
NX> 1004 Error: NX Agent exited with exit status 1.
NX> 1006 Session status: closed

```

Any ideas what may be the issue?  I'm using SSH port 22 which is open on the FW.

---

### Post by kevdog on 2007-11-27
Have you ever logged in before -- even once?

---

### Post by nuzzy on 2007-11-27
No, but I fixed it using another tutorial:

[http://ubuntuforums.org/showthread.php?t=620057](http://ubuntuforums.org/showthread.php?t=620057)

---

### Post by kevdog on 2007-11-27
Can you briefly summarize what the solution was?  Was it the font path?

---

### Post by daflame on 2007-11-27
> **kevdog said:**
> Can you briefly summarize what the solution was?  Was it the font path?

I have posted updated packages for Gutsy at the location mentioned above.  From the trouble I was having from an earlier post I gave up on the Seveas repos since they are still using an outdated package setup.  Why use nxclient 1.5   which is getting harder to find and an out of date FreeNX when you can update to nxclient 3.0 which is 64bit safe and built for 64bit and FreeNX 0.7.1 using the nx-3.0 backend?  Debian is the only Linux flavor this far behind sadly.  Go here if you need packages for Gutsy and please stop using outdated software:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

### Post by kevdog on 2007-11-28
I believe the title of the HowTo is labeled how to use seveas repositories on the Feisty -- not Nomachine's client on Gutsy.  When I wrote this thread it was specifically for Feisty *hint check the title.  I am sure there are better ways now of setting up freenx, however I was trying to recommend a way that used software that was not as restrictive as NoMachine's.

---

### Post by daflame on 2007-11-29
> **kevdog said:**
> I believe the title of the HowTo is labeled how to use seveas repositories on the Feisty -- not Nomachine's client on Gutsy.  When I wrote this thread it was specifically for Feisty *hint check the title.  I am sure there are better ways now of setting up freenx, however I was trying to recommend a way that used software that was not as restrictive as NoMachine's.

I am not using any of NoMachine's commercial software on the forum except the client, which although commercial it is still free to use but not open source.

I am actually using freenx 0.7.1 on the forum with the nx-3.0 open source backend.  All open source and free as in freedom.

I do not have a repo yet, but I wouldn't mind someone offering to host the packages.  Also, if you would like, I can offer up the sources and diffs for someone to compile (I do not have Feisty anymore) so that everyone here can update their feisty version as well.

Finally, I apologize if my post sounded condescending to your brilliant efforts to assist the community (I have read most of the posts) as you have done an excellent job, but I was just stating the fact that we in the Ubuntu Linux world are way behind and it's time to catch up.  I do not mean to disrespect anyone.

---

### Post by kevdog on 2007-11-29
Thanks for your edition to FreeNx -- anyone using FreeNx I would point them to your post as it is updated compared to mine.  Ubuntu/Debian Repositiories in general offer older versions of software.  That is kind of the nature of Debian in general.  I will try to install freenx server and client according to your instructions.  Thanks for the updated instructions.  I'm glad at least someone in the community provides updates to proposed solutions that worked in the past, but due to improvements may not be applicable for today's versions.

---

### Post by kwaanens on 2008-02-26
2 small questions:

- If I want to access my freenx server computer from somewhere not on the local network, what host do I put in. I currently connect to the computer name, but that doesn't work on the internet, I'm assuming?

- Is there any way I can be able to copy files over freenx+ssh easily? I can currently use the clipboard across computers, but not files.

Thanks for a great howto!

EDIT: I'm using Gutsy 64 bit on both server and client, and had to fiddle around with some stuff to get it working.

---

### Post by kevdog on 2008-02-26
#1 - you would access your computer by IP address, or if using noip.com or something like this service, it would assign your computer a name so it would associate the IP address with a name.  For this two work, if you are behind a router, your computer should be assigned an IP address, the ssh port from the router needs to be forwarded to the server, and the iptables (firewall) modified (using firestarter, guarddog, or manually) to allow inbound connections.

#2 - Copy files -- Im not sure about this.  I only can think of using scp.

---

### Post by clever on 2008-02-26
The easiest way I have found to copy files is to make an ssh connection directly with the Nautilus file browser.

Open Nautilus, and if it's set to show individual buttons for each directory at the top of the window then you have to change to address mode.  Just click the icon on the left with the paper & pencil to switch to a text field where it will let you type an address.

Then type in ssh://serverIP and hit enter.  It will make the connection and prompt for your username and password.  After that you can browse the file system very easily and copy/paste files.

You can also use Places | Connect To Server to create an SSH connection that will create an icon on your desktop for easy use in the future.

---

### Post by kwaanens on 2008-02-27
> **clever said:**
> The easiest way I have found to copy files is to make an ssh connection directly with the Nautilus file browser.

Open Nautilus, and if it's set to show individual buttons for each directory at the top of the window then you have to change to address mode.  Just click the icon on the left with the paper & pencil to switch to a text field where it will let you type an address.

Then type in ssh://serverIP and hit enter.  It will make the connection and prompt for your username and password.  After that you can browse the file system very easily and copy/paste files.

You can also use Places | Connect To Server to create an SSH connection that will create an icon on your desktop for easy use in the future.

Thanks for that! I managed to SSH into it. I should have thought of this, it was so obvious... This helps a lot.
But no way to copy files directly within FreeNX as of yet then?

---

### Post by kwaanens on 2008-02-27
> **kevdog said:**
> #1 - you would access your computer by IP address, or if using noip.com or something like this service, it would assign your computer a name so it would associate the IP address with a name.  For this two work, if you are behind a router, your computer should be assigned an IP address, the ssh port from the router needs to be forwarded to the server, and the iptables (firewall) modified (using firestarter, guarddog, or manually) to allow inbound connections.

Thanks!
I'll check this out when I find the time.

---

### Post by drseuk on 2008-08-29
> **RealMabu said:**
> Hi,
what if I fail step 6?
I have managed to set up ports to 8888 and here is what I get:
```

root@...:/var/lib/nxserver/home/.ssh# ssh -i client.id_dsa.key nx@localhost -p 8888
Read from socket failed: Connection reset by peer
root@...:/var/lib/nxserver/home/.ssh# 

```

Checking my config against your steps:
1.Repositories: OK
2.I miss the:
```
FontPath        "/usr/share/fonts/X11/misc/"
```
But i guess this isnt my problem...
3.I miss nxclient but I just need the server on my ubuntu box...
4.I edited /etc/ssh/sshd_config adding the line:
```
AuthorizedKeysFile %h/.ssh/authorized_keys2
```
5.I use SSHD on port 8888 and accomplished this by editing both /etc/ssh/sshd_config:
```
Port 8888
```
and /etc/nxserver/node.conf:
```
SSHD_PORT=8888
```

Any ideas?

P.S. *EDIT*
I add the verbose output of the debugging ssh command... maybe you guys find it useful...
```

root@...:/var/lib/nxserver/home/.ssh# ssh -v -i client.id_dsa.key nx@localhost -p 8888
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 8888.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file client.id_dsa.key type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug1: An invalid name was supplied
Configuration file does not specify default realm

debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: An invalid name was supplied
Configuration file does not specify default realm

debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer
root@...:/var/lib/nxserver/home/.ssh# 

```
Hi,

Not being able to login to the localhost (from within a remote ssh session) to the localhost *IS* caused by fiddling with the ListenPort option. Restoring ListenPort to 0.0.0.0 will fix this and also fix remote NX connections in this instance.

This should be bumped. Nothing to do with iptables. Also please c.f., [http://ubuntuforums.org/showthread.php?t=231451](http://ubuntuforums.org/showthread.php?t=231451) [Subject: "**ssh username@localhost fails, but can ssh into the computer from another computer**"].

Cheers,

James

---

### Post by svaens on 2009-02-07
Hi all, 

I have a question regarding how to ensure the ssh is setup as securely as freeNX itself. 

I followed the instructions found here:
[https://help.ubuntu.com/community/FreeNX#Using%20custom%20SSH%20keys]("https://help.ubuntu.com/community/FreeNX#Using%20custom%20SSH%20keys")
and setup the custom keys. I am using ssh for authentication (not the NX database or anything like that). 

That all worked fine. Really great. I tested the connection from a client to my freenx machine, first without the client key i had custom generated and it correctly would not authenticate. Then after importing the custom key i'd generated, I was able to authenticate. I am still asked for username/password authentication (user account must exist) which is how I like it, and I can log in and get a session no problems at all. 

However, a few questions:

1. the purpose of setting up the custom keys at all was why?  So that no one can connect without them right? Otherwise it is just a matter of guessing username/password combination, and that is not as secure right?

2. well, if my assumptions about (1) are correct, what about sshd itself? 
   After i installed freenx, (which installed sshd) I am now able to connect to my machine simply using ssh. But to do so i need no key file or anything. It simply works. So, what was the point of setting up extra security for freenx, if ssh itself is still not as secure. 

3. If my assumptions about 2 are correct, I would like to provide the same level of security for ssh itself as for freenx. 
Can I apply public/private key security with ssh 
(e.g. as described in this website: [http://www.debuntu.org/ssh-key-based-authentication]("http://www.debuntu.org/ssh-key-based-authentication") without breaking my freenx setup?

any advice will be greatly appreciated!

---

### Post by kevdog on 2009-02-07
FreeNX runs on top of ssh.  Your ability to ssh into the server via the command line only has nothing to do with FreeNx.  If you want to use only key based authentication for ssh (and not passwords), you need to make the change within the sshd_config file.  

I'm not sure if I have answered your questions.

---

### Post by svaens on 2009-02-08
Almost. Thanks for the reply. 

Two more questions:

1. Can you setup ssh to use BOTH key based authentication and username/password?

2. Are you saying (from your post) that what changes I make to ssh authentication will NOT affect the setup for freeNX, and the client connections to it?

thanks again for your help!

---

### Post by kevdog on 2009-02-08
Yes, I believe by default the ssh daemon excepts both passwords and keys.

FreeNx uses key based ssh authentication, with internal freenx username/password authentication.  As long as the freenx key is included in the individual's authorized_keys file on the server, you should be good to go.

---

### Post by joris1977 on 2009-06-12
> **kevdog said:**
> Yes, I believe by default the ssh daemon excepts both passwords and keys.

FreeNx uses key based ssh authentication, with internal freenx username/password authentication.  As long as the freenx key is included in the individual's authorized_keys file on the server, you should be good to go.


I guess you are right, but it took some more steps to get NX and ssh with key authentication working. 

I posted how I did it in this thread: 
[http://ubuntuforums.org/editpost.php?do=updatepost&p=7443968](http://ubuntuforums.org/editpost.php?do=updatepost&p=7443968)

Because this thread might be easier to find for people with the same question. I post my solution here as well. 

[COLOR="Red"]WARNING: I am new to linux and feel uncomfortable editing config files I don't totally understand. As far I can understand it seems safe what I have done and is safer than a ssh setup without key authentification but try at your own risk.[/COLOR]

I would really appreciate any critical comments on how I did this from people with a better understanding of NX and SSH.

This two links putted me on the right path:
[http://wiki.centos.org/HowTos/FreeNX](http://wiki.centos.org/HowTos/FreeNX)
[http://linuxgazette.net/135/knaggs.html](http://linuxgazette.net/135/knaggs.html)

Steps to take

Install ssh. I followed this tutorial:
[http://www.debuntu.org/ssh-key-based-authentication](http://www.debuntu.org/ssh-key-based-authentication)

Install freeNX I followed this tutorial:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

So now you have a secure ssh setup with key authentification but cannot login to NX over ssh

Edit the /etc/ssh/sshd_config file and change/add the following lines:
```
AllowUsers nx
AllowUsers (your user name)
UsePAM yes
```

Don't forget to restart the sshd daemon after making that change:

```
sudo /etc/init.d/ssh restart
```

Next step is to copy the  /var/lib/nxserver/home/.ssh/client.id_dsa.key to your client machine. (You probably already did this following the freenx howto)  

But you need to copy the key on the client machine to .ssh and rename it.

like this:

```
cp $HOME/client.id_dsa.key $HOME/.ssh/id_dsa
```

By now, you should be ready to login to the nx server over ssh

You can try this with:

```
ssh nx@remote-server
```
It will respond with
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 105 

Works? Good. Let's go on. By default, if you try to connect to the NX server, it will use the nx account for the ssh connection (with key authentication) but it will try also to connect in ssh with your own username/password to the host you're trying to reach. Because you've disabled the PasswordAuthentication over ssh, you have to use the NX Database to allow pass-through authentication. Be sure that /etc/nxserver/node.conf file contains the following line :

```
ENABLE_PASSDB_AUTHENTICATION="1"
```
 
I am not sure if it is really necessary but I guess it can do no harm to restart to freenx server at this point.

```
sudo nxserver --restart
```

Last step is to create a account on the NX server. 

```
sudo nxserver --adduser (yourusername)
```

NX server will reply with:

NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 716 Public key added to: /home/yourusername/.ssh/authorized_keys2
NX> 1001 Bye.
NX> 999 Bye

and add a  password

```
sudo nxserver --passwd (yourusername)
```

NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
New password: 
Password changed.
NX> 999 Bye

That's it, now you should be able to do a secure login with the NoMachine NX client for linux using key authentification

Works for me and should work for you.

:popcorn:

Please comment if you think this setup is not secure or unwise for some reason.

---

### Post by goldbuffalo on 2009-06-16
Dear DEVDOG,
First many thanks for your tutor!!!!
i passed setting up freeNX (tested ok wit 3 user) but when I add new user. It can't login wit log: NX> 148 Server capacity: not reach for user: goldbuffalo

Pls help cause my stupid understanding yr tutor

Many thanks :popcorn:

---

### Post by goldbuffalo on 2009-06-16
Dear DEV DOG

I fixed my last posted by gedit sshd_config %h/.ssh/authorized_keys2 ???? Why does it run? Very very thanks if explain me!!!

Thanks so much !!! :popcorn:

---

### Post by AlexanderDGreat on 2009-10-15
Does this work with a Static IP address? When I switched to a static IP address by configuring /etc/network/interfaces, auto eth0, iface eth0 inet static, etc... it doesn't work. What could be the problem?

Thanks for the guide.

---

### Post by kevdog on 2009-10-17
If you can't make it work with a static IP address, your problem is obviously related to something else.  I would first try setting up a simple ssh server with static ip addresses and troubleshooting that way.

---

### Post by joris1977 on 2009-11-04
Hi kevdog

Did you write the tutorial in the community wiki? It seems not to be working anymore with karmic. I can't create any custom_keys, when i follow the wiki. It was working in Jaunty and hardy. Does anybody else have this issue?

And stopping the server with 

sudo /etc/init.d/freenx stop isn't working in karmic

sudo /ect/init.d/freenx-server stop is working ,so no drama here

No custom-keys is weird, but maybe something has changed?

grts

Joris

---

### Post by cougarmaster on 2009-11-05
Has anyone got remote printing to work? I mean the client is Windows XP with a Xerox Phaser 3116 usb connected locally and the server is Ubuntu 9.10. I want to be able to print from ubuntu to windows xp. Anyone have any tips or howtos ? Been at it 3 weeks and still cant get it to print. File sharing and stuff all works just printing is so stubburn. It recognises my printer and adds it to the printer configurations but when I print anything from any application it just keeps it in queue and holds it there. Please anyone... If your configuration is working please post you config files so I can see what I am missing?

---

### Post by kevdog on 2009-11-05
I have to really update this thread.  As you can see I wrote this a long time ago on Feisty Fawn -- (which is no longer actively supported by Canonical now).  Things have definitely changed with the Karmic release.  Possibly this weekend when I have time I will update the thread.

---

### Post by joris1977 on 2009-11-05
ah cool looking forward to it. Hope it solves my troubles with the karmic freenx.

---

### Post by cougarmaster on 2009-11-06
Hope you can give a more detailed setup for file sharing and printing from a windows 2000,xp,vista and also from a ubuntu or any gnome desktop.

---

### Post by kevdog on 2009-11-07
> **cougarmaster said:**
> Hope you can give a more detailed setup for file sharing and printing from a windows 2000,xp,vista and also from a ubuntu or any gnome desktop.

Those topics will most likely not be covered..

---

### Post by cougarmaster on 2009-11-07
Why? Is it because it cant be done? Or still a long way before nxserver can do printing? Because then the company will need to buy windows server and use the RDP printing meaning they will give up on linux entirely and shift back to windows.

---

### Post by joris1977 on 2009-11-08
> **cougarmaster said:**
> Why? Is it because it cant be done? Or still a long way before nxserver can do printing? Because then the company will need to buy windows server and use the RDP printing meaning they will give up on linux entirely and shift back to windows.


I don't know if freenx can already do printing, but I am pretty sure that Nomachine NX server can do printing. If the company you work for is ready to spent a lot of money on microsoft than they might want to consider to spent some money on Nomachine as well. When you buy the Nomachine server I guess support is included. I recall you can test the Nomachine NX server for free.   

They seem to be a nice company, because they release the source code and this is where freenx is based on.   

[http://www.nomachine.com/]("http://www.nomachine.com/")

---

### Post by cougarmaster on 2009-11-08
I found another program called x2go but I do prefer freenx. But it really looks nice and supports remote printing. BUT I hope you can try out the printing.

---

### Post by kevdog on 2009-11-09
There will be no input about printing from me -- hopefully someone else may be able to add this information which I can then add to the main page.

---

### Post by spartan1011 on 2010-05-19
This awesome! Worked great thanks for the tut. Keep up the good work.

---

### Post by jaaf64 on 2010-08-29
Hi,
I am new to ssh and to FreeNX.

I managed to remotely log with FreeNX and SSH following the instruction of
 **[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX).**

I started with default keys but when I wanted to create custom keys I had trouble with this:

> [COLOR="navy"]After installation, FreeNX will use a set of default ssh keys for authentication. This is a security risk, especially on any internet-facing machines, and the default keys should be replaced with your own custom keys.

To change the default keys to your own custom keys - on the machine hosting the freenx-server, run the command:

sudo dpkg-reconfigure freenx-server
This will launch a dialogue that will guide you through the generation of custom keys. On the first page hit 'OK' and on the second page select 'Create new custom keys'

a key file called client.id_dsa.key will be created in: /var/lib/nxserver/home/custom_keys/

Now, we need to transfer the key to the client machine so that it can be imported in the FreeNX client application. First copy the key to your home directory on the server machine:

sudo cp /var/lib/nxserver/home/custom_keys/client.id_dsa.key ~/
Next, copy client.id_dsa.key to your client machine. Ideally you should copy the file securely, for example by running the following command from the client computer:[/COLOR]

In fact there was no custom_keys directory created.


Please see picture in attachments

Eventually I got this

> jaaf@jaaf-desktop:~$ sudo dpkg-reconfigure freenx-server
[sudo] password for jaaf: 
stop: Unknown job: freenx-server
start: Unknown job: freenx-server
jaaf@jaaf-desktop:~$


I don't know what to do!?

---

### Post by bugalo on 2010-08-31
The keys are actually in

/var/lib/nxserver/home/.ssh/client.id_dsa.key

---

### Post by jaaf64 on 2010-08-31
Thank you.
That's fine now.

---

### Post by Tamale on 2010-09-01
Long time user of nomachine's server/client software, but only recently wanted to be able to play audio on the client from the server.

Tried Audacious with the esd output, and it actually worked first try.. but.. lots of stuttering. I'd try playing with settings but I can't find any to tweak in audacious, nxclient or server, or ubuntu 10.04.. help!

---

### Post by supremo900 on 2010-09-20
Hey, I'm getting a "small" error.
I installed with successful FreeNX on the Ubuntu Hardy, I can log in and use with all features but, if I close the window (terminate or suspend session) I can't log in anymore.... So, to fix this I have to reboot my vps.

Can anyone help me?


**Please, answer: How is my english?

---

### Post by peshko-lnx on 2010-11-12
So, I followed the instructions, and I keep getting the error message "Authentication failed for user <username>".

I can successfully ssh to the box using the <username> and nx using keys and no password. I tried with Mac and Ubuntu client and getting the same error message.

How can I debug where it fails authentication? In the auth.log I get:

Nov 12 17:48:43 mylaptop nxserver[10381]: (nx) Failed login for user=<username> from IP=xxx.xxx.xxx.xxx

One question I have. Do I need to add user using nxserver --adduser

```
root@mylaptop:/var/log# nxserver --adduser
NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 500 Error: The passdb function is not activated in node.conf.

Most probably your FreeNX setup will work out of the box without this
functionality and you've been misleaded by an old tutorial or old
documentation to do this step.

If however you really need this functionality, just set
ENABLE_PASSDB_AUTHENTICATION="1" in node.conf.

NX> 999 Bye
```

---

