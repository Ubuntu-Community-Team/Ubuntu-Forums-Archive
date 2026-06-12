---
title: "HOWTO: Setup vncserver + gdm on Ubuntu 8.04 Desktop"
date: 2008-05-15
forum: Outdated Tutorials &amp; Tips
---

### Post by kcnnc on 2008-05-15
Much of the information comes from this threads  [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402) ```

```and [http://ubuntuforums.org/showthread.php?t=191564](http://ubuntuforums.org/showthread.php?t=191564) and links in the threads. However the threads were started since 2006 and many pages long. After spending a few days digging through the information and links, I hope this information will save you time if you are setting up vncserver and gdm on 8.04.

The setup was done almost immediately after a fresh installation of 8.04 desktop on our office internal network.

**Objective:**
To have vncserver setup with gdm on the host so that a remote vnc connection to it will be greeted with a gdm login screen for the user to login.


Clarification of terms used:
Host - refers to the PC you are trying to install vncserver on.
Remote - the PC that is going to connect to the host

**1. Get required packages installed**
On the host, run
```
sudo apt-get install vnc4server xinetd
```

Being a server guy, I prefer to ssh into the host and do all the work, so I also 
```
sudo apt-get install openssh-server
```
This way I can directly test the vnc by using vncclient on my remote desktop to the host.
Of course if you have only a host PC, then you may also need a vncclient to test it.

**2. Enable XDMCP**
This is the part that is responsible for bring up the gdm login.

```
sudo vi /etc/gdm/gdm.conf
```

Uncomment this line
```
RemoteGreeter=/usr/lib/gdm/gdmlogin
```

Enable xdmcp, look for [xdmcp] and change Enable to true.
```
[xdmcp]
Enable=true

```

Restart gdm,
```
sudo /etc/init.d/gdm restart
```

**3. Setup xinetd**
Create a new service file for xinetd
```
sudo vi /etc/xinetd.d/Xvnc
```
(vi is of course one of many editors you can use)

Paste the following into the file and save:
```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = no
        user = nobody
        only_from = localhost
        server = /usr/bin/Xvnc
        server_args = -inetd -query localhost -geometry 1024x768  -depth 16 -cc 3 -once -SecurityTypes=none -extension XFIXES
        port = 5901
}
```

Restart xinetd
```
sudo  /etc/init.d/xinetd restart
```

**4. Connect from remote**
Because I added *only_from = localhost* in /etc/xinetd.d/Xvnc above, I will need to ssh tunnel and forward my remote port (see term clarification above, as this is actually my local PC that I working from) to the host (this is the 'remote' where vncserver is being installed). If you do not need this step (why not?), just remove the line.

I use putty on Windows so just go to 
Connections >SSH >Tunnels
Source Port: 5901
Destination: localhost:5901
Add
Then establish a normal ssh connection to the host or use my existing ssh connection.

This link might be helpful for those using other clients [https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

I use UltraVNC, so this is what I do:
Open Viewer
VNC Server: localhost:5901
Connect

**5. Done**
The vnc viewer should open up and a gdm login screen presented (with a Debian logo).
Enter your username and password. That's it.


Hopefully this do not generate 45+9 pages of discussion.

[COLOR="Navy"]Update :[/COLOR]
[How to connect with an Ubuntu remote using vinagre (Ubuntu's default vnc client) through an ssh tunnel]("http://ubuntuforums.org/showthread.php?t=795036&page=2#12")

---

### Post by KubuntuKilledMe on 2008-05-16
Some notes on using this with kdm would be great. I guess i'll have to dig in those threads you found.

---

### Post by kcnnc on 2008-05-19
I have no experience with kdm. Presumably step 2 (Enable XDMCP) is the only point to focus attention on.

---

### Post by tmaleshafske on 2008-05-19
Great how to works perfectly.  
Question though how do you make it work to have another remote session on 5902.  Which would truely give you multiple remote sessions?

---

### Post by geezerone on 2008-05-19
Thanks for that, nice concise write-up. :)

---

### Post by kcnnc on 2008-05-20
> **tmaleshafske said:**
> Question though how do you make it work to have another remote session on 5902.  Which would truely give you multiple remote sessions?

Just open another vnc connection to the same port.
It works ... I just did it on my desktop.

---

### Post by geezerone on 2008-05-21
What about getting privileges to perform tasks such as Shutdown from the power button icon. Do changes just have to be made under the login window preferences  to allow remote connections admin rights or another way?

TIA

---

### Post by kcnnc on 2008-05-22
> **geezerone said:**
> What about getting privileges to perform tasks such as Shutdown from the power button icon. Do changes just have to be made under the login window preferences  to allow remote connections admin rights or another way?

In my case I don't have a need for those so I don't ready know how to do it. Maybe someone has an idea?

---

### Post by iCara on 2008-05-22
Worked perfectly for me on 8.04 desktop (not fresh install, upgraded from 7.10).

Thanks!

---

### Post by trdc on 2008-05-22
Very nice work. I spent a couple hours trying to get this to work using those guides you mentioned, but I could never got the login screen to come up. Your guide worked perfectly though.

---

### Post by geezerone on 2008-05-22
> **kcnnc said:**
> In my case I don't have a need for those so I don't ready know how to do it. Maybe someone has an idea?

Thanks for replying. I know I can ```
sudo shutdown now -P
``` from terminal or create launcher, to shutdown the box but maybe it is because I am logging on twice as the same user? The remote unit auto-logins to allow wireless to come up and thus my remote connection to connect as I am using this remote unit as a download file server.

---

### Post by Rigrig on 2008-05-31
Thanks you for this guide, finally got this working thanks to you.

Something that might be usefull to add:

**How to connect with an Ubuntu remote using vinagre (Ubuntu's default vnc client) through an ssh tunnel:**

Make sure the right packages are installed on the remote: (Ubuntu should already have vinagre installed by default)
```
sudo apt-get install openssh-client vinagre
```

To login through an ssh tunnel:
```
ssh -fNT *user*@*hostname* -L 5900:127.0.0.1:5901 && vinagre localhost:5900 && ps -AO pid,command | grep 'ssh -fNT .*@.* -L 5900:127.0.0.1:5901' | sed 's/^[ ]*//' | cut -d' ' -f1 | xargs kill

```
Replace *user* and *hostname* with the user name and address used to login.

This will start ssh, which will prompt you for your password, and then forward port 5900 to the host.
Then it starts vinagre on the forwarded port.
When you close vinagre the ssh tunnel is closed (the part from *&& ps* to the end is to find the tunneling ssh process, then kill it. There's probably some much simpler way to do this that I missed)
You could also remove the end of the line, starting from *&& ps -AO* to leave the tunnel open, then you can always reconnect by just opening vinagre (in the menu: 'Internet' > 'Remote Desktop Viewer') and connecting to localhost on port 5900.

Because its forwarding port 5900 to 5901, this will also work if you try it out on the same machine as you are running the server.

---

### Post by XekaLula on 2008-06-01
I tried the how-to on a new 8.04 installation.
I must be really close here but for some reason I don't see the login screen, only a gray background with a big X cursor. 

Does anyone have an idea what I am doing wrong?

Thanks,
Lu

---

### Post by cyboc on 2008-06-04
Thanks for this HOWTO. It mostly works but one problem is that after I login, I get this error message:

```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

GNOME will still try to restart the Settings Daemon next time you log in.
```

Any suggestions on how to fix that error?

Some more questions:
[LIST]
[*]Would this HOWTO also work with tightvncserver instead of vnc4server?
[*]Should I uninstall the vino VNC server?
[/LIST]

Cheers

---

### Post by geezerone on 2008-06-04
The last page in **[COLOR=Blue][THIS]("http://ubuntuforums.org/showthread.php?t=577946&page=3")[/COLOR]** particular post may be of interest with regards to your Gnome error messages.

---

### Post by cyboc on 2008-06-05
geezerone, thanks for the suggestion. Unfortunately, it doesn't fix the error message for me. Note that I ONLY get the error message when I login via VNC. I do NOT get the error message when I login at the console.

---

### Post by geezerone on 2008-06-05
I found [COLOR=Red]**[THIS]("http://ubuntuforums.org/showthread.php?t=333738&highlight=error+starting+GNOME+Settings+Daemon+vnc")**[/COLOR] post also which looks like others had the same problem but no solution to that post anyhow. On page 1 of this topic [This]("https://help.ubuntu.com/community/VNCOverSSH") is regarding VNC/SSH in general.

Do you get this problem if you create a different user and login as that via VNC?

---

### Post by dylansimpson on 2008-06-05
Thanks worked great for me.

However how would one keep the session alive so that you could continue to run programs on the remote machine while closing your VNC viewer?

---

### Post by pumax84 on 2008-06-10
Hi all... I'm italian, so sorry for my bad english! :P

It worked for me, but i have a problem in vnc session: Gnome theme "switching"... Why? Can you help me?

Thanks,
pumax84

---

### Post by Amannim on 2008-06-10
```

service xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1216x960 -depth 24 -once -fp /usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/,/usr/share/fonts/X11/encodings/,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/util/ passwordFile=/home/adam/.vnc/passwd -extension XFIXES -desktop WindowName
        port = 5901
}

```

Here's a copy of the xinetd config I'm using for resumable sessions in 8.04 /w VNC. 

I had to kill my .gconf folder in order for everything to work after upgrading from 7.10. Kind of bummed about that, but after logging in through gdm the vnc server would segfault and throw me out. Creating a new user and logging in as them worked fine. Tried my best to reset everything to default but I just wasn't getting it all. 

Both the new test account and my personal account I get the gnome-settings warning box, but frankly I'd take that message over the system not working. :)

---

### Post by kcnnc on 2008-06-18
Catching up on the reply ...

Rigrig, 
Updated the additional in the main text.

XekaLula,
Perhaps check your gdm.conf to see if you have all the changes. Uncomment the line etc.

cyboc,
I have no idea about the error and have not try tightvnc. Would assume that tightvnc would be pretty similar.
You don't have to remove vino. It is used for remote desktop for the user, a somewhat different purpose.

dylansimpson,
#20 should be the solution.
Basically set **wait = yes**
See *man xinetd* somewhere near the end about this.

pumax84,
Sorry don't quite understand the problem here.

---

### Post by Pjukern on 2008-06-24
Im having a problems connecting with vnc after i followed this guide.

In the first place i could not login with vns unless i logged in at the console first. This server is headless and has only power and ethernet connected. So I need to be able to log in with vnc after reboot without having to connect a monitor/keyboard/mouse.

I followed this guide, but i was doing thorugh vns, and when i came to the point where i should restart GDM i lost the connection.
I did the last steps through ssh, but still cant log in with vnc..

---

### Post by geezerone on 2008-06-24
If you have an ethernet connection you will be able to setup autologin (System > Administration > Login Window > Security ; then tick "Enable automatic login" for your desired username. Test this before moving to location without kbd/mouse/screen.

This may work with wireless connection but I found that the wireless key needed to be unlocked and hence a keyboard attached which defeats the whole idea.

HTH

---

### Post by Pjukern on 2008-06-25
> **geezerone said:**
> If you have an ethernet connection you will be able to setup autologin (System > Administration > Login Window > Security ; then tick "Enable automatic login" for your desired username. Test this before moving to location without kbd/mouse/screen.

This may work with wireless connection but I found that the wireless key needed to be unlocked and hence a keyboard attached which defeats the whole idea.

HTH

Is there a way to enable this through ssh?

---

### Post by geezerone on 2008-06-25
You ssh first to create your secure tunnel and then vnc over this. You need to configure auto-login first with kbd/mouse attached and then test. Once configured, remove mouse/kdb and this should work ok.

---

### Post by Pjukern on 2008-06-25
> **geezerone said:**
> You ssh first to create your secure tunnel and then vnc over this. You need to configure auto-login first with kbd/mouse attached and then test. Once configured, remove mouse/kdb and this should work ok.

I actually got it figured out.
In /etc/gdm/gdm.conf i just replaced "autologin=false" with "autologin=true"
Also entered my username in the line below, autologinuser=username
then i restarted GDM.

I can now connect with vnc. Didnt have to open a tunnel with ssh.

---

### Post by geezerone on 2008-06-25
Glad it is sorted. I understand the OP was setup with experience of servers in a workplace and using ssh is just a more secure way of moving data.

---

### Post by Pjukern on 2008-06-25
> **geezerone said:**
> Glad it is sorted. I understand the OP was setup with experience of servers in a workplace and using ssh is just a more secure way of moving data.

Yeah i understood that, and I totally agree with that solution, it would also just require you to open up for ssh in firewall, you wouldnt need to open for 5900/5901.

I just gave it a second try, i added the "only_from = localhost" in the  /etc/xinetd.d/Xvnc, but im still able to log in with vnc without having a tunell in putty..

will look more into this. maybe I need a restart.

edit: figured it out, i wasnt using localhost in vnc.. i was still using my servers ip (knocks my head in table)

Anyway forgot to mention, great guide! even me, a totally newbie got this up and working (yeah except for the vnc/ssh) 
now i can log into the box after powerloss etc.. without having to log on to the console first.

---

### Post by megamaced on 2008-06-26
Is there a way to automatically disable all GNOME theming when connecting via VNC?

Sometimes the GNOME theme just "crashes" anyway when using TightVNC and displays a very basic looking GNOME. This is better for me as it makes my desktop much faster to use over WAN.

---

### Post by drewster1829 on 2008-06-28
Great write up!  I had to find a way to get my wifi card enabled without network manager (so it would have network access before login), [here, at the bottom]("http://ubuntuforums.org/archive/index.php/t-598880.html"), and it works (but then it makes network manager worthless, which is fine with me).

I also had to do some voodoo to get vnc4server to work properly (editing the font paths in /etc/vnc.conf), and I followed this HowTo to the T...but I still am having the problem XekaLula was having...all I get when I log into the other machine is a blank screen with an X. (I'm suprised I was able to forward the port to get the SSH tunneling to work...I tried it both with and without tunneling with no problems.  I only discovered SSH and it's wonderful usefulness yesterday :))

I'm almost certain it's an XDMCP problem (and, yes, I *did* edit /etc/gdm/gdm.conf, removing the comment mark before "Remote Greeter=/usr/lib/gdm/gdmlogin" and changing Enable to "true" in the [xdmcp] section. Of course, I've restarted gdm and xinetd (on the server) about a thousand times trying to get all of the above to work, and even rebooted the server a few times, too, for good measure.

By going to the gdm login window in the client machine, and attempting to use the GUI to login to the server machine with XDMCP results in a quit network search, with no xdmcp hosts found.  Trying to type in either the IP address or the host name also doesn't work (yes, both machines are on the same LAN, both Wifi connections).  I remember having trouble getting XDMCP to work in Gutsy, and I just gave up.  Yes, Hardy is on both the client and the server, and the server still gives me the grey screen with the black X cursor, and nothing else (when it should be the XDMCP login screen).  What am I doing wrong?

---

### Post by brttdls on 2008-07-02
i can login via ssh and vnc with no problem, but when the welcome window opens, it is a grey screen with a command prompt. do you have any ideas?

---

### Post by pmsumner on 2008-07-02
Thank you!  This worked for me grand.  First time I got the grey screen, until I logged out of the SSH session and logged back in.  Now working fine (but dog slow compared to the Vino setup..).

---

### Post by dtown240 on 2008-07-02
To the OP, Thank you

---

### Post by kcnnc on 2008-07-04
To those that get the gray screen, I really do not know how to fix that.

I did get it while following the other howto in the forum. Eventually I figured out the right combination, did a clean install, wrote this howto and use it for all my desktop setup ever since.

Perhaps it was something left over from configurations you had tried. The most likely places to look are /etc/gdm/gdm.conf and *server_args =* part in /etc/xinetd.d/Xvnc. Try remove those vnc setup directories in the user directory that was created if you followed some of the other howto, I don't think they are needed.

---

### Post by coldfusion212 on 2008-07-07
> **pumax84 said:**
> Hi all... I'm italian, so sorry for my bad english! :P

It worked for me, but i have a problem in vnc session: Gnome theme "switching"... Why? Can you help me?

Thanks,
pumax84

Hello all, new to the forums here.

I have just followed kcnnc's instructions for setting up a gnome vnc session (thanks!) and I am also experiencing what pumax84 refers to as "theme switching".

After logging in to the remote session or opening any applications in the session the gnome theme will jump to the default un-themed windows and bars at which point it re-themes all of the open windows and bars. I have seen this happen while scrolling through a file browser window as well. I have tried removing the gnome2

Any help or advice in fixing this little issue would be much appreciated, thanks!

EDIT: As I was typing this the gnome settings daemon crashed, reporting that it had restarted too many times. I will search on this topic and see if I can find a solution.

EDIT2: It looks like there is an issue with the gnome-settings-daemon keyboard.
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245)

---

### Post by reviver on 2008-07-08
I was also getting the dead, grey X window when I would try to connect even though I followed the guide completely.  What I figured out is there was one more line that needed to be uncommented in /etc/gdm/gdm.conf for it to work for me.  Right under the ```
[xdmcp]
Enable=true
```
line, there's another line that might need to be uncommented.  I uncommented ```
HonorIndirect=true
```
restarted gdm and then tried to connect again.  Voila, no grey screen, just gdm ready and waiting for login info!  =]

---

### Post by kcnnc on 2008-07-09
> **reviver said:**
> line, there's another line that might need to be uncommented.  I uncommented ```
HonorIndirect=true
```
restarted gdm and then tried to connect again.  Voila, no grey screen, just gdm ready and waiting for login info!  =]

I am no expert at gdm so I have no idea what that line does. My configuration has it commented out.

This page might be help for those that are tuning the configuration: [http://www.gnome.org/projects/gdm/docs/2.20/configuration.html#xdmcpsection](http://www.gnome.org/projects/gdm/docs/2.20/configuration.html#xdmcpsection)

---

### Post by mikeduffy13 on 2008-07-09
thanks for the tut.  i have a slightly different problem.  I have the ssh tunnel setup correctly, and followed all of the other instructions, but when I use vncviewer to connect to localhost:5901, I get a quick splash of an X11 terminal and then it closes right away...

HOWEVER - even if I first log into Ubuntu w/ kb/mouse and then VNC in from a client with localhost:5901 I still get the X11 splash.  When I am logged in, I can just VNC with the servers IP address so I assume that works just because XDCMP or whatever is enabled.

EDIT: when not logged in via console, and I use VNC over SSH tunnel with xx.xx.xx.xx :localhost:5901 --> I get "unable to connect to host: Connection refused (10061)".  I should also mention that I am using 7.10...maybe I need to upgrade?

---

### Post by kcnnc on 2008-07-10
mikeduffy13:
Maybe take a look at this and the few post above it
[http://ubuntuforums.org/showpost.php?p=5258830&postcount=26](http://ubuntuforums.org/showpost.php?p=5258830&postcount=26)

---

### Post by musides on 2008-07-30
> **cyboc said:**
> 

```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

GNOME will still try to restart the Settings Daemon next time you log in.
```

Any suggestions on how to fix that error?


Cheers

I found a workaround at [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245)
Disabling the "keyboard" and "mouse" g-s-d plugin solved my problem.

---

### Post by martijntje on 2008-12-31
I followed this guide, and also have the problem with an empty screen with the X cursor. I even tried to enable HonorIndirect without any luck.

All the necessary changes are made, it just won't work. Does anybody here have a clue on how to fix this?

---

### Post by syborfical on 2009-02-02
Ive done this i just get this!! its really annoying.. 

Because VNC was working now its not ... 

[IMG]http://members.wideband.net.au/syborfical/Xvnc.png[/IMG]

---

### Post by adski-tux on 2009-02-14
I cant remember where I found this fix but it soved my grey screen problem. Took me hours of trawling to find it.

Edit /etc/modprobe.d/aliases and find the line containing

**alias net-pf-10 ipv6**

and replace **ipv6** with **off**. 
After reboot everything should work!


:guitar:

Hope this helps

---

### Post by vinhomn on 2009-02-20
> **syborfical said:**
> Ive done this i just get this!! its really annoying.. 

Because VNC was working now its not ... 

[IMG]http://members.wideband.net.au/syborfical/Xvnc.png[/IMG]

I have a problem like you, I tried to fix this by:

Edit /etc/gdm/gdm.conf-custom
```
sudo vim /etc/gdm/gdm.conf-custom
```
(try another editor if you can't use the vim editor)

find: 
```
[daemon]
```
add after:
```
RemoteGreeter=/usr/lib/gdm/gdmgreeter
```

find: 
```
[security]
```
add after:
```
AllowRemoteRoot=true
AllowRoot=true
```

find: 
```
[xdmcp]
```
add after:
```
Enable=true
```

restart gdm
```
sudo /etc/init.d/gdm restart
```

Hope this helps :)
Sorry for my bad English :P.

---

### Post by composites on 2009-03-07
> **dylansimpson said:**
> Thanks worked great for me.

However how would one keep the session alive so that you could continue to run programs on the remote machine while closing your VNC viewer?

> **kcnnc said:**
> 
dylansimpson,
#20 should be the solution.
Basically set **wait = yes**
See *man xinetd* somewhere near the end about this.

Thanks for the tutorial. Everything has worked great, expect I wanted to have the session I started to be resumable, so I could start a session, start a couple programs, close vnc, then later open vnc and manage the programs.

However, with **wait = yes** I am not able to open vnc at all. It just gives the error "The connection closed unexpectedly. Do you wish to attempt to reconnect to localhost:5901". If I change it back to **wait = no** then I am able to load vnc again (but session aren't resumable.)

---

### Post by JohnnyVW on 2009-05-03
I had the same gray screen or connection refused when trying to connect to my Xubuntu laptop from my Ubuntu desktop.

I undid everything in this how-to and successfully did this:

[http://www.vincentkong.com/2008/02/remote-desktop-on-xubuntu/](http://www.vincentkong.com/2008/02/remote-desktop-on-xubuntu/)

Hope this helps out a few gray-screen victims!

---

### Post by MrSalti on 2009-05-08
As far as the "Theme Switching", or more accurately the Gnome settings-daemon recursively crashing then giving up, I have stumbled upon this page.

[http://www.francescosantini.com/index.php?page=linux&lang=en](http://www.francescosantini.com/index.php?page=linux&lang=en)

Will let you know what happens.

---

### Post by piyushj on 2009-05-15
i don't know if it will help any1--i got it working in 8.04.2 ubuntu with latest updates.

install vnc4server
make .vnc/xstartup file as
---
unset SESSION_MANAGER
exec sh /etc/X11/xinit/xinitrc
---
note the additional 'sh' above
------
run this
sudo mkdir /usr/X11R6/lib/X11
sudo mkdir /usr/X11R6/lib/X11/lib
sudo ln -s /usr/share/fonts/X11 /usr/X11R6/lib/X11/fonts
-----
u are done !!
set vncpasswd first and u r done !!

---

### Post by Crugster on 2009-08-01
> **coldfusion212 said:**
> ... I am also experiencing what pumax84 refers to as "theme switching".

After logging in to the remote session or opening any applications in the session the gnome theme will jump to the default un-themed windows and bars at which point it re-themes all of the open windows and bars. I have seen this happen while scrolling through a file browser window as well. I have tried removing the gnome2

Any help or advice in fixing this little issue would be much appreciated, thanks!

EDIT: As I was typing this the gnome settings daemon crashed, reporting that it had restarted too many times. I will search on this topic and see if I can find a solution.

EDIT2: It looks like there is an issue with the gnome-settings-daemon keyboard.
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245)

I am experiencing the theme-switching as well and have been googling for 3 days now and this was the best related page/post (however also without a solution) I could find thus far.  I was wondering (seeing it has been a year and I am on 9.04) whether this is solved yet, or if someone found a work around. Thanks in advance guys!

Just found this url stating it is probably a bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245)

Anyone able to verify / give advice anyway?

---

### Post by azzopardim on 2009-08-05
Running Ubuntu 9.04 and I have the same problem of not seeing the gdm but only get the grey X11 screen. Tried the configuration mentioned for gm.conf and Xvnc. Can anybody help ?

gdm.conf

[daemon]
RemoteGreeter=/usr/lib/gdm/gdmlogin

[xdmcp]
Enable=true

[security]
AllowRoot=true
AllowRemoteRoot=true

Xvnc
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = no
        user = nobody
        server = /usr/bin/Xvnc
        server_args = -inetd -query localhost -geometry 1024x768  -depth 16 -cc 3 -once -SecurityTypes=none -extension XFIXES
        port = 5901
}

---

### Post by SeetheZA on 2009-08-06
According to a post over at [https://answers.launchpad.net/ubuntu/+source/gdm/+question/62380](https://answers.launchpad.net/ubuntu/+source/gdm/+question/62380) there might be a bug in Jaunty's (9.04) IPV6 code that is causing Xvnc to not launch GDM.

After following this guide I was also experiencing the problem on 9.04 (64 bit version), whereby I could open a VNC session but just got the grey screen with an X cursor. Changing -query localhost in the server_args parameter of /etc/xinet.d/Xvnc to -query 127.0.0.1 as recommended in the referenced post did the trick for me.

The full line that's working for me is:
server_args = -inetd -query 127.0.0.1 -geometry 1024x768  -depth 16 -cc 3 -once -SecurityTypes=none -extension XFIXES

Finding that fix is four hours of my life that I'll never get back - hope this helps you!

---

### Post by Crugster on 2009-08-13
> **azzopardim said:**
> Running Ubuntu 9.04 and I have the same problem of not seeing the gdm but only get the grey X11 screen. Tried the configuration mentioned for gm.conf and Xvnc. Can anybody help ?
     

**@ Azzopardim**: If you DO get an X-server (gray with the old style mous-pointer) you might want to adding the following (for gnome) to the top of your xstartup file:

  ```
unset SESSION_MANAGER
exec sh /etc/X11/xinit/xinitrc
```Note the sh, btw! However, I (as well as others) am experiencing theme-switching. The theme-chooser will very shortly change the theme, but when I stop using the chooser itself it refers back to the default icon/theme appearance. Anyone got an idea/link? EDIT: Apperantly this is a bug in 9.04

---

### Post by jeffmings on 2009-08-17
tightvncserver problems with Ubuntu server 8.04

Hi!

    Just wanted to add that tightvncserver has some sort of character encoding problem with 8.04 LTS.  As stated earlier in this thread, use vnc4server instead.
    I.e., if your keyboard input is received as the wrong characters by your vnc server, you may have installed tightvncserver instead of vnc4server.
    E.g., if you hit the keys asdf and you see abhk or something similar, be sure to use the RealVNC variant of the VNC server, which is labelled vnc4server in most cases.
    This information would have saved me a lot of trouble, and I just wanted to make sure other users know about it.

Aloha,
-Jeff Mings

---

### Post by the_one(2) on 2009-09-02
I got the grey screen as well. I fixed it by making the changes in /etc/gdm/gdm.conf-custom instead of /etc/gdm/gdm.conf

---

### Post by PhDLinux on 2010-01-15
I'm running Ubuntu 9.10. I just ran into the "grey screen of X" for the first time. Until I ran update-manager this evening and accepted all its suggestions, my setup had been working fine.

My best guess at a diagnosis is that the file named /usr/lib/gdm/gdmgreeter does not exist on my system. So if gdm goes looking for one, it will fail and a bare X screen is a likely consequence. After investigating the contents of /usr/lib/gdm, I directed gdm to use a greeter that *does* exist. This happens in the gdm configuration file. I don't know where the main one is kept ... but it is certainly not in /etc/gdm/gdm.conf. That file is not present in my nearly-default installation. However, I do have a file named /etc/gdm/custom.conf. I arranged it to contain just these four lines:
```
[xdmcp]
Enable=true
[daemon]
RemoteGreeter=/usr/lib/gdm/gdm-simple-greeter

```
(Earlier posts have recommended adding some settings under the [security] heading that actually *reduce* the system's security. I'm glad everything works without them!)

For completeness/reference, here is what I have in /etc/xinetd.d/vnc. Another user suggested explicitly writing the numbers 127.0.0.1 instead of the name localhost. I tried this while groping around, but now I'm not certain whether it was this or the gdmgreeter symlink that solved my problem.
```
# Start a VNC connection with gdm login prompt: 1280x1024, 24bpp.
service 1280x1024-24
{
	type		= UNLISTED
	port		= 5901
	socket_type     = stream
	protocol        = tcp
	wait            = no
	user            = nobody
	server          = /usr/bin/Xvnc
	server_args     = -inetd -noreset -SecurityTypes None -once -extension XFIXES -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/75dpi -co /usr/share/X11/rgb -geometry 1263x1024 -depth 24 -query 127.0.0.1
}
```
I'm not sure if my last step is truly needed, but I also added one line to mention this service in my file /etc/services:
```
1280x1024-24	5901/tcp			# VNC Service
```
I hope this might help somebody else fighting the grey screen of X.

---

### Post by poolecl on 2010-01-17
> **PhDLinux said:**
>  Another user suggested explicitly writing the numbers 127.0.0.1 instead of the name localhost. I tried this while groping around, but now I'm not certain whether it was this or the gdmgreeter symlink that solved my problem.

It was the localhost name that was the problem.  I have just been fighting with this for the past 6 hours.  I finally got it to work by changing localhost to 127.0.0.1.  (Found it by accident when Xnest-ing in from a different machine would work when localhost-ing would not!)  So for some reason the localhost name quit working.  The error logs were full of errors like 

```
Jan 17 18:11:18 MYCOMPUTER gdm-simple-slave[5161]: WARNING: Unable to connect to display ::1:9
```and /var/run/gdm was filling up with auth-for-gdm-xxxxxx directories.

 It looks like something in the recent updates was not allowing X communications without an explicit IP address.  Anyone have any clue which update?  (I hate X sometimes)

---

### Post by allanduym on 2010-07-28
I need help, I am working in ubuntu 10.04,but there is no configure file on the dirctory /etc/gdm/gdm.conf,how can I do ? and I need more message about how to configure vnc4server on ubuntu10.04 ,such as vieweronly,alwaysshared,client login automaticly, how can I write this option to the configure file, I means I dont know "value"and "values" exactly, thanks for help me !

---

### Post by xp_newbie on 2010-11-11
Hmmm... this *almost* works. By "almost" I mean the remote desktop appears briefly, then causes my vnc client (RealVNC 4.1) to close immediately.

Any idea what could be the reason and how to fix this?

If this could be of any relevance, I looked at my remote server logs and founds this:

[QUOTE= /var/log/daemon.log]Nov 11 15:17:04 myubuntu xinetd[6730]: warning: can't get client address: Transport endpoint is not connected[/QUOTE]

and:
[QUOTE= /var/log/gdm/:0.log](==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 11 15:31:57 2010
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ramdac" already built-in
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
SetGrabKeysState - disabled
SetGrabKeysState - enabled
[/QUOTE]

Thanks. :popcorn:

---

### Post by xp_newbie on 2010-11-11
> **xp_newbie said:**
> Hmmm... this *almost* works. By "almost" I mean the remote desktop appears briefly, then causes my vnc client (RealVNC 4.1) to close immediately.

Any idea what could be the reason and how to fix this?
I fixed it.

All I did was replace the line:
```
server_args = -inetd :1 -query localhost -geometry 1920x1080 -depth 24 -once -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd

```
With:
```
server_args = -inetd -query localhost -geometry 1920x1080  -depth 24 -cc 3 -once -SecurityTypes=none -extension XFIXES
```
Frankly, I don't really understand why this works because I don't have the time right now to delve into this. It just works (with the annoying side-effect of starting a new Gnome desktop session for every VNC run, when I really need only one)

---

### Post by Dr.iCe on 2011-07-24
using Ubuntu 10.04 the GDM config file is not there, anyone know where it is or how to set this up correctly?

---

