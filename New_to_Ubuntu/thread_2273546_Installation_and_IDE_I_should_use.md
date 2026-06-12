---
title: "Installation and IDE I should use"
date: 2015-04-13
forum: New to Ubuntu
---

### Post by mighri on 2015-04-13
On this pc I'm using now, I could install lubuntu and it runs fine. I use Intel(R) Pentium(R) 4 CPU 2.66GHz        with 739 MB. In Task Manager I read "Memory: 430MB of 739MB used" but with lshw -c memory I read 1015MiB. 

At this moment I opened just two programs firefox and lxterminal. Isn't 430MB not too much ?

Anyway, I don't really have a problem with this one, but I'd like to know which software, IDE, I could select and install to practice programming and scripting. Do you advice **anjuta**, for example? 

My problem is with installing lubuntu on my old laptop which is dell inspiron 4150:
                                                                                                                                                                                         Intel Pentium 4-M 1.7 GHz 
  256 MB memory
  AGP 4x - ATI Mobility Radeon 7500 - 16 MB DDR  GCPU

I had windows xp running on it. I formatted it to use lubuntu but I experienced some troubles during the installation. The screen got blue after selecting language, and install. It took more than an hour to skipt this skip and go to next which is network identification. One thing I liked before all, is that it detected the wifi network interface while I need to install driver on windows manually. The installation took almost 2 hours. I could install it, and running it as well, but as soon as I started the firefox, it stopped and was totally frozen. Now, because I use lubuntu on tis pc, I know I should add another 256MB memory to this laptop. I would like to know why this happened. I mean, on the website I understood that even 128MB should be able to run lubuntu.

-- edit --

[I]Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic[/I]

---

### Post by Rex Bouwense on 2015-04-13
While you may be able to install Lubuntu with as little as 128 Mbs of RAM, such a system would not perform well enough for daily use.  You will need a minimum of 384 Mbs for your system to operate at a better level.  With 512 Mbs of RAM you should have very few problems.  The reason why your system is freezing on you is probably due to the small amount of RAM that you have installed.  Since RAM is so cheap, adding more shouldn't be a problem.

---

### Post by ian-weisser on 2015-04-13
Use the commands 'free' and 'top' to snapshot your CPU and memory usage under various loads.
You will quickly see a trend if your memory is inadequate, or if you are using a resource-hogging application.

Use any language you wish. IDEs and compilers are available in Software Center for most languages.

---

### Post by grahammechanical on 2015-04-13
Speaking from my own experience, web browsers use a lot of memory and web sites add to the memory used, especially if the pages have a lot of flash content and we have more than one tab open at the same time.

---

### Post by mighri on 2015-04-13
> **Rex Bouwense said:**
> While you may be able to install Lubuntu with as little as 128 Mbs of RAM, such a system would not perform well enough for daily use.  You will need a minimum of 384 Mbs for your system to operate at a better level.  With 512 Mbs of RAM you should have very few problems.  The reason why your system is freezing on you is probably due to the small amount of RAM that you have installed.  Since RAM is so cheap, adding more shouldn't be a problem.
Is that what's going on? OK, but why am I consuming +400MB while no program is running except my browser at the moment.
I closed all tabs except this one; it's 317MB. 

> **Rex Bouwense said:**
> With 512 Mbs of RAM you should  have very few problems.
I have 739MB on my desktop, but I just faced a new problem. I tried to add embedded terminal and it causes some troubles when I type in a command. It freezes a while, and then continues working with delay printing char after another. Strange, or are there maybe other problems? 

I just edited my first post, I added release I have, so if you could check and maybe advice an upgrade or update..

Thank you very much, mr. Rex.

---

### Post by mighri on 2015-04-13
> **ian-weisser said:**
> Use the commands 'free' and 'top' to snapshot your CPU and memory usage under various loads.
You will quickly see a trend if your memory is inadequate, or if you are using a resource-hogging application.

Use any language you wish. IDEs and compilers are available in Software Center for most languages.
I wish many things:D, but I'm seeking some suggestions which one to use as IDE that works fine on lubuntu running on machine with 730MB memory. Right now, I just use gedit after I downloaded the build-essential. Great one, but I don't like using command line each time to compile, interpreter, browse, debug or check warning .. If you understand what I mean. :)

I think no top or free on the laptop now. I will expand the memory, and then, it will work fine or at least as good as it's running on my desktop. 

Or is firefox not suitable for lubuntu in my case? 

-- edit --

I installed build-essentials. What will happen if I download an IDE. Will that install the compiler like gcc as well, or is it going to use the installed one?

Thanks.

---

### Post by mighri on 2015-04-13
> **grahammechanical said:**
> Speaking from my own experience, web browsers use a lot of memory and web sites add to the memory used, especially if the pages have a lot of flash content and we have more than one tab open at the same time.
A good reason why I don't use Chrome which is a good one, but not in my pc and older laptop. 
I think it's impossible to use browser without flash content because I follow some tutorials and they are all video's of course. :p

Thanks! ):P

---

### Post by ian-weisser on 2015-04-13
What language(s) do you wish to use?
C? Perl? Python? Go? Vala? Java? QT? Erlang? Haskell? JS?

---

### Post by mighri on 2015-04-13
> **ian-weisser said:**
> What language(s) do you wish to use?
C? Perl? Python? Go? Vala? Java? QT? Erlang? Haskell? JS?
Yes, C, PHP and JavaScript. :)

One problem with gedit when I use with embedded terminal, it freezes and goes slowly. When I use shift + any key, it just stops interacting.

I tested anjuta, and just with first hello world, I clicked run (F3), it excuted some building files, and at the end I received "the application anjuta has closed unexpectedly". 

Nothing works. I think I will format it again, and try to test ubuntu. :D

---

### Post by mighri on 2015-04-14
I noticed:
When using shift or another key in gedit, the program ibus-ui-daemon got up and consumes 100% cpu.

---

### Post by ian-weisser on 2015-04-14
> **mighri said:**
> When using shift or another key in gedit, the program ibus-ui-daemon got up and consumes 100% cpu.

See the [bug report]("https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1276186") for suggestions and workarounds.

---

### Post by buzzingrobot on 2015-04-14
Application memory use remains essentially the same regardless of the desktop GUI in use. Look around for alternate applications that may use less memory.  For example, Midori is one potential alternative to Firefox.

All you really need to learn programming/scripting is a text editor and a shell (aka the Terminal). GUI-fied IDE's are pleasant and can be useful, but they're intended for use by production developers, add their own resource requirements, and their own learning curves.

---

### Post by mighri on 2015-04-15
> **ian-weisser said:**
> See the [bug report]("https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1276186") for suggestions and workarounds.
Preferences > language support >: keyboard input method system:: none

And then reboot, I think this is solved as long as I don't use another language alongside English. :p

Thank you.

---

### Post by mighri on 2015-04-15
> **buzzingrobot said:**
> Application memory use remains essentially the same regardless of the desktop GUI in use. Look around for alternate applications that may use less memory.  For example, Midori is one potential alternative to Firefox.

All you really need to learn programming/scripting is a text editor and a shell (aka the Terminal). GUI-fied IDE's are pleasant and can be useful, but they're intended for use by production developers, add their own resource requirements, and their own learning curves.

That is exactly why I asked for advice which IDE I should use to learn and practice some programming knowledge in C, PHP, JS ..

Thanks ):P

---

### Post by walterorlin on 2015-04-23
Editors are always a measure of personal workflow. The alternate isntaller will probably work better for the laptop as it cannot run the live installer with 256 mb of ram. Also on my old dell desktop the live installer took a really long time to complete and was very slow but the alternate installer uses less resources. I don't think firefox would be useable with 256 mb of ram. On more powerful computers I have seen browsers use more ram than entire virtual machines running lubuntu.

---

