---
title: "Of shell scripts and GUIs..."
date: 2005-01-08
forum: Programming Talk
---

### Post by kokiri on 2005-01-08
Anyone have any ideas on how one would create a frontend for a regular old #!/bin/bash shell script??

I've looked at python, python & Tkinter, pyGTK, and I just wanna  ](*,) 

Cookies would be appreciated    :-D

---

### Post by stateq2 on 2005-01-08
pygtk may take a little time getting used to, but once you figure it out, making a gui is pretty easy...although I'm currently stuggling on a few of pygtk's undocumented areas :(

post some code :)

---

### Post by sobralense on 2005-01-08
already tried "dialog" ?  =)  or dont want a curses based?

---

### Post by kokiri on 2005-01-08
I would really like to stay away from curses based if I could.

I guess I'll let a bit of the cat out of the bag ahead of time.  :smile: 

I'm working on a personally exciting project for the community here.

After reading many desktop users lament on and on about this and that not included or working after a clean install, I'm currently creating Unity:
The **U**buntu **N**on-free & **I**rritation **T**amer..**Y**? Cause it's the nice thing to do.

I could smack Unity out using an event driven shell script, but that's not as ashthetically pleasing or as friendly as a full blown simple button click gui.

---

### Post by #Greg on 2005-01-09
I'm doing something similar now.

I'm making a shell script which'll upgrade and install (and remove!) various apps for my Ubuntu desktop from apt and various other sites and do most of the configuring for me. 
I'm often changing various things around on different boxes so I (re)install things a lot so something like this could really save me a lot of time. I've got various shell scripts which go install dlls for codecs and the like so I'd like to put it all into one script I can run after a fresh install, should save me hours and hours of time that I spend tinkering a new install. I'm just going for the simple .sh though, nothing fancy :)

As for the Y, how about a tongue-in-cheek "Yutility", as in:
The **U**buntu **N**on-free & **I**rritation **T**amer **Y**utility.

Just a thought :)

---

### Post by kokiri on 2005-01-09
Mine hopefully will become something fancy, but right now it's just a bash script too.

I like the Yutilitie... Hee hee, that's a keeper. 

My script aims to hopefully encompass all the howto's and faq's via automation using menus and the like.

If there's anything you'd (or anyone for that matter) like to contribute I should have the first version out here shortly under its own thread.

Right now I'm waiting for permissions to reuse some code snippets from a few members here before I release it.

---

### Post by heema on 2005-01-10
yes it would be gr8 if some one posted a howto or example of converting a bash script to gui

---

### Post by wulf on 2005-01-10
Here's a little script I sometimes use. All it does is pop up a window with a message and a big button to close it down:
```
#!/usr/bin/wish

# Pop up a box to let user know a task is complete
# Documentation for tcl/tk at http://www.tcl.tk/

label .topspace -text ""
pack .topspace

button .ready -text "READY!!!"
.ready configure -command "destroy ."
pack .ready

label .complete -text "The specified task is\nnow complete."
.complete configure -width 20
.complete configure -pady 10
pack .complete
```
I use it (from the command line) to notify me when a big task has finished running. For example:
```
bzip2 bigfile.tar; ready
```
It's also handy as an alarm clock, for example if I want to give myself a time limit on completing a task:
```
sleep 15m; ready
```
It's not really a GUI but I think it could probably be extended to include other buttons, with other actions tied to them. Personally, I'm happy keeping my utility scripts small, simple and commandline driven.

Wulf

---

### Post by heema on 2005-01-10
[QUOTE=wulf]Personally, I'm happy keeping my utility scripts small, simple and commandline driven.

Wulf[/QUOTE]

Yes i like them too to be small and simple but sometimes it easier to have a gui for it , like for e.g. i made a small commanbdline menu script to connect,disconnect,redial my dsl , but it would be nicer if i converted it to a gui


P.S.: Kommander looks to be really promising  

[http://kde-apps.org/content/show.php?content=12865](http://kde-apps.org/content/show.php?content=12865)

---

