---
title: "Stream data over network?"
date: 2008-08-05
forum: Programming Talk
---

### Post by kachofool on 2008-08-05
Hey all

This is going to be a fairly open ended question. I have a Windows-only application that is connected to a motion tracking camera. The output of this application are the X,Y coordinates of the object that is being tracked. The API for the camera is Windows-only, but I want to be able to stream the data recieved by the camera over to a Linux machine. I'd be developing a program on Linux that would make use of the coordinate data.

So the question is how would I accomplish such a thing? The windows application is basically outputting data to a command line. It's minimal to reduce processing load. How could I send the coordinate data from the Windows app to a Linux machine (it would be over a network)? 

I'm really not sure where to begin and would appreciate any ideas!


Thanks,

KF

---

### Post by era86 on 2008-08-05
Have you looked into winsock?  This might be a place to start.  You could do something lame like store the raw text in a file and ftp it over ;)

---

### Post by kachofool on 2008-08-05
I'll check out Winsock, thanks. I don't want to dump to a text output from the command line and FTP it since this application needs to be as close to 'real-time' as possible. I want to take every step to ensure minimum latency.

---

### Post by Nick Lake on 2008-08-05
Yep have a look at using sockets (winsock). Basically wrap up the data output from you're device's Windows API and pump out as ASCII on to a socket. Write your app in Linux to connect to the socket on your Windows machine and parse the ASCII sentence.
A few other ideas:

* Wrap up the output from the device and send to a web service running on your Linux box (could be a simple URL with arguments or even an XML service). You could get it to post to the web server every 10 seconds or so.

* Set up a database and write the XY data to a table. Get your Linux app' to poll the database every so often.

* Simply write from your Windows app in append mode to a file on the Linux box.

Out of curiosity what motion capture system are you using?

Regards,
Nick Lake

---

### Post by kachofool on 2008-08-05
I'm using a SmartNAV camera from NaturalPoint along with their OptiTrack SDK.

---

### Post by kachofool on 2008-08-06
So I think I've got the basics of WinSock down. I have a small TCP client set up as a test built with Visual C++. I was able to successfully send data to remote hosts with it...

Now the issue is the Linux program, which I want to act like a server. I have a few questions about this (and linux programming)...

* What API (like WinSocks for Windows) do I use to build socket applications on Linux

* Will an app I build with Ubuntu be compatible with other Linux distros (popular ones, anyway)

* Is there a way to build the app so that it will be cross compatible with OS X?

* Are there any IDEs that work well with Ubuntu?

Thanks!
KF

---

### Post by Vadi on 2008-08-06
I'll try and answer some...

* sys/socket.h for socketing

* yep, high chance that it'll work just fine

* maybe if you use some 'pure' C libraries, yeah

* there's a ton actually, but give [Geany]("apt:geany") a try.

---

### Post by era86 on 2008-08-06
> **kachofool said:**
> 
* What API (like WinSocks for Windows) do I use to build socket applications on Linux

* Will an app I build with Ubuntu be compatible with other Linux distros (popular ones, anyway)

* Is there a way to build the app so that it will be cross compatible with OS X?

* Are there any IDEs that work well with Ubuntu?


If you are doing the server end in C, it comes with socket libraries built in.

I'm thinking your server will run on any linux distro assuming it has the proper libraries you plan to use.

Yes there is a way.  Are you using a GUI?

Anjuta, Eclipse, etc.  There are many.

Goodluck!:guitar:

---

### Post by Nick Lake on 2008-08-07
Why not try and use Mono? And then develop it in C#.NET... Just one way to support multiple OS.

You will need to use System.Net.Sockets

Regards,
Nick Lake

---

