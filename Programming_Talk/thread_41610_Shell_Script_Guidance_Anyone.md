---
title: "Shell Script Guidance Anyone???"
date: 2005-06-14
forum: Programming Talk
---

### Post by apoc.feuer on 2005-06-14
I'm not sure whether I'm posting it at the correct section or not though, moderators kindly shift this thread to a appropiate section if this thread is ir-relevant here. Ok, the story is this, I have a Ubuntu machine that requires gain access to my Unix server. Right now I'm using telnet to gain access to it. But the process might be complicated to my end users the steps are as follows: 

From terminal: 
Step 1:telnet
Step 2:telnet>environ define TERM 'VT100' [COLOR=Blue]<---Because my Unix can only recongnise terminals that are set to VT100[/COLOR]
Step 3:telnet>environ define TERMCOLOR 'VT100' 
Step 4:telnet>open 192.XXX.X.XXX
Step 5: End user log in with their userid and password to gain access to our server

In order for me to minimise typo-error for end-users etc, I have created a shell script so that the above process is automated and end users only need to log in our Unix server to perform their daily tasks. This is where I got stuck...below is my shell script (Guess i simplify the entire script too much??!! I'm clueless here...)

My first shell script (test.sh)
==================
Line 1: telnet
Line 2: environ define TERM 'VT100' 
Line 3: environ define TERMCOLOR 'VT100'
Line 4: open 192.XXX.X.XXX
==================

Error message
==========
./test.sh: line 2: environ: command not found
./test.sh: line 3: environ: command not found
==========

It's seems that my script is unable to carry out the correct command in telnet environment. Is it possible to let my script 'know' that it's in the telnet environment and it must set the terminal type to VT100 in order for it to gain access to our unix server? Any advise/suggestions would be greatly appreciated. (Anyway this is my first time doing shell script hehe)

---

### Post by thumper on 2005-06-14
[QUOTE=apoc.feuer]From terminal: 
My first shell script (test.sh)
==================
Line 1: telnet
Line 2: environ define TERM 'VT100' 
Line 3: environ define TERMCOLOR 'VT100'
Line 4: open 192.XXX.X.XXX
==================
[/QUOTE]
I would suggest setting the TERM and TERMCOLOR environment prior to calling telnet.

something like this:
```

#!/bin/sh
TERM=VT100
TERMCOLOR=VT100
export TERM TERMCOLOR
telnet 192.168.x.xxx
```

---

### Post by apoc.feuer on 2005-06-14
[QUOTE=thumper]I would suggest setting the TERM and TERMCOLOR environment prior to calling telnet.

something like this:
```

#!/bin/sh
TERM=VT100
TERMCOLOR=VT100
export TERM TERMCOLOR
telnet 192.168.x.xxx
```[/QUOTE]

Hi Thumper, thanks for the suggestion, did try to set TERM and TERMCOLOR prior to calling telnet, however when I get to the login of my Unix server its says that it is unable to recongise my terminal type, therefore I think I must set the terminal type in telnet environment in order to make the script work. 

But hey, thanks for the assistance and suggestion given. Thank you so much...:grin:

---

### Post by jakev383 on 2005-06-14
Try something like this:

#!/bin/sh
( echo "environ define TERM 'VT100'"
sleep 1
echo environ define TERMCOLOR 'VT100'
sleep 1
echo open 192.168.1.1
sleep 5
) | telnet

Or some variation of that.

---

### Post by desdinova on 2005-06-14
I think you'll need to slap those environ commands in **~/.telnetrc** as they're config commands for telnet

---

### Post by LordHunter317 on 2005-06-14
[QUOTE=desdinova]I think you'll need to slap those environ commands in **~/.telnetrc** as they're config commands for telnet[/QUOTE]
 desdinova's got it right.  

telnet is a clasical interactive UNIX program.  Meaning it's tied to the terminal in a lot of fundamentally stupid ways, making it very difficult to script around when necessary.

---

### Post by apoc.feuer on 2005-06-14
Thanks for the support and suggestion so far, as I'm pretty new to linux, would to know where can I find the telnetrc files. From the information I gathered from WWW so far, most of the manpage says that its located at the user's home folder which I cannot find this file in my home folder.... :???:  

Have I misinterpreted the information??? I'm clueless here....

---

### Post by LordHunter317 on 2005-06-14
If it's not there, you have to create it.  That's also pretty typical UNIX

---

### Post by jerome bettis on 2005-06-14
have you considered using ssh instead?

much better idea IMO

---

### Post by apoc.feuer on 2005-06-15
[QUOTE=jerome bettis]have you considered using ssh instead?

much better idea IMO[/QUOTE]

hmm...do I have to write script for ssh or is it a interactive application??? I'm open to new ideas or suggestions though, I been trying out telnetrc for the entire morning but to no avail (Probably I'm slow and I know nuts about also) 

Anyway, thanks for the earlier suggestions given by: jakev383, desdinova, LordHunter317 and you jerome bettis.... :)

---

### Post by ltmon on 2005-06-15
[QUOTE=apoc.feuer]hmm...do I have to write script for ssh or is it a interactive application??? I'm open to new ideas or suggestions though, I been trying out telnetrc for the entire morning but to no avail (Probably I'm slow and I know nuts about also) 

Anyway, thanks for the earlier suggestions given by: jakev383, desdinova, LordHunter317 and you jerome bettis.... :)[/QUOTE]

SSH is less archaic (i.e. you usually don't have to worry about terminal settings) and more secure (passwords not sent in clear for a start).  As long as you have an ssh daemon running on your server.  Then all you usually need to do is:

> ssh 192.168.x.x

---

### Post by LordHunter317 on 2005-06-15
Well, that's not  true.  He still very well may have to worry about terminal settings.  SSH is just less fustrating about it than telenet.

Of course, the machine he's connecting to has to run the SSH server, and if it's not, it may not be trivial to get it installed and running.

---

