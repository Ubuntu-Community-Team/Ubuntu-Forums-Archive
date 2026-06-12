---
title: "Cannot update anything, Help please"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by craigrobbo on 2013-04-27
Hey guys.

I tried to update my intel drivers today because I am having some graphical issues with games.

on intel driver update it starts to update and I get this error:


```
W:Failed to fetch http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu/dists/quantal/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```


Now, I have tried changing the repositories from UK to main but it made no difference.

When I use Ubuntu update manager (software updater) I get this:

```
Failed to download repository information

Check your Internet connection.


Details:
W:Failed to fetch http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu/dists/quantal/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

Now To adress a few simplties.

I am connected to the internet and every other internet related feature works flawlessly. 

I asume somewhere its having issues connecting to the repository servers but thats the part i am stuck with.

All help is MASSIVLEY appreciated.

Craig

---

### Post by ibjsb4 on 2013-04-27
There is no 12.10 release, you need to remove it.

[http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu/dists/](http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu/dists/)

---

### Post by craigrobbo on 2013-04-27
Thanks for that.

When you say remove it, i am unsure what you mean sorry - Remove what?

Am I limited to updating my graphics drivers at this time?

Craig

---

### Post by ibjsb4 on 2013-04-27
ppa.launchpad.net/paullo612/unityshell-rotated

Has no package for Quantal 12.10, the last package built was for precise 12.04.

Open up software sources and either remove or just uncheck it.

[ATTACH=CONFIG]241877[/ATTACH]

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by snowpine on 2013-04-27
One of the ways new users get in big trouble is by adding a bunch of random, unsupported software to their system.

[http://ppa.launchpad.net/paullo612/unityshell-rotated](http://ppa.launchpad.net/paullo612/unityshell-rotated) is **not** an appropriate software source for your Ubuntu 12.10 install. Don't use it. Here are instructions for managing your software sources: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Ubuntu includes intel video drivers out-of-the-box. No extra steps are necessary and you do not need to add any software sources to run Ubuntu on intel graphics. 

I notice that you have already started a thread about your gaming graphics issue, that is a good start. But you didn't identify your hardware in that thread: computer manufacturer, model number, video chipset, type of monitor, type of connection, etc. so you should definitely add that information to the other thread if you want good advice. :)

If you are ever unsure about whether or not installing particular software on your Ubuntu is a good idea or a bad idea, **ask first** on these forums. We will give you good advice. :)

---

### Post by computerandu on 2013-04-27
> **craigrobbo said:**
> Thanks for that.

When you say remove it, i am unsure what you mean sorry - Remove what?

Am I limited to updating my graphics drivers at this time?

Craig

As you can see in the error, you are trying to use PPA paullo612/unityshell-rotated

But as stated by ibjsb, this PPA has no version available for 12.10. As you can see in the link: [http://ppa.launchpad.net/paullo612/u.../ubuntu/dists/]("http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu/dists/")

Now, while updating, it tries to get the files from a address which doesn't exist. To fix it, you need to remove this non-working PPA.

More details about this kind of problem: [http://itsfoss.com/failed-to-download-repository-information-ubuntu-13-04/](http://itsfoss.com/failed-to-download-repository-information-ubuntu-13-04/)

Read this detailed article on [how to delete a PPA in Ubuntu]("http://itsfoss.com/how-to-remove-or-delete-ppas-quick-tip/").

---

### Post by craigrobbo on 2013-04-27
Hey guys.


ibjsb4's solution worked removing that package - That was something I had tried a while back.

As for the gaming, Its an intel HD 4000 graphics card Intel Dual core processor and 4Gb ram, not the best - However on windows it did play Half life at a reasonable/playable level - however on linuxx the into screen is upside down(weird) with a green line through it and I get all sounds of the menu but nothing shows.

I also have a similar issue when running compiz 3D windows whereby they go black or just blocky and dont move at all.

Again I really appreciate the help a lot guys.

---

### Post by snowpine on 2013-04-27
You should add those details to your "weird graphics problems" thread. Good luck! :)

---

### Post by ibjsb4 on 2013-04-27
Yep, one problem down :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

