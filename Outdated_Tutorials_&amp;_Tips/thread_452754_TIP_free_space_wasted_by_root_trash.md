---
title: "TIP: free space wasted by root trash"
date: 2007-05-23
forum: Outdated Tutorials &amp; Tips
---

### Post by dbbolton on 2007-05-23
If you're using GNOME, run this command:
```
gksudo nautilus '/root/.Trash/'
```you might not see anything, or, if you're like me, you'll see about 2 000 files. you'll probably want to delete them or simply "empty" the trash.

i suppose that anything you delete while running nautilus as root goes there. like an idiot, i had assumed that such things would just go in '~/.Trash'

i've been using ubuntu for about a year now, and just realised this. it may seem like common sense, but if it could happen to me, it could happen to you.

EDIT:

If you're using Xfce, run this:

```
gksudo thunar
```

Then click on "Trash."

---

### Post by sehe on 2007-06-09
noli me castigare baculo; nec te videtus ero

---

### Post by wie6Ein0 on 2007-06-10
Wow... I also did not know this. I'm glad that you started this thread.

Fortunately, I only have 28 files there, totaling at about 80 MB.

---

### Post by mhenriday on 2007-06-14
When I entered the command and pressed «Enter», the following appeared on my terminal screen
> mhenriday@mhenriday-desktop:~$ gksudo nautilus '/root/.Trash/'
(nautilus:19211): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.4

ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device

...

ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
mhenriday@mhenriday-desktop:~$ gksudo nautilus '/root/.Trash/''
i e, about thirty lines of what looked to me very much like «trash», while at the same time a small window opened which informed me that 'root/.Trash/' couldn't be found and that I should check the spelling. When, nevertheless, I repeated the command without changing anything, I got the same message, but none of the «trash» seen above appeared on my terminal screen. Am I justified in assuming that I have in fact, all these messages to the contrary, succeeded in emptying the trash ?...

Henri

---

### Post by dbbolton on 2007-06-14
> **mhenriday said:**
> When I entered the command and pressed «Enter», the following appeared on my terminal screen

i e, about thirty lines of what looked to me very much like «trash», while at the same time a small window opened which informed me that 'root/.Trash/' couldn't be found and that I should check the spelling. When, nevertheless, I repeated the command without changing anything, I got the same message, but none of the «trash» seen above appeared on my terminal screen. Am I justified in assuming that I have in fact, all these messages to the contrary, succeeded in emptying the trash ?...

Henri
i was able to duplicate this problem. apparently, the directory /root/.Trash/ isn't created until the first time you delete something while using nautilus as root. so, in other words, your "root trash" didn't exist yet. as soon as you delete something as root, it will be created automatically.

---

### Post by mhenriday on 2007-06-14
> **dbbolton said:**
> i was able to duplicate this problem. apparently, the directory /root/.Trash/ isn't created until the first time you delete something while using nautilus as root. so, in other words, your "root trash" didn't exist yet. as soon as you delete something as root, it will be created automatically.

My impression was that by the very act of entering the command```
gksudo nautilus '/root/.Trash/'
``` I was, in fact, deleting something as root. Is this a misunderstanding ? In that event, how can I then «delete something while using nautilus as root» ?...

Henri

---

### Post by dbbolton on 2007-06-14
> **mhenriday said:**
> My impression was that by the very act of entering the command```
gksudo nautilus '/root/.Trash/'
``` I was, in fact, deleting something as root. Is this a misunderstanding ? In that event, how can I then «delete something while using nautilus as root» ?...

Henri
that command just launches Nautilus as root, and opens root's trash folder. 

as a general rule, you should NOT delete things while root, as you could damage your system. if you don't have the permissions to delete a certain file, and must delete it as root, then you can launch 'gksudo nautilus', browse to the file, and right-click on it and delete it. then, it will be an the /root/.Trash/ folder.

this is tip was intended for people who have deleted things with nautilus as root, then didn't know that the "deleted" files were still on their computer/where they had gone. it was NOT intended to tell people to start using nautilus as root to delete things.

---

### Post by mhenriday on 2007-06-15
Thanks, **dbbolton**, for the explanation ! If you don't mind, I'd like to pursue this matter a bit further. The files that appear on my terminal after executing the command are mainly of the following type :```
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
``` and look very much like trash to me. Can they be safely removed by right-clicking  and then deleting them and are there any advantages - saved space, etc - to doing so ?...

Henri

---

### Post by dbbolton on 2007-06-15
> **mhenriday said:**
> Thanks, **dbbolton**, for the explanation ! If you don't mind, I'd like to pursue this matter a bit further. The files that appear on my terminal after executing the command are mainly of the following type :```
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
``` and look very much like trash to me. Can they be safely removed by right-clicking  and then deleting them and are there any advantages - saved space, etc - to doing so ?...

Henri
does nautilus open at all after you type the command?

---

### Post by mhenriday on 2007-06-15
> **dbbolton said:**
> does nautilus open at all after you type the command?

Three things happen when I type the command into a terminal.
[LIST=1]The following appears in the terminal :
> mhenriday@mhenriday-desktop:~$ gksudo nautilus '/root/.Trash/'
Initializing gnome-mount extension
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.4

ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
[*]A window showing files under **root **appears
[*]A warning to the effect that **"/root/.Trash"** could not be found appears, and I am admonished to check my orthography.
[/LIST]
On the other hand, when I click the **nautilus** icon on my upper panel, a window showing files under my **home folder** appears ! Thus I don't really know how to answer your question ; _something_ certainly happens when I execute the command, but not exactly that which happens when I open **nautilus** by clicking the icon. I must confess that I find myself utterly confused - par for the course !...

Henri

---

### Post by dbbolton on 2007-06-15
> **mhenriday said:**
> Three things happen when I type the command into a terminal.
[LIST=1]The following appears in the terminal :

[*]A window showing files under **root **appears
[*]A warning to the effect that **"/root/.Trash"** could not be found appears, and I am admonished to check my orthography.
[/LIST]
On the other hand, when I click the **nautilus** icon on my upper panel, a window showing files under my **home folder** appears ! Thus I don't really know how to answer your question ; _something_ certainly happens when I execute the command, but not exactly that which happens when I open **nautilus** by clicking the icon. I must confess that I find myself utterly confused - par for the course !...

Henri
the text that appears in the terminal under no. 1 can be ignored. what you listed under no. 2 is nautilus- it's the file browser. the warning you describe in no. 3 appears because you haven't deleted anything as root, thus you don't have a root trash.

'root' is actually a different user for your computer. when you normally run commands, you run them as yourself. when you put sudo or gksudo in front of a command, you are running the command as root. 

even system administrator accounts have limits. however, the root, or superuser, can do pretty much anything. that's why you need to be very careful when doing things as root.

---

### Post by mhenriday on 2007-06-16
> **dbbolton said:**
> the text that appears in the terminal under no. 1 can be ignored. what you listed under no. 2 is nautilus- it's the file browser. the warning you describe in no. 3 appears because you haven't deleted anything as root, thus you don't have a root trash.

...



Thanks, **dbbolton**, for your kind explanation ! From what I have seen the difference between using the ordinary file browser command in the upper panel and accessing **nautilus** via the gksudo command seems to be that the latter can be used to access files in **root**. In fact, playing around a bit, I discovered that by typing ```
gksudo nautilus '/root/'
``` without the .Trash argument, I get the same file-browser window, without that annoying warning. The only thing that then appears as a folder under **root** is **desktop**, and when I click **desktop**, I find it empty. So the conclusion must be, precisely as you indicate, that I don't have a **trash** folder under **desktop**. But then again, seeing as no files seem to be stored under **root,** I don't really seem to need one, either. Or have I, in my ignorance missed something important along the way ?...

Henri

---

### Post by dbbolton on 2007-06-16
> **mhenriday said:**
> Thanks, **dbbolton**, for your kind explanation ! From what I have seen the difference between using the ordinary file browser command in the upper panel and accessing **nautilus** via the gksudo command seems to be that the latter can be used to access files in **root**. In fact, playing around a bit, I discovered that by typing ```
gksudo nautilus '/root/'
``` without the .Trash argument, I get the same file-browser window, without that annoying warning. The only thing that then appears as a folder under **root** is **desktop**, and when I click **desktop**, I find it empty. So the conclusion must be, precisely as you indicate, that I don't have a **trash** folder under **desktop**. But then again, seeing as no files seem to be stored under **root,** I don't really seem to need one, either. Or have I, in my ignorance missed something important along the way ?...

Henri
the command you mentioned
```
gksudo nautilus '/root/'
```

is like telling your computer "open the folder called '/root' with Nautilus as the superuser."

let me give you an example scenario. let's say that i write a small program and i want to move it to the '/usr/bin' folder, but i don't have the permissions to put files in that folder. i could then launch nautilus as superuser and drag my program to the folder where i want it.

later on, i decide that i want to delete that program. so, i launch nautilus as superuser, browse to /usr/bin, and right click on my folder, then click "move to Trash" (or 'move to Delete Items folder' in some cases). once i do that, my program isn't really deleted, it has just been moved to root's trash folder, which is located at '/root/.Trash'.

when i delete files as myself, they will be put in my trash, which is located at '~/.Trash' or '/home/daniel/.Trash'

---

### Post by mhenriday on 2007-06-19
And my home-user trash can be emptied by clicking the wastebasket icon on the desktop. Thanks, for your patience, **dbbolton**, and your explanations ; I now think I understand what's going on....

Henri

---

### Post by mcgerard on 2007-12-06
Thanks **DBBOLTON**. I spent days trying to recover disk space and to see where my deleted files had gone to. After finding your post, I had it sorted out in 5 minutes. Recovered several GB of space.

---

### Post by muskratmx on 2007-12-08
Correct me if I'm wrong!

> this is tip was intended for people who have deleted things with nautilus as root, then didn't know that the "deleted" files were still on their computer/where they had gone. it was NOT intended to tell people to start using nautilus as root to delete things.

Delete and trash/recycle bin in Linux are two different things.

When you delete it's gone no need to empty the trash wither you delete as user or root. But when you trash an item then it goes to the trash bin, which later will need emptied.

---

### Post by Rogar on 2007-12-08
Thanks. I deleted stuff (as root) a couple weeks ago. It said the files were being sent to trash, but of course the desktop trash didn't show them. I am no longer confused!

---

### Post by dbbolton on 2007-12-09
> **muskratmx said:**
> Correct me if I'm wrong!



Delete and trash/recycle bin in Linux are two different things.

When you delete it's gone no need to empty the trash wither you delete as user or root. But when you trash an item then it goes to the trash bin, which later will need emptied.

it should read:

this is tip was intended for people who have *moved things to the trash* things with nautilus as root, then didn't know that the "deleted" files were still on their computer/where they had gone. it was NOT intended to tell people to start using nautilus as root to delete things.

---

### Post by muskratmx on 2007-12-09
> this is tip was intended for people who have *moved things to the trash* things with nautilus as root, then didn't know that the "deleted" files were still on their computer/where they had gone. it was NOT intended to tell people to start using nautilus as root to delete things.

But your mixing the two words "Trash" and "Delete".

In Nautilus when you right click an item to remove it. You may either choose "trash" or "delete", as a user or as root, makes no difference. All through this thread folks have said "I deleted then need to empty trash" and that is incorrect.

Yes in the MS world that would be correct, but in Linux if you "Delete" you bypass the trash bin and there is no return. No need to empty trash.

I aggree people should not be deleting items as root unless they absolutly need to. But at the same time, if I want to redeem disk space, placing items in the trash is just double work. I have to remove it twice, once from my workspace, then from my recycle bin.

MS forces one to do that. With Linux one has a choice, 

"Delete" or "Trash"

---

### Post by bionnaki on 2007-12-09
there is no such directory .Trash in Root

---

### Post by muskratmx on 2007-12-09
> there is no such directory .Trash in Root

You are correct! If you haven't trashed anything as "Root" yet. The frist time you trash an item as root it will be created. Mind you "trash" not delete as root.

---

### Post by furytheory on 2009-01-19
I was having a similar problem deleting my trash, it kept telling me that I didn't have permission to delete this one directory "os". So I found this thread and was trying to enter the commands, but there was no trash at the .nautilus directory, so here is what I did:
-----------------------------------------------------------------------
[FONT=Trebuchet MS][COLOR=DimGray]11:25:54[dan:/root]$[COLOR="Green"] locate Trash[/COLOR]
/home/dan/.local/share/Trash
/home/dan/.local/share/Trash/files
/home/dan/.local/share/Trash/info
/home/dan/.local/share/Trash/files/os
/home/dan/.local/share/Trash/info/os.trashinfo
/home/dan/.local/share/Trash/info/s5030787.jpg.trashinfo
/home/dan/.local/share/Trash/info/s5030788.jpg.trashinfo
[COLOR=Red]... there was more ...
... a whole lot more ...[/COLOR]
11:26:05[dan:/root]$ [COLOR="Green"]cd /home/dan/.local/share/Trash[/COLOR]
11:34:53[dan:~/.local/share/Trash]$ [COLOR="Green"]ls -la[/COLOR]
total 24
drwx------ 4 dan dan  4096 2008-12-03 20:24 .
drwxr-xr-x 7 dan dan  4096 2009-01-18 13:50 ..
drwx------ 2 dan dan  4096 2009-01-19 11:13 files
drwx------ 2 dan dan 12288 2009-01-19 11:14 info
11:35:07[dan:~/.local/share/Trash]$ [COLOR="Green"]cd files/[/COLOR]
11:35:22[dan:~/.local/share/Trash/files]$ [COLOR="Green"]ls -la[/COLOR]
drwx------ 2 dan dan 4096 2009-01-19 11:13 .
drwx------ 4 dan dan 4096 2008-12-03 20:24 ..
drwx------ 4 dan dan 4096 2008-12-03 20:24 os
11:35:25[dan:~/.local/share/Trash/files]$ [COLOR="Green"]sudo rm -vR os[/COLOR]
Password:
removed directory: `os'
[COLOR=Red]... any other files within directory ...
... just in case I missed any ...
... -R recursive attribute used ...[/COLOR]
11:40:00[dan:~/.local/share/Trash/files]$ [COLOR="Green"]cd ./../info[/COLOR]
11:40:30[dan:~/.local/share/Trash/info]$ [COLOR="Green"]ls -la[/COLOR]
drwx------ 2 dan dan 4096 2009-01-19 11:13 .
drwx------ 4 dan dan 4096 2008-12-03 20:24 ..
drwx------ 4 dan dan 4096 2008-12-03 20:24 s5030787.jpg.trashinfo
drwx------ 4 dan dan 4096 2008-12-03 20:24 s5030788.jpg.trashinfo
[COLOR=Red]... a whole bunch more ...[/COLOR]
11:41:20[dan:~/.local/share/Trash/info]$ [COLOR="Green"]sudo rm -vR s*.j*.tr*[/COLOR]
Password:
removed file: s5030787.jpg.trashinfo
removed file: s5030788.jpg.trashinfo
[COLOR=Red]... lotsa files that begin with s ...
... have a "j" behind the first dot ...
... and have "tr" after the second dot ...[/COLOR]
11:41:20[dan:~/.local/share/Trash/info]$[/COLOR]
[/FONT]
-----------------------------------------------------------------------
[COLOR=DimGray]So remember: 
Find the files with 'locate';
Change the directory with 'cd' + /path/to/desired/file/;
List the contents of file with attributes with 'ls -la';
Unless you are already root, you will use sudo after the '$';
Determine the files and directories that need to be deleted;
 -- If you need to delete a whole directory you will need to use 'rm -vR [dir name]';
 -- If you need to delete a file you will use 'rm -v [path/to/file]';
The -v attribute will show you all files that you told the system work with;
The -R attribute will remove all of the files within the directory first;[/COLOR]
-----------------------------------------------------------------------
Anyway, I hope this solution works for those that the other solution didn't. I realize that there are faster ways to do what I did, but it's better to learn from square one. 
This is a great site. Thank you everyone for all of your tips!! Keep up the good work!!

---

### Post by pneaveill on 2009-04-24
> **furytheory said:**
> I was having a similar problem deleting my trash, it kept telling me that I didn't have permission to delete this one directory "os". So I found this thread and was trying to enter the commands, but there was no trash at the .nautilus directory, so here is what I did:
-----------------------------------------------------------------------
[FONT=Trebuchet MS][COLOR=DimGray]11:25:54[dan:/root]$[COLOR=Green] locate Trash[/COLOR]
~/.local/share/Trash/*
[/COLOR][/FONT]
Anyway, I hope this solution works for those that the other solution didn't. I realize that there are faster ways to do what I did, but it's better to learn from square one. 
This is a great site. Thank you everyone for all of your tips!! Keep up the good work!!

Sorry for the edit of you post and the delay in response.

Often the best option on the newer ubuntu releases is as follows

sudo rm -rf  [FONT=Trebuchet MS][COLOR=DimGray]~/.local/share/Trash/*[/COLOR][/FONT]

---

### Post by thatsmyboy on 2009-07-31
saved me big headaches with this! thanks for posting.


> **furytheory said:**
> I was having a similar problem deleting my trash, it kept telling me that I didn't have permission to delete this one directory "os". So I found this thread and was trying to enter the commands, but there was no trash at the .nautilus directory, so here is what I did:
-----------------------------------------------------------------------
[FONT=Trebuchet MS][COLOR=DimGray]11:25:54[dan:/root]$[COLOR="Green"] locate Trash[/COLOR]

-----------------------------------------------------------------------
Anyway, I hope this solution works for those that the other solution didn't. I realize that there are faster ways to do what I did, but it's better to learn from square one. 
This is a great site. Thank you everyone for all of your tips!! Keep up the good work!!

---

