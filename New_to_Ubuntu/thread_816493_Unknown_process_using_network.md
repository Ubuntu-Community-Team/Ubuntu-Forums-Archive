---
title: "Unknown process using network"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by funkadelic on 2008-06-02
Some unknown application/process is using my network connection -- how can I determine what it is...?

---

### Post by kwacka on 2008-06-02
A couple of command line options:
```
top
``` - The  top program provides a dynamic real-time view of a running system.
It can display system summary information as well as a list of tasks    currently being managed by the Linux kernel.

```
ps -A
``` report a snapshot of the current processes.

---

### Post by funkadelic on 2008-06-02
> **kwacka said:**
> A couple of command line options:
```
top
``` - The  top program provides a dynamic real-time view of a running system.
It can display system summary information as well as a list of tasks    currently being managed by the Linux kernel.

Which column in top shows network activity?

---

### Post by isparkes on 2008-06-02
For network activity, you can also use:

```
netstat -a
```

---

### Post by dracayr on 2008-06-02
none, top and ps have nothing to do with the network

dracayr

---

### Post by funkadelic on 2008-06-02
System Monitor shows that I am *constantly *receiving at ~2KiB/s even when I have no network-related applications open (i.e. just sitting at the desktop)...

Does this make any sense? How can I determine what I am I receiving?

I am using Hardy on an Eee PC... wireless is turned off...

---

### Post by avtolle on 2008-06-02
> **funkadelic said:**
> System Monitor shows that I am *constantly *receiving at ~2KiB/s even when I have no network-related applications open (i.e. just sitting at the desktop)...

Does this make any sense? How can I determine what I am I receiving?

I am using Hardy on an Eee PC... wireless is turned off...
No offense meant by this question; do you have a wired connection? And, just for another dumb question, do you have the weather applete, e.g., set up on the desktop? I know you say there's no network-related applications open, but just a thought.

---

### Post by Het Irv on 2008-06-02
You could also install Wireshark.  It's not the easiest to use, but it might give you some ideas where the packets are going/coming from.

Note: It needs to be run as root to see your network interfaces.

---

### Post by kwacka on 2008-06-02
> **dracayr said:**
> none, top and ps have nothing to do with the network

dracayr
You are, of course, correct.

They merely show **ALL** processes (including the unknown ones) that are running.

---

### Post by funkadelic on 2008-06-02
> **avtolle said:**
> No offense meant by this question; do you have a wired connection? And, just for another dumb question, do you have the weather applete, e.g., set up on the desktop? I know you say there's no network-related applications open, but just a thought.

Yes I have a wired connection that is otherwise working fine. No applets are running.

---

### Post by avtolle on 2008-06-02
> **funkadelic said:**
> Yes I have a wired connection that is otherwise working fine. No applets are running.
Another wild guess; is your clock synched to a network server? I'm shooting in the dark here, as is apparent. And, if you want to wrestle with it, wireshark may help.

---

### Post by Prospero2006 on 2008-06-02
sudo apt-get install ntop

That will break down your network usage nicely.

Also:

sudo apt-get install iptraf

iptraf will dump every raw packet on the network in real time
and show you a running list of which ip addresses are involved.
You'll have to run that one from the command line with

sudo iptraf

---

### Post by Het Irv on 2008-06-03
The easiest thing to do with any IP addresses you get from any of these programs would be to use the whois search under network tools.  It will tell you who owns the IP address, it should give you an idea what is using it.

---

### Post by funkadelic on 2008-06-04
Thanks to all. iptraf shows no actual activity, so I guess this was a false alarm? (A bug with system monitor?)

---

### Post by unimatrix on 2009-03-02
You can find the process using network with lsof if you know which port is being used or which address it's destined to (you can find out with tcpdump or wireshark or similar).

For example, if there's data going in or out port 80, you can type
```
sudo lsof -i :80
```
and it will show you which process is busy on that port (probably Apache in this case).

Or if you see a connection with an address, for example "029.133-78-65.ftth.swbr.surewest.net", you can see which program made it by typing:
```
sudo lsof -i @029.133-78-65.ftth.swbr.surewest.net
```

There, this should answer the question. I know I've been looking for this myself and could never find it.

---

### Post by Mindbleed on 2009-11-30
I am having this same thing happening to me on an Eee PC with Netbook remix.  It is constantly using about a kb of network, but I can't figure out what it is.

If you ever figure out what it is, want to post the solution?  I will post what I find if I find anything.

---

### Post by dvanrensburg on 2011-04-26
I have found the package nethogs to be useful in finding processes using the network.

sudo apt-get install nethogs

sudo nethogs
[COLOR=#000000][FONT=Times New Roman][FONT=arial][/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=arial][/FONT][/FONT][/COLOR]

---

### Post by 3rdalbum on 2011-04-26
I know this is a massive bump, but I'm pretty sure it was either falsely reported in Hardy, or caused by the network card itself (not by any running processes). Updating to Intrepid seemed to fix it - maybe because of better wireless drivers.

---

