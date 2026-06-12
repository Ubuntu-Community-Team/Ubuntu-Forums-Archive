---
title: "Checking Battery State [OK]  X Crashing"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by grahamt2280 on 2008-11-14
Hi All,

I've just done a fresh install of Kubuntu Intrepid on my Acer Travelmate 530. 

The problem I have now is the screen randomly goes black and a single line of text saying "Checking Battery State [OK]" appears at the top for a few seconds, then X restarts and I am left at the login screen.

The crashing occurs whether I'm on mains power or battery.

I've done a full update & upgrade & dist-upgrade, but that didn't help.

I've also turn on proposed updates, and re-upgraded, also to no effect.

I know that its not a hardware issue, as before Intrepid I was a happy Gutsy and Hardy user on this same laptop, (and Dual boot XP works fine as well).

Does anyone have any pointers for me?

Thanks in advance.

Graham

---

### Post by talsemgeest on 2008-11-15
This really does seem like a bug, so you should post it on launchpad. That way, if it is a problem with Ubuntu it can be fixed.

[https://launchpad.net/ubuntu/+filebug](https://launchpad.net/ubuntu/+filebug)

---

### Post by itsasailboat on 2008-11-23
i have the same problem after upgrading kubuntu from heron to ibex on my hp dv1000 series laptop with Intel® Extreme Graphics 2.  

furthermore, graphics are garbled at the corners of the login screen.  

has a bug report been filed?  anyone else have this problem?

---

### Post by marco_ask on 2008-12-11
I have the same problem. 
I have been using Intrepid Ibex for some days, but today I can't login and the login screen come back after account insertion... :confused:

---

### Post by dkuhlman on 2008-12-11
I have this problem, too.  The boot process stalls with last line showing "Checking battery state".

Here are a couple of additional pieces of information:

1. When it stalls there, I can switch to a text mode console (with Alt-F1) and linux is usable.  But, no X Windows or desktop, of course.

2. I have this problem with kernel 2.6.27-7.  But, I can boot kernel 2.6.24-21 just fine.

- Dave

---

### Post by marco_ask on 2008-12-12
Let me explain better my situation:
> **dkuhlman said:**
> 
I have this problem, too.  The boot process stalls with last line showing "Checking battery state".

My system is not stalled on "Checking battery state", but precisely restarts and goes back to the login screen.
> **dkuhlman said:**
> 
1. When it stalls there, I can switch to a text mode console (with Alt-F1) and linux is usable.  But, no X Windows or desktop, of course.

With Ctrl + Alt + F1 the system goes to text mode console, but it asks me login name and password; I enter them and the system responds with the number of my console (tty1) and then back to ask login name and password...
> **dkuhlman said:**
> 
2. I have this problem with kernel 2.6.27-7.  But, I can boot kernel 2.6.24-21 just fine.

Unfortunately I have no other kernel to load, then I have the system unusable.

If anyone knows any help, he would be grateful

---

### Post by unable111 on 2008-12-12
I have the same problem as marco_ask
Worked ok this morning, rebooted this evening and now this.

I notice that I am unable to remotely log in via ssh, pop3(dovecot) or webmin.

I can type the wrong password in and it rejects that, type the right one in, sits there for a couple of seconds and then prompts me for the login again.

---

### Post by unable111 on 2008-12-12
Add to that.
I have been able to go to recovery, drop to root shell and that works, then startx works so it is not a problem with xwindows or ati drivers.  I noticed the USB or ps/2 mice didn't work, I am not sure if they are supposed to here.

Cannot do anything in kde without a mouse so crtl+alt+delete restarted it, shutdown without problems.
Back at the root prompt I was able to start dovecot as something to test authentication and telnet to port 110, took the username and password then after a few seconds came back as
-err Temporary authentication failure

---

### Post by uwave on 2008-12-12
I too,
As the original poster stated, Am having the black screen "x"
but mine was flashing every couple of seconds.
This was on several Panasonic CF-28 toughbooks I tried.
Nothing would get me in, I had to remove the power to reboot.

I have a post started to try and figure out whats going on.
I am currently trying the ALT distro's in hopes that I can get thru this without too much pain.
I did have success on two other desktops so I'm happy there but my other three desktops are a mess. One with scrolling harddrive error lines after the install altho the partitioning went well. still boots XP.
The other starts up fine but the video is a messed-up double image (TNT2 card). XP still works fine on it too.

I hope this gets fixed soon. I'm seeing too many problems on the board and I am thinking I should try again at a future date.

---

### Post by drmayuraa on 2008-12-14
> **grahamt2280 said:**
> Hi All,

I've just done a fresh install of Kubuntu Intrepid on my Acer Travelmate 530. 

The problem I have now is the screen randomly goes black and a single line of text saying "Checking Battery State [OK]" appears at the top for a few seconds, then X restarts and I am left at the login screen.

The crashing occurs whether I'm on mains power or battery.

I've done a full update & upgrade & dist-upgrade, but that didn't help.

I've also turn on proposed updates, and re-upgraded, also to no effect.

I know that its not a hardware issue, as before Intrepid I was a happy Gutsy and Hardy user on this same laptop, (and Dual boot XP works fine as well).

Does anyone have any pointers for me?

Thanks in advance.

Graham







What is the solution for the problem. I'm experiencing the same.

---

### Post by GuiGuy on 2009-02-21
Add me to that, when downgrading my wife's PC from 8.04 to 8.10

Well, at least I have an image to put back

---

### Post by salida on 2009-03-10
hey there. i had the same problem and just managed to fixed it after many retries.

i booted normaly and when stack on "checking battery state"
i pressed ctrl+f1 and i edited xorg.conf 
(sudo nano /etx/X11/xorg.conf) i tryied to use the default settings for resolution and depth.then saved and reboot

and it just worked out....

hope it helps someone

---

### Post by Ubangi on 2010-10-11
... and I am too. Anyone even looked at this since it was first reported 5 years ago??

---

### Post by devanalias on 2010-11-20
I had same problem.
That is not a battery (or acpi) problem because it says "checking battery status.... **OK**"
It hangs later.
Try logging in and typing xinit in the shell
Then, if doesn't work I can't help you.
If xinit works try gedit or any similar gtk programm.
I think you'll get a undefined symbol g_malloc_n ... or something about libgdk-x11....
If that's your case go here: [http://bugs.launchpad.net/ubuntu/+bug/301601/comments/7](http://bugs.launchpad.net/ubuntu/+bug/301601/comments/7)

good luck!

---

