---
title: "Building and Compiling"
date: 2006-05-17
forum: Programming Talk
---

### Post by annaraps on 2006-05-17
Hi

Is there a difference in Compling Source and Building it?

By Compiling I mean the usual ./configure , make and make install routine.

I am not sure what building does , I tried to build using the command *"apt-get source --build <pacakage-name>" * and it took an awful long time.

Thanks

---

### Post by BobSongs on 2006-05-17
Am I correct in assuming you meant **build-dep**?

To test this feature I did the following```
sudo apt-get remove csh
```and removed the c shell. Then I followed it up by```
sudo apt-get build-dep csh
```to see the net result. Here's what apt-get said> Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
[indent]build-essential g++ g++-4.0 groff libstdc++6-4.0-dev pmake[/indent]
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 1981kB/5830kB of archives.
After unpacking 20.3MB of additional disk space will be used.
Do you want to continue [Y/n]?Hmm. I figured, normally it doesn't require 20.3 Mb. So I tried the standard method```
sudo apt-get install csh
```and got> Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
[indent]csh[/indent]
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/239kB of archives.
After unpacking 393kB of additional disk space will be used.Is there a reason why you're using this switch? Has installing a certain package caused problems?

---

### Post by annaraps on 2006-05-17
No , I don't mean the build-dep option.

If I want csh to be "built" then I do something
like 

apt-get source -b csh

I think build-dep just takes care of the dependencies
you need to have before installing a specific package.

I tried installing openscenegraph to be precise.But I need
the source of the API not just the binaries to be installed.

Sorry for the delay in the reply

---

