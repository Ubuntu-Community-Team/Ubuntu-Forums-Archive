---
title: "unable to locate package : ("
date: 2011-11-22
forum: New to Ubuntu
---

### Post by Gojira on 2011-11-22
Hello,

As I am trying to install a package I get the following error:

lucian@ubuntu:~$ sudo apt-get install ros-electric-care-o-bot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ros-electric-care-o-bot


I have do mention that I did execute before:

lucian@ubuntu:~$ sudo apt-get update

and it worked

(I use WuBI, if that has any importance at all)

Could somebody help, please?

---

### Post by hhh on 2011-11-22
I have no idea what that software is, but it looks like you have to install it from a third-party source...
[http://www.ros.org/wiki/Robots/Care-O-bot/electric](http://www.ros.org/wiki/Robots/Care-O-bot/electric)

If you use Ubuntu 11.10, post back and maybe someone can help you to compile it.

---

### Post by F.G. on 2011-11-22
i guess you need to add the correct repository to the sources list. you can do this by opening up synaptic, going to settings > repositories and adding the third party repo.
sorry i've no idea what that is for 'ros-electric-care-o-bot'.
once you've done that running:

sudo apt-get update
and
sudo apt-get install ros-electric-care-o-bot

should work.

---

### Post by Gojira on 2011-11-22
Hello, 

Thanks for the replies.
I do use ubuntu 11.10. Still, i have went through all that is written in the tutorial, and still no results.
As a am newbie in Linux, I don't really know what a third-party repositoy looks like.

Is it enough to do what is told on :

[http://www.ros.org/wiki/Robots/Care-O-bot/electric](http://www.ros.org/wiki/Robots/Care-O-bot/electric) ?

But anyway it doesn't work so...

what should I do?

---

### Post by beew on 2011-11-22
> **Gojira said:**
> Hello, 

Thanks for the replies.
I do use ubuntu 11.10. Still, i have went through all that is written in the tutorial, and still no results.
As a am newbie in Linux, I don't really know what a third-party repositoy looks like.

Is it enough to do what is told on :

[http://www.ros.org/wiki/Robots/Care-O-bot/electric](http://www.ros.org/wiki/Robots/Care-O-bot/electric) ?

But anyway it doesn't work so...

what should I do?

It looks like they haven't set up a repository for 11.10 (see point 1.2, the repositories are for 10.04, 10.10 and 11.04)

---

### Post by bluexrider on 2011-11-22
You are unable to get the required software because is hasn't been made available for your OS yet.

---

### Post by sandyd on 2011-11-22
Glut3 was replaced by freeglut.

[https://launchpad.net/ubuntu/oneiric/amd64/libglut3-dev/3.7-25](https://launchpad.net/ubuntu/oneiric/amd64/libglut3-dev/3.7-25)

Interestingly enough, oneiric is in the repo, but theirs [no ros-electic-care-o-bot package]("http://packages.ros.org/ros/ubuntu/pool/main/r/ros-electric-care-o-bot/")???

---

### Post by lolpenguin on 2011-11-23
Whoops, the package is not in any repository available in your software sources. Find a third-party repository (Personal Package Archive) which contains the software and add it to software sources, and it should work. Try searching [launchpad.net]("https://launchpad.net") for a PPA.

---

### Post by Gojira on 2011-11-23
Ahm, this is embarassing, but I don't fully understand your answer. Do you mean searching the software with something like Synapse and download it?

I've already done that but it didn't work. Could I have done it wrong?

Thanks for the previous answers

---

### Post by Serpher on 2011-11-23
Sandyd's solution would be the easiest. Click [here](http://packages.ros.org/ros/ubuntu/pool/main/r/ros-electric-care-o-bot/), and download the .deb file that is for your version of Ubuntu (Natty, Lucid etc etc) and your processor architecture being AMD (amd64) or Intel (i386). When you have the .deb just double click it and follow the on screen instructions. It's really easy.

---

### Post by beew on 2011-11-23
> **Serpher said:**
> Sandyd's solution would be the easiest. Click [here]("http://packages.ros.org/ros/ubuntu/pool/main/r/ros-electric-care-o-bot/"), and download the .deb file that is for your version of Ubuntu (Natty, Lucid etc etc) and your processor architecture being AMD (amd64) or Intel (i386). When you have the .deb just double click it and follow the on screen instructions. It's really easy.

There is NO solution because the program is not available for 11.10. Look at the .debs, none of them is for oneiric.

@Op, sorry, there is no solution, we are just trying to tell you that the program doesn't have a version for 11.10 at the moment. You may have to wait a few weeks for them to package it, this is one reason that I never install the latest Ubuntu release without waiting a few months.

---

### Post by Gojira on 2011-11-24
Thanks Beew and all the others. I shall reinstall an older version of Ubuntu und come with other questions laters =)

---

