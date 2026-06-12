---
title: "How to decode Ubuntu command names."
date: 2008-07-06
forum: New to Ubuntu
---

### Post by esbo on 2008-07-06
Is there a list anywhere which decodes ubuntu command names from something utterly meaningless into something descriptive?

---

### Post by Xerp on 2008-07-06
What specifically would you like decoded? Do you have an example?

---

### Post by natman on 2008-07-06
Not sure exactly what you mean but have a go at this
[HTML]man pwd[/HTML]
putting man before the command gives a description of it. Have a play around. Otherwise i use this site for general Linux help
[HTML]http://www.linuxcommand.org/learning_the_shell.php[/HTML]
Sorry should have said, try man pwd in a terminal.

---

### Post by lamego on 2008-07-06
Sure, that is one of the most import features on Unix/Linux systems, it's the "man" (manual reader) command, on the terminal just type:
```
man command
```

---

### Post by lisati on 2008-07-06
For starters, commands that begin with "ls"often have something to do with listing stuff; "su" stands for "super user"; "cp" for "copy", "mv" for "move"

You might want to look here: [http://ubuntuforums.org/showthread.php?t=846097](http://ubuntuforums.org/showthread.php?t=846097)

---

### Post by esbo on 2008-07-06
> **Xerp said:**
> What specifically would you like decoded? Do you have an example?

Not that i can recall, it's hard to  remember random meaningless names, thats why I wanted a list.

---

### Post by esbo on 2008-07-06
I am specifically looking for a list, 'man' requires me to know the name of
the command in the first place.

I guess I could type every word I know into man and see if it is a command, but I figure that will take several hours.

---

### Post by quantumstitch on 2008-07-06
This is a start:
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
Best,
-stitch

---

### Post by hansdown on 2008-07-06
Go to fosswire.com where You can download the unix/linux command reference sheet. They also have an ubuntu reference cheat sheet.

---

### Post by steveneddy on 2008-07-06
Two things:

[http://ubuntuforums.org/showpost.php?p=338302&postcount=1](http://ubuntuforums.org/showpost.php?p=338302&postcount=1)

Here's a CLI start:

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by Dr Small on 2008-07-06
> **esbo said:**
> I am specifically looking for a list, 'man' requires me to know the name of
the command in the first place.

I guess I could type every word I know into man and see if it is a command, but I figure that will take several hours.
Here is a large list:
[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

---

### Post by oldos2er on 2008-07-06
> **esbo said:**
> I am specifically looking for a list, 'man' requires me to know the name of
the command in the first place.

I guess I could type every word I know into man and see if it is a command, but I figure that will take several hours.

 Hit the Tab key twice in the terminal to show all commands.

---

### Post by decoherence on 2008-07-06
*apropos* or *man -k* will search the manual pages based on keywords you enter at the command. for example
```

$ apropos network

/etc/network/interfaces (5) [interfaces] - network interface configuration fo...
NetworkManager (8)   - network management daemon
NetworkManagerDispatcher (8) - daemon that runs commands in response to off/o...
aseqnet (1)          - ALSA sequencer connectors over network
avahi-autoipd (8)    - IPv4LL network address configuration daemon
bittorrent-downloader.bittorrent (1) - download files using a scatter-gather ...
btdownloadcurses (1) - download files using a scatter-gather network
btdownloadcurses.bittorrent (1) - download files using a scatter-gather network
btdownloadheadless (1) - download files using a scatter-gather network
btdownloadheadless.bittorrent (1) - download files using a scatter-gather net...
ctstat (8)           - unified linux network statistics
dhclient-script (8)  - DHCP client network configuration script
dund (1)             - BlueZ Bluetooth dial-up networking daemon
fping (8)            - send ICMP ECHO_REQUEST packets to network hosts
fping6 (8)           - send ICMP ECHO_REQUEST packets to network hosts
gnome (1)            - The GNU Network Object Model Environment
gnunet-tracekit (1)  - - overlay network traceing
ifconfig (8)         - configure a network interface
ifdown (8)           - take a network interface down
ifup (8)             - bring a network interface up
interfaces (5)       - network interface configuration for ifup and ifdown
iwconfig (8)         - configure a wireless network interface
iwgetid (8)          - Report ESSID, NWID or AP/Cell Address of wireless network
iwpriv (8)           - configure optionals (private) parameters of a wireless...
jng (5)              - JPEG Network Graphics (JNG) sub-format
libmng (3)           - Multiple-image Network Graphics (MNG) Reference Librar...
etc..
```

browse through the list until you find something that looks promising. Then use the *man* command to figure out if it really does what you want and how to use it. ie
```

man NetworkManager
```
or 
```

man 8 NetworkManager
```

though the second isn't really needed with NetworkManager's paltry man page. 

Try variations on the keyword if you don't find what you're looking for.

---

