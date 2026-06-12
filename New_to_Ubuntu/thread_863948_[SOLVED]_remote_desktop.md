---
title: "[SOLVED] remote desktop"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by pikabuntu on 2008-07-19
I can not get remote desktop to work right.
(see screenshots)

---

### Post by pikabuntu on 2008-07-19
i also have a similar problem if I try to do the same thing but on opposite computers.

---

### Post by pavel989 on 2008-07-19
if ur doing it that way, try instead "localhost" instead of the current name
---------------------------------------------------------------------------
while posting u updated. make sure u have ports forwarded correctly!!!

---

### Post by pikabuntu on 2008-07-19
what exactly do you mean ?

---

### Post by pavel989 on 2008-07-19
vncviewer localhost

---

### Post by pikabuntu on 2008-07-19
it let me log in and then it did this in the window:
[ATTACH]78237[/ATTACH]
EDIT:
it does this on both computers

---

### Post by pavel989 on 2008-07-19
w8, so u logged into that computer from another and it did that?

also maybe u just need to restart x server?

---

### Post by pikabuntu on 2008-07-19
> **pavel989 said:**
> w8, so u logged into that computer from another and it did that?

also maybe u just need to restart x server?
yeah
how to restart x server?

---

### Post by pavel989 on 2008-07-19
well rebooting works, but theres a faster way.

i warn you ahead of time, it will log u out and close everything so save open documents:

ctrl+alt+backspace

---

### Post by pikabuntu on 2008-07-19
> **pavel989 said:**
> w8, so u logged into that computer from another and it did that?

also maybe u just need to restart x server?
Just making sure but I mean the computer I logged on with did this. :)

---

### Post by pikabuntu on 2008-07-19
I restarted x and it still does that. :(
edit:
what's happening is that i am using the computer to take control of itself

---

### Post by pavel989 on 2008-07-19
so the computer which logged onto the vnc server, got all freaky? in that case it doesnt have anything to do with the server. How many times did u try to open the connection with the other command?

---

### Post by pavel989 on 2008-07-19
oh well then yea itd get freaky. try using another computer

---

### Post by pikabuntu on 2008-07-19
> **pavel989 said:**
> so the computer which logged onto the vnc server, got all freaky? in that case it doesnt have anything to do with the server. How many times did u try to open the connection with the other command?
once or twice, but the computer is taking over itself, i figured out, which explains the strange screenshot

---

### Post by pikabuntu on 2008-07-19
> **pavel989 said:**
> oh well then yea itd get freaky. try using another computer
the other one does the same thing :(

EDIT:
What exactly does "localhost" do anyway?

---

### Post by pavel989 on 2008-07-19
goes to the local host. your computer.

what do u mean the computer is taking over itself exactly? are there vnc viewer windows open?

if you want to connect to other computers, itd have to be an ip address.

---

### Post by AlanR8 on 2008-07-19
Looks like your master machine doesn't know the name of the slave machine looking at that error message.

Easiest way to deal with that is to tell the host to connect to the slave using IP addresses for instance:

vnc:/192.168.0.XXX

---

### Post by pikabuntu on 2008-07-19
how do i do this with an ip address
EDIT:
did not see above post :)

how do i find out the ip address?

---

### Post by pikabuntu on 2008-07-19
ok the ip address is .105
but it says this when i did what u said:

bash: vnc:/192.168.0.105: No such file or directory

---

### Post by pavel989 on 2008-07-19
do vncviewer 192.168.0.105

---

### Post by pikabuntu on 2008-07-19
> **pavel989 said:**
> do vncviewer 192.168.0.105
this works!!!!
it is *extremely *slow tho.

---

### Post by pikabuntu on 2008-07-19
thanks for the help !!!

---

### Post by pavel989 on 2008-07-19
np. if its slow, it could be that your resolution is too high on the server, or you might not have ports opened. either way, vnc isn't known for its speed...

---

### Post by pikabuntu on 2008-07-19
oh well. I am just excited that it works!

---

### Post by pikabuntu on 2008-07-19
> **pavel989 said:**
> np. if its slow, it could be that your resolution is too high on the server, or you might not have ports opened. either way, vnc isn't known for its speed...
what do u mean by ports?

---

### Post by pavel989 on 2008-07-19
if you have a home router, there's usually a configuration inside of it.

And theres something called port forwarding. It's a security feature to prevent hackers. you have to either trigger ports 5900 and 5901 or forward them to a specific computer. have a look here: [http://portforward.com/]("http://portforward.com/")

---

