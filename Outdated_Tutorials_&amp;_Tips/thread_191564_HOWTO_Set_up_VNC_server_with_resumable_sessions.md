---
title: "HOWTO: Set up VNC server with resumable sessions"
date: 2006-06-07
forum: Outdated Tutorials &amp; Tips
---

### Post by L4mp on 2006-06-07
Set up VNC server with resumable sessions on dapper (6.06) 


1. Enable XDMCP

```
sudo gedit /etc/gdm/gdm.conf

```

then find this rule:
# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
# RemoteGreeter=/usr/lib/gdm/gdmlogin

remove the '#' in the last line so there should be:

# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
   RemoteGreeter=/usr/lib/gdm/gdmlogin


Note: Before doing the next step, you need to make sure the extra repositories (e.g. universe) are enabled:
[http://easylinux.info/wiki/Ubuntu#Ho...a_repositories](http://easylinux.info/wiki/Ubuntu#Ho...a_repositories)

2. Install required packages (vncserver and xinetd)

Code:
```

sudo apt-get install vnc4server xinetd
```


Note to AMD64 users: The current version of vnc4server in the repositories has a bug, so you need to download and install the fixed vnc4 packages as shown below:

Code:

```
wget http://qt1.iq.usp.br/download/vnc4server_4.0-7.3_amd64.deb wget http://qt1.iq.usp.br/download/xvnc4viewer_4.0-7.3_amd64.deb sudo dpkg -i vnc4server_4.0-7.3_amd64.deb sudo dpkg -i xvnc4viewer_4.0-7.3_amd64.deb
```



3. Set the VNC passwd
Code:

```
sudo vncpasswd /root/.vncpasswd
```


4. Add vnc service to xinetd:
Code:
```

sudo gedit /etc/xinetd.d/Xvnc

```

Enter this into the new file:

Code:
```

service Xvnc { type = UNLISTED disable = no socket_type = stream protocol = tcp wait = yes user = root server = /usr/bin/Xvnc server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd port = 5901 }

```

5. Restart xinetd (usually there is no need to reboot, but occasionally it might be required)

Code:```


sudo /etc/init.d/xinetd stop sudo killall Xvnc sudo /etc/init.d/xinetd start
```


6. That's it! To test that this is working first try to connect from the same machine (the machine we just set up the VNC server on):

Code:
```

vncviewer localhost:1

```

You should be prompted for the VNC password, and then see the GDM login screen where you can login and start a new X session. If that works, you can now go ahead and try to connect from remote machine using your favorite VNC client (remember to first close the local vncviewer we started above). Remember to use the VNC server machine's domain name or IP address, followed by :1 (e.g. 192.168.0.100:1). If connecting locally as shown above works, but connecting remotely fails, then this means you have a problem with a firewall which is blocking some ports. See the notes below about how to deal with that.

Note about ports: The VNC server set up as shown uses TCP port 5901. If you are using firewall software (e.g. firestarter) on that machine, you need to allow incoming connections on this port. If you are using a router which assigns your machine a private address (e.g. 192.168.0.100) which is not accessible from the internet, then you need to forward TCP port 5901 from the router to this machine.

Note about security: This setup allows any user to start an X-session remotely by logging in using his regular password (after starting the VNC connection using the VNC password), so if the user disconnects without logging out, any other user which knows the VNC password can connect afterwards and resume the same session that the first user started. So if you do not want to log out before disconnecting, it's advisable to at least lock your VNC X-session screen. Also note that while a remote user is connected thru VNC, no other connection will be accepted. An idle VNC client will be disconnected after one hour, but this can be changed by using the "-IdleTimeout" option in the server_args line in /etc/xinetd.d/Xvnc. For example, you can add "-IdleTimeout 300" to change it to 5 minutes.




ps. This was copy/pasted from a few posts made by Tichondrius and elemental666. I simply putted them together and tested everything! It works here for me now.

If questions just post :)

---

### Post by Cirrocco on 2006-06-08
you missed a step:

**enable remote login**
system -> administration -> login Window
remote tab
choose "same as local" (or whatever?)

---

### Post by Cirrocco on 2006-06-08
but I can't get mine working

when I do: "vncviewer localhost:1"

I get:
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server


ideas?

---

### Post by sirspiddy on 2006-06-10
The problem is with the formatting of the text, if you blindly copy(which I did), it doesn't work.  Here is the same code formatted for those who like to copy and paste:

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

---

### Post by brotheralwyn on 2006-06-10
OK. I've been trying to do this for about 5 hours now and still can't get this to work.

When I run vncviewer I just get a window with an X session running and nothing else (no terminal window, no window manager, no login screen. Just a gray background with an "X" cursor). How do I get the login manager, gnome, etc. to come up running in the vncserver???????


On another question:
Eventually I would like to set this up so I can tunnel VNC over SSH. I have SSH working, but is there any way to tell the vncserver only to accept connections coming in over SSH?

---

### Post by halitech on 2006-06-10
having the same problem here with the greybackground and x. any help would be appreciated

---

### Post by sirspiddy on 2006-06-10
OK, I had the same problem before until I performed the following

System->Administration->Login Window
Click on Remote Tab
Changed style to "Same as Local"
Click on the "Configure XDMCP..." buton
Uncheck "Honor indirect request"
Click Close on both windows

reboot

NOTE:  I have both vncserver and vnc4server on my pc.

Far as the SSH session I typically use openssh or putty on a remote machine
I connect to the ssh server running on the Ubuntu box and create a local mapping
by using a local port address mapped to the IP:VNC Port the Ubuntu box 
Then simply run your vnc client by connecting to "Localhost"LocalPort"

Hope that helps

---

### Post by halitech on 2006-06-11
that got it for me, thanks alot

---

### Post by brotheralwyn on 2006-06-11
Thanks! A reboot worked for me. Guess I've been using a Mac too long.....

---

### Post by johnthejack on 2006-06-13
I'm trying to set this up with Ultra vncviewer in Windows xphome and Xvnc in Ubuntu as server. I've followed these instructions. I open Ultra vncviewer on my Windows and I get "Failed to get server address". I am not sure whether it's relevant but the Port Ultra Vnc uses is 5900. I tried it also with the last line in the edit above changed from 5901 to 5900, but still the same result. Is there something I should have done before this page of instructions? Is there something I can check? Thanks.

---

### Post by johnthejack on 2006-06-13
Ok sorry, stumbled on this thread after a search. Just seen I have to ask question somewhere else.

---

### Post by 3rdparty on 2006-06-15
whatever updates were just released got this working again for me (it was working in breezy, but broke in dapper), automatically!

---

### Post by Cirrocco on 2006-06-16
I hope your right.

I'm downloading them now - new kernel, bunch of gnome2 stuff, etc...

I am just sick of using the built in "remote desktop" vnc server.  It's slow and choppy and smells of alderberries.

---

### Post by MystaMax on 2006-06-19
should this work w/ xubuntu?

---

### Post by MystaMax on 2006-06-19
nevermind, I got it working. I had to also restart my server, and adjust my Xvnc file to reflect what sirspiddy suggested. Other than that, it was a pretty painless process. Thanks for the guide!

---

### Post by cofin on 2006-06-19
This procedure worked flawlessly in Xubuntu for me.

---

### Post by dhalexos on 2006-06-21
I'm a new linux user en i chose ubuntu 6.06. It's a clean install.

Now I tried this howto and I always have dependencies problems when i try to install vnc4server.

The following packages have unmet dependencies.
vnc4server: Depends: xserver-common but it is not installable
E: Broken packages

What did I wrong?

thx

---

### Post by p_alexander on 2006-06-21
L4mp copied an older version of this HOWTO from the Breezy thread. The one below is updated with extra info for AMD64 users especially and it allows normal copy/paste with all the line breaks in the right spots. But his leaves out a critical step. If L4mp could update that would be great and I'll remove this.

Oh yeah, my VNC broke with the grey screen after some updates today, including a kernel upgrade. Looking into it and will update when I fix.

--------------------------------------------------

I added a bunch of stuff that I had to do in order to make this work on my amd64 box. This box was originally installed under 5.10 and upgraded to 6.06. Everything pretty much out of the box. YMMV.

Oh yeah, this also made Vino work as well, not sure why. Perhaps the xdmcp stuff. So, vino is on display 0, vnc4 on display 1.

This is copied from L4mp's post above with my changes added to the amd64 section.

PS - Ignore the "HTML" comment in the "HTML Code" boxes. I couldn't get regular code boxes to include line breaks. Noob at work.

1. Enable XDMCP

```
sudo gedit /etc/gdm/gdm.conf

```
then find this rule:
# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
# RemoteGreeter=/usr/lib/gdm/gdmlogin

remove the '#' in the last line so there should be:

# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
   RemoteGreeter=/usr/lib/gdm/gdmlogin

[COLOR="Red"]Note: I had to also change another part of the gdm.conf file. Also, a restart was required so gdm could read the new configuration.[/COLOR]

Look for the following piece of text in /etc/gdm/gdm.conf
[html]
[xdmcp]
# Distributions: Ship with this off.  It is never a safe thing to leave out on
# the net.  Setting up /etc/hosts.allow and /etc/hosts.deny to only allow local
# access is another alternative but not the safest.  Firewalling port 177 is
# the safest if you wish to have xdmcp on.  Read the manual for more notes on
# the security of XDMCP.
Enable=false
[/html]
Change the Enable=false to Enable=true

Note: Before doing the next step, you need to make sure the extra repositories (e.g. universe) are enabled:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

2. Install required packages (vncserver and xinetd)

Code:
```

sudo apt-get install vnc4server xinetd
```
i386 users can skip to step 3, AMD64 users continue to 2a.

2a. Note to AMD64 users: The current version of vnc4server in the repositories has a bug, so you need to download and install the fixed vnc4 packages as shown below:

Code:
[HTML]
wget http://qt1.iq.usp.br/download/vnc4server_4.0-7.3_amd64.deb
wget http://qt1.iq.usp.br/download/xvnc4viewer_4.0-7.3_amd64.deb
sudo dpkg -i vnc4server_4.0-7.3_amd64.deb
sudo dpkg -i xvnc4viewer_4.0-7.3_amd64.deb
[/HTML]
Some people may have unmet depencies in these packages and will need to install additional packages.

Code:
[HTML]
sudo apt-get install gcc-3.3-base
sudo apt-get install libstdc++5
[/HTML]
There is one dependent package that cannot be installed as it has been deprecated in the new 6.06. Therefore, we have to force the vnc4server packages to install.

Code:
[HTML]
sudo dpkg -i --force-all vnc4server_4.0-7.3_amd64.deb 
sudo dpkg -i --force-all xvnc4server_4.0-7.3_amd64.deb
[/HTML]
I am loathe to force package installs BUT it seems to work in this case. An updated, working AMD64 vnc4server package would be preferable.

3. Set the VNC passwd

Code:
```
sudo vncpasswd /root/.vncpasswd
```

4. Add vnc service to xinetd:

Code:
```

sudo gedit /etc/xinetd.d/Xvnc

```
Enter this into the new file:

Code:
[HTML]
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
[/HTML]

5. Restart xinetd (usually there is no need to reboot, but occasionally it might be required)

Code:
[HTML]
sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo /etc/init.d/xinetd start
[/HTML]

6. That's it! To test that this is working first try to connect from the same machine (the machine we just set up the VNC server on):

Code:
```

vncviewer localhost:1

```

You should be prompted for the VNC password, and then see the GDM login screen where you can login and start a new X session. If that works, you can now go ahead and try to connect from remote machine using your favorite VNC client (remember to first close the local vncviewer we started above). Remember to use the VNC server machine's domain name or IP address, followed by :1 (e.g. 192.168.0.100:1). If connecting locally as shown above works, but connecting remotely fails, then this means you have a problem with a firewall which is blocking some ports. See the notes below about how to deal with that.

Note about ports: The VNC server set up as shown uses TCP port 5901. If you are using firewall software (e.g. firestarter) on that machine, you need to allow incoming connections on this port. If you are using a router which assigns your machine a private address (e.g. 192.168.0.100) which is not accessible from the internet, then you need to forward TCP port 5901 from the router to this machine.

Note about security: This setup allows any user to start an X-session remotely by logging in using his regular password (after starting the VNC connection using the VNC password), so if the user disconnects without logging out, any other user which knows the VNC password can connect afterwards and resume the same session that the first user started. So if you do not want to log out before disconnecting, it's advisable to at least lock your VNC X-session screen. Also note that while a remote user is connected thru VNC, no other connection will be accepted. An idle VNC client will be disconnected after one hour, but this can be changed by using the "-IdleTimeout" option in the server_args line in /etc/xinetd.d/Xvnc. For example, you can add "-IdleTimeout 300" to change it to 5 minutes.

---

### Post by dhalexos on 2006-06-21
I tried to do the folowing step but i still got the dependencies probleme.
I have a i386 system.

[QUOTE=p_alexander]
1. Enable XDMCP

[COLOR="Red"]Note: I had to also change another part of the gdm.conf file. Also, a restart was required so gdm could read the new configuration.[/COLOR]

Look for the following piece of text in /etc/gdm/gdm.conf
[html]
[xdmcp]
# Distributions: Ship with this off.  It is never a safe thing to leave out on
# the net.  Setting up /etc/hosts.allow and /etc/hosts.deny to only allow local
# access is another alternative but not the safest.  Firewalling port 177 is
# the safest if you wish to have xdmcp on.  Read the manual for more notes on
# the security of XDMCP.
Enable=false
[/html]
Change the Enable=false to Enable=true
[/QUOTE]

I hope somebody can help me.

---

### Post by halitech on 2006-06-21
I got this working fine on 1 system but I'm having trouble with a second system. the other system is running xubuntu on an AMD 350 with 64 meg of ram and a 2gig drive. I'm sure most of you can see where this is going already but I have an added twist. The serial port (yes, it's an old socket 7 board with no ps/2 mouse port) is either dead or the mouse I am using is dead. so, as I have no mouse, I can not use the option of going system-prefs-etc to enable the log ins and I also don't have the room to install gnome so I can't edit the gdm/gdm.conf file to allow them either. I do have xfce installed but without a mouse, kinda at a standstill. I can log in with ssh and I even tried webmin which doesn't seem to give me the option to set what I think I need to change either. I know there has to be a way to do this rfom the CLI but I'll be a smurf if I can figure it out :( some one please help me out

---

### Post by halitech on 2006-06-21
ok, I'm not sure but I seemed to have missed this thread [Dapper Server GUI]("http://ubuntuforums.org/showthread.php?t=194283") so rebooting the server now to see if it works *crosses fingers*

---

### Post by halitech on 2006-06-21
gah, still same thing, I get the grey screen and a big ugly x, must have missed something. 

If I have xfce installed and not gnome, when it asks which to load, gdm or xdm, should I pick xdm or gdm? I think I picked gdm. would that matter as long as gdm was installed?

---

### Post by JackandJohn on 2006-06-24
[QUOTE=halitech]gah, still same thing, I get the grey screen and a big ugly x, must have missed something. 

If I have xfce installed and not gnome, when it asks which to load, gdm or xdm, should I pick xdm or gdm? I think I picked gdm. would that matter as long as gdm was installed?[/QUOTE]

One thing for XFCE:
You may have to change it to 'startxfce' instead. (this loads xfce in the screen instead of gnome/kde, etc)
I found this out when I was doing the same thing, but through FreeNX

---

### Post by halitech on 2006-06-24
well, guess my problem is actually dead serial ports on the board so gonna have to get a usb mouse this week and hope my usb card works.

---

### Post by closeyourwindows on 2006-06-25
how would one access this from a remote computer:  
would this be vncviewer <ip address> 
and what about a router, is there a port that needs to be added in the command line?

---

### Post by halitech on 2006-06-25
I've been using 

vncviewer <IP ADDRESS:1>

for the router, I believe you would need to open port 5900

---

### Post by deuce868 on 2006-07-02
Any ideas why the authentication wouldn't work? I get a password prompt when using the 
vncviewer localhost:1 

It will not accept the password though. I have checked that the password file exists. I even tried adding +r to the file just in case. I've rerun the command a few times to see if I might have mistyped the password, but no go. 

edit: nvm...stupid me named the password file vncpassword (no 'or' in the example)

---

### Post by BiggerBadderBen on 2006-07-04
Does anybody know how to change the system settings ("Same as local", etc.) without X?  I only have SSH access to my server and am getting the grey background without X.

---

### Post by Daiver on 2006-07-05
I have a question.

I only seem to be able to access IP:1.  When I try to use IP:0 it says "connection refused".

The machine is already logged into a GNOME desktop, so I should be able to access it, but I can't.

Can anyone help me?

---

### Post by anti-net on 2006-07-09
I'm having the same problem with the big gray X :( If i find out what i did wrong i'll post. but if anyone knows please let me know!

---

### Post by djmadkins on 2006-07-09
For those with the grey screen and the x, I had the exact same thing wrong..

The fix? check to make sure that you have ONLY the software installed (related to VNC) that is described on the first page of this post.. Somewhere along the way I had another version of VNC installed..

What I did specifically was remove ALL vnc related software completely, restart, then follow the instructions again.

Hope this helps.

---

### Post by WillyTP on 2006-07-10
On AMD64, I've been able to make vnc + xinetd working without problems, using ubuntu's dapper original packages:

vnc4server 4.1.1+xorg1.0.2-0ubuntu1 
vnc4-common 4.1.1+xorg1.0.2-0ubuntu1
xvnc4viewer 4.1.1+xorg1.0.2-0ubuntu1

However, only with GDM works. With KDM, I get the infamous grey screen. I modified the /etc/kde3/kdm/kdmrc to enable XDMCP and /etc/kde3/kdm/Xaccess to enable all hosts... but nothing. KDM doesn't spawn. Since on another PC with Kubuntu Dapper x86 even KDM works, I think this is a bug of KDM for amd64.

---

### Post by krazykirk on 2006-07-10
hmm... it's not quite working for me...

```

kirk@kirk-desktop:~$ vncviewer localhost:1 VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05 Copyright (C) 2002-2003 RealVNC Ltd. Copyright (C) 1994-2000 AT&T Laboratories Cambridge. See http://www.realvnc.com for information on VNC. ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104) 
```


thats what happens when i try to test it.

Anyone know a solution?

---

### Post by WillyTP on 2006-07-11
I solved the problem with KDM!
In /etc/kde3/kdm/kdmrc, I uncommented the line
```
#SourceAddress=true
```
to
```
SourceAddress=true
```
and now finally KDM works! :D

---

### Post by UbuntuniX on 2006-07-11
On this topic,
is there any way to secure your VNC to stop people from hijacking your computer over the web?

If not I recommend you stick with SSH ;)

---

### Post by mssever on 2006-07-14
I keep getting the following error when trying to use VNC:
```
$ vncviewer scott-desktop:1
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
```
I get the same error when I connect from the machine itself using vncviewer localhost:1. As far as I can tell, I've followed the instructions exactly.

Here's my /etc/xinetd.d/Xvnc:
```
service Xvnc {
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

Any ideas?

EDIT: I don't know if this is relavant, but I am able to connect using XDMCP.

---

### Post by timbobsteve on 2006-07-18
Hi All,

I have followed this tutorial and a similar one on the gentoo forums (HOWOT - Xvnc Terminal Server) but I have one question.

I can connect to a machine fine through VNC, but I am unable to connect multiple machines to my VNC server e.g.:

1 machine can connect to the vnc-800x600x16 service
1 machine can connect to the vnc-1024x768-16 service

but 2 machines cannot connect to the same service (say both connect at 800x600x16)

I would like to know if this is possible to get happening as it would be most beneficial and a good step toward a permanent Terminal Server replacement.

Thanks for any help you can provide.

---

### Post by timbobsteve on 2006-07-19
I have fixed the problem. The key is to not specify a screen to use in the server args for /etc/xinetd.d/Xvnc file.

Instead of using these server args:


```
...
server_args = -inetd :1 -query localhost -geometry 800x600 -depth 16 -fp /usr/share/X11/fonts/misc -once
...
```

I used

```
...
server_args = -inetd -query localhost -geometry 800x600 -depth 16 -once
...
```

Now I can have as many sessions of each configurating as I want. I found using VNC in this manner is more productive and easy to setup that FreeNX, but that is just my opinion.

---

### Post by kirschey on 2006-08-03
> **sirspiddy said:**
> 
System->Administration->Login Window
Click on Remote Tab
Changed style to "Same as Local"
Click on the "Configure XDMCP..." buton
Uncheck "Honor indirect request"
Click Close on both windows

reboot


I am using 6.06 with the gnome desktop on the server LAMP build.   Where exactly is the Configure XDMCP button I don't see it where you said?

I type "vncviewer localhost:1"
And I get the error "ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer(104)"

---

### Post by zhenya on 2006-08-04
I have followed this tutorial exactly, however I'm trying to connect remotely over SSH.  After I start my ssh session, I start the VNC viewer on localhost:1 but I get the error:
  Connection failed - Error reading Protocol Version

  Possible causes:
  
  - You've forgotten to select a DSMPlugin and the Server uses a DSMPlugin
  - Viewer and Server are not compatible (they use different RFB protocols)
  - Bad Connection

This setup had been working with vino-server, but the connection was so slow that it wasn't really usable, even at very low color depths.  Now I get this error no matter what.  Anyone have any thoughts?

Thanks!

---

### Post by gurgle on 2006-08-31
weird - the post #18 i was using. everything was a-ok, and now I get a grey screen when I authticate. 

Its a grey screen with a black X as the mouse cursor. I tried installing kubuntu-desktop, could this be the problem?

---

### Post by funchords on 2006-09-08
(In reply to the top post in this thread...)

The code in Step 5 should be:

```

sudo /etc/init.d/xinetd stop ;  sudo killall Xvnc ; sudo /etc/init.d/xinetd start

```

---

### Post by funchords on 2006-09-08
(In reply to the top post in this thread...)

The contents of the new file in step 4 should be

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

---

### Post by funchords on 2006-09-09
> **L4mp said:**
> 
1. Enable XDMCP

```
sudo gedit /etc/gdm/gdm.conf

```

then find this rule:
# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
# RemoteGreeter=/usr/lib/gdm/gdmlogin

remove the '#' in the last line so there should be:

# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
   RemoteGreeter=/usr/lib/gdm/gdmlogin


1.  You don't need to uncomment this line.  The lines with the comment marks are the default settings.

2.  You should not edit gdm.conf, you should edit gdm.conf-custom.  When gdm is updated, changes in gdm.conf will be overwritten.  Changes in gdm.conf-custom will not.

My re-write of step 1 would be:

1. Enable XDMCP and local connections

```
sudo gedit /etc/gdm/gdm.conf-custom

```

Toward the end of this file, you'll find these empty sections:

```

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]

```

Add two lines:
Under [security], add the line: DisallowTCP=false
Under [xdmcp], add the line: Enable=true

The end of the gdm.conf-custom file now reads as follows:

```

[daemon]

[security]
DisallowTCP=false
[xdmcp]
Enable=true
[gui]

[greeter]

[chooser]

[debug]

[servers]

```

---

### Post by funchords on 2006-09-09
> **zhenya said:**
> I have followed this tutorial exactly, however I'm trying to connect remotely over SSH.  After I start my ssh session, I start the VNC viewer on localhost:1 but I get the error:
  Connection failed - Error reading Protocol Version

  Possible causes:
  
  - You've forgotten to select a DSMPlugin and the Server uses a DSMPlugin
  - Viewer and Server are not compatible (they use different RFB protocols)
  - Bad Connection

This setup had been working with vino-server, but the connection was so slow that it wasn't really usable, even at very low color depths.  Now I get this error no matter what.  Anyone have any thoughts?

Thanks!Because you are using SSH (good for you!), connection attempts over an SSH tunnel appear to be coming from localhost.  This needs to be enabled in gdm.  It is not enabled by default.

To enable local connections:

```
sudo gedit /etc/gdm/gdm.conf-custom

```

Toward the end of this file, you'll find these empty sections:

```

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]

```

Add two lines:
Under [security], add the line: DisallowTCP=false
Under [xdmcp], add the line: Enable=true

The end of the gdm.conf-custom file now reads as follows:

```

[daemon]

[security]
DisallowTCP=false
[xdmcp]
Enable=true
[gui]

[greeter]

[chooser]

[debug]

[servers]

```

After saving these changes, reboot the system (easier) or restart X and Xvnc.

---

### Post by john.steer on 2006-09-15
I have set this up and its working well apart from occasionally getting locked out.

If I am running the vnc session across the internet occasionally I will get disconnected from the session. If I try to reconnect it asks me for the session password again but it doesnt recognise the password that I used to start the session initially. 

Any clues on what might be happening?

And No I'm not mistyping the password :)

---

### Post by DarkKoopa on 2006-09-25
> **zhenya said:**
> I have followed this tutorial exactly, however I'm trying to connect remotely over SSH.  After I start my ssh session, I start the VNC viewer on localhost:1 but I get the error:
  Connection failed - Error reading Protocol Version

  Possible causes:
  
  - You've forgotten to select a DSMPlugin and the Server uses a DSMPlugin
  - Viewer and Server are not compatible (they use different RFB protocols)
  - Bad Connection

This setup had been working with vino-server, but the connection was so slow that it wasn't really usable, even at very low color depths.  Now I get this error no matter what.  Anyone have any thoughts?

Thanks!


Did you ever get this going?

I'm using vino ATM like you where and my god is frustratingly slow.

I want to know if you got it going over SSH (I too can use vino VNC over SSH with Windows PuTTY), so I have someone to reference to before this n00b kills his linux box :biggrin:

---

### Post by Witty Name on 2006-09-25
Did we ever conclusively arrive at the only plausible reason for VNC now being broken is the flawed kernel / graphics packages?

Also long term support my arse, I am turning off my adept notifier as we speak... there. **** it.

---

### Post by marost on 2006-11-15
:confused: How do you create some kind of file which you can run to switch this vnc server on and off? I think it's important not to have it running all the time. I guess I need to stop my ssh server too while I'm at it. Anyone know how to do this? :confused: 

Thank you kindly.

---

### Post by haunter on 2006-12-03
Hi. I'm fairly new to *nix and I can't seem to get vnc going.
```

haunted@haunted-server:~$ vncviewer localhost:1

VNC Viewer Free Edition 4.1.2 for X - built May 12 2006 17:42:13
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Sun Dec  3 15:14:26 2006
 CConn:       connected to host localhost port 5901


```


That is all im getting atm :< 

Does anyone know what i may be doing wrong?

---

### Post by FRAMBO on 2006-12-20
Re Post#50

I'm getting the same message from the  command ```
vncviewer localhost:1

```  Vncviewer connects but nothing appears to happen graphical.  The terminal just stays static.  

Bit of an experienced Kubuntu & Ubuntu user but I'm still out of my element as I've spent 2 days on this problem.  ](*,) 

The vnc server is xubuntu desktop 6.10 with a static IP on a static network.  

I've followed the various tutorials on the forums here but no dice.  

When trying to connect from WinXP via UltraVNC on port 5901 I receive a message "Connecting..." which seems to never time out.    When I have used the default UltraVNC port my connection is flatly refused so I know the 2 machines can connect to each other.  

In addition when I install Samba server on the xubuntu box I can view the files from a Winxp client via the windows network.       

I'm certain I'm missing something to prevent the vnc clients from opening up once connected.  :???: 

Suggestions?

---

### Post by FRAMBO on 2006-12-20
When I manually listen on the xubuntu server I receive the following when connecting from WinXP Ultra VNC:

```
VNC Viewer Free Edition 4.1.1 for X - built May 29 2006 12:45:36
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Wed Dec 20 09:58:40 2006
 main:        Listening on port 5500


Wed Dec 20 09:58:57 2006
 CConn:       Accepted connection from 19*.***.**.**::1155

```

I do not receive a GUI on the Winxp side...

---

### Post by FRAMBO on 2006-12-20
Finally relief!  I was thinking too much like a windows user.  Did not understand the sessions thing.  

For xubuntu logging into a active session I dumped all the vnc packages except **vnc common** (needed for passwords setup) and **x11vnc.**  Disabled remote login via the window login dialog.  

This how to explains what is needed and how to do it: [http://www.ubuntuforums.org/showthread.php?t=45565&highlight=x11vnc](http://www.ubuntuforums.org/showthread.php?t=45565&highlight=x11vnc)  

The autocusel section is a litle out of date but I'm running without it.

---

### Post by maxnutter on 2007-02-04
I'm having big problems; running on Xubuntu 6.10 x64, everything seems to be installed ok, but when I try to connect via vnc (UltraVnc, TightVnc) it asks for a password, which works ok and then the client starts up saying something about starting the initial screen, but the desktop does not appear and the client eventually closes. Unfortunately, this also closes/crashes the desktop on the server and I have to reboot.

To make things more complicated, I don't have easy connection to a monitor on the remote box, so I'm admining it via webmin.

Seriously scratching my head here, so any help appreciated!

---

### Post by mrsteveman1 on 2007-02-10
maxnutter, i think you might be having a problem with the vnc package, there was a 64bit bug in the one thats included in the repo, and theres a fix for it now i think on the start of this thread somewhere. Other than that, there's nothing i can think of that would cause the kernel to panic and reboot, if thats what is happening.

Your best option might be to try and install vino which is what gnome uses for desktop sharing, then you can enable autologin on the x session (otherwise someone has to login at a screen first or it doesn't start), then you still have the vnc password for security. This would let you login with VNC securely and easily, without all the extra config a 2nd vnc screen requires.

It should be possible to install vino for any window manager, though its integrated in gnome by default.

Im not familiar with the way the display manager handles things in Xfce but ill post what i did in gnome, some of it is universal but hopefully the rest is similar, i also have remote desktop sharing in gnome on screen 0:0, so keep that in mind when i talk about :0 and :1

> 
install vnc4server (32bit machine)

install xinetd and make sure its default config is empty except for the include at the end 

copy the correctly formatted (vertical list) xinetd config entry for Xvnc into /etc/xinetd.d/Xvnc, its listed on the first page of this thread.

Then i went into the  "System > Administration > Login Window"  item in gnome, to the remote tab and selected "Same As Local" in the top item. I also went into the gdm config file /etc/gdm/gdm.conf and made sure that "RemoteGreeter=/usr/lib/gdm/gdmlogin" was not commented out. This is gdm specific but there should be an equivalent for xfce, possibly you could use gdm to start xfce as well if needed.

Theres also a section in the gdm.conf file 

"[xdmcp] 
Enable=False" 

under my setup the new screen still works so im not sure what enabling that would do. Its possible gdm is handling logins somewhere else regardless of this file, if you do enable that option make sure its behind a firewall like the file says, you DON'T need port 177 open for vnc to work, vnc connects locally to the xserver, so you don't need anything but the vnc port open on a firewall.





You should probably connect your client to the server with the ip:screen syntax instead of specifying the port, because if you specify a port it defaults to the :0 screen which is wrong, we want it to say, for instance in my case 192.168.1.2:1 , and the right tcp/ip port is used by default.


Use a client that is on the same LAN subnet for testing to remove possible firewall issues until it works, this will help isolate the problem.

---

### Post by richteel on 2007-02-21
> **john.steer said:**
> I have set this up and its working well apart from occasionally getting locked out.

If I am running the vnc session across the internet occasionally I will get disconnected from the session. If I try to reconnect it asks me for the session password again but it doesnt recognise the password that I used to start the session initially. 

Any clues on what might be happening?

And No I'm not mistyping the password :)

Did you ever find a solution to this issue?  I am having the same problem an wish to resolve it as soon as possible.

---

### Post by zupidupi on 2007-02-26
Hiya,

I'm fighting with the vnc as well. I have a a standard Ubuntu (Edgy) installation on a server, to which I want to set up a vnc-connection from a client running a live-cd bootup. 

I've followed the step-by-step-guide at 

[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

rather closely.

I have no problem connecting when both are running Gnome. I issue the command "vncviewer 192.168.1.102:1" from a terminal on the client, enter the vnc-password, and I get a login-window which works A-OK.

The problem arises when I try to open a connection *with the server in console mode*. I remove  the gdm-link in the rc2.d-directory, start up the server again. When I try to connect again I get to enter the vnc-password, but then I get nothing but a grey screen.

It seems to me that I'm missing something. I read in another thread that it wouldn't be necessary to run a x-session on the server in order to get a GUI with vnc ([http://www.linuxquestions.org/questions/showthread.php?t=523864](http://www.linuxquestions.org/questions/showthread.php?t=523864), post #7) but I obviously need to do something else - fiddle with some settings, run some other daemon/program - you tell me!

Any help for solving this would be much appreciated!

Thx in advance,

   Mike

---

### Post by Jose Catre-Vandis on 2007-02-26
> **zupidupi said:**
> Hiya,

I'm fighting with the vnc as well. I have a a standard Ubuntu (Edgy) installation on a server, to which I want to set up a vnc-connection from a client running a live-cd bootup. 

I've followed the step-by-step-guide at 

[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

rather closely.

I have no problem connecting when both are running Gnome. I issue the command "vncviewer 192.168.1.102:1" from a terminal on the client, enter the vnc-password, and I get a login-window which works A-OK.

The problem arises when I try to open a connection *with the server in console mode*. I remove  the gdm-link in the rc2.d-directory, start up the server again. When I try to connect again I get to enter the vnc-password, but then I get nothing but a grey screen.

It seems to me that I'm missing something. I read in another thread that it wouldn't be necessary to run a x-session on the server in order to get a GUI with vnc ([http://www.linuxquestions.org/questions/showthread.php?t=523864](http://www.linuxquestions.org/questions/showthread.php?t=523864), post #7) but I obviously need to do something else - fiddle with some settings, run some other daemon/program - you tell me!

Any help for solving this would be much appreciated!

Thx in advance,

   Mike

You are probably better off using ssh to connect when your server is in console mode. Install openssh-server on the "server", and then you should be able to log into your server from a remote machine with the following syntax:
```
 ssh username@ipofserver
```
 to take things further, you can also use "screen" once you are logged in, to run multiple terminals on your remote server that will stay open once you logout. Research screen (in the repos) and on the forum for how it works. 
You can use putty to access via ssh from a windows box

---

### Post by Jose Catre-Vandis on 2007-02-26
> **L4mp said:**
> Set up VNC server with resumable sessions on dapper (6.06) 


1. Enable XDMCP

```
sudo gedit /etc/gdm/gdm.conf

```

then find this rule:
# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
# RemoteGreeter=/usr/lib/gdm/gdmlogin

remove the '#' in the last line so there should be:

# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
   RemoteGreeter=/usr/lib/gdm/gdmlogin


Note: Before doing the next step, you need to make sure the extra repositories (e.g. universe) are enabled:
[http://easylinux.info/wiki/Ubuntu#Ho...a_repositories](http://easylinux.info/wiki/Ubuntu#Ho...a_repositories)

2. Install required packages (vncserver and xinetd)

Code:
```

sudo apt-get install vnc4server xinetd
```


Note to AMD64 users: The current version of vnc4server in the repositories has a bug, so you need to download and install the fixed vnc4 packages as shown below:

Code:

```
wget http://qt1.iq.usp.br/download/vnc4server_4.0-7.3_amd64.deb wget http://qt1.iq.usp.br/download/xvnc4viewer_4.0-7.3_amd64.deb sudo dpkg -i vnc4server_4.0-7.3_amd64.deb sudo dpkg -i xvnc4viewer_4.0-7.3_amd64.deb
```



3. Set the VNC passwd
Code:

```
sudo vncpasswd /root/.vncpasswd
```


4. Add vnc service to xinetd:
Code:
```

sudo gedit /etc/xinetd.d/Xvnc

```

Enter this into the new file:

Code:
```

service Xvnc { type = UNLISTED disable = no socket_type = stream protocol = tcp wait = yes user = root server = /usr/bin/Xvnc server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd port = 5901 }

```

5. Restart xinetd (usually there is no need to reboot, but occasionally it might be required)

Code:```


sudo /etc/init.d/xinetd stop sudo killall Xvnc sudo /etc/init.d/xinetd start
```


6. That's it! To test that this is working first try to connect from the same machine (the machine we just set up the VNC server on):

Code:
```

vncviewer localhost:1

```

You should be prompted for the VNC password, and then see the GDM login screen where you can login and start a new X session. If that works, you can now go ahead and try to connect from remote machine using your favorite VNC client (remember to first close the local vncviewer we started above). Remember to use the VNC server machine's domain name or IP address, followed by :1 (e.g. 192.168.0.100:1). If connecting locally as shown above works, but connecting remotely fails, then this means you have a problem with a firewall which is blocking some ports. See the notes below about how to deal with that.

Note about ports: The VNC server set up as shown uses TCP port 5901. If you are using firewall software (e.g. firestarter) on that machine, you need to allow incoming connections on this port. If you are using a router which assigns your machine a private address (e.g. 192.168.0.100) which is not accessible from the internet, then you need to forward TCP port 5901 from the router to this machine.

Note about security: This setup allows any user to start an X-session remotely by logging in using his regular password (after starting the VNC connection using the VNC password), so if the user disconnects without logging out, any other user which knows the VNC password can connect afterwards and resume the same session that the first user started. So if you do not want to log out before disconnecting, it's advisable to at least lock your VNC X-session screen. Also note that while a remote user is connected thru VNC, no other connection will be accepted. An idle VNC client will be disconnected after one hour, but this can be changed by using the "-IdleTimeout" option in the server_args line in /etc/xinetd.d/Xvnc. For example, you can add "-IdleTimeout 300" to change it to 5 minutes.




ps. This was copy/pasted from a few posts made by Tichondrius and elemental666. I simply putted them together and tested everything! It works here for me now.

If questions just post :)

I can't get the java viewer to work using this method. I have vnc-java installed, but just get a white browser window with "RFB 003.008" in it. How to connect vnc-java to Xvnc?

---

### Post by zupidupi on 2007-02-27
Hiya,

> **Jose Catre-Vandis said:**
> You are probably better off using ssh to connect when your server is in console mode. Install openssh-server on the "server", and then you should be able to log into your server from a remote machine with the following syntax:
```
 ssh username@ipofserver
```
 to take things further, you can also use "screen" once you are logged in, to run multiple terminals on your remote server that will stay open once you logout. Research screen (in the repos) and on the forum for how it works. 
You can use putty to access via ssh from a windows box

Thx for your reply, I'll look into the "screen"-command. I've (naturally) ssh:d into the server on previous occasions. But, I'm still interested in opening the graphical connection - for many different reasons, among which you'll find curiosity and a will to explore!

Cheerio,

   Mike

---

### Post by KrIaXPaTaLa on 2007-03-14
> **Jose Catre-Vandis said:**
> I can't get the java viewer to work using this method. I have vnc-java installed, but just get a white browser window with "RFB 003.008" in it. How to connect vnc-java to Xvnc?

Would like to access trough web browser as well, on port 80. Any thoughts?

Regards,

KrIaX, Portugal

---

### Post by doobydave on 2007-03-21
I have been trying this. It seems to work flawlessly on dapper but on edgy there seems to be some issues.

I've found this how-to (which works), [http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)
but it uses a slightly older version of vnc4server so that may not be the best thing to do.

However on launchpad, [https://launchpad.net/ubuntu/edgy/+source/vnc4/+bug/3593](https://launchpad.net/ubuntu/edgy/+source/vnc4/+bug/3593)
there was a fix to create a symbolic link to the correct fonts directory

sudo ln -s /usr/share/fonts/X11 /usr/share/X11/fonts

I tried this and it worked, but only till i rebooted. I now get a different error message :-

$ vncviewer localhost:1
VNC viewer version 3.3.7 - built Jul  4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.8 (viewer 3.3)
Password: 
ReadFromRFBServer: rdr::EndOfStream

Anyway to fix this?

---

### Post by eagle63 on 2007-03-31
Quick question:  Can xinetd be installed/used with other VNC servers (other than vnc4server) and still work?  I've got tightVNC server working great on my Dapper box, and I'd love to add the ability to have resumable sessions, but I'd like to know if I have to uninstall tightVNC first or if I can keep it in place and just add xinetd.  Thanks!

---

### Post by gert cuykens on 2007-04-03
> **doobydave said:**
> 
$ vncviewer localhost:1
VNC viewer version 3.3.7 - built Jul  4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.8 (viewer 3.3)
Password: 
ReadFromRFBServer: rdr::EndOfStream

I am having the excat same problem i was wondering about the protocol output ?
"protocol version 3.8 (viewer 3.3)"

---

### Post by gert cuykens on 2007-04-03
This works for me

> I had the "ReadFromRFBSServer: rdr::EndOfStream" error message. Removing "-query localhost" from the server_args line in /etc/xinetd.d/Xvnc file solved this problem.


I now have a black white dotted X screen, coming close to make it work i think :)

---

### Post by doobydave on 2007-04-03
@gert

Let us know if that has totally fixed it.

Cheers.

---

### Post by bsdchopper on 2007-04-03
i can start vncviewer correctly but when i do so i see dozens of windows (such a ugly word, i know) showing my desktop so i can't do anything but closing vncviewer.

anyone knows how to fix this problem?

---

### Post by gurgle on 2007-04-05
> **gert cuykens said:**
> This works for me



I now have a black white dotted X screen, coming close to make it work i think :)

i get the same thing. anyone figured out why yet?

---

### Post by bsdchopper on 2007-04-06
now i'm in the same situation too!

---

### Post by ilovebsod on 2007-04-24
anyone get this working?  I'm getting the 

ReadFromRFBServer: rdr::EndOfStream

error as well.


read through a lot of posts on many forums and no real solution?

---

### Post by fiskpinnen on 2007-04-25
After spending to much time on this solution and getting constant problems I gave up and went back to my old way which works perfect unless you crave logging in to a separate desktops at the same time. Just wanted to post it here since it may suit others as well. The trick is to ditch vnc4server and opt for x11vnc, and as I said, works great. Works from the gdm login prompt and on.

1. Disable Desktop Sharing under System -> Preferences -> Remote Desktop
2. sudo apt-get install x11vnc
3. sudo x11vnc -storepasswd yourpasswordhere /etc/x11vnc.pass
4. sudo gedit /etc/X11/gdm/Init/Default
5. add this line to the bottom above exit:  /usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900
6. sudo gedit /etc/X11/gdm/gdm.conf-custom and add "KillInitClients=false" under section [daemon] so you don&#8217;t get your session killed after you log in (without the "")
7. restart

Happy vnc'ing for you!

---

### Post by nameuser909 on 2007-06-19
just a thought: the annoying gray screen stuff that comes up, this might not help with the resumable session stuff, but i usually just run vnc4server from ssh when i want vnc instead.

the gray screen stuff is from your home folder/.vnc/xstartup file:

xsetroot -solid grey <--------
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
twm &

if you dont want to enable xdmcp and all that you could just change this file to:
#xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
gdm &
# or kdm if your in kubuntu

if you dont have a .vnc folder in your /root accounts folder and vnc is being run as root then i'd just copy it over there eg with 
sudo cp -r ~/.vnc /root
or graphically in kde
kdesu konqueror 
or graphically in gnome (i think)
gksu nautilus

---

### Post by nameuser909 on 2007-06-19
made  a mistake in the last post, its not 
gdm &
or 
kdm & # for kubuntu

its 
gnome-session &
startkde &

---

### Post by jdbg on 2007-06-26
> **fiskpinnen said:**
> After spending to much time on this solution and getting constant problems I gave up and went back to my old way which works perfect unless you crave logging in to a separate desktops at the same time. Just wanted to post it here since it may suit others as well. The trick is to ditch vnc4server and opt for x11vnc, and as I said, works great. Works from the gdm login prompt and on.

1. Disable Desktop Sharing under System -> Preferences -> Remote Desktop
2. sudo apt-get install x11vnc
3. sudo x11vnc -storepasswd yourpasswordhere /etc/x11vnc.pass
4. sudo gedit /etc/X11/gdm/Init/Default
5. add this line to the bottom above exit:  /usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900
6. sudo gedit /etc/X11/gdm/gdm.conf-custom and add "KillInitClients=false" under section [daemon] so you don’t get your session killed after you log in (without the "")
7. restart

Happy vnc'ing for you!

great! that solved almost a one-week long search of mine for a solution to my vnc problem.
many thanks!

---

### Post by rickwookie on 2007-08-07
> **fiskpinnen said:**
> After spending to much time on this solution and getting constant problems I gave up and went back to my old way which works perfect unless you crave logging in to a separate desktops at the same time. Just wanted to post it here since it may suit others as well. The trick is to ditch vnc4server and opt for x11vnc, and as I said, works great. Works from the gdm login prompt and on.

1. Disable Desktop Sharing under System -> Preferences -> Remote Desktop
2. sudo apt-get install x11vnc
3. sudo x11vnc -storepasswd yourpasswordhere /etc/x11vnc.pass
4. sudo gedit /etc/X11/gdm/Init/Default
5. add this line to the bottom above exit:  /usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900
6. sudo gedit /etc/X11/gdm/gdm.conf-custom and add "KillInitClients=false" under section [daemon] so you don’t get your session killed after you log in (without the "")
7. restart

Happy vnc'ing for you!

I've added KillInitClients=false under [daemon] in gdm.conf-custom, but the session is still being killed when I log on. I'm using Feisty (7.04), any ideas?

---

### Post by ToeKnee on 2007-08-09
Ok, I'm stuck here and need some help...  I am fairly new to linux in general.  I've read through every post related to vnc I can find, and tried about everything I've come across, but I still can not get this to work right and start on it's own.

I've running feisty with vnc4server installed.  Vnc works perfectly If I manually start xinetd with "sudo /etc/init.d/xinetd start".  However I can not get it to start on it's own after a reboot.  This is a remote machine, and I won't be physically near it to be able to start it everytime I want to log into it.  

It seems either xinetd is not running on it's own at boot up, or something is failing during boot that keeps it from working correctly that I'm not finding.  If someone can point me to a related thread that I haven't come across, or point me in the right direction I'd really appreciate it!  :)

---

### Post by pdundas on 2007-08-20
OK - I'm suffering from a couple of the problems above (on Feisty Fawn / 7.04).

**grey screen - no gnome, dm log in **

When I got everything set up initially, I connected with "vncviewer localhost:1", gave the password, and got the grey dotted screen with cursor. Same result from a remote box.  

*It looks to me like just plain X with no RemoteGreeter, no window manager, or anything. But the greeter is where it says it should be in the conf file - maybe the problem was that I put it in the /etc/gdm/gdm.conf (which gets overwritten or is naughty, or something), rather than in the officially approved /etc/gdm/gdm.conf-custom (at least on feisty it is).*

Suggestions very welcome (and explanation of why even more so).

But I can't test that because of the next problem...

**RFB read error on login**

Anyway, when I rebooted, I started the vncviewer, and now get the following error (after I give password):

```
$ vncviewer localhost:1
VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
VNC server supports protocol version 3.8 (viewer 3.3)
Password: 
**ReadFromRFBServer: rdr::EndOfStream**
```
(It doesn't work from a remote machine either "connection closed" after password)

So I can't try the other suggestions to see if they start the greeter.

What causes this error (I know that the software WAS working before the reboot, so it's presumably some bit of config that has got lost on reboot, rather than a version conflict or anything)?


As I said above - any help or explanation very welcome...

---

### Post by pdundas on 2007-08-20
Fixed the stream error problem.

Doh! I thought I'd tried the fix mentioned on previous page, but evidently not. Removing [FONT="Courier New"][COLOR="DarkGreen"]-query localhost[/COLOR][/FONT] from /etc/inetd.d/Xvnc (and provoking a reload with [FONT="Courier New"][COLOR="DarkRed"]kill -SIGHUP[/COLOR][/FONT] on the xinetd daemon process) worked. 

Not sure why - is the "query" option one that only makes sense in a nowait/multithreaded mode operation, where new servers are fired off for each connection attempt? Must investigate...

---

### Post by irvin on 2007-08-21
Hi

I've the same problem with the x11vnc server.
I installed a new feisty with updates and then openssh-server and x11vnc. after this I edited the stuff as mentioned here.
I get one access to the login screen but after this it will be closed, I never see the desktop.

And then: this error:

ReadFromRFBServer: rdr::EndOfStream

or

channel 3 open failed...

I used to different logins

vncviewer -via user@host localhost:0

or

ssh -N -L 5900:localhost:5900 user@host
and
vncviewer localhost:0

I tried 2 new feisty installations on different pc's and it didn't work, but last week I did this installation on another feisty on a different pc and it worked.
I checked all the edited files and there are the same. What's the problem, any other ideas ? I tried now about 20 hours and I can't believe it.
But as I see, I'm not alone ;-)
Thanx

---

### Post by pdundas on 2007-08-21
I think it's working now.

I rooted around (and read the vnc4server bug thread, [over here]("https://launchpad.net/ubuntu/+source/vnc4/+bug/78282")) and made some more changes to the Xvnc service definition in [FONT=Courier New]/etc/xinetd.d/Xvnc[/FONT]. This then worked, with an actual login screen and all.
[LIST]
[*]fixed the font path - it should be [FONT=Courier New]/[COLOR=darkred]usr/share[COLOR=red]/fonts/X11/[/COLOR]misc[/COLOR][/FONT] (parts were reversed).
[*]added [FONT=Courier New][COLOR=darkred]-query localhost[/COLOR][/FONT] back in.
[*]tried then rejected suggestion to remove "-once"  (though it make no difference for first log on, when I didn't use it, and logged out, I was stuck with a still running Xvnc session with no new login prompt).
[*]added [FONT="Courier New"][COLOR="DarkRed"]-extension FIXES[/COLOR][/FONT][/LIST][SIZE=1](I found it helpful to add a few versions of the service to the Xvnc file (Xvnc1, Xvnc2, etc, with different options - especially different ports, so I could try several in a row without restarting xinetd and any running VNC servers.)[/SIZE]

The VNC service description that worked for me was:
```
service Xvnc2
{
   type = UNLISTED
   disable = no
   socket_type = stream
   protocol = tcp
   wait = yes
   user = root
   server = /usr/bin/Xvnc
   server_args = -inetd :2 -query localhost -geometry 1024x768 -depth 16
      -once -fp /usr/share/fonts/X11/misc -DisconnectClients-0 -NeverShared
      passwordFile=/root/.vncpasswd -extension XFIXES
   port = 5902
}
```

Note that the server_args line as far as XFIXES [COLOR="darkred"]must be all on one line[/COLOR], or the service **will not start**.

Note that after editing this xinetd definition, you need to kill any running Xvnc server tasks, and restart xinetd.
```
$ sudo /etc/init.d/xinetd stop
$ sudo killall Xvnc
$ sudo /etc/init.d/xinetd start
```

It was NOT necessary to have run vncserver or vnc4server to create an [FONT="Courier New"]xstartup[/FONT] file to tell it to run gnome or login - that was looked after by editing [FONT="Courier New"][COLOR="darkred"]/etc/gdm/gdm.conf-custom[/COLOR][/FONT] (not [FONT="Courier New"]gdm.conf[/FONT], since you're not supposed to edit that directly, and changes could get lost). The important bit of the file was:

```
[daemon]
RemoteGreeter=/usr/lib/gdm/gdmlogin
AlwaysLoginCurrentSession=false

[security]
DisallowTCP=false

[xdmcp]
Enable=true
HonorIndirect=false

[gui]

[greeter]

[chooser]

[debug]

[servers]
```

There is stuff in here that I don't know what it does - and some of it may not be ideal.

And after editing this, you need to get the server to reload the config.

After all that I got a login screen on vnc, but wasn't able to log on until I set the option to allow multiple X logins for the same user *(system > admin > login window; general tab; unselect "disable multiple logins for single user")*. If you have spare accounts this may not be an issue, and note that some apps (and toolbar thingies) complain if the same user runs them in multiple X sessions.

Not yet sure if this will survive a reboot... *[COLOR="DarkRed"]yes, it did![/COLOR]*

Now to get it working on Dapper and Suse Enterprise...

---

### Post by Elohim on 2007-08-29
[QUOTE=pdundas;3230475]I think it's working now.

....

QUOTE]

Thanks - this helped me out very much!  So for my first post here, I will say Thank You! :)

---

### Post by irvin on 2007-10-28
Hallo

On 7.04, I installed x11vnc which works great !

Now I tried to install it on 7.10 (Gutsy) but there are a few files missing.

There's no file or directory like this:

/etc/X11/gdm/Init/Default
and
/etc/X11/gdm/gdm.conf

Does anyone how to configure x11vnc on Gutsy ?

On 7.04 I made these steps:
- installed openssh-server and x11vnc from synaptic

- sudo x11vnc -storepasswd yourpasswordhere /etc/x11vnc.pass

- sudo gedit /etc/X11/gdm/Init/Default

and this line to the file:

/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900 -xrandr

- sudo gedit /etc/X11/gdm/gdm.conf

now search for this line :

#KillInitClients=true

And change it to this:

KillInitClients=false

Restart your PC

That's it

Thanx
Irvin

---

### Post by erwall on 2007-10-29
> **irvin said:**
> Hallo

On 7.04, I installed x11vnc which works great !

Now I tried to install it on 7.10 (Gutsy) but there are a few files missing.

There's no file or directory like this:

/etc/X11/gdm/Init/Default
and
/etc/X11/gdm/gdm.conf

Does anyone how to configure x11vnc on Gutsy ?

On 7.04 I made these steps:
- installed openssh-server and x11vnc from synaptic

- sudo x11vnc -storepasswd yourpasswordhere /etc/x11vnc.pass

- sudo gedit /etc/X11/gdm/Init/Default

and this line to the file:

/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900 -xrandr

- sudo gedit /etc/X11/gdm/gdm.conf

now search for this line :

#KillInitClients=true

And change it to this:

KillInitClients=false

Restart your PC

That's it

Thanx
Irvin
Here's what worked for me, had to change a couple of things for it to work in Gutsy:

```
sudo aptitude install x11vnc
```

```
sudo x11vnc -storepasswd yourpasswordhere /etc/x11vnc.pass
```

```
sudo chmod 744 /etc/x11vnc.pass
```

```
sudo gedit /etc/gdm/Init/Default
```

add this line to the file above "exit 0":

/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -noxdamage -forever -bg -rfbport 5900

```
sudo gedit /etc/gdm/gdm.conf
```

add the following under the daemon section

```
KillInitClients=false
```

Restart your PC

Post back here if it worked.

---

### Post by irvin on 2007-10-30
Hi

Many thanks, man was I blind to see only the directory changed.
I just made 2 changes to my installation in the path. I didn't made "chmod" and don't use the "-noxdamage" option

Here's what I changed:

Ubuntu 7.04
sudo gedit /etc/X11/gdm/Init/Default

Ubuntu 7.10
sudo gedit /etc/gdm/Init/Default

and

Ubuntu 7.04
/etc/X11/gdm/gdm.conf

Ubuntu 7.10
/etc/gdm/gdm.conf

Also I don't need the "-xrandr" option with 7.10 at the moment.
With 7.04 sometimes it worked for me without -xrandr, but on the last installations it only worked with this option.

Mant thanks again !
Irvin

---

### Post by knoid on 2007-12-03
Hi

I'm running 7.10 Gutsy and I've been trying to set this up as summarised on the grumpymole blog here - [http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html](http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html)

Followed the instructions to a tee but I still get "Connection reset by peer" whether trying to connect locally with xvncviewer or remotely with realvnc on win.

If I stop xinetd and start vnc4server on it's own with the following parameters:

```
sudo vnc4server -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
```

I can connect successfully with any VNC client.

So the problem appears to be something in xinetd.

Looking in syslog (which I wouldn't have thought to do without this post: [http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)) for xinetd events I get the following:

```
Dec  3 09:03:13 Vault xinetd[7172]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Dec  3 09:03:13 Vault xinetd[7172]: Started working: 1 available service
Dec  3 09:03:24 Vault xinetd[7173]: warning: can't get client address: Transport endpoint is not connected
```

Several hundred instances of the "transport endpoint" line follow, then:

```
Dec  3 09:03:24 Vault xinetd[7222]: warning: can't get client address: Transport endpoint is not connected
Dec  3 09:03:24 Vault xinetd[7172]: Deactivating service Xvnc due to excessive incoming connections.  Restarting in 10 seconds.
Dec  3 09:03:34 Vault xinetd[7172]: Activating service Xvnc
Dec  3 09:03:36 Vault xinetd[7223]: warning: can't get client address: Transport endpoint is not connected

```

I'm not what you'd call a Linux expert so any pointers in troubleshooting this would be greatly appreciated - feel free to go into needlessly excessive detail, too :D.

Thanks in advance!

---

### Post by xp_newbie on 2007-12-03
> **L4mp said:**
> I simply putted them together and tested everything! It works here for me now.No you didn't test everything. If you tested everything you wouldn't have written
> sudo /etc/init.d/xinetd stop sudo killall Xvnc sudo /etc/init.d/xinetd start
but rather
```
sudo /etc/init.d/xinetd stop; sudo killall Xvnc; sudo /etc/init.d/xinetd start
```

Also note that with port 5901 that you specified in /etc/xinetd.d/Xvnc, there is no chance for the free version of RealVNC to work. It should be changed back to 5900, just as in the Vino Remote Desktop that comes pre-packaged with Ubuntu.

Also note that that the Vino Remote Desktop needs to be disabled in order not to create contention between your method and Ubuntu's method.

If questions just post :)

---

### Post by wareagle on 2008-02-11
I am able to get copy/paste between the client and the host if I run vncconfig on the server.  Is it possible to run this at startup so I don't have to do this?

---

### Post by Cerin on 2008-05-07
Has anyone gotten this to work with Ubuntu 8? I went through all the setup, but all I get via vncviewer is either the Refuse/Allow prompt or a real old-school grey X screen that doesn't let me login.

---

### Post by Skip Da Shu on 2008-05-09
> **xp_newbie said:**
> 

Also note that with port 5901 that you specified in /etc/xinetd.d/Xvnc, there is no chance for the free version of RealVNC to work. It should be changed back to 5900...

Actually the 5901 can be worked around... from the other resumable sessions thread: [HERE]("http://ubuntuforums.org/showpost.php?p=4906879&postcount=445")

---

### Post by theharlequin on 2008-06-20
> **sirspiddy said:**
> OK, I had the same problem before until I performed the following

System->Administration->Login Window
Click on Remote Tab
Changed style to "Same as Local"
Click on the "Configure XDMCP..." buton
Uncheck "Honor indirect request"
Click Close on both windows

reboot

NOTE:  I have both vncserver and vnc4server on my pc.

Far as the SSH session I typically use openssh or putty on a remote machine
I connect to the ssh server running on the Ubuntu box and create a local mapping
by using a local port address mapped to the IP:VNC Port the Ubuntu box 
Then simply run your vnc client by connecting to "Localhost"LocalPort"

Hope that helps

Is there anyway to do this through a terminal because in Xubuntu my resolution is only 800x600 and the bottom button which I need to select is cut off?

---

### Post by Dj Dutchman on 2008-06-20
Hi, I have set everything up and it works well, well actually it _worked_ well because now when I login (remotely) everything loads except the two bars at the top and bottom (applications, places, etc)???

Anybody that can help? Btw I'm running xubuntu 8.04...

---

### Post by mssever on 2008-06-20
> **Dj Dutchman said:**
> Hi, I have set everything up and it works well, well actually it _worked_ well because now when I login (remotely) everything loads except the two bars at the top and bottom (applications, places, etc)???

Anybody that can help? Btw I'm running xubuntu 8.04...
Have you checked whether your panel is still alive? Or has it crashed or otherwise died? In Gnome, the panel is called gnome-panel. I don't know what it's called in Xfce.

---

### Post by Dj Dutchman on 2008-06-20
Well, if I plug in the monitor to the PC (screen 0) then its there and working fine but in screen 1 (remote) it isn't there. How do I find out if it has 'crashed or otherwise died'?

---

### Post by popie on 2008-06-20
> **Cerin said:**
> Has anyone gotten this to work with Ubuntu 8? I went through all the setup, but all I get via vncviewer is either the Refuse/Allow prompt or a real old-school grey X screen that doesn't let me login.

I posted the step by step instructions that I use for v8.04 on another topic:
[http://ubuntuforums.org/showthread.php?p=5229232#post5229232](http://ubuntuforums.org/showthread.php?p=5229232#post5229232)

(post 458 in that thread)

---

### Post by mssever on 2008-06-20
> **Dj Dutchman said:**
> Well, if I plug in the monitor to the PC (screen 0) then its there and working fine but in screen 1 (remote) it isn't there. How do I find out if it has 'crashed or otherwise died'?
Use htop to look through the list of processes and see if the panel is running. Hit u to filter by username. If you need to know what the panel is called, then examine htop's output when the panel is running.

Also, have you verified that you don't have a screen size mismatch where the remote screen is simply large enough that the panel disappears?

---

### Post by Dj Dutchman on 2008-06-21
Like I said it worked, the panel used to be there but I'll try what you said just now...

---

### Post by Dj Dutchman on 2008-06-21
How do I start htop without the panel and over a remote connection??? I'm using vncviewer...

---

### Post by mssever on 2008-06-22
> **Dj Dutchman said:**
> How do I start htop without the panel and over a remote connection??? I'm using vncviewer...
Do it from the terminal. If you can't open a terminal in your remote VNC session, leave the session open, then SSH into the box as a separate connection and run htop from there.

---

### Post by MrGrey1 on 2008-07-18
> **fiskpinnen said:**
> After spending to much time on this solution and getting constant problems I gave up and went back to my old way which works perfect unless you crave logging in to a separate desktops at the same time. Just wanted to post it here since it may suit others as well. The trick is to ditch vnc4server and opt for x11vnc, and as I said, works great. Works from the gdm login prompt and on.

1. Disable Desktop Sharing under System -> Preferences -> Remote Desktop
2. sudo apt-get install x11vnc
3. sudo x11vnc -storepasswd yourpasswordhere /etc/x11vnc.pass
4. sudo gedit /etc/X11/gdm/Init/Default
5. add this line to the bottom above exit:  /usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900
6. sudo gedit /etc/X11/gdm/gdm.conf-custom and add "KillInitClients=false" under section [daemon] so you don’t get your session killed after you log in (without the "")
7. restart

Happy vnc'ing for you!

I KISS YOU! BeU ti ful! Wasted far too much time on this and your instructions fixed it straight up. Running 8.04. (Setup with WOL to turn machine on, setup with tunneling through ssh so secure, can access from anywhere! Yay!)

---

### Post by irvin on 2008-08-13
Hallo

I'm using x11vnc for remote desktop on Ubuntu 8.04 with SSH which works great. With this config I can login directly after reboot for 1 User:

What I want now is to login with several users at the same time.
As I heard that this won't work with x11vnc, i heard this should work with vnc4server.

for example:
I have these users:

no1@test (admin)
no2@test
no3@test

Every user has a different password ! That's important. And every user can use only his own files, except the "admin" which ist "no1@test".

What does I have to change (which config files) for login with multiple users at the same time ? So everyone has his own desktop and can use his own files.

I tried several things found here but nothing worked for me.
May somebody made this and can help me ?

Can i go only over one port 5900 or does every user has a own port 5900, 5901, 5902 ?

---

### Post by djacidjac on 2008-09-27
how about on Hardy?...

Hi, does anyone know how to get a login when connected via VNC in Hardy Heron? Everything else I've got working fine. I think I just need to add the correct lines to /etc/.vnc/xstartup and maybe also to /etc/gdm/gdm.conf-custom. Any insight would be great. 

I can start a gnome session by adding gnome-session to /etc/.vnc/xstartup and mostly any other app that I want but I'm not sure how to call up the gdm login. Also, I can't start an xfce4-session that way; I can do sudo xfce4-session from a remote terminal via VNC, but that's it. Do I need to change the permissions of an XFCE related file?

What is the gdm login screen called and where is it located?

I'm using tightVNC on Hardy Heron and Chicken of the VNC on mac OS X.4.11

---

### Post by mssever on 2008-09-29
> **djacidjac said:**
> how about on Hardy?...

Hi, does anyone know how to get a login when connected via VNC in Hardy Heron? Everything else I've got working fine. I think I just need to add the correct lines to /etc/.vnc/xstartup and maybe also to /etc/gdm/gdm.conf-custom. Any insight would be great. 

I can start a gnome session by adding gnome-session to /etc/.vnc/xstartup and mostly any other app that I want but I'm not sure how to call up the gdm login. Also, I can't start an xfce4-session that way; I can do sudo xfce4-session from a remote terminal via VNC, but that's it. Do I need to change the permissions of an XFCE related file?

What is the gdm login screen called and where is it located?

I'm using tightVNC on Hardy Heron and Chicken of the VNC on mac OS X.4.11
/etc/.vnc/xstartup is definitely a nonstandard path. Do you mean /etc/vnc/xstartup? The instructions in this thread work for me under Hardy. And I don't have anything under /etc/vnc.

---

### Post by danimaltron on 2008-10-23
I followed instrutions to set this up on new ubuntu install. It told this:

```
service Xvnc
vncviewer localhost:1
[B]localhost 5901
/usr/bin/vncviewer: 28: java: not found[/B]

```

So I opened up synaptic package manager and installed Java and all dependent packages.

Then I went back and tried it, and Voila! the login screen opened up. I typed in my password and nothing happened...

Then terminal told me this:

```

 vncviewer localhost:1
localhost 5901
[B]java.net.ConnectException: Connection refused
   at gnu.java.net.PlainSocketImpl.connect(libgcj.so.81)
   at java.net.Socket.connect(libgcj.so.81)
   at java.net.Socket.connect(libgcj.so.81)
   at java.net.Socket.<init>(libgcj.so.81)
   at java.net.Socket.<init>(libgcj.so.81)
   at rfbProto.<init>(rfbProto.java:93)
   at vncviewer.connectAndAuthenticate(vncviewer.java:193)
   at vncviewer.run(vncviewer.java:122)
   at java.lang.Thread.run(libgcj.so.81)
java.net.ConnectException: Connection refused[/B]

```

What does this mean? Do I have some sort of Java problem?

I'm brand new to ubuntu and not sure what to do from here.

Thanks

---

### Post by danimaltron on 2008-10-23
I remembered that I originally installed something from an article I seen here: [http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php](http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php)

So I uninstalled that and restarted this tutorial.

Now when I tried to connect to localhost, it says:

**vncviewer: read: Connection reset by peer**

---

### Post by breauxlg on 2009-02-19
When I try to use gedit I get a message "cannot open display" so I used the text editor to create the Xvnc file in /etc/xinetd.d/ but when I try the vncviewer localhost:1 I get a message "cannot open display".

---

### Post by jcr1 on 2009-02-19
Hi,

I have follwed this guide plus other very similar ones, and i always get :

```

jonr@jonr-laptop:~$ vncviewer localhost:1
Connected to RFB server, using protocol version 3.8
Performing standard VNC authentication
Password: 
vncviewer: VNC server closed connection
jonr@jonr-laptop:~$ 

```

Any ideas why this would happen?

Thanks in advance.

---

### Post by twisted_hick on 2009-03-04
Hello I would like to be able to just VNC straight to the desktop of a already running session(xubuntu 8.10, ubuntu 8.04) also. I have gotten the resumable sessions working but now when I try to login with out the ":1" at the end of the ip I get
> vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
 I still connect fine to the windows machines on the lan I can control the active desktop and use the resources fine. I've burned the midnight coffee and might have over looked the solution in the forums so any help would be greatly appreciated.

---

### Post by Skip Da Shu on 2009-04-03
> **twisted_hick said:**
> Hello I would like to be able to just VNC straight to the desktop of a already running session(xubuntu 8.10, ubuntu 8.04) also. I have gotten the resumable sessions working but now when I try to login with out the ":1" at the end of the ip I get
 I still connect fine to the windows machines on the lan I can control the active desktop and use the resources fine. I've burned the midnight coffee and might have over looked the solution in the forums so any help would be greatly appreciated.

The :1 at the end gets added to 5900 to set the port the VNC communication is to happen on.  If the remote machine is set up for 5901 then you have to include the :1.  If you don't want to do that you have to set up the VNC server on the remote machine to use the default port of 5900.  Which is fine and unless you are setting up port forwarding for remote access from outside your LAN in the router to multiple machines then the default of 5900 should be fine.


or did I misunderstand the question?

---

### Post by man0l0 on 2009-07-01
i use "vncserver localhost:1" but nothing happens.when i use "grep xinetd /var/log/syslog" and i get "warning: can't get client address: Transport endpoint is not connected"    endlessly....the port 5901 is open and when i use "ps -ef | grep Xvnc" i get 
cool     22169 22051  0 21:40 pts/0    00:00:00 grep Xvnc
root     22170  4707  0 21:40 ?        00:00:00 [Xvnc]


any ideas????  ](*,)

---

### Post by caue.rego on 2009-07-06
although I still don't have it working, here are a couple ideas:

[http://ubuntuforums.org/showthread.php?p=5229232#post5229232](http://ubuntuforums.org/showthread.php?p=5229232#post5229232)

and

[http://ubuntuforums.org/showthread.php?p=7486294](http://ubuntuforums.org/showthread.php?p=7486294)

---

### Post by Skip Da Shu on 2009-07-06
For reasons unknown I didn't find the original thread on using x11vnc.  It was either written by or maybe many of my questions had been answered by Krunge.

However, starting about halfway down [**THIS**]("http://www.skipsjunk.net/how-to/xubuntu04.html") page is a how-to on it.  I used that and my Intrepid desktop or Windoze machine still connects to the machines with that setup at the LOGON screen.  I haven't been back through the install since v8.10.  With that release, as I recall, you needed to add the '-noxfixes' to the command line.

---

### Post by caue.rego on 2009-07-06
> **Skip Da Shu said:**
> For reasons unknown I didn't find the original thread on using x11vnc.  It was either written by or maybe many of my questions had been answered by Krunge.


the one i've seem is actually the #71 post in this very topic, but not by that Krunge guy:
[http://ubuntuforums.org/showthread.php?p=2533903](http://ubuntuforums.org/showthread.php?p=2533903)

---

