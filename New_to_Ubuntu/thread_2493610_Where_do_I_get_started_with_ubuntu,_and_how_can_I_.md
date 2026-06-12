---
title: "Where do I get started with ubuntu, and how can I fully utilize it?"
date: 2023-12-19
forum: New to Ubuntu
---

### Post by zzimforcee on 2023-12-19
as I stated in the title I am new to Linux OS and would like to become more familiar with it but I don't really know how to fully utilize it. If I need to install different applications and such.

---

### Post by MAFoElffen on 2023-12-19
Welcome to Ubuntu Forums.

That is a very subjective question...

These should be a good start. You can right-click on these links to download these PDF's to read at your leisure.:
[https://wiki.ubuntu.com/Training?action=AttachFile&do=get&target=DesktopCourseStudentGuide.pdf](https://wiki.ubuntu.com/Training?action=AttachFile&do=get&target=DesktopCourseStudentGuide.pdf)
[http://ftp.labdoo.org/download/Public/manuals/manuals-ubuntu/EN/The%20Official%20Ubuntu%20Book,%207th%20Edition.pdf](http://ftp.labdoo.org/download/Public/manuals/manuals-ubuntu/EN/The%20Official%20Ubuntu%20Book,%207th%20Edition.pdf)

Both of those have much information to learn about using Ubuntu.

---

### Post by UltimateCat on 2023-12-19
There are a number of ways to get started with Ubuntu.
The best way to get acquainted with Linux is to try it.
To do that download the Ubuntu .iso to your computer. Once that's done you'll want to check the integrity of the .iso image.

[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

If you are using a Windows computer you'll need either Balena Etcher or Ventoy to make your Ubuntu .iso into a Live image on a USB thumb drive.
[https://etcher.balena.io/](https://etcher.balena.io/)
[https://www.ventoy.net/en/index.html](https://www.ventoy.net/en/index.html)

Once Etcher or Ventoy have successfully made your usb thumb drive bootable plug it into your computer.
With the Ubuntu Live USB thumb drive in place reboot your computer and press the key as it is rebooting to enter into your BIOS.
Go to the boot section of your BIOS and make the USB thumb drive to be the first selection in the boot list.
Save the changes and reboot.
Upon rebooting Ubuntu will begin to boot so you can try it.

You can also try Ubuntu in a virtual machine like Virtual Box.

[https://www.geeksforgeeks.org/how-to-install-virtualbox-on-windows/](https://www.geeksforgeeks.org/how-to-install-virtualbox-on-windows/)

All the best-

Ultimatecat

---

### Post by guiverc on 2023-12-19
I'll suggest installing Ubuntu on a second machine (many of us have older or secondary devices we no longer rely on) and try just using it.

Can you get Ubuntu installed?, access the internet? do the things you normally use a computer for etc

Set yourself goals, if you normally use a windows computer to do a task for example, how would you do that task on Ubuntu; think about what it required and look for the apps/programs or packages required & see if you can install them.

You'll make mistakes; we all do. Many of us learn more from those mistakes than our easy successes. When you make a mistake though; you've got a new task in just recoverying from that. Have a go at that, and then try and non-destructively re-install the system using that re-install as a fix. Once you've learnt how to non-destructively re-install (and how quick it is), you'll be less scare of making mistakes too. Whilst we can re-install our software super fast.

Note:  the re-install is best with desktop systems, you didn't mention if you're wanting to get to know Ubuntu Server type systems, or desktops, with their being slight differences esp. with regards re-install. Always rely on backups, as a re-install can fix the software issue, and whilst it can re-install around your data; it cannot recovery any deleted data so backups are required.

[http://tutorials.ubuntu.com/](http://tutorials.ubuntu.com/)

---

### Post by TheFu on 2023-12-20
> **zzimforcee said:**
> as I stated in the title I am new to Linux OS and would like to become more familiar with it but I don't really know how to fully utilize it. If I need to install different applications and such.

As others have said, this is a huge topic and the answer, best answer, depends on things we don't know and you don't know.  Nobody learns Unix/Linux following the same path.

To _fully utilize_ it, just know that won't happen for at least a decade of daily, constant, use.  There's just too much to know and too many different answers for almost every question of "How do I .... "

If there aren't 50 answers, there are probably 500 answers to any question.  Of course, you might not like the answers, since no OS is perfect, like no program is perfect.

Anyway, I used to be asked how to learn Linux (don't get too caught up in 1 distro, they are all very similar). Here's my answer and links for other ideas.  [https://blog.jdpfu.com/2017/03/31/learning-linux-condensed](https://blog.jdpfu.com/2017/03/31/learning-linux-condensed)   Learning things in the correct order can make things much easier.  There are a number of posts in these forums from others new to linux, asking for similar advice.  Find those threads and review them, but don't become parallelized with gathering data. At some point, you have to begin.

---

### Post by #&amp;thj^% on 2023-12-20
> **TheFu said:**
>  but don't become parallelized with gathering data. At some point, you have to begin.

+1
"The Journey of a 1000 miles begins with the first Step"

---

### Post by SeijiSensei on 2023-12-20
Identify the tasks you want your computer to do, then install the necessary software. For me these are:

Web browser: Firefox (installed by default)
E-Mail Client: Thunderbird
Office Programs: LibreOffice (installed by default I think)
Image Editor: GNU Image Manipulation Program (GIMP)
Video Editor: KDEnlive

What else might you want?

---

### Post by Dennis N on 2023-12-20
When I wanted to learn about LInux, I bought a book and read it (It was called "Beginning Ubuntu Linux") in 2007. I read the whole thing before I even installed Ubuntu 7.04 from the free CD that Ubuntu had sent in the mail. There still are real physical books about Ubuntu - For example, I looked just now on Amazon, and see at least 3 specifically for Ubuntu 22.04 LTS. That might be an idea for you to consider.

---

### Post by TheFu on 2023-12-20
> **SeijiSensei said:**
> Identify the tasks you want your computer to do, then install the necessary software. For me these are:
 ...
What else might you want?

A calculator, alarm clock, notepad/wiki, methods to automatically share files between all his devices like tablets, phones, and other computers without giving data to cloudy services.  

Perhaps photography albums, recipe files, audio books and music, videos and movies, automatic updates for weather in 3 places, news feeds from reputable sources, not social media, a way to save webpages to read later, perhaps on a tablet when disconnected. Translation of files when needed too. None of this includes the most powerful stuff like automating these things so the information is waiting and he doesn't need to go find it.  Just having music directors shared across devices is nice for many people who go disconnected like I do. I prefer playing music stored inside my android devices, not streamed, so having those directories automatically shared to each is nice.

Ways to share files securely with acquaintances, not just trusted friends and family.

Easy to use backups and disaster recovery can't be forgotten. All storage fails, we just hope that doesn't happen before we have solid backups or migrate our data to larger storage - nobody goes to smaller storage, do they?

Having voice control for all these things.  I can dream, right?

We are Linux people. We can self-host lots of things.  Some ideas: [https://github.com/awesome-selfhosted/awesome-selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted)

IMHO, 80% of the power in Linux systems is automation, not point-n-click, with manual look ups.

---

### Post by ian-weisser on 2023-12-20
> **zzimforcee said:**
> ...I don't really know how to fully utilize it. If I need to install different applications and such.

How to install different applications is well explained by the Ubuntu Desktop installer slide show.
It is also well explained by Google.

You learn how to "fully utilize" by using it. Ubuntu Desktop is designed to be discoverable and safe.

If you were to present a specific example or two that a Search Engine cannot answer, we could offer more detailed advice.

---

### Post by ActionParsnip on 2023-12-21
How did you become familiar with the previous OS you used? (Windows? MacOS? etc)

---

### Post by Rubi1200 on 2023-12-21
Start with small, easy steps. Keep it simple.

Learn how to install and uninstall software using the GUI apps, then move on to the command line.

Then it is up to you to decide where to go next. It depends on your needs as a computer user.

---

### Post by yancek on 2023-12-21
Try reading through the Ubuntu Desktop Guide at the link below.

[https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)

---

### Post by MAFoElffen on 2023-12-21
Here goes with my first recommendation:

I learn the most by diving in and doing things. Get your hands dirty and do things over and over again.

1) As a beginner, do yourself a big favor, one of the earliest skills you should learn is to do a backup and be able to restore it.

That first skill will save you. Always have a good place to be able to return to. 

When you decide to try something new where there might be a system change, do a backup first. If it goes wrong, restore your backup.

If you have questions about backups, ask TheFu or search on his UserName here.

You don't know how many times Users come here for help, where if they just had a good backup, it would have saved them days of work.

2) Have a plan. Decide what your goal is and figure out how you want to get there. Learn the steps to do that. Type that out i your plan. Just doing that will map out what you should do... And getting that out into a plan sometimes points out where it might have weaknesses to work out.

I also do this. It helps in keeping records of where my system is, and how to get it back to where I want it if something goes wrong. It also helps me when tryig to learn new things. On what my goal was, what was expected, and what really happened.

Treat it as a journey, and an adventure. Sometimes getting there is not as important as how you got there.

This is how I tried to motivate my past Computer Science students and team-members to challenge themselves, and make that mean something to themselves. If you can paint a picture for them that they can see something they want for themselves, that makes that so much easier.

---

### Post by aljames2 on 2023-12-21
> **MAFoElffen said:**
> Sometimes getting there is not as important as how you got there.

Very true, resonates with me. When I started, I knew I was getting knee deep in new learning, and some info made sense at first, and other info eventually made sense, and still more being added to the repertoire of knowledge.

A notepad is your friend. Pluma, Mousepad, Gedit, whichever comes with your distro, use it to take notes of your steps and narrate what you are doing & why.  I have a document, one of my first, that I used to list command line commands that do common things and that are used most often.  Links have already been provided to some great resources.  Download the free Linux command line document and save it on your phone, and pull it up and start reading while you’re having lunch.  I probably did that every day for about three months.

When it’s fun, and you enjoy it, you will embrace the journey.

My motivation was to ditch the big W, success!  Now I just have to tolerate it at work. :)

---

