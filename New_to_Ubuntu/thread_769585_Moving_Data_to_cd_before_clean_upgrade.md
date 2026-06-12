---
title: "Moving Data to cd before clean upgrade ?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by valjour on 2008-04-26
Hi,

I have saved data to dvd/cd before in Gutsy.  However, how can I include firefox bookmarks (I have a ton!) (and how about my Thunderbird emails?) with home folder before I put data to disk prior to upgrade? Won't I loose them otherwise? 

I wish to later transfer some data back to a cleanly installed Hardy machine after my 8.04 distro disk arrives.

Thank You for the help.

Pete

---

### Post by disturbedite on 2008-04-26
i do the same thing every time a new version is released.  (although i test the new versions).  i prefer a clean install.
except i have a second HDD that i usually move everything that i need to backup on the main HDD to.

to backup firefox's bookmarks in fx2, copy the bookmarks.html in your profile folder.  in fx3, simply open up places organizer (bookmarks organizer) & click backup & choose a place to save the file to.

---

### Post by Moop on 2008-04-26
I always backup my whole Thunderbird profile when I'm moving the data. The profile is in your home directory in .mozilla-thunderbird. (enable viewing of hidden files to see it) If you copy that into your new home directory before you run Thunderbird for the first time, everything will be as it was in your old install when you start Thunderbird.

---

### Post by valjour on 2008-04-26
Thanks Disturbedite and Moop,

I went to bookmarks manager and exported bookmarks.html to home folder.  Is that all I have to put on the cd or dvd to access them after I do the clean install? 

Moop, is profiles folder online can't seem to find it from my browser or home for complete ffx backup? I guess I am asking where is it?   

I have yet to decide if i am going to to a full system backup or simply put my home folder on cd.  Haven't done anything noteworthy or integral just learning how to work with Linux.

As a newb with 5 seconds of bash experience I tried some tricks that did not go over very well. Stuff experts would be weary of, like updating perfectly good working bios because there was a newer (6 year old update) available (exe from Dell). 

Avast tells me that my kernel is compromised, ready to explode i think the message read, and I get assorted lengthy error messages when I scan. My plan with Hardy is to document every thing i do to the last detail and not mess with things that are not broken. 

Bash (command line scripting) makes my head spin.  Still attempting to get over my microsludge point and click ignorance. Man and info/doc pages are a big help in adding to the spin:)  I'm overwhelmed with info is all. 

Hoping the repetition of starting fresh will act as a reinforcement of what I have been trying to learn.

Thanks again

Pete

---

### Post by Moop on 2008-04-26
Go to Places-Home folder. Use ctrl-h to enable viewing of hidden folders. There should be a folder named .mozilla and maybe .mozilla-thunderbird. Your profiles are stored in the folders. You could just copy the whole folder. 

All you need to do with your bookmarks is import the file you saved into your new firefox install. 

Consider creating a separate partition for /home on your new install. Then you could just keep your /home directory when doing a fresh install and not worry about copying things over.

---

### Post by valjour on 2008-04-27
Thanks Moop,

When I make the cd or dvd I think I will unhide and copy all of home to it.  There is some cool stuff in there.  

Is there a tutorial/link on key shortcuts like ctrl-h? I know save and print thats about it.

How would i create a separate partition for my home folder?  Is it best to do so at the time of the installation?  I will be using a live full 8.04 distro cd to do the upgrade. Need to get my kernel restabalized.  I ordered it about three weeks ago from Canada.  For the Gutsy upgrade it took over a month for me to actually get it.  This being a new distro may take longer I assume. Did so last time as a safeguard in case I royally messed up my machine- upgraded from Feisty through GUI update. 

And would I import bookmarks the same way I exported them?  Could i do it straight from the "backup" cd I have created to save a step? Or move old profiles into the new folders? Or both...

Thanks for fielding so many questions.  I catch on quicker and seem to retain more.  Sometimes I feel so alone and lost in my weeks of pouring over books and man pages.  I am determined to learn Linux and programming and contribute more someday. So many angles to this thing...wouldn't have it any other way. Nothing good is easy.  I just haven't heard the pop where it all becomes simple yet.

Pete

---

### Post by Moop on 2008-04-27
Keyboard shortcuts.  [https://help.ubuntu.com/community/KeyboardShortcuts](https://help.ubuntu.com/community/KeyboardShortcuts)

Yes you create a separate partition for /home when you do the install. Use the partitioner on the live cd to partition your hdd before you install. Typical would be something like 10gb for /
2gb for swap and the rest for /home. Then when you install you choose manual when you get to the partitioner and assign the proper mount points (/ and /home) to the partitions you created. There are many partitioning strategies and you may want to research what will be best for you. [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Yes you can import your bookmarks directly from the cd the same way you exported them. If you copy your firefox profile (or the mozilla folder) from your old install into your /home on your new install then your bookmarks and settings will be there the first time you run firefox. Remember that Hardy has Firefox 3 installed by default so all your extensions may not work if your coming from a older version of Firefox.   

Good luck. Just ask if you need help.

---

### Post by valjour on 2008-04-29
Thanks Moop,

I appreciate the links.  Upgrade CD's shoud be here in a couple days.  Got confirmation that they were shipped out Sunday right after you posted.  I will  let you know how it all goes during the install. Hoping to get it done   next weekend latest. Excited to check out Hardy. If I need help with the partitioning I will post here when I get to that point. Or if I run into any snafus before that point.  Pretty sure the links should carry me through.

Moop and Disturbite :guitar: 


Thanks again

---

### Post by eeried on 2008-04-29
Hello,

Can you really confirm that if you copy your whole .mozilla-thunderbird to a fresh install of Thunderbird and before launching Thunderbird for the first time, you actually get a working Thunderbird complete with your accounts (of course addresses and folders aren't a problem), even if the version of Thunderbird has changed?

cheers,

---

### Post by Moop on 2008-04-29
> **eeried said:**
> Hello,

Can you really confirm that if you copy your whole .mozilla-thunderbird to a fresh install of Thunderbird and before launching Thunderbird for the first time, you actually get a working Thunderbird complete with your accounts (of course addresses and folders aren't a problem), even if the version of Thunderbird has changed?

cheers,
I've always had success with doing it that way and I doubt if the version of Thunderbird makes a difference except for maybe any extensions like Lightening etc.

---

### Post by eeried on 2008-04-29
Many thanks Moop!

---

### Post by valjour on 2008-05-06
Hi All-

Got my new disk but they only sent the (regular) i386 Desktop CD for 8.04 LTS.  Shows the CD on my desktop but does not seem to boot straight from it.    What am i missing here?  Does this mean I have to fdisk to start from scratch?  Just feel like starting over and learning new stuff.  Would be some good lessons for me.  Where could I find info on whole process on a manual clean upgrade with this disk?  Thanks 

Could I do the whole thing with Bash?

Pete

---

### Post by octoberdan on 2008-05-06
> **valjour said:**
> Hi All-

Got my new disk but they only sent the (regular) i386 Desktop CD for 8.04 LTS.  Shows the CD on my desktop but does not seem to boot straight from it.    What am i missing here?  Does this mean I have to fdisk to start from scratch?  Just feel like starting over and learning new stuff.  Would be some good lessons for me.  Where could I find info on whole process on a manual clean upgrade with this disk?  Thanks 

Could I do the whole thing with Bash?
ve
Pete

Yes, but you probably don't have to. If you're not booting from it automatically, you may need to configure the BIOS to boot from the CD drive before looking at the hard drive. There should be a section that lists the priority of boot devices, make sure your CD is at the top of the list. You may need to switch it back after your finished your installation. It's worth a try.

---

### Post by valjour on 2008-05-07
Hey octoberdan,

I think I'd like to do it from bash and repartition my hard drive.  Is it too much of a headache? I'm in the learning stages and want to gain insight into my machine so we can become one and dwell in unity with our brethren.

I am not opposed to changing bios ordering.  To get in thats probably F2 on a Dell?

Thanks

Pete

---

### Post by valjour on 2008-05-09
Well, I got the clean install upgrade done and created new partitions manually 

1.  /boot     148M
2.  /       26000M
3.  /home   45872M
4.  swap     8003M


Are these numbers a little much?  In the right order? Did not know what to do if i just left unusable free space at the end of the volume.  Would only let me make 4 partitions.  When i didn't allocate all the space it was deemed unusable by ubiquity partitioner.   I gather that there is some way that I could have added Logical Volumes in the fourth partition. (I don't know how I could have got that done)  

Haven't had any immediate problems after setting this up and such so far.  No problem updating or adding to my bare bones set up in the first hours of use.

Please let me know if this allocation will be okay or are there better suggestions on how to better utilize my space now that I am set up?  

Thanks For All the help so far,

Pete

---

