---
title: "Missing project templates in Netbeans on Ubuntu"
date: 2007-05-19
forum: Programming Talk
---

### Post by smartX on 2007-05-19
I am new to Ubuntu and Linux. I installed NetBeans but many of the new project templates were missing. I installed the same version (5.5) on my Windows Vista and it displays all the templates. I reinstalled netbeans several times changed and reinstalled JVMs (I am using java6 now) but to no avail. I tried the .deb packages as well as .bin installations but still no progress. I googled a lot but could only find a few posts with the same problem but no solution. Is this something inherent to linux or am I missing some sort of configuration. I appreciate your help.

---

### Post by haloedrain on 2007-05-20
I'm having the same or at least a similar problem.  When I try to create a new project I have the categories "Sample" and "Standard".  The only project type for "Standard" is "Java Project With Existing Ant Script."  I don't have one of those, so I can't create a new project.  I'm used to seeing quite a few more categories than this on both sides.

I'm also having trouble opening existing project files.  They have the little project icon on them, but when I click to open them the icon changes to a regular folder and I can't open them as a project.

I'm running java 6, Netbeans 5.5.

---

### Post by samjh on 2007-05-20
No problems for me.

It shows all the standard project templates and wizards:

[img]http://img139.imageshack.us/img139/9901/screenshotss4.png[/img]

Are you guys running Compz/Beryl or "Desktop Effects" (actually Compiz)?  If you are, then turn them off.

Otherwise, something is serious kooky with your configuration or installations.  Try downloading the installation binary again, maybe it was corrupted.

---

### Post by haloedrain on 2007-05-20
This is what I get.  It's missing most of the categories and has an extra Standard category.
[IMG]http://img526.imageshack.us/img526/364/screenshotnewprojectdc7.png[/IMG]

I was running Compiz, but Netbeans didn't load at all so I turned it off.  I guess it's a weird configuration issue.  I'll try installing again.

---

### Post by haloedrain on 2007-05-20
After uninstalling completely and reinstalling with a new netbeans download I'm still getting the same problem. ](*,)

Is it possible to create new templates, or add downloaded templates?

---

### Post by samjh on 2007-05-20
If all fails, try using the archive distribution downloadable from this page (bottom half of the page):
[http://www.netbeans.info/downloads/all.php?b_id=2323](http://www.netbeans.info/downloads/all.php?b_id=2323)

Just extract the files to a directory of your own choosing, navigate to the bin directory and run the launcher.

You might even want to compare the files in the archive distribution with the files installed by the binary installer to see if there are any differences.

---

### Post by decimal on 2007-05-21
Try to update netbeans , did the trick for me. 
Go to menu Tools and select Update Manager.

---

### Post by haloedrain on 2007-05-21
Aha!  Brilliant!  I still don't have all the categories I had in windows, but I've got the General category with Java Application now, which is what I really wanted.  Yay!

---

### Post by smartX on 2007-05-21
Still no luck. I ran the update and some of the updates failed. Was there a specific module you updated that gave you the functionality? would appreciate any help.

---

### Post by haloedrain on 2007-05-21
I'm not really sure which one worked, I installed just about all of them except for the ones that had to do with mobile applications or web applications because I don't have the extensions for those ones to work.  So I don't know which one in particular helped.  There was one that had something to do with opening project files, you might try that one.

There was at least one that said the update was already installed and would I like to write over it, and I said yes to all of them.  That might have made a difference too.

---

### Post by smartX on 2007-05-22
Will the updating didn't work for me but something else did. I am posting this for the good of others as it took me quite a while to figure it out.

Solution (does not need un-install), tested on Ubuntu 7.04:

Note: <username> indicates the name of the account you are logged into.

1: locate user dir (Netbeans - Help - About - Details).
for instance:

/home/<username>/.netbeans/5.5



2: remove the .netbeans or - if you have multiple netbeans the 5.5 folder:
for instance [open a terminal] and type (warning custom setting will be lost):

rm /home/<username>/.netbeans


or

rm /home/<username>/.netbeans/5.5



3: start netbeans from a terminal using the --jdkhome option
for instance [open a terminal] and type:

netbeans --jdkhome /usr/lib/jvm/java-6-sun-1.6.0.00



4: now you should be able to launch netbeans normally from now on (using that convinient shortcut in your Applications menu :).

Reference: [http://forum.java.sun.com/thread.jspa?threadID=5112119&tstart=0](http://forum.java.sun.com/thread.jspa?threadID=5112119&tstart=0)
-----------------------------------------------------------------------------------------------
Well number 4 above didn't work out for me so I simply hard coded my launcher to netbeans --jdkhome /usr/lib/jvm/java-6-sun-1.6.0.00
I think the conventional way would be to edit the netbeans.config file but havn't tried that since I can use this method.

Hope this helps out you people. 
Cheers

---

### Post by malfist on 2007-06-10
Go to  Tools -> Module Manager and select the deselected ones that control the package options. I don't remember what they're called but they should be easy to find.

---

### Post by dzinch on 2007-11-05
hi, i spent way too much time on this... i have done everything, what is told here and nothing worked! except when i edited the netbeans config file (etc/netbeans5.5/netbeans.conf). i've changed this line

netbeans_default_userdir="${HOME}/.netbeans/5.5"

into this one:

netbeans_default_userdir="${HOME}/"

that was the trick for me :)

---

### Post by daschmidt on 2007-11-16
I had the same problem, but all the win default projects types appear after I add support to Eclipse projects

```

go at Tools>Update Center;
Select every box and click next;
Look for Eclipse project Importer and Add.
Finish the installation.

```

It is possible to install JBuilder projects importer as well.

---

### Post by pengu on 2007-11-16
i tried everything, and nothing works... 

im using Xubuntu 7.10, netbeans from standard repos

this is so fustrating, now i have to use windows whenever i program in java just because of this stupid problem...

---

### Post by veloce on 2007-11-17
As another data point: I installed netbeans from the gutsy repository.  I then used update manager to add the openoffice.org templates. 

 I have all the project templates available.

(of course the openoffice template won't actually *work* - but it doesn't look like anyone else uses them with netbeans!)

---

### Post by virtualXTC on 2008-05-14
Wow, so much info in one thread.

So I'm guessing most of us:
a) ignored the messages about incorrect paths to files when we first installed netbeans
b) are using compiz

**Problem a** is solved (as smartX pointed out) by in a terminal typing
```

netbeans --jdkhome /usr/lib/jvm/java < tab >

```
and picking the version of the jdk you would like to use.
All of the deletion steps smartX did are unnecessary (though I'm greatful he figured out where the proper path was)

This alone may solve everything, I don't know; I did use the update manager to install some templates.

**Problem B** didn't seem plausible at first as netbeans seemed to be working fine on my machine before updating jdkhome.  Oddly, after updating it wouldn't load anything in the program window.  So with the blank window still open I disabled compiz, sure enough, the program was then properly rendered.  For kicks I re-enabled compiz, and everything still worked!!!  The only glitch I seem to notice is that you cannot pick a specific workspace to put netbeans on, however "move right" works.

:-D

---

### Post by ernz on 2008-11-25
I was getting an error message on NetBeans load. Something about JDK not found or something.

```
sudo aptitude install sun-java6-jdk
```

...fixed that.

As for the missing templates, deleting my /home/ernz/.netbeans directory and restarting NetBeans gave me the missing templates I was after. Not all of the ones on my windows install, but enough for a standard java app

Hope this helps.

EDIT: For the record - I am running NetBeans on 6.0.1 from the standard repositories with compiz working on Hardy Heron.

---

### Post by asesor on 2009-04-07
Well, in my case, i just, create a new proyect with almost the same name, 
and copied all old folders to this new proyect, ater that, when i opened the new proyect it ask by the main class, specifically when i tryied to run it, i just gave it the main class. And it started working normaly just with a little difference in the name, just change it to the old name and that's it working again.  

For certain rason if you move the proyect it lost the main netbean class path.

---

