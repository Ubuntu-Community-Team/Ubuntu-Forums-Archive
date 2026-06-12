---
title: "Creating Portable Linux Apps"
date: 2009-10-21
forum: Programming Talk
---

### Post by abroun on 2009-10-21
Hi all,

First of all, apologies if this is the wrong place to post. I did a quick search of the forums and this seemed like the most promising place to post.

So, I'm trying to work out the best way build applications so that they work on multiple versions of Linux and can be carried around on a USB stick.

The reason I want to do this is because I'm currently doing a group project at University where we'd like to use Pyrobot [http://pyrorobotics.org/](http://pyrorobotics.org/) to simulate the robot and in the future it'd be great to use Player/Stage [http://playerstage.sourceforge.net/](http://playerstage.sourceforge.net/) and Gazebo (a 3D robot simulator) as well. The only problem is that the University labs all seem to run a different version of Linux and the space available for personal files is limited (~250MB). Also, it'd be good if members of the team could have a copy of these programs on their USB stick so that they can run them at home (most now have Ubuntu 9.04 installed).

I don't think that a modified Live Disc or USB is the way to go as the University machines wont boot them. Therefore I was thinking that the best way of getting the programs to run was to statically link them along with their dependancies so that they can be as self contained as possible on the USB. So for example, to get Pyrobot to run I think that I need to create a statically linked version of Python, put it on the USB, then install Pyrobot on the USB and point it at my version of Python.

My questions are

- Does this seem like a sensible way to go and does anyone have any better ideas?
- Does anyone have any experience with building statically linked libraries? I think that most of the apps I want to build will be autotools based so is there a standard way of getting these to link statically?

Anyway, thanks for looking, any answers or advice much appreciated.

Regards

Alan

---

### Post by hessiess on 2009-10-21
Python is an interpreted languages and is the same across all platforms, including different versions of Linux. As Linux comes with python by default, it should already be possible to run the program on the machines.

Trying to build a statically linked version of a program as big as python is just asking for problems, and even if you did manage you would probably end up with path problems, python stores libs in /usr/lib/python2.*.

---

