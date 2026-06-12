---
title: "SSH emacs"
date: 2008-01-25
forum: Programming Talk
---

### Post by spetsacdc on 2008-01-25
I use ssh [email]username@thecomputersaddress.edu[/email] to connect to these server computers at my school. I have a .cpp file on that computer that I want to edit from my home laptop. 

So I do: emacs hello_world.cpp

The problem is that it turns the terminal into like a "terminal version of emacs". The mouse doesn't work and it is all black and white. On my pc I can type emacs22-gtx and it opens a nice version of emacs.

How do I edit the remote files in emacs22-gtx?

At school my professor has a mac and when he is showing us how to program he has a colored emacs.

Thanks

---

### Post by LaRoza on 2008-01-25
I have no experience with Emacs.

I do not know if you can run gui apps over SSH. You can use SFTP instead.

---

### Post by spetsacdc on 2008-01-25
Hmm that gives me:

ssh: xxxx.xxx.edu: Name or service not known

Is there a difference between ssh and shh. I have both in my notes, but I figured I wrote it down wrong once.

---

### Post by LaRoza on 2008-01-25
> **spetsacdc said:**
> Hmm that gives me:

ssh: xxxx.xxx.edu: Name or service not known

Is there a difference between ssh and shh. I have both in my notes, but I figured I wrote it down wrong once.

I don't understand what happened. What is shh?

SFTP [http://en.wikipedia.org/wiki/SSH_file_transfer_protocol](http://en.wikipedia.org/wiki/SSH_file_transfer_protocol)

Use FileZilla or maybe gFTP.

---

### Post by spetsacdc on 2008-01-25
I don't think shh is anything...I just copied ssh in class incorrectly.

Also, I made an error logging in with sftp...now it works.

But, for some reason I can't get either emacs to run, or run my compiled programs. Are the commands different than when using ssh?

I tried:

sftp> emacs22-gtx project_1.cpp
Invalid command.

sftp> emacs
Invalid command.

sftp> emacs project_1.cpp
Invalid command.

sftp> emacs ./project_1.cpp
Invalid command.

sftp> ls
project_1       project_1.cpp   project_1.cpp~  

sftp> project_1
Invalid command.

sftp> ./project_1
Invalid command.

---

### Post by wolfbone on 2008-01-25
C-x C-f /username@thecomputersaddress.edu:hello_world.cpp

Read the TRAMP manual:

C-h i g(tramp)usage <RET>

---

### Post by CptPicard on 2008-01-25
No, you don't use sftp for running anything. Running emacs on top of a terminal emulator is supposed to make it "look all black and white and the mouse doesn't work" -- that's the text-mode emacs without X11. That's how I use emacs most of the time when administering my remote servers and it works just great :)

Now, you **can** actually run X apps over the network as the X protocol is network transparent. This is something I think most people haven't ever even tried or even know how to do, but it's a totally cool feature and not something you'd get on Windows.

What you would need to do is to tunnel the X protocol over ssh. A quick googling finds this tutorial for example

[http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

---

### Post by NGSG on 2008-01-25
two approaches:

CTRL-X CTRL-F file://mylogin@myremotemachine:myfile

it will ask for the password each time you save, you can then set ssh such that you don't need to give your password.
a more simple approach, is to ssh directly to the machine and use emacs -nw if installed there.

for colors META-X font-lock-mode 

hope this helps.

---

### Post by LaRoza on 2008-01-25
> **wolfbone said:**
> C-x C-f /username@thecomputersaddress.edu:hello_world.cpp

RTFM:

C-h i g(tramp)usage <RET>

See the policy of this forum (link in my sig). Number seven should interest you.

---

### Post by spetsacdc on 2008-01-25
Thanks for the help, but I guess I'll stick with the text mode emacs. Does anyone know how to access the toolbar with like the file button on it? I try to click it and nothing happens.


Thanks

---

### Post by CptPicard on 2008-01-25
To be honest, I don't know, because I learned the keyboard commands... as should you. :) That's where the power lies.

---

### Post by wolfbone on 2008-01-25
> **NGSG said:**
> two approaches:

CTRL-X CTRL-F file://mylogin@myremotemachine:myfile

it will ask for the password each time you save, you can then set ssh such that you don't need to give your password.
a more simple approach, is to ssh directly to the machine and use emacs -nw if installed there.

for colors META-X font-lock-mode 

hope this helps.

file://... ???

And how is ssh'ing in to the machine simpler than just opening the file as normal?

---

### Post by SuperElectric on 2008-10-17
If you want to use emacs exactly as it's configured on your school (remote) machine, you should ssh into it and then run emacs. It'll run remotely, but display as normal (not in terminal mode) locally. This is the simplest option, but if your net connection is slow, this may be frustrating, since this requires it to pump pixels over the net at real time.

To run emacs remotely, connect to your school computer first using:
ssh -Y myusername@myschoolcomputer

Once logged in, just type "emacs" as usual, and it'll be running remotely and displaying locally.

If you find the above leads to slow interaction, you can also run emacs on your home (local) machine, and have it use ssh to access your files over the net. This saves net traffic because all it has to do is read text files and send your edits when you save, as opposed to pumping pixels.

To do this, launch emacs on your home machine, then in emacs type Ctrl-x, Ctrl-f, which brings up a file prompt in the minibuffer. In the minibuffer enter //ssh:myusername@myschoolcomputer:~/path/to/myfile.cpp

It'll ask you for your password, then you're on your way.

---

### Post by iponeverything on 2008-10-17
if you 

ssh -X [email]user@place.edu[/email]

and run emacs on the remote server, it should pop up the X11 version on your desktop.

---

