---
title: "Accessing/viewing video from a security system"
date: 2013-05-15
forum: New to Ubuntu
---

### Post by squakie on 2013-05-15
A friend has a local gas station/convenience store.  He has a security system in place that records video.  He has tried moving the video files to his Ubuntu PC to gain more space on the security system and to review them.  I've haven't gotten to see it (I can understand - it's his security system), but he has told me he has tried a USB drive but couldn't see the files in Ubuntu - what ever that means, he has tried a cable USB connection (I don't know if it's a crossover cable or not).  He claims he cannot see them at all.  I've asked what file type they are but he just says security videos.  I have suggested to start with the gstreamer additions (used to be good, bad and ugly, but I don't know if perhaps that is part of Ubuntu restricted extras now or not), and then VLC.  It's a little hard to understand what he has or hasn't done.  So, I thought I'd just ask out here if anyone has any experience with these types of files and accessing them in Ubuntu.

I understand it may be a taboo topic - since it deals with security systems, but I'm hoping if no great details are given - perhaps just a file type and how to process them in Ubuntu - might still be allowed.

Thanks!

---

### Post by mastablasta on 2013-05-16
he needs restricted extras package as the codecs are there. if the videos are in DVD format or somehtign liek that then he will need libdvdcss or something liek that (how to watch DVD on ubuntu).

but probably installing "restricted extras" package + VLC should do it.

---

### Post by squakie on 2013-05-16
Thanks mastablasta - I'll pass it all along to him tomorrow - and try to get him to understand a USB crossover cable versus a USB to USB cable - that might be tough!

---

### Post by grahammechanical on 2013-05-16
Surely this wonderful security system came with a method of storing/archiving the recorded video? The process is surely computer based? What OS? What standard file format? I would not be surprised if a version of embedded Linux is not being used in the base unit. The archive may be compressed. That would make sense. The videos would soon fill up the hard disk otherwise. So, perhaps the videos are compressed as they are recorded. 

Regards.

---

### Post by alhefner on 2013-05-16
Knowing the video file format will not compromise his security system. That needs to be knowm before you can really figure out what will be needed to play those video files.

---

### Post by squakie on 2013-05-17
yeah - I've pushed and pushed for that and all he says is "they're video files".  I keep asking what type - dvix, mpeg4, etc., etc..  He doesn't "get" it.  The system has it's own recorder and he tries to dump the files off to usb flash drive, but now he's saying he can't burn it to a dvd in Linux.  He insists that he has to buy this ultra-expensive dvd recording software of some sort - I keep telling him you can do it all for free.  The first step is the file type and finding the appropriate codec and even a transcoder from there.  I've recommended installing Ubuntu-restricted-extras and perhaps some of the winxx codecs from mediabuntu, as well as the css decoding things hoping to find the "thing" that will allow him to read/view the videos.  After that burning to dvd is a no brainer using free software as well.  He really just doesn't understand, and to be honest, unless he does some of the things I've recommended - like telling me the file type, perhaps even the manufacturer and model number for his security system so I can look some things up on the company's web site.  I even asked if he could make a 1 minute or so test on his security system, copy it to a flash and let me "play" with it so I can see what's really going on, but he won't do that.

Right now, it's at a stand still as he won't let me actually see in person what he's messing with.  Without that or getting the information from him I've requested, I know he's just going to get more frustrated - and he's at wit's end right now.

I don't know what else I can do to try to help him.  So, thanks everyone for the replies.  I'm going to leave this thread open but I probably won't be checking it unless I get something from him.

Thanks again everyone!

---

### Post by squakie on 2013-06-25
Well, the person in question has never gotten back to me on any of my questions, so no need to leave this thread just hanging out there.

Thanks everyone for your contributions.

---

