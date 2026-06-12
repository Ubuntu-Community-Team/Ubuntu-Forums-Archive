---
title: "Problem compiling SDL dev libraries"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by Acharn on 2012-11-27
The other day I was looking for games to install and ran across reference to one called Marathon. I was pleased to find there was a native Linux version which uses an engine called AlephOne. I haven't compiled packages since I ran a FreeBSD server about fifteen years ago, but that part of it seemed to go well enough. According to the A1 web site all I should have to do is enter the command "./configure && make && make install." Just like I used to do, except I used to have to clean up with "make clean" afterward.

Well, of course, it hasn't been that easy. running the configure script revealed there were dependencies I also had to install, and for the most part that went easily, but now I've come up against what seems to be a recursive wall I can't get around. I need to install the SDL (Simple Directmedia Layer) dev libraries. The main one, libdev1.2-dev gives me the following message:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libsdl1.2-dev : Depends: libglu1-mesa-dev but it is not going to be installed
                 Depends: libpulse-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```
I've searched with Google and there are several web sites that purport to tell me how to do it and they all end up giving me the same error. I can't tell when most of them were written, but at least one mentioned Ubuntu 10.04. I'm running 12.04 (waiting for the update manager to tell me to install 12.10), so apparently this dependency problem arose sometime during the last one or two upgrades.

Anyone can tell me how to install these libraries?

---

