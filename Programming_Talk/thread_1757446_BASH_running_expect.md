---
title: "BASH running expect"
date: 2011-05-13
forum: Programming Talk
---

### Post by Binary-Synapse on 2011-05-13
Hello.
 
I want to automate a bash script so it does not ask you for a password.
But this time I cannot touch the sudoers file.
 
The very simple bash script is this one:
 
```
 
#!/bin/bash
 
command1="./Documents/program/superY"
sudo $command1
 
rm -f /home/userX/MYscript.sh
 
exit 0

```
 
Some notes:
The script will be run on many equal machines (same hardware and software image).
All machines have the same user passwords.
Let's assume userX pass is something like: [COLOR=darkorange]**ccXdfd729mYv**[/COLOR]
 
The problem is that program **superY** has to run with root privileges.
And I don't want to type the long and complex _userX_ password everytime.
 
How can I do this?
 
I thought of program **expect** (which is installed on all the machines where the script is going to run).
 
But how can I integrate **expect **inside my BASH script?
 
Can someone provide me an example?
I'm no pro and I have seen some [COLOR=red]**ssh**[/COLOR] examples where expect is used but I didn't understand them quite well (maybe because expect uses Tcl which I never used until now).
 
Thank you

---

### Post by bashologist on 2011-05-14
Unless I've misunderstood the question would this work?
```
echo password | sudo -S ./script
sudo -k
```
Read the manual for more details if that's what you were looking for. Good luck.

---

### Post by Binary-Synapse on 2011-05-15
Hello bashologist.
 
Your suggestion worked perfectly! Thank you.
 
[COLOR=red]Follow-up question:[/COLOR]
 
Can I instruct sudo to **not** display the following message:
```
[sudo] password for userX: 
```
 
I don't want to show that line of text asking for the password in the terminal.
It's only a cosmetic issue, but still...
Is it possible?
 
Thank you

---

### Post by bashologist on 2011-07-01
Slow response, but better late than never?
```
echo password | sudo -S ./script 2> /dev/null
```
Redirect stderr to null.

---

### Post by Binary-Synapse on 2011-07-24
Hello bashologist.
 
It worked perfectly!!
 
I want to be your friend. :D
 
Regards

---

