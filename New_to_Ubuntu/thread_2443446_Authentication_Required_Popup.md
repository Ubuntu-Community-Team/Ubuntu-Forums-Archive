---
title: "Authentication Required Popup"
date: 2020-05-15
forum: New to Ubuntu
---

### Post by fhesseti on 2020-05-15
Hi I am a new Linux user and Ive just installed "Howdy" which allows me to use my camera for face recognition like windows hello. I actually dont know if this is related but given the timing i think it may be. For some reason every now and then this horrible popup in the top left appears telling me that authentication is required to do one thing or another and it wont go away unless i logout and it appears on top of literally everything, even a full screen video. Whenever I click on "authenticate" or "cancel", it does absolutely nothing. Whats causing this and how do I stop it (Im ok if it means making the computer less secure). I would rather not get rid of Howdy either. Thanks for helping me, Im slowly learning and if i can deal with this i really will end up loving ubuntu, as other than this its amazing so far :)

---

### Post by CelticWarrior on 2020-05-15
Are you using autologin? If so then don't and it won't show up.

---

### Post by fhesseti on 2020-05-15
It is very on and off in terms of when it does show up it doesnt happen everytime but when it does i have to log out and its very annoying. and as for autologin, nope, autologin is off. Thats where you are just logged in straight away isnt it? I turned that off because I use howdy to log me in with face recognition. No point automatically logging in if i can just use face recognition if you get what i mean.

---

### Post by grahammechanical on 2020-05-15
I have just done a little reading about this program. Do you have to give the program your Ubuntu login user password? If you don not then I guess that even if it gets you to a Ubuntu desktop but it may not unlock the key ring.

[https://itsfoss.com/ubuntu-keyring/](https://itsfoss.com/ubuntu-keyring/)

Regards.

---

### Post by fhesseti on 2020-05-15
I had to use the password to get it set up, but that applies to everything doesnt it? Also that isnt the same popup I get have you seen the attatched screenshot? Thanks for trying to help, I love the community looking out for one another im looking forward to the linux future

---

### Post by fhesseti on 2020-05-16
usr/bin/env authentication is required is what popped up this time. What is usr/bin/env? when i go there it says it cant find any programs to open it. It also says its owned by "root". would changing that to me solve this? if so how do I do that?

---

### Post by Holger_Gehrke on 2020-05-16
'/usr/bin/env' is a program to start another program with a specific environment. It's often used in the "she-bang" line at the start of a script, for example '#!/usr/bin/env python' at the start of a python script. This line is used by the system to find the interpreter for the script. If you write a script this way you don't have to specify the path to the interpreter for the script thus making the script slightly more universal since the interpreter will be found as long as it's in a directory that's in the list of directories stored in PATH. A lot of the programs used for system management are actually scripts, so that's probably what's causing this message.

Holger

---

### Post by fhesseti on 2020-05-16
I really appreciate the help and Im sorry if i sound dumb, but i am lol. I dont really know exactly what you mean by this, how do i go about fixing this? Im very new to linux been a windows user all my life so its all very alien to me, thanks.

Edit: it now says authentication is required to run usr/bin/env as the super usr. Like the first time whenever i click on cancel or authenticate, it doesnt do anything. I have to log out and in again for it to go away, which isnt ideal at all. If you can simplify the solution for me I will be ever so grateful :)

---

### Post by Holger_Gehrke on 2020-05-16
There's two kinds of programs: binary executables which are made up of instructions that can be directly executed by the processor and executable text that needs to be run through an interpreter program that executes the commands the text contains. The latter kind of program can have a line at the start that tells the OS what program to use as the interpreter for it. That line has the form '#!/path/to/the/interpreter-program'. The problem with this is that it makes it necessary for the interpreter to be in a specific place. The way around that limitation is to use a line like '#!/usr/bin/env interpreter-program'. 'env' without any variable definitions loads a standard environment and loads the first program of the given name it finds in a directory in PATH. 'howdy' obviously doesn't expect this behaviour and instead of telling you what executable text it's trying to run it tells you it's trying to run 'env'. 

Either there's something very wrong with your installation of howdy (you did run 'sudo howdy add' to take a picture of your face and add it to the known faces, didn't you ?) or it has the kind of bug I'd expect in an early alpha-build of a program. Beyond that I really can't help, because on my system it either isn't happy with my camera or my machine is simply to slow. When I try to use it, I always get a timeout during recognition.

Holger

Edit: If you should decide to remove howdy, please be aware that a simple 'sudo apt remove howdy && sudo apt autoremove' does not clean it out completely since it needs some packages for python that aren't in the PPA and are not available in the versions needed in the repositories. On my machine with XUbuntu 18.04 it installed 300 Megabytes worth of libraries through pip3 (the python package installer). So additionally 'sudo pip uninstall opencv-python' was necessary to get rid of the left-overs.

---

### Post by fhesseti on 2020-05-16
Thanks for the reply. I did indeed do sudo howdy add and everything seems to go smoothly with it. As for the timeouts i had the same problem initially, and i fixed it by doing sudo howdy config and increasing the "certainty" from 3.5 to 5. Howdy works brilliantly now and it rarely times out, so maybe give it another go if you haven't tried that. As for the popup issue I think it is related to howdy but again I cant be 100% sure so next time I get it I will do exactly what you said in terms of uninstalling it properly and see if it solves the issue. If it is howdy, Ill ask the developers about it on github. Ill report back when im sure it is howdy that's causing it. Unless of course you know for sure that it is howdy in which case I will contact them immediately :)

---

