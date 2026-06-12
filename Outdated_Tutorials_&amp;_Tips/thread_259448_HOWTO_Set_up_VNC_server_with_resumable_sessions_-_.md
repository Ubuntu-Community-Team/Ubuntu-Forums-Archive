---
title: "HOWTO: Set up VNC server with resumable sessions - KUBUNTU VERSION"
date: 2006-09-17
forum: Outdated Tutorials &amp; Tips
---

### Post by paperdiesel on 2006-09-17
This guide is very similar to the Gnome Ubuntu HOWTO, located here:

[http://ubuntuforums.org/showthread.php?t=122402]("http://ubuntuforums.org/showthread.php?t=122402")

I have borrowed a lot of the notes from that author, only changing things to work for Kubuntu users.  Most of the credit for the info goes to the author of that post.  If you are having problems, I **strongly recommend** browsing through that thread first.

This guide is intended for Kubuntu users, and details how to enable Xdmcp for your KDE session.  It was written using Kubuntu 6.06 (i386) as a reference.  In the steps, I use kate as the text editor, but you can use whatever editor you prefer.  In reality I use vi, but most people don't know vi commands so I stick with kate in these examples.

**Required packages:**

To make sure you have the proper software installed, execute the following:

Type in a terminal:
```
sudo apt-get install vnc4server xinetd xvncviewer
```

The latest versions are:
vnc4server: Xvnc Free Edition 4.1.1
xinetd: xinetd Version 2.3.14 libwrap loadavg
xvncviewer: VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05

If you're using previous versions of any of these packages, there's no guarantee this will work. (Actually, there's no guarantee this will work anyway, but if you use versions below what I indicated, then you're just making it harder on yourself ](*,) )

WARNING:  Make sure you install **vnc4server** and NOT **vncserver**.  These packages ARE different, and the latter will NOT work correctly.

**Note to AMD64 users:** The current version of vnc4server in the repositories has a bug, so you need to download and install the fixed vnc4 packages as shown below:
```

wget http://qt1.iq.usp.br/download/vnc4server_4.0-7.3_amd64.deb
wget http://qt1.iq.usp.br/download/xvnc4viewer_4.0-7.3_amd64.deb
sudo dpkg -i vnc4server_4.0-7.3_amd64.deb
sudo dpkg -i xvnc4viewer_4.0-7.3_amd64.deb

```

**THE STEPS:**

**1. ENABLE XDMCP IN KDE**

Type in a terminal:
```
sudo kate /etc/kde3/kdm/kdmrc
```

At the very bottom of the file, you'll see this section:

```

[Xdmcp]
Enable=false
Willing=/etc/kde3/kdm/Xwilling

```

Change it to look exactly like this:
```

[Xdmcp]
Enable=true
Port=177
Xaccess=/etc/kde3/kdm/Xaccess
Willing=/etc/kde3/kdm/Xwilling

```

Save the file and quit.  Then type this in your terminal:

```
sudo kate /etc/kde3/kdm/Xaccess
```

This is a big file and can be confusing, so make sure you do this exactly as shown.  Scroll down and find this line:

```
#*                                       #any host can get a login window
```

Remove the **#** from the beginning of that line, so it looks like this:

```
*                                       #any host can get a login window
```

Then find this line:
```
#*               CHOOSER BROADCAST       #any indirect host can get a chooser
```

Remove the **#** from the beginning of that line, so it looks like this:
```

*               CHOOSER BROADCAST       #any indirect host can get a chooser
```

Save the file and quit out of KATE.

Now we need to restart the KDM process so it will re-read the configuration file. The easiest way to do this is to just reboot the machine. The quickest is to do the following:

```
ps -ef | grep kdm
```

This will print out a list of processes with the letters 'kdm' in the name. Find the one that looks like the following (Specifically the one that ends in /usr/bin/kdm):

```
root    4530      1     0 0:09:20 ?          00:00:00 /usr/bin/kdm
```

See the number right after root? 4530 in my example, you will almost certainly have a different number. That's the process ID or PID. Type the following command to restart kdm (Substituting the PID number you have for the 4530 in my example):

```
sudo kill -HUP 4530
```


**2. SET THE VNC PASSWORD**

Type this in a terminal:
```
sudo vncpasswd /root/.vncpasswd
```


**3. ADD VNC SERVICE TO XINETD**

Type this in a terminal:
```
sudo kate /etc/xinetd.d/Xvnc
```

Enter this in to the new file:
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

I recommend leaving all of that code alone, but you can safely change the 1024x768 to be a bigger or smaller resolution for your Xvnc window, depending on what you want.  You can also change the depth, but understand that increasing the depth bits will cause more bandwidth to be used over your network, which could slow down your VNC experience considerably.


**4. RESTART XINETD**

If the following code does not work, try rebooting:
```

sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo /etc/init.d/xinetd start

```

Don't worry if you see a message like "Xvnc: no process killed".  This just means there was no open, active session of VNC running at the time.  This is expected and is normal.


**5. TEST**

If you followed all of the above steps correctly, you should now be able to test your VNC server.  Type the following in a terminal:
```
vncviewer localhost:1
```

You should be prompted for the VNC password, and then see the KDM login screen where you can login and start a new X session. If that works, you can now go ahead and try to connect from remote machine using your favorite VNC client (remember to first close the local vncviewer we started above). Remember to use the VNC server machine's domain name or IP address, followed by :1 (e.g. 192.168.0.100:1). If connecting locally as shown above works, but connecting remotely fails, then this means you have a problem with a firewall which is blocking some ports. See the notes below about how to deal with that.

**Note about ports:** The VNC server set up as shown uses TCP port 5901. If you are using firewall software (e.g. firestarter) on that machine, you need to allow incoming connections on this port. If you are using a router which assigns your machine a private address (e.g. 192.168.0.100) which is not accessible from the internet, then you need to forward TCP port 5901 from the router to this machine.

**Note about security:** This setup allows any user to start an X-session remotely by logging in using his regular password (after starting the VNC connection using the VNC password), so if the user disconnects without logging out, any other user which knows the VNC password can connect afterwards and resume the same session that the first user started. So if you do not want to log out before disconnecting, it's advisable to at least lock your VNC X-session screen. Also note that while a remote user is connected thru VNC, no other connection will be accepted. An idle VNC client will be disconnected after one hour, but this can be changed by using the "-IdleTimeout" option in the server_args line in /etc/xinetd.d/Xvnc. For example, you can add "-IdleTimeout 300" to change it to 5 minutes.


reference links:
Gnome VNC howto: [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)
Xdmcp in kdm: [http://klomdark.servebeer.com:8081/MessageBase2/ReadMessage.aspx?MsgNum=1967](http://klomdark.servebeer.com:8081/MessageBase2/ReadMessage.aspx?MsgNum=1967)


Good luck!

---

### Post by master_b on 2006-09-26
Hi paperdiesel

Thanks for the Kubuntu HowTo for vnc4server.

I've been trying to get remote access (over my home LAN) to desktop:0 ( actual desktop) of a remote "headless" PC ie no monitor, mouse or keyboard, but its NVidea TV out is connected to a TV and I can view the "cloned" desktop ( and TV output) on that.

Can successfully remotely access the pc using NX ( better than vnc, Krfb etc in my opinion) but none of those allow access to desktop:0, whereas vnc4 will ( at least according to its website).

Will post re my success or otherwise.

Bill

---

### Post by master_b on 2006-09-27
Follow-up:-

Worked perfectly except that I get a grey desktop. Remember having same problem eons ago with vnc but forget fix. Will figure it out and post.

In addittion, NX still works without problems, whereas when I had plain vnc installed, NX wouldn't work when the vncserver was running.

Bill

---

### Post by paperdiesel on 2006-09-27
Hey Bill,

If you want to use VNC to view display :0, I'd recommend [x11vnc]("http://www.karlrunge.com/x11vnc/").  I used it a while back, and if I remember correctly, it acts as a VNC extension to the X server, and loads inside your xorg.conf file and allows you to VNC in to the main display.

I've also heard about people using vnc4server and getting grey screens.  But if you're trying to use vnc4server to display :0, that might be why you're getting a grey screen.  Try x11vnc and let me know if it works.

---

### Post by master_b on 2006-09-27
Hi paperdiesel

thanks for the reply.

Have tried several "HowTos" for remote connecting to desktop:0, including x11vnc, but your instructions herewith are the only one's that I've found for Kubuntu.

Problem is that many of the Ubuntu "Howtos" give instructions to use various Gnome Menu items that just don't exist with Kubuntu/KDE, and fail to name the actual config files that are altered.

From past experience with vnc,  which I haven't used since discovering NX, I have vague recollections that in order to fix the "grey screen" problem, a config file has to be altered to include the starting of the desired window manager, in this case kde.

When I get time I'll dig through my old install notes and try to find the info. Have "googled" to no avail. I think that this "grey screen" problem can occur regardless of whether you are using Krdc, vnc, x11vnc etc.

Bill

---

### Post by paperdiesel on 2006-09-28
Ah, well if that's the case, the only config file I know that sounds similar to what you describe is the xstartup file, located in ~/.vnc/

Open up ~/.vnc/xstartup and scroll to the bottom of the file.  If you see a line that looks like:

```
twm &
```

Change it to:

```
startkde &
```.

See if that helps.

---

### Post by master_b on 2006-09-29
Hi paperdiesel

Yep, thats the file I was looking for, though I now believe that that isn't my problem.

Did an nmap of both the Client PC:-

PORT     STATE SERVICE
22/tcp   open  ssh
111/tcp  open  rpcbind
631/tcp  open  ipp
693/tcp  open  unknown
782/tcp  open  hp-managed-node
2049/tcp open  nfs

and the Server PC:-

PORT     STATE SERVICE
22/tcp   open  ssh
5901/tcp open  vnc-1
6001/tcp open  X11:1

Don't seem to be able to open/forward any more ports on my modem/router ( 10 forwarded at present)

I'm not sure where the problem is - I'm still getting a grey screen with vncviewer from the Client pc. Am thinking that it may be related to 6001 X11.

Will keep trying. If I can find a cross-over cable I'll try direct from pc to pc without the modem/router.

Bill

---

### Post by paperdiesel on 2006-09-29
Can you get a successful vnc session running on the server machine?  Test it on the server with 

```
xvncviewer localhost:1
```
If it works on the server and not from a remove client, it has to be a network issue.  But if you get a grey screen testing it form the server itself, it's most likely a vnc settings issue.

---

### Post by master_b on 2006-09-29
Hi paperdiesel

Getting closer to success.

Have determined that NX is running on remote pc, so when I start vnc4server I need to log-in remotely to desktop:2.( I had been logging into desktop:1 which is the NX remote desktop).

I then was getting a grey screen with a white terminal.

Editing ~/.vnc/xstartup with "startkde &" and remotely logging in to desktop:2 has kde start automatically but crash while loading the desktop.

Will continue to attempt to fix problem - first by removing NX. I'd prefer to keep it installed and running, but I'll try to get xvnc4viewer accessing desktop:0 first.

Bill

---

### Post by Al_maverick on 2006-09-30
I get an error while trying to dpkg vnc4server

> al@maverick:~/tmp$ sudo dpkg -i vnc4server_4.0-7.3_amd64.deb
Selecting previously deselected package vnc4server.
(Reading database ... 142996 files and directories currently installed.)
Unpacking vnc4server (from vnc4server_4.0-7.3_amd64.deb) ...
dpkg: dependency problems prevent configuration of vnc4server:
 vnc4server depends on xserver-common; however:
  Package xserver-common is not installed.
dpkg: error processing vnc4server (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 vnc4server

I tried to install xserver-common but it says it depends on xorg-common, or something. I just dont want to go any further without if Im gonna mess my X installation.

---

### Post by paperdiesel on 2006-09-30
> **Al_maverick said:**
> I get an error while trying to dpkg vnc4server



I tried to install xserver-common but it says it depends on xorg-common, or something. I just dont want to go any further without if Im gonna mess my X installation.

Did you install the AMD64 version of ubuntu?  If so, I'm not sure what's up.  But if you're running the x86 install on 64 bit architecture, all 32 bit packages will work on 64 bit processors assuming you've installed the x86 version of ubuntu.

---

### Post by Al_maverick on 2006-10-01
> **paperdiesel said:**
> Did you install the AMD64 version of ubuntu?  If so, I'm not sure what's up.  But if you're running the x86 install on 64 bit architecture, all 32 bit packages will work on 64 bit processors assuming you've installed the x86 version of ubuntu.

Im running Dapper for AMD64. I upgraged from Breezy for AMD64.
Specifically, this is the kernel image im running now: 2.6.15-26-amd64-generic

My question is, is there a problem installing xorg-common and all the other packages it says it needs, like xserver-common?

---

### Post by paperdiesel on 2006-10-01
Well I'm certainly no expert, but my opinion is that there is no problem getting the additional packages it needs.  That being said, it's never a bad idea to backup certian files, such as your /etc/X11/xorg.conf file, your /etc/network/interfaces, etc.

I would go ahead and let them download and install.  But it might not hurt to ask around some more or browse for similar issues on these forums.

---

### Post by Al_maverick on 2006-10-02
> **paperdiesel said:**
> Well I'm certainly no expert, but my opinion is that there is no problem getting the additional packages it needs.  That being said, it's never a bad idea to backup certian files, such as your /etc/X11/xorg.conf file, your /etc/network/interfaces, etc.

I would go ahead and let them download and install.  But it might not hurt to ask around some more or browse for similar issues on these forums.

I got some errors trying to install xserver-common. One of them said it had been replaced by x11-common, which i already have on my system.
So I ran dpkg again, with the option --ignore-depends=xserver-common. It ran flawlessly and now its working.

Tnx for the how-to, paperdiesel!! :)

---

### Post by glave on 2006-12-24
Just for reference, I had a problem with myself getting a connection reset by peer.

[http://ubuntuforums.org/showthread.php?p=1869576&highlight=then+I+tried+to+manually+create+the+server+with#post1869576](http://ubuntuforums.org/showthread.php?p=1869576&highlight=then+I+tried+to+manually+create+the+server+with#post1869576)

Following the above advice (adding my fonts path to the config) I was able to get things working smoothly!

---

### Post by pickarooney on 2006-12-24
I get the following when running vncviewer localhost:1 on Kubuntu 6.10 64-bit, qfter forcing the dpkg files to install without deps.
```

VNC viewer for X version 4.0 - built Oct 19 2005 20:19:45
Copyright (C) 2002-2004 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Mon Dec 25 00:51:54 2006
 main:        unable to connect to host: Connection refused (111)

```

Same if I try to connect to 192.168.1.100 (my PC) or when changing the number after teh colon to 0 or 15900 (my open VNC port, set as such in the setup file).

---

### Post by leprasmurf on 2006-12-25
great guide, I'll have to try it with edubuntu.

---

### Post by ErikTheRed on 2006-12-26
When I try to run *vncviewer localhost:1* i get this
> ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)

Any ideas?

EDIT: Oh it sounds like the solution was posted earlier in the thread, sorry for not reading. For reference my fonts path with /usr/share/fonts/X11/misc

---

### Post by ErikTheRed on 2007-01-01
Is it possible to setup VNC so that you can connect to display :0 ?

---

### Post by petitchevalroux on 2007-01-18
Hi all 
I just install the vnc4server ubuntu official package for 64 on edgy (4.1.1+xorg1.0.2-0ubuntu1.6.10.1). And in order to make it work i just create a link with
```
sudo ln -s /usr/share/fonts/X11/ /usr/share/X11/fonts
```
Thanks for the tuto.
I hope it will help

---

### Post by SVWander on 2007-02-17
I just tried to install VNC in KDE. when I rebooted it didn't go to my Xwindow (if that is the right term) but simply a blank screen prompting me to log on. How do I get my machine working again?
tm

---

### Post by pixelhead on 2007-03-05
Great HowTo!!! Thanks a lot!!!

- Andreas

---

### Post by fuzzyeric on 2007-03-31
I too have the "gray screen" on AMD64 problem.  I've traced this problem down a bit.  It's caused by
1) I don't start a GUI on display :0.  (It's a headless server in a closet.  No point in wasting a couple hundred MB in pointless footprint.)
2) Xvnc starts no window manager.

So, although KDE is an XDMCP server, it's not running and isn't started by the xinetd->Xvnc chain.

Resolution:  Use vnc4server, which not only can start Xvnc, but can *also* start your window manager et al.  Modify the /etc/xinetd.d/Xvnc file to read as:

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/vnc4server
        server_args = :1 -geometry 1280x768 -depth 16 -query localhost -inetd -o
nce -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/misc/,/usr/share/fonts/X1
1/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/ -DisconnectCli
ents=0 -AlwaysShared -IdleTimeout=0 passwordFile=/root/.vncpasswd
        port = 5901
}

What's changed is the name of the server.  The arguments have also been sorted to suit the syntax of vnc4server.

---

### Post by deserthowler on 2007-04-15
I am running Kubuntu Dapper.

I had TightVNC installed so I uninstalled it and the other VNC stuff.  I installed everything just as you said in the WIKI.  It worked just as stated.  I got the sign-in screen just as I wanted.  I had the monitor running on the server computer and got a log-in window there too.  I ended up running 2 sessions simultaneously ... one on the client and one on the server computer.

I got a lot of error messages from kate so I went to nano and wrote the configuration files.

GREAT WIKI!!!!  :KS :KS :KS   It worked.  That's all I can say. :D 

Earl

---

### Post by cmoman on 2007-05-07
> 1) I don't start a GUI on display :0. (It's a headless server in a closet. No point in wasting a couple hundred MB in pointless footprint.)

I managed to get the VNC part going well thanks.

I was wondering how you achieve 1) above?

Thanks

---

### Post by borahshadow on 2007-05-18
> 
Resolution: Use vnc4server, which not only can start Xvnc, but can *also* start your window manager et al. Modify the /etc/xinetd.d/Xvnc file to read as:

service Xvnc
{
type = UNLISTED
disable = no
socket_type = stream
protocol = tcp
wait = yes
user = root
server = /usr/bin/vnc4server
server_args = :1 -geometry 1280x768 -depth 16 -query localhost -inetd -o
nce -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/misc/,/usr/share/fonts/X1
1/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/ -DisconnectCli
ents=0 -AlwaysShared -IdleTimeout=0 passwordFile=/root/.vncpasswd
port = 5901
}
I did that but now it get 
>  main:        unable to connect to host: Connection refused (111)

any ideas?
also how would I make it so that multiple users can each have their own session open at the same time?

ps I have followed this but that should not affest this I don't think
[http://www.realvnc.com/products/free/4.1/x0.html]("http://www.realvnc.com/products/free/4.1/x0.html")

---

### Post by kumarnarain on 2007-06-21
Hai
Tried installing ...bu the package is looking for xserver-common..which version will be compatible...or is there a workaround??

Unpacking replacement vnc4server ...
dpkg: dependency problems prevent configuration of vnc4server:
 vnc4server depends on xserver-common; however:
  Package xserver-common is not installed.


that is the message I got...:confused:


Regards
Kumar

---

### Post by Al_maverick on 2007-06-21
> **Al_maverick said:**
> I got some errors trying to install xserver-common. One of them said it had been replaced by x11-common, which i already have on my system.
So I ran dpkg again, with the option --ignore-depends=xserver-common. It ran flawlessly and now its working.

Tnx for the how-to, paperdiesel!! :)

This could help you avoid the xserver-common dependency. I think there is an error in how the package dependencies were built. xserver-common is deprecated.

---

### Post by kumarnarain on 2007-06-23
Hai
Evrything is fine....i am getting a log in screen with the command ::

vncviewer localhost:1

but it is not accepting root and the password I had set earlier..I am yet to test it with a dyndns name I have..

Any help??

---

### Post by kumarnarain on 2007-06-26
Hai
I have finished installing vnc and I am able to get a log in screen when I tested it with local host...but it is not accepting the user name password   combination I supplied...I have reset the pwd a number of times...still the same problem is there...also I tried logging in from a remote location thru vnc using a dyndns account i get the following words "RFB 003.008"

Any help??

---

### Post by kumarnarain on 2007-06-27
Hai
This is a repost of what [I had posted here]("http://ubuntuforums.org/showthread.php?p=2885097#post2885097")
I think I am very close to getting it...just need to cross this step!!
I have finished installing vnc and I am able to get a log in screen when I tested it with local host...but it is not accepting the user name password combination I supplied...I have reset the pwd a number of times...still the same problem is there...also I tried logging in from a remote location thru vnc using a dyndns account i get the following words "RFB 003.008"

Any help??

---

### Post by Al_maverick on 2007-06-27
have you set the vnc password? its different from your regular user password.

---

### Post by kumarnarain on 2007-06-28
Hai
Thanks for the reply....
I have got it working within the local machine now...still I am not able to do it from a remote machine...my router has port forwarding (udp 5901)enabled. I am trying to access the machine thru a dyndns account that I have

Thanks

---

### Post by kumarnarain on 2007-06-28
Sorry....read TCP instead of UDP in the above post...

---

### Post by cmoman on 2007-06-28
Have you made sure your VNC client is using port 5901 to connect? The default for RealVNC is port 5900 from memory. Your VNC client might be doing the same.
You specify the port like hostname:vncscreen: port eg nyname.dyndns.org:1:5901

---

### Post by kumarnarain on 2007-06-29
Hai
Yes..I have done that and yet it doesn't seem to be working.....Moreover firefox doesn't seem to be accepting the myname.dyndns.org:1:5901 format

I had to add a string to about:config of Firefox and still I am unable to connect

Regards

Kumar

---

### Post by cmoman on 2007-06-29
if you are using a web browser, don't you need the java packages for the vncserver installed?  I've never used the web browser interface so I can't comment too much more.
what's the result if you use a vnc client on the machine you're logging in from?
[http://www.realvnc.com](http://www.realvnc.com) if you need a windoze client, there a free version but you have to look for it.

---

### Post by Al_maverick on 2007-06-29
did you check that dyndns is working correctly. if you run a nslookup, can you find the pc and it is the correct IP?
in firefox, did you add http:// in front of the address, to make sure that it tries to open as a http page?
as advised, i would try first with a normal vnc client, to eliminate uncertainties.

---

### Post by kumarnarain on 2007-06-29
Well....I have done all that and just to be sure I tried running a streaming server ....that works well...so my guess is that it has got to do with the settings/conf files..

---

### Post by maybeway36 on 2007-07-06
I think it might be better to use kwrite instead of kate, since you're only editing one file at a time anyway.

---

### Post by netvampire on 2007-07-25
Thanks. Guide Worked Great.

---

### Post by philo23 on 2007-07-28
when i tried
```
vncviewer localhost:1
```
the first time, i got a X for a cursor and a black and white background and the desktop just didnt do anything else.
after i restarted and tried again, i got this error:
```
ReadFromRFBServer: rdr::EndOfStream
```
Any ideas people, i want to get this pc monitor-less as soon as possible but i cant untill i can remote desktop to it.

Thanks in advance who ever helps.

---

### Post by KristoferP on 2007-08-02
I've followed this guide and got it working on my computer using Kubuntu Fiesty. But whenever i try to launch some aplications like firefox from a vnc session i get the following error:
```
X Error: BadRequest (invalid request code or no such operation) 1
  Major opcode:  146
  Minor opcode:  2
  Resource id:  0x3800001
Xlib:  extension "XInputExtension" missing on display "monkeybox.local:1.0".
Failed to get list of devices
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 190 error_code 1 request_code 146 minor_code 23)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Actually i get that error message from all GUI programs i try to launch from the console, but some of the just report the error (up until "The program 'X' received an X Window System error...) then launch.

What could be the cause?

---

### Post by jd65pl on 2007-08-05
> **philo23 said:**
> when i tried
```
vncviewer localhost:1
```the first time, i got a X for a cursor and a black and white background and the desktop just didnt do anything else.
after i restarted and tried again, i got this error:
```
ReadFromRFBServer: rdr::EndOfStream
```Any ideas people, i want to get this pc monitor-less as soon as possible but i cant untill i can remote desktop to it.

Thanks in advance who ever helps.

I get the same?? Anyone have any ideas?

---

### Post by geek.de.nz on 2007-08-12
> [SIZE=-1]The error was '**BadRequest** (**invalid request code or no such operation**)'. (Details: **serial** 190 **error_code** 1 **request_code** 146 minor_code 23) ...[/SIZE]

This issue was still there for me. After a bit of googling and looking i found out that making your /etc/xinetd.d/Xvnc file look like this helps:

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}

---

### Post by AlfaTrion on 2007-08-27
worked like a charm.
thank you so much!

---

### Post by ukdoc on 2007-10-06
This works absolutely brilliantly.

However, I have noticed I get the following error whenever I log in via a VNC session:

see: [http://bugs.kde.org/show_bug.cgi?id=144514]("http://bugs.kde.org/show_bug.cgi?id=144514")

(Basically the power manager crashes - description at url above)

Anyone got any suggestions how to fix this - it only happens with VNC sessions - if I log in when I'm actually at my desktop there are no errors.

Cheers

---

### Post by darksmurf on 2007-10-25
Worked great in Kubuntu and Ubuntu 7.10, the setup is virtually the same with the only difference being how to enable Xdmcp for kdm or gdm...kdm was easier.

---

### Post by happyface on 2007-10-27
Well I followed the tutorial and I just can't get vncviewer to work. Here's the log i get:

```

Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'

Xvnc Free Edition 4.1.2 - built May 12 2006 17:42:24
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 40201000, The XFree86 Project, Inc


Sat Oct 27 11:11:00 2007
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      Listening for HTTP connections on port 5801
 vncext:      created VNC server for screen 0
Could not init font path element unix/:7100, removing from list!

Fatal server error:
could not open default font 'fixed'
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":1.0"
      after 0 requests (0 known processed) with 0 events remaining.
vncconfig: unable to open display ":1"
xterm Xt error: Can't open display: :1
xset:  unable to open display ":1"

```

I keep getting the fontpath and the rgb error even though i have adjusted the paths in /etc/vnc.config like this:

```

 $fontPath = "/usr/share/fonts/X11/misc,";
 $fontPath .= "/usr/share/fonts/X11/75dpi/:unscaled,";
 $fontPath .= "/usr/share/fonts/X11/100dpi/:unscaled,";
 $fontPath .= "/usr/share/fonts/X11/Type1,";
 $fontPath .= "/usr/share/fonts/X11/100dpi,";
 $fontPath .= "/usr/share/fonts/X11/75dpi";

 $colorPath = "/usr/lib/X11/rgb.txt";

```

Could someone tell me what I'm doing wrong?

Thanks in advance.

---

### Post by reefland on 2007-10-30
> **philo23 said:**
> when i tried
```
vncviewer localhost:1
```
the first time, i got a X for a cursor and a black and white background and the desktop just didnt do anything else.
after i restarted and tried again, i got this error:
```
ReadFromRFBServer: rdr::EndOfStream
```
Any ideas people, i want to get this pc monitor-less as soon as possible but i cant untill i can remote desktop to it.

Thanks in advance who ever helps.

I got this same error on kubuntu 7.10.  I fixed it by simply adding the "-extension XFIXES" as described in this thread solved the problem for me.

---

### Post by lcslouis on 2007-11-06
is there anyway is can set this for mutiple users as in i want to make 5 users and let each have access to an account how can i do this?

---

### Post by specher on 2007-11-07
Hello,

I am also looking to run vnc4server on a kubuntu 7,04 and try to connect to display :0
Does anyone already succeed in that
Which parameter do I have to change in the xinet file to achieve that. i tried to change the 5901 to 5900, but it seems only to change the port as i could expect it.

Thanks,

specher

---

### Post by RavonTUS on 2007-11-10
```

sudo apt-get install vnc4server xinetd xvncviewer

```

**This completly removes VMware.**  I did not see that coming.  I am total screwed now.  All my servers are gone.  

-R

---

### Post by paperdiesel on 2007-11-10
> **RavonTUS said:**
> ```

sudo apt-get install vnc4server xinetd xvncviewer

```

**This completly removes VMware.**  I did not see that coming.  I am total screwed now.  All my servers are gone.  

-R

Um.. no.  It does no such thing.  Something else must have gone horribly wrong if VMware was uninstalled by apt-get.

---

### Post by JackW24 on 2008-01-05
Hi everyone,

I'm a little new to this, but followed this tutorial (and the other version somewhere on these forums) I've managed to get both hamachi and xvnc loading on startup, letting me log into my kubuntu box from wherever I get a connection, fantastic.

The problem is, if I am in a vnc session and I choose to log out, then my main session (the one on the monitor physically connected to the box) logs out also to the shutdown screen and hangs there.

Any ideas?

I'm using Kubuntu 6.06 (i think), and everything else seems to be working exactly as expected.

---

### Post by flowersrj on 2008-01-23
Hi,

I have followed everything to a tee from the beginning but if I puTTY to the server and run "vncviewer localhost:0" I get the message ...

      **unable to open display ""**

I have double checked everything.  How can I debug/trace this?    This is on Gutsy Ubuntu Server.  

If I puTTY to the server and run vnc4server it returns ...

      **New 'desktop-1:2  (beezlebub)' is desktop-1:2**

I should mention also that the server is sitting at the logon display and this is on my network between 2 Kubuntu Gutsy machines and server temporarily has no firewall (behind NAT router).

Thanks, Rich

---

### Post by pickarooney on 2008-06-18
I got this set up fine on localhost, but am unable to connect using my external IP address or DynDNS address. Port 5901 is open on my router and forwarded to this PC. [www.canyouseeme.org](www.canyouseeme.org) says the port is open but I can't telnet my external Ip on 5901...

What am I missing?

[edit]

seems there are two or three ports open for vnc, judging by nmap. How to disable whatever service is on 5900 (assuming this is in some way responsible for my problem) ?

22/tcp   open  ssh
631/tcp  open  ipp
5800/tcp open  vnc-http
5900/tcp open  vnc
5901/tcp open  vnc-1
6001/tcp open  X11:1
6881/tcp open  bittorent-tracker
8080/tcp open  http-proxy

---

### Post by bobg-m on 2008-07-27
OK, I'm using kubuntu 8.04 (hardy heron). I have Xvnc, vnc4server installed. I know xinetd is working - it starts running Xvnc OK, and runs chargen and daytime too fine.

I don;t have a /etc/vnc.conf file - it seems this was never installed. I'm not using a vnc password (although this does work if I enable in the xinetd conf).

vncviewer starts, connects but then immediately disconnects, looks like it can't find kdm. Here are my various files:

/etc/xinetd.d/Xvnc

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
        server_args = -inetd :1 -query localhost -geometry 800x480 -depth 16 -once
-fp /usr/share/fonts/X11/misc/ -DisconnectClients=0 -NeverShared -SecurityTypes Non
e
        port = 5901
}

```

/etc/kde3/kdm/kdmrc

```

[X-*-Greeter]
AntiAliasing=true
ColorScheme=
EchoMode=OneStar
FaceSource=PreferUser
FailFont=Sans Serif,10,-1,5,75,0,0,0,0,0
GUIStyle=
GreetFont=Sans Serif,22,-1,5,50,0,0,0,0,0
GreetString=Welcome to Kubuntu at %n
GreeterPos=50,50
HiddenUsers=
Language=en_GB
LogoArea=Clock
LogoPixmap=/usr/share/apps/kdm/pics/kdelogo.png
MaxShowUID=29999
MinShowUID=1000
Preloader=/usr/bin/preloadkde
SelectedUsers=
ShowUsers=NotHidden
SortUsers=true
StdFont=Sans Serif,10,-1,5,50,0,0,0,0,0
Theme=@@@ToBeReplacedByDesktopBase@@@
UseBackground=true
UserCompletion=false
UserList=true

[X-:*-Core]
AllowNullPasswd=true
AllowShutdown=All
NoPassEnable=false
NoPassUsers=
ServerArgsLocal=
ServerCmd=/usr/bin/X -br

[X-:*-Greeter]
AllowClose=true
DefaultUser=bob
FocusPasswd=true
LoginMode=DefaultLocal
PreselectUser=Previous

[X-:0-Core]
AutoLoginAgain=false
AutoLoginDelay=0
AutoLoginEnable=false
AutoLoginLocked=false
AutoLoginUser=bob
ClientLogFile=.xsession-errors

[Xdmcp]
Enable=true
Port=177
KeyFile=/etc/kde3/kdm/kdmkeys
Xaccess=/etc/kde3/kdm/Xaccess
Willing=/etc/kde3/kdm/Xwilling

```

Xaccess is, in part

```

*                                       #any host can get a login window


*               CHOOSER BROADCAST       #any indirect host can get a chooser

```

Any ideas what I may be missing?

---

### Post by lars-friedrich on 2008-08-05
Hello,

thanks to this howto I've successfully installed 7 parallel resumable VNC-sessions (displays 1 to 7 and ports 5901 to 5907 respectively) on a kubuntu hardy heron (HP DL160 server). Now up to 7 users can simultaneously run separate resumable VNC sessions via Xvnc.

But there is one problem - I haven't found a solution, yet:
I enabled the GLX-extension for the Matrox G200e of the server (we need GLX-extension for compiling a library). The problem is that GLX is only available on display :0. This means that the extension runs on the server-console in the server-room, but not via the Xvnc-connections (displays :1.0 to :7.0). 
E.g. **glxinfo** delivers this when I run it via VNC (display :1):```

name of display: ibiapowerslave01.local:1.0
Xlib:  extension "GLX" missing on display "ibiapowerslave01.local:1.0".
Xlib:  extension "GLX" missing on display "ibiapowerslave01.local:1.0".
Xlib:  extension "GLX" missing on display "ibiapowerslave01.local:1.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display "ibiapowerslave01.local:1.0".
Xlib:  extension "GLX" missing on display "ibiapowerslave01.local:1.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display "ibiapowerslave01.local:1.0".
Xlib:  extension "GLX" missing on display "ibiapowerslave01.local:1.0".
0x22 16 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
```



Has someone of you faced a comparable problem? Does someone know a solution for this issue?
I'd be very grateful for some hints and inspirations!

cheers, lars

---

### Post by VaZso on 2008-08-06
> **lars-friedrich said:**
> Hello,

thanks to this howto I've successfully installed 7 parallel resumable VNC-sessions (displays 1 to 7 and ports 5901 to 5907 respectively) on a kubuntu hardy heron (HP DL160 server). Now up to 7 users can simultaneously run separate resumable VNC sessions via Xvnc.


Could you paste here some contents of your relevant config files?
I try to set up resumable sessions, but it doesn't work for me yet.

Although this is Debian, I think there isn't many differences...
For me, the Xvnc itself works well, I can log in from another machine and work on the desktop.
...but if I close the vncviewer window, I loose my work.

I've tried some configurations (modifications in /etc/xinet.d/xvncserver), but without success. Sometimes the server refused the connection, for example when I gave DisconnectClients=0 option...

Also, if I enable "wait" in this config file, the clients waits forever... at least too much time, so I think something doesn't do the right thing... What is this option for?

Now I will try to install xvnc4server (there is Xvnc in the config at this time), I hope it will help me...

----

Anyway, if I could set this up, can I start these sessions (and the applications they have to run) at the boot time? - so, before the user logs in by vnc.

I hope you can help me.

---

### Post by lars-friedrich on 2008-08-07
hi,

in /etc/kde3/kdm/kdmrc I did exactly what was suggested in the HowTo:
(relevant section)
```
[Xdmcp]
# Whether KDM should listen to incoming XDMCP requests.
# Default is true
Enable=true
# The UDP port on which KDM should listen for XDMCP requests. Do not change.
# Default is 177
Port=177
# File with the private keys of X-terminals. Required for XDM authentication.
# Default is ""
#KeyFile=/etc/kde3/kdm/kdmkeys
# XDMCP access control file in the usual XDM-Xaccess format.
# Default is "/etc/kde3/kdm/Xaccess"
Xaccess=/etc/kde3/kdm/Xaccess
# Number of seconds to wait for display to respond after the user has
# selected a host from the chooser.
# Default is 15
#ChoiceTimeout=10
# Strip domain name from remote display names if it is equal to the local
# domain.
# Default is true
#RemoveDomainname=false
# Use the numeric IP address of the incoming connection on multihomed hosts
# instead of the host name.
# Default is false
#SourceAddress=true
# The program which is invoked to dynamically generate replies to XDMCP
# DirectQuery or BroadcastQuery requests.
# If empty, no program is invoked and "Willing to manage" is sent.
# Default is ""
Willing=/etc/kde3/kdm/Xwilling
```

in /etc/kde3/kdm/Xaccess I also just uncommented the two lines listed in the HowTo.

I installed the **vnc4server** (deb-package).

The I modified /etc/xinet.d/Xvnc:

```
service Xvnc_user1
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
	server_args = :1 -geometry 1280x768 -depth 16 -query localhost -inetd -once -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/ -DisconnectClients=0 -AlwaysShared -IdleTimeout=0 passwordFile=/home/user1/.vncpasswd_user1 -extension XFIXES
        port = 5901
}

service Xvnc_user5
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
	server_args = :2 -geometry 1280x768 -depth 16 -query localhost -inetd -once -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/ -DisconnectClients=0 -AlwaysShared -IdleTimeout=0 passwordFile=/home/user5/.vncpasswd_user5 -extension XFIXES
        port = 5902
}

service Xvnc_user3
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
	server_args = :3 -geometry 1280x768 -depth 16 -query localhost -inetd -once -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/ -DisconnectClients=0 -AlwaysShared -IdleTimeout=0 passwordFile=/home/user3/.vncpasswd_user3 -extension XFIXES
        port = 5903
}

service Xvnc_user2
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
	server_args = :4 -geometry 1280x768 -depth 16 -query localhost -inetd -once -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/ -DisconnectClients=0 -AlwaysShared -IdleTimeout=0 passwordFile=/home/user2/.vncpasswd_user2 -extension XFIXES
        port = 5904
}

service Xvnc_user4
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
	server_args = :5 -geometry 1280x768 -depth 16 -query localhost -inetd -once -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/ -DisconnectClients=0 -AlwaysShared -IdleTimeout=0 passwordFile=/home/user4/.vncpasswd_user4 -extension XFIXES
        port = 5905
}

service Xvnc_user6
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
	server_args = :6 -geometry 1280x768 -depth 16 -query localhost -inetd -once -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/ -DisconnectClients=0 -AlwaysShared -IdleTimeout=0 passwordFile=/home/user6/.vncpasswd_user6 -extension XFIXES
        port = 5906
}

service Xvnc_student
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
	server_args = :7 -geometry 1280x768 -depth 16 -query localhost -inetd -once -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/ -DisconnectClients=0 -AlwaysShared -IdleTimeout=0 passwordFile=/root/.vncpasswd_student -extension XFIXES
        port = 5907
}
```

By convention I assigned a specific port to a specific user. Ports 5901 to 5906 are connected to VNC-password-files in the according user's home folder (apply chown userX:userX to it, so that the user can change his password using vncpasswd himself).
We have an additional VNC-account for a 'rightless' student - hence, his vncpasswd file is in the root-home.

This VNC-policy works really good, but unfortunately the GLX-extension is not supported by Xvnc. There is a project xf4vnc obviously supporting GLX, but there are no deb-packages and 64bit-binaries and I have not successfully compiled it, yet.

At the moment we are executing GLX-dependent applications via ssh -X, but this is not resumable like the VNC-policy is ...


>Anyway, if I could set this up, can I start these sessions (and the applications they have to run) at the boot time? - so, before the user logs in by vnc.

I cannot really tell you, but I think it could be possible to 'simulate' logins on the machine itself (maybe via a cron-job and some bash-scripts?). We do not need comparable features - our machine is something like a power-slave which we are using for complex and time-consuming model-calculations (therefore the resumable-aspect is quite important to us).

> Although this is Debian, I think there isn't many differences...
I think this, too!


cheers, lars

---

### Post by VaZso on 2008-08-07
> **lars-friedrich said:**
> in /etc/kde3/kdm/kdmrc I did exactly what was suggested in the HowTo:
...

Thank you very much, now it works for me with vnc4server.

Also, I can start the server for every user by su - user command.

Thanks again. :KS

---

### Post by mexus on 2008-11-05
Running Ubuntu Server 8.10 with KDE 4 installed.

Works fine. I use it with SSH tunneling.
The problem is that the vnc server and client are connected with 1000MB LAN, but the quality is very bad. I have set the depth to 24 but still bad quality. You can't see the text in task manager. The icons are not OK. Client is set to maximum? How can I get better quality or I should use other vnc server?

/etc/kde4/kdm/kdmrc
> 
Enable=true
Port=177
Xaccess=/etc/kde4/kdm/Xaccess
Willing=/etc/kde4/kdm/Xwilling

/etc/kde4/kdm/Xaccess
> 
*                                       #any host can get a login window
*
*               CHOOSER BROADCAST       #any indirect host can get a chooser

/etc/xinetd.d/Xvnc
> 
service Xvnc
{
type = UNLISTED
disable = no
socket_type = stream
protocol = tcp
wait = yes
user = root
server = /usr/bin/Xvnc
server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 24 -once -fp/usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueTy -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
port = 5901
}




Here is a screenshot:

---

### Post by jfeezie on 2008-11-06
I have the same settings as above and am also experiencing really terrible display issues. Many of the menu items are un readable... see attached picture. Any suggestions???

---

### Post by mexus on 2008-11-07
the same as mine

---

### Post by ukdoc on 2008-11-25
I'm also having exactly the same problem with an almost unreadable screen with KDE4 over vnc.

---

### Post by joegeek on 2009-01-27
I'm having problems setting this up,...

I'm trying to connect via RealVNC windows client 4.1.3 (although it doesnt work on localhost either).

On client side: I get the "grey screen" without a console box.

On server side: While tailing /var/log/syslog I see:
```
Jan 27 02:37:07 bigblackbox xinetd[5631]: warning: can't get client address: Transport endpoint is not connected
Jan 27 02:37:07 bigblackbox kdm: bigblackbox.blah.com:1[5644]: Abnormal termination of greeter for display bigblackbox.blah.com:1, code 1, signal 0
```
Just befor client is prompted for a password.

Any ideas?


btw: the blah.com is a "fake" domain setup just for my network, as these machines never see the internet anyway.  DHCP & Bind is setup properly on another ubuntu machine.

---

### Post by mexus on 2009-02-26
I have modified the previous how-to so it works for Kubuntu 8.10 with KDE 4.1 or 4.2 

The bug I mentioned few posts ago is still there. Non visible Desktop plasmoid and plasmoid options.

** Required packages:**

To make sure you have the proper software installed, execute the following:

Type in a terminal:

```
sudo apt-get install vnc4server xinetd xvnc4viewer
```

The latest versions are:
vnc4server: Xvnc Free Edition 4.1.1
xvncviewer: VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:23:14

If you're using previous versions of any of these packages, there's no guarantee this will work. (Actually, there's no guarantee this will work anyway, but if you use versions below what I indicated, then you're just making it harder on yourself)


I use VI as text editor (there is a bug in the default vi installation), so we need to install:

```
sudo apt-get install vim-full
```

**THE STEPS:**
[B]
1. ENABLE XDMCP IN KDE[/B]

Type in a terminal:

```
sudo vi /etc/kde4/kdm/kdmrc
```

Find the Xdmcp section and uncomment and edit the lines so they look like this:

```

[Xdmcp]
Enable=true
Port=177
Xaccess=/etc/kde4/kdm/Xaccess
Willing=/etc/kde4/kdm/Xwilling
```


Save the file and quit. Then type this in your terminal:

```
sudo vi /etc/kde4/kdm/Xaccess
```

This is a big file and can be confusing, so make sure you do this exactly as shown. Scroll down and find this line:

```

#*                                       #any host can get a login window
```


Remove the # from the beginning of that line, so it looks like this:

```
*                                       #any host can get a login window
```



Then find this line:

```
 #*               CHOOSER BROADCAST       #any indirect host can get a chooser 
```

Remove the # from the beginning of that line, so it looks like this:

```
 *               CHOOSER BROADCAST       #any indirect host can get a chooser 
```

Save the file and quit out of VIM.

Now we need to restart the KDM process so it will re-read the configuration file. The easiest way to do this is to just reboot the machine. The quickest is to do the following:

```
ps -ef | grep kdm
```


This will print out a list of processes with the letters 'kdm' in the name. Find the one that looks like the following (Specifically the one that ends in /usr/bin/kdm):

```
root    4530      1     0 0:09:20 ?          00:00:00 /usr/bin/kdm
```

See the number right after root? 4530 in my example, you will almost certainly have a different number. That's the process ID or PID. Type the following command to restart kdm (Substituting the PID number you have for the 4530 in my example):

```
sudo kill -HUP 4530
```

[B]
2. SET THE VNC PASSWORD[/B]

Type this in a terminal:

```
sudo vncpasswd /root/.vncpasswd
```


**3. ADD VNC SERVICE TO XINETD**

Type this in a terminal:

```
sudo vi /etc/xinetd.d/Xvnc
```

Enter this in to the new file:

```

Service Xvnc
{
type = UNLISTED
disable = no
socket_type = stream
protocol = tcp
wait = yes
user = root
server = /usr/bin/Xvnc
server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
port = 5901
}

```

To ensure that your font path (-fp) is correct you can use:

```
xset q
```
[B]
note: Doesn't work under SSH[/B]

I recommend leaving all of that code alone, but you can safely change the 1024x768 to be a bigger or smaller resolution for your Xvnc window, depending on what you want. You can also change the depth, but understand that increasing the depth bits will cause more bandwidth to be used over your network, which could slow down your VNC experience considerably.

**4. Edit /root/.vnc/xstartup with correct parameters for KDE,**

```
sudo vi /root/.vnc/xstartup 
```

 so the file looks like this

```
#!/bin/sh
# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc


[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
startkde &

```

**5. RESTART XINETD**

If the following code does not work, try rebooting:

```

sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo /etc/init.d/xinetd start

```

Don't worry if you see a message like "Xvnc: no process killed". This just means there was no open, active session of VNC running at the time. This is expected and is normal.


**6. TEST**

If you followed all of the above steps correctly, you should now be able to test your VNC server. Type the following in a terminal:
Code:

vncviewer localhost:1

You should be prompted for the VNC password, and then see the KDM login screen where you can login and start a new X session. If that works, you can now go ahead and try to connect from remote machine using your favorite VNC client (remember to first close the local vncviewer we started above). Remember to use the VNC server machine's domain name or IP address, followed by :1 (e.g. 192.168.0.100:1). If connecting locally as shown above works, but connecting remotely fails, then this means you have a problem with a firewall which is blocking some ports. See the notes below about how to deal with that.

Note about ports: The VNC server set up as shown uses TCP port 5901. If you are using firewall software (e.g. firestarter) on that machine, you need to allow incoming connections on this port. If you are using a router which assigns your machine a private address (e.g. 192.168.0.100) which is not accessible from the internet, then you need to forward TCP port 5901 from the router to this machine.

Note about security: This setup allows any user to start an X-session remotely by logging in using his regular password (after starting the VNC connection using the VNC password), so if the user disconnects without logging out, any other user which knows the VNC password can connect afterwards and resume the same session that the first user started. So if you do not want to log out before disconnecting, it's advisable to at least lock your VNC X-session screen. Also note that while a remote user is connected thru VNC, no other connection will be accepted. An idle VNC client will be disconnected after one hour, but this can be changed by using the "-IdleTimeout" option in the server_args line in /etc/xinetd.d/Xvnc. For example, you can add "-IdleTimeout 300" to change it to 5 minutes.

---

### Post by carpman on 2010-07-26
Anyone have this working in lucid kubuntu?

as user i get fail with

```

vncviewer localhost:1

VNC Viewer Free Edition 4.1.1 for X - built Apr  9 2010 18:41:55
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Mon Jul 26 20:18:13 2010
 CConn:       connected to host localhost port 5901

Mon Jul 26 20:18:14 2010
 main:        read: Connection reset by peer (104)


```

as root

```

root@prospero:/home/michael/.ssh# /usr/bin/Xvnc :2 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd

Xvnc Free Edition 4.1.1 - built Apr  9 2010 18:47:36
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc


Mon Jul 26 20:14:07 2010
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5902
 vncext:      created VNC server for screen 0


```


what i can see on root test is it looking for connection on port 5902 but in Xvnc config file it is set to 5901?


cheers

---

