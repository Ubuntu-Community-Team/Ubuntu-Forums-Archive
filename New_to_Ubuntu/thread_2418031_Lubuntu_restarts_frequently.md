---
title: "Lubuntu restarts frequently"
date: 2019-04-30
forum: New to Ubuntu
---

### Post by diegoatravesar on 2019-04-30
Hello everyone, hopefully you guys will be able to help me figure out what's going on.

In advance, I have some experience with Linux, but pretty much just enough to get myself into trouble, not much more.

I set up a server(Pentium 4, 3Ghz with 2gb RAM and an older GPU) to do a few things for me, mainly host Plex and allow me to stream my digital content to other devices on my network. Since the specs are fairly low, I decided to use Lubuntu which has a nice, tiny memory footprint.
Recently it feels like the server has been doing a lot of unnecessary restarts. I'm not sure if something is causing this intentionally, or if it's crashing, as I'm not sure where to look for crash logs.

The server starts Plex, PyMedusa, Transmission(this one is currently disabled), Teamviewer and Watcher3 on startup, and is also supposed to be autoconnecting to NordVPN on startup as well using their autoconnect feature.

NordVPN doesn't always reconnect on reboot, but that's an issue I'm currently dealing with their support about and should be unrelated to the restarting itself.

I guess my questions are: why is Lubuntu restarting constantly and where can I view my crash logs from?

---

### Post by TheFu on 2019-04-30
/var/log/

That is the main location for all system level logs.

No Unix/Linux system should restart unless you ask it to.  1 day, 50 days, 3 yrs - no restarts unless you've asked it or setup automatic patching.

Running a GUI on a low-end server is a bad idea.

---

### Post by diegoatravesar on 2019-04-30
Alright, I pulled that up, should I be looking in the syslog files then? There are quite a number of logs in there. I'm attaching a picture of all the files so you can see what I mean.

I know, I initially set it up with GUI because that's what I was comfortable with, I could probably manage now with just ssh and command line.
I've also had it suggested to me to use something like tigervnc to set the server up as headless until I need the GUI, however I'm not really sure how to go about doing that.

The server handles things fairly well considering, the second screenshot is the system resources when remoting into the GUI using Teamviewer.

[https://m.imgur.com/tuI3PLu,Z2Ep4wE](https://m.imgur.com/tuI3PLu,Z2Ep4wE)

[IMG]https://m.imgur.com/tuI3PLu[/IMG]
[IMG]https://m.imgur.com/Z2Ep4wE[/IMG]

---

### Post by Autodave on 2019-04-30
I did not read your logs because they are above my pay grade: I wouldn't have an idea of what I was looking at.  However, what you are describing could be a hardware problem.  My first guess (based on everything that you are asking it to do) would be overheating.  Are all cooling fans especially the GPU one, clean and operating properly?  Try running the unit without the side cover on it and you could also put a small desktop fan blowing onto it.

My second thought would be bad and/or overheating RAM sticks.  Again, removing the cover might help.  You could also run the memory checker to see if it comes up with anything.

Lastly, a weak power supply *could* cause this, but that is unlikely.  Usually, a PSU doesn't recover and allow the machine to restart.  It could happen, just not likely.

---

### Post by diegoatravesar on 2019-04-30
I haven't posted any logs as of yet, as I don't know which logs to post. 
That could be possible, but I'm hoping not. I ran all the hardware against PC-Check6.05 before setting it up and it passed all the tests 10 times straight so it shouldn't be bad, unless its does since doing the testing.

It could be over heating, I'll have to try and monitor that, since it's currently not in a space where I can see it on a regular basis.

---

### Post by TheFu on 2019-04-30
> **diegoatravesar said:**
> I haven't posted any logs as of yet, as I don't know which logs to post. 
That could be possible, but I'm hoping not. I ran all the hardware against PC-Check6.05 before setting it up and it passed all the tests 10 times straight so it shouldn't be bad, unless its does since doing the testing.

It could be over heating, I'll have to try and monitor that, since it's currently not in a space where I can see it on a regular basis.

I'm not a fan of image files. 

Nobody wants you to upload log files - usually there is sensitive information inside that shouldn't be posted online anywhere. I won't look at them - that's what I get paid to do - it is called work. We expect you to look through them and google for anything "funny" so you can learn.  "Funny" means lines that have warnings or errors - literally - look for "warn" and "err".  If there are related lines above or below those key characters that ARE related, then those other lines often provide more information about the issue.

If there are a few specific lines need help, assuming you already googled first, post only those lines and say from which file they are.

Hardware issues 99% of the time show up in the log files in some way.

This might make your life easier searching the logs
```
$ sudo egrep -i 'err|warn' /var/log/*g | more 
```

Unix systems have tremendous text file searching and processing built-in.  Learn to use that part of the system.  I'd bet there are at least 50 commands just for handling the smallest things. Sorting, reversing, to upper, to lower, Capitalizing, searching, cutting, parsing, joining, showing the first lines or the last lines in any stream or file ... are all there and have been since the 1970s.  They are highly optimized by now.

If the system is overheating, then there will be messages inside the logs. GPUs and CPUs automatically slow down when they see an overheat. This doesn't crash. It just slows things down.  If some other part of the system overheats, all bets are off.  I've never seen a system overheat in that way.  I have seen capacitors from the 1990s fail. They don't use those types of caps anymore in motherboards.

---

### Post by diegoatravesar on 2019-04-30
I can understand that. I definitely understand not posting any full logs for those reasons. I guess I should have added I am a Mobile Developer by trade, so I am familiar with working through error logs and trying to figure things out. My main issues so far have been finding them, and searching through them from there.

Thank you for posting that code, that has made it easier to at least take an initial look through the logs, I can't imagine having tried to dig through them from start to finish in one go.

The majority of the Err/Warn messages are coming from either TeamViewer, or Plex. I'll take a look around at the related messages and see what I can find.
I'll definitely have to put some time into learning more of the text file searching stuff, because I can see now how useful it really is.

It doesn't look like anything is mentioning any heat related issues so far.

Thank you both for your time and help so far, I really appreciate it!

---

### Post by TheFu on 2019-04-30
A dev who doesn't know about grep?  Not sure I believe it.  BTW, all mobile devices today are based on Unix, so many of these commands should be on iOS and Android systems already. If they aren't, there are GNU tools packages, at least for Android.  Apply hates GNU, so that's a different issue.

---

### Post by diegoatravesar on 2019-04-30
I know, it sounds strange, doesn't it?
We had very little little(read, no) training with Linux itself in school, our main focuses were Java for Android / Desktop, Swift for iOS, PHP for Backends(Not exactly my preference, but meh), and C# for Unity Development. Lots of development in Programming... almost nothing in working with Servers. Even working with PHP, we were essentially limited to an FTP server, and debugging through a web browser. Everything I know I've had to teach myself, and with what little spare time I have, that hasn't been very much. 

I've managed to cross out Plex as an issue, apparently the logs it grabbed for that are normal output. I have a "binary" files stating they are matches as well, so I'm currently working my way through those to see what's showing up.

---

### Post by TheFu on 2019-04-30
"strings" is a useful tool on binary files, sometimes.

Schools can only teach about 5% of what a professional developer needs to know.  Everyone, always, has gaps in their knowledge.  To avoid that, stick with well-reviewed books and work from start to finish on the subject.  I can recommand **UNIX Power Tools**, to get your fu right on text processing in a shell.  Over 90% of command line stuff is the same between Linux and Unix. Also, a $1 used, 20 yr old, book is probably just as good on that stuff as a $55 book published in 2019.

Languages change all the time.  Options for most shell commands change very slowly, and the old options have been retained since the 1980s, mostly.

---

### Post by diegoatravesar on 2019-04-30
Alright, I've installed strings and will have a go at it a little later.

Yeah, school was useful for getting the basics down, but there is definitely a lot I still need to learn. I will have to check out that book, I actually really like working through textbooks. 

At the moment, I'm not seeing anything that looks super serious, but like I said above, I'll give strings a go and see what I come up with. If not, I'll probably wait until the next confirmed crash to see what I can come up with when I have a better timeframe to look at when browsing the logs.

---

### Post by him610 on 2019-04-30
> Everything I know I've had to teach myself
One gets little more than an introduction to anything in school. Some folks never got that introduction in school; many are self-taught. It is what you do afterwards and in which direction you choose that will make you what you will someday become.

---

### Post by diegoatravesar on 2019-05-03
Alright, so I have potentially good news, as well as some less so good news.

After some digging, I believe the issue was TeamViewer. I'm still not really sure why, but it seems to be the most consistent thing in / around my crashes so I went in and disabled it.  Since then, the server seems content to run without crashing much more smoothly.

As I haven't had time to look into tigervnc or an equivalent, I decided to go the route of disabling both lighten and TeamViewer when I'm not needing a GUI, with the intent to start both back up temporarily as needed.

I've now discovered that disabling lighten was not such a good idea. I was able to disable it, but when I try to run
```
sudo systemctl enable lightdm.service
```
I get the following message.
```
Synchronizing state of lightdm.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable lightdm
The unit files have no installation config (WantedBy, RequiredBy, Also, Alias
settings in the [Install] section, and DefaultInstance for template units).
This means they are not meant to be enabled using systemctl.
Possible reasons for having this kind of units are:
1) A unit may be statically enabled by being symlinked from another unit's
   .wants/ or .requires/ directory.
2) A unit's purpose may be to act as a helper for some other unit which has
   a requirement dependency on it.
3) A unit may be started when needed via activation (socket, path, timer,
   D-Bus, udev, scripted systemctl call, ...).
4) In case of template units, the unit is meant to be enabled with some
   instance name specified.

```

This looks to me like it's failing to enable it. I am also unable to get TeamViewer restarted, following the guide on [http://www.tonisoto.com/2013/07/launching-teamviewer-remotely-throught-ssh/]("http://www.tonisoto.com/2013/07/launching-teamviewer-remotely-throught-ssh/"). Specifically, the command
```
TeamViewer start teamviewer
``` gives me the following:
```
Init...
xprop:  unable to open display ''
CheckCPU: SSE2 support: yes
Checking setup...
Launching TeamViewer ...
Launching TeamViewer GUI ...

bash: [2443: 1 (255)] tcsetattr: Inappropriate ioctl for device
```

So it appears that I've resolved my original issue, only to create a new one for myself. At this point, i assume I should probably create a new thread as the issue in question is no longer the same.

---

