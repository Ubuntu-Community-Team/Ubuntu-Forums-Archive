---
title: "hijacked pc problem"
date: 2011-08-14
forum: Repositories &amp; Backports
---

### Post by sjvinc on 2011-08-14
I think this is where I need to place this. My pc got infected with  something way back in late 2004 when the Node I was connected to  crashed. My ISP told me they had a very bad virus or something in the  system at the time.  Suddenly I could not do very much with my pc. I  seemed to have lost all administrative rights. 

I checked everything and I kept finding things that should not have been  there. Everyone kept telling me they was supposed to be there but no XP  book that I either bought or read through other sources mentioned those  items.   Then recently, I used a tool that found that my trash was  corrupt and removed it.  

next I found a server that I knew for a fact was a Unix server and  decided to put a Linux live cd in to see if there was Linux hiding in my  hd somewhere. Sure enough I found it. My Ubuntu cd went through the  motions of doing an install, but never once completed and I had to  cancel each install because of messages that it could not find my cdrom  drive and the wrong Linux was on the drive.  

The first time I got in, I went through command line mode and found two  CDRom;s one was marked CDrom0 the other just cdrom with a ton of other  folders leading to null.   I also found a broken pipe, then several  other pipes.   The hd is set to do a silent swap with the root drive. I  also looked at modified dates and found the latest modification to be  2005 with the earliest being 2000.  If my Ubuntu would have installed  any of that, I should have found something with 2011 or so I would  think.

I tried to look at different things and even tried to get into sudo as  my book suggested I try. some items were not there, others I was denied  access. I can not even change my Ubuntu password, I have tried and  nothing works. I have three linux books and one of them is about Ubuntu.  so I have not done anything that was now suggested in the book. Plus  with this being hijacked, I am a bit worried about actually logging into  a root account.   There are two redirection starting at boot of the  system. from just about 10 seconds after I hit the power button. one  leads right into Unbuntu vm the other is if I am using the cdrom to  start the system. 

Everything is running in memory, I have found two traps and when Ubuntu  found and wanted to remove one of the bad CDrom's I got a warning that  my system would be hosed if I continued. I chose to play it safe and  read all I could from the logs.  

Through one log, I saw that Root (the user) was making changes to the  system, locking out items, putting blocks on ligitimate parts of Ubuntu  and making fake copies of the same things. Then it switched to Ubuntu  and tried to get back into root and could not. It spent some time trying  to switch and I think finally gave up.  Lucky for me, it was not able  to change everything in the root folder, even though it has tried to  hide the root folder, I was still able to get there and read the log  files. 

My problem is, what is the best way to undo all of this. I can not just  go in and wipe the system. First it has a cdrom leading to null, plus  two dangerous items that threaten to do damage that it promises I will  regret.  I can only log in as a user with Ubuntu, I can not use any  tools because they have been corrupted by another part of this corrupt  Ubuntu (I have pics of the log for this) even with that, I can not gain  access to it. then I do not know what v.2 was like, the version I have  on cd is around v.8 I have seen a modification date of around 2000.   

I had a suggestion from a friend that they would put it on their secure  server and try to get it out. I am worried about that for obvious  reasons. This is nothing to play with, I would rather let it sit like a  paper weight than allow someone to let it get out. 

I also tried to do shutdowns and could not get it to shut down.  I am  thinking that I need to have good copies of all that it actually did, or  close enough to be able to at least have something made up and put on a  memory stick, possibly like a virus would be and set off as soon as the  system looked at it. something that would go in and move all those  pointers, return the Ubuntu (user) to what it is supposed to be and fix  the setup to the absolute min of what it should be in order to remain  stable. Plus I have to be able to lock out those traps that I have found  and hope there are none others.   

I do not have either my system or my notes with me, so all this is from  memory.  I will be able to give a much better explanation of exactly  what was done in a few days if needed.   My current problem is do I  trust my corrupted pc to people I am not sure what they will do with  this Ubuntu if they get it out? will I be able to turn this around?  While I might not be new to pc's, I am quite new to the Linux side. I  feel like I have been going through a crash course in learning this  Linux system.  I spent one week reading each book before I even went  into my system and looked around it. 

what was v.2 like? I am sure that many of the things I could use in  Ubuntu now was not there then. that could explain why I am having such a  problem. I have also found things from x.0.org  and a few other things,  I feel like this x.0.org is part of the exploit, since I saw some  things in a log file for it which lead me to think it was not exactly  doing good. 

I need some suggestions and some very good ones. The problems that I am  having are not mentioned anywhere. over the years I have gone to all  these other places to get their help in removing this thing - naturally I  didn't know there was a Linux hiding in my system, but if they was as  good as they claimed, they should have seen it. that is my reason for  the hesitation to bring my machine to them now.   Therefore, I feel as  though I am forced to get this stopped and get it out myself.   I also  think that I am either in for the education of my life or I am going to  fall so hard, I might never stand up again.

I do know and like command line, I have been on computers since the  80's, so I do have something to work with. I just wish that I had spent  the last 5 years learning and understanding Linux the way I did with  Microsoft.  although it has not actually hurt me. I have always hated  Microsoft and dislike all the garbage they put into the system. while  switching tty for my ubuntu user, I did notice that I somehow got into  one of the streams, I am not sure which one or where it went. I just got  out as soon as I saw I was there.

I do not think this actual pc is secure enough to even discuss actual  fixes at this moment. but in a few days I will be at a much more secure  spot... I hope anyway.

---

### Post by Elfy on 2011-08-14
Ok - this is not the right place for this.

There was no version 2 of ubuntu - started in 2006 - 4.10

This is again a wall of text with no apparent support request, please start a new thread in one of the support forums - stating plainly what it is you need from people - you can link to this wall of text there, but this thread just like the last one is closed.

---

