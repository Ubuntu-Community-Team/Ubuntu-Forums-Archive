---
title: "[SOLVED] Rebuild/repair an installation to get GDM running"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by jeepfreak2002 on 2008-08-08
OK - my machine did the standard hard drive check after so many restarts and found all sorts of problems.  Thing is, I ran diagnostics on the drive and the RAM and everything checks out.  I thought that the system was turned into swiss cheese, but everything seems to be in tact, except that the Gnome Desktop Manager just will not load.  

I have stopped, and tried to restart GDM, it stops GDM, but says that GDM is not the default desktop manager and will not restart it.

I have tried to reconfigure x-server, re-installed the nvidia driver (through Envy) and nothing gets the GDM up and running.  

What can I do to get GDM up?  Is there sort of a "repair installation" that I could do worse case senario?

---

### Post by markjensen on 2008-08-08
You could try a **sudo apt-get remove gdm** followed by an "install" of it.

Did you recently do something that installed kdm?  or maybe xdm?

---

### Post by jeepfreak2002 on 2008-08-08
no I did not install KDM...  I am using a tweaked version of Ubuntu called Linux Mint, but it is still using Gnome...

I could try your suggestion...  this is the one thing that frustrates me with Linux still.  Like it or not Windows does not just drop you to a command line - ever.  It may not work, but at least you can click your way through a problem.  Still love my Linux, though.

---

### Post by markjensen on 2008-08-09
Funny.  Windows has a recovery console that is text only.

And when Windows has a screen freeze, you are kindof stuck.   In Linux you can open up one of the other terminal sessions and log in.

Can you check for kdm with a
**dpkg --list | grep kdm**
just to make sure that you don't have two display managers that might be in conflict with each other?

---

### Post by jeepfreak2002 on 2008-08-09
WILL DO - I will check tonight.  (I'm at work)

---

### Post by jeepfreak2002 on 2008-08-09
Now on reboot its trying to start and xserver.  I'm getting an error message in a GUI like error.  And it says:  

No servers were defined in the configuration file and XDMCP was disabled.  This can only be a configuration error GDM has started a single server for you.  You should log in and fix the configuration.  Note that automatic and timed logins are disabled now.

---

### Post by markjensen on 2008-08-11
What happened that suddenly the faults are changing?   Either something is making changes, or the hard drive is faulty and files are being lost.

Try removing gdm with
**sudo apt-get remove --purge gdm**
make sure it doesn't drag other dependencies with it, or else you may end up needing to re-install these, too.

From what I see, this should remove the configuration information, too.

Then **sudo apt-get install gdm** should get it back.

---

### Post by jeepfreak2002 on 2008-08-12
Thank you for your help here is the resolution, or I should say the culprit 1st.

I am running a Shuttle XPC barebones box.  Turns out the BIOS (which I had updated due to other issues (months back), I might add...)  cause incompatibility issues with RAM and certain CPU's.

The previous BIOS revision ended in "Q", this BIOS revision ends "R" - you think that there were some kinks with this board????

Anyways - I installed the newest BIOS revision and decided to try Hardy 64bit - it works flawlessly.  Prior to the BIOS upgrade I could not even run an integrity check on the disk or run the LiveCD.

Long story short, the system was never healthy from day 1, and the resulting corruption of the GDM was bound to occur.  Thank you for your time and help.

Jeepfreak

---

