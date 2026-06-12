---
title: "Where is the Applications folder in 11.10?"
date: 2011-12-21
forum: New to Ubuntu
---

### Post by Archdeacon on 2011-12-21
I am an absolute beginner, having installed Ubuntu 11.10 3 days ago. I cannot find either the System or Applications folder! My userid has 'Administrator' rights. I downloaded the Gnome Log File viewer which installed OK but I cannot find it!

---

### Post by -nat- on 2011-12-21
Welecome to Ubuntu!

I'm not entirely sure what you mean by System or Applications folders, however, if you just want to launch the app you need to go into the dash, which is done by clicking on the Ubuntu logo at the top-right of your screen. From here you can either navigate through the list of apps to the one you want, or type its name into the search bar. Click on an app to launch it.

There's more info [here]("https://help.ubuntu.com/11.10/ubuntu-help/unity-dash-intro.html").

---

### Post by anewguy on 2011-12-22
There is no single "System" folder in Linux.  All kinds of things that make up the Linux system are in different folders - kernel in 1, binaries for system tools, etc., in more than 1, documentation in more than 1, etc..

If you're coming from Windows and trying to find equivalents in the Linux file hierarchy, you need to know the file system in Linux is very different and you should look online for one of the guides.  If you are coming from a MAC I'm afraid I can't help you - we had MAC's at work, but someone else supported those.


Dave ;)

---

### Post by Paqman on 2011-12-22
> **Archdeacon said:**
> I cannot find either the System or Applications folder!

Older versions of the Gnome desktop interface had a top panel with three drop-down menus: "Applications", "Places" and "System". If you follow old guides or screenshots that's what it will probably show. 

Recently this all changed, and in Ubuntu you now launch applications or system tools by either hitting the big Ubuntu button on the launcher on the left or by hitting the Windows key. You then start to type the name of what you're looking for and it should come up. Stuff you use a lot can be pinned to the launcher by right clicking on the icon once it's running.

---

### Post by Archdeacon on 2011-12-22
OK Thank you all for the replies - I clicked the Dash Home button and eventually wound up at the right point and found the Gnome Log File Viewer; only problem is it shows a blank screen! Do I need to point it somewhere?

---

### Post by agillator on 2011-12-22
Here is a link that will give you a somewhat detailed explanation of the suggested organization of the file system on Linux: [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html). As pointed already, there is no 'Applications' or 'System' folder. Sometimes it can be a trick to find something when you have just installed it. The 'find' command is useful there, as well as 'whereis' and 'locate'. Use the 'man' command (e.g. 'man find') to get information on how to use the commands. 

To add to the confusion, where things go often depends on your source of installation. For example, if you install the Apache web server by compiling it from source all its files will probably end up in /usr/local/apache2 although you can put them anywhere. On the other hand, if you install the server through aptitude (or apt-get or whatever) the files will be scattered throughout the system: configuration files in /etc/apache2, log files in /var/log/apache2, web pages in /var/www, system files in /usr/lib/apache2, and so on. Confusing at first but it eventually begins to make some sense. 

Hope this helps. Mentioning where you are coming from, I would guess Windows, might help others understand the context of your question.

---

### Post by MartijnNL on 2011-12-22
Like Paqman says: the OP is probably talking about the old applications menu, not about directories in the filesystem. So let's not make it more complicated by trying to explain the filesystem hierarchy. Although this may be useful knowledge at some point.

Archdeacon, you might want to have a look at this: [http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

I assume that's the program you mean? I haven't worked with it myself yet.

---

### Post by anewguy on 2011-12-22
> **Paqman said:**
> Older versions of the Gnome desktop interface had a top panel with three drop-down menus: "Applications", "Places" and "System". If you follow old guides or screenshots that's what it will probably show. 

Recently this all changed, and in Ubuntu you now launch applications or system tools by either hitting the big Ubuntu button on the launcher on the left or by hitting the Windows key. You then start to type the name of what you're looking for and it should come up. Stuff you use a lot can be pinned to the launcher by right clicking on the icon once it's running.

Good catch!  It didn't even cross my mind the OP was talking about menu options!  I'm running on a 20-watt bulb again ;)

Dave ;)

---

### Post by asuastrophysics on 2012-06-24
@Archdeacon

In the filesystem, the "applications" folder can be found here:
```
/usr/share/applications/
```
This contains the majority of the programs installed on your computer, much like the "Applications" folder in OSX also does. :p

Cheers

---

### Post by coffeecat on 2012-06-24
I know this thread is only 6 months old, but the OP, Archdeacon, has not logged in since they posted the second time and, as others have said, they were probably asking about the Applications menu, not the file structure. 

Thread closed.

---

