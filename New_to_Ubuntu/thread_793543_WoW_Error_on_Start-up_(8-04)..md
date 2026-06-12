---
title: "WoW Error on Start-up (8-04)."
date: 2008-05-13
forum: New to Ubuntu
---

### Post by papuccino1 on 2008-05-13
I made all the tweaks, read all the threads and I still have this problem.
Every time I start WoW I get a critical error and my screen gets smaller, I have WINE and the latest Nvidia driver.

What should I do, has anyone found a solution to it?

---

### Post by shinobitux on 2008-05-13
You say your screen gets smaller? Does your desktop resolution change or does WoW just crash and show that window in your screenshot? Do you ever see anything when you start the game (ie - black screen, a movie, etc)?

This may be a bit beyond me but it kinda looks like a permissions issue. Is the directory for C:\Program\ Files specified in your wine config file in your home directory or does your user have write access to it?

---

### Post by papuccino1 on 2008-05-13
> **shinobitux said:**
> You say your screen gets smaller? Does your desktop resolution change or does WoW just crash and show that window in your screenshot? Do you ever see anything when you start the game (ie - black screen, a movie, etc)?
My resolution changes and I can't get it back up. I can't hear any music or see anything, I barely open the game and the error pops-up.

> **shinobitux said:**
> Is the directory for C:\Program\ Files specified in your wine config file in your home directory or does your user have write access to it?
I'm the only user on the PC doesn't that make me have all the rights (if not how do I change it).

Note: I'm running WINE 0.9.59.

---

### Post by Caram on 2008-05-13
> **papuccino1 said:**
> 
I'm the only user on the PC doesn't that make me have all the rights (if not how do I change it).


Nope. Root is required for MANY things.

---

### Post by shinobitux on 2008-05-13
Hm...where is your wow.exe file?

One thing to try *once* is to "sudo wine wow.exe"

This will run the game in superuser mode. Definitely not a permanent solution.

I don't like the fact that your resolution changes. Did you compile the Nvidia drivers yourself?

---

### Post by shinobitux on 2008-05-13
I don't think I explained things thoroughly enough.

Caram is completely right.

When you log in and run Ubuntu, by default you run with user-level access (unless you log in as root).

User-level access gives you complete access to your home directory but little or no write access to the rest of the computer.

Being the computer's owner and having setup the computer you are automatically included in the admin group which can invoke superuser privileges. You do this by prefixing the word "sudo" (super-user do) to the beginning of a command line argument.

A superuser has nearly unlimited access to your computer. The reason you don't login as root is for the same reason you shouldn't use Windows in administrator mode. You can literally do *anything* and a mistyped command can mean doom.

---

### Post by sonoma_jack on 2008-05-13
> **papuccino1 said:**
> I made all the tweaks, read all the threads and I still have this problem.
Every time I start WoW I get a critical error and my screen gets smaller, I have WINE and the latest Nvidia driver.

What should I do, has anyone found a solution to it?

I got this exact problem.  I called Blizzard and they said the crash (ERROR #132) is usually caused by out dated drivers.  

I grabbed EnvyNG and installed new drivers and still have the same problem, I hope we can get some help here.

---

### Post by justin whitaker on 2008-05-13
Check WOWWiki.

[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

Make the recommended changes to the config.wtf.

I had exactly the same issue on my machine, but once I went in and set OpenGL and the ffx tweaks, it ran fine.

---

### Post by papuccino1 on 2008-05-14
Ok I got it working but every time I want to enter the server (after typing my account and password) I get a instant message saying; "Disconnected from the server."

I checked the realmlist.wtf and everything is as it's supposed to be. I read the Troubleshooting F.A.Q.'s from WoWWiki ([Link]("http://www.wowwiki.com/Linux/Wine/Troubleshooting")) and I found no solution, no one has had this problem before.

====== EDIT ======

Got it to work, thanks for all the help guys I really appreciate it :)

---

### Post by sonoma_jack on 2008-05-14
> **papuccino1 said:**
> Ok I got it working but every time I want to enter the server (after typing my account and password) I get a instant message saying; "Disconnected from the server."

I checked the realmlist.wtf and everything is as it's supposed to be. I read the Troubleshooting F.A.Q.'s from WoWWiki ([Link]("http://www.wowwiki.com/Linux/Wine/Troubleshooting")) and I found no solution, no one has had this problem before.

====== EDIT ======

Got it to work, thanks for all the help guys I really appreciate it :)

papuccino, what did you do exactly to get it "working"? I'm still having a problem, tried a bunch of stuff.  I'm still pretty n00b-tastic at linux, but I work in the gaming industry and feel an obligation to push the industry in this direction (or be ready for it when it goes on its own).

---

### Post by Firefighter503 on 2008-05-14
> **justin whitaker said:**
> Check WOWWiki.

[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

Make the recommended changes to the config.wtf.

I had exactly the same issue on my machine, but once I went in and set OpenGL and the ffx tweaks, it ran fine.

What if you are having this exact same error, but don't have a config.wtf file? For the life of me I can not find it, (fresh install of ubuntu 8.04, and WoW) and I think it is not created until you log into a character... am I wrong about that?

---

