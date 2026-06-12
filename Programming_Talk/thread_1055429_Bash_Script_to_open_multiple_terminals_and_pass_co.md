---
title: "Bash: Script to open multiple terminals and pass commands to them"
date: 2009-01-30
forum: Programming Talk
---

### Post by derelict888 on 2009-01-30
I've been searching around but I can't find what I'm looking for (I'm sure I'm just using the wrong strings). I want to create a script that will run a for loop and open a new instance of terminal and pass a command to it, say ping. I can get multiple windows open during a loop but the commands are all run in the original terminal. Here is the code I currently have;
```

for ip in ` < "$file" `; do
	{
	gnome-terminal;
        ping -c 2 $ip | tee -a ping_summary.txt
	}
done

```
I know this code isn't right, but I don't know how to make the ping portion of the loop get passed into the newly opened terminals. Thanks for any help

---

### Post by slakkie on 2009-01-30
Interesting question, but why do you want to do this?

You could background your task and run several tasks in the same terminal.

Like this:

```

for i in $(cat somehosts) ; do
     ping $i | tee -a $i.log &
done

```

---

### Post by derelict888 on 2009-01-30
Well I have a full /19 of IPs that I'm pinging (8190 IPs) so rather than wait for 8190 IPs ping individually, I'd like to split up the job over serveral terminals. It will help me know I've routed them correctly.

---

### Post by slakkie on 2009-01-30
Use nmap for that nmap -sP a.b.c.d/19

---

### Post by geirha on 2009-01-30
For the original question, you could do something like:
```

#!/bin/bash
for ip in ` < "$file" `; do
    gnome-terminal -x bash -c "ping -c 2 $ip | tee -a ping_summary.txt; read -n1" [color=red]&[/color]
done

```

The "read -n1" at the end is so that the terminal will not close immediately after the ping is done, but rather wait until a key is pressed.

EDIT: Forgot the & to put the process in the background. Added it in red now.
EDIT2 (over one year later): 
for var in `` is bad practice. My above code should've been
```

#!/bin/bash
while read ip; do
    gnome-terminal -x bash -c 'ping -c 2 "$1" | tee -a ping_summary.txt; read -n1' _ "$ip" [color=red]&[/color]
done < somehosts

```

---

### Post by derelict888 on 2009-01-30
Good suggestion, unfortunately I do have other IPs all over the place. Currently, after I've changed domains on my IPs or vice-versa, I'll cat all the said IPs to 1 file. So the file could have multiple class Cs from all over the place - so your suggestion works great for the /19 but not for lots of IPs not grouped in any /#.

Currently I'll just ping a few random IPs in a few of the ranges, but I'd rather make the machine do a check on all of em  : )

---

### Post by slakkie on 2009-01-30
Then you cannot do that, that is correct. But I was thinking, you need to only traceroute one IP per /24 for to check wheter the routing for the whole /19 is setup correctly. Which are 32 IP's in total.. 

But again, that will not work for you.

---

### Post by derelict888 on 2009-02-02
> **geirha said:**
> For the original question, you could do something like:
```

#!/bin/bash
for ip in ` < "$file" `; do
    gnome-terminal -x bash -c "ping -c 2 $ip | tee -a ping_summary.txt; read -n1" [color=red]&[/color]
done

```
The "read -n1" at the end is so that the terminal will not close immediately after the ping is done, but rather wait until a key is pressed.

EDIT: Forgot the & to put the process in the background. Added it in red now.

The code you wrote did work, and I forgot to make some vital changes. Realizing I didn't want 10,000+ terminal windows popping up I was supposed to change how many IPs the list had or change how often a new instance of terminal was called. So in my testing phase I ran the script which began opening a /19's worth of terminals for every IP lmao. Thanks, I have what I need now (I think) to finish my script.
:popcorn:

---

### Post by aybhave on 2010-06-22
Hi,

Im also facing a similar problem. This is my code

#!/bin/sh

gnome-terminal -e "tail -f /var/log/kern.log" -t "Kernel Log"
gnome-terminal -e "date" -t "Iperf"


The first terminal opens properly, but the second does not. Any ideas?

Thanks

---

### Post by geirha on 2010-06-22
*tail -f* runs "forever".
*date* outputs the current date and exits, and when the terminal's command exits, the default behavior of the terminal is to exit too. You can change that behavior in gnome-terminal's settings, or you can make sure the command does not exit immediately.

```
gnome-terminal -t "Iperf" -x bash -c 'date;read' &
```
Here we use a shell to run date, and then read when date is done. read will run until it gets a line of input.

Oh, and don't forget to background the gnome-terminals; otherwise the second terminal will not open before the first terminal has closed, etc.

[http://mywiki.wooledge.org/ProcessManagement](http://mywiki.wooledge.org/ProcessManagement)

---

### Post by aybhave on 2010-06-22
Thanks for your prompt reply.

So what I want to do is the following. Im working on a project in which I need to keep 4 windows open on the screen at a time. This is what I want to run in each window

Window 1: cd /home/ayb/Code
Window2: ssh into emucontrol.ece.cmu.edu and run some command say 'date'
Window3: ssh into emucontrol.ece.cmu.edu and run some other command say 'date' and 'ls' one after the other
Window4: ssh into emucontrol.ece.cmu.edu and run yet another command say 'ls'

I want all these windows to remain open after the script finishes. I also want to provide the password of SSH directly from the command and not type it manually.In this way, I can quickly get my environment up and running every morning instead of doing everything manually.

I would be grateful if you could provide a script to do this

Thanks

---

### Post by aybhave on 2010-06-22
Thanks for your prompt reply.

So what I want to do is the following. Im working on a project in which I  need to keep 4 windows open on the screen at a time. This is what I  want to run in each window

Window 1: cd /home/ayb/Code
Window2: ssh into emucontrol.ece.cmu.edu and run some command say 'date'
Window3: ssh into emucontrol.ece.cmu.edu and run some other command say  'date' and 'ls' one after the other
Window4: ssh into emucontrol.ece.cmu.edu and run yet another command say  'ls'

I want all these windows to remain open after the script finishes. I  also want to provide the password of SSH directly from the command and  not type it manually.In this way, I can quickly get my environment up  and running every morning instead of doing everything manually.

I would be grateful if you could provide a script to do this

Thanks

---

### Post by slavik on 2010-06-22
1. set up ssh trust
2. read what others said about backgrounding and running commands in terminals.

---

### Post by aybhave on 2010-06-23
#!/bin/sh

gnome-terminal -t 'Iperf' -x 'date' &
gnome-terminal -t 'Kernel Log' -x 'tail -f /var/log/kern.log' &

I did try to use the suggestions posted here and the above example script still does not work. A terminal pops up saying "Error creating child process". I cannot use the 'read' method outlined earlier because it will exit after one line of input, whereas I want to keep the terminal runnng.

Any suggestions?

--Aditya

---

