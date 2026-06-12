---
title: "Eclipse plugins in /usr/local/lib/eclipse/plugins possible?"
date: 2007-02-07
forum: Programming Talk
---

### Post by elektronaut on 2007-02-07
Hi,

I installed Eclipse from the repository and would like to install plugins into /usr/local/lib/eclipse/plugins. The subdirectories belong to user 'root' and group 'staff'. I don't want to start Eclipse with 'sudo eclipse' each time I want to install a plugin, so I added this line to '/etc/group': ```
staff:x:50:myUserName,root
```Now it seems to work for some plugins, but not for all. I have no clue why the installation of some plugins fails. This is the situation:```
$ ls -la /usr/local/lib/eclipse/
insgesamt 28
drwxrwsr-x  4 root staff  4096 2006-12-29 20:08 .
drwxr-xr-x  6 root root   4096 2006-12-29 20:08 ..
-rwxrwxr-x  1 root staff     0 2006-12-29 20:08 .eclipseextension
drwxrwsr-x 38 root staff  4096 2007-02-08 01:44 features
drwxrwsr-x 30 root staff 16384 2007-02-08 04:30 plugins

```
Could somebody explain me if it should work with the permissions as they are set? I didn't choose 'setgid', don't know how this got here, never used it myself.

---

### Post by phossal on 2007-02-08
> **elektronaut said:**
> I installed Eclipse from the repository and would like to install plugins into /usr/local/lib/eclipse/plugins. The subdirectories belong to user 'root' and group 'staff'. I don't want to start Eclipse with 'sudo eclipse' each time I want to install a plugin, so I added this line to '/etc/group':staff:x:50:myUserName,root

I installed eclipse from the repository myself recently (which I don't always do), and I downloaded the CDT plugin. After extracting the CDT .tar.gz file to my desktop, which produces a folder called eclipse and contains sub folders named features and plugins, I simply used the terminal to copy what I needed. 

For example, to copy the plugins, I either use *sudo nautilus*, or *sudo mv* from the command line. I use sudo obviously to have write permissions into /usr/lib/eclipse (and its sub folders). But I never use eclipse as the root user. All my plugins (like CDT) work for *all* users.

---

### Post by elektronaut on 2007-02-08
Yes, that surely is a working solution. But then I would loose the update functionality.

---

### Post by phossal on 2007-02-08
What update functionality?

---

### Post by elektronaut on 2007-02-08
I mean the Eclipse menu Help -> Software Updates.

---

### Post by phossal on 2007-02-08
I don't think you do. I use the update feature occasionally. Works fine, even when I install plugins myself. And the same is true when I install *eclipse* myself.

---

### Post by lloyd mcclendon on 2007-02-08
> **elektronaut said:**
> I mean the Eclipse menu Help -> Software Updates.

[www.yoxos.com/ondemand](www.yoxos.com/ondemand)

pick your plugins and just extract it to your home directory.  i've been using eclipse on linux for almost 4 years now and this is by far the most painless way.  the yoxos install manager is a very nice piece of work, i can't wait for the next release.

---

### Post by phossal on 2007-02-08
I still don't get it. If eclipse is installed, you can simply copy any plugins and features into the corresponding folders (without eclipse open) using *sudo mv*. You don't need any special permissions, and you don't need to launch eclipse with sudo, and you don't have to put them solely in your home directory.

---

### Post by elektronaut on 2009-06-17
Well, it's been a long time. I guess I didn't explain clearly what I wanted back then. The purpose was to have one central plugin directory to avoid duplication in case of using different Eclipse installations. Just want to let you know that with the new Eclipse versions this seems to be the way to do it:

[http://michaelscharf.blogspot.com/2009/02/p2-how-i-install-plugins-in-extension.html](http://michaelscharf.blogspot.com/2009/02/p2-how-i-install-plugins-in-extension.html)

And adding your user to group staff as mentioned in my first post lets you install plugins without having to start Eclipse as root.

---

