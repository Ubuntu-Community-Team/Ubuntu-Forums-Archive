---
title: "Please help...Need Laymens terms"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by ~MK~ on 2008-06-25
Hey there:

I'm new to Ubuntu, I've only been using it for the net and listening to music. I can't stand Microsoft because I have even more problems with it than Ubuntu.

I need help with my MP3 player, but I don't just need instructions. Every time I read a post about how to solve my problem it gives me a bunch of jargon that I cannot understand, and if I can't understand it I cannot use it to solve my problem.

All I would like is for someone to please explain to me, or help me use my Samsung U3 2gb Mp3 player. As much as I enjoy reading the posts I do not understand things like "type .... in root file...etc. etc. I just don't understand at this point. If someone could please give me step by step instructions, a link or anything that shows me how to get my MP3 player to work (in some form of english) that would be greatly appreciated. It seems like everyone on here is seasoned with computers in general, so figuring this stuff out is easy for them.

I think that's great! And hopefully I'll learn too, but I'm starting to cry and lose my faith in Ubuntu. It just seems like everything is so difficult.


Thanks for any help!!!

~Meghan~

---

### Post by JoshuaRL on 2008-06-25
Hi Meghan, and sorry you're having problems.  Have you found any other threads that have fixed the problem for other users?  If so, we can guide you through it step by step.

And don't worry about making mistakes or not understanding.  Everyone starts somewhere, and we're all here to help.

And welcome to Ubuntu!

- Josh

---

### Post by unutbu on 2008-06-25
I'm adapting the solution provided at [http://lobzang.free.fr/tip005.html](http://lobzang.free.fr/tip005.html)
for Ubuntu:

Open up a terminal (To do this, see [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)).
Run the command

```
sudo apt-get install libmtp6 gnomad2
```
You will be asked for your password. 

You don't need to change udev rules because Ubuntu has this set for you already. 

So now just plug in the mp3 player, and launch gnomad2. (Click on the gnome panel menu bar item Applications>Sound & Video>gnomad2. I'm guessing this is where it will be, if it isn't there, look around in the menu. If you can't find it, post and we'll give you instructions on how to create a menu item for it.)

---

### Post by ~MK~ on 2008-06-25
Hey guys: 

Thanks for the reply.

Josh here is a link to about 4 posts with something to do with my MP3 player:

[http://ubuntuforums.org/archive/index.php/t-540577.html]("http://ubuntuforums.org/archive/index.php/t-540577.html")
 
Does this help?

I will try to do what Unutbu just posted, but I don't have gnomad2, I only have rythmbox and I tried downloading gnomad2 half an hour ago and it wouldn't work.

I'll let you know what happens.

Thanks GUYS!!!

---

### Post by Bradtek on 2008-06-25
> **~MK~ said:**
> 
I do not understand things like "type .... in root file...etc. etc. I just don't understand at this point.


90% of the time understanding what people suggest you try is optional.
If someone suggests "type this into a terminal and post the output here"
generally the only understanding that is required knowing how to copy and paste.

I am pretty new to Linux and understand very little about how it works,
but with alot of copy/paste from this forum I have Ubuntu running pretty much the way I want it to.

Once a problem is solved then you will have plenty of time to study how & why

---

### Post by Dr Small on 2008-06-25
> **Bradtek said:**
> 90% of the time understanding what people suggest you try is optional.
If someone suggests "type this into a terminal and post the output here"
generally the only understanding that is required knowing how to copy and paste.

I am pretty new to Linux and understand very little about how it works,
but with alot of copy/paste from this forum I have Ubuntu running pretty much the way I want it to.

Once a problem is solved then you will have plenty of time to study how & why
That's right. We generally put things in code tags and tell you to run the command and give us back the output, as it is usually crucial to solving your problems.

Copy and Pasting isn't that hard, but you should try to understand the command, so you can learn to solve problems on your own, and know what commands NOT to run ;)

---

### Post by ~MK~ on 2008-06-25
Unutbu:

The terminal says: Couldn't find package libmtp6

What does this mean?
Please help

Thanks,
~Meghan~

---

### Post by Bradtek on 2008-06-25
> **~MK~ said:**
> Unutbu:

The terminal says: Couldn't find package libmtp6

What does this mean?
Please help

Thanks,
~Meghan~

I am running Ubuntu 8.04 and there is no libmtp6 
in synaptic but there is libmtp7

---

### Post by ~MK~ on 2008-06-25
> **Dr Small said:**
> That's right. We generally put things in code tags and tell you to run the command and give us back the output, as it is usually crucial to solving your problems.

Copy and Pasting isn't that hard, but you should try to understand the command, so you can learn to solve problems on your own, and know what commands NOT to run ;)

I think you guys misunderstood what I was trying to say. I understand the concept of copy and pasting, and I'm not trying to understand what all the jargon means at the moment. I was merely trying to understand what the jargon meant for me to do. All the posts I found about solving my MP3 problems were filled with steps I did not understand. If my problem was just a matter of copy and pasting in the terminal than I wouldn't be as flustered as I am right now.

I'm sorry, but for me reading posts was not helping.

So I came here.

Thanks,
~Meghan~

---

### Post by ~MK~ on 2008-06-25
> **Bradtek said:**
> I am running Ubuntu 8.04 and there is no libmtp6 
in synaptic but there is libmtp7

I think it's because I'm running Ubuntu 7.04.

Thanks,
~Meghan~

---

### Post by unutbu on 2008-06-25
Sorry, I should have asked which version of Ubuntu you are running.

Feisty has libmtp5 and gnomad2 according to [http://packages.ubuntu.com/feisty/libmtp5](http://packages.ubuntu.com/feisty/libmtp5),
[http://packages.ubuntu.com/feisty/gnomad2](http://packages.ubuntu.com/feisty/gnomad2)
so the command should be

```
sudo apt-get install libmtp5 gnomad2
```

---

### Post by Bradtek on 2008-06-25
It may be helpful to say specifically  what you don't understand 
with reference to the steps.
eg.
Someone suggested I do "this" but I don't understand how to do this.

Otherwise you could possibly end up with more steps (or just more of the same ones) you don't understand.

---

### Post by ~MK~ on 2008-06-25
Unutbu:

I think it installed Gnomad2, but when I click on it to open it says: 

**No jukeboxes found on USB bus**

When I try to transfer music files over to the jukebox it closes. My MP3 player is still not recognized.

Is there something I'm doing wrong?

Thanks for all your help so far, it seems to be working.

~Meghan~

---

### Post by unutbu on 2008-06-25
Please run 

```
lsusb
``` with the mp3 player plugged in.

---

### Post by ~MK~ on 2008-06-25
Ok, I did just that, now what is supposed to happen?

When I open up Gnomad 2 it still does the same thing.

Thanks,
~Meghan~

---

### Post by unutbu on 2008-06-25
Please post the output to

```
lsusb
```

:lolflag: (sorry-- my bad)

---

### Post by ~MK~ on 2008-06-25
What does the "output" mean?

I can't even tell if something is "your bad" because I don't know what you're doing, but if you say it is I'll believe you! Your emoticon was very funny in the post too!

Thanks,
~Meghan~

---

### Post by Dr Small on 2008-06-25
"Post the output" means, in layman terms, that whatever command he just gave you, run it, and post the output (what is shown on the screen, in the terminal) to a new post, in this thread.

---

### Post by unutbu on 2008-06-25
When I type 

```
lsusb
```

My terminal responds with
```
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 413c:2003 Dell Computer Corp.  (my keyboard)
Bus 002 Device 002: ID 0461:4d15 Primax Electronics, Ltd   (my mouse)
Bus 002 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 07d1:3a08 D-Link System   (my wireless adapter)
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

```
It gives us some information about what devices are connected to the machine via its USB ports. Hopefully, when you run lsusb, you will get some output which indicates that your machine recognizes that the mp3 player is connected to it.

---

### Post by ~MK~ on 2008-06-25
mk@mk-desktop:~$ lsusb
Bus 004 Device 003: ID 04e8:507d Samsung Electronics Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
mk@mk-desktop:~$ 


LOL...Thanks you two! So the above is what my output was.

Thanks for the clarification!
~Meghan~

---

### Post by unutbu on 2008-06-25
What happens when you type

```
gksudo gnomad2
```

---

### Post by ~MK~ on 2008-06-25
Autodetected device with VID=04e8 and PID=507d is UNKNOWN.
Please report this VID/PID and the device model name etc to the
libmtp development team!
Connected to MTP device.
Queried Samsung YP-U3

ANd then: Gnomad popped up and in the "jukebox Library" window it says:

Samsung Music Space
Samsung Rising Sun

But I still don't know where to go from there.

---

### Post by unutbu on 2008-06-25
Hm. It sounds like gnomad2 is now running, but it's not clear how to transfer files to and from the mp3 player? Is that right?

If so, I'm sorry but I think I've taken you as far as I know how to go. I don't have an mp3 player and have never used gnomad2. Maybe someone who has some experience can give you some advice?

---

### Post by ~MK~ on 2008-06-25
I think that's about right, but no worries I shall sleep on it.

Honestly you've helped me so much, I didn't even cry once!
I shall go to bed, and try again tomorrow after my computer has restarted. For someone who doesn't own an MP3 player, or have Gnomad2 you sure knew a lot.

Thanks again for all your help, and also thanks to everyone else in the previous posts for all your help, I have gotten farther and less frustrated with these last posts than I have ever.

~Meghan~

---

### Post by JoshuaRL on 2008-06-25
> **~MK~ said:**
> I think that's about right, but no worries I shall sleep on it.

Honestly you've helped me so much, I didn't even cry once!
I shall go to bed, and try again tomorrow after my computer has restarted. For someone who doesn't own an MP3 player, or have Gnomad2 you sure knew a lot.

Thanks again for all your help, and also thanks to everyone else in the previous posts for all your help, I have gotten farther and less frustrated with these last posts than I have ever.

~Meghan~

Maybe it's just because you're running Feisty.  Maybe your device hadn't been released then.  Or maybe those older versions of those libraries didn't have support for your device yet.  Have you considered upgrading to either Gutsy or Hardy?  That might solve your problem.

---

### Post by ~MK~ on 2008-06-26
I will greatly consider upgrading to Gutsy or Hardy, but I don't know how. Could you please tell where/how I would go about doing that?

Also would I lose my files on my version now if I upgraded?

Thanks,
Meghan

---

### Post by JoshuaRL on 2008-06-26
No, you would if you reinstalled the newer versions, but upgrades should keep everything.  If you want to, just put this into the terminal:
```

update manager -d

```
That should let you update through the Update Manager.

---

### Post by fidamehran on 2008-06-26
> **~MK~ said:**
> I think you guys misunderstood what I was trying to say. I understand the concept of copy and pasting, and I'm not trying to understand what all the jargon means at the moment. I was merely trying to understand what the jargon meant for me to do. All the posts I found about solving my MP3 problems were filled with steps I did not understand. If my problem was just a matter of copy and pasting in the terminal than I wouldn't be as flustered as I am right now.

I'm sorry, but for me reading posts was not helping.

So I came here.

Thanks,
~Meghan~
You will know the meaning of the jargons soon enough. I am only a few days old at the forum and I did some commands by myself. For example, cp=copy, cd=what you type to get into a directory (like DOS). etc etc
Anyway, you'll soon learn 2-3 commands. Others you can learn as you go on solving problems with the forum people.

---

### Post by rburkartjo on 2008-06-26
mk try this it is to do and might work. got to applications at let top then click add/remove. in search box that will appear at top type in gnomad2. install it will be installed under sound & videos. then open gnomad2 see if this will work it did with my daughter creative mp3 player. 
it imported all her songs no problem. let me know if this helped/cheesemaker

---

### Post by ~MK~ on 2008-06-26
> **JoshuaRL said:**
> No, you would if you reinstalled the newer versions, but upgrades should keep everything.  If you want to, just put this into the terminal:
```

update manager -d

```
That should let you update through the Update Manager.

This didn't work, it said command not recognised.

Any other ideas?

Thanks,
Meghan

---

### Post by ~MK~ on 2008-06-26
> **rburkartjo said:**
> mk try this it is to do and might work. got to applications at let top then click add/remove. in search box that will appear at top type in gnomad2. install it will be installed under sound & videos. then open gnomad2 see if this will work it did with my daughter creative mp3 player. 
it imported all her songs no problem. let me know if this helped/cheesemaker

I tried this, but it didn't work either. Any other ideas?

Thanks,
~Meghan~

---

### Post by JoshuaRL on 2008-06-27
> **~MK~ said:**
> This didn't work, it said command not recognised.

Any other ideas?

Thanks,
Meghan

Man, I'm so stupid sometimes.
```

gksu update-manager -d

```

Sorry.

---

### Post by unutbu on 2008-06-27
On the principal "Look before you leap", wouldn't it be safer to install Heron in a separate partition? If there is no space available for a separate partition, I simply wouldn't upgrade until I could purchase a second hard drive. If there are any hardware problems the OP would be stuck without an easy way to revert.

I might be wrong, especially since I don't know how gnomad2 works, but it was my impression that the OP has already got gnomad2 working, and just needs instructions on how to use it.

---

### Post by ~MK~ on 2008-06-28
> **JoshuaRL said:**
> Man, I'm so stupid sometimes.
```

gksu update-manager -d

```

Sorry.


HA ha, that's ok. So I installed it, but it still doesn't detect my player and gnomad 2 does the same thing when I open it: I cannot transfer files onto the player.

However Rhythmbox popped up when I plugged it in, but it didn't do anything.

So I'm not sure what to do, because the back of the box on this player says it plays "ogg" files.

Here is a link to a thread of other people getting it to work, but I cannot understand what they mean by these steps.

[http://ubuntuforums.org/archive/index.php/t-540577.html](http://ubuntuforums.org/archive/index.php/t-540577.html)

Thanks,
Meghan

---

