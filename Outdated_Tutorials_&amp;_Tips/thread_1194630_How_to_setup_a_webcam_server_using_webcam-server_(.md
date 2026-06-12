---
title: "How to setup a webcam server using webcam-server (Includes daemon script)"
date: 2009-06-22
forum: Outdated Tutorials &amp; Tips
---

### Post by d3k4y on 2009-06-22
This tutorial explains how to setup a webcam server using the webcam-server package.  I have written a daemon script since webcam-server does not provide one.  I will provide it to you.  This tutorial comes from my blog.  I will provide the link to the [original post]("http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2"), but note, I am simply elaborating on my original writing.

I used Ubuntu 9.04 and a [Logitech QuickCam Communicate MP]("http://hacktivision.com/index.php/2009/06/11/ubuntu-webcam?blog=2") to create this tutorial.  It is a good idea to see if your webcam is working by using "Cheese Webcam Booth" or "Camorama Webcam Viewer".  Both can be installed using "Add/Remove..." in the main menu in the task bar.

So let's get started!

**1. Installing the webcam-server package**

The webcam-server package can be installed by searching with synaptic if you prefer to use a GUI.  The command line is

```
sudo apt-get install webcam-server
```

Enter your password if prompted. Answer yes with a "y" if prompted.

**2. Create the startup script.**

Use your favorite text editor to create and edit the file /etc/init.d/webcam-server.  You will need to be root or use sudo.  This command will create and open the file in nano:

```
sudo nano /etc/init.d/webcam-server
```

Once open, paste the following text into the file:

```
#!/bin/sh

SERVER_BIN=webcam-server
LOCK_FILE=/var/lock/$SERVER_BIN
RTRN=0
OPTIONS='-v -g 320x240 -p 8888 -c hacktivision.com'

start() {

[ -f $LOCK_FILE ] && echo "$SERVER_BIN already started"
[ -f $LOCK_FILE ] && return

echo -n "Starting $SERVER_BIN: "
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
nohup $SERVER_BIN $OPTIONS > /dev/null 2>/dev/null &
RTRN=$?
[ $RTRN -eq 0 ] && echo Started! || echo FAIL
[ $RTRN -eq 0 ] && touch $LOCK_FILE
}

stop() {
[ -f $LOCK_FILE ] || echo "$SERVER_BIN is not running"
[ -f $LOCK_FILE ] || return
echo -n "Stopping $SERVER_BIN: "
pkill -f "$SERVER_BIN $OPTIONS"
RTRN=$?
rm -f $LOCK_FILE
[ $RTRN -eq 0 ] && echo Stopped! || echo FAIL
}

case "$1" in
start)
start
;;
stop)
stop
;;
restart)
stop
start
;;
*)
echo "Usage: $0 {start|stop|restart}"
RTRN=1
esac

exit $RTRN
```

Please note that the line

```
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
```

is required for some webcams, but you may be able to remove it if your webcam does not require it.  The workaround was found at [https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/314805]("https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/314805").

**3. Set permissions and link the startup script**

You will need to set permissions and  create a link in the /etc/rc3.d directory that points to the script.  Here are the commands to do so:

```
sudo chmod +x /etc/init.d/webcam-server
sudo update-rc.d webcam-server defaults

```

Again, enter your password if prompted.

**4. Test your webcam and startup script**

It's a good idea to test if your startup script and webcam are working at this point.  You can do this by running

```
sudo /etc/init.d/webcam-server start
```

and then using your browser to view [http://localhost:8888/]("http://localhost:8888/").  You should see a snapshot from your webcam.  Do a full refresh to see an updated picture.  If you do not see a picture, or get an error, consider adding or removing the "*export LD_PRELOAD=...*" line from your script.  If that does not work, please reply with your findings and I will try to help.

**5.  Install Apache HTTP Server**

Up to this point, you can view snapshots from your webcam locally, but you probably want to share your webcam with the world (or at least some friends).  To do this, you will need to install Apache (or another web server if you choose).

To install apache run

```
sudo apt-get install apache2
```

Accept all the default options, or if you are an advanced user, configure Apache as you so choose.  Apache will be started when installation is complete.  Also, your webroot, or the directory that Apache will share.

*You may need to forward port 80 on your router to your computers IP address.

**6. Copy the webcam-server html and applet to your webroot**

The webcam-server package comes with html and java files that will allow visitors to see a stream of images from your webcam.  The webpage uses an applet to do this.

To copy the files to your webroot run

```
sudo cp /usr/share/doc/webcam-server/applet/* /var/www/
```

To test if you copied the files correctly, and if Apache is working, goto [http://localhost/webcam.html]("http://localhost/webcam.html").

You should see a stream from your webcam.  If you do not, make sure several files have been copied to your webroot, including webcam.html and some jar and gz files.

**Conclusion and tips**

You are now setup to stream your webcam on a webpage, but there is more to do to share it with the world.

The default webcam.html file is setup to only run at 1 frame per second and only be server to localhost, meaning only on your computer.  It can be edited to server at a domain or from an IP address though.  You can also add your own HTML to customize the page that is streaming your webcam.

Here is an example of what the webcam.html file would look like on my website, [hacktivision.com]("http://hacktivision.com/") at 60 frames per second:

```
<html>
<head>
<title>WebCam</title>
</head>
<p align="center">
<a href="http://hacktivision.com" title="hacktivision.com - Ubuntu webcam server">Hacktivision</a>
</p>
<div align="center">
<APPLET CODE = "WebCamApplet.class" archive="applet.jar" WIDTH = "320" HEIGHT = "240">
<param name=URL value="http://hacktivision.com:8888">
<param name=FPS value="60">
<param name=width value="320">
<param name=height value="240">
</APPLET>
</div>
</body>
</html>
```

**Credits**

I wrote the original article which can be found at [http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2]("http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2").

I found the workaround used in the startup script at [https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/314805]("https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/314805").

And of course, much of my Linux knowledge was attained right here at Ubuntu Forums.

---

### Post by dmizer on 2009-06-23
The startup script won't allow a stop:
```
$ sudo /etc/init.d/webcam-server stop
Stopping webcam-server: FAIL
```

Also, I couldn't get this to output any video. Though to be fair, I haven't gotten any cam server software to output video. Cheese works though, and VLC will accept a live stream. Just can't get any server software to do squat.

---

### Post by d3k4y on 2009-06-24
dmizer, start the webcam-server daemon as described in the tutorial, then run:

```
sudo rm -f /var/lock/webcam-server
sudo pkill -f "webcam-server -v -g 320x240 -p 8888 -c hacktivision.com"
```

to stop the webcam-server.

Please report your results.

---

### Post by dmizer on 2009-06-24
Yes, this kills the server.

Still get zero output from the camera though.

---

### Post by d3k4y on 2009-06-24
Well, then let's try to figure that out before we figure out the startup script.  What happens if you run webcam-server by itself?  Can you get anything when you goto [http://localhost:8888/?](http://localhost:8888/?)

Do you get an error? A black box?

---

### Post by dmizer on 2009-06-24
This is the error I get:
```
dmizer@tsubame:~$ webcam-server
No supported colour palette found.
```
I've done some searching on that error and haven't found much. I get the same error from 3 different webcams, all of which work perfectly in skype and cheese. Cheese can even record video.

Also, I've made sure that my account is a member of the video group, as well as made sure that www-data is a member of the video group:
```
$ cat /etc/group | grep video
video:x:1002:dmizer,www-data
```

---

### Post by d3k4y on 2009-06-25
I got that error with my logictech.  That's what the line
```
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so

```
is supposed to fix.

Try running this:
```
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so; webcam-server
```

If it starts webcam-server successfully, check to see if you get any output at the localhost address I gave you.

That fixed my issue.  But yeah, I'd start googling for your specific webcam and its compatibility with Ubuntu.

---

### Post by radioraheem on 2009-08-04
Hi d3k4y - Thank you for the excellent How-To.  I've managed to setup everything you outlined here successfully, but when I use the preview at [http://localhost:8888](http://localhost:8888) I get a single picture from the web cam.  Refreshing the browser does not change anything.  

It seems the camera takes one picture and nothing else until you restart the server, then the same thing happens again (new picture, doesn't take any others).

If I run webcam -v by itself and connect to the preview URL I can see the following output from my terminal:

```
2009-08-04 15:13:38 [/dev/video0] webcam_server started
2009-08-04 15:13:47 [/dev/video0] 127.0.0.1 connected via HTTP
2009-08-04 15:13:49 [/dev/video0] 127.0.0.1 disconnected, 2 seconds, 4611 bytes, 2.25 Kbytes/second, 1 frames, 0.50 fps
2009-08-04 15:13:52 [/dev/video0] 127.0.0.1 connected via HTTP
2009-08-04 15:13:52 [/dev/video0] 127.0.0.1 disconnected, 0 seconds, 4611 bytes, 4.50 Kbytes/second, 1 frames, 1.00 fps
2009-08-04 15:13:53 [/dev/video0] 127.0.0.1 connected via HTTP
2009-08-04 15:13:53 [/dev/video0] 127.0.0.1 disconnected, 0 seconds, 4611 bytes, 4.50 Kbytes/second, 1 frames, 1.00 fps
```

Any idea why I can't get it to update the image?  I really want to use this software but a streaming webcam that only shows one frame is pretty useless.

I am using a Logitech V-UBK45. Cheese can utilize the cam without any extra steps or modifications. 

Thanks in advance for any advice!

---

### Post by kssummer on 2009-10-10
So I can get webcam-server working, and it SEEMS apache2 is working even though I get this error when starting:

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

My symptom: localhost/webcam.html does not display anything. The source says:
<html>
<head>
<title>WebCam</title>
</head>
<APPLET CODE = "WebCamApplet.class" archive="applet.jar" WIDTH = "320" HEIGHT = "240">
<param name=URL value="http://localhost:8888">
<param name=FPS value="4">
<param name=width value="320">
<param name=height value="240">
</APPLET>
</body>
</html>
and there are camera images on localhost:8888. I can even constant refresh to get a semi-stream going.

Do I have to set up apache2 ports and/or virtual host for this to work?

---

### Post by kssummer on 2009-10-10
> **radioraheem said:**
> Hi d3k4y - Thank you for the excellent How-To.  I've managed to setup everything you outlined here successfully, but when I use the preview at [http://localhost:8888](http://localhost:8888) I get a single picture from the web cam.  Refreshing the browser does not change anything.  

It seems the camera takes one picture and nothing else until you restart the server, then the same thing happens again (new picture, doesn't take any others).

If I run webcam -v by itself and connect to the preview URL I can see the following output from my terminal:

```
2009-08-04 15:13:38 [/dev/video0] webcam_server started
2009-08-04 15:13:47 [/dev/video0] 127.0.0.1 connected via HTTP
2009-08-04 15:13:49 [/dev/video0] 127.0.0.1 disconnected, 2 seconds, 4611 bytes, 2.25 Kbytes/second, 1 frames, 0.50 fps
2009-08-04 15:13:52 [/dev/video0] 127.0.0.1 connected via HTTP
2009-08-04 15:13:52 [/dev/video0] 127.0.0.1 disconnected, 0 seconds, 4611 bytes, 4.50 Kbytes/second, 1 frames, 1.00 fps
2009-08-04 15:13:53 [/dev/video0] 127.0.0.1 connected via HTTP
2009-08-04 15:13:53 [/dev/video0] 127.0.0.1 disconnected, 0 seconds, 4611 bytes, 4.50 Kbytes/second, 1 frames, 1.00 fps
```Any idea why I can't get it to update the image?  I really want to use this software but a streaming webcam that only shows one frame is pretty useless.

I am using a Logitech V-UBK45. Cheese can utilize the cam without any extra steps or modifications. 

Thanks in advance for any advice!

Mine was doing this without an internet connection. I brought eth0 back up, and could refresh to get new images.

---

### Post by carex on 2009-10-20
Hello,

I am also experiencing the same problem.
Just one static image.
When I want to refresh the page here is what I get in the log file:

2009-10-20 11:25:15 [/dev/video0] 192.168.1.7 connected via HTTP
2009-10-20 11:25:15 [/dev/video0] 192.168.1.7 disconnected, 0 seconds, 18323 bytes, 17.89 Kbytes/second, 1 frames, 1.00 fps
2009-10-20 11:25:15 [/dev/video0] 192.168.1.7 connected via HTTP
2009-10-20 11:25:15 [/dev/video0] 192.168.1.7 disconnected, 0 seconds, 18323 bytes, 17.89 Kbytes/second, 1 frames, 1.00 fps
.......
.......

Any idea what I am doing wrong ?
Thanks.

(ubuntu 9.4 , webcam_server 0.50)

---

### Post by OnlyLinuxLives on 2009-11-04
I also am having this trouble where I only get one or 2 images without restarting the computer. My WebCam is a HP Deluxe Webcam.

---

### Post by theluddite on 2010-01-05
Great tut.  I was having difficulty changing the refresh rate and making the feed viewable outside my LAN until I cam across this post.

At risk of stating the obvious, **make sure you port forward 8888 in your router settings** if you're trying to view the feed from outside the LAN.  Don't I feel stupid for not figuring this out earlier.

---

### Post by aminal on 2010-01-08
Having the exact same issue with the 1 or 2 frames thing as mentioned by others above.  Also, when I try to use the given webpage, java platform starts up but all I get is the black "connecting, please wait."

Any ideas?

thanks.

*edit*

Using Quickcam Express (046d)

---

### Post by aminal on 2010-01-08
Bump

---

### Post by emax2000 on 2010-01-10
Please help me . And sorry for my english is very bad.

Now I've follow the guide and now the 127.0.0.1:8888 work fine but when i connect with 127.0.0.1/webcam.html on the screen appear the hacktivision logo but nothing else , i've copied all files in the /var/www/ but i trust that non exec the java files.

Tank you

---

### Post by dlbrando on 2010-01-21
I got it working and was to the stage of having friends try to see it from outside my lan.  I shut down the computer and powercycled the router to have everything start fresh.  I then went into the router settings to confirm the port 80 was forwarded as well as 8888.  

Now all I get is the black "connecting" screen.  I tried copying the applet source into the index.html page before I power cycled everything, and it came up under local host, but now it is doing the same thing as well.  

Any ideas?

I don't even intend to get a domain name, I was just going to memorize the public IP and use that so I can just use the camera as a cheap security camera.

---

### Post by Spigot1 on 2010-08-23
Any luck dlbrando?  I came to the same point you did and have not been able to get the feed from outside my LAN, Feel like i've tried everything..

Thanks

---

### Post by ubudog on 2010-09-13
Thanks for this tutorial, it really helped.  Only one problem though.  I can't view the webcam.html remotely eg, going to [http://ipaddress/webcam.html](http://ipaddress/webcam.html).  It pops up with a java security window, I click allow, but it says "Error connecting to host".  Any way to fix this?  Other than that, everything works great.  :p

---

### Post by InnerBushman on 2010-09-26
I have the same problem.
When i open the web-cam from server A and feed the applet from server A too users say it works OK. But when i open the web-cam from server B while feed it from server A the users say they see the "wait" screen.
I, myself, haven't experienced the problem since I'm opening it locally from inside the server's A lan. There's also one user who said he can open the web-cam from both, the A and B servers and it streams OK. Someone suggested me it's a security problem and it is possible that the browsers are blocking the app and not allow them to connect outside the domain B to domain A by default. That's why users don't get any security warning.

Any ideas how to fix or walk around?

Bushman

---

### Post by duceduc on 2010-10-28
I am also having issue with the setup. I get a black screen when connecting via the web. 

I am running ubuntu 10.4 server edition. How can I check if my webcam is working on the server? I've read the line in the OP where you can use two different apps to test, but I am using a server ubuntu and not a client.

---

### Post by loothi on 2010-11-28
Hi All. Thanks for the tutorial. I had a problem with the init script.. the -f flag of the pkill command wasn't killing the webcam-server process, even though it was removing the lock file. I knocked another one up which I'll paste below. Works for me on ubuntu 9.10


```

#!/bin/sh

SERVER_NAME=webcam-server
SERVER_BIN=/usr/bin/webcam-server
LOCK_FILE=/var/lock/$SERVER_NAME
RTRN=0
OPTIONS='-v -g 320x240 -p 8888'

start() {

    if [ -f $LOCK_FILE ] ; then
        echo "$SERVER_NAME appears to be running"
        return
    fi

    echo "Starting webcam streamer: $SERVER_NAME."
    export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
    nohup $SERVER_BIN $OPTIONS > /dev/null 2>/dev/null &
    RTRN=$?

    if [ $RTRN -eq 0 ]; then
        touch $LOCK_FILE
    else
        echo "Error starting $SERVER_NAME: returned $RTRN"

    fi
}

stop() {
    if [ ! -f $LOCK_FILE ]; then
       echo "$SERVER_NAME is not running"
       return
    fi

    echo "Stopping webcam streamer: $SERVER_NAME."
    pkill -f "$SERVER_BIN" 
    RTRN=$?

    if [ $RTRN -eq 0 ]; then
        rm -f $LOCK_FILE
    else
        echo "Error stopping $SERVER_NAME: returned $RTRN"
    fi
}

case "$1" in
start)
start
;;
stop)
stop
;;
restart)
stop
start
;;
*)
echo "Usage: $0 {start|stop|restart}"
RTRN=1
esac

exit $RTRN

```

---

### Post by ubudog on 2011-04-06
Thank you, this works great!  I built an app in REAL Studio that refreshes it with an HTML Socket (whatever it's called), and now I have a nice little security system.  :-)

---

### Post by NoSalt on 2011-04-23
Hello All

    I was wondering if anybody has ever been able to successfully get webcam-server to work? I have been trying for a while now, and I just cannot get it to work for me.

I am running XUbuntu 10.04 on a Dell PowerEdge T110. I am using a Logitech C250 Webcam. First, I tried *Cheese*, and that worked great, so I know my webcam is supported. Next, I installed webcam-server using apt-get, no problems there either. I have been reading information on how to get this set up in several locations:

```

http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2
http://webcamserver.sourceforge.net/
http://ubuntuforums.org/showthread.php?t=1194630

```

I can successfully point my browser to [http://localhost:8888](http://localhost:8888) and see myself on the page. The issue comes with accessing the cam from an html document. I copied all of the files from usr/share/doc/webcam-server/applet/ to /var/www/webcam/ , but there is no success. Whenever I attempt to view it from localhost, I get an Apache error message stating:

```

[Sat Apr 23 19:23:16 2011] [error] [client 127.0.0.1] File does not exist: /var/www/webcam/WebCamApplet.class, referer: http://127.0.0.1/var/www/webcam/webcam.html

```

And, when I attempt to access the page from another computer, all I get is the init.jpg file, no Apache error either.

This is becoming really frustrating, so I was hoping somebody out there actually got this to work, and could help me out. Any and all advice will be greatly appreciated.

Thanks for reading, and have a great day.  :)

---

### Post by dmizer on 2011-04-23
> **NoSalt said:**
> First, I tried *Cheese*, and that worked great, so I know my webcam is supported.

Actually, I have learned that Cheese accepts direct input from the webcam, whereas webcam-server works through video4linux2 which may or may not support your camera.

Check to see if your camera works in a video4linux capable program rather than in Cheese. VLC uses video4linux2 as does camorama.

This may not be your problem, but it's worth investigating.

Also keep in mind that the webcam-server project appears to be dead and hasn't received any updates to the code since around 2004.

---

### Post by NoSalt on 2011-04-23
dmizer

    Yes, my camera works through VLC. I went to Media -> Open Capture Device, I entered "/dev/video0" for my video device name, and it works great.

---

### Post by NoSalt on 2011-04-29
Just checking in ... anybody have any ideas for me?

Thanks :)

---

### Post by feeblminds on 2011-06-12
Hi, just picked up this thread trying to solve my problem with webcam-server.  Im running XFCE on Ubuntu 10.04.  When I run the script above it seems to work but the localhost link just hangs on loading screen, if I remove 'export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so' I get unable to connect through browser.

If I run webcam-server -d /dev/video0 -p 8888 I get the following:
ioctl (VIDIOCGCAP): Invalid argument
ioctl (VIDIOCSPICT): Invalid argument
error setting video device parameters, using defaults
ioctl (VIDIOCGCAP): Invalid argument
ioctl (VIDIOCSPICT): Invalid argument
not a valid video device? quitting.

I can run VLC server using vlc v412:///dev/video0 which works fine, also Cheese works fine.

Any thoughts?

---

### Post by mo7ard on 2011-07-19
Brilliant tutorial... worked like a charm with my Ubuntu 10.10! :P

I'm just trying to customize the html and conf to my needs... if I have any doubts, I'll be posting here :)

Thanks!!!!

---

### Post by mo7ard on 2011-07-19
I'm having trouble in port forwarding to the web...

In the webcam-server config file, I have "-p 9999" set, and in the index.html file in Apache (*yes, I replaced the index content with the webcam.html one*) I have set "<param name=URL value="http://localhost:9999">"

So...[INDENT]. if I open my web browser in [http://localhost/](http://localhost/) I can see my webcam feed
. if I open my web browser in [http://localhost:9977/](http://localhost:9977/) I can see a static image

[/INDENT]... but no matter what I do, I can't port forward this feed. I tell my browser that my machine IP with port 9999 is to be open at port 9999, and when I try to open via my public IP (e.g. http:// 12.34.56.78:9977) all I get is the static image.

I've even replaced the "localhost" in the index.html with my IP address but I get the same problem... no matter what I do, I can't see my feed outside my network... what am I doing wrong? Help, please...

Thanks!!

EDIT: I disabled my firewall to let any incoming traffic to my PC, so the problem isn't there.

---

### Post by Henk-Jan on 2011-09-07
Thanks for the excellent web-cam server. On my 9.04 system, it worked perfectly.
However I cannot load it on my 11.04 system:
sudo apt-get install webcam-server ends in error ('can't find package').

Hope you can help.

---

### Post by ubudog on 2011-09-07
> **Henk-Jan said:**
> Thanks for the excellent web-cam server. On my 9.04 system, it worked perfectly.
However I cannot load it on my 11.04 system:
sudo apt-get install webcam-server ends in error ('can't find package').

Hope you can help.

You probably have to add the 9.04 repos, or someone's custom repos.  

Or, you could build it from scratch, here:
[https://launchpad.net/ubuntu/lucid/+source/webcam-server/0.50-4/+files/webcam-server_0.50.orig.tar.gz](https://launchpad.net/ubuntu/lucid/+source/webcam-server/0.50-4/+files/webcam-server_0.50.orig.tar.gz)

For information on how to build it from source, see this:
[http://ubudog.net/blog/?p=61](http://ubudog.net/blog/?p=61)
(assuming you have all dependencies)

Good luck!  :-)

---

### Post by Henk-Jan on 2011-09-07
I'm getting an error after ./configure:
Could not find jpeglib.h

How to load this? It seems not te be available in Synaptic.


Output in terminal:

~/temp/webcam_server-0.50$ ./configure
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... missing
checking for working autoconf... found
checking for working automake-1.4... missing
checking for working autoheader... found
checking for working makeinfo... missing
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for a BSD compatible install... /usr/bin/install -c
checking for mawk... mawk
checking how to run the C preprocessor... gcc -E
checking whether gcc needs -traditional... no
checking whether ln -s works... yes
checking for ftime... yes
checking for inet_ntoa... yes
checking for malloc... yes
checking for memset... yes
checking for munmap... yes
checking for select... yes
checking for socket... yes
checking for strchr... yes
checking for strstr... yes
checking for unistd.h... yes
checking for getpagesize... yes
checking for working mmap... yes
checking for strftime... yes
checking for jpeglib.h... no
configure: error: Could not find jpeglib.h

---

### Post by ubudog on 2011-09-07
Try this:
```
sudo apt-get install libjpeg62 libjpeg62-dev
```

Then do ./configure again.

---

### Post by Henk-Jan on 2011-09-08
Yes, some succes now! But also another error:

checking for jpeglib.h... yes
checking for linux/videodev.h... no

---

### Post by ubudog on 2011-09-08
> **Henk-Jan said:**
> Yes, some succes now! But also another error:

checking for jpeglib.h... yes
checking for linux/videodev.h... no

Try this:
```
sudo apt-get install libvideo-ivtv-perl
```

That might work.

---

### Post by Henk-Jan on 2011-09-08
Nope ... still same error after loading:


checking for jpeglib.h... yes
checking for linux/videodev.h... no
configure: error: Could not find linux/videodev.h

However module videodev.ko does exist:

root: modprobe -l | grep videodev
kernel/drivers/media/video/videodev.ko

---

### Post by ubudog on 2011-09-08
Ok, try this:
```
sudo apt-get install libv4l-0 libv4l-dev libwebcam0-dev libwebcam0
```

That should do it; webcam-server requires Video For Linux.  (V4L)

---

### Post by Henk-Jan on 2011-09-08
... fails again.

Observe this:

root: locate videodev.h
/usr/src/linux-headers-2.6.28-14/include/linux/videodev.h
/usr/src/linux-headers-2.6.28-15/include/linux/videodev.h
/usr/src/linux-headers-2.6.28-16/include/linux/videodev.h
/usr/src/linux-headers-2.6.28-17/include/linux/videodev.h
/usr/src/linux-headers-2.6.28-18/include/linux/videodev.h

And this:

root: locate videodev2.h
/usr/include/linux/videodev2.h
/usr/src/linux-headers-2.6.28-14/include/linux/videodev2.h
/usr/src/linux-headers-2.6.28-15/include/linux/videodev2.h
/usr/src/linux-headers-2.6.28-16/include/linux/videodev2.h
/usr/src/linux-headers-2.6.28-17/include/linux/videodev2.h
/usr/src/linux-headers-2.6.28-18/include/linux/videodev2.h
/usr/src/linux-headers-2.6.38-11/include/linux/videodev2.h
/usr/src/linux-headers-2.6.38-11-generic/include/linux/videodev2.h

I'm running Ubuntu 10.4 with kernel 2.6.38-11-generic

We are getting close now, right?

---

### Post by Vinno on 2011-09-08
Does this webcam server work on a server and can take input from say a laptop?

---

### Post by ubudog on 2011-09-08
> **Vinno said:**
> Does this webcam server work on a server and can take input from say a laptop?

Not positive, but maybe.  I think that the webcam has to be on the local machine though.

---

### Post by Henk-Jan on 2011-09-10
I think webcam-server needs to be updated to be compatible with videodev2.h, which is supplied with the current en future  kernels. Videodev.h seems to be obsolete.

---

