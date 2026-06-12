---
title: "VBNC And MonoDevelop"
date: 2008-01-10
forum: Programming Talk
---

### Post by dean20007 on 2008-01-10
HI guys 

I have installed MonoDevelop version 0.14, I have installed mono 1.2.6.

My problem is when I try and create a VB.NET project (just a simple console one) that when I try and build from MOno develop I get the following error 

```

Build failed. ApplicationName='vbnc', CommandLine='"@/tmp/tmp4b3aef60.tmp"', CurrentDirectory='/home/dean/Projects/heartbeat/heartbeat', PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'
```

If I run vbnc from a terminal with the argument "@/tmp/tmp4b3aef60.tmp" it builds fine, so i am guessing That monoDevelop is not picking up the mono 1.2.6. 

Does anyone know I get it to find and use this so I can build successfully from within MonoDevelop?

Additonally when I installed Mono it told me the following files could not be found so I may not be able to use some graphical features of mono

libgailutil.so.17 libnspr4.so libplc4.so libplds4.so

These don't seem to be in any repos....does anyone have any ideas?

Cheers

Thanks

Dean

---

### Post by dean20007 on 2008-01-12
bump

---

### Post by eropka on 2008-01-14
I can't help you, but I'm a newbie looking to install mono 1.2.6 too... How did you do that?

---

### Post by dean20007 on 2008-01-14
Mono 1.2.6  can be downloaded from:
[http://www.mono-project.com/Downloads]("http://www.mono-project.com/Downloads")

---

### Post by gangrelsurf on 2008-08-06
I've got the same problem. Have you worked anything out?

---

### Post by tinny on 2008-08-06
If you are using Ubuntu Hardy MonoDevelop can be installed from "Add / Remove Applications.." (universe repository must be enabled).

I think this version is 1.0, but because it is a Ubuntu package it should be tested and work correctly.

FYI: [http://packages.ubuntu.com/hardy/monodevelop](http://packages.ubuntu.com/hardy/monodevelop)

---

### Post by ShadowMaster22 on 2008-09-12
Download vbnc (using synaptic or apt-get or whatever you will).  It worked for me, but there still is a problem. The program will run through monoDevelop's run button, but the end file is an .exe file, which doesn't run in linux. Go figure!

---

### Post by Zugzwang on 2008-09-12
> **ShadowMaster22 said:**
> Download vbnc (using synaptic or apt-get or whatever you will).  It worked for me, but there still is a problem. The program will run through monoDevelop's run button, but the end file is an .exe file, which doesn't run in linux. Go figure!

Interesting. Using packages.ubuntu.com, I couldn't find it in any package. What was the name of the package you installed? Do you use Hardy, Intrepid, Gutsy or an older distribution?

---

### Post by true_friend on 2008-09-12
Use latest packages for Hardy from unofficial repository. [The address]("http://directhex.mfgames.com/hardy.html"), mono 1.9.1 and MD 1.0 is available here. The compiler package should like mono-vbnc. Hopefully you will get it.

---

### Post by ShadowMaster22 on 2008-09-12
OK. I just figured out the vb.net thing. you have to have vbnc installed. i just used
*sudo apt-get install vbnc*
in the terminal.
also... to run the compiled .exe file, DO NOT use
*./myprogram.exe*
instead, use
*mono myprogram.exe*
and it works fine.
hope this helps.  worked for me fer Ubuntu 8.04 (Hardy Heron) on a Dell Studio 1535.

---

### Post by true_friend on 2008-09-14
It always work so :D
mono xxx.exe is the standard command to run .net applications on linux.

---

### Post by Klep7o on 2009-05-16
Might be specific for 9.04 but I couldn't *install the *[I]vbnc package using:

sudo apt-get install [/I][I]vbnc

Instead:

sudo apt-get install mono-[/I][I]vbnc

Now everything seems to work
[/I]

---

### Post by slimx3m on 2009-05-29
thnx so much Klep7o, that worked like a charm. :)

---

### Post by Edussooriya on 2009-11-12
I tried both ways. but it doesn't work and displays following message.

root@asoka:/home/asoka# apt-get install vbnc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vbnc


root@asoka:/home/asoka# apt-get install mono-vbnc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mono-vbnc

can anyone help me please?

---

### Post by directhex on 2009-11-13
> **Edussooriya said:**
> I tried both ways. but it doesn't work and displays following message.

root@asoka:/home/asoka# apt-get install vbnc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vbnc


root@asoka:/home/asoka# apt-get install mono-vbnc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mono-vbnc

can anyone help me please?

Either your repositories aren't set up properly, or you're running pre-Jaunty Ubuntu

---

### Post by lovol on 2009-11-17
going to the synaptic package manager and typing vbnc, and installing 'mono-vbnc' fixed this.

But as an aside, I just used the new Ubuntu download center to install mono, and maybe I've naive for expecting VB.Net to work out the box, but maybe some extra info on what is and is not installed would be nice.


AKA when starting up VS.NET, you know what is and isn't installed, also the templates are just not available, which is both annoying, and good!

THANKS FOR THE ANSWER THOUGH

---

### Post by phrostbyte on 2009-11-17
> **directhex said:**
> Either your repositories aren't set up properly, or you're running pre-Jaunty Ubuntu

Does Mono's VB support late binding?

---

### Post by directhex on 2009-11-18
> **phrostbyte said:**
> Does Mono's VB support late binding?

Yes, but it might be buggy on non-trivial cases. Maybe.

---

