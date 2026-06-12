---
title: "Opentk Opengl issue"
date: 2012-11-17
forum: Programming Talk
---

### Post by Minguo on 2012-11-17
Hi I am trying to work with C# and mono, I downloaded opentk  [http://www.opentk.com/](http://www.opentk.com/)


I have a similar experience to the poster in this thread:
[http://ubuntuforums.org/showthread.php?p=11998770](http://ubuntuforums.org/showthread.php?p=11998770)

However, instead of a DllNotFoundException, I get a NullReferenceException error, both when I try to run the examples that use OpenGL and when I try to run any code that I compile. (Everything compiles fine, and I can run the sound examples just fine (uses OpenAL))

```
Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at OpenTK.Graphics.GraphicsMode.get_Default () [0x00000] in <filename unknown>:0 
  at StarterKit.Game..ctor () [0x00000] in <filename unknown>:0 
  at StarterKit.Game.Main () [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.NullReferenceException: Object reference not set to an instance of an object
  at OpenTK.Graphics.GraphicsMode.get_Default () [0x00000] in <filename unknown>:0 
  at StarterKit.Game..ctor () [0x00000] in <filename unknown>:0 
  at StarterKit.Game.Main () [0x00000] in <filename unknown>:0 

```

So I guess that it is somehow the interface between mono and opengl that is screwing everything up.  

I've got a whole bunch of opengl libraries and development versions and utility packages and whatnot installed.  How do I go about troubleshooting this?
 
glxgears works fine, and glxinfo says my glx version is 1.4



Edit:
Ok, so I asked on the openTK forums as well, and it seems there is an issue with the current stable release of OpenTK. 
opentk.com/node/1811
 Installing the current SVN seems to have resolved the issue, though I would still like to know how I would have gone about trouble shooting the issue.

---

