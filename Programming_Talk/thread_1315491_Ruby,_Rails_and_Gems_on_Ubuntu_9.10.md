---
title: "Ruby, Rails and Gems on Ubuntu 9.10"
date: 2009-11-05
forum: Programming Talk
---

### Post by Unknown-Master on 2009-11-05
I have just installed a fresh copy of ubuntu 9.04 and then upgraded it to 9.10

I then proceeded to install ruby-full ( 1.8.7), ruby gems(1.3.5). I then installed using gem, rails (2.3.4), his however did not work as expected. I can not use the rails command from the shell.

So I then saw that I could sudo aptitude install rails and in doing so could use the rails command. I was satisfied till I noticed that the version was 2.2.3. How would I upgrade this to 2.3.4

My other question is: Why are the gem packages now having to be installed through aptitude/apt-get to be used ? I can't use the rake command either (I have installed rake with gem). I think that ruby gems should be managing its packages instead of aptitude or apt-get or am I doing something wrong here :(

Thanks guys

---

### Post by crush304 on 2009-11-05
if you install rails with gem and you want to run rails from the command line, you have to add the gem directory to the path 

you can add the following to your ~/.bashrc file

#Export the path for Ruby Gems
export PATH=$PATH:/var/lib/gems/1.8/bin

you'll need to verify i listed the correct directory for karmic

---

### Post by Unknown-Master on 2009-11-05
Thanks, working 100's now :D
+ + +

---

