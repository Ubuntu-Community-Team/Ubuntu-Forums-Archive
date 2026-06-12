---
title: "Set up VNC server with resumable sessions - KUBUNTU UPDATED VERSION"
date: 2009-02-23
forum: Outdated Tutorials &amp; Tips
---

### Post by mexus on 2009-02-23
Based on: 
[http://ubuntuforums.org/showthread.php?t=259448](http://ubuntuforums.org/showthread.php?t=259448)
[B]

I have modified the previous how-to so it works for Kubuntu 8.10 and Kubuntu 9.04 with KDE 4.X
Required packages:[/B]

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
server_args = -inetd :1 -query [COLOR="Red"]127.0.0.1[/COLOR] -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
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

### Post by maheiz on 2009-03-10
Thanks mexus, this works great. How can I allow multiple viewers to connect (-alwaysshared) ? I am aware that this is a security concern.

---

### Post by maheiz on 2009-03-10
oops, I just notice the -NeverShared parameter in your sample Xvnc config. Sharing works if I switch to -AlwaysShared

---

### Post by drugusv on 2009-03-17
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



hi, one question, what mean "user = root", is this default user ho can log in kde? if i use an another user in kde, for example "dexter", then i connect in login manager, i choose my account "dexter" and type the password, and press enter, but!!! is opening not my session with my opened doccuments and and programs, i view an clear desktop :), how i can acces "dexter"'s session? thanks

---

### Post by MrNet on 2009-07-10
Take care: In some cases, "-query localhost" doesn't work properly and leads to a grey desktop. It can be solved by setting the server arg to "-query 127.0.0.1"!

---

### Post by IgnorantGuru on 2009-08-14
Thanks for this update!

Mostly it worked.  I did indeed get a gray screen until I changed localhost to 127.0.0.1 (which wasn't the case in KDE3).  However, the fonts don't look right - they look like X fonts, not KDE4.  Is this the best it can do?  And the graphics are far from clean - the taskbar is scrambled and mostly unreadable, and there are other distortions in the windows.  I am using kubuntu karmic alpha4.

Increasing the depth to 24 didn't seem to do anything.  Increasing it to 32 causes a completely black window.

Ironically, the desktop background image is very clear (air).

I used vnc4server in KDE3 and it was much cleaner looking.  Any suggestions?

Edit: Also, there was no /root/.vnc/xstartup file (or folder), but I created it.  It appears it's not needed (works without it).  But I also don't have a /etc/vnc folder, which xstartup file seems to reference.  ???

---

### Post by myjess on 2010-03-11
Someone help please?

Last reply is the same for me on karmic. No /etc/vnc dir. Grey xwindows screen only.

Thank you.

---

### Post by laka77 on 2010-05-04
Great HOWTO, however, I keep getting the following error:

Tue May  4 15:34:51 2010
 CConn:       connected to host localhost port 5901
 main:        read: Connection reset by peer (104)

When I run vnc4server from the command line, I can connect just fine.  Any ideas?

Thanks!

---

