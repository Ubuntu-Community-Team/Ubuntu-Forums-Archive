---
title: "Black screen with dialog reading &quot;Out of Range&quot;"
date: 2013-08-13
forum: New to Ubuntu
---

### Post by steve_ball2 on 2013-08-13
Newby

I need help please!  I've just installed Ubuntu 12.04.2 alongside a Windows XP OS on an old x86 based Dell Optiplex GX 270 machine with a GenuineIntel ~2261 MHz processor and an Intel [R] 82865G Graphics Controller.  When I boot the machine I’m presented with the option to either load Windows XP or Ubuntu.  When I select Ubuntu there is an initial pause and then a black screen with a small dialog reading “Out of Range”.  I have browsed the forum and done some internet research and I am satisfied that it is a screen resolution problem.  I just don’t know how to correct the problem?  Any and all help would be greatly appreciated!

Thanks in advance,
Steve

---

### Post by Boab1993 on 2013-08-13
Hi steve_ball2,

Lets try a bit of experimenting, hold down shift while your computer is booting and the grub menu should appear.

When it gives you the option to boot to linux, press E.

An editing screen should appear, at the end of one of the lines should read 'quiet splash', replace with 'quiet splash nomodeset'

Follow the instructions to continue booting with those settings at the bottom of the grub menu.

---

### Post by steve_ball2 on 2013-08-14
Hi Boab1993,

You are the MAN!  Thank you for your quick response to my problem.  I used the edit that you suggested and got the Ubuntu graphical interface.  However, I still have a bit of a problem and would like to pick your brain a little further if I may?  Once Ubuntu boots I am presented with a dialog box telling me that the system is in low graphics mode (screen, graphics card, and input devices).  The dialog box has a command button reading &#8216;OK&#8217;.  I press enter on the keyboard and I am presented with a second dialog box asking me what I would like to do: (1) Run in low graphics mode; (2) Reconfigure graphics; (3) Troubleshoot the error; (4) Exit to console login.  The problem is that I have no keyboard or mouse input and I can&#8217;t choose any of the options presented.  I can&#8217;t do anything really?  If you could help I would really appreciate your input.  I&#8217;m looking forward to my first cup of Ubuntu!

Also, how do I save the edit?  Upon reboot I had to edit the line again.

Thanks in advance Boab1993,
Steve

---

### Post by Boab1993 on 2013-08-15
Sorry for the late reply steve.

To save the edit, login with the options i gave you again and you can either go to a command line and type:

gksudo gedit /etc/default/grub
[FONT=arial]
Or go to the path /etc/default/grub

and for either, edit the file in the same way (find quiet splash, add nomodeset)

Which ever your comfortable with.

As for the login events, can i get a screen shot of the screen you are given with the options?

There will be many, many more cups my friend
[/FONT]

---

### Post by steve_ball2 on 2013-08-15
Hi Boab1993,

No need for apologies... I really appreciate your help with this issue.

I've attached a couple of jpeg screen shots.  I have keyboard input with the 'System in low-graphics mode' dialog.  I depress the keyboard Enter key and then I'm present with the second dialog 'What would you like to do?'  At this point I have no mouse or keyboard input.  I'm just stuck.      

Thanks again Boab1993,
Steve

---

### Post by Boab1993 on 2013-08-15
Ah okay, i think ive got you.

Low graphics mode occurs when you have usually bad graphics drivers, among other things.

I was looking for documentation i could refer you to, as this problem has many solutions, and stumbled upon this very comprehensive reply on [http://askubuntu.com/](http://askubuntu.com/)

Heres the solution : [http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)

They run through pretty much every fix, so it'll but much easier than you sifting through documentation.

Hope this gets you on your way, report back with findings.

---

### Post by steve_ball2 on 2013-08-15
No luck yet Boab1993 but I'll keep trying until I get it right.  

I am actually going to be taking an online course (Intro to Linux/Unix Operating Systems) this September 4[SUP]th[/SUP] offered by the University of Massachusetts/Lowell.  I will be able to connect to their campus servers for the course.  But, I just wanted to get a bit of a head start by familiarizing myself with the operating system before the start of class.  Again, thank you for all your help.  

Steve

---

### Post by Boab1993 on 2013-08-15
Hmm, you can always try updating all software,

Try typing 'sudo apt-get update' then 'sudo apt-get upgrade', restart. Its a long shot but can't hurt.

If  your using it for academic purposes and have no problem with  re-installing, another option is to try the alternate CD install.

[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

Its always good to start at the deep end and work your way back i find when learning about these kind of things.

---

### Post by steve_ball2 on 2013-08-16
Hi Boab1993,

I tried updating the software to no avail.  So, I decided to re-install the operating system using an alternate cd.  At the conclusion of the install I rebooted the machine and I had the same problem: stuck with the 'What would you like to do?' dialog box and no keyboard input.  

But I agree with your philosophy: starting at the deep end and working your way back is the best way to learn.
 
Thank you for your time and patience Boab1993.
 
Steve

---

### Post by Boab1993 on 2013-08-16
Hi again steve, 

Might be a silly time to ask, but what are your hardware specs(HDD size, RAM)

Sad to hear about that not working out, but ill keep looking for some kind of solution. 

Remain hopeful.

---

