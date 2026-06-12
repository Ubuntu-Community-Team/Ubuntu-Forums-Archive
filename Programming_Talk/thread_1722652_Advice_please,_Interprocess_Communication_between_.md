---
title: "Advice please, Interprocess Communication between 2 programs"
date: 2011-04-06
forum: Programming Talk
---

### Post by Cool Javelin on 2011-04-06
Hello Friends:

I need a little advice on how to implement some kind of IPC between 2 or more programs asynchronously.

I have a bunch of experience programming in non-GUI environments, but none getting this type of problem solved, especially communication over a network.

I have written a home automation software on Linux that watches several things like the garage door (open or closed,) water well pump (on or off,) temperature of the living room, etc. It also writes to log files and displays a screen-full of instant statuses of the things it monitors.

I would like to split the program into 2 parts. Part one will be the "monitor" part that watches the hardware and writes to logs. Part 2 will be the "display" part that paints a screen-full on either another *nix machine, or maybe a windows machine. Also, any number of display programs may be run to get info from the one monitor program.

I understand both programs will have to know about each other. Eventually, I would like the monitor to become a daemon.

I am thinking of only one-way communication, the monitor talks and any display can listen, but I may want more sophistication later, in that one (or more) displays can tell the monitor to do something like "close the garage door" for example.

I started looking into D-bus, but it appears to only work between two processes on the same desktop.

I also thought of making the monitor write to many little files to keep the status of each thing and let the display read them, but I don't like that idea for several reasons.

The program is currently written in Pascal and I would like to keep that, but I don't think the language matters too much.

Does anyone have any suggestions that may help me to get going on this?

Thanks, Mark.

PS, upon rereading this I see I started a lot of sentences with "I." I guess I think a lot of I. :)

---

### Post by amauk on 2011-04-06
Best way to do this is with sockets
(Using either TCP or UDP)

The monitor binds to a port number and listens for requests
The display sends a request to monitorIP:port for information
Monitor responds to request by sending information back to the display program

---

### Post by LemursDontExist on 2011-04-07
Sockets are definitely the way to go, one way or the other.  That said, you may save yourself a lot of trouble by piggybacking on some existing socket system rather than writing your own socket server.

If I were doing this, I would write a web interface for the monitor program, run a webserver (like apache) and allow remote machines to communicate with the monitor that way.  This solution has the advantage of being easy to implement, easy to customize, and cross platform.

It's also worth noting that if you don't care about windows support you can use ssh -X to tunnel an X windows application over ssh, which would allow you to access a program on the monitor machine (and basically use the ssh socket for your IPC).  If you don't want a gui, this is even better, ssh does everything you need!

For both of these solutions, you'll of course still need IPC on the monitor machine, but the display program can be on the same machine as the monitor and you can use dbus or files, or shared memory, and your webserver or ssh server handles the sockets for you.

Not that sockets are that difficult to deal with - in python I can write a socket server in 15 minutes.  But with Apache I know I'm not going to have to spend any time debugging socket or threading issues.  You can have a single thread monitor program, and a single thread display program, and the webserver does the rest for you.

---

### Post by amauk on 2011-04-07
Indeed,
you could probably get a prototype up and running using Apache & PHP inside of 30 mins

Apache handles the low-level networking stuff
A few simple PHP scripts to collect & collate the data

It's dependant on what hardware you're running on, though
If you're planning to run the monitor program on some really basic hardware (Eg. the [Beagle Board](http://beagleboard.org/)), then you don't want to be running such heavy programs as Apache & PHP

---

### Post by Cool Javelin on 2011-04-07
This is great, amauk, and LemursDontExist, it is exactly the kind of advice I was looking for.

Assuming for a minute I want to run an Apache server for the monitor, can you point to a good tutorial or 2 to get me started.

I have never done this kind of stuff before, and have no idea of the overall picture.

Some basic questions are...

Do I start Apache, then call my program from Apache and let Apache handle the input to my program via stdin?

or

Do I start my program and call Apache somehow when I want or expect input from something,

or

are the 2 parts even connected that way at all, ie. does my monitor program talk to Apache in another terminal window?

Keep in mind I have a LOT of work in the monitor program and I don't relish the idea of rewriting it totally from scratch. I don't mind changing the I/O however, the program is heavily structured and all the I/O is in one unit.

---
I guess the display part could be used via a web interface like Firefox or I.E. That would eliminate 1/2 the work.

I already have an Apache server on that machine. I installed "motion", a camera monitor and the installation also installed Apache.

Would I use the same instance of Apache, or would it require a second instance?

Maybe I will start poking around Google for using Apache.

I see I have a steep learning curve ahead of me, but once I get some basic understanding of the "system" (Apache, IPC, web interfaces...) I bet it will fall into place pretty fast.

I have some experience writing web pages and have a working knowledge of HTML but this may be totally different.

Mark.

---

### Post by amauk on 2011-04-07
How you do this is dependant on what you've already done

When you query the monitor program, what exactly does it output?
(If you could post some sample output, that'd be great)

To start with, make sure you have a working Apache webserver & PHP on your monitor system

Then, assuming your monitor program is
/usr/local/bin/monitor
A simple PHP script such as```
<?php
passthru ('/usr/local/bin/monitor');
?>
```will simply dump the output of the monitor program to the browser

Save your PHP script as, say
/var/www/monitor.php

Then point a web browser to
http://<monitor_ip>/monitor.php
to have all output from the monitor program displayed in the browser

Where you go from here is up to you
If you want to stick with the Apache + PHP setup, then you can (possibly) start breaking apart your monitor program into separate modules

You can add support for command line arguments, in order to filter what gets returned
Say```
/usr/local/bin/monitor --lights
```Only returns info about lighting
Then you can have a PHP script called
lights.php
that simply does```
<?php
passthru ('/usr/local/bin/monitor --lights');
?>
```

In time, you may wish to migrate away from using Apache & PHP
but as a first prototype it should be relatively simple to get something up and running

---

### Post by LemursDontExist on 2011-04-08
> **Cool Javelin said:**
> Do I start Apache, then call my program from Apache and let Apache handle the input to my program via stdin?

Generally the approach is to configure Apache to allow a script to be executed, have the script output html, and then point the web browser at the script.  Apache runs the script, and sends the output to the browser.  A basic tutorial is available [here]("httpd.apache.org/docs/2.0/howto/cgi.html").

As for multiple instances of Apache - you just need one instance.  It waits for requests and then runs your scripts when the requests come in.

The script can be in any language.  That said, PHP is definitely the language to use, and is very easy to learn.  It will probably take less time to install PHP and learn how to use it than to write the same script in another language.  PHP is one of the most used languages on the planet and there are hundreds of good references and tutorials out there.  At least in Ubuntu, installing PHP should automatically configure apache to use its scripts with no further effort on your part, which saves a bunch of trouble.  If you want to write your scripts in Pascal though, that should work too.  Pascal probably has a CGI module you can use to simplify some of the work.

You'll need some form of IPC between the monitor program and the PHP script, but since both run on the same machine you have lots of options.  I believe that PHP has dbus support, so that might be the cleanest solution.  As Amauk noted, a lot depends on how you're currently doing I/O for the monitor.  If the monitor is outputting log files, your PHP script could simply scrape data from those files.  For more interactivity, something that doesn't involve hard drive writes is probably best.

---

### Post by Cool Javelin on 2011-04-08
Thanks a second time to both of you for this, I have been researching the methods you both recommend. I am reading through the tutorial page LemursDontExist suggested.

amauk asked for some output from the monitor program, I may do that, but right now it is on a headless server.

The program needs to be started with root privileges as it talks to a special data acquisition board and I am using and uses the port function.

The screen shows a list of things on the left, and the current status on the right. Once a second, it checks everything then repaints only those things that have changed.

The monitor needs to continue to run, but I guess I could make the display take a snapshot by looking at the last line in all the logs then paint the screen once, then Apache could call the display.

This would have a 2 fold advantage, one, the display wouldn't have to be tun with root privileges, 2, it would eliminate the loop.

In fact, if I went that way, I would not have to change the monitor at all, only create a duplicate display program.

I have only read the first page of the tutorial so far, but I see in the tutorial an example that Apache calls a Perl script, I assume I can just as easily call a Pascal program I write?

Thanks again to both of you, I will spend a few days experimenting with this and let you know. I have a long honeydo list and can only work on this in the evenings.

Mark.

---

### Post by LemursDontExist on 2011-04-08
> **Cool Javelin said:**
> The monitor needs to continue to run, but I guess I could make the display take a snapshot by looking at the last line in all the logs then paint the screen once, then Apache could call the display.

This would have a 2 fold advantage, one, the display wouldn't have to be tun with root privileges, 2, it would eliminate the loop.

In fact, if I went that way, I would not have to change the monitor at all, only create a duplicate display program.

I have only read the first page of the tutorial so far, but I see in the tutorial an example that Apache calls a Perl script, I assume I can just as easily call a Pascal program I write?

If I understand your setup correctly and you already have a display program which gets its data from log files, then you're 95% of the way there!  All you'll need to do is have the display program output html to stdout when called instead of whatever it is currently doing.

And, Pascal should work fine - CGI is a universal interface.

Good luck!

---

### Post by chouhan.raj1978 on 2011-04-26
Hi,

I am also facing same type of problem..

I have two different application, one is in Linux gateway (written entirely in ANSI C and Linux) and other is dot net server application.I wanted to implement a communication channel (code in Linux and C) or some mechanism, which will help these different services to share objects/data.

Is it possible to communicate between two distinct OS environment using C and Linux remoting?

If so, what could be the fine tuned way to achieve the same? What are the other possible thoughts to implement the same apart from remoting and web service?

Any thoughts / link/ sample application will be appreciated.

Regards

Raj

---

### Post by LemursDontExist on 2011-04-26
The original answer stands - you need to use sockets.  I don't know a whole lot about socket programming in dot net, but sockets are a universal cross platform standard for IPC and should work for you.  If you don't want to use a webserver, your best bet is to write a socket client server setup yourself.

I wrote a socket server in C once, but I can't find the code anymore, and you can probably find a tutorial on the topic as easily as I can - just search for "C socket server" or something like that.

Good luck!

---

