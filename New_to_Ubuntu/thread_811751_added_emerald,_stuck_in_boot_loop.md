---
title: "added emerald, stuck in boot loop"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by yanqui on 2008-05-29
Following instructions elsewhere on this forum, I added emerald to the startup, and now Ubuntu Hardy Heron won't boot.  I log in with my name and password, and it tries, it really does, and I get a screen with a few lines of text, the last of which is "running local boot scripts" then it tries to do something but eventually (in about two seconds) goes back to the login screen.  I've tried the following, with exactly the same results:

Options>Select Session>Gnome

Options>Select Session>Failsafe Gnome

What do I need to do to remove emerald from teh startup if I can't get started up?

---

### Post by glennric on 2008-05-29
How did you add emerald to start up?

---

### Post by yanqui on 2008-05-29
Preferences>Sessions>Add, added emerald, command was emerald --replace

---

### Post by glennric on 2008-05-29
Ok, then to remove emerald from your startup do the following:
First hit Ctrl-Alt-F2, and log in to the console.  Then
```
cd ~/.config/autostart
ls
```
Find the .desktop file that has emerald in its name and delete it with
```
rm filename
```
save it try
```
mv filename ~
```
Then it will be in your home directory if you want it again.
If you don't see a file with emerald in the name you will have to look in the files to find the one that is loading emerald.

---

### Post by yanqui on 2008-05-29
That worked!  Thanks so much.

I'm running the Heron in a virtual machine (VMWare Workstation).  I haven't been able to decipher the instructions on how to install vmware tools yet; could that be an issue?  I don't even really know what vmware tools will do, but I think I read somewhere that graphics will be affected.

---

### Post by glennric on 2008-05-29
I assume that you are running compiz, since you are trying to run emerald.  If this is not the case then you can't run emerald anyway.  

If you do have compiz running, then try starting emerald after you are logged in and see if it works.
To do this type
```
emerald --replace &
```
in a terminal.

---

### Post by yanqui on 2008-05-29
This is what makes this forum so great--I don't feel like an idiot for not knowing how to do something.  Compiz is installed, according to what I see when I go to synaptic package manager.  when you say "have compiz running" I don't know what that means (well, I know what it means, it's obvious) but I don't know how to make it happen.

---

### Post by glennric on 2008-05-29
Did you try to type "emerald --replace &" in a terminal yet?  What happened if so?

To see if compiz is running you can type
```
ps aux | grep compiz
```

---

### Post by yanqui on 2008-07-03
> **glennric said:**
> Did you try to type "emerald --replace &" in a terminal yet?  What happened if so?
no, i didn't try that.

> To see if compiz is running you can type
```
ps aux | grep compiz
```

the output is 6983 0.0 0.2 3004 764 pts/0 S+ 15:59 grep compiz

what does that mean?

---

### Post by tjwoosta on 2008-07-03
usually if compiz or emerald or anything gives you troubles and you cant login
just use safe mode, its a lifesaver

(at the login screen there is a menu at the bottom left)

then you can reverse what you messed up then login normal mode again

---

