---
title: "[SOLVED] Which Forum to use to learn about common Ubuntu features?"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Kellemora on 2008-11-07
Hi Gang

Hate to sound sarcastic, but MOST of my recent questions have gone unanswered here in the beginners forum.  Seems like common things like mounting a hard drive or configuring a hardwired LAN take a backseat to fixing an MP3 player or some speaker squeaks or a game.

Or is it they expect you to KNOW EVERYTHING within two months time?
Or after two months, you are no longer considered a beginner, so nobody answers anymore, other than another noob?

I've tried to be as helpful as I could be on these forums with things I finally figured out that other noob's hadn't yet!
It may not be the right way, but it got the job done and made a few happy campers.

Seems like the reciprocal doesn't exist here anymore!

Did the LTS fall down and go boom from behind 8.04?

I've read thousands of documents over the last two months in trying to learn, many of them are grossly in error, yet end up right here in tips & techniques.

WHAT FORUM AM I SUPPOSED TO USE TO LEARN HOW TO EDIT FSTAB PROPERLY SO A HARD DRIVE CAN BE MOUNTED FROM A COMMAND LINE?????

TTUL
Gary

---

### Post by taurus on 2008-11-07
I didn't see your previous post so I don't know what you are talking about but if you want to edit /etc/fstab from a prompt, just run

```
sudo nano -Bw /etc/fstab
```
Save the changes with <Ctrl>x.

---

### Post by keplerspeed on 2008-11-07
Ubuntu is a community driven OS. The more input from the community (ie you and I) the better the support will get. I would like the say that the ubuntu forums is fantastic, and without a doubt, the best resource of how to's and info.

Posts may go unanswered for a few reasons. If you are not be clear, or being plain rude, may people (like me) will move on to help someone that atleast tries to help themself.

To mount a harddrive from a command line is not difficult, with the right syntax. If you have an issue, be clear about your problem.

Most problems can be solved by spending time to understand documentation. For HD mounting, look here:

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

We are all ubuntu users, taking time out of our day to help others, because we love ubuntu, and want everyone to have an excellent computing experience with it. So be friendly.

---

### Post by philinux on 2008-11-07
[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

From google "fstab".

I'd suggest 
gksudo gedit /etc/fstab

---

### Post by overdrank on 2008-11-07
> **Kellemora said:**
> Hi Gang

Hate to sound sarcastic, but MOST of my recent questions have gone unanswered here in the beginners forum.  Seems like common things like mounting a hard drive or configuring a hardwired LAN take a backseat to fixing an MP3 player or some speaker squeaks or a game.

Or is it they expect you to KNOW EVERYTHING within two months time?
Or after two months, you are no longer considered a beginner, so nobody answers anymore, other than another noob?

I've tried to be as helpful as I could be on these forums with things I finally figured out that other noob's hadn't yet!
It may not be the right way, but it got the job done and made a few happy campers.

Seems like the reciprocal doesn't exist here anymore!

Did the LTS fall down and go boom from behind 8.04?

I've read thousands of documents over the last two months in trying to learn, many of them are grossly in error, yet end up right here in tips & techniques.

WHAT FORUM AM I SUPPOSED TO USE TO LEARN HOW TO EDIT FSTAB PROPERLY SO A HARD DRIVE CAN BE MOUNTED FROM A COMMAND LINE?????

TTUL
Gary

Hi and is this the post you are speaking of
[http://ubuntuforums.org/showthread.php?t=973644](http://ubuntuforums.org/showthread.php?t=973644)
If so it has been only 10 hrs and the forum has been really busy with the new release of Intrepid and many post go unanswered for some time.

---

### Post by asgard_command on 2008-11-07
I find the forums invaluble.
Most of the most basic issues I can find solutions to with a little google searching. I use the forums if I can't find an answer on my own.

---

### Post by Kellemora on 2008-11-07
Hi KS & OD

I agree that we are all just folks helping other folks!

But it appears that more important matters are shoved aside quite readily lately.  We had a MAJOR problem pop up here earlier in the week and it was responded to by a single noob who SAW the importance of the post and realized the consequences of it not being answered.  By responding it bumped it back to the top.

As far as all the links that have been given, I've already got ALL of them bookmarked and have read them.  Many are way over my head!
Most appear to assume you have a phd in computer science the way they are written!

With the Release of 8.10, they should have DIVIDED the forum, so the appropriate forum could be used for each major release, like they have on other forums for other releases.

8.04 is a stable LTS release, LTS is supposed to mean Long Term Support, NOT no support after a new unstable release comes out.

So my question still remains unanswered, WHICH FORUM should I be using to learn about Mounting secondary drives, the Mount and Umount, WHAT OPTIONS should the fstab have.

After two months, I know how to open fstab and edit the file, but not necessarily what code to use.

I'm probably one of the FEW here that have independent computers to try my learning skills on, so I don't mess up my primary working computers with trying things and messing up my whole system.  It SAVES tons of posts about I messed up, now help me fix it.

I'm here to LEARN, which is why I've read nearly everything and purchased many books as well.

If you ASK how to mount a hard drive in the advanced forums, they tell you to TRY the beginners forum.
If you ask in the beginners forum, Nobody Responds that knows how, or if they do, they send you to a LINK that THEY understand, but a noob don't.

I've read EVERY web site, every man page, and every tip & technique about writing a line of script to mount a 2nd hard drive.  The things they suggest just don't work in Hardy!!!!
Maybe in release 6 or prior.

And now I hear 8.10 don't have a root terminal anymore too.

After nearly two decades of Linux, many common features are still not available.  I know, must not be relevant to others or someone would have written a program to do it.  No money in FREE either.  I understand that!

I may not be a programmer, but I am a manufacturer and have released to the public many formula's and product techniques, and even released 3 patents to the public domain 10 years before their expiration date to promote the industry they were associated with.  I like Open Source and try to put it to daily use in many things, not just Linux.

In any case, thanks for posting the links, it was a gesture in the right direction.

TTUL
Gary

---

### Post by philinux on 2008-11-07
I think you need this.

**pysdm** it's in synaptic.

Graphical Storage Device Manager
PySDM is a PyGTK Storage Device Manager that allows full customization of hard
disk mountpoints whitout manually access to fstab.
It also allows the creation of udev rules for dynamic configuration of storage
devices

If you install it i think from memory it appears in system>admin.

---

### Post by oldos2er on 2008-11-07
"8.04 is a stable LTS release, LTS is supposed to mean Long Term Support, NOT no support after a new unstable release comes out."

 The support referred to there is not what you find here in the forum. It's [http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid) .

 "As far as all the links that have been given, I've already got ALL of them bookmarked and have read them. Many are way over my head!"

 Please post examples of exactly what's over your head--then we can help.

---

### Post by RequinB4 on 2008-11-07
See the links in my signature.

---

### Post by kansasnoob on 2008-11-07
Speaking only for myself, I get here when I can. I answer what I can.

In this case I'm sadly clueless:confused:

---

### Post by NoVista on 2008-11-07
It's marked solved.
Rants        1
Just Asking  0

---

