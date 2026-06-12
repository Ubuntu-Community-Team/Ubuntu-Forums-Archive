---
title: "Basic Script Writing Question"
date: 2006-07-16
forum: Programming Talk
---

### Post by featherking on 2006-07-16
Hello,

Im trying to make a script that will open up a terminal window, run the program with the help option to display all available options and then allow me to look at those and type whatever i want.

I have this so far

```

#!/bin/bash

gnome-terminal -x sudo aireplay-ng --help


```
The script executes fine, but it closes the window when its done. I want it to stay open so i can look at what help displayed and then type what i want. Is there any way to make the window stay open? This is what i want to see:

```

  Aireplay-ng 0.6 - (C) 2006 Thomas d'Otreppe
  Original work: Christophe Devine
  http://www.aircrack-ng.org

  usage: aireplay-ng <options> <replay interface>

  source options:

      -i iface  : capture packets from this interface
      -r file   : extract packets from this pcap file

  attack modes (Numbers can still be used):

      --deauth      count : deauthenticate 1 or all stations (-0)
      --fakeauth    delay : fake authentication with AP (-1)
      --interactive       : interactive frame selection (-2)
      --arpreplay         : standard ARP-request replay (-3)
      --chopchop          : decrypt/chopchop WEP packet (-4)

chris@Chris-Laptop:~/Desktop$

```

---

### Post by llamakc on 2006-07-16
Why not put something in .bash_aliases instead?

---

### Post by featherking on 2006-07-16
Im afraid im unfamiliar with .bash_aliases? (Still pretty new here) what would that help me with?

---

### Post by tseliot on 2006-07-16
I have moved the thread to the "Programming Talk" section so that your chances to get an answer will (possibly) increase

---

### Post by Randomskk on 2006-07-16
Hm.. I can't think of anything to do this off the top of my head, but..
There is a live CD, BackTrack, which is designed for security and stuff, and all their terminal programs have menu entries, when you click the menu entry it loads a console with the help thing displayed and keeps the console opened.
You may be able to do a similar thing, although I don't have a copy of BackTrack handy.

Still, going on what program you're trying to run, I imagine backtrack may be of interest anyway :P

---

### Post by featherking on 2006-07-16
Yeah i got the idea from a similar live cd, i cant remember which one though, but i dont need all the tools from cd's like those, i just like to be able to run a select few, but i really like having the help options load up so you can see what to do.

Ill have to see if i can figure it out from there i guess

---

### Post by llamakc on 2006-07-16
If you're using Gnome, you can add a Launcher to your Desktop or Panel.

In the 'Command' field for the launcher put: 

sudo aireplay-ng --help

and check the 'run in terminal box'.

This should work (not tested though).

---

### Post by featherking on 2006-07-16
Thanks but unfortunately this yields the same results as what im getting. Aireplay is running and its working correctly but as soon as its done showing the help prompt it exits, thinking that its done its job. Ive been looking and still have found no answer, someone mentioned getting backtrack live cd as it apparently does what im looking for, but i have super slow internet here and would take a while to download a live cd...

---

### Post by featherking on 2006-07-16
Solution:

Using an xterm instead gnome-terminal let me pass this command

```
xterm -e /bin/bash -c "aircrack-ng; sudo -s"
```

I loaded up a nUbuntu cd i found and this is the command he uses to load each tool. It achieves just what i want; however, if someone could explain to me exactly what this does i would appreciate it!

chris

---

