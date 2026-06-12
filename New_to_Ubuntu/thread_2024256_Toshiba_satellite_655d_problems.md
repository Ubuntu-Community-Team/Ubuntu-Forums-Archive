---
title: "Toshiba satellite 655d problems"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by Partychuckwalla on 2012-07-13
Three weeks ago, I posted this:
[I]I just installed 12.04 on a brand new Toshiba C655. With or without the  boot CD, the process stops at the login screen. I can't move the arrow  with the touchpad, nor can I enter text into the Password box.
I'm a real rookie, please help.[/I]
The post had 107 views, but no replies. Did I not include enough information? I finally got back around to addressing this problem.
Really, please help

---

### Post by circlemaster on 2012-07-13
Some things you could try from the top of my head:

See if you can access a terminal by pressing CTRL + ALT + F1
Connect a USB mouse and see if the pointer moves then

---

### Post by QIII on 2012-07-13
Can you give us a bit of info about the hardware, particularly the graphics?

How did you install this?  Dual boot, Wubi, wiping out Windows?

(Don't be concerned that you got so many views and no answers.  It just means that those who looked at it didn't have an answer for you.  If you don't get an answer in 24 hours, bump the thread by adding a new post.  Not less than 24 hours, though.  Since this is a worldwide community and some people may not see it while you are generally around, you can try bumping at 36 hours to get more visibility.)

---

### Post by Partychuckwalla on 2012-07-13
Some more information:
Upon powering up, I get a purple screen, the screen goes blank and then an ubuntu screen appears with 5 dots under the word ubuntu.  At this point, the cursor and the keyboard will lock-up. When I hold down the power button the machine turns off. As I repeat trying to boot, I get varying lengths of time before it locks.  I once got to enter a few characters of my login before it locked.

I held Alt+Ctrl+F1 and I got:

[I]Ubuntu 12.04 LTS pinto-Satellite-C655D tty1

pinto-Satellite-655D login:[/I]

but the keyboard is locked

---

### Post by Partychuckwalla on 2012-07-13
circlemaster-Thanks for your help. At least I got to see something different.  Progress!

Qlll- I jumped in with both feet and wiped windows. I don't anything about my graphics driver. I have the computer with me, but I left all of the info at home, and am now at the library using free Ubuntu machines!

---

### Post by QIII on 2012-07-13
If this is happening at that point, what I was going to suggest will not work.

I found the base specs for your machine, but within the same model there may be different hardware.  I'll assume it's a Turion with an ATI 4350 graphics chip.  Strangely, AMD APUs often present themselves as Turions and are even advertised that way.  If it's an APU, you'll have hybrid ATI/ATI graphics, which can be an issue.

Edit:  OK.  See now that you wiped Windows.

Did you download as a torrent or a normal download?  Did you check the md5sum on your installation media after downloading it?  Did you burn the image on your writer's lowest speed?  Did you do the disk integrity check on the media?

Sometimes things can be good enough to "install", but if there is a problem with image integrity then strange things can happen.

---

### Post by Partychuckwalla on 2012-07-13
Qlll- Wow!
It was a normal download, but I don't know the write speed nor did I check the integrity.
On a unrelated note, how can I refresh the forum to update the posts. Oh, by the way did I mention that I'm a real rookie?:confused:

---

### Post by QIII on 2012-07-13
For this thread, just hit the refresh button on your browser once in a while.

Does your disk work in a Live session?  That's the "Try Ubuntu" option when you boot from the disk.

---

### Post by Partychuckwalla on 2012-07-13
Refresh button? They are running Mozilla Firefox.  Is it the clockwise circular arrow at the right hand side of the address bar?
When I try to boot from the CD, I get the same results.

---

### Post by BBQdave on 2012-07-13
> **QIII said:**
> hybrid ATI/ATI graphics, which can be an issue.

Sometimes things can be good enough to "install", but if there is a problem with image integrity then strange things can happen.

I have a Toshiba Satellite C655 with intel graphics. I am currently running Fedora 16 (64-bit) with no issue. I have tested Ubuntu 12.04 LTS (64-bit) and the cd loaded the live session fine, and installed fine. I tested Ubuntu 12.04 LTS for a few days with no issues.

So there is a very real possibility of a bad install (live cd). If you can boot up the Ubunutu 12.04 LTS (64-bit or sometimes referenced as amd64) and run the live session, that should show you how your hardware will perform (with Ubuntu).

If the install media is fine, than it could be your hybrid ATI graphics giving trouble, which is odd, because the standard video drivers in the linux kernel (though basic) should work with your hardware. The issue would become 3d acceleration not supported. Which again, you could test with running the live cd session.

---

