---
title: "HOWTO: x11vnc (vnc for display :0)"
date: 2007-02-16
forum: Outdated Tutorials &amp; Tips
---

### Post by ErikTheRed on 2007-02-16
x11vnc is very similar to vnc, except that it allows you to view display :0, the display that would currently be showing on your monitor if you were sitting at your computer. 

1. Install the package
```
sudo aptitude install x11vnc
```

2. Run the following command
```
ps wwaux | grep auth
```
[INDENT]This command should output something like this:
```
root      3838 10.1  1.7  13308  8840 tty7     Ss+  15:35   2:14 /usr/bin/X -br -nolisten tcp :0 vt7 -auth **/var/run/xauth/A:0-LliKdB**
erik      5156  0.0  0.1   2800   752 pts/0    R+   15:57   0:00 grep auth

```
Note the bolded path after -auth, as you will need this for the next step[/INDENT]

3. Add x11vnc service to xinetd
```
sudo nano /etc/xinetd.d/x11vnc
```

[INDENT]Enter this into the new file:
```
service x11vnc
{
        port            = 5900
        type            = UNLISTED
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/bin/x11vnc
        server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth **/var/run/xauth/A:0-LliKdB** -many -bg
        disable         = no
}
```
Notice the bolded path, this is where you put the path you found in step 2.[/INDENT]

4. Restart xinetd
```
sudo /etc/init.d/xinetd restart
```

5. You can now connect to display :0 from another machine by using a VNC client. For example:
```
sudo vncviewer vnchost:0
```

A lot of this is thanks to Tichondrius' great VNC HOW-TO which is [here]("http://ubuntuforums.org/showthread.php?p=771174"). [His post on using x11vnc]("http://ubuntuforums.org/showpost.php?p=771174&postcount=61") is on page 7 of that thread. In his HOW-TO there was an issue where the connection would drop out whenever you logged in or out, but I believe I have rectified this problem by using the new method to find the path  to use with the -auth option.

Please let me know if there are any problems with this HOW-TO.

---

### Post by krunge on 2007-02-19
Hi,

Newer versions of x11vnc (might not be in ubuntu yet) support automatic
finding of the -auth authority file, and can also find both the DISPLAY and authority
file using unix username and password login.  This is the FINDDISPLAY
stuff here: [http://www.karlrunge.com/x11vnc/faq.html#faq-userlogin]("http://www.karlrunge.com/x11vnc/faq.html#faq-userlogin")

E.g.:

```
server_args     = -inetd -o /var/log/x11vnc.log -svc
```

or -xdmsvc instead of -svc.  The -find option may also be useful here.

---

### Post by benfindlay on 2007-03-14
I have been trying to get this set up, but when I type ```
ps wwaux | grep auth
``` to find the code for the -auth part, it just says > -auth /var/lib/gdm/:0.Xauth

Am I going wrong anywhere obvious?

Cheers

---

### Post by benfindlay on 2007-03-14
Just realised I have only been trying to connect via SSH. Just tried it and it will connect direct, but not through SSH. Any ideas why that is then?

---

### Post by krunge on 2007-03-14
> Am I going wrong anywhere obvious?

No, that looks fine.  /var/lib/gdm/:0.Xauth is where gdm(1) puts the server auth file.  It's nice that the filename doesn't have a random part like the kdm and xdm servers do. Please send your entire /etc/xinetd.d/x11vnc (or equivalent) file.

> Just realised I have only been trying to connect via SSH. Just tried it and it will connect direct, but not through SSH. Any ideas why that is then?


What was the full ssh command you ran, and the vncviewer command you ran?  Do any errors or warnings get printed out (either by ssh, vncviewer, or in the x11vnc log file)?

---

### Post by Al_maverick on 2007-03-14
When xinetd starts I get an error in daemon.log. Any idea what it may be?

> 
Mar 14 21:57:06 maverick xinetd[11740]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.conf] [line=14]
Mar 14 21:57:06 maverick xinetd[11740]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
Mar 14 21:57:06 maverick xinetd[11740]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard] [line=26]
Mar 14 21:57:06 maverick xinetd[11740]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=25]
Mar 14 21:57:06 maverick xinetd[11740]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=26]
Mar 14 21:57:06 maverick xinetd[11740]: Reading included configuration file: /etc/xinetd.d/x11vnc [file=/etc/xinetd.d/x11vnc] [line=28]
Mar 14 21:57:06 maverick xinetd[11740]: removing chargen
Mar 14 21:57:06 maverick xinetd[11740]: removing chargen
Mar 14 21:57:06 maverick xinetd[11740]: removing daytime
Mar 14 21:57:06 maverick xinetd[11740]: removing daytime
Mar 14 21:57:06 maverick xinetd[11740]: removing discard
Mar 14 21:57:06 maverick xinetd[11740]: removing discard
Mar 14 21:57:06 maverick xinetd[11740]: removing echo
Mar 14 21:57:06 maverick xinetd[11740]: removing echo
Mar 14 21:57:06 maverick xinetd[11740]: removing time
Mar 14 21:57:06 maverick xinetd[11740]: removing time
Mar 14 21:57:06 maverick xinetd[11740]: bind failed (Address already in use (errno = 98)). service = x11vnc
Mar 14 21:57:06 maverick xinetd[11740]: Service x11vnc failed to start and is deactivated.
Mar 14 21:57:06 maverick xinetd[11740]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Mar 14 21:57:06 maverick xinetd[11740]: Started working: 0 available services


---

### Post by jpkotta on 2007-03-14
This is what I use to connect to an already running server (on display :0):
```
#!/bin/bash

usage="$0 [user@]remote_host"

if [[ x$1 == x"" ]] ; then
    echo $usage
    exit 1
fi

ssh $1 'x11vnc -localhost -display :0 -scale 4/5 -bg' 
vncviewer -via $1 -encodings 'copyrect tight zrle hextile' localhost:0

```

All you need is X11Forwarding in ssh.

---

### Post by krunge on 2007-03-14
> Mar 14 21:57:06 maverick xinetd[11740]: bind failed (Address already in use (errno = 9 ). service = x11vnc

It looks like something else is already listening on port 5900.

Check 'netstat -ant | grep 5900' output and (perhaps as root) 'lsof -P | grep 5900'

---

### Post by Al_maverick on 2007-03-15
> **krunge said:**
> It looks like something else is already listening on port 5900.

Check 'netstat -ant | grep 5900' output and (perhaps as root) 'lsof -P | grep 5900'

That was it. I dunno why, krfb was still running. I killed it, then inmediately afterwards I restarted xinetd. Now it worked. Thanks a lot!

---

### Post by FlashUK on 2007-03-26
Very useful thread. Been following the steps to get x11vnc working on edgy 6.10 ubuntu.
Managed to get it to work on the end on port 5900 but I'd like to point out a mistake on the karlrunge.com that had me scrathing my head for ages:

> x11vnc -display :0 -auth /var/gdm/:0.Xauth

Please note that ubuntu's gdm is located at **/var/lib/gdm/:0.Xauth**. I missed out the word **lib** when I was writing my xinetd file.
But now it even works on bootup! Thanks very much for sharing this with us :)

Btw, edgy currently uses 0.8.2 of x11vnc.

---

### Post by Jbloudg20 on 2007-03-27
Any reports if this will work for a dual head configuration using FGLRX drivers? I am using the default VINO right now, and we all know how buggy that is.

---

### Post by Ek0nomik on 2007-03-27
Thanks ErikTheRed.  Worked on the first try.  :)

I am using a Radeon 9800 using fglrx drivers in case anyone is wondering.

Cheers!

---

### Post by Jbloudg20 on 2007-03-28
I dont seem to have a /etc/xinetd directory. When I go to create the file as specified, it won't let me saying the directory does not exist. sure enough ls /etc shows there is not xinetd directory. 

I am trying to get this running! Can anyone help?

---

### Post by krunge on 2007-03-28
You probably have a /etc/inetd.conf based inetd.

Here is how I do these this sort of thing on those systems.  Add a single line to that file like this:

```
5900    stream  tcp     nowait  root    /usr/sbin/tcpd /usr/local/bin/x11vnc.sh
```

where, for simplicity, I just put the x11vnc call and its option in the shell script /usr/local/bin/x11vnc.sh

Then something like: /etc/init.d/inetd restart
to restart inetd, and of course if your system filrewall blocks port 5900 you will have to poke a hole in it.

More info: [http://www.karlrunge.com/x11vnc/faq.html#faq-inetd]("http://www.karlrunge.com/x11vnc/faq.html#faq-inetd")

---

### Post by Jbloudg20 on 2007-03-28
I don't have that file either. Should I?

---

### Post by krunge on 2007-03-29
> I don't have that file either. Should I?

If you want to run inetd (you can find manpages and other documention for it on the web) you will need to install some package probably named "inetd" or "xinetd".

In 24 years of using unix I've never seen a machine w/o inetd (except perhaps for some locked down boxes where it was forcibly removed after install), but I guess there is a first time for everything  ;-)

---

### Post by Jbloudg20 on 2007-03-29
Well, I really don't want to go through a thousand hoops to make this work. VINO works right now, albeit very buggy. 

I had kind of thought this would be a fairly simple, install a package, start a service at startup thing. Guess not.

---

### Post by krunge on 2007-03-29
> I had kind of thought this would be a fairly simple, install a package, start a service at startup thing. Guess not.

No, it's pretty easy.  You don't need inetd stuff like the people in this thread are talking about.

You just need to install the x11vnc package (see the beginning of this thread or [http://www.karlrunge.com/x11vnc/bins]("http://www.karlrunge.com/x11vnc/bins")) and
type "x11vnc" in a window or if you ssh in remotely type "x11vnc -display :0" to point it
at the X session display you are logged into.

At that point it is the same service as vino.  If you want it to always be available put it in your gnome or kde "Startup Programs".  You should give it the "-forever" option to keep listening after the first client disconnects.

---

### Post by bdogg64 on 2007-03-30
> **ErikTheRed said:**
> x11vnc is very similar to vnc, except that it allows you to view display :0, the display that would currently be showing on your monitor if you were sitting at your computer. 

1. Install the package
```
sudo aptitude install x11vnc
```

2. Run the following command
```
ps wwaux | grep auth
```
[INDENT]This command should output something like this:
```
root      3838 10.1  1.7  13308  8840 tty7     Ss+  15:35   2:14 /usr/bin/X -br -nolisten tcp :0 vt7 -auth **/var/run/xauth/A:0-LliKdB**
erik      5156  0.0  0.1   2800   752 pts/0    R+   15:57   0:00 grep auth

```
Note the bolded path after -auth, as you will need this for the next step[/INDENT]

3. Add x11vnc service to xinetd
```
sudo nano /etc/xinetd.d/x11vnc
```

[INDENT]Enter this into the new file:
```
service x11vnc
{
        port            = 5900
        type            = UNLISTED
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/bin/x11vnc
        server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth **/var/run/xauth/A:0-LliKdB** -many -bg
        disable         = no
}
```
Notice the bolded path, this is where you put the path you found in step 2.[/INDENT]

4. Restart xinetd
```
sudo /etc/init.d/xinetd restart
```

5. You can now connect to display :0 from another machine by using a VNC client. For example:
```
sudo vncviewer vnchost:0
```

A lot of this is thanks to Tichondrius' great VNC HOW-TO which is [here]("http://ubuntuforums.org/showthread.php?p=771174"). [His post on using x11vnc]("http://ubuntuforums.org/showpost.php?p=771174&postcount=61") is on page 7 of that thread. In his HOW-TO there was an issue where the connection would drop out whenever you logged in or out, but I believe I have rectified this problem by using the new method to find the path  to use with the -auth option.

Please let me know if there are any problems with this HOW-TO.

This is a great HOWTO, but there is one part missing to get it completely working in KDE. 

```
ps wwaux | grep auth
``` 

will return a different file every time you reboot, unless you add the setting in /etc/kde3/kdm/kdmrc under [X-:*-Core]

```
AuthFile=A:0-LliKdB
```

You can change the AuthFile to be something different, just make sure you have the same file in your server_args in your Xvnc services file

I hope this helps someone

B

---

### Post by Gujs on 2007-05-01
Is there a way to automatically lock gnome session when I exit vncviewer? Because I don't want to have accessible session if somebody comes to my computer.

---

### Post by krunge on 2007-05-03
> Is there a way to automatically lock gnome session when I exit vncviewer? Because I don't want to have accessible session if somebody comes to my computer.

For x11vnc see this link:  [http://www.karlrunge.com/x11vnc/faq.html#faq-gone-lock]("http://www.karlrunge.com/x11vnc/faq.html#faq-gone-lock") For example, you supply:

```
x11vnc ... -gone "xlock -mode blank &"
```

or whatever command invokes a screen locker.

---

### Post by jnorth on 2007-05-31
@ErikTheRed - cool guide - but just curious, why run using xinetd?

The method I've been using for some time is detailed here and IMHO *might* be a little easier?

Anyway, I'm not posting this to take away from your thread, I just merely do not want to duplicate Howto's, especially if there's a reason not to do this using gdm as I have been.

Here's the link to another post I created for a user asking questions:
[http://ubuntuforums.org/showpost.php?p=2757451&postcount=6](http://ubuntuforums.org/showpost.php?p=2757451&postcount=6)

Thanks - no offense, just hoping to add to the community ;)

---

### Post by 4integration on 2007-07-19
> **bdogg64 said:**
> This is a great HOWTO, but there is one part missing to get it completely working in KDE. 

```
ps wwaux | grep auth
``` 

will return a different file every time you reboot, unless you add the setting in /etc/kde3/kdm/kdmrc under [X-:*-Core]

```
AuthFile=A:0-LliKdB
```

You can change the AuthFile to be something different, just make sure you have the same file in your server_args in your Xvnc services file

I hope this helps someone

B

I am trying to get x11vnc to run under Kubuntu Feisty Fawn but having problems.
By setting the AuthFile to A:0-test1 it's created in file system root (/) not in /var/run/xauth/.
I have also tried absolute path in AuthFile and also to set AuthDir to /var/run/xauth and then I don't find the file at all.

If you have some ideas I would be happy.

---

### Post by maybeway36 on 2007-09-23
I always set the AuthFile to /root/xauth and use that path in the x11vnc arguments.

---

### Post by krunge on 2007-09-25
>  I always set the AuthFile to /root/xauth and use that path in the x11vnc arguments.

That's smart.  I wish the default system configuration was that clever.

---

### Post by Deadmode on 2008-04-19
if you are getting vnc to work, but you want it password protected be sure to add -passwd "yourpassword" into the server arguments.  

```
service x11vnc
{
        port            = 5900
        type            = UNLISTED
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/bin/x11vnc
        server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth /var/lib/gdm/:0.Xauth -passwd yourpassword -many -bg
        disable         = no
}
```

then I would set that file to root.
```
sudo chmod 600 /etc/xinetd.d/x11vnc
```

Now when you vnc into your computer it will prompt you with a password and also if anyone was tampering with your computer they wouldn't be able to mess with or see your password for /etc/xinetd.d/x11vnc file.

---

