---
title: "Projects Ideas to Play Around With"
date: 2007-04-04
forum: Programming Talk
---

### Post by Zuph on 2007-04-04
Working in IT, programming has become more of a hobby of mine and less of a job requirement.  A lot of the things I need can be adapted from off-the-shelf solutions, and little more is needed than modifying config files here and there.  While my programming background isn't extensive or broad, I still get the itch from time to time to start working on a project that will expand my knowledge and may actually get used.  So, that's the point of this thread:

What project ideas do you have floating around in your head that you'd like to play around with, even if you don't have the knowledge or ability to pull them off?

Ideas kicking around my head right now:

A simple, easy to develop for MUD engine.

A simple, easy to use workflow engine, using XML files to define workflow objects, overall workflow, role based access control, etc.

Multiplayer web game engine, similar to Pardus or other online RPG-like games.

---

### Post by stuffradio on 2007-04-04
I think the web game engine out of your list would probably be the funnest one... too many MUDs on teh interwebs

---

### Post by jerryrw on 2007-04-04
A system that can check installed packages in apt for deb and/or yum for rpm on your linux box save this to a file that can then be taken to an internet connected PC running windows, use the Windows machine to check repos for updates/new software and dl them to the windows box so they can be taken to the offline linux box and installed.

I think I know roughly how and it would definately be a python thing for the cross paltform stuff.  I've seen a lagre number of people in forums, myself included, that need a tool to do this.

---

### Post by henrikwidth on 2007-04-05
jerryrw: Seen APTonCD ?

---

### Post by jerryrw on 2007-04-05
Thanks for the link.  That may be a very good starting point.  This was a side burner project of mine for when I get some free time after Tax season in the US.  This looks like a nice gui wrapper for making local repos after downloading the files using apt directly.

What I am thinking about is if I have a Linux PC at home that has no internet connection and Have a Windows box at work/friends house with an internet connection.  Not just using two nearly identical Linux installations which is what that the software at that link is for.  And I'll quote from the site:

>Exist any interest to release an MS Windows version?
>Many peoples have been asked if an Windows version will be released, where the peoples would >download the packages of an entire repository in a Windows box. But I'm not an Windows >programmer, and I don't like Visual Basic or Delphi :P

Wheras I am a Windows Delphi Programmer I may be able to help a little here and this may be a great base to start with.

The program would really only need two parts:

Easy/ier part
A *nix app that would read the deb/rpm local database and export this to a file to be taken to a networked box.

Hard/er Part
A more or less port of apt-get/yum to Windows to read the file exported from the *nix box and then connect to the appropriate repos and resolve dependencies and download the files which can then be rolled into a local repo.

---

