---
title: "If no restore point : then ?"
date: 2014-01-03
forum: New to Ubuntu
---

### Post by flyfisherbryan on 2014-01-03
This is my first ever post.  I have been running Ubuntu 13.10 for about a month and have a problem (the nature of which is irrelevant) and have seen several threads that have addressed similar problems.  Each thread (and sometimes each post withinin a thread) suggest something different to do to fix the problem.  All of these solutions involve using sudo, which we newbies are warned can be dangerous if you do not know what you're doing.  I only use the command line if I can undo what I have just done, but do not understand enough to do this in sudo yet.  What to do?

---

### Post by deadflowr on 2014-01-03
sudo allows an administrative user to run at the system's highest levels.
This allows us to briefly run commands that would otherwise need to be run as root.
If you have questions about what a command will be doing, just ask.
If you want to make sure that the command you are going to enter is correct and that no problems will happen when it's run, just post it and ask.

---

### Post by flyfisherbryan on 2014-01-03
I know what sudo is and have used it.  I have even undone a few things where I understood what was going on.  I guess my real question then is can you direct me to a good place to teach me so I do not have to ask all the time... though I do appreciate the help. :)

---

### Post by deadflowr on 2014-01-03
This might be of help
[http://ubuntuforums.org/showthread.php?t=2015424](http://ubuntuforums.org/showthread.php?t=2015424)

---

### Post by king.of.random on 2014-01-03
Bear in mind also that your problem has probably been asked many times by other newbies and as such searching the forum can be your answer. Also most commands have a built in manual ie 

```
man apt-get
```

or

```
info apt-get
```

To a newbie command line entry can seem daunting but in many ways it performs tasks available through a gui but much faster; so it makes sense to learn as much as you can.... and as suggested never be shy to ask as I bet there are many others who also would like to know :)

---

### Post by flyfisherbryan on 2014-01-03
Thanks to both of you! :D

---

### Post by king.of.random on 2014-01-03
No problem and good luck with your Linux adventures!!

---

### Post by Impavidus on 2014-01-04
When someone comes with a problem here, many commands suggested to him are meant to further diagnose the problem. They don't change anything on your system. Often several command are needed to find out what the problem exactly is, and those commands may not be suggested by the same user here. We want to be quite sure what the problem is before giving a command to solve it, else the problem could become worse. So, be careful when somebody says: "Use this command and your problem will magically go away." I try to make people understand their problem, so that they can prevent it from happening again. Furthermore, there may be different ways of solving the same problem.

Also watch the number of beans on this forum. Someone with few beans is often a newbie too, someone with many beans is likely a veteran. If a newbie and a veteran contradict each other, go with the veteran. Of course I'm not saying you should never listen to a newbie.

---

### Post by buzzingrobot on 2014-01-04
Caution is traditionally advised when using sudo because it temporarily gives an ordinary user the ability to alter parts of the system users cannot otherwise alter. 

Unix, the model for Linux, was designed a few decades ago as a multi-user system. That means multiple users can log on to accounts on one machine, simultaneously or sequentially.  Say, for example, an office with one Unix machine and ten employees in ten offices.  The employees would not need a separate Unix machine, just a screen and a keyboard, and they'd log in to their accounts over the local network. 

The obvious issue with this is that users need to be segregated -- walled off -- from each other so they can't alter, accidentally or delilberately, other users' files

This is accomplished in Unix/Linux by a system of permissions, rights, etc., that can be associated with a specific user.  Typically, a user has full rights to the contents of his or her /home directory (e.g., /home/bob, /home/sally. etc.) but little or no right to any other user's directories. 

The user who administers all this -- who has the power to create and delete user accounts and assign rights and permissions to a user -- is the "root" user, aka "superuser' aka "administrator".  The root user has rights to everything on the system and is, in effect, all-powerful.

In the multi-user setup envisioned in traditional Unix, with actual multiple people accessing one machine, any user who wanted to do something that required rights or permissions he did not have -- say, install files outside his /home directory -- would need to ask the person who was the root/superuser/adminstrator to do it for him.

Today, the typical Linux user is the sole person at a machine.  That means we need to be our own root users.  While it is possible to configure a Unix system so you can run as root all the time, this is both very risky and often surprisingly inconvenient.  Use of "sudo" allows an ordinary user to assume root authority on a per-command basis.  One of its purposes is to wave a "Be Careful!" flag.

One reason online advice is often presented as a command line to be copied into a terminal is that it is difficult to explain, in text, how to navigate through a GUI to accomplish the same thing, especially given the many interfaces/GUI's available in Linux.

---

### Post by The Cog on 2014-01-04
I'm sure nobody would be offended if you replied to one of their suggestions with something like:
Before I do this, can you explain what it does and how to undo it if I need to.

I for one would respect someone who has the sense to ask such a question, although I would hope they would have read the man page first. Remember that if you need to ask, then other people reading the thread later will likely have the same question.

---

### Post by buzzingrobot on 2014-01-04
And don't fret if the man pages seem impenetrable.  They were typically written by the developer of that tool and are deliberately terse, dense, and make assumptions about the user's knowledge and experience. I.e., they aren't intended as easy lessons for newbies.

For instance, the man page of "cp", one of the most common commands, details several options that rely on recursion.  If you don't already know what recursion is all about, you may be at a loss.

So, yep, just ask.  

(Remember, no one memorizes what they don't use day in and day out.  They just know where to look it up.)

---

### Post by flyfisherbryan on 2014-01-04
Thanks everybody!  I have now downloaded some of the literature and am starting to read through it.  When I have a question, I will ask.

---

### Post by Mark Phelps on 2014-01-04
Your thread title implies that you're looking for a feature similar in Linux to what folks think "restore points" do in MS Windows, right?

Unfortunately, there is no such feature -- especially given that MS Windows restore points do NOT, despite the common belief, act like a time machine, returning the MS Windows PC to a former date.  All they really do is overwrite the registry and some operating system files with older copies that were automatically saved when system changes were made (i.e., Windows Updates).

Linux does not save old versions of system files and there is no registry.

So, in Linux, if you want the ability to return your machine to a previous state, you have to make the backups yourself; otherwise, you nothing to use to roll-back the machine to a prior state.

---

### Post by mastablasta on 2014-01-04
then there are timed automatic backups or manul backup depending what you want to do or need. 

"back in time" will create snapshots

rsync will do incremental backups

Clonezilla or the more easy Redobackup will create system image (bit by bit copy)

Mintbackup tool will create system folder backup and home folder backups 

etc.

---

### Post by cmcanulty on 2014-01-04
ubuntu Tweak has 3 restore options that will sometimes save you from things done wrong.

---

### Post by king.of.random on 2014-01-04
> **Impavidus said:**
> Also watch the number of beans on this forum. Someone with few beans is often a newbie too, someone with many beans is likely a veteran. If a newbie and a veteran contradict each other, go with the veteran. Of course I'm not saying you should never listen to a newbie.

I do agree in general with the beans. However if, like myself, the respondent has few beans because they are a new "returner" to Ubuntu, but with years of Linux experience then this isn't necessarily true. It maybe also that the user has years of Ubuntu usage but only recently had time to contribute to the forum. I haven't explored all the options in the profile setup but it might also be an idea to check the respondents background.

As a rule of thumb though, I guess that fewer beans does mean newbie...

---

### Post by Impavidus on 2014-01-04
Yeah, that's why I wrote "is **often** a newbie too." In fact, when I first came here I already had several years of Ubuntu experience (started with Dapper Drake). Still, I can say I learned quite a lot since.

---

### Post by flyfisherbryan on 2014-01-04
My whole post was predicated on my policy of taking everything on the internet with a grain of salt (or 2).  But one way or the other everyone here has said something helpful, regardless of bean totals.    I came to Linux via Tor and Tails, then decided to try Ubuntu.  I am reading a ton on Command Line and realize it is just a different dialect I must learn, not an entirely new language.  Thanks again eveyone! :KS

---

### Post by Dave_L on 2014-01-04
> **king.of.random said:**
> I do agree in general with the beans. However if, like myself, the respondent has few beans because they are a new "returner" to Ubuntu, but with years of Linux experience then this isn't necessarily true. It maybe also that the user has years of Ubuntu usage but only recently had time to contribute to the forum. I haven't explored all the options in the profile setup but it might also be an idea to check the respondents background.

As a rule of thumb though, I guess that fewer beans does mean newbie...

You can also take a look at the person's other posts to get an idea of whether his advice is worth trusting. That's what I usually do.

Regarding the original post, "LVM snapshots" might be a solution, if you want to go to the trouble of setting that up.

---

