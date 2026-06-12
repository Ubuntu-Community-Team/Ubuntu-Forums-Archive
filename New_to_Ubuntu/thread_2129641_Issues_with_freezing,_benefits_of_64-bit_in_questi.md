---
title: "Issues with freezing, benefits of 64-bit in question (ubuntu 12.10/cinnamon)"
date: 2013-03-26
forum: New to Ubuntu
---

### Post by jonnymopar on 2013-03-26
Hi all,

I'm newly registered here, but I've been lurking around getting advice from this board for a little while.

I'm currently using an HP NC8430 notebook with a Core2 Duo 2.0GHz and 3GB RAM.  I started off with Mint 14 64-bit KDE, and had issues with it freezing periodically (couldn't even get to the terminal).  I then decided to try Mint 13 64-bit Cinnamon and I had less issues with it, but still had the freezing issue once in a while.

Then I decided to go for it and learn Linux the hard way: I started with a minimal install of Ubuntu 12.10, then added Cinnamon 1.6.7 manually.  My issues with freezing up are ALMOST completely gone (one freeze up per week versus once per couple of hours when I started) and the computer is running faster than I've ever seen it.  Still, I'd like to get rid of this issue once and for all.

This computer maxes out at 4GB RAM, which I'm not even at that level.  Is there any benefit to sticking with the 64-bit Ubuntu on a computer like this?  I'm just not sure what else to try, other than maybe going to a 32-bit operating system.  Right now, I only use the computer for Firefox, Wine, DOSBox, LibreOffice Writer and Calc, and Spotify.  It's relatively lightly used.  When I was having issues with the aforementioned versions of Mint, I was really only using Firefox, since I was still getting used to Linux overall (which is why I went with Mint in the first place).

Also, before you say that it might be the laptop itself causing the problem, I ran Windows 7 64-bit for over a year with no issues and I also ran the 64-bit Windows 8 Consumer Preview for nearly 5 months and also had no issues there.

---

### Post by Impavidus on 2013-03-27
In principle, 64 bit is slightly faster. On how large the difference is opinions vary. 64 bit also allows you to use more than 3GB RAM more effectively (without PAE), but also uses more memory for the same tasks. Between 1GB and 3GB there is a kind of grey area, where it doesn't matter much whether you have 32 or 64 bit. If the computer is only lightly used it doesn't matter at all. I don't know whether switching to 32 bit will solve your problem, but you could try.

---

### Post by jonnymopar on 2013-03-27
Thanks you for the reply.  Your comment about the "grey area" is a large part of why I'm asking the question.  I may try 32-bit and see where I get.  I saw some posts on the Mint forums about the switch to 32-bit solving some issues, but I'm not using Mint anymore.

Side note: after using Windows 8 :mad:, I can't wait to get further into Linux.  To my amazement, with every distro that I've tried on this particular computer, I didn't have to mess with a single driver to get everything to work.

---

### Post by moody_mark on 2013-03-27
Hi, I dont think its the OS itself thats giving you problems, its likely an application. The reason I say this is that I had similar issues when I first started using Ubuntu on my Dell E6400 back in late 2008. I narrowed it down to a java application that seemed to make the X server spin up using up to 80% CPU. If I avoided the application things were ok. I've been using Ubuntu 10.04 on this machine now for over 4 years, and one thing I can tell you is its just as fast now as when I first installed it, even with all the extra packages I've added over the years.

So, heres a few pointers, I'm not sure how much of this you might have tried, so please excuse me if I'm telling you to do stuff you have already tried;

- When the "freeze" happens, try CTRL+ALT+F1 to break out to a console, run "top" to see if you see whats eating up resources
- If you get a console session ok then see if you can kill off a few processes, even if you have to kill the X server, and then run up the desktop again
- If you can't get any keyboard response, then try logging in remotely via ssh from another machine on your home network (assuming you have openssh installed and access to another machine?)
- If the machine seems to just lockup completely (i.e. no keyboard, pressing caps lock doesnt even bring the caps lock light on), try doing some things like using the "disk utility" to check the disc make sure there are no disk errors.
- do you have any errors in the /var/log/* log files there, usuall messages, syslog or kern.log
- you could write a cron job to trigger a one-shot output of "top" to a file every 5 mins, so if the crash happens you might get a view of the offending application
- try running the machine from another window manager, perhaps installing LXDE and see if it happens on there too?

Most importantly, dont give up! If you keep on keeping on, then you'll crack it in the end :-)

btw... do you have an interest in mopar cars or is your username just co-incidence?

---

### Post by jonnymopar on 2013-03-27
Thanks for the pointers!  I actually didn't know about CTRL+ALT+F1.  I've been trying it with F6 to get to the terminal.  It's interesting that you say it might be an application, because the last time it happened, I was on a website that was heavy on Flash and uses Java as well.

I looked through syslog, syslog.1, kern.log, and kern.log.1.  Honestly I don't even really know what I'd be looking for as far as errors.

I'm unfamiliar with "cron job", so I'll have to do some research on that one.

As for my username, it's no coincidence. :D I have two Mopars right now: one extremely reliable high-mileage daily driver, and one classic nice weather toy that I just about doubled the horsepower in, plus converted it from automatic to 5-speed. My username is a nickname that I've had for years.

---

### Post by moody_mark on 2013-03-28
> **jonnymopar said:**
> Thanks for the pointers!  I actually didn't know about CTRL+ALT+F1.

Theres actually 6 consoles you can use from CTRL+ALT+F1 through to CTRL+ATL+F6 basically the linux desktop is just another process on top of the actual operating system so you can drop out to the command line shell and stop / start the desktop, or window manager etc.

> It's interesting that you say it might be an application, because the last time it happened, I was on a website that was heavy on Flash and uses Java as well.

Yes the flash plugin is a culprit sometimes, Ive seen some flash based sites eat up all the memory on a small under powered machine. You machine sounds like its got some decent CPU horsepower (pardon the car-related pun there), and as long as you have minimum 512MB RAM you should be ok on most flash sites. I would though strongly advise using the "noscript" plugin in firefox, its a great security tool and I've used it for years, it may even help with your problem as it could be a script within another site causing the issue. Have you tried google chrome or any other browsers?

> I looked through syslog, syslog.1, kern.log, and kern.log.1.  Honestly I don't even really know what I'd be looking for as far as errors.

The logs are generally good but its true the problems arent always obvious. Im far from a sysadmin and been using Linux on my daily work machine since 2008 now but I still dont understand everything in those logs. You'll get a lot of help on here on on the IRC channels.

>  I'm unfamiliar with "cron job", so I'll have to do some research on that one.

cron is basically a process where you can trigger things on a regular basis, its the equivalent of the windows task scheduler to give you a parallel, have a look here for some info: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

>  As for my username, it's no coincidence. :D I have two Mopars right now: one extremely reliable high-mileage daily driver, and one classic nice weather toy that I just about doubled the horsepower in, plus converted it from automatic to 5-speed. My username is a nickname that I've had for years.

You're a lucky guy, that's a great combination, a daily driver AND a nice weather one. I used to own a 1973 Charger with a small block 316ci I think it was, unfortunately with the weather here in the UK if you dont have a dry garage the bodywork will suffer, so I sold it onto someone who could give it a good home. I like all sorts of cars but I have a soft spot for the 60s and 70s era American cars, especially some of mopar stable. The prices are high nowdays, a good condition 1969 Charger 440 R/T could fetch anything around £30,000 possibly more depending on the paperwork etc. Lovely cars but petrol is so expensive nowdays too.

If you need any more help, feel free to pm me.

Some more links:

some great tips here, used this site a lot when I first got started --> [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)
terminal how tos --> [https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto) and [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
just found this, looks quite comprehensive --> [http://ubuntuguide.org/wiki/Ubuntu_Quantal](http://ubuntuguide.org/wiki/Ubuntu_Quantal)

Cheers! -Mark

---

### Post by jonnymopar on 2013-03-28
Thank you for the links. I'm trying to learn all that I can.

> **moody_mark said:**
> Theres actually 6 consoles you can use from CTRL+ALT+F1 through to CTRL+ATL+F6 basically the linux desktop is just another process on top of the actual operating system so you can drop out to the command line shell and stop / start the desktop, or window manager etc. 

I was playing around with that last night (unfortunately trying to recover from a partial freeze-up). Pardon the Microsoft comparison, but it's like having 6 separate DOS prompts available at all times. I noticed also (at least with Cinnamon), that CTRL+ALT+F7 brings you back to the desktop. After the computer stopped responding last night, I was able to access all of those consoles at any time, but I couldn't get past the user login prompt. I could enter my user name, but pressing enter would just put a carriage return and nothing else would happen after that. You could carriage return down the entire page and it would never ask for a password.

> **moody_mark said:**
> Yes the flash plugin is a culprit sometimes, Ive seen some flash based sites eat up all the memory on a small under powered machine. You machine sounds like its got some decent CPU horsepower (pardon the car-related pun there), and as long as you have minimum 512MB RAM you should be ok on most flash sites. I would though strongly advise using the "noscript" plugin in firefox, its a great security tool and I've used it for years, it may even help with your problem as it could be a script within another site causing the issue. Have you tried google chrome or any other browsers?

I haven't tried anything other than Firefox with this particular installation. It installed with Cinnamon, so I've stuck with it for now. With the other distros that I previously mentioned, I was using Opera. I briefly tried Chromium and had no problems with it, but it was only for a short amount of time in Mint 13 before I wiped the machine clean and manually installed everything as it is now.

> **moody_mark said:**
> ...cars...

I'm a big fan of the 60's/70's era Mopars as well, but my personal preference is **puts on flame suit** 80's turbo Mopars. What can I say? My summer car is 24 years old, now has well over 260hp, and on long highway trips will get 32-34 miles per gallon. Sure, that kind of fuel mileage at those horsepower levels are possible with new cars too, but you won't find T-tops on anything recent :cool:.

---

### Post by moody_mark on 2013-04-03
> **jonnymopar said:**
> T...After the computer stopped responding last night, I was able to access all of those consoles at any time, but I couldn't get past the user login prompt. I could enter my user name, but pressing enter would just put a carriage return and nothing else would happen after that. You could carriage return down the entire page and it would never ask for a password....

Ok, correct so the F7 usually does return you to the desktop, the X session runs on one of the "tty" consoles usually tty7. Now if its not giving you a login, how long did you give it? If its asked you for a username then it should come back, if something is eating up the CPU or Memory then it might take a while to get a login. Give it about 5 mins tops.

If it doesn't come back you can reboot the machine using the ALT+SYSREQ keys and pressing R E I S U B keys in slow succession about 1 second apart. You'll need to do a bit of finger stretching but it makes sure the machine shutsdown cleanly.

> I haven't tried anything other than Firefox with this particular installation. It installed with Cinnamon, so I've stuck with it for now. With the other distros that I previously mentioned, I was using Opera. I briefly tried Chromium and had no problems with it, but it was only for a short amount of time in Mint 13 before I wiped the machine clean and manually installed everything as it is now. 

You can install other browsers, you dont just have to use firefox, try adding the "noscript" plugin to firefox and see if that helps, as I said it might be a script on a page on one of your favourite sites thats causing the problem. You should be able to install opera too, I dont think its in the repositories but it might be. I've got Firefox, Chromium, Chrome, Midori and Opera installed on my work machine. Its very useful to have multiple browsers if you get a problem with a site to verify against.


> 
I'm a big fan of the 60's/70's era Mopars as well, but my personal preference is **puts on flame suit** 80's turbo Mopars. What can I say? My summer car is 24 years old, now has well over 260hp, and on long highway trips will get 32-34 miles per gallon. Sure, that kind of fuel mileage at those horsepower levels are possible with new cars too, but you won't find T-tops on anything recent :cool:.

Yeah some of the 80s cars are nice too, t-tops are very "knight rider" brings back some great memories from when I was a kid. That good HP for that MPG, you probably would get that out of today's cars with a smaller capacity engine but you'd have to look at something pretty top-end like a BMW M-series and that will cost you $$$ or £££ :-)

---

### Post by stig on 2013-04-03
jonnymopar, in case it's a related problem have a look at this thread (but ignore the title):
[http://ubuntuforums.org/showthread.php?t=2128691](http://ubuntuforums.org/showthread.php?t=2128691)

---

### Post by jonnymopar on 2013-05-18
Ok, let's revisit this.  Same exact computer, now has 12.04 32-bit.  Same basic problem: random freezing.

The desktop, other than the mouse cursor, is completely unresponsive.  I was able to CTRL-ALT-F1 into a terminal.  After typing in my user name and pressing Enter, same as before, no other response, so I left it and walked away.  When I came back about half an hour later, it had the following two messages repeated many times:
[B]
INFO: task kworker/0:0:6301 block for more than 120 seconds.
"echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[/B]
Any idea what this might mean?  I left it for another half hour and it kept doing the same thing, so I had to hard shut down.  I'm sure the second line is just explanatory, but what about the first one?  Also, it never did ask me for my password.

---

