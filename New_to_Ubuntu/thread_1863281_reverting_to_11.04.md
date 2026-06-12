---
title: "reverting to 11.04"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by keithmac on 2011-10-17
I've recently installed Ubuntu 11.04, dual-booting alongside Vista.  I also installed Ubuntu Tweak which gave me many useful settings options.  I loved the resultant o/s but today I foolishly upgraded to 11.10 - I didn't know the risks...:(

I can live with the new version although I don't like the changes and didn't need any of 'em.  I especially miss the 'Power' setting options I had before - like being able to configure the laptop Power button to 'Suspend' or 'Shut Down', for example. And I liked 'Suspend' without needing a password to log back in.....  Now my questions:

Sticking with 11.10, could I get back all the power setting options I had before?   Can I return to not having to use a password to log in from 'suspend'? 

 If not could I reinstall 11.04 from the Live CD I made?  If so do I just use the Manual partitioning option and delete 11.01 before directly replacing  it with 11.04 in exactly the same partition?

Any other tips and suggestions would be greatly appreciated - I'm an Ubuntu virgin so I need all the help I can get - please! :lolflag:

---

### Post by 11jmb on 2011-10-17
I don't think I can help you with your question about the power options, but you should know that reinstalling from the 11.04 cd will not save your files, applications, or settings. You will need to back them up.

In the future, I recommend not upgrading between stable releases. It is better and less buggy to backup and do a clean install. If you want to check out a new release without committing to the reinstall, keep a small partition on your hard drive to experiment with new operating systems or run the new OS on a virtual machine

---

### Post by keithmac on 2011-10-17
> **11jmb said:**
> I don't think I can help you with your question about the power options, but you should know that reinstalling from the 11.04 cd will not save your files, applications, or settings. You will need to back them up.

In the future, I recommend not upgrading between stable releases. It is better and less buggy to backup and do a clean install. If you want to check out a new release without committing to the reinstall, keep a small partition on your hard drive to experiment with new operating systems or run the new OS on a virtual machine

Having read postings in the main sections earlier today, after the upgrade, I immediately realised my naivete and reached the same conclusions as you've mentioned -  for the next time!!  Clean install when everyone else has found the bugs and they've been sorted - just like Windows!

I'd expected Ubuntu was largely developed and hadn't anticipated major, or pointless minor, changes plus associated bugs.  What a dope!

I'm not concerned about saving files, settings or apps. as I've been using Linux just for fast booting into email, Internet browsing etc.  I have few Ubuntu files as I use Vista for accessing/saving important and historical stuff.

But I'd like someone to reassure me that I know how to clear all the traces of 11.10 before re-installing 11.04 if that's what I have to do.  I'd prefer not to but the lost utilities were important.

---

### Post by keithmac on 2011-10-18
anyone able to help this beginner?

---

### Post by nothingspecial on 2011-10-18
Well if you do a clean install and choose to use the entire drive the installer will format your hard disk leaving no trace of your previous install.

---

### Post by CarlosFerreira on 2011-10-18
> **keithmac said:**
> Having read postings in the main sections earlier today, after the upgrade, I immediately realised my naivete and reached the same conclusions as you've mentioned -  for the next time!!  Clean install when everyone else has found the bugs and they've been sorted - just like Windows!

I'd expected Ubuntu was largely developed and hadn't anticipated major, or pointless minor, changes plus associated bugs.  What a dope!

Please don't take this the wrong way, but a more positive attitude might be to stick with 11.10 and file bug reports on Launchpad. 

There are a number of people who will recommend you to stick only to LTS releases, and that is fine, but I find that ubuntu - and Linux distros in general - are all about taking ownership of the OS. If, like me, you can't write a line of code to save your life, you can at least help with testing and reporting what's wrong and needs fixing. If we all just lay back and wait for someone else to iron the bugs, nobody is going to have nice power option or convenient ubuntu tweaks.

Sorry, rant over.

---

### Post by keithmac on 2011-10-18
> **nothingspecial said:**
> Well if you do a clean install and choose to use the entire drive the installer will format your hard disk leaving no trace of your previous install.

A sledgehammer to crack a nut....

I'm not convinced Ubuntu is that good that I want to wipe Windows off my machine!   No, all I'd like is to revert to or re-install 11.04 or to get back the lost Power Button settings, choose not to use a Password after Suspend and get Flash Player working.  Maybe I should keep waiting for the bug fixes?

But if I _do_ decide I don't want to wait, how do I re-install 11.04 in place of 11.10?  Is it a difficult task?

---

### Post by nothingspecial on 2011-10-18
Ah, I did not realise you had a windows partition.

Start the install process. When you get to the partitioning bit. I think it asks you "How do you want to install Ubuntu?" something like that.

Choose the option "Something else"

Choose your current Ubuntu partition.
Choose to use it as an ext4 journaling file system
Choose a mountpoint of /
Choose to format the partition.

**_[COLOR="Red"]Do not touch the Windows partition[/COLOR]_**

That's it. No need to partition first, just get the installer to use the correct partition.

---

### Post by keithmac on 2011-10-18
> **CarlosFerreira said:**
> Please don't take this the wrong way, but a more positive attitude might be to stick with 11.10 and file bug reports on Launchpad. 

There are a number of people who will recommend you to stick only to LTS releases, and that is fine, but I find that ubuntu - and Linux distros in general - are all about taking ownership of the OS. If, like me, you can't write a line of code to save your life, you can at least help with testing and reporting what's wrong and needs fixing. If we all just lay back and wait for someone else to iron the bugs, nobody is going to have nice power option or convenient ubuntu tweaks.

Sorry, rant over.

I'm brand new to these forums but I can file a bug report if that's what's needed, although I suspect experienced users will have seen and reported before me.  I wasn't laying back so much as wanting to get back to using the system I'd just gotten used to and liked - I have no desire to take ownership of the o/s on my machine as I'm not computer literate.  I teach other subjects elsewhere which occupies much of my time.

 I chose Ubuntu Linux as I mistakenly thought it would be a simple o/s.  And the "nice power option or convenient ubuntu tweaks" were all there and working in 11.04 and dead easy to configure - why bust 'em when a newer version comes in?  I'm not a computer expert, just an ordinary guy.  I like things simple.

Surely what works should be left alone to improve what doesn't?

---

### Post by keithmac on 2011-10-18
> **nothingspecial said:**
> Ah, I did not realise you had a windows partition.

Start the install process. When you get to the partitioning bit. I think it asks you "How do you want to install Ubuntu?" something like that.

Choose the option "Something else"

Choose your current Ubuntu partition.
Choose to use it as an ext4 journaling file system
Choose a mountpoint of /
Choose to format the partition.

**_[COLOR=Red]Do not touch the Windows partition[/COLOR]_**

That's it. No need to partition first, just get the installer to use the correct partition.

THANK YOU - that's what I need.

---

### Post by Mark Phelps on 2011-10-18
> **keithmac said:**
> why bust 'em when a newer version comes in?  I'm not a computer expert, just an ordinary guy.  I like things simple.

Surely what works should be left alone to improve what doesn't?

This basically happens with every Ubuntu release -- some old stuff still works, some doesn't.

Which is why we generally advise folks NOT to so an in-place upgrade, but instead, to create a new partition and install the new version to that.  This way, if you have problems, you still have the older version to rely upon.

---

### Post by grahammechanical on 2011-10-18
> Which is why we generally advise folks NOT to so an in-place upgrade, but instead, to create a new partition and install the new version to that. This way, if you have problems, you still have the older version to rely upon.

+1   It is what works for me.

---

### Post by keithmac on 2011-10-18
> **Mark Phelps said:**
> This basically happens with every Ubuntu release -- some old stuff still works, some doesn't.

Which is why we generally advise folks NOT to so an in-place upgrade, but instead, to create a new partition and install the new version to that.  This way, if you have problems, you still have the older version to rely upon.

Yep I'd picked that up from my recent viewing of these forum discussions and it's what I'll do NEXT time - if only I'd thought about it before, eh? ;)  Thought it was only Microsoft who messed systems up?

ah well, onward and upward - I'll get there :D

thanks for your comments

---

### Post by keithmac on 2011-10-22
> **nothingspecial said:**
> Ah, I did not realise you had a windows partition.

Start the install process. When you get to the partitioning bit. I think it asks you "How do you want to install Ubuntu?" something like that.

Choose the option "Something else"

Choose your current Ubuntu partition.
Choose to use it as an ext4 journaling file system
Choose a mountpoint of /
Choose to format the partition.

**_[COLOR=Red]Do not touch the Windows partition[/COLOR]_**

That's it. No need to partition first, just get the installer to use the correct partition.

thanks again for your help :D

 What is simple and everyday for you would be  unfathomable to me.  After fiddling about with 11.10 this week it was nearly sorted but I was still stuck with certain restrictions so today I followed your guidance and reinstalled 11.04 - now I'm happy because it works in the way I want and, as a bonus, from what I read on these threads I've learned how to configure parts of the system.

I'll toast your health tomorrow.

---

