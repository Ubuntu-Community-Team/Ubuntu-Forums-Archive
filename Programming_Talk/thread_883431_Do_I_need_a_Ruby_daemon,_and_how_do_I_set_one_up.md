---
title: "Do I need a Ruby daemon, and how do I set one up?"
date: 2008-08-07
forum: Programming Talk
---

### Post by Mr_Chapendi on 2008-08-07
This is driving me nuts.
For a project, I'm setting up a custom volume on screen display using Ruby and the Ruby bindings to XOSD.  (I know, it's not pretty, but it's a project.)  I have *an* implementation set up already, but it leaves something to be desired because my code simply generates a new XOSD object everytime I change the volume.  This is fine if I change it slowly (because the XOSD object before will fade before the new one appears), but if I hold down the button, it draws multiple XOSD objects on top of each other and it looks really bad.

My question - how do I create one object (in this case an X on-screen-display) and only modify that object every time I change the volume, instead of creating a new one?  Currently, changing the volume calls a script that draws the changed display and then ends (hence requiring a new object each time.)  Perhaps I need a process that is always running in the background (a daemon?) and call it via the command line with what needs to change?

I'll upload the code I have right now.

---

### Post by mssever on 2008-08-08
First, you're requiring rubygems for no reason.

If you want to run a daemon, install libdaemonize-ruby, then: ```
require 'daemonize'
# Do stuff. When you're ready to daemonize your process:
Daemonize::daemonize
```Since you won't adjust the volume all the time, you might want to make the daemon auto-exit after a timeout of no activity (and auto-start when necessary).

EDIT: The forum says that your attached file has 0 views, but I did look at it. Must be new math, where 0 + 1 = 0. :)

EDIT 2: There may very well be ways to solve this problem without using a daemon. I'm not familiar with XOSD, so I can't recommend any alternatives. Probably there's nothing wrong with a daemon approach, except that it might waste a small (probably negligible) amount of memory when you're not using it.

---

### Post by Mr_Chapendi on 2008-08-08
@mssever : I was requiring rubygems because I installed daemons as a gem.  (If I were running Ubuntu on this particular machine, I'd follow your advice and install libdaemons-ruby - unfortunately, this project is for my Arch laptop and not for my Ubuntu desktop.) Thank you for pointing it out though - I think assuming I was using ubuntu was quite reasonable given the forums I'm posting on.  

Instead of implementing a daemon, I used the drb library, which is designed to make an object accessible remotely over a network to another Ruby program as if it were local.
Basically, I created a server (volosds) that will create an object on startup and shares that object over port 9000.  Then, I moved all of the actual changing functions into a client (volosdclient) that accesses the previously created object via port localhost:9000 to change it.  (This has the added bonus that I should theoretically be able to change my volume remotely - with an onscreen display! :lolflag:)

So now, I have two questions.
First - how do I speed this method up?  Although I no longer have an overlap problem, I do have a noticeable latency between hitting a button and seeing the OSD.

Second - how would I implement this as a daemon?  I keep hitting all sorts of walls with the daemon stuff - I'm pretty sure I just don't understand it well enough to use it.  I'm still interested in the daemon approach because I'm guessing it would solve my latency issues.

Uploading new code.

---

### Post by mssever on 2008-08-08
> **Mr_Chapendi said:**
> First - how do I speed this method up?  Although I no longer have an overlap problem, I do have a noticeable latency between hitting a button and seeing the OSD.I'd forgotten about drb when I wrote my earlier post. I've never messed with it, though, so I'm afraid I can't help much here. 

> Second - how would I implement this as a daemon?  I keep hitting all sorts of walls with the daemon stuff - I'm pretty sure I just don't understand it well enough to use it.  I'm still interested in the daemon approach because I'm guessing it would solve my latency issues.It might or might not solve your latency problem (it depends on what's causing the problem), but here's the approach I thought of (you'll need to add in appropriate error checking).

[LIST=1]
[*]On startup, volosd looks for a FIFO (or maybe a socket) in a known location (such as /tmp).
[*]If it finds the FIFO, then it assumes that a daemon is already running, so it prints an appropriate command to the FIFO and exits. (You'd need some way to make sure stale FIFOs don't get left behind to confuse the script.)
[*]If the FIFO doesn't exist, then the script daemonizes, sets up the FIFO, processes the command it was given on startup, and enters a basic event loop, listening on the FIFO for further commands. It should also set a timer (for 30 seconds perhaps) that gets reset every time a command is processed.
[*]When the timer expires, the daemon exits, to avoid needlessly consuming resources.
[/LIST]

---

### Post by Mr_Chapendi on 2008-08-14
Well, I've definitely made some headway on a daemon approach to this problem.  But now I have other interesting problems.

I haven't tried to get it working the way you suggested mssever, and that may be my next step.  Instead, I have a daemon that polls the fifo rapidly looking for any commands to process.

On one hand, my latency issues have been solved!  :)  Button presses result in snappy and immediate changes.

On the other hand, my daemon uses between 0.3 and 1 percent of my CPU at all times! :mad:

Another issue has to do with how how long to display the OSD after commands are issued.  At the moment, it only displays the OSD for as long as the poll interval, so as to not slow the process down so much.  (The osd.wait(interval) command stops execution and forces me to wait.)  Unfortunately, this slows the process and also shows the OSD as a flicker.

I'm thinking I could solve that - on each command, show the OSD for the next 0.3 seconds, let's say, before hiding it.  If another command comes through in the meantime, it'll reupdate the 0.3s countdown.  My problem is that the 'meantime' requires the use of a thread, right?  I honestly have not the slightest clue on how to go about that.  My only programming classes have covered basic (and I mean *basic* Java, definitely no threads) Java and ADT's in C++ - nothing that really helps me out here.  I'm going to dive in and see how to do Ruby threads, but I know that you can really shoot yourself in the foot with those - any advice I should heed?  (Oh, as an extension of this, maybe I could use another timer thread to reduce the polling rate if no commands have happened recently?  I think that might help my CPU usage woes.)

Of course, if I decide to do it your way, my CPU usage shouldn't be too much of an issue, and it may allow me to fix something else - the media button repeat rate.  Right now, the repeat rate is far too high on the media buttons, causing any hold of the button to make my volume max out or drop to nothing.  If, instead of simply echoing my commands to the FIFO I run it through another Ruby script I should be able to filter out repetitions to an acceptable rate.  How to do this, I haven't the foggiest idea.

Anyway, I appreciate the help I've gotten so far and I will appreciate any further guidance.  Thanks, mssever!

Edit: Whoops, forgot the code.  There it is.

---

### Post by stylishpants on 2008-08-14
Polling kind of sucks for this sort of thing.  One option would be to avoid polling altogether by using inotify.


Ruby does have a basic but functional wrapper library for inotify.  I have not tried to use it on a FIFO but I expect it should work.

Attached find a bit of code I wrote that just watches the file (or entire directory tree) given on the command line and prints any filesystem events that occur.

It started off as one of the example files that comes along with the libinotify-ruby package (you need to install that BTW), but is quite heavily modified now.

Anyway, you could run this thing to see what event type is generated when the FIFO is modified, and then integrate inotify notification into your own code to make it sleep until that inotify event occurs.

---

### Post by Mr_Chapendi on 2008-08-15
Unfortunately, stylishpants, this code is for an Arch machine and I have no idea what the crap it's ruby-libinotify package is installing so I can't use that code.

However, you did spur me to find this Ruby gem instead - [RInotify]("http://rubyforge.org/projects/rinotify/").  It seems to just be another inotify binding, and I've managed to get the example file to report changes on FIFO's after some tweaks.  (Like not letting it check if the FIFO is a file.  :lol:  That fails, apparently...)

I'll play with this some and get back to you.  It seems very promising.  Thanks very much.

---

### Post by Mr_Chapendi on 2008-08-15
This is the last hurrah of my polling-let's-kill-the-cpu-code.  I managed to get it to show the OSD for 1.2 seconds after the last command so that it doesn't flicker on and off if I decide to hold the button.  It still changes it a bit fast, but I'm not sure I want to mess with that quite yet.

Next step - event-driven daemon!

---

