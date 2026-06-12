---
title: "How to: Install XMMS2"
date: 2006-02-15
forum: Outdated Tutorials &amp; Tips
---

### Post by curtis on 2006-02-15
First add the XMMS 2 repositories to /etc/apt/sources.list

```
 
sudo gedit /etc/apt/sources.list

```
Then add

```

deb http://exodus.xmms.se/debian stable main

```
to the bottom of it.
And save it.

Then update the apt-get database.

```

sudo apt-get update

```

Then finally install the XMMS2 packages (And some extra codecs)

```

sudo apt-get install xmms2 xmms2-decoder-mad xmms2-decoder-vorbis

```

Then it should work via starting the xmms2 server.

```

xmms2d &

```

Then run the client

```

xmms2

```

To add a playlist you go into a directory with your MP3's or OGG's and run

```

xmms2 add file-to-play

```

Typing 
```

xmms2 help

```

Will show you a list of options.
I'll add how to add the entries in the GNOME/KDE menus a bit later.

---

### Post by Clark Nova on 2006-02-15
I tried to follow your instructions but I can't get it to work properly, I get this:

```
simon@Desktop:~$ sudo apt-get install xmms2 xmms2-decoder-mad xmms2-decoder-vorb is
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xmms2

```


Any idea?:???:  I'm still very much a novice so I copied and pasted your instructions into the console. I'm still trying to solve problems myself but it's a slow process :(

---

### Post by Lord Illidan on 2006-02-15
[quote=SiBuntu]I tried to follow your instructions but I can't get it to work properly, I get this:

```
simon@Desktop:~$ sudo apt-get install xmms2 xmms2-decoder-mad xmms2-decoder-vorb is
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xmms2

``` 

Any idea?:???:  I'm still very much a novice so I copied and pasted your instructions into the console. I'm still trying to solve problems myself but it's a slow process :([/quote] 
Did you add the repo? 
Add this line to your sources.list
```
 deb [http://exodus.xmms.se/debian]("http://exodus.xmms.se/debian") 
```
You might want to copy and paste it with vi or gedit.
stable main Then continue with ```
sudo apt-get update
```

---

### Post by curtis on 2006-02-15
Sorry I messed up the echo part.
Please re-try it.

---

### Post by zachtib on 2006-02-15
im confused, is there no gui for xmms2?

aha, apparently not. no wonder i couldnt find screenshots anywhere

---

### Post by curtis on 2006-02-15
No,
no graphical clients yet for GNOME or KDE.
It is quiet new though so it may take a while.

---

### Post by Metz on 2006-04-13
Will be attempting this install tonight. I'm currently using XMMS as it's the only thing that'll talk to my usb sound device (Logitech Wireless music system). MPD would be my prefered solution...I like the socket control, but I can't get it to talk to the device. XMMS2 will give me the daemon that I need running on the server, plus the remote handeling (including my bluetooth phone :))...so I'll try this asap.

---

### Post by maart on 2006-04-16
How can i install this GUI for xmms2?
[http://juxtapose.sourceforge.net/](http://juxtapose.sourceforge.net/)

---

### Post by Metz on 2006-05-05
Well.....I got XMMS2 working on my server, but after trying out a few clients, and either failing to get them working or no liking them much.....I set about creating my own.

The setup I run (as mentioned above) uses a wireless USB device to beam the sounds over to my speakers. I decided I wanted a web-client so that anyone connected to my internal network could control the player from their laptops or wifi-enabled phones, etc. To get this working, I had to grant the www-data user permission to access audio devices (and external media, which is where the music is stored, usb 200gb drive). 

Next was to create a .asoundrc file for the www-data user which pointed the output to pcm device 1 instead of zero. Again this worked fine.

I had started to write an xmms2 php module, but I've come across a couple of issues, and I get bored easily ;)...so for the sake of immediate results, I resorted to using exec and calling the xmms2 cli with instructions ;):)

End result is a bit of a Heath Robinson affair....but it works well. Had a party last sunday..server tucked in it's cupboard under the stairs, speakers in the garden, and a 10hour playlist. Didn't faulter once, and had people making requests and chaging the playlist all day long :):)

---

### Post by ranser on 2008-03-10
No GUI??!?!?! 
Why bother announce it then?? Who in his right mind would choose a command line based player over a GUI one??? Sometimes I here "linux people are crazy freaks!", and ocasionally I just see why... this is scarry, man....

---

### Post by kaivalagi on 2008-03-24
Come on Ranser, having the ability to control a music daemon using a separate gui isn't such a bad thing. It gives a bit of autonomy and keeps things lightweight. I would imagine we'll be seeing some network based server components for it soon so it can be used to stream music etc from a server with no frontend!

Take a look at this presentation for an intro into what it really does: [http://exodus.xmms.se/podcasts/01-fosdem_presentation.mov]("http://exodus.xmms.se/podcasts/01-fosdem_presentation.mov")
There are also gui's for it, which admittedly still need some work,  but they provide the necessary functionality and can be closed completely without your music stopping...

BTW, these "crazy freaks" as you put it, brought us a miriad of open source software...all of which _somebody_ finds a use for.

---

### Post by ranser on 2008-03-25
OK I overreacted a bit maybe, but still releasing a software for general public without GUI these days is somewhat like me installing a door to your home without any paint  on it and without handles. And then when you try to open it and fail I will say "well it is working U just need to know how". I am not saying they don't have any merit, it is just they should have finished what they started, otherwise it is pretty useless to many people and that's a shame...

---

### Post by kaivalagi on 2008-03-25
Ranser, you're are right in one aspect, when the xmms2 team released what they did, it would have made sense to create a frontend to go with it, even if it was a simple one. It could then form a basis for others to improve upon to produce something a bit more special. The main purpose of xmms2 is to form a base for client/server based music playing / collections etc.

As it stands there are several UI's for it still in development and somewhat working, however the uptake is slow and some of them that arguably work are not present in the gutsy repo's, which would have been nice.

Right now I think the best xmms2 frontend package available in the repo's for gutsy is esperanza, you might want to check it out....it doesn't have the features of say rhythmbox or listen but it's a start, and allows you to configure playlists which is what xmms2 is all about.

I like your avatar by the way! Much more symbolic than mine :)

---

### Post by rjdsmiths on 2008-05-27
When I Update [sudo apt-get update] i get tihis:

W: Failed to fetch [http://exodus.xmms.se/debian/dists/stable/main/binary-i386/Packages.gz](http://exodus.xmms.se/debian/dists/stable/main/binary-i386/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

Is it me or is it you link?

---

### Post by kaivalagi on 2008-05-28
> **rjdsmiths said:**
> When I Update [sudo apt-get update] i get tihis:

W: Failed to fetch [http://exodus.xmms.se/debian/dists/stable/main/binary-i386/Packages.gz](http://exodus.xmms.se/debian/dists/stable/main/binary-i386/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

Is it me or is it you link?

I installed xmms2 from the standard ubuntu repos. I suggest you comment out this alternative repo from your /etc/apt/sources.list file, update and try again. The source listed above was posted 2006, it has probably been and gone...

---

