---
title: "Previewing second monitor off first monitor..."
date: 2011-09-21
forum: New to Ubuntu
---

### Post by lincoln.burton on 2011-09-21
Guys,
[INDENT]First I'm new. So comments suggestions on this post are welcome.
Second: I'm not sure whether to post here (as it's my first) or in another more specific section, regarding monitor issues say.
I have done some searching regarding this problem and haven't found "exactly" what I've been looking for, so next step is to ask the community.[/INDENT]

Background:
[INDENT]I'm running Ubuntu 11.04.
Installed Ubuntu a week ago.
Have an Nvidia card and two monitors running on that card.
One monitor is a regular monitor connected via DVI, the other is actually a TV connected via HDMI.
The HDMI connection is achieved by a DVI=>HDMI converter that comes with the NVIDIA card. This is plugged into the FIRST connection on the Nvidia Card, the reason for this is that audio is available on this connection for HDMI!)
At the moment I'm running Twin View in X, this was setup using the Nvidia drivers, and I'm using the TV as an extension to the desktop, with the primary monitor in the configuation being the actual monitor, not the TV.[/INDENT]

Problem:
[INDENT]The TV is in another room to the PC and herein lies the problem. When I start up a media player to watch a video, I can see what I'm doing on the monitor to start the movie, but once running I cant just easily drag and drop the application onto the TV (my second monitor) and set it to full screen, I cant see what to click on etc...
 It's not that the OS doesn't support this (playing the movie on the second screen), the problem is I cant see what I'm doing on the TV.
If everything was in the same room I'd have no issues.[/INDENT]
     
Question:
[INDENT]Is there some way to run a preview of the second monitor on the first monitor, the preview allowing control of whatever is displayed on that monitor?[/INDENT]
              
              
Notes:
[INDENT]It seems like the workspace switcher offers a limited tool to do this, is there any other built in functionality of Ubuntu that can answer this need?
     
I've tried using VNC. This would satisfy my needs IF I could get it to work. It would also allow me to use my phone to run vnc client over wifi, and use it as a second mouse to start/stop media player etc...
When I was doing this I was running the video card drivers in a different configuration.
The second output to my TV was setup as a seperate X screen. The complication was that when I started X11VNC server with the following command "x11vnc -avahi -display :0.1", and likewise for the media player "banshee -display :0.1"
When I'd connect with a vnc client, as soon as I'd move my mouse into the top left hand corner of the VNC window, it would reposition my mouse to the top left hand corner of the primary monitor I was using.
(If this last sentence doesn't make sense I'll try to explain this in more detail, just ask!)[/INDENT]

Hope that someone out there has either had and solved this problem and can help or provide some ideas on what I should try.

Kind Regards,
        Lincoln

---

### Post by papibe on 2011-09-21
Welcome to the forums!

Since the other monitor is in the other room, may the idea of 'extended' desktop is not working as you want. Have you consider to clone your monitors? That way it could be very easy to set up a movie on the TV.

The only problem of cloning your monitor would be if you thought of the initial setup, so you can play the movie on the TV, AND keep working on the desktop.

Just some thoughts,
Regards.

---

### Post by Jagoly on 2011-09-21
CCTV?

Ok that's probably not an option. What resolutions are the TV and monitor?

PS: may I ask what this setup is for?

---

### Post by lincoln.burton on 2011-09-21
Hi papibe,
[INDENT]I'd prefer not to use mirroring if possible, reasons:
a) As you correctly stated, you cant have person A work on one Monitor and person B watch a Movie on the TV.
b) There can be issues with regards to resolution as well. If the resolution is not the same on both screens (which natively it isn't in my case), then my TV will try to rescale the image to make it fit, and it slightly looses quality.

I'd really prefer not to use mirroring if possible.

Thanks for your suggestion though :)[/INDENT]

Kind Regards,
     Lincoln

---

### Post by lincoln.burton on 2011-09-21
Hi Jagoly,

Resolutions :
[INDENT]Monitor 1400x1050
TV:1,920x1,080 (I think, I'll have to double check this!)[/INDENT]

Purpose:
[INDENT]To be able to work on one monitor and watch a Movie/TV show on the second. But be able to start the show to watch from the first.[/INDENT]

Kind Regards, 
            Lincoln

---

### Post by Jagoly on 2011-09-21
So you want to be able to control everything on the tv, without actually being able to see the TV, or just control videos playing?

---

### Post by lincoln.burton on 2011-09-21
Jagoly,
[INDENT]> So you want to be able to control everything on the tv, without actually being able to see the TV

That would be fantastic!

The latter option could work as well, the first option is preferable though.[/INDENT]

Kind Regards,
Lincoln

---

### Post by papibe on 2011-09-26
Since no one has came out with a good solution, I'm going share what is working of me. May be it can give you some ideas.

I have a very similar setup. My desktop doubles as workstation and HTPC. In my case both monitors are in the same room though.

I chose to go with 2 'Separate X Screens'. The main reason is that one of my concerns was, that if no one was using the desktop, you can use the TV to either browse the Internet, or watch movies. Since separate xscreens offers the full desktop look and experience, I went for that setup. All menus are there, so everything is easy to launch.

What makes the experience even better is a wireless keyboard and mouse (or a all-in-one combo). That way you lay back, pause/rewind/forward the movie, or browse those funny kitten and puppy videos on youtube :p

I keep my regular wired keyboard and mouse on the workstation side of this setup, since there's no limitations on how many keyboard or mouse you have connected.

I've thought of your setup and I came up with a 'blind man' solution. These are my premises:
[LIST]
[*]You can launch applications from the terminal of the primary screen, so they appear on the second one (TV).
[*]You can use command line options to lauch those apps directly on fullscreen.
[*]Most media players can be handled using shortcuts.
[*]To execute shortcuts on the TV, you just move the mouse beyond the scope of the screen, and press the shortcuts.
[/LIST]
For example, let's say your favorite media player is mplayer. Open a terminal in the desktop and run something this:
```
$ cd MediaDir
$ mplayer -display :0.1 -fs mymovie.mp4
```
That will start a movie on the TV, and fullscreen.

Let's say later someone yell you from the other room, "could you pause the movie?". To do that is very simple: move the mouse beyond the edge of your monitor (in my case the right edge) and you press space (maybe a click would be necessary to select the window). To resume the movie just repeat the operation.

In the particular case of mplayer, you don't need even to move the mouse, you can press those shortcuts from the same terminal in which you are running it.

That's it. I hope these ideas are not too basic or dumb, and they would help you in your quest for the "Multimedia Grail".

Regards.

Note: the syntax for launching an app on the second display in fullscreen may varies from player to player.

---

### Post by lincoln.burton on 2011-09-26
papibe,[INDENT]Thanks for taking the time to get back to me.

What I've found is that the workspace switcher allows you to view the second monitor in a Twin View setup.

I've also noticed that if i open media player, and drag it till its nearly over on the other monitor I cannot see, then double click to make it go full screen, it then goes full screen on the second monitor!

Secondly I can use the workspace switcher to view that second monitor off the first, then click on the full screen playing video and drag it back onto the original monitor.

This, whilst it is a bit of a hack, suffices my needs, without any extra software.

I will try your method. I was considering running "dual seat" configuration which I have seen mentioned on the web as well.

For the time I'll resolve this issue as "Answered"

Thanks for your help!

[/INDENT]Lincoln

---

### Post by krunge on 2011-11-19
The workaround for the 2nd screen :0.1 and the mouse might be solved by adding this option to x11vnc:
```

-xwarppointer

```

More info: [http://ubuntuforums.org/showthread.php?t=1858316](http://ubuntuforums.org/showthread.php?t=1858316)

---

