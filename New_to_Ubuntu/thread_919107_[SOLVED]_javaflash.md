---
title: "[SOLVED] java/flash"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Georgia boy on 2008-09-13
Hi. I was reading in the applications and noticed Open JDK Java, Icetea Java, Gnash SWFViewer and SWF DEC Flash. What is the difference between all of these? Are all Open source and are they just as good to use as the Adobe? 

I know that when going to some sites they say that I need some plug-ins but don't tell me what they are, just say to "Click here to download" and out of habit I don't download unknown plug-ins just because some site says I need them when they don't tell me what they are. 

So, if I download one of these that I'm questioning about will that take care of being able to view some of the stuff on the sites? :confused:
Want to stay Open Source as much as possible when doing anything. :) 

Thanks in advance for all of your responses and help.
Tom

---

### Post by perlluver on 2008-09-13
> **Georgia boy said:**
> Hi. I was reading in the applications and noticed Open JDK Java, Icetea Java, Gnash SWFViewer and SWF DEC Flash. What is the difference between all of these? Are all Open source and are they just as good to use as the Adobe? 

I know that when going to some sites they say that I need some plug-ins but don't tell me what they are, just say to "Click here to download" and out of habit I don't download unknown plug-ins just because some site says I need them when they don't tell me what they are. 

So, if I download one of these that I'm questioning about will that take care of being able to view some of the stuff on the sites? :confused:
Want to stay Open Source as much as possible when doing anything. :) 

Thanks in advance for all of your responses and help.
Tom

IceTea, and JDK, are both open source Java's, You can try them, if you don't like them, then Install Sun-Java.  As for SWF-Dec, and Gnash, SWF-Dec is the better on, but neither are up to par with Adobe Flash.  Like I said though you can try them if you like.

---

### Post by Mornedhel on 2008-09-13
For best performance, you'll have to use the binary blobs provided by Adobe. Otherwise, Gnash is GNU-licensed. I'm not sure which license swf-dec uses, but I'm pretty certain it's free. Both are usable as replacements for flashplugin-nonfree, until they crash.

Sun's Java VM is almost entirely, if not entirely open-source right now.

---

### Post by Georgia boy on 2008-09-15
Tried the two flashes. Couldn't get You-tube to work nor some of the other sites. Did the install from the applications of Adobe Flash. Everything worked. Thanks for your helpful suggestions. As far as I can tell the java is working. Will find out later I guess if it don't. Then I'll install the Sun Java.

Why is the Adobe Flash in the restricted area? If you go to their site it's free for downloading right? So, why not put in other areas for downloading?
Due to not being a copy left software?

Thanks
Tom

---

### Post by manishtech on 2008-09-15
> Why is the Adobe Flash in the restricted area? If you go to their site it's free for downloading right? So, why not put in other areas for downloading?
Due to not being a copy left software?
Its just because Adobe chose it to be so. Now they have relaxed their EULA since it was giving some problems due to licensing restrictions of some areas.
Free for downloading, but not in sense of freedom? Right??
Why not put it up in other places for downloading? I think first I have to read the whole EULA and I can answer this...

---

### Post by Georgia boy on 2008-09-15
Thanks Manishtech. Let me know what you find out. There are so many things listed as restricted yet when you go to some of the sites they show as free download. Gets kind of confusing at times.:)

I always try to use the Open source as much as possible and am always promoting it to friends, family and co-workers. 

I know that I ask dumb questions at times but that is the way I learn. By researching and if not finding then asking. I have always gotten such great help and responses from the forums. So far I have never been slammed like I have seen some getting slammed on other forums. Great bunch of people here, believe you me.:)

Tom

---

### Post by manishtech on 2008-09-15
> Thanks Manishtech. Let me know what you find out. There are so many things listed as restricted yet when you go to some of the sites they show as free download. Gets kind of confusing at times.:smile:
They write free download, maybe they mean free of cost. It should be free of cost, how can they charge for a software made by others atleast by ethics.
Surely I would tell you, but the EULA is intentionally made quite complicatefd with highly confusing legal and technical terms so that it gives two different meanings.

> I always try to use the Open source as much as possible and am always promoting it to friends, family and co-workers. 
That's great buddy! Keep it up....

> I know that I ask dumb questions at times but that is the way I learn. By researching and if not finding then asking. I have always gotten such great help and responses from the forums. So far I have never been slammed like I have seen some getting slammed on other forums. Great bunch of people here, believe you me.:smile:
When I started using Ubuntu, my questions were so dumb, that I used to get kicked in some communities. At my time, I didnt have presence to internet properly. :(

People at ubuntuforums are really great. Hats off the this community. :)

---

### Post by Mornedhel on 2008-09-15
Restricted does not mean it's not "free as in beer". It means it can't be on a default install of Ubuntu because of legal issues : it's not "free as in speech". For instance, if I remember correctly, the flashplugin-nonfree package downloads the actual binary straight from Adobe's website (with their consent, of course). A few packages require you to read and accept an EULA after download.

If you are concerned about what packages are free/libre software, install the vrms package and run vrms from the command line to get a list of what packages are or are not free, and how free your overall installation is.

---

### Post by dew5 on 2008-09-15
hello

For the java install instructions check

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

as for flash player to play youtube media check

[http://www.cyberciti.biz/faq/ubuntu-linux-how-to-install-flash-player-for-firefox/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-install-flash-player-for-firefox/)

hope this helps.

dew5

---

### Post by ggaaron on 2008-09-17
I see that nobody mentioned this. Sun is making java free software and OpenJDK is official Sun project and product of this switch. It will become official Sun's JDK some day. It is still not complete (a little part of libraries that Sun didn't have right to change license is still not covered by free alternatives) and Icedtea makes it complete by using parts of GCJ. What Ubuntu calls OpenJDK in repository is in fact Icedtea. It can be considered complete and during the porting process they even made some things better.

I use Gnash exclusively, many things work, youtube works, but it is still some way until it has features of proprietary counterpart.

And free software doesn't have anything to do with price, adobe flash is proprietary software (as is sun-java).

If you are a really hard free software fan then you can try gNewSense, a distribution based on Ubuntu, but consisting only of free software.

---

### Post by Georgia boy on 2008-09-21
Using the Open Jdk Java. Tried Gnash and other but unable to view Youtube or some of the other sites. So went with the Flash. I'll keep an eye on the Gnash to see if sometime it might work for me or not. I also checked out the site mentioned about GNewSense. Might be worth looking into but for now I'm using the Ubuntu. Haven't checked out my Windows side of the house for about a month now. Someone mentioned something about updates but when I did go there it was still current. So, closed out and went back to Ubuntu. Using it more and more all the time now. Really like it so far.
Tom

---

