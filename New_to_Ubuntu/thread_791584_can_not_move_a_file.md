---
title: "can not move a file"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-05-12
This weekend I installed Realplayer 11 on my computer (and it actually works) but I can not move the files from my desktop to my home folder.

When I try to move it the error I get is:

Error while moving "RealPlayer-11.0.0.4028
There was an error moving the file into /home/shawn.
Error moving file: Permission denied

When I try to change the properties in the preferences it says that it has some sort of owner called "root" and I have no password for this name.

Can you help me move this?

---

### Post by gn2 on 2008-05-12
Press Alt+F2 type gksudo nautilus

Press Enter.

The file browser will now open with full root permissions and you will be able to move any files.

Be careful what you move or edit and close the file browser immediately when you are finished.

---

### Post by Monicker on 2008-05-12
Did you download the file while acting as root?

Prefix your move command with sudo


```
sudo mv file /home/shawn
```

---

### Post by chili555 on 2008-05-12
In a terminal, do:```
sudo mv /home/shawn/Desktop/RealPlayer-11.0.0.4028 /home/shawn/
```

---

### Post by Tyche on 2008-05-12
> **saskatchewan said:**
> This weekend I installed Realplayer 11 on my computer (and it actually works) but I can not move the files from my desktop to my home folder.

When I try to move it the error I get is:

Error while moving "RealPlayer-11.0.0.4028
There was an error moving the file into /home/shawn.
Error moving file: Permission denied

When I try to change the properties in the preferences it says that it has some sort of owner called "root" and I have no password for this name.

Can you help me move this?


I'll try.  First, I'm going to define some terms for you, so that you will understand what I'm suggesting:

1. sudo = super user do = a command to temporarily allow a user administrative privileges based on the user's password.

2. chown = change owner = a command to change the ownership of a file or directory.

3. root = the absolute administrator of a computer.  Ubuntu does NOT create a root user, but uses the sudo command to emable administration on a temporary basis.

4. terminal = From the pull-down menues, Applications -> Accessories -> Terminal.  This provides you with the ability to use the command line to make changes in your computer.

5. cd (followed by the name of a directory) = change directory.  In a terminal, the cd command will allow you to change your location to a different location.

And now, I think we're ready to start:

1.  Open a terminal.

2.  type "cd Desktop" (without the quotes) and hit the ENTER key.  This will put you in the Desktop directory.

3.  type "sudo chown shawn RealPlayer-11.0.0.4028" (without the quotes) and hit the ENTER key.  The terminal will return a request for your password.  Type it and hit enter (the password will NOT show up on screen). When the terminal returns to the normal prompt, the ownership of the file should have been changed, and the root authorization (the sudo command) will have terminated.  This is a security feature to keep unauthorized people from making major changes to your computer.

I hope this helps.

---

### Post by saskatchewan on 2008-05-12
Excellent!!!

Thanks everybody, I got it moved.

---

### Post by pchandler on 2008-05-31
> **gn2 said:**
> Press Alt+F2 type gksudo nautilus

Press Enter.

The file browser will now open with full root permissions and you will be able to move any files.

Be careful what you move or edit and close the file browser immediately when you are finished.

Im having the same problem. But surely there is a better way, say chmod something and setting the folder permissions via a terminal ? So then you can drag and drop from your own desktop, rather than running as root when you dont need to ?? nautilus is great, but Im thinking that running your suggestion doesnt really solve the problem, just offers a solution to skirt round a problem that will still remain.

---

### Post by pchandler on 2008-05-31
> **pchandler said:**
> Im having the same problem. But surely there is a better way, say chmod something and setting the folder permissions via a terminal ? So then you can drag and drop from your own desktop, rather than running as root when you dont need to ?? nautilus is great, but Im thinking that running your suggestion doesnt really solve the problem, just offers a solution to skirt round a problem that will still remain.

I used Tyche's method which solved the problem to.

---

