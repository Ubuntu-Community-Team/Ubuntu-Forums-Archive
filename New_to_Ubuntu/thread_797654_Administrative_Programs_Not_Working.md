---
title: "Administrative Programs Not Working"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by dconstruct on 2008-05-17
Hey guys,

I have a problem.  For whatever reason, most of my Administrative programs will not open.  Like, when I try to do Update Manager to update programs, it opens but when it gets to the point where it actually has to install, it freezes up.  And, when I go to Add/Remove Programs, it opens up but after I select the programs and go to add, it freezes.  And, any of the System > Administration programs don't even open.  It says "Starting Whatever..." in the menu, but it never actually opens up.

I'm running Ubuntu Studio on Hardy Heron, with my laptop HP 530.  Any ideas or suggestions?  Any little codes you need?  Let me know!

Thanks,

Adam

---

### Post by kellemes on 2008-05-17
> **dconstruct said:**
> Hey guys,

I have a problem.  For whatever reason, most of my Administrative programs will not open.  Like, when I try to do Update Manager to update programs, it opens but when it gets to the point where it actually has to install, it freezes up.  And, when I go to Add/Remove Programs, it opens up but after I select the programs and go to add, it freezes.  And, any of the System > Administration programs don't even open.  It says "Starting Whatever..." in the menu, but it never actually opens up.

I'm running Ubuntu Studio on Hardy Heron, with my laptop HP 530.  Any ideas or suggestions?  Any little codes you need?  Let me know!

Thanks,

Adam

From a terminal window can you please try the following?
And try again installing stuff..
```
sudo apt-get update
```

---

### Post by dconstruct on 2008-05-17
Okay, I ran that.  And, an update manager icon came up in the top menu.  I double clicked it.  It opened up.  Gave me one update for Totem.  I clicked Install Update.  A thing in the bottom menu came up saying "Starting Administrative Application" and the Update Manager turned blue.  And, then nothing happened.

What next?  What do you mean by try installing things again?  What things?

Thanks mate!

Adam

---

### Post by dconstruct on 2008-05-17
Any ideas?  For the update manager, I can work around it by right clicking on the icon and just clicking Install All Updates and it works fine.  But, it might have something to do with the password verification dialog that pops up, because it never usually gets that far like it did in previous versions of ubuntu.

---

### Post by nowshining on 2008-05-17
if the gui isn't working for u u can install from the terminal and yes using TAB for completing works.

sudo apt-get install nameofitemuwanttoinstall

---

### Post by dconstruct on 2008-05-17
Yeah, I know how to do that.  The main issue that I'm having is that I'm not able to change system settings or customize preferences because they won't open after I click on them.  And, when I upgraded to Hardy, it did say that I had a successful installation.  So, I never encountered any problems during the install either.  Any more ideas?

---

### Post by nowshining on 2008-05-17
try opening them up via the command line and do a few actions - and then exit out of the program and return to the terminal and post if any errors if any.

---

### Post by dconstruct on 2008-05-17
For example, what command would I run to open up Hardware Drivers through the terminal?

---

### Post by dconstruct on 2008-05-17
In playing around, I noticed in the System Monitor that i had several processes running under the id "gksu" that linked up to update-manager and things like that, that had frozen.  And, I ran the command:

```
killall gksu
```

And, it seemed to unfreeze some of my processes that I had running.  But, after it had finished working with whatever it was doing before it froze, I tried searching for updates in update manager, and it froze again.  And another killall command  unfroze it, but I still don't want to have to run that command every time I want to update or change something in the GUI.

Any ideas?

---

### Post by nowshining on 2008-05-17
well u can open up any of them, try editing the menu and see what command it shows in the command box for that. I don't use Ubuntu - I use Kubuntu.

My guess is it's the same thing I'm having - of which sudo and the name of the program works fine but won't work in this mode from the menus, of which I changed to run in terminal and insert my pw there which circumvents this problem.

if u want u can also try 

sudo xhost +

to disable the X access control list. - "sudo xhost -" re-enables the access control list.

if all else fails or u'd like to try this first, u can try removing all .Xauthority files - logging out and back in to see if this works.

---

### Post by nowshining on 2008-05-17
oh I forgot to add - i just remembered, did u click the arrow when installing? it may be asking u a question and either typing a Y for Yes or N for No to continue might suffice or okay to accepts a license, etc..

---

### Post by dconstruct on 2008-05-18
It opens up the programs from the terminal.  Is there a way that I can change the menu commands to be able to access them differently or with the password already inputted?

---

### Post by nicolas_ho_taylor on 2008-05-18
I'm having similar problems. I suspect it began when I enabled Auto-login. 
Now most administrative functions fail. There's a box on the task bar for a brief while, after I select System> Administration> Login Window (for example). The box says "Starting Administrati..."
And after 10 seconds or so, it vanishes. Shortly after that, the task bar box for "Login Window" vanishes too.
It's as though the program attempted to open a password-request dialogue, but failed.

I think this is a bug, not a Newbie mistake. I'm heading over to the bug-report forum. See you there!

PS - some administration still works - the System> Administration> Users and Groups option requests my password as usual, and works fine!

---

### Post by rpage on 2008-05-19
I am also getting "[COLOR="Red"]Starting Administrative Application[/COLOR]" and then it just goes away leaving the Update Manager locked up. This is only happening on my laptop. My desktop has all the updates and functions fine.

---

### Post by dconstruct on 2008-05-19
Could you post a link to the bug report forum thread you start so I can keep an update on how to fix this when it comes?  I just bought a wireless mouse and I can't open up the Hardware Drivers to use it.

Thanks!

Adam

---

