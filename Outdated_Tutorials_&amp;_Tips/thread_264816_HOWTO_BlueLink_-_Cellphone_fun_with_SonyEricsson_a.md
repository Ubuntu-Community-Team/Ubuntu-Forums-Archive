---
title: "HOWTO: BlueLink - Cellphone fun with SonyEricsson and linux"
date: 2006-09-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Laterix on 2006-09-25
I'm here to announce the first release of my [BlueLink project]("http://www.taimila.com/bluelink/"). BlueLink is a daemon that connects to cell phone via bluetooth and is aware of phone's state. For example when your cell phone rings, BlueLink displays notification bubble on your desktop. [**See screenshot**](http://users.utu.fi/ljtaim/pics/shot-1.jpg).

At the moment BlueLink works only with some of the SonyEricsson models, but the software is designed so that it's relatively easy to add support also for Nokia, Samsung etc. phone. If you are C++ programmer and interested, please check out the [developement section]("http://www.taimila.com/bluelink/development.php") of the BlueLink site.

Now, I need testers. BlueLink should work with the following SonyEricsson series: *K750 series*, *W800 series*, *Z520 series*, *W600 series*, *W550 series*, *W900 series* and *W810 series*. I have only K750i model, so I've tested it only with that.

**What do you need?**
[LIST]
[*]SonyEricsson cell phone
[*]Working Bluetooth device on your computer
[/LIST]

**Howto install and configure BlueLink**
[LIST=1]
[*][Download source package]("http://sourceforge.net/project/showfiles.php?group_id=177813") from Sourceforge to your home directory.

[*]Extract package to your home directory and enter *bluelink* directory.
```

cd~
tar zxfv bluelink-v0.1.tar.gz
cd bluelink

```

[*]Install dependencies with apt-get.
```

sudo apt-get install libnotify-dev libbluetooth1-dev

```

[*]Compile BlueLink with make. This creates a executable file named *bluelink*.
```

make

```
    
[*]Copy configuration files to your home directory. Give the following command in bluelink directory
```
cp .bluelink ~
```
    
[*]Move bluelink executable file where every you want. For example to /usr/bin and make sure that it is executable.
```

sudo mv bluelink /usr/bin
sudo chmod 755 /usr/bin/bluelink 

```
 
[*]Move to ~/.bluelink directory and open *bluelink.conf* file with your favourite text-editor. Just add your phone's bluetooth address to
allowed devices. You can get this address for example with hcitool. Just give command *hcitool scan* in terminal. And make sure your phone's bluetooth is enabled and that your phone is visible to other devices.
```

cd ~/.bluelink
gedit bluelink.conf

```
 
[*]Create a separate configuration file for your cell phone. You can do this by copying *template.conf* to *00:11:22:AA:BB:CC.conf* where 00:11:22:AA:BB:CC is your phone's bluetooth address.
```

cp template.conf "00:11:22:AA:BB:CC.conf"

```
  
[*]Edit your phone's configuration file. This should be straight forward. If not, ask here and I'll explain what to do.
 
[*]Execute bluelink and enjoy! :) Check out --help parameter for more options
```

bluelink

```
[/LIST]

**Notes**
This is my first Linux program and also my first C++ program ever. This is also the very first Alpha release, so expect that something might be broken. It works fine on my computer, but that doesn't tell much. I hope you try it and give me feedback, bug notes, feature requestes etc.

---

### Post by aknapp on 2006-09-25
I have a z520a, here's whats happening

I get a message on my phone that says "Unknown wants to use your phone as a modem, allow - yes or no?" I say yes and then allow always. Then it says "Add knapper-desktop to your devics?" If I hit no the connection dies, but if I hit yes it asks for a keycode, I don't know where to find this code.

---

### Post by Laterix on 2006-09-25
Ok, you have to pair your phone with your computer and make your computer to trusted device in your phone. Computers code is in /etc/bluetooth/pin file. Edit the file and replace the default 1234 with the code you want to. After that restart bluetooth with the command 
```

sudo /etc/init.d/bluez-utils restart

```
Now take your phone and search for devices and when it finds your computer add it to your devices and make it trusted (trust always or something like that). When it asks the pin code just give the some code you put in the /etc/bluetooth/pin file.

This should do the trick.

---

### Post by aknapp on 2006-09-25
Ok, I have tried that. I looked in the pin file and it shows "1234". I did as you said and added the device in my phone, only, when I go to put in the pin (1234) it says Connection failed, retry? yes or no?

---

### Post by Laterix on 2006-09-25
:( hmm... sounds weird. I have to admit that I don't know much about pairing in linux. That's the way worked for me. Pairing seems to be a problem for many users. Search ubuntuforums for "pairing" and "bluetooth". You should find useful threads. I hope you get the paring to work!

---

### Post by rarstar on 2006-09-25
how do i find the address of my phone?

---

### Post by Laterix on 2006-09-25
> **rarstar said:**
> how do i find the address of my phone?
Make sure that your phone's bluetooth is enabled and device is set visible and then type in terminal
```

hcitool scan

```

---

### Post by michaelp on 2006-09-29
You should add an rss feed to your page, so we can follow this project.

Looks promising :)

---

### Post by Laterix on 2006-09-29
> **michaelp said:**
> You should add an rss feed to your page, so we can follow this project.

Looks promising :)

Good idea. Too bad, that I have no idea how to create RSS feed.

---

### Post by Laterix on 2006-10-09
I've been reported that BlueLink also works with Sony Ericsson K800i phone.

---

### Post by Joshua Hesketh on 2006-10-13
Hey,

This looks like a very promising project but unfortunately I am having little luck getting it to work.

I am using edgy with the latest updates and when running "Bluetooth File Sharing" bluelink fails to connect to my device with this error:

```
josh@Josh-Laptop:~$ sudo bluelink --debug
DEBUG: Opening file /home/josh/.bluelink/bluelink.conf
DEBUG: Allowed phone: 00:16:20:41:5B:D1
DEBUG: Searching for bluetooth devices...
DEBUG: Found 2 device(s).
DEBUG: Number of currently active phone: 0
DEBUG: Connect to the phone 00:16:20:41:5B:D1
DEBUG: Opening file /home/josh/.bluelink/00:16:20:41:5B:D1.conf
DEBUG: Opening connection to SonyEricsson phone
DEBUG: Couldn't open socket to device: 00:16:20:41:5B:D1
Error: Connecting phone failed!
DEBUG: Found 2 device(s).
DEBUG: Number of currently active phone: 0
DEBUG: Connect to the phone 00:16:20:41:5B:D1
DEBUG: Opening file /home/josh/.bluelink/00:16:20:41:5B:D1.conf
DEBUG: Opening connection to SonyEricsson phone
DEBUG: Couldn't open socket to device: 00:16:20:41:5B:D1
Error: Connecting phone failed!
Closing BlueLink...
Plase wait or press CTRL+C for quick and dirty exit.
DEBUG: Stopped scanning bluetooth devices.

```

Without "Bluetooth File Sharing" here is the output of the terminal:

```
josh@Josh-Laptop:~$ sudo bluelink --debug
DEBUG: Opening file /home/josh/.bluelink/bluelink.conf
DEBUG: Allowed phone: 00:16:20:41:5B:D1
DEBUG: Searching for bluetooth devices...
DEBUG: Found 2 device(s).
DEBUG: Number of currently active phone: 0
DEBUG: Connect to the phone 00:16:20:41:5B:D1
DEBUG: Opening file /home/josh/.bluelink/00:16:20:41:5B:D1.conf
DEBUG: Opening connection to SonyEricsson phone
DEBUG: Start monitoring RFCommSocket...
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
terminate called after throwing an instance of 'Exception'
Aborted (core dumped)

```

My guess is that bluelink is trying to prompt my phone for a handshake here, but fails. I see a quick second of bluetooth activity on my phone before the program fails. My phone doesn't bring up any pairing key prompt or anything (although my phone should already be paired so this may not be an issue).

My phone is the Sony Ericsson W800i, which is based on the K750i model (nearly exactly the same, just with latter software, and a different case).

I have tried running the program from root and as a user with no success. Any help is appreciated.

Cheers,
Josh

---

### Post by Joshua Hesketh on 2006-10-13
Well after booting up my laptop the next day it seems to "justs work". I don't think I changed anything, but it seems reasonably stable. The only issue is that I have to start the "Bluetooth File Sharing" applet after bluelink. No biggy ;)

Great project mate, keep up the good work.

Cheers,
Josh

---

### Post by Laterix on 2006-10-14
> **Joshua Hesketh said:**
> Well after booting up my laptop the next day it seems to "justs work". I don't think I changed anything, but it seems reasonably stable. The only issue is that I have to start the "Bluetooth File Sharing" applet after bluelink. No biggy ;)

I'm glad you got it working. My internet was down couple of days and I wasn't able to reply. I have the same problem with "Bluetooth file sharing" and I don't know why that is. Unfortunately I don't have much time for the project right now. I made a quick hack to pause banshee during calls, but I needs to be written again for release.

---

### Post by LucasLinard on 2006-10-15
Hi,
I'm having trouble to install it.
I didn't find libbluetooth1-dev. I found libbluetooth2-dev and installed it.
when I typed "make" I got the following error:
> lucas@ubuntu:~/bluelink$ make
g++ -Wall -g main.cpp -o bluelink `pkg-config libnotify --cflags --libs` -l bluetooth -l pthread
SonyEricsson.cpp: In member function ‘virtual void SonyEricsson::handleReceivedMessage(std::string)’:
SonyEricsson.cpp:88: warning: format ‘%d’ expects type ‘int*’, but argument 3 has type ‘ccstatus*’
SonyEricsson.cpp:100: warning: format ‘%d’ expects type ‘int*’, but argument 4 has type ‘ccstatus*’
SonyEricsson.cpp:100: warning: format ‘%d’ expects type ‘int*’, but argument 5 has type ‘calltype*’
SonyEricsson.cpp:100: warning: format ‘%d’ expects type ‘int*’, but argument 7 has type ‘exitcause*’
SonyEricsson.cpp:142: warning: format ‘%d’ expects type ‘int*’, but argument 4 has type ‘ccstatus*’
SonyEricsson.cpp:142: warning: format ‘%d’ expects type ‘int*’, but argument 5 has type ‘calltype*’
main.cpp: At global scope:
main.cpp:109: error: expected declaration before ‘}’ token
make: ** [all] Erro 1

Can you help me?

---

### Post by Joshua Hesketh on 2006-10-15
> **LucasLinard said:**
> Hi,
I'm having trouble to install it.
I didn't find libbluetooth1-dev. I found libbluetooth2-dev and installed it.
when I typed "make" I got the following error:

Can you help me?
I had the same problem when I tried to compile it.
 
My solution was to open up main.cpp and remove the '}' token on line 109 (the very last one).
 
From the comment in the code it seems that it was designed as a work around to some error, but it seems to be causing more problems.

---

### Post by Scotty B. on 2006-10-18
> **Joshua Hesketh said:**
> I had the same problem when I tried to compile it.
 
My solution was to open up main.cpp and remove the '}' token on line 109 (the very last one).
 
From the comment in the code it seems that it was designed as a work around to some error, but it seems to be causing more problems.

I'm encountering the same problem:

> g++ -Wall -g main.cpp -o bluelink `pkg-config libnotify --cflags --libs` -l bluetooth -l pthread
SonyEricsson.cpp: In member function ‘virtual void SonyEricsson::handleReceivedMessage(std::string)’:
SonyEricsson.cpp:88: warning: format ‘%d’ expects type ‘int*’, but argument 3 has type ‘ccstatus*’
SonyEricsson.cpp:100: warning: format ‘%d’ expects type ‘int*’, but argument 4 has type ‘ccstatus*’
SonyEricsson.cpp:100: warning: format ‘%d’ expects type ‘int*’, but argument 5 has type ‘calltype*’
SonyEricsson.cpp:100: warning: format ‘%d’ expects type ‘int*’, but argument 7 has type ‘exitcause*’
SonyEricsson.cpp:142: warning: format ‘%d’ expects type ‘int*’, but argument 4 has type ‘ccstatus*’
SonyEricsson.cpp:142: warning: format ‘%d’ expects type ‘int*’, but argument 5 has type ‘calltype*’


Except, no error in the Main.cpp file. :-k

---

### Post by Joshua Hesketh on 2006-10-18
> **Scotty B. said:**
> I'm encountering the same problem:



Except, no error in the Main.cpp file. :-k

That output is all warnings, no errors. That means you should have successfuly compiled it and can complete the next installation steps.

---

### Post by Laterix on 2006-10-18
> **Joshua Hesketh said:**
> I had the same problem when I tried to compile it.
 
My solution was to open up main.cpp and remove the '}' token on line 109 (the very last one).
 
From the comment in the code it seems that it was designed as a work around to some error, but it seems to be causing more problems.

yes, this is the solution. In dapper it won't compile without that bracket, but in Edgy it won't compile if the bracket is there. :) I'm not sure why that is.

---

### Post by mhueting on 2006-10-18
When i try to connect my phone (Ericsson w800i) I get the following error:
```

DEBUG: Opening file /home/moos/.bluelink/bluelink.conf
DEBUG: Allowed phone: 00:11:22:AA:BB:CC
DEBUG: Allowed phone: 00:16:20:2E:6B:C4
DEBUG: Searching for bluetooth devices...
DEBUG: Found 1 device(s).
DEBUG: Number of currently active phone: 0
DEBUG: Connect to the phone 00:16:20:2E:6B:C4
DEBUG: Opening file /home/moos/.bluelink/00:16:20:2E:6B:C4.conf
DEBUG: Opening connection to SonyEricsson phone
DEBUG: Start monitoring RFCommSocket...
terminate called after throwing an instance of 'FileException'
Aborted

```

Do you know a solution to this? I'm fairly new to bluetooth 8)

---

### Post by Laterix on 2006-10-18
> **mhueting said:**
> When i try to connect my phone (Ericsson w800i) I get the following error:
```

DEBUG: Opening file /home/moos/.bluelink/bluelink.conf
DEBUG: Allowed phone: 00:11:22:AA:BB:CC
DEBUG: Allowed phone: 00:16:20:2E:6B:C4
DEBUG: Searching for bluetooth devices...
DEBUG: Found 1 device(s).
DEBUG: Number of currently active phone: 0
DEBUG: Connect to the phone 00:16:20:2E:6B:C4
DEBUG: Opening file /home/moos/.bluelink/00:16:20:2E:6B:C4.conf
DEBUG: Opening connection to SonyEricsson phone
DEBUG: Start monitoring RFCommSocket...
terminate called after throwing an instance of 'FileException'
Aborted

```

Do you know a solution to this? I'm fairly new to bluetooth 8)

Well, it's because my code sucks :) But, I think you have enabled logging, but the log file doesn't exists. Yes, it really should create one but it doesn't. So turn off logging or create empty file for the log.

---

### Post by alejandrops on 2006-10-25
amazing idea!
is one of my dream apps! :)
hope it will work with nokia soon.

---

### Post by rarstar on 2006-11-12
hi, i get this error when trying to install the dependencies...

E: Couldn't find package libbluetooth1-dev

---

### Post by Joshua Hesketh on 2006-11-12
> **rarstar said:**
> hi, i get this error when trying to install the dependencies...

E: Couldn't find package libbluetooth1-dev

The tutorial is made for dapper, the libbluetooth1-dev package is out of date. Try installing libbluetooth2-dev and it should work.

```
sudo apt-get install libnotify-dev libbluetooth2-dev
```

Cheers,
Josh

---

### Post by Aetherius on 2006-11-18
your site is ...... missing...... my friend

---

### Post by Laterix on 2006-11-19
> **Aetherius said:**
> your site is ...... missing...... my friend

Damn, your right! How did this happened. I have 25Gb/month limit...

---

### Post by Ago12 on 2006-11-20
> **Laterix said:**
> Damn, your right! How did this happened. I have 25Gb/month limit...
It works now ;)

Your app looks promising! :)

Wow, I have been waiting for something like that for ages :)

But I have a problem: I'm on edgy, I've installed libnotify2, but whan I compile I have the same warnings as above:

> g++ -Wall -g main.cpp -o bluelink `pkg-config libnotify --cflags --libs` -l bluetooth -l pthread
SonyEricsson.cpp: In member function &#8216;virtual void SonyEricsson::handleReceivedMessage(std::string)&#8217;:
SonyEricsson.cpp:88: warning: format &#8216;%d&#8217; expects type &#8216;int*&#8217;, but argument 3 has type &#8216;ccstatus*&#8217;
SonyEricsson.cpp:100: warning: format &#8216;%d&#8217; expects type &#8216;int*&#8217;, but argument 4 has type &#8216;ccstatus*&#8217;
SonyEricsson.cpp:100: warning: format &#8216;%d&#8217; expects type &#8216;int*&#8217;, but argument 5 has type &#8216;calltype*&#8217;
SonyEricsson.cpp:100: warning: format &#8216;%d&#8217; expects type &#8216;int*&#8217;, but argument 7 has type &#8216;exitcause*&#8217;
SonyEricsson.cpp:142: warning: format &#8216;%d&#8217; expects type &#8216;int*&#8217;, but argument 4 has type &#8216;ccstatus*&#8217;
SonyEricsson.cpp:142: warning: format &#8216;%d&#8217; expects type &#8216;int*&#8217;, but argument 5 has type &#8216;calltype*&#8217;

And when I run it, evrything looks fine (a popup appears, telling that it is connected), but:

> bluelink --debug
DEBUG: Opening file /home/fabien/.bluelink/bluelink.conf
DEBUG: Allowed phone: 00:12:EE:73:F3:C6
DEBUG: Searching for bluetooth devices...
DEBUG: Found 1 device(s).
DEBUG: Number of currently active phone: 0
DEBUG: Connect to the phone 00:12:EE:73:F3:C6
DEBUG: Opening file /home/fabien/.bluelink/00:12:EE:73:F3:C6.conf
DEBUG: Opening connection to SonyEricsson phone
DEBUG: Start monitoring RFCommSocket...
DEBUG: Opening file /home/fabien/.bluelink/libnotify/avatars.conf
DEBUG: Start initializing phone...
DEBUG: Sending message: AT&F
DEBUG: Received:AT&F
DEBUG: Received:OK
DEBUG: Sending message: ATE0
DEBUG: Received:ATE0
DEBUG: Received:OK
DEBUG: Sending message: AT+CSCS="UTF-8"
DEBUG: Received:OK
DEBUG: Sending message: AT+CLIP=1
DEBUG: Received:OK
DEBUG: Sending message: AT*EIPS=1,1
DEBUG: Received:OK
DEBUG: Sending message: AT*EIPS=2,1
DEBUG: Received:OK
DEBUG: Sending message: AT*ECAM=1
DEBUG: Received:OK
DEBUG: Sending message: AT+CNMI=2,1
DEBUG: Received:OK
DEBUG: Sending message: AT+CSIL=1
DEBUG: Received:OK
DEBUG: Libnotify received event.
DEBUG: Initializing phone completed.
DEBUG: Received:RING
DEBUG: Received:*ECAV: 1,6,1
DEBUG: Received:+CLIP: "",161,,,""
DEBUG: PhoneEvent INCOMING_CALL
DEBUG: Libnotify received event.
Error: Couldn't display notification!
DEBUG: Received:RING
DEBUG: Received:+CLIP: "",161,,,""
DEBUG: Received:RING
DEBUG: Received:+CLIP: "",161,,,""
DEBUG: Received:*ECAV: 1,0,1,08,222
DEBUG: PhoneEvent CALL_MISSED
DEBUG: Libnotify received event.

** ERROR **: file dbus-gproxy.c: line 2123 (dbus_g_proxy_begin_call_internal): assertion failed: (pending != NULL)
aborting...
Abandon

And no notification :(

It is probably a problem with libnotify, but I cant tell why :(

---

### Post by Ago12 on 2006-11-20
One more thing: outgoing calls are ok...

bah?

---

### Post by Laterix on 2006-11-22
I'm sorry to hear that. I have tested BlueLink only with Dapper so far. Sounds strange that outgoing calls would work, but incoming not. I really don't know how to help at the moment. Except that warnings in compiling is normal and they are not serious.

I wish I would have more time to develope BlueLink... :neutral:

---

### Post by Ago12 on 2006-11-22
And I wish I knew anything about coding! (or some time to learn) :D

Anyway, I'll wait, or not use it :)

Thanks anyway ;)

---

### Post by bonden on 2006-12-27
I had the same problem as Ago12 at first, but the problem suddenly disappeared. It works fine now with Ubuntu Edgy and SE w800i

---

### Post by Joshua Hesketh on 2006-12-27
I use bluelink every day in edgy, it is a very nice concept be can be somewhat unstable. I more or less run it and when it works it works and when it doesn't it doesn't and I live with that. If I get some time I might see if I can help contribute any code to make it more stable in the future.

- Josh

---

### Post by Laterix on 2006-12-29
> **Joshua Hesketh said:**
> I use bluelink every day in edgy, it is a very nice concept be can be somewhat unstable. I more or less run it and when it works it works and when it doesn't it doesn't and I live with that. If I get some time I might see if I can help contribute any code to make it more stable in the future.

It would be great if someone would have time to make it better. Unfortunately I don't have time for that. Could you tell me when it doesn't work? I know at least that it needs to be executed before Gnome Obex server.

---

### Post by undiaperfecto on 2007-05-08
HOWTO for feisty??? :(

---

### Post by mwerlberger on 2007-05-10
Sounds really cool. I defenitely have a look at it at the weekend. Maybe when i have time i will have a look at the code too.

Hopefully it works with my W810i :-).

Regards,
 Manuel

---

