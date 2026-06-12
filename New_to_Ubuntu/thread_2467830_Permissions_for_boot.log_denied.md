---
title: "Permissions for boot.log denied"
date: 2021-10-08
forum: New to Ubuntu
---

### Post by deads2 on 2021-10-08
Hi there,

I'm completely new to Linux. I'm quite a noob when it comes to computing skills in general. *But finally taking the time to educate myself as I am aiming to pursue a career in this field*.

So I only downloaded Ubuntu a couple of days ago on Virtualbox and this morning decided to have a little play around.

I found myself in the /var/log directory and decided I wanted to take a look at the boot.log file, however, permission was denied.

I've tried google searching for answers, but I'm struggling to find any coherent information that makes sense to me (being a beginner).

Any help would be appreciated.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289250&stc=1[/IMG]

---

### Post by psychohermit on 2021-10-08
Try sudo cat boot.log|less

--glenn

[edit]
my boot.log is zero length but boot.log.1 was interesting.
[/edit]

---

### Post by ActionParsnip on 2021-10-09
The boot.log file isn't readable by your user. You can check permissions with
```

ls -la /var/log/boot.log

```
So, as psychohermit says, you will need to prefix with sudo.

---

### Post by yancek on 2021-10-09
>  I've tried google searching for answers, but I'm struggling to find any  coherent information that makes sense to me (being a beginner).


I don't know what you used in your search but, you should be able to find something to help.  Remember that Linux/Ubuntu is a multiuser system so it will always have (by default), 2 users.  In your post, you show a user 'Jake'.  The images you posted show you are logged in as user Jake so you don't have permission to access those files as 'Jake' and that was explained in the other posts.

Using Linux, a standard user generally will not have access to write to anything outside his/her home directory.  Using sudo is explained at the site at the link below which is an official Ubuntu Documentation site and it is essential for an Ubuntu user to understand.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You can also use the 'man' command to get info on various commands, in this case type:  man sudo in a terminal and you will get pages of explanations of the command sudo.  You can use man to get an explanation of any Linux command.  In my experience, the man pages are often cryptic or difficult to understand for a new user. but I would try that before googling it.

When I go to the /var/log directory on my Ubuntu 20.04 using the file manager, I see a red x on some of the.  That means trouble ahead as you found.  Using a terminal and running the command below gets you to the /var/log directory:

 cd /var/log/

and the command below shows only root has access to that file
 ls -l boot.log
-rw------- 1 root root 0 Oct  9 05:55 boot.log

Generally, user will have access to at least read files  outside the user home directory but not always, as you have found.  I don't know why the boot.log file is not available to read by a normal user when other files in that directory are but, I'm sure there is a logical reason and someone will likely post the answer.  

Good luck and enjoy Ubuntu.

---

### Post by him610 on 2021-10-09
> I'm completely new to Linux. 
You need to read up on Linux, or at least have a link to a good reference.
[https://linuxcommand.org/tlcl.php]("https://linuxcommand.org/tlcl.php")

---

### Post by grahammechanical on 2021-10-10
I am not speaking with the authority of a Linux developer. Far from it.

Boot log files are not created by the user. Being a file of boot messages they are created by Linux as the root user before the user (you and me) is logged in. They are therefore owned by root. How could it be otherwise? And so we need to elevate the priviledges or permissions of the user to access them.

Regards

---

### Post by TheFu on 2021-10-10
> **him610 said:**
> You need to read up on Linux, or at least have a link to a good reference.
[https://linuxcommand.org/tlcl.php]("https://linuxcommand.org/tlcl.php")

+1.  Good book with topics covered IN THE CORRECT ORDER.  Learning things in the correct order means you'll have the background as skills build on previously learned skills and understanding.  Otherwise, the connections won't be made and things will seem thrown together and much harder to learn.  But with the connections, in the proper order, the pieces will fit and things will connect, so the puzzle gets filled in with each new topic and the different aspects of early topics make more and more and more sense. There is an elegance to Unix.  As understanding becomes deeper, you'll be able to do things that nobody taught, but because you understand how things work internally, that the new idea you have will work. 

Stamp out *cat* abuse!!!

Don't do this:
```
 sudo cat boot.log|less
```
Why not?
[LIST]
[*]cat isn't needed. Using it is wasteful.
[*]the file specified assumes it is in the current directory - it is not. Actually, my 18.04 system doesn't have a file named "boot.log" at all.
[*]use less /var/log/bootstrap.log
[*]bootstrap.log doesn't need sudo to read.
[/LIST]
On 20.04, and perhaps later releases, there is a /var/log/boot.log ... that appears to be rotated and compressed at boot.
```
$ ll /var/log/boot.log*
-rw------- 1 root root  7521 Oct 10 11:44 /var/log/boot.log
-rw------- 1 root root  7614 Oct  3 00:00 /var/log/boot.log.1
-rw------- 1 root root  7824 Sep 28 00:00 /var/log/boot.log.2
-rw------- 1 root root  7889 Sep 19 00:00 /var/log/boot.log.3
-rw------- 1 root root  7922 Sep 12 00:00 /var/log/boot.log.4
-rw------- 1 root root 15692 Sep  9 00:00 /var/log/boot.log.5
-rw------- 1 root root  7235 Aug 30 00:00 /var/log/boot.log.6
-rw------- 1 root root  7472 Aug 22 00:00 /var/log/boot.log.7
```
That output tells me that sudo is necessary.
**sudo less /var/log/boot.log**
is the command to use.  Whenever someone types cat, they are probably wasting 2 extra, unneeded, processes.  It is wasteful and unnecessary. Nearly all of the programs like less, more, grep, and 99.99999999999999999% of the others accept a filename as input.

less is what we call a PAGER.  more is another.  By setting an environment variable, PAGER=less, you'll have less used by all programs that want to show stuff a page at a time. I generally prefer less over more, because it allows going backwards in the buffer, not just forwards.  There's 1 thing I dislike about less (the default settings) and that is that it clears the screen when it is done. More leaves the screen content alone. There are times when both modes are useful.

Stamp out *cat* abuse!!!

---

### Post by deads2 on 2021-10-17
I used the sudo command and it worked, so thankyou!


> **him610 said:**
> You need to read up on Linux, or at least have a link to a good reference.
[https://linuxcommand.org/tlcl.php](https://linuxcommand.org/tlcl.php)

I was looking for a good Linux guide. Will read this book.

To everyone who responded to my question, thankyou very much. I can tell that this forum has a bunch of knowledgeable people, which is great because I'm keen to make Linux second nature to me. I already enjoy using. Next time I hope my question isn't so basic.

---

### Post by ActionParsnip on 2021-10-17
[https://ubuntuhandbook.org/](https://ubuntuhandbook.org/)

May help. Personally I'd say just use the OS which I'm guessing is how you learned Windows

---

### Post by TheFu on 2021-10-17
> **ActionParsnip said:**
> [https://ubuntuhandbook.org/](https://ubuntuhandbook.org/)

May help. Personally I'd say just use the OS which I'm guessing is how you learned Windows

This is how many people do it. After a few years, they just start learning about their blind spots because they missed huge parts of "basic Unix background" that a solid book will cover.
I find it amazing that in the first week, people don't have to learn Unix permissions - at least 80% of them - just to get along.  That is such a core aspect to using and understanding how all Unix systems actually work.  I've come across people in these forums who have been end-users of Ubuntu for over a decade, yet don't understand permissions. Seems completely crazy to me.

And to understand permissions, userids and groupids need to be understood.  In my classes, the first 3 sessions do a little background, how to login, about 20 basic command, then we do users, groups, and permissions.

---

