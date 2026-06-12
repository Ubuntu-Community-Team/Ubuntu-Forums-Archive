---
title: "creating the equivalent of a .deb in windows"
date: 2010-02-17
forum: Programming Talk
---

### Post by donkyhotay on 2010-02-17
I've been working on a [FOSS project](code.google.com/p/tether) the past year or so and am finally reaching a point where I need to consider distribution options. It's a game written in python that uses pygame, PIL, twisted, and zope libraries. With linux I can just create a .deb file since all of these dependencies are available in most repositories. With windows things become more problematic, two of the dependencies (twisted and zope) I can include within the game itself. Makes it a little bloated but it works. The others, python, pygame, PIL I can't integrate which means they need to be downloaded and installed seperately before users can play it. I would prefer to have it so that windows users can just install and play without having to find, download and install a bunch of dependencies first. My first thought was to use py2exe, however I found out this requires either distributing a .dll file that is copyrighted by microsoft that I don't have (or want) a license for, or it requires my users to download/install a microsoft library which defeats the entire purpose. My second thought was to create an installer that would check if the dependencies were already installed and if they weren't, go online, download them, and install them (similar to what a .deb file does). However I'm not a particularly skilled programmer and the only way I can think of doing this would be hacking together a .bat script which is ugly and I haven't written a .bat file since I had win95 on my system. So I wanted to ask, are there any other solutions I've missed?

---

### Post by donkyhotay on 2010-02-19
I managed to answer my own question and am posting it here in case anyone else has a similar issue. I found a scripting language called [autoit](http://www.autoitscript.com/autoit3/index.shtml) that is somewhat similar to bash and is capable of compiling standalone windows exectubles.

---

### Post by doas777 on 2010-02-19
I work primarily in .net, so I just have it create my installer for me usually (which can be configured to download external content), but you can easily write your own, especially if you only need to copy files to a location, create a few shortcuts, etc. the uninstaller is a slightly bigger deal, as it gets into specific reg entires, but still isn;'t too strenuous. 
Most professional companies just buy the tools from installsheild, or just make their own. 
Be wary of autopackers and AIO distro tools however, as most virus scanners notice them nowadays. many malicious coders use these tools to bind evil code to desirable code like warez cracks.

---

### Post by donkyhotay on 2010-02-19
Part of my problem is I don't own a windows based computer, don't really have access to .net or other windows based tools. Also I want to keep things FOSS. Apparently autoit is a scripting language, not a packager, I would have to write my own installer with it. My plan is to actually write a simple "find out if python is installed, download and install if it isn't, run a python script" in autoit and then compile it for windows. From there I can install the rest of it using a python script since I'm much more familiar with python and I won't have to recompile everytime there is a change (I can just modify my python scripts instead), especially since compiling requires a windows system. I just wanted to avoid having to tell people, download and install python before they were able to download and install my game.

---

