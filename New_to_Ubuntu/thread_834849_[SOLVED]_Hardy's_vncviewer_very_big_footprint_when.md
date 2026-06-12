---
title: "[SOLVED] Hardy's vncviewer very big footprint when active: way to dial it down, or us"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by swarup on 2008-06-19
When I use the default vncviewer in Hardy, i.e. when someone accesses my desktop remotely to see something on my screen, then it shoots my netgear dongle immediately into high gear so that the little blue light is flashing really really quickly as though huge amounts of data are being transferred. Even if there is just simple text on my screen with no such need for exorbitant data transfer. It puts such huge demand on the data transfer system, that my whole computer runs slowly for as long as the remote desktop is connected. 

If I have the very same text on my screen, but am booted into Puppy instead of Ubuntu, then when someone accesses my computer remotely to see my screen, there is no resource drain at all.

Puppy uses x11vnc server ([http://www.murga-linux.com/puppy/viewtopic.php?t=27424](http://www.murga-linux.com/puppy/viewtopic.php?t=27424)) instead of vncviewer. So I am wondering, in Ubuntu is there some way either to switch from vncviewer to x11vnc server, or to dial down the data transfer rate when using vncviewer so it is not so demanding on my computer?

---

### Post by Happy_Man on 2008-06-19
Why not just use x11vnc on Ubuntu?

```
sudo apt-get install x11vnc
```

---

### Post by cariboo on 2008-06-19
You could also use the builtin remote desktop server as it is based on vnc. Just go to System-->Preferences-->Remote Desktop and set the options you want.

Jim

---

### Post by swarup on 2008-06-19
> **Happy_Man said:**
> Why not just use x11vnc on Ubuntu?

```
sudo apt-get install x11vnc
```

Excellent. Thank you. :)
I should have known it was so easy!

I've installed it, and it seems to be running entirely as a command line application. That is, to start up x11vnc I will have to do
```

x11vnc -rfbauth /home/swarup/.vnc/passwd
```

And to stop x11vnc I will have to do ctrl-c in terminal window. 

Is this the only way to do this? Or is there some way to have it incorporated as a GUI or at least not to have such a complex command line order for opening it. (I could see typing "x11vnc" in the command line, that is easy enough. But if you do that it gives you all sorts of warnings and then announces you have started x11nvc without a password.)

---

### Post by RequinB4 on 2008-06-19
> **swarup said:**
> Excellent. Thank you. :)
I should have known it was so easy!

I've installed it, and it seems to be running entirely as a command line application. That is, to start up x11vnc I will have to do
```

x11vnc -rfbauth /home/swarup/.vnc/passwd
```

And to stop x11vnc I will have to do ctrl-c in terminal window. 

Is this the only way to do this? Or is there some way to have it incorporated as a GUI or at least not to have such a complex command line order for opening it. (I could see typing "x11vnc" in the command line, that is easy enough. But if you do that it gives you all sorts of warnings and then announces you have started x11nvc without a password.)

You can make a desktop or menu shortcut using the above code - on desktop, right click, create launcher, choose icon and launcher name, under command put 
```
x11vnc -rfbauth /home/swarup/.vnc/passwd
```
and a comment if you wish.  Same deal for a menu shortcut except you right click one of the menus, edit menus, go to the place you want it to be (I'd choose internet) and choose New Item...

---

### Post by swarup on 2008-06-20
> **RequinB4 said:**
> Same deal for a menu shortcut except you right click one of the menus, edit menus, go to the place you want it to be (I'd choose internet) and choose New Item...

Ok, great. :) This is what I have now just done. I created a launcher, called it x11vnc server, put the command line (x11vnc -rfbauth /home/swarup/.vnc/passwd) into it, and placed the launcher as a menu item under Applications -> Internet. 

Now, two questions:

1. When I click on the launcher, how do I know whether it has worker or not? When I did the command in the terminal window itself, it would give me a whole bunch of output and ultimately tell me the VNC desktop address of the computer, so others could address it and access it. But when I do this via the menu item launcher, I don't get any sign of whether something has been accomplished or not.

2. If it did work for activating x11vnc server, then when later I want to stop it, how do I do so? When it was done in terminal window, I would do "ctrl-c" and that would x11vnc. But now using this launcher I've made, do I still have to go into a terminal windows to stop it? Will it even work to do "ctrl-c" since I didn't start x11vnc in the terminal window? --Is there another way to stop it, now that I've created a launcher to start it? Perhaps I need another launcher to stop it? (If so, then how do I put "ctrl-c" in the launcher's command line?)

---

### Post by krunge on 2008-06-20
> **swarup said:**
> Ok, great. :) This is what I have now just done. I created a launcher, called it x11vnc server, put the command line (x11vnc -rfbauth /home/swarup/.vnc/passwd) into it, and placed the launcher as a menu item under Applications -> Internet. 

Now, two questions:

1. When I click on the launcher, how do I know whether it has worker or not? When I did the command in the terminal window itself, it would give me a whole bunch of output and ultimately tell me the VNC desktop address of the computer, so others could address it and access it. But when I do this via the menu item launcher, I don't get any sign of whether something has been accomplished or not.

2. If it did work for activating x11vnc server, then when later I want to stop it, how do I do so? When it was done in terminal window, I would do "ctrl-c" and that would x11vnc. But now using this launcher I've made, do I still have to go into a terminal windows to stop it? Will it even work to do "ctrl-c" since I didn't start x11vnc in the terminal window? --Is there another way to stop it, now that I've created a launcher to start it? Perhaps I need another launcher to stop it? (If so, then how do I put "ctrl-c" in the launcher's command line?)

There is a remote control command to stop x11vnc:
```

x11vnc -R stop

```
this will stop an already running one.

If you don't do this from inside a terminal on the Desktop (e.g. you ssh in to stop x11vnc) you will need to add '-display :0' to the above line.

Also typing 'killall x11vnc' in a terminal should work too. You could put either one in a launcher if you wanted to.

x11vnc also has a little used gui mode.  It is a bit of an ugly hack, but it works for some people.  So you could put this in your launcher:

```

x11vnc -gui tray -rfbauth /home/swarup/.vnc/passwd

```
You will probably need to add tk:
```

apt-get install tk8.4

```
or something like that (just add the tk/wish program somehow).

That should put a little icon in the system tray that you can click on to change settings, stop it, etc.

If you try it let me know if it worked or not.

---

### Post by swarup on 2008-06-23
Yes, thank you very much. All I had to do was go into Package Manager and install tk8.4, then code "x11vnc -gui tray -rfbauth /home/swarup/.vnc/passwd", and the GUI appears on the upper panel. It seems to be working fine as well.

My question now is, that once I start up x11vnc, I am having difficulty getting it to be the host in a remote desktop session. As I am running Hardy, so the default host is Hardy's vncviewer. 

The person who wants to visit my desktop is also running Hardy, so he has the Remote Desktop Viewer with the autoFind feature (RDV 0.5.1 - Vinagre, the VNC client for the GNOME Desktop). When he clicks on "find" to see who is on-line that he can connect to, he sees my computer as available. But if he selects that ("swarup's remote desktop on swarup-laptop") then he connects to me via my vncviewer rather than the x11vnc server.

Now, when I start up x11vnc via the code you gave ( "x11vnc -gui tray -rfbauth /home/swarup/.vnc/passwd"), it gives a lot of code in the output and ultimately gives the information:

```
The VNC desktop is:      swarup-laptop:2
PORT=5902
```

So I thought, ok let me try having my friend access my computer using this above info, instead of using autofind. So in his vncview screen where it asks, "What machine do you want to connect to?", I had him put in "swarup-laptop:2" for the host, and 5902 for the port. (The default port in that window is 5900, but I had him change it to 5902.) Well, when he then clicks "connect", it answers something about that the host is closed. 

So I just need to know how I can get my x11vnc host (rather than Hardy's default vncviewer) to be available for access by my friend's computer.

---

### Post by krunge on 2008-06-24
> **swarup said:**
> 

My question now is, that once I start up x11vnc, I am having difficulty getting it to be the host in a remote desktop session. As I am running Hardy, so the default host is Hardy's vncviewer. 

I'm pretty sure you mean "vnc server" not "vncviewer" (both here and in earlier posts). The viewer is the client (i.e. the side where you view)
> 
So I thought, ok let me try having my friend access my computer using this above info, instead of using autofind. So in his vncview screen where it asks, "What machine do you want to connect to?", I had him put in "swarup-laptop:2" for the host, and 5902 for the port. (The default port in that window is 5900, but I had him change it to 5902.) Well, when he then clicks "connect", it answers something about that the host is closed. 

That should have worked.  What was the x11vnc output when your friend tried to connect? (please post all after the "PORT=5902").

Have your friend also try Tightvncviewer, just in case there is some incompatibility with vinagre.

I don't know how to disable the other VNC server you have running on 5900.    Look around in the desktop menus for "Remote Desktop ..." or something.

Also try using ps(1), top(1), and maybe lsof(1) to see if you can locate the process for that VNC server.  That may provide a clue to its name and how to disable it.

You may also have your host level firewall blocking port 5902.  Maybe "firestarter" is the name of the tool to configure your firewall.

---

### Post by swarup on 2008-06-24
> **krunge said:**
> I'm pretty sure you mean "vnc server" not "vncviewer" (both here and in earlier posts). The viewer is the client (i.e. the side where you view)

Yes, thank you. Now it is clear. That is what I meant.

> **krunge said:**
> That should have worked.  What was the x11vnc output when your friend tried to connect? (please post all after the "PORT=5902").

When my friend tries to connect, I do not see any further terminal output in my computer beyond what appeared at the time of my giving the command for x11vnc to start. Here is the terminal output after the PORT=5902 (all of it was there before he tried to connect):

```
The VNC desktop is:      swarup-laptop:2
PORT=5902

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

more info: http://www.karlrunge.com/x11vnc/#faq-client-caching


24/06/2008 07:45:50 gui: got SIGUSR1
24/06/2008 07:45:50 gui: ping succeeded.
24/06/2008 07:46:05 read X11VNC_REMOTE: qry=ping
24/06/2008 07:46:05 read X11VNC_REMOTE: ans=ping:swarup-laptop:0.0
24/06/2008 07:46:05 read X11VNC_REMOTE: cmd=client_info_sock:127.0.0.1:13037 ...
24/06/2008 07:46:05 client_info_sock to: 127.0.0.1:13037
24/06/2008 07:46:07 remote_cmd: will try to embed 0x4000084 in the system tray.
24/06/2008 07:46:07 tray_embed: using parent: tkx11vnc - swarup-laptop:0.0
```

When he then tries to connect by using "swarup-laptop:2" and Port 5902, he then gets the message: "connection to host 'swarup-laptop:2:5902' was closed". That is the same message that comes after one has been in a session with the working default Ubuntu Remote Desktop, and then ends it. After ending the session, one gets that very same message.

Now, when I set up x11vnc I did set it up with a password. But I assume that as per the usual convention, when he tries to connect it should ask him for the password and then connect him when he enters it.

> **krunge said:**
> Have your friend also try Tightvncviewer, just in case there is some incompatibility with vinagre.

I just searched Synaptic Package Manager for it. There is only one package, and it is called "xtightvncviewer". I assume that is the right one. I've installed it on his computer. When you then do "tightvncviewer" in terminal, it opens a tiny GUI on the desktop which says "vncserver" and has a window underneath it. I entered "swarup-laptop:2" in the window, and it gave the output: "couldn't convert 'swarup-laptop' to host address". 

```
krpa@krpa-desktop:~$ xtightvncviewer
Couldn't convert 'swarup-laptop' to host address
```

I then tried entering "swarup-laptop:2:5902" in that GUI window, and the following terminal window output appeared:
```

krpa@krpa-desktop:~$ xtightvncviewer
TightVNC viewer version 1.2.9

Usage: xtightvncviewer [<OPTIONS>] [<HOST>][:<DISPLAY#>]
       xtightvncviewer [<OPTIONS>] [<HOST>][::<PORT#>]
       xtightvncviewer [<OPTIONS>] -listen [<DISPLAY#>]
       xtightvncviewer -help

<OPTIONS> are standard Xt options, or:
        -via <GATEWAY>
        -shared (set by default)
        -noshared
        -viewonly
        -fullscreen
        -noraiseonbeep
        -passwd <PASSWD-FILENAME>
        -encodings <ENCODING-LIST> (e.g. "tight copyrect")
        -bgr233
        -owncmap
        -truecolour
        -depth <DEPTH>
        -compresslevel <COMPRESS-VALUE> (0..9: 0-fast, 9-best)
        -quality <JPEG-QUALITY-VALUE> (0..9: 0-low, 9-high)
        -nojpeg
        -nocursorshape
        -x11cursor

Option names may be abbreviated, e.g. -bgr instead of -bgr233.
See the manual page for more information.
krpa@krpa-desktop:~$
```

So that certainly looks more promising. But still, my desktop did not appear on his computer. And nor did it ask for my password. So it looks like something more is needed in order for the process to complete. Can you tell by looking at the above, what that would be?

> **krunge said:**
> I don't know how to disable the other VNC server you have running on 5900.    Look around in the desktop menus for "Remote Desktop ..." or something.

There is such a listing for "Remote Desktop" under preferences, but there is no option there to disable anything. Then under Applications -> Internet, there is an option for "Remote Desktop Viewer", but that of course is the client side and would not help us here.

> **krunge said:**
> Also try using ps(1), top(1), and maybe lsof(1) to see if you can locate the process for that VNC server.  That may provide a clue to its name and how to disable it.

None of those commands are recognizable to terminal, but if you type "top" then it does run the list of processes, along with cpu and memory usage etc. If I have my friend access my computer using the usual Ubuntu default way via vncviewer and vinagre, then the process for that in top is called "vino-server". Perhaps that is the name of the process you were looking for. Do you think it would need to be blocked in order for the x11vnc server to work?

> **krunge said:**
> You may also have your host level firewall blocking port 5902.  Maybe "firestarter" is the name of the tool to configure your firewall.

I was unaware that I even have a host level firewall. I tried typing "firestarter" in terminal, and it says 

```
The program 'firestarter' is currently not installed.  You can install it by typing:
sudo apt-get install firestarter
```

If after reading everything else I've sent above you think I need to install this and try it, then I will.

---

### Post by krunge on 2008-06-24
> **swarup said:**
> 
When my friend tries to connect, I do not see any further terminal output in my computer beyond what appeared at the time of my giving the command for x11vnc to start. Here is the terminal output after the PORT=5902 (all of it was there before he tried to connect):

...

When he then tries to connect by using "swarup-laptop:2" and Port 5902, he then gets the message: "connection to host 'swarup-laptop:2:5902' was closed". That is the same message that comes after one has been in a session with the working default Ubuntu Remote Desktop, and then ends it. After ending the session, one gets that very same message.

Ah, if x11vnc doesn't print anything when he tries to connect, that means the connection never reached x11vnc.  It will print out that a client is trying to connect.

Can your friend from his computer ping your machine or ssh to it?  That would show if there is some level of network connectivity.  From the rest of your post it appears "swarpup-laptop" does not resolve to an IP address.

What is your laptops IP address?  (type ifconfig to see).  Then try xtightvncviewer 192.168.1.20:2.  (replace 192.168.1.20 with the IP you find for it).

BTW, yes "xtightvncviewer" is what I was referring to.  Could be useful for testing connectivity.  It seems to give a better error message.

> None of those commands are recognizable to terminal, but if you type "top" then it does run the list of processes, along with cpu and memory usage etc. If I have my friend access my computer using the usual Ubuntu default way via vncviewer and vinagre, then the process for that in top is called "vino-server". Perhaps that is the name of the process you were looking for. Do you think it would need to be blocked in order for the x11vnc server to work?

Yes, you will need to disable vino-server.  That is the GNOME vnc server. I believe it is the one that gives the high load you mentioned in your post (I too noticed huge network load from it last time I tried it).

Somehow you enabled it, and now you have to figure out how to disable it.  Sorry I don't know what to try besides the menus.

---

### Post by swarup on 2008-06-24
You figured out the problem! :)

xtightvncserver could not work with the name "swarup-laptop". It only works with the actual IP address. As soon as I substituted swarup-laptop's IP address in instead of the word "swarup-laptop", then everything worked perfectly. That is all there was to it. And I didn't even have to disable vino-server.

I really like the way xllvnc server shows all the events in the terminal window, so you can see exactly what is happening. 

Now, one last question. Are there any variables in x11vnc server or xtightvncviewer which can be adjusted to put more or less load on the host computer? For example, when one starts up x11vnc server, among the code which comes in terminal window is this:

```
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

more info: http://www.karlrunge.com/x11vnc/#faq-client-caching
```

Does it sound like this pixel caching feature would help put less load on the host computer? And does the actual terminal command include the three dots (...) the way it appears above? (x11vnc -ncache 10 ...)

Here are some other lines from the terminal output, once the connection between the two computers was made. I am wondering whether any of these parameters could be varied, so as to put less load on the host computer (My goal is to have x11vnc make as small a demand as possible on the cpu and ram, and minimize the need for it to provoke the laptop fan to run):

1. bits per pixel in client (viewer) computer:

```
24/06/2008 22:39:16 Pixel format for client 192.168.0.102:
24/06/2008 22:39:16   32 bpp, depth 24, little endian

```

2. Network rate:

```
24/06/2008 22:39:16 Using tight encoding for client 192.168.0.102
24/06/2008 22:39:19 client 1 network rate 111.1 KB/sec (2371.2 eff KB/sec)
24/06/2008 22:39:19 client 1 latency:  7.6 ms
24/06/2008 22:39:19 dt1: 0.9326, dt2: 0.3805 dt3: 0.0076 bytes: 145437
24/06/2008 22:39:19 link_rate: LR_BROADBAND - 7 ms, 111 KB/s
24/06/2008 22:39:19 could not connect to ident: 192.168.0.102:113
24/06/2008 22:40:12 increased wireframe timeouts for slow network connection.
24/06/2008 22:40:12 netrate: 111 KB/sec, latency: 7 ms
24/06/2008 22:42:49 client_count: 0
24/06/2008 22:42:49 Restored X server key autorepeat to: 1
```

Here are some statistics that were produced once I cut the x11vnc connection. I don't know whether it may shed any light on the network load on the host computer:

```
24/06/2008 22:42:49 Client 192.168.0.102 gone
24/06/2008 22:42:49 Statistics             events    Transmit/ RawEquiv ( saved)
24/06/2008 22:42:49  ServerCutText       :      1 |        58/       58 (  0.0%)
24/06/2008 22:42:49  FramebufferUpdate   :    136 |         0/        0 (  0.0%)
24/06/2008 22:42:49  LastRect            :     13 |       156/      156 (  0.0%)
24/06/2008 22:42:49  tight               :   1418 |    755016/ 12427748 ( 93.9%)
24/06/2008 22:42:49  PointerPos          :     20 |       240/      240 (  0.0%)
24/06/2008 22:42:49  RichCursor          :     15 |     36000/    36000 (  0.0%)
24/06/2008 22:42:49  TOTALS              :   1603 |    791470/ 12464202 ( 93.7%)
24/06/2008 22:42:49 Statistics             events    Received/ RawEquiv ( saved)
24/06/2008 22:42:49  PointerEvent        :   1970 |     11820/    11820 (  0.0%)
24/06/2008 22:42:49  FramebufferUpdate   :    140 |      1400/     1400 (  0.0%)
24/06/2008 22:42:49  SetEncodings        :      1 |        52/       52 (  0.0%)
24/06/2008 22:42:49  SetPixelFormat      :      1 |        20/       20 (  0.0%)
24/06/2008 22:42:49  TOTALS              :   2112 |     13292/    13292 (  0.0%)
24/06/2008 22:42:49 destroyed xdamage object: 0x4200024
```

---

### Post by swarup on 2008-06-25
I've been using the x11vnc server all day today, and my colleague the xtightvncviewer. The system is far faster and less burdensome to the host computer, then the default Ubuntu Remote Desktop (vinagre).

I would like to make the xllvnc server even less burdensome if possible, as my laptop is old and it still has to work a bit, using the fan etc when x11vnc server is on. 

If I just do word processing in English in a text editor then the computer is quiet and relaxed. But if I type in Hindi (using SCIM), and on top of that have the spellchecker running, then along with x11vnc server that is quite a job. When I type in such a setting, the computer can't quite keep up and some of the letters appear a tad after I type them. But still, it is FAR better than it was with vinagre.

If you have any suggestions for trimming it down a bit based perhaps on the info I gave in my previous post, that would be great.

Add: I've figured out how to determine whether the guest computer requests permission to joint the host's vinagre server or the host's x11vnc server. It all depends on the way the guest computer makes the request from xtightvncserver. If in it's tiny gui for specifying the vnc server you want you just put the IP address, then it'll go to the host computer's vinagre. And if you put "IP address:2", then it will instead access the host's x11vnc server.

---

### Post by krunge on 2008-06-26
> **swarup said:**
> Does it sound like this pixel caching feature would help put less load on the host computer? And does the actual terminal command include the three dots (...) the way it appears above? (x11vnc -ncache 10 ...)

No, the "..." means any other options you want to supply (e.g.: your "-rfbauth /home/swarup/.vnc/passwd")

The -ncache method uses a lot of RAM (10X more for -ncache 10, e.g. 150MB instead of a normal 15MB).  So that may negatively impact your machine's performance... depends on how much RAM you have (you'll use 10X extra on the VNC viewer side as well).

However on a slow link (broadband or dialup) it can yield a really nice speedup because of the pixmap caching on the viewer side.

Also, if the caching is working well it can decrease the video card reading load (x11vnc reads the video card framebuffer).  Read the FAQ link mentioned for details why.

One other issue, the cached pixmaps are stored in the lower portion of the viewer for compatibility (and are visible if you scroll down).  This confuses most people.  
> 
I would like to make the x11vnc server even less burdensome if possible, as my laptop is old and it still has to work a bit, using the fan etc when x11vnc server is on. 

Maybe the -wait N option where N is time in milliseconds to wait between screen polls (default is 20 ms). That reduces load on the machine, but of course may lead to changes not being sent as soon.  More Info: [http://www.karlrunge.com/x11vnc/faq.html#faq-less-resource]("http://www.karlrunge.com/x11vnc/faq.html#faq-less-resource")

Also look on that page for 'ShadowFB'.  That gives a nice speedup and also reduces load, but it modifies your X server a bit.

> 
Add: I've figured out how to determine whether the guest computer requests permission to joint the host's vinagre server or the host's x11vnc server. It all depends on the way the guest computer makes the request from xtightvncserver. If in it's tiny gui for specifying the vnc server you want you just put the IP address, then it'll go to the host computer's vinagre. And if you put "IP address:2", then it will instead access the host's x11vnc server.

But I think this is only by pure luck it is :2.  My guess is you have vino-server running on port 5900 (VNC display ':0') and some **OTHER** vnc server running on port 5901 (VNC display ':1'); with those two ports already taken, x11vnc finds and uses port 5902 (VNC display ':2').

So ':2' may change if you reboot the machine, etc.  You can supply x11vnc with the option '-rfbport 5902' to force it to use VNC display ':2'.  I think you should get rid of those other two VNC servers you have running...

---

### Post by swarup on 2008-06-28
> **krunge said:**
> Maybe the -wait N option where N is time in milliseconds to wait between screen polls (default is 20 ms). That reduces load on the machine, but of course may lead to changes not being sent as soon.  More Info: [http://www.karlrunge.com/x11vnc/#faq-less-resource]("http://www.karlrunge.com/x11vnc/#faq-less-resource")

Also look on that page for 'ShadowFB'.  That gives a nice speedup and also reduces load, but it modifies your X server a bit.

Hey, that's really interesting stuff! Thanks for the info. :) 

There are also a few additional options in the paragraph you referred me to, for decreasing the use of system resources. Here is the actual para:

> Q-68: How can I make x11vnc use less system resources?

The -nap (now on by default) and "-wait n" (where n is the sleep between polls in milliseconds, the default is 30 or so) option are good places to start. Something like "-sb 15" will cause x11vnc to go into a deep-sleep mode after 15 seconds of no activity (instead of the default 60).

Reducing the X server bits per pixel depth (e.g. to 16bpp or even 8bpp) will further decrease memory I/O and network I/O. The ShadowFB X server setting will make x11vnc's screen polling less severe. Using the -onetile option will use less memory and use fewer shared memory slots (add -fs 1.0 for one less slot). 


One important question: How are these features implemented? Take for example, my terminal command for starting xllvnc server:
```

x11vnc -gui tray -rfbauth /home/swarup/.vnc/passwd
```

Any of the above features I want to implement, do I insert the respective code into the above command line? And does it matter where I place it in the order of the command (i.e. before or after "gui tray", or  "-rfbauth") ? For example:

1) The code "-nap" (they say "nap" is now on by default. So does putting "-nap" into the command line, turn it off? "On" is the resource-saving setting, right?);
2) "-wait n" (why did they say to use for that, "-sb 15"? They told to use the word "wait" and then put "sb" instead.) 
3) They say to try "reducing the X server bits per pixel depth". But they didn't tell the command for how to do it?

> **krunge said:**
> I think you should get rid of those other two VNC servers you have running...

1. Why do you feel I need to get rid of them? Do you think this will improve how x11vnc server functions?
2. As far as I know I only have the one other VNC server, called "vinagre" on the port 5900. I don't know of any other VNC server on my system.

---

### Post by krunge on 2008-07-01
> **swarup said:**
> 
Any of the above features I want to implement, do I insert the respective code into the above command line? And does it matter where I place it in the order of the command (i.e. before or after "gui tray", or  "-rfbauth")?

Yes, in the standard unix command way, you put the options you want to enable on the command line and in any order.
> 
1) The code "-nap" (they say "nap" is now on by default. So does putting "-nap" into the command line, turn it off? "On" is the resource-saving setting, right?);

The x11vnc documentation says use "-nonap" to turn it off.
> 
2) "-wait n" (why did they say to use for that, "-sb 15"? They told to use the word "wait" and then put "sb" instead.)

The "-sb" statement was intended to convey "-sb" is yet another option to try to reduce resource usage (i.e. in addition to, and independent of, "-nap").
>   
3) They say to try "reducing the X server bits per pixel depth". But they didn't tell the command for how to do it?

How to change the X server color depth depends alot on one's OS/distro and distro version (and likely the desktop being used as well).  There is no one command to do it.  It is a reconfiguration of the X server, and the desktop will need to be restarted for it to take affect.

Personally, I hand edit /etc/X11/xorg.conf and adjust the DefaultDepth setting of the "Screen" Section (e.g. set it to 16 instead of 24).  I am sure there are GUI ways to do this via clicking in the menus, but I don't know what they are.
> 
1. Why do you feel I need to get rid of them? Do you think this will improve how x11vnc server functions?

Previously it sounded like you wanted get rid of them, but couldn't find out how. If you intend to use them, then certainly keep them running. If you get rid of them, then x11vnc will get the default VNC port 5900, perhaps that will be convenient.
> 
2. As far as I know I only have the one other VNC server, called "vinagre" on the port 5900. I don't know of any other VNC server on my system.

I am willing to bet you must have had two running (one on port 5900 and another on port 5901).  Otherwise there is no reason for x11vnc to pick 5902 (it works its way up from 5900 until it finds a free one; one can force the setting with -rfbport).  Maybe the 5901 one is actually a stray x11vnc you started up but didn't kill.

The main point I wanted to make is that you can't count on x11vnc always taking port 5902 (VNC display :2 ). Use -rfbport 5902 if you want to force that setting.

BTW, I think you mean "vino-server".  "vinagre" is a Viewer (client) IIRC.

---

### Post by swarup on 2008-07-02
> **krunge said:**
> Yes, in the standard unix command way, you put the options you want to enable on the command line and in any order.

I see. So these settings could only be adjusted at the time of giving the command to start X11vnc server, right? --By adding these various features into the very command for starting up x11vnc server. That is, once the program is started and running a session, there wouldn't be any way to change the settings and experiment with them. Each time one wanted to experiment, one would have to close down x11vnc server and restart it, this time with different feature settings. Is this correct?

> **krunge said:**
> Personally, I hand edit /etc/X11/xorg.conf and adjust the DefaultDepth setting of the "Screen" Section (e.g. set it to 16 instead of 24).

I just went into that file to try changing it. But in the "Screen" section there is no line there for DefaultDepth:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Is the default set for 24 without having any such line here? And would I then have to add a line for it if I wanted to change it? If so, exactly how would the line read? (Something like DefaultDepth       "16"?)

---

### Post by swarup on 2008-07-03
I should add as a conclusion for this thread, that if anyone has an older computer and needs to preserve system resources, x11vnc server is a marvelous remote desktop tool. It allows one to turn down the sampling rate and memory usage so that it doesn't negatively affect one's computer's performance at all. Use the "wait", "sb", and "onetile" features and you'll have great performance with your older computer. The default setting for "wait" is 30 ms; I have set it to 100 or even 200, and it works great.

---

