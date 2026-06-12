---
title: "Basic Script Writing Question"
date: 2006-07-16
forum: Programming Talk
---

### Post by featherking on 2006-07-16
Sorry for the double post but i think this is a better place to ask this,

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

### Post by jayemef on 2006-07-16
You can accomplish this pretty easily with xterm, as it has the -hold option to do exactly what you are asking about. So for example, you could run
```
#!/bin/bash

xterm -hold -e "sudo aireplay-ng --help"
```

I had responded to a similar question earlier, suggesting to use the read command. Didn't actually try it, but it turns out that it doesn't work. This worked fine for me though.

---

### Post by featherking on 2006-07-16
Well thats a step in the right direction, but it doesnt give me a prompt where i can then run the command. Does that make sense? So no i can see all the different options, but then i want to say "aireplay-ng -a -b -c" and have it run, is there anyway to bring up the prompt?

---

