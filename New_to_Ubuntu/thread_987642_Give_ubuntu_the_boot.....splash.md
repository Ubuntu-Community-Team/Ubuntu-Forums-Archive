---
title: "Give ubuntu the boot.....splash"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by newbrain on 2008-11-19
Hi,
   I'm a real greenhorn as far as Linux is concerned. But I have just dipped my toe in the water and installed ubuntu 8.10 on my old HP ZV5000 laptop. The problem I have with unbuntu is this.

From time to time..(about once a day) my system crashed when i boot. After asking a few questions on the other forums (that was helpful) I know now that I have what is know as the boot splash problem. In short I get a second ghost progress bar when I boot linux. I am told that this is a known issue.So what should I do.....(take a running jump I hear)

Should I keep posting on different forums? And while we are on the subject of forums. How am i supposed to know which forum I should post a question on?

I am now at the point of throwing in the towel and trying another distro.

I would hate to do this, but what option do I have? Please, please, please help me out on this one. any feedback would be great..

I get the impression that much of the ubuntu community operates on a broadcast only mode. i.e 'I say what I like, and I like what I say...but I don't answer questions'. <snip>

1) Is the a problem with the boot splash process
2) When can I expect it to get fixed
3) Do I need to register it as a new bug
4) Who can I take to.
5) Am I wasting my time.

<snip>

---

### Post by Aiello on 2008-11-19
<snip>

What I would suggest is:
A. Installing start up manager ```
sudo apt-get install startupmanager
```, and then installing another splash screen from [www.gnome-look.org](www.gnome-look.org)
B. See if you can't somehow disable or reinstall the program that creates the splash screen. I'm sure from a little searching and Googling you can come up with something.
C. If you aren't too invested in your current installation, try installing 8.04 instead. It is a LTS edition and has been around for longer, so more bugs might be ironed out of it.

<snip>

---

### Post by jimmy the saint on 2008-11-19
I don't know what it was about your post that made want to just bend over backwards and help you, but man do I ever.  So here is my advice.  First, I agree with the 8.04 idea.  Hardy, 8.04, is a long term release.  It has had around 7 months to have most of the bugs worked out.

Second, I don't know if by other forums you mean other sections (as in not beginner talk on the Ubuntu forums), or other forums (as in NOT the Ubuntu forums) but I do know that I, and everyone else here, are here because we enjoy sharing our (in my case limited) knowledge of how to get things done in Ubuntu.  We do this because we had just started once and got a lot of help here and want to give back.  Nobody says you have to come here, or that when you do, we have to tolerate you.  So before you worry about your Ubuntu install, please work on your attitude.  This forum is a friendly place filled with (mostly) friendly people.

Third, if you provide a link to the other threads in which you were told it was a known bug, perhaps we can track that bug report down and see how to best help you.

---

### Post by newbrain on 2008-11-19
Thanks for your replys. I was told it was a known bug in a private mail from another member.

I have had to reboot my ubuntu machine three time now to get it up and running. the splash screen corruption is even worse now...im pulling my hair out now...

I would perfer to keep 8.10 but i guess im stuffed

note to the moderator. in my day it was considered bad manners to filler a message and not offer a solution...quick to critise..slow to help...thanks

---

### Post by newbrain on 2008-11-19
thanks for that...i started out with a friendly attitude, and a problem..and (as i have been told - see above) I have a bad attitude..I wonder why...maybe its because I can't get help..or at least I get conflicting help..Im at a lost..I love you all, but please help me....:(

---

### Post by newbrain on 2008-11-19
Here is a link to a  picture of the kinda thing Im getting

[http://launchpadlibrarian.net/17989328/usplash-doubled-progress-bar.png]("http://launchpadlibrarian.net/17989328/usplash-doubled-progress-bar.png")

Is this a know bug?

---

### Post by anewguy on 2008-11-20
To me, that looks like a video problem.  I would suggest that you push F6 (I think it is) at boot when it says you can, then edit the boot line by adding vga=791 to it and see if it will boot okay.

Dave :)

---

