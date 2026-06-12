---
title: "Do not unpack or run TBB as root."
date: 2013-06-21
forum: New to Ubuntu
---

### Post by jfbooth on 2013-06-21
I was carefully following some steps in a Tor installation tutorial.  Everything was going fine until (per instructions) I ran the application which erred with:

```
~/Desktop/tor-browser_en-US $ ./start-tor-browser

Launching Tor Browser Bundle for Linux in /home/Desktop/tor-browser_en-US
./App/vidalia: 1: ./App/vidalia: ELF&#65533;: not found
./App/vidalia: 2: ./App/vidalia: Syntax error: "(" unexpected
Vidalia exited abnormally.  Exit code: 2
```

Reading the next and last instruction, it says:

> Do not unpack or run TBB as root.

Well, I am pretty sure I did ..... both.  What have I messed up and how do I fix it so I can start over and do it right this time?  

Thank you in advance.

---

### Post by Frogs Hair on 2013-06-21
You may want to post a link to the tutorial . While testing Tor I extracted the package in a directory of my choice , opened the folder and double clicked the  start-tor-browser script, but did not use the terminal.

---

### Post by jfbooth on 2013-06-21
> **Frogs Hair said:**
> You may want to post a link to the tutorial . While testing Tor I extracted the package in a directory of my choice , opened the folder and double clicked the  start-tor-browser script, but did not use the terminal.


Thank you for the reply.


No evidence of how to contact 'tutorial' ... and though I may not have made it clear, the problem is more 'what to do about unpacking a file as root' than the tutorial failure.  

Trust me, I will get more help from here than from the tutorial site  ... I hope.

---

### Post by Paqman on 2013-06-21
> **jfbooth said:**
> 
Well, I am pretty sure I did ..... both. 

The only way you would have done this is if you were running as root in a terminal window, or otherwise unpacked and ran it using the "sudo" prefix. If you just clicked on the package to unpack it, then clicked on the start-tor-browser file then you didn't run it as root.

The TOR bundle is pretty straightforward to use. Download, unpack, click and you're done. If it's failed then I'd suggest making sure you've downloaded the right version (eg: 32 or 64 bit and that it's the one for Linux), delete it and and try downloading it again. You may just have got a bad download.

---

### Post by QIII on 2013-06-21
Hello!

The reason Frog's Hair asked for the link to the tutorial is so that it may be reviewed to see what you have done.

It is much easier to help when we know how you got where you are.

Cheers!

---

### Post by jfbooth on 2013-06-21
> **Paqman said:**
> The only way you would have done this is if you were running as root in a terminal window, or otherwise unpacked and ran it using the "sudo" prefix. If you just clicked on the package to unpack it, then clicked on the start-tor-browser file then you didn't run it as root.

The TOR bundle is pretty straightforward to use. Download, unpack, click and you're done. If it's failed then I'd suggest making sure you've downloaded the right version (eg: 32 or 64 bit and that it's the one for Linux), delete it and and try downloading it again. You may just have got a bad download.

I did unpack it as root .. I am 99% certain.  I am 98% sure I ran it as root.  The issue is not Tor or its error.  I simply want to know what the negative result of unpacking and running anything as root ... because I believe I did and need to undo any damage that was done.

This is more of a Linux question than a Tor question.

Here is a link to the tutorial ... I misread the request for it:

[http://www.instructables.com/id/Raspberry-Pi-Tor-relay/](http://www.instructables.com/id/Raspberry-Pi-Tor-relay/)

---

### Post by Paqman on 2013-06-22
Unpacking an archive as root shouldn't cause any irreparable damage, although it might result in your files being unpacked to a funny location such as /root instead of your home folder. It may also cause permissions problems, as the files would not have been created by the user that was going to use them. 

Executing an application as root is however potentially very dangerous. It would prevent that application from being controlled by the permissions system, and in the case of an application that connects to the internet it could allow an attacker to exploit a bug in that application and gain access to any part of the system. In short, you'd blow away all your security, it'd be like painting a bullseye on your forehead while waving a big sign saying "PWN ME!!".

Generally speaking you want to run as little as possible as root, if something doesn't *need* to run as root, it shouldn't.

If you unpacked the archive as root, simply delete it (you'll need to use sudo) and re-extract it as a normal user.

---

### Post by jfbooth on 2013-06-22
> Unpacking an archive as root shouldn't cause any irreparable damage, although ....

There we go.  THANK YOU ..... now I understand the repurcussions of what i did ... and learned something too.  I uninstalled TBB and deleted the folder I unpacked to.  All is well, ...evidently.  I really appreciate your comments and help.

---

### Post by Paqman on 2013-06-23
I'm more concerned about why you were so sure you did it as root in the first place. Why were you doing this kind of thing as root? Were you running in a root shell, or did you just use sudo on the command line? Stick to normal GUI ways of doing stuff like this in future and it'll be less risky.

---

### Post by newb85 on 2013-06-23
> **Paqman said:**
> Stick to normal GUI ways of doing stuff like this in future and it'll be less risky.

Whilst this advice may not be wrong *per se*, I would avoid discouraging people from learning to use the terminal instead of "normal GUI".  But that's just me.  It's not bad for people who want to learn to use the CLI to do it for everyday tasks in order to become more comfortable and familiar with it.  My version of that advice would be, "Be conscientious about what commands you issue as root (or with sudo) in the future, and it'll be less risky."

But I do second the rest of what Paqman said.  Provided Tor's developers didn't create a security vulnerability that has already been exploited, there isn't any irreparable damage.  Unpacking as root means the files unpacked will be owned as root, instead of the normal user.  Running as root means the application could do literally anything to your system.  (Of course, in theory someone could write an application with malicious intent so that if you run it as root it automatically trashes your system.  Given that the Tor devs specifically told you *not* to unpack or run as root, I doubt that's the case.)

In addition to the aforementioned advice, I would also suggest that, whenever possible, you stick to using software from the repositories and PPAs you know you can trust.  In the repositories, the software will not have malicious intent, security vulnerabilities are corrected when they are found, and bug fixes are sometimes issued.  In a PPA from a source you trust, you should enjoy the same benefits (though the reviews probably won't be by the Ubuntu devs.)  But I'm not saying *never* download and unpack archives to install software.  I'm only saying it's often not the best way.

In the case of Tor, the devs recommend using one of their PPAs instead of the Universe repo, because "In the past [the packages in the repo] have not reliably been updated. That means you could be missing stability and security fixes."  Following option two or three at [https://www.torproject.org/docs/debian](https://www.torproject.org/docs/debian) is probably the best way of installing Tor.  (Of course, this is assuming you trust the developers at the Tor project.)

---

### Post by jfbooth on 2013-06-23
> **Paqman said:**
> I'm more concerned about why you were so sure you did it as root in the first place. Why were you doing this kind of thing as root? Were you running in a root shell, or did you just use sudo on the command line? Stick to normal GUI ways of doing stuff like this in future and it'll be less risky.

Thank you for your advice ... I give it total respect.  When I have a problem, I usually first do a GOOGLE search for a solution.  Most of those solutions instruct to use Terminal for commands ... as in the case of this problem.  In this case, I made the mistake of opening Terminal as root. Being a major rookie, my thought was I would then not need sudo for anything.  The warning came in the instructions at its very end.  Thanks to you (and others) I now know better ... and even better than that, I know WHY.

---

### Post by jfbooth on 2013-06-23
> **newb85 said:**
> Whilst this advice may not be wrong *per se*, I would avoid discouraging people from learning to use the terminal instead of "normal GUI".  But that's just me.  It's not bad for people who want to learn to use the CLI to do it for everyday tasks in order to become more comfortable and familiar with it.  My version of that advice would be, "Be conscientious about what commands you issue as root (or with sudo) in the future, and it'll be less risky."

But I do second the rest of what Paqman said.  Provided Tor's developers didn't create a security vulnerability that has already been exploited, there isn't any irreparable damage.  Unpacking as root means the files unpacked will be owned as root, instead of the normal user.  Running as root means the application could do literally anything to your system.  (Of course, in theory someone could write an application with malicious intent so that if you run it as root it automatically trashes your system.  Given that the Tor devs specifically told you *not* to unpack or run as root, I doubt that's the case.)

In addition to the aforementioned advice, I would also suggest that, whenever possible, you stick to using software from the repositories and PPAs you know you can trust.  In the repositories, the software will not have malicious intent, security vulnerabilities are corrected when they are found, and bug fixes are sometimes issued.  In a PPA from a source you trust, you should enjoy the same benefits (though the reviews probably won't be by the Ubuntu devs.)  But I'm not saying *never* download and unpack archives to install software.  I'm only saying it's often not the best way.

In the case of Tor, the devs recommend using one of their PPAs instead of the Universe repo, because "In the past [the packages in the repo] have not reliably been updated. That means you could be missing stability and security fixes."  Following option two or three at [https://www.torproject.org/docs/debian](https://www.torproject.org/docs/debian) is probably the best way of installing Tor.  (Of course, this is assuming you trust the developers at the Tor project.)

Learning from mistakes is a SLOW process.  Your wisdom and knowledge is obvious and I benefit from it.  It all makes sense ... the problem is, I don't know HOW to do a lot of things I am advised to do.  I have been using both apt-get and Synaptics package manager ... not understanding exactly what they are ... 'different repository access utilities' in my mind.  I only recently realized Synaptics is simply a front end for Aptitude .. DUH.  Seems like YUM equates to Aptitude but for Red Hat packages ... and YUM EXT equates to Synaptics.  My point is ... that has taken YEARS for me to 'realize' could have been understood in an hour of tutoring.  Alas .. no such tutoring exists that I know of.  I often pull the trigger to see if it is loaded ... because there is no other way to learn.  Support in forums ... thank God for it .. and people like you .. but it is always 'after the fact'.

In any case ... thank you all ... for your courtesy, wisdom, time, and advice.

---

### Post by Paqman on 2013-06-24
> **jfbooth said:**
> In this case, I made the mistake of opening Terminal as root. Being a major rookie, my thought was I would then not need sudo for anything.

Using sudo when you need it may be a bit of a pain, but it's there to protect you. A root terminal is a powerful thing, treat it with a bit of caution and you'll have less problems.

---

