---
title: "Linux Computers For Students: Pilot Project Questions"
date: 2016-12-06
forum: New to Ubuntu
---

### Post by j.horn on 2016-12-06
Hello everyone,

I am an high school teacher that has been granted permission to start a pilot project using Linux. I have some Linux experience. I've happily run Linux on my home computer for years with no complaints. I do not consider myself an expert by any means. I am very good at research and Terminal copy/paste! 
 
Phase 1 of the pilot has two goals:
Goal #1: The school is 'Bring Your Own Device.' This pilot will provide cost efficient computers to students that do not have devices. 
Goal #2: Test the effectiveness of Linux in the school environment. 

At this point students will not be learning about Linux. Not to worry, Phase 2 will be project based: Terminal, updating a system, installing and maintaining a Linux computer. If all goes well, the plan is to turn the support of the pilot over to the students.

For the pilot, I've been given twelve old laptops to use. I've  successfully installed Lubuntu on them and a few other applications. However, due to the parameters of Phase 1 the laptops need to be locked down. I will not always be able to supervise the students (if they use the laptops in other classes, during lunch, in library, etc.). At first I thought the standard 'Guest' login would be fine, but I believe it will be too limiting for a positive user experience (Goal 2). The students will potentially use laptops for a few days at a time. Therefore, it would be very convenient if they could save to the hard drive and not lose work between logins. Also, I would like to provide them with a more personalized experience than the generic guest account (ie. specific system settings, wallpaper, browser main page, etc.). So I have a few initial questions:

1) Is there a way to modify the Guest account defaults? 
So every time a students logs in they see a specific wallpaper, open the browser and it is the school's website, etc.?

2)  #1 does not solve the saving work issue. If I create a 'Student' account (Type: Desktop User). Is there a way to then limit students from making superficial changes on the account? 
They cannot change desktop wallpaper, panel settings, desktop icons, etc. This way every student has a consistent interface and I do not have to constantly be reseting wallpapers and color schemes.

3) In regards to #2, is there a way to quickly and easily update the system and erase the contents of the home directory, applications, etc.? 
This is particularly important as the laptops would be shared among students. I would need to insure everything a previous student did was wiped before handing the laptop over to another student. I'm imagining logging into Admin account and clicking on an icon on my desktop that runs a script that does all this.... creating which is beyond my current knowledge!

Due to my limited knowledge, this is a grand undertaking for me. I am open to any and all advice on making this project succeed.

Thank you,

James Horn

---

### Post by ajgreeny on 2016-12-06
Assuming each student will always use the same physical machine it might be best to create a standard user for each student on their machine, ie, a user with no sudo use ability so they can not install or remove applications, and give each users /home folder 700 permissions so no-one apart from that user can even read their files.

This way each user will have their own desktop wallpaper etc etc, after logging in, will be able to save and delete files in their own /home/*username* folder on the machine, and even change their own wallpaper, but not anybody else's, and of course, they will not be able to install any unwanted (by you) applications as they will not have sudo rights.

Assuming you are the administrator of all these machines you will perhaps need to be the one user who has admin rights and can use sudo to install applications etc etc and also will be able to remove saved configurations for each user when necessary.

How does that sound to you? We perhaps need to know in more detail what it is that you want each user to able to do, and what not to not be able to do.

---

### Post by kpatz on 2016-12-06
> 1) Is there a way to modify the Guest account defaults? 
So every time a students logs in they see a specific wallpaper, open the browser and it is the school's website, etc.?See here: [https://help.ubuntu.com/community/CustomizeGuestSession](https://help.ubuntu.com/community/CustomizeGuestSession)

> 2) #1 does not solve the saving work issue. If I create a 'Student' account (Type: Desktop User). Is there a way to then limit students from making superficial changes on the account? 
They cannot change desktop wallpaper, panel settings, desktop icons, etc. This way every student has a consistent interface and I do not have to constantly be reseting wallpapers and color schemes.You can set up a /var/guest-data directory where guest users can save things.  Or just create a regular account for the student and use a script to wipe their home directory and recopy /etc/skel or a copy of a preconfigured home directory.

> 3) In regards to #2, is there a way to quickly and easily update the system and erase the contents of the home directory, applications, etc.? 
This is particularly important as the laptops would be shared among students. I would need to insure everything a previous student did was wiped before handing the laptop over to another student. I'm imagining logging into Admin account and clicking on an icon on my desktop that runs a script that does all this.... creating which is beyond my current knowledge!If you use a single user account shared by whatever student has the laptop, you can use a script to clear and reset the home directory as I mentioned in #2 above.  Or give each student their own account, but that gets tricky if the students sometimes switch machines.

---

### Post by j.horn on 2016-12-07
@ajgreeny: Students will not use the same laptops all the time. The laptops will be circulated as needed. 

Students will need access to internet, office suite, and multimedia software.  

@kpatz: "[...] use a script to clear and reset the home directory."
This would be ideal. When a computer is returned, I could login to Admin, update, and run the script. The script can be written to function only on a specific user?
I'm going to look around the net and see what I can find.

I will also look at the link you provided.

I do not want to be rude, but if I cannot find such a script already made or something I can request help modifying, is there a place I can politely ask for such a script to be written by a willing volunteer? I ask because I do not know how much work it would be to write such a script. For example, it is one thing to ask someone to help you carry something down to the curb. It is another thing entirely to ask someone to mow your lawn, bag the grass, and carry the bags down to the curb.

---

### Post by HermanAB on 2016-12-08
Howdy,

I have some experience with this problem.

A specially configured guest account is probably the easiest way to do it.

The biggest issue to me was maintenance of the machines.  A student will always figure out a way to mess a machine up, whether intentional or accidental.  Therefore, it is is important to have a way to re-install the machines very quickly and easily so that you don't have to waste your time with it:  If *anything* is wrong with a machine - simply plug it into a mirror server and re-install it automatically.

Note that you cannot keep a single 'image' for replication, since every machine is always different in some way.  The Ubuntu automatic install system will handle these differences without a problem.

Therefore you need to look into making your own mirror server and automating the install with preseeding:
[http://www.aeronetworks.ca/2016/03/debian-installation-for-control-freaks.html](http://www.aeronetworks.ca/2016/03/debian-installation-for-control-freaks.html)

Students can keep their personal data on USB sticks and SD cards, then you don't have to worry about it.

---

### Post by Digitalscribbler on 2016-12-13
I'm coming late to this thread, but on kind of a more general note, you might want to take a look at how Penn Manor High School has attracted quite a bit of positive publicity for its efforts in integrating Open Source Software in its curriculum. One distinctive feature to their approach is that they give their students root access. Their tech director, Charlie Reisinger has done a TEDx talk [https://www.youtube.com/watch?v=f8Co37GO2Fc](https://www.youtube.com/watch?v=f8Co37GO2Fc) and also Red Hat's Open Source Education column has an interview with him [https://opensource.com/education/14/9/interview-charlie-reisinger-penn-manor](https://opensource.com/education/14/9/interview-charlie-reisinger-penn-manor)  Good luck!

---

### Post by Bucky Ball on 2016-12-13
[QUOTE=Digitalscribbler]Red Hat's Open Source Education column has an interview with him[/QUOTE]

This suggests Penn Manor High School is using Red Hat. Red Hat is a totally different kettle of fish to Ubuntu.

Still, some of the principles may be relevant from one to the other. How you get there may be radically different, though. ;)

---

### Post by j.horn on 2016-12-21
Busy time in the school as the holidays (finally) arrive!

@ Digitalscribbler
Thank you for the info. I am going to watch the video this evening.

@ HermanAB
Thank you for the link. That is an impressive post. I know enough to understand what you are getting at and have done. Unfortunately, I do not know enough to do it myself! Given time it'll settle in I guess. :)

@ kpatz
I was doubtful at first, but I've had a lot of success with customizing the guest session. The laptops now easily login with a school wallpaper, some general settings in place, and the browser complete with school website as the homepage and a few plugins.

At this point I believe this will be the direction I will go. Thank you.
(The "No session for pid 1045" error bug is annoying, but from what I've seen there is no fix yet, so I'll just live with it.)

---

### Post by HermanAB on 2016-12-22
As I alluded above, the big problem is not installing the system and making it work - the big problem is doing it again, and again, and again... ad nauseam.  It gets really tiring after a while.

So when you reach that point, read up on making a mirror server and automating the install with a preseed file.

---

