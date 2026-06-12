---
title: "Interesting going-ons at Gobo Linux"
date: 2007-04-13
forum: Other OS Talk
---

### Post by ThinkBuntu on 2007-04-13
Has anyone here heard about Gobo Linux ([www.gobolinux.org)?](www.gobolinux.org)?) Read what they have to say on the website. An interesting new direction for desktop Linux...

---

### Post by zaratustra on 2007-04-13
I have read something what I don't understand... It is said that it's filesystem is its package manager? I haven't used any drugs recently so I am pretty sure that I am not halucinating... Can someone enlight me?

---

### Post by Hendrixski on 2007-04-13
> **zaratustra said:**
> I have read something what I don't understand... It is said that it's filesystem is its package manager? I haven't used any drugs recently so I am pretty sure that I am not halucinating... Can someone enlight me?

That sounds like a pretty interesting concept. I don't know how well such a system would handle dependencies though.  :-/

---

### Post by justin whitaker on 2007-04-13
> **zaratustra said:**
> I have read something what I don't understand... It is said that it's filesystem is its package manager? I haven't used any drugs recently I am pretty sure that I am not halucinating... Can someone enlight me?

It's pretty straight forward: they modify the kernel so that it allows you to hide large parts of the typical Unix file tree, and install programs into their own dedicated folders.

Open Office, for example, is under /Programs/Open Office 2.2.2 (or something like that). 

That means you can install multiple versions of the same application, and even link and delink it from the user interface on the fly. Uninstalling is simply removing the symlinks and deleting the folder. 

I have been following this for a while...very interesting distro.

---

### Post by ThinkBuntu on 2007-04-13
About the Unix filesystem...Gobo linux uses symbolic links, but is there any reason some very large development project couldn't build a system (as well as packages) that used a more intuitive folder system? Even Apple doesn't have the balls to do this, "ls /" reveals a typical Unix filesystem.

---

### Post by justin whitaker on 2007-04-13
> **ThinkBuntu said:**
> About the Unix filesystem...Gobo linux uses symbolic links, but is there any reason some very large development project couldn't build a system (as well as packages) that used a more intuitive folder system? Even Apple doesn't have the balls to do this, "ls /" reveals a typical Unix filesystem.

No, there isn't. Gobo does the whole Gobohide/symlink thing because they do not have the manpower to completely rewrite every application so that it works with the new file/folder structure. 

The symlinks lets them hide most of the file system, and still compile most apps from source correctly.

---

### Post by Nils Olav on 2007-04-13
> **justin whitaker said:**
> Open Office, for example, is under /Programs/Open Office 2.2.2 (or something like that). 


Programs/Open Office/2.2.2 actually

> **zaratustra said:**
> I have read something what I don't understand... It is said that it's filesystem is its package manager? I haven't used any drugs recently so I am pretty sure that I am not halucinating... Can someone enlight me?

It means that the file hierarchy keeps the packages together oppose to a database.

---

### Post by zaratustra on 2007-04-13
thanks everyone who answered... Finally I found something new:) I think I'll have new friend in vmware, but after exams:)

---

### Post by igknighted on 2007-04-13
Ewww, its a return to the wretched windows file hierarchy!!  Keep it away!

Only partially in gest... I think the separation the *nix based systems have, while tricky for new users to grasp, is more logical in a computing sense.  So sure, it could be changed around like gobo does, but I am not in favor, I prefer the current method.

---

### Post by rai4shu2 on 2007-04-13
Looks to me like your "Programs" folder gets as crowded as a normal "/usr/bin" folder. Not sure what advantage you get out of doing that.

---

### Post by zaratustra on 2007-04-13
Well, if you change something what was developed by "men with big beards", you must know what you do:)) But why would we won't try it even if it is disaster? Other thing is bothering me... How does it handles dependencies?

---

### Post by Nils Olav on 2007-04-13
> **rai4shu2 said:**
> Looks to me like your "Programs" folder gets as crowded as a normal "/usr/bin" folder. Not sure what advantage you get out of doing that.

:-s 

That's definitely not the point.

---

### Post by Nils Olav on 2007-04-13
> **zaratustra said:**
> ... Other thing is bothering me... How does it handles dependencies?

Just like any other package manager, it checks (something tells me that's not what you meant).

---

### Post by toppavak on 2007-04-18
Well, even though the /Programs folder would get relatively crowded, it would still be far easier to find application binaries in it than digging through the many possible locations they could be in the traditional filesystem.

---

### Post by zaratustra on 2007-04-18
Have you heard of "whereis"? 
I tried LiveCD, and I am not so impressed with what I have seen. I am satisfied with current file hierarchy and I won't change distro to have a another one...

---

### Post by Nils Olav on 2007-04-18
> **zaratustra said:**
> Have you heard of "whereis"?...

That doesn't solve much and is more work.

---

### Post by hanzomon4 on 2007-04-18
> **Nils Olav said:**
> That doesn't solve much and is more work.

:confused:

---

### Post by Nils Olav on 2007-04-18
> **hanzomon4 said:**
> :confused:

You know, more typing.

---

### Post by fistfullofroses on 2007-07-27
there is something similar to a package manager "#Compile packagename"
it will resolve dependencies for programs that are known to have a "recipe"
only problem is that there are not enough users and contributors to the project to make
enough "recipes" to make the whole system work properly.

---

### Post by stepan2 on 2007-07-27
is it based on something? If it is comming directly form linux then i would never use it

---

### Post by fistfullofroses on 2007-07-27
it isn't really based on much of anything, it is a totally new tool and totally new distribution. it has some very interesting features, and innovative ideas.

---

### Post by stepan2 on 2007-07-29
i dont think it will go very big because people would have to compile everything

---

### Post by Wiebelhaus on 2007-07-29
> **ThinkBuntu said:**
> Has anyone here heard about Gobo Linux ([www.gobolinux.org)?](www.gobolinux.org)?) Read what they have to say on the website. An interesting new direction for desktop Linux...

your an evil man temping a recovering distro whore.

But it makes great sense.

---

### Post by fistfullofroses on 2007-07-29
Well, if you think the need to compile things will steer people away think again. Compile is totally automated in Gobo, plus they do have packages that can be installed via InstallPackage. And, besides that... think Gentoo, Sabayon, Source Mage, Socerer.

---

