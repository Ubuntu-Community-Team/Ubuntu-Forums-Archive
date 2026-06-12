---
title: "missing file/folder NOTES &amp; EMBLEMS (Ubuntu 10.04 ==&gt; 12.04)"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by Thinkintuit on 2012-06-06
I've just upgraded from a Pangolin Performance running 10.04 to a Gazelle Professional running 12.04, and right away I've encountered a serious problem that is affecting my work.

On my Pang/10.04 I would place emblems on files to categorize them in various ways, and would make notes on the  files, sometimes containing quite a bit of textual information. On 12.04  on my new Gazelle, I don't see the emblems or notes fields when I  right-click on a file. On 10.04 if I right-click on a file I see five fields: Basic, Emblems, Permissions, Open With, Notes. On 12.04 I'm only seeing three: Basic, Permissions, Share.

This means on my new machine I'm unable to access important  meta-data on literally thousands of files that I've worked with  over several months, and I've got looming deadlines. 

So my questions are:
1) Is there a way to reactivate the "notes" and "emblem" options (especially notes) on 12.04 so that I can make new notes?
2)  Is there a way to access, on my new machine, the notes and emblems that I've put on the  files when I was working with them on 10.04 on my Pangolin?

The second question is more important: I can formulate a new way of working as I move forward (although that would be a drag), but if I can't access the meta-data on my new machine, then I don't have access (on the new machine) to a lot of work I've already done.

Thanks for any help.

(Aside for anyone who is wondering: I edit nonfiction anthologies aimed primarily at high school / early college audiences. This involves doing humongous amounts of raw research, mostly on the Internet.)

---

### Post by blackbird34 on 2012-06-06
Thunar (the Xfce file manager ) supports emblems in a right click > "Properties" tab. However I don't know if it would pick up your metadata as i don't use emblems, and I can't test myself...

Why not try it?

```
sudo apt-get install thunar
```

---

### Post by Thinkintuit on 2012-06-06
Thanks for the reply, blackbird34. I'm going to hold off on that for now because I *just* got this computer and I don't want to mess around with things too much in case there are other software/hardware problems. (And indeed, the computer froze several times last night and this morning; there have been several automatic software updates so we'll see what happens.) 

I'm reluctant to add too many confounding variables just yet--especially since I'm not very technically inclined; it would be easy for me to do something I wouldn't understand, or that would confuse efforts on the part of System76 to diagnose and resolve any other problems that may occur with this new machine.

That said, I appreciate your reply, and if anyone else has anything to add I'd appreciate that as well. :)

I'continue to mull over how I want to proceed with this...

---

### Post by blackbird34 on 2012-06-06
You're welcome. Although there's no need to worry, Thunar is perfectly harmless (you can also get it in the Ubuntu Software Center, it shouldn't cause problems). You could simply make a copy of one of your folders to tinker about  until you can get the metadata out of the files, i suppose. 

PS: if you are worried about problems, you could always do regular backups with a tool such as Back In Time (see Software Center too). 
Don't worry too much, you'll settle in fine, i'm not very technically inclined either :D

---

### Post by Thinkintuit on 2012-06-06
Thanks again! Back in Time sounds useful. I just looked at the description, though, and it says it's a gnome program. Will that work in 12.04? I thought gnome had been replaced with Unity, or am I misunderstanding something?

---

### Post by blackbird34 on 2012-06-06
Yes, i've installed it, it works fine, just did a backup, and I am using Unity :D , it integrates nicely now as Unity is built on top of the latest version of Gnome (Gnome 3.4) in Ubuntu 12.04.
You can set  it up to do  automatic backups regularly and then forget about it, and it backs up to plain files, so you can restore your files with a plain file manager if need be.

---

### Post by Thinkintuit on 2012-06-07
I've decide to take a new tack on this; I started a new thread asking how, moving forward, I can achieve a similar result on 12.04: [http://ubuntuforums.org/showthread.php?p=12007136#post12007136](http://ubuntuforums.org/showthread.php?p=12007136#post12007136)

I may try reinstalling the emblems as you helpfully suggested, blackbird34, but it's the ability to stick **notes** on files that is essential. If I can't access the notes in my new OS environment I'll just have to finish those projects on my old laptop (ugh). But I need to either figure out a way to do something *very* similar on 12.04 or *completely* change how I do my work.

---

### Post by Thinkintuit on 2012-06-09
Blackbird34, I took your advice and installed Thunar. So far it seems to be working fine. The emblems look great! That will help a bit, although as I said, it's the "notes" feature that is most important to me.

I opened another thread about this, and got a lot of technically advanced advice that was way over my head, as well as a useful link that at least shed some light on why the oh-so-useful "notes" feature was discontinued. However, the upshot is that that feature *really* seems to be gone, with no apparent way (that I can see so far) to bring it back.

That's a serious drag. For now I'm planning to continue to use my old laptop with 10.04 to do my work (and hope that it doesn't die anytime soon), and gradually figure out a whole new way of doing my job on 12.04. 

<sigh>

---

### Post by Thinkintuit on 2012-06-26
I have a solution, of sorts, to the missing "notes" option: install KDE.

KDE uses a file management system called Dolphin that has a notes field; it also has the ability to put from 1 to 5 stars on a file.

So I could use KDE for working with my files and use something like my old work system. However, that would involve getting used to working with KDE. Currently I'm leaning towards coming up with a different approach to my editing work, using Unity. I mourn the loss of notes, but somehow I will get over it and someday I will learn to love again...  

Thanks again, everyone, for your input on this problem. And thanks especially to my friend Charles V., who took on this problem and eventually pointed me in the direction of KDE.

---

### Post by Ravi5kumar on 2012-07-31
Is there a no way I can install those features into nautilus?! Thuner adds XFCE dependencies which I don't want! Please help!!

---

### Post by tahitiwibble on 2012-10-29
I can't believe that they did this! :mad: 

Like you Thinkintuit I had volumes of notes in my file's 'properties'. Reference numbers, parts numbers, customer's coordinates etc etc etc ........ since upgrading to 12.04 THEY'VE GONE :shock:

If anyone else finds a simple, non-technical way of getting the info back ...... please, please post the solution here.

---

### Post by zombifier25 on 2012-10-29
[http://askubuntu.com/questions/90853/file-notes-tab-gone-in-nautilus-3-2-1](http://askubuntu.com/questions/90853/file-notes-tab-gone-in-nautilus-3-2-1)

To view notes for a file:
```
gvfs-info -a metadata::annotation filename
```

---

