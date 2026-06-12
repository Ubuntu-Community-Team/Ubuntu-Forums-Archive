---
title: "Can Ruby on Rails installed on Ubuntu Touch?"
date: 2013-11-04
forum: Programming Talk
---

### Post by hanfe-strife on 2013-11-04
The thing is, I not yet having a tablet with Ubuntu Touch inside it. But I always wondered if I have one, can I install Ruby on Rails that using RVM on that Ubuntu Touch?

Is there anyone done trying this one? Or perhaps I should install just Ubuntu on my (soon) tablet?

Thank you so much.

---

### Post by TheFu on 2013-11-04
106 viewers and no answer, so I thought I would drop a comment ... not an answer.

It all comes down to dependencies, right?  It will mainly be about having the tools ported to ARM. Most common things have been ported - gcc, g++, libc .... it would be the native code in ruby gems that would concern me the most.

Would you consider another alternative that solves this and many other problems?  Remote desktop/remote shell.   There are many remote desktop tools ... and I would believe these would be worked on first - vnc especially.

I have run a version of Ubuntu w/ Backtrack under my 10 ARM tablet.  Had to use a VNC-server running under ARM to access it from Android on the same machine. It was a chroot setup.  In theory, the most popular stuff worked, but a keyboard and touch interface translation issue made it completely unusable for me.  Pressing -m- on my keyboard always pulled up an email client. That was about a year ago. I should try again.  Running RoR on that platform wouldnt be too bad, though it would be slow - after all, Rails it a hog compared to other options and if you use continuous testing methods, it will be hard to have a great development environment on any ARM system.

Interesting question regardless.  Now I am curious too.  You have probably already seen this: [http://stackoverflow.com/questions/4033337/ruby-on-rails-performance-on-arm](http://stackoverflow.com/questions/4033337/ruby-on-rails-performance-on-arm)

---

