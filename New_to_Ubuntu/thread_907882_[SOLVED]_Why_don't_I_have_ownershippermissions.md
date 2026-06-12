---
title: "[SOLVED] Why don't I have ownership/permissions?"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by edzell on 2008-09-01
Newbie running 7.10 gnome after uninstalling 8.04

I wanted to run a windows program (calendarscope) under wine. In my home directory, created a folder - calendar - in which to place the install .exe file. But in file browser the folder icon showed a little padlock and I was prevented from putting anything into it. Why would it be locked when I was working in my home directory, and created it there?

I eventually managed to unlock it with chown although scarcely knowing what I was doing; just parroting a command line from another thread. Then installed calendarscope using the wine command. All well and good -it runs. Now I want to copy the c_scope data folder from my windows HD into the wine folder where the program executable now sits. But once more I find the wine folder (calendarscope) is locked and, worse still, it is apparently owned by root. Again why???

My attempts to gain ownership using chown - still largely unaware how it works - have failed and I'm just stymied. What's going on here and how can I get control of it?

---

### Post by lazyart on 2008-09-01
If you're manipulating folders (copy and such) via sudo then you're gonna accidentally lock em up.  Are you launching calendarscope / wine via sudo?

Anyhow, restore permissions on all your folders with```
sudo chown edzell:edzell -R /home/edzell
```
assuming your login is edzell on your machine.

Good luck.

---

### Post by edzell on 2008-09-01
> **lazyart said:**
> If you're manipulating folders (copy and such) via sudo then you're gonna accidentally lock em up.  Are you launching calendarscope / wine via sudo?

Anyhow, restore permissions on all your folders with```
sudo chown edzell:edzell -R /home/edzell
```assuming your login is edzell on your machine.

Good luck.

Many thanks for the swift reply. Can't recall on which occasions I used sudo. I generally only use it when I find I can't do what I want without it. 

It seems you're saying that Ubuntu doesn't know that sudo means that edzell is the "operator" at the moment? I thought I was the only one who could use sudo and should automatically have ownership/access to whatever I  create in my home directory?. (Not that there are any other users created so far.) Sorry to burden you with my complete lack of understanding, and my verbose attempts to illlustrate it.

Wine has put a calendarscope launcher on the desktop and that's how I've been starting it. I'll run the chown code you've provided. I think I already tried it but likely got it wrong - but I'm still anxious to know how to avoid giving ownership to root when I don't intend it.

---

### Post by edzell on 2008-09-01
Thanks lazyart, the chown code did the trick. If you have comments on the rest of my queries please do let me have them.

---

### Post by dRock1286 on 2008-09-01
Don't forget to mark this as solved in case anyone else has had problems with it too.

---

### Post by edzell on 2008-09-02
> **dRock1286 said:**
> Don't forget to mark this as solved in case anyone else has had problems with it too.
I will but I'm giving it a bit of time to see if the unanswered parts of my questions get addressed. In a sense it's not "wholly" solved for me. I still don't understand why/how ownership of the new file became root, or how to avoid repeating that problem.

I'm grateful for the help received but eager for a more complete understanding.

---

### Post by Paqman on 2008-09-02
> **edzell said:**
> I still don't understand why/how ownership of the new file became root, or how to avoid repeating that problem.


If you were using Nautilus as root (ie: launched with gksu nautilus) or if you created the folder in the CLI with sudo mkdir, then it would be owned by root.

---

### Post by lovinglinux on 2008-09-02
All files and folders under /home/me should be owned by me? Are there any exceptions?

I will be safe restoring ownership with the command posted above?

I confess I used Nautilus with sudo, so I probably need to fix this...

---

### Post by Perfect Storm on 2008-09-02
> **lovinglinux said:**
> All files and folders under /home/me should be owned by me? Are there any exceptions?

I will be safe restoring ownership with the command posted above?

I confess I used Nautilus with sudo, so I probably need to fix this...

Only if you manipulate with them/it with sudo command. So in general be careful what you do with sudo command even in your own home directory.
I'm not fond that given advise for people using nautilus with gksudo as it seems alot of people accidently mess up stuff quickly because of it.

Much safer to use the terminal in such cases if anything required superuser.

---

### Post by lovinglinux on 2008-09-02
> **Artificial Intelligence said:**
> Only if you manipulate with them/it with sudo command. So in general be careful what you do with sudo command even in your own home directory.
I'm not fond that given advise for people using nautilus with gksudo as it seems alot of people accidently mess up stuff quickly because of it.

Much safer to use the terminal in such cases if anything required superuser.

I'm being more careful, specially after reading that I shouldn't run any GUI with sudo, but gksudo instead. So if I need to run nautilus with superuser privileges I should run it with gksudo instead right? If I opt to make file operations with commands in the terminal, then I don't need gksudo right?

---

### Post by Perfect Storm on 2008-09-02
gksudo is used when running a graphical/gui application/program
sudo non-graphical.

Example with text editor programs;

gedit:
gksudo gedit <path>/<file>

nano:

sudo nano <path>/<file>

---

### Post by lovinglinux on 2008-09-02
> **Artificial Intelligence said:**
> gksudo is used when running a graphical/gui application/program
sudo non-graphical.

Example with text editor programs;

gedit:
gksudo gedit <path>/<file>

nano:

sudo nano <path>/<file>

Sorry if this sounds stupid, but isn't Nautilus a graphical one?

---

### Post by Perfect Storm on 2008-09-02
Yes, nautilus is graphical.
By running a graphical application with only sudo instead of gksudo you can mess up the permission of it. Which is why it's important to use the right sudo command.

---

### Post by lovinglinux on 2008-09-02
> **Artificial Intelligence said:**
> Yes, nautilus is graphical.
By running a graphical application with only sudo instead of gksudo you can mess up the permission of it. Which is why it's important to use the right sudo command.

Is there a way to know if I have already messed with something? I'm sure I used sudo with Nautilus several times :oops:

---

### Post by Perfect Storm on 2008-09-02
Well, if you don't get any weirdness (like permission complain) by using nautilus as normal user - then it should be okay.

---

### Post by lovinglinux on 2008-09-02
OK then. Thanks.

---

### Post by edzell on 2008-09-02
Ouch! For me this is turning into a big can of worms.

1. I created a folder - calendar - within my home folder, using the "create folder" option; accessed by right-clicking in the file browser window. But the folder created  was immediately shown as locked Is this normal?

2. Is Nautilus the same as File Browser or subtly different? And what about File Manager?

3. So far I've used sudo in both the gui terminal and "the other one" that you get with ctrl-alt-F1 etc. Does it behave differently in the one vs the other?

4. What is gksu, and the same questions apply.

5. When I installed calendarscope using sudo wine, it was given root ownership, which prevented me from migrating the data files to it from my windows drive. Now I've changed ownership to myself, but I'm thinking it might have been smarter to only change permissions, so that the program stays available to other users (though there aren't any yet..) Comments welcome.

Apologies to any who may be impatient with such basic questions. This stuff must be hard for many newcomers, especially if they thought they'd be using it easily right away. At least it is for me (You can tell :))

---

### Post by lazyart on 2008-09-06
1. That's odd.  You should look at the permissions of that folder and find out what they are set to.  Sounds like you were running nautilus as super user, but something doesn't seem right still.
2. They are the same.
3. The difference in sudo and gksudo is not where you are running them, but that you are using them to run.  If it's just a terminal command, or a terminal program use sudo.  If you are launching a graphical application, then use gksudo.
4. gksu is equivalent to su and it not used in Ubuntu by default.  You'll have to research it on your own-- it's against forum policy to discuss it.
5. You shouldn't have installed calendarscope using sudo-- which may be the unlying problem here.  Just wine would have been fine since it "installs" to your home directory.  Sudo was then mucking around in your home directory, adding files and setting permissions for the root user.

BTW-You can keep ownership of a file and still give permission for others to use it...

---

### Post by edzell on 2008-09-07
[FONT=Verdana, sans-serif][SIZE=3]Thanks, lazyart, for the comprehensive reply. I'll mark the thread solved even though not everything is crystal clear to me.[/SIZE][/FONT]
 

 [FONT=Verdana, sans-serif][SIZE=3]Truth to tell, I'm finding linux a bit too challenging/time consuming for me at present so I'm probably going to forget it for a while. But that's way off topic so I'll leave it at that.[/SIZE][/FONT]

---

