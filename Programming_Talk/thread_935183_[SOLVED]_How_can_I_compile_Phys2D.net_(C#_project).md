---
title: "[SOLVED] How can I compile Phys2D.net? (C# project)"
date: 2008-10-01
forum: Programming Talk
---

### Post by KIAaze on 2008-10-01
I would like to try out the examples of Phys2D.net: [http://physics2d.googlepages.com/](http://physics2d.googlepages.com/)

Unfortunately, it doesn't come with any kind of readme explaining how to build it (or I missed it). There are some .sln and .csproj files, but I have no idea how to use them.

My attempts at opening/importing the projects into monodevelop have all failed so far.

Note: I have no experience in C#, but I do have experience with C and C++.
The reason I want to be able to run it, is to figure out the algorithm used to calculate shapes from images and test its speed.

---

### Post by jimi_hendrix on 2008-10-01
check the sticky for how to compile C# code if you can get the source...but it might not work because it could use the .NET framework (even thought that seems to be tagged on most C# things i see even if it doesnt use .NET...)

---

### Post by KIAaze on 2008-10-06
Ok, I must have messed something up during my first compilation attempts, because now I managed to compile it without any errors using the .sln file at the root from a clean extract...

However, now I get errors when running it:
```
[9][~/Desktop/Physics2D.Net/Physics2DDemo/bin/Debug]$  ./Physics2DDemo.exe 
Welcome to the Physics2D.Net Demo
In the demo pressing the number keys or W-O will load different demos.
Left Clicking will allow you to pick objects up.
Middle clicking on the screen will launch a projectile where you click.
Right clicking and holding will shoot out particles where you click.
holding M will place 3 rotating rays that shoot out particles on impact.
The left and right arrow keys will move the tank.
SpaceBar will fire the tanks cannon.
In the upper left corner a small colored box will appear.
If it is green then the engine has too little to do and is skipping a timestep
If it is red then the engine has too much to do.
P or Pause will pause the simulation.
Press Enter To Start

Before 42
After 14
Subdivide 24
Before 160
After 47
Subdivide 94
Before 216
After 84
Subdivide 90

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Tao.OpenGl.Delegates ---> System.NotSupportedException: Unknown platform - cannot get function pointer.
  at Tao.OpenGl.Gl.GetFunctionPointerForExtensionMethod (System.String name) [0x00000] 
  at Tao.OpenGl.Gl.GetDelegateForExtensionMethod (System.String name, System.Type signature) [0x00000] 
  at Tao.OpenGl.Delegates..cctor () [0x00000] --- End of inner exception stack trace ---

  at Tao.OpenGl.Gl.glShadeModel (Int32 mode) [0x00000] 
  at Physics2DDemo.OpenGlWindow.Init () [0x00000] 
  at Physics2DDemo.OpenGlWindow.Run () [0x00000] 
  at Physics2DDemo.Program.Main (System.String[] args) [0x00000] 

```

---

### Post by KIAaze on 2008-10-07
Problem solved. :)
[http://groups.google.com/group/physics2ddotnet/browse_thread/thread/1726a9de0b7739c7](http://groups.google.com/group/physics2ddotnet/browse_thread/thread/1726a9de0b7739c7)

More info about dll.config files:
[http://www.codeproject.com/KB/cs/runtimeconsoleconfigfile.aspx](http://www.codeproject.com/KB/cs/runtimeconsoleconfigfile.aspx)

---

