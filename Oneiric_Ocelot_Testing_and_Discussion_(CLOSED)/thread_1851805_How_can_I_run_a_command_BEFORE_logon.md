---
title: "How can I run a command BEFORE logon?"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Srocchi on 2011-09-29
Due to a faulty GPU, I have to run a fixed-performance underclock of my GPU at boot. I already have that command running when my user logs in (automatically), but if I logoff or try to change users *Black Screen of Death* my GPU goes back to original configuration and its time for a hard reboot.

So I guess I'd have to somehow run this command just after X starts and right before I get logged in. Sounds about right? How do I do that?

I have a NVIDIA 9700M GTS. I'm running the 11.10 beta version.
This is the command: 
nvidia-settings -a GPUOverclockingState=1 -a GPU2DClockFreqs=300,250 -a GPU3DClockFreqs=450,300

Thanks in advance.

Edit: "Solution" on Page 2

---

### Post by bokgeneraal on 2011-09-29
I googled it for you. Here's the link [http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)
Thanks now I know , always wanted to do something like this.8-)
If you don't mind. Tell me how you get commands to run automatically when the user logs in.

---

### Post by staticd on 2011-09-29
Try adding it to /etc/gdm/Xsession

---

### Post by ninjaaron on 2011-09-29
> **bokgeneraal said:**
> 
If you don't mind. Tell me how you get commands to run automatically when the user logs in.

There are a lot of ways.  The easies is to open a program called "startup applications."  You can specifiy any command you want executed at login here.

---

### Post by Srocchi on 2011-09-29
> **ninjaaron said:**
> There are a lot of ways.  The easies is to open a program called "startup applications."  You can specifiy any command you want executed at login here.

Yup, thats how I do it.

I'm gonna test those two suggestions right now, thank you.

Isn't this [http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28) just a more complicated way of doing what "Startup Applications" does automatically for you? Cause my script already runs from init.d.

---

### Post by seawolf167 on 2011-09-29
See these two links for more info on specific instructions:
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)
[https://help.ubuntu.com/community/AddingProgramToSessionStartup](https://help.ubuntu.com/community/AddingProgramToSessionStartup)

---

### Post by oldos2er on 2011-09-29
Moved to Ubuntu +1 (Oneiric Ocelot).

---

### Post by Srocchi on 2011-09-29
These run AFTER login
[https://help.ubuntu.com/community/AddingProgramToSessionStartup](https://help.ubuntu.com/community/AddingProgramToSessionStartup)
[http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)

This one looked like it was gonna work, but at the sight of my Login Screen (after going through all of the steps and loggind off for my own test) my GPU bailed on me. Hard Reboot.

I'm going to try making it a service as suggested by seawolf 167  
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

---

### Post by lucazade on 2011-09-29
in /etc/rc.local ?
not sure X is already started when rc.local is invoked.. anyway give it a try.

---

### Post by Srocchi on 2011-09-29
> **oldos2er said:**
> Moved to Ubuntu +1 (Oneiric Ocelot).

:S  
This _really_ doesn't seem like the best place for it, but who am I to disagree?

---

### Post by cariboo on 2011-09-29
> **Srocchi said:**
> :S  
This _really_ doesn't seem like the best place for it, but who am I to disagree?

This is the right place for your thread, as most of the answers you've gotten so far don't work in Oneiric. Most of the posters have given you a solution that will work in Natty but not newer versions.

---

### Post by Srocchi on 2011-09-30
None of these worked :(
This weekend I'll try to find some time to try all of these on a fresh 11.04 install, since its been said that some of these would work on it.

If anyone has a different possible solution to it, I'm still here.

I'll give news as soon as I try these on a fresh install.

---

### Post by Srocchi on 2011-10-03
I fixed my problem with a very unorthodox solution (well, it worked). 

Edited the .bashrc and included the line I wanted it to run.
I called it "unorthodox" because now this command runs every single time I open up a terminal. So it wouldn't work if it was a more cpu/time demanding command.

Works on 11.04 and 11.10

---

