---
title: "Howto: Use the Edonkey Network with Amule Daemon And AmuleWeb"
date: 2006-12-29
forum: Outdated Tutorials &amp; Tips
---

### Post by netyire on 2006-12-29
_[SIZE="3"]Formalities: (Due to forum regulations) ;) [/SIZE]_

This guide was written with information based upon the Amule wiki and the Ubuntu forum. Thanks to the people who wrote the stuff. This guide was tested on Ubuntu Edgy Eft 6.10. And, (because of regulations) and the fact that I do not want to be exploited, I have to state that I will not be able to guarantee support. (Not that I will not, I can try to help, but no promises OK?).

To cut this all short, what I want to say is: Thanks to those who helped, and I hope this helps you! :D 

[SIZE="3"]_Installing the required stuff:_[/SIZE]

Okay, you are all set and want to download stuff from the edonkey network, however you may have tried amule and realized that it crashes (Based on certain things maybe). Anyway, this guide is about setting up the amule-daemon and amuleweb. (This way, I don't think you have to worry about the GUI crashing, and you can also see the download status from work!).
First, you need to install the required packages, to do so enter this in a terminal:
```
sudo apt-get install amule-daemon
```

OK, thats all you have to do to installed the required stuff!

[SIZE="3"]_Configuring it (So it works the way you want):_[/SIZE]

Right, you now have the stuff needed to proceed. Now in the configuration section, enter this in the terminal:
```
amuled
```
Now, it will fail (this is the first time you run it, but don't freak out - it will create the configuration files you need. Now cd to the amule configuration directory by typing:
```
cd ~/.aMule
```

Okay, now type:
```
gedit amule.conf
```
Places of interest include: (The following may not be correct)
1. Port = <Enter the TCP port, you want to use>
2. UDPPort = <This is the UDP port if you want>
3. UDPDisable = <Set this to 1 to disable>
4. AcceptExternalConnections = <Set this to 1>
5. ECPassword = <Enter hash here, for howto read on>

I think the ECPassword is the md5sum of the password you want, to get the md5sum, enter the following in another terminal:
```
echo -n <yourpassword> | md5sum | cut -d ' ' -f 1
```
Now copy the output and paste it in the ECPassword = <paste it here>. Now, you're done with the amule.conf, :). Now you only have to configure - amuleweb!

To do so enter:
```
amuleweb -w
```
This will write the needed configuration files, then type:
```
gedit remote.conf
```
Paste the md5sum password you generated just now into the password, adminpassword and guestpassword stuff. And you are done with the configuration.

[SIZE="3"]_Running it:_[/SIZE]

OK, after all that work, have two terminals open. In one type:
```
amuled
```
To run the amule-daemon.

In the other type:
```
amuleweb
```
To run the web interface.

Then open a web browser and type:
[http://localhost:4711](http://localhost:4711)

From work type:
http://<youripaddress>:4711

When prompted for the password its the password you used to create the md5sum, not the md5sum password.

---

### Post by Al_maverick on 2007-04-13
When I start the amuleweb I get this error.

> WSThread: Thread started
WSThread: could not create socket on :4712


Any ideas?

---

### Post by xhaos on 2007-04-17
it means that you have something else using this port, maybe you are running mule 2 times?

---

### Post by Al_maverick on 2007-04-19
Only amuled was running. I quit amule client before running the how-to.
I even changed the port in amule.conf and remote.conf to another port, and I got the same error.
weird :confused:

I modified it to run on port 4720. I get this from netstat

> al@maverick:/etc/default$ sudo netstat -p | grep 4720
tcp        0      0 localhost:4720          localhost:39219         ESTABLISHED6466/amuled
tcp        0      0 localhost:39219         localhost:4720          ESTABLISHED6469/amuleweb


---

### Post by Al_maverick on 2007-04-21
I found what the problems were:

1- when running amuled, it would also start amuleweb. That way, when I tried to run it on the second console, it couldnt create the socket because the previous instance of amuleweb had already taken it.
2- The ECport and the amuleweb port were the same. I changed the ECPort back to 4712 and left the amuleweb port on 4720.

Voila! Now I can connect to amuleweb on 4720.

Thanks a lot for the howto. I had a few glitches, but its working now. :)

---

### Post by brainst0rm on 2007-07-22
I have a problem with amuled. I can start it, and amuleweb works (I can connect to it), but it tells me that is not connected, indeed I cannot do any search...

Here the output of amuled
```
amuled: OnInit - starting timer
Initialising aMule
Checking if there is an instance already running...
No other instances are running.
Loading temp files from /home/ubuntu/.aMule/Temp.

All PartFiles Loaded.
ListenSocket: Ok.

*** TCP socket (ECServer) listening on 0.0.0.0:4712
*** Server UDP socket (TCP+3) at 0.0.0.0:4665
*** TCP socket (TCP) listening on 0.0.0.0:4662
*** Client UDP socket (extended eMule) at 0.0.0.0:4672
Empty dir /home/ubuntu/.aMule/Incoming shared
```

and amuleweb

```
This is amuleweb 2.1.0

Creating client...
Succeeded! Connection established to aMule 2.1.0

--------------------------------------
|          aMule Web Server          |
--------------------------------------

Use 'Help' for command list

Web Server: Started
aMuleweb$ 
WSThread: Thread started
WSThread: created socket listening on :4711
```

Thanks.

---

### Post by 0x45455844 on 2007-10-08
i get the following error after logging in into amuleweb

```

02:25:47 PM: Error: can't open file '/usr/share/amule/webserver/php-default/black.gif' (error 2: No such file or directory)
CFileImage: failed to open /usr/share/amule/webserver/php-default/black.gif
Segmentation fault (core dumped)

```

and there are a lot of them, when trying to put some image by that path, another one isn't found. what's wrong with it?

---

### Post by KubuntuKilledMe on 2007-10-08
In my experience, amuleweb crashes waaaay too often for use. I use amulegui instead to control the daemon.

---

### Post by chopsueysensei on 2008-03-23
> **0x45455844 said:**
> i get the following error after logging in into amuleweb

```

02:25:47 PM: Error: can't open file '/usr/share/amule/webserver/php-default/black.gif' (error 2: No such file or directory)
CFileImage: failed to open /usr/share/amule/webserver/php-default/black.gif
Segmentation fault (core dumped)

```

and there are a lot of them, when trying to put some image by that path, another one isn't found. what's wrong with it?

Hi.
I don't know if you still read this, but I've read this problem is fixed in version 2.2.0.
See ya.

---

### Post by Moonshiner on 2008-06-02
I'm using amuled with amuleweb running on Hardy machine and controlled through web-interface from Windoze machine. I'd prefer to use amulegui, but it's Windoze version refused to work on my PC somehow. Web-interface works, but it's still somewhat buggy. For example, the sorting of the columns does work in "transfers", but not in "servers", the filtering of downloads by "Waiting/Downloading/ etc" doesn't work at all, not mention the lack of features compared to gui...

---

### Post by Sniffer on 2008-06-10
Have a question on this topic

I have just a hardy server terminal mode, the amule web / daemon that you install support downloading files over 4GB???

Or do i need to install CVS instead??

Thanks

---

### Post by chache on 2008-06-12
Thanks dude, that's what I am looking for!! Thank you

---

### Post by Endolith on 2009-02-27
When I follow these directions, I get > Firefox can't establish a connection to the server at localhost:4711.  If I connect to [http://localhost:4712/](http://localhost:4712/), I get a blank white page.

---

### Post by mathfeel on 2009-03-29
Hi, I am trying to do the same thing. amuled seems started correctly:
```
$ sudo -u p2p amuled
amuled: OnInit - starting timer
Initialising aMuled 2.2.3 using wxGTK2 v2.8.9
Checking if there is an instance already running...
No other instances are running.
HTTP download thread started
ListenSocket: Ok.
Loading temp files from /Export/p2p/Temp.

All PartFiles Loaded.
No shareable files found in directory: /Export/p2p/Incoming
Host: amule.sourceforge.net:80
URL: http://amule.sourceforge.net/lastversion
Response: 200 (Error: 0)
Download size: 6
HTTP download thread ended

```

but still can't connect
```

$ amulecmd -p 4712 -h localhost
This is amulecmd 2.2.3

Creating client...
ReadPacket: packet have invalid flags 0
Connection Failed. Unable to connect to localhost:4712
```

any idea?

---

### Post by NeonRush on 2009-04-12
I've been searching forever, maybe someone can help me. I'm writing a program that interfaces with amulecmd and runs kad searches for me. I built into it the ability to run "amuled -f" and it's working great, but there's an issue.

It would seem that because I'm running kad searches, as opposed to local or global, amuled needs to be running for a while to build up a list of useful peers. I would revert back to local, preferably global, but don't want all the crap results that come back.

My question it would seem is how do I run amuled at boot so that by the time I actually use my app amule has had time to build a kad list. I'm running Intrepid and there's no "Startup Applications" type program that I can find.

Thanks

---

