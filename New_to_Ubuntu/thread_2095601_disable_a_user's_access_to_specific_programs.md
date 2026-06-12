---
title: "disable a user's access to specific programs"
date: 2012-12-17
forum: New to Ubuntu
---

### Post by Charles-2007 on 2012-12-17
I've been using Ubuntu on my PCs for about five years and am evaluating Edubuntu for a school use.  In short, how can I disable a user's access (a user below sudo level) on a PC to specific programs?

---

### Post by cmcanulty on 2012-12-17
I run Ubuntu at a library and also would like to do this

---

### Post by lykwydchykyn on 2012-12-17
Some desktop environments (KDE, XFCE) include a kiosk framework so that you can limit the functions a user can access; this way, could effectively remove the shortcuts to an application and the "run command" or terminal functions from the desktop, and make it impossible for the command to be run.

Looks like Edubuntu now uses Unity, though, and AFAICT there is no kiosk framework for Unity.

There are a couple of other approaches, of course, but they aren't perfect:

- Build up a minimal environment from scratch, providing launchers for only those applications you want users to be able to run.  This requires some knowledge and tinkering, of course.

- Remove execute permissions from the program binaries using chmod, restricting execute to the owner & group only (which is root, so sudo users would be able to run those commands with sudo):
```

sudo chmod a-x /usr/bin/somebinary

```

...or to the admin group (which would allow admins to run them with or withou sudo):
```

sudo chown root:admin /usr/bin/somebinary && sudo chmod a-x /usr/bin/somebinary

```

The basic problem with this approach is that your permissions will likely get "corrected" by updates to the program.  So if you go this route, put the chmod/chown commands in a script and run it after updates.

- Probably the "correct way" to do this is through PolicyKit, but I have no idea how to begin going about that.  There isn't a GUI for policykit anymore either, so it involves hand-configuring some files in /etc/polkit-1/.

---

### Post by Impavidus on 2012-12-17
Making some entries in /etc/sudoers (or including something in /etc/sudoers.d/) should give fine-grained control over who can do what. I've never edited those files myself, so I can't be more specific, but help is available on the web. I'm not sure how things work with putting sudo before commands for which you don't need a password, but the affected users (those who are allowed to use the program) can include that in the launcher or make a bash alias for is.

For some easy coarse control you can set up some groups, set certain programs as executable only for the group and put them in the correct group.```
chmod 750 exam-result-manager
chown root:teachers exam-result-manager
```assuming not everyone is allowed to use the exam result manager.

---

### Post by chadk5utc on 2012-12-17
[http://askubuntu.com/questions/66718/how-to-manage-users-and-groups](http://askubuntu.com/questions/66718/how-to-manage-users-and-groups)

On a larger scale there is LTSP
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

This last one we used in schools worked very well but maybe overkill here.
[http://www.untangle.com/](http://www.untangle.com/)

---

### Post by cmcanulty on 2012-12-17
thanks not easy for sure

---

### Post by Charles-2007 on 2012-12-18
I think it is unfortunate that Edubuntu, an operating system that is "labelled" for education i.e. for children, is so challenging to configure.  I know plenty of kids who left alone for ten minutes (heck, for five!) with an Ubuntu desktop could really get in some trouble.

What would be useful would be blacklist/whitelist controls that don't require a terminal window and a string of sudo commands.

I think I'm going to bail on Edubuntu and go with a kiosk program like IWK or Webconverger (even Chromium OS with a blacklist/whitelist on the browser).

---

### Post by squakie on 2012-12-18
Access rights, and in particular when doing so at a user or group level, has never been easy.  Every operating system I've worked with since "way back when" allowed you to set up access rights, and it takes some planning and thinking to do it right.  I would look at a little wider scope than this one particular instance to see if there isn't more that you may need to do and therefore only do the big work once.

Perhaps you actually would like some sort of menu system, with the menu being built at log in by user and/or group.

---

### Post by chadk5utc on 2012-12-18
I agree with Squakie on this it takes careful planning and thought with any operating system. Most end users never know its even done, they just know what they do at the office or school, whats allowed or not allowed or maybe more so what they can do and whats been blocked. Its called Role-based access control.

---

### Post by lykwydchykyn on 2012-12-18
> **Charles-2007 said:**
> I think it is unfortunate that Edubuntu, an operating system that is "labelled" for education i.e. for children, is so challenging to configure.  I know plenty of kids who left alone for ten minutes (heck, for five!) with an Ubuntu desktop could really get in some trouble.

It is what it is.  I didn't make it, just offering free advice.
> 
What would be useful would be blacklist/whitelist controls that don't require a terminal window and a string of sudo commands.

It would be, and for all I know it may exist.  I'm not aware of it, though.  What would be a shame is if you dumped Edubuntu without [giving this feedback to the actual developers](http://www.edubuntu.org/contact).  They may have a better solution, or it may at least give them some direction on what's lacking from the project.
> 
I think I'm going to bail on Edubuntu and go with a kiosk program like IWK or Webconverger (even Chromium OS with a blacklist/whitelist on the browser).

If you just need a web browser, this isn't too hard to do.  I have some tutorials on my blog, as well as a custom kiosk-oriented browser that I wrote.  I use these quite successfully with LTSP on Ubuntu at a public library to deliver catalog terminals and other browser-based services.  If that sounds useful, I can point you to some resources.  If not, feel free to use what makes you happy.

---

### Post by squakie on 2012-12-19
What happens when they exit the browser? ;)

If a menuing program doesn't exist (I'd be quite surprised), then I could try to build one for you, but it will take me a little while.  It would be driven from files (either by userid at login or by a group of names).

---

### Post by Charles-2007 on 2012-12-24
I've seen your post on kiosk that looks really interesting -- I might give it a whirl if I'm feeling brave.

---

### Post by Charles-2007 on 2013-02-06
SOLVED.  You can look under my forum UserID Charles-2007 to see how I did it (February 2013 revision):

[http://ubuntuforums.org/showthread.php?t=2113023](http://ubuntuforums.org/showthread.php?t=2113023)

Best wishes.

---

