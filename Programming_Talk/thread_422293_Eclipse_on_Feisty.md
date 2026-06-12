---
title: "Eclipse on Feisty"
date: 2007-04-25
forum: Programming Talk
---

### Post by pan69 on 2007-04-25
He guys,

I've installed Eclipse/Tomcat using the instructions on this page: [https://help.ubuntu.com/community/EclipseWebTools](https://help.ubuntu.com/community/EclipseWebTools)

Now, when I try to install the subclipse plugin I get an error message saying "permission denied". I assume it has to do with write permissions on the Eclipse folder. On the instructions page, at some point, they execute this *chown -R root:root eclipse* in the */opt* folder. Ofcourse, I launch Eclipse through a desktop icon under my own user name.

Whats the best way to fix this behaviour?

Thanks!

PS: Now we're on the topic anyways, why are they installing eclipse in the *opt* folder? What does *opt* stand for and why should I install Eclipse and Tomcat there?

---

### Post by md4 on 2007-04-25
Start Eclipse with "sudo eclipse", then you can use the update manager to install/update plugins for eclipse

Hope this helps

---

### Post by pan69 on 2007-04-25
Thanks for your response but it's not really the solution I'm looking for. I guess I need to make the system know that it's OK for my account to install plugins in Eclipse. What would be the best to do that?

---

### Post by Compyx on 2007-04-25
You could do a
```
sudo chown -R <your username> /opt/eclipse
```
that will make /opt/eclipse writable for your user account.

---

### Post by pan69 on 2007-04-25
Cheers mate! That worked like a charm.

With the *chown*, do I do an actual change of ownership of the files (to me) or do I add my ownership with the account that already owned the files? I.e, if I now would do a: *sudo chown -R <some_other_user> /opt/eclipse* would that add an ownership or replace the ownership with the new account?

PS: I like your avatar. :)

---

### Post by phossal on 2007-04-25
The command changes the ownership of the files to you. The net result is that you *or* root can write to them. I'm not a fan of packages, but this is a fairly simple solution. I typically install Java and Eclipse from their respective sites.

[EDIT] To answer your other question, if you change the files to some other user, you will (most likely) not be able to write to them any longer using your personal, non-root account.

---

### Post by charlieg on 2007-04-25
I just installed Eclipse manually in my home dir.  Easier to manage things that way, plus I can run multiple Eclipse installations if I want to try out funky new things without messing with my official development installation.

---

### Post by pan69 on 2007-04-25
Thanks guys!

I run multiple Eclipse installations as well. I found this article on managing plugins for multiple Eclipse installations. Good read.

[http://www.javalobby.org/java/forums/t18678.html](http://www.javalobby.org/java/forums/t18678.html)

---

### Post by phossal on 2007-04-25
Oh my God. That's a lot of work. I much prefer downloading the eclipse tarball and simply *extracting* it. To each his own.

---

### Post by pan69 on 2007-04-25
Yeah I know. The thing is that Eclipse becomes a bit unmaintainable when you install multiple perspectives. I do Flash/ActionScript, Java/J2EE/Web and C/C++ development in Eclipse. I prefer to have all three installations in their on scope because running them from the same Eclipse installation becomes a big mess. The sharing of plugins is excellent because all my installations use e.g. Subclipse for version control. This means that I do not have to install the plugin three times and I only have to update one set of plugins that are shared by all installations.

---

### Post by barmazal on 2007-04-25
> **md4 said:**
> Start Eclipse with "sudo eclipse", then you can use the update manager to install/update plugins for eclipse

Hope this helps

omg never seen it coming

thanks.

---

### Post by mtbosworth on 2007-08-03
Time to revive the thread.  

Here's my issue.  I tried install in Eclipse 3.3 Eurpoa on my ubuntu fiesty box and it ran fine but was acting weird with installing plugins.  Probably, the issue that was originally sited. My question is involving reverting back to 3.2.  I deleted 3.3 and did a reinstallation of 3.2.  If I click on the Eclipse icon it starts opening up and then closes.  If I try to start eclipse from the command line is says:
/usr/bin/eclipse: line 170: /usr/lib/eclipse/eclipse: Permission denied
/usr/bin/eclipse: line 170: exec: /usr/lib/eclipse/eclipse: cannot execute: Permission denied

What's up with that?  It'll start fine if I do sudo eclipse, but I want my account to be able to run Eclipse.  Thanks in advance.

---

### Post by phossal on 2007-08-03
I would install eclipse by extracting it. You can then move it wherever you want, and create menu items as needed. The thread I use for reference is here: [http://ubuntuforums.org/showthread.php?t=332674](http://ubuntuforums.org/showthread.php?t=332674)

---

### Post by mtbosworth on 2007-08-06
I'm trying the manual install, but I'm having difficulties using the filesystem.  I like ubuntu's security, but its annoying trying to copy file around and then you keep getting denied because of permissions.  I decided to install 3.3 so I downloaded the 3.3 tarball from the Eclipse site.  I extract it and try to move it to /usr/lib/eclipse but it won't let me.  May be because the folder currently exists.   Even if I do sudo mv.. it denies me.  Any tips?

---

