---
title: "How to understand directory listing for Trash/"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by jps2012 on 2012-04-18
Nautilus suddenly won't let me empty the trash, so I'd like to do it via the command line. I understand (based on forum info) that I should use 

When I try to get a listing of the contents of Trash/, this is what I see 

[email]root@JPS:/home/joel/.local[/email]/share/Trash/info# ls -a
.  ..

A dot, a space, two dots. I'm not sure what that means (other than that I could, by ending a command with a dot, stay in the same directory, or with two dots and go up one level). 

What I don't understand is why "ls -a" won't give me the contents of Trash. 

I also don't understand why running the following command doesn't seem to affect Trash (I still see the icons for each file as they appear in Nautilus). 

rm -rf /Trash/*

If anyone sees a logic error I'm making, in the way I'm issuing commands, and the directories I'm acting in, I'd appreciate hearing about it. Thanks.

---

### Post by alphacrucis2 on 2012-04-18
> **jps2012 said:**
> Nautilus suddenly won't let me empty the trash, so I'd like to do it via the command line. I understand (based on forum info) that I should use 

When I try to get a listing of the contents of Trash/, this is what I see 

[email]root@JPS:/home/joel/.local[/email]/share/Trash/info# ls -a
.  ..

A dot, a space, two dots. I'm not sure what that means (other than that I could, by ending a command with a dot, stay in the same directory, or with two dots and go up one level). 

What I don't understand is why "ls -a" won't give me the contents of Trash. 

I also don't understand why running the following command doesn't seem to affect Trash (I still see the icons for each file as they appear in Nautilus). 

rm -rf /Trash/*

If anyone sees a logic error I'm making, in the way I'm issuing commands, and the directories I'm acting in, I'd appreciate hearing about it. Thanks.

The rm -rf /Trash/* is definitely wrong. The leading / means that it is an absolute path under the file system root. The folder /Trash under the file system root shouldn't normally exist. You want a relative path - ie leave the leading / off. 

Not sure why your ls -a doesn't work as it does for me

---

### Post by jps2012 on 2012-04-18
Thanks, alpha. I used a relative path, descended into the directory to this point: 

[email]root@JPS:/home/joel/.local[/email]/share/Trash/files# 


I used this command to do the delete: 

 rm -i -R Junkfiles2012

It SEEMED to work. I got a prompt for each file, used Y to delete each file successively. But maybe not successfully. Nautilus STILL shows the files as sitting in Trash. 

Any idea why that would happen? If I can't trust Nautilus to give me an accurate picture of what's in a directory ... then I feel more than lost.

---

### Post by Shazaam on 2012-04-18
Try this...
```
ls -l
```
(lowecase L's)

---

### Post by codemaniac on 2012-04-18
> **jps2012 said:**
> What I don't understand is why "ls -a" won't give me the contents of Trash. 


And also make sure there are contents in your trash .

---

### Post by bab1 on 2012-04-18
> **jps2012 said:**
> Nautilus suddenly won't let me empty the trash, so I'd like to do it via the command line. I understand (based on forum info) that I should use 

When I try to get a listing of the contents of Trash/, this is what I see 

[email]root@JPS:/home/joel/.local[/email]/share/Trash/info# ls -a
.  ..

A dot, a space, two dots. I'm not sure what that means (other than that I could, by ending a command with a dot, stay in the same directory, or with two dots and go up one level). 

What I don't understand is why "ls -a" won't give me the contents of Trash. 

I also don't understand why running the following command doesn't seem to affect Trash (I still see the icons for each file as they appear in Nautilus). 

rm -rf /Trash/*

If anyone sees a logic error I'm making, in the way I'm issuing commands, and the directories I'm acting in, I'd appreciate hearing about it. Thanks.

The *dot* and *double dot* (. and ..) are aliases```
. = the current working directory (see *pwd*)

.. = the directory that is just about the current working directory
```

The icon of the trash can (either full or empty) sometimes is not coordinated with the Trash directory.  Why?  Who knows, but its not a big deal.  If you have looked in the ~/.local/share/Trash/files directory and nothing is there so be it.  :-)

Here is the trash in my unemptied Trash folder```

~/.local/share/Trash/files$ls -a
.                            cake.ra             earlyinthe (copy).ra
..                           castaway (copy).ra  earlyinthe.ra
achinheartedblues (copy).ra  castaway.ra         getitfixed (copy).ra
achinheartedblues.ra         coalcart (copy).ra
cake (copy).ra               coalcart.ra

*[COLOR="Blue"]and after emptying the trash[/COLOR]*

~/.local/share/Trash/files$ ls -a
.  ..

```

---

### Post by jps2012 on 2012-04-18
Shazzam: "ls -l" returns "0 files" 

So bash and Nautilus disagree. Maybe I need to do updatedb before Nautilus knows what's going on? I'll try that (it's a wild guess, but harmless) to see what happens. And I'll close every Nautilus window.

... and they're still there. I'm going to restart to see if that fixes it ...

---

### Post by jps2012 on 2012-04-18
Nope. After manually deleting the files via bash, updating the database and restarting Nautilus still shows the Trash folder as containing 10 folders, 158 items, using 2.9 gigs. 

This kind of tells me one of the two --either bash or Nautilus -- can't be right. The question, of course, is WHICH ONE?

---

### Post by jps2012 on 2012-04-18
Bab: Thanks for pointing out that the dot and double dot were aliases. I kept seeing those characters in ls listings but didn't know what they meant. Thanks also for taking the time to show me (so I could see how the files should list) the contents of your Trash. I think we're listening to the same kind of music! 

Now if I could just get Nautilus to sing straight to me.

---

### Post by alphacrucis2 on 2012-04-18
> **jps2012 said:**
> Nope. After manually deleting the files via bash, updating the database and restarting Nautilus still shows the Trash folder as containing 10 folders, 158 items, using 2.9 gigs. 

This kind of tells me one of the two --either bash or Nautilus -- can't be right. The question, of course, is WHICH ONE?

I would trust the ls command over any graphical tool.

---

### Post by Shazaam on 2012-04-18
Another (WARNING! Full root nautilus powers- be careful)...
```
gksudo nautilus
```
CTRL+H to show hidden files.

---

### Post by jps2012 on 2012-04-19
Shazzam: I'm not sure what that command is supposed to tell me. Wouldn't it tell me EVERY hidden file on my system? How would that resolve the conflict between bash and Nautilus (please note, I'm not arguing; I'm just ignorant; but trying to change that).

---

### Post by bab1 on 2012-04-19
> **jps2012 said:**
> Nope. After manually deleting the files via bash, updating the database and restarting Nautilus still shows the Trash folder as containing 10 folders, 158 items, using 2.9 gigs. 

This kind of tells me one of the two --either bash or Nautilus -- can't be right. The question, of course, is WHICH ONE?

Can you show us the info (graphic)?

---

### Post by bab1 on 2012-04-19
> **Shazaam said:**
> Another (WARNING! Full root nautilus powers- be careful)...
```
gksudo nautilus
```
CTRL+H to show hidden files.

If this is his directory then root is not needed.

---

### Post by bab1 on 2012-04-19
> **jps2012 said:**
> Shazzam: I'm not sure what that command is supposed to tell me. Wouldn't it tell me EVERY hidden file on my system? How would that resolve the conflict between bash and Nautilus (please note, I'm not arguing; I'm just ignorant; but trying to change that).
In a sense you are correct, the file system can be shown from the CLI or via Nautilus.  They are not the same routines but they should be close.  I'm more curious about the 10 folders, 158 items, using 2.9 gigs.  Once again, a picture is worth a thousand words.

---

### Post by jps2012 on 2012-04-19
OK, folks, thanks for hanging in there with me. I ran gksudo nautilus. A window popped up (I guess you expected that; I had no idea what would happen). 

I clicked on the Trash icon in the left panel. A window popped up, then a warning" operation not supported." 

No files are shown, but I've got a little wheel spinning (the Ubuntu version of the Vortex of Doom/Beachball Apocalypse). 

It spins and spins. And next? Does this mean my trash can is corrupt (sounds redundant)?

---

### Post by bab1 on 2012-04-19
> **jps2012 said:**
> OK, folks, thanks for hanging in there with me. I ran gksudo nautilus. A window popped up (I guess you expected that; I had no idea what would happen). 

I clicked on the Trash icon in the left panel. A window popped up, then a warning" operation not supported." 

No files are shown, but I've got a little wheel spinning (the Ubuntu version of the Vortex of Doom/Beachball Apocalypse). 

It spins and spins. And next? Does this mean my trash can is corrupt (sounds redundant)?

What can I say?  :D

See the posts directly above your last post.

---

### Post by wojox on 2012-04-19
Run these two commands:
```
rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
sudo rm -rf /root/.local/share/Trash/*/** &> /dev/null

```
They will purge your trash.

---

### Post by jps2012 on 2012-04-19
Well, there's what distinguishes the experts from the beginners. To me, a system that says one thing in Nautilus, and another thing in a Nautilus window launched from the Terminal, and another thing in Terminal ... isn't overwhelmingly comprehensible (although "what can I say" kind of implies it's comprehensible to someone). 

The fundamental problem remains the same--a beginner trying to understand why different access points yield different information (and the fact that they DO yield different info). 

I'm used to believing an "operation not supported" message, combined with a perpetual vortex of doom doesn't imply "everything is hunky dorky." So ... maybe you can see why I might (and other beginners might) think something funky was going on (and would want to unravel it, so we could really, really understand). 

I do get that you're saying I shouldn't worry any more. But what I'd really like to do is understand. I guess one lesson in this is that I shouldn't trust Nautilus to show me what I have (or don't have) in my system, even for files that are not hidden by the system. 

Thanks for guiding me through the commands.

---

### Post by bab1 on 2012-04-19
> **jps2012 said:**
> Well, there's what distinguishes the experts from the beginners. 

To me, a system that says one thing in Nautilus, and another thing in a Nautilus window launched from the Terminal, 
Edit: These are the same unless you open one with a different user (i.e like root)> 

and another thing in Terminal ... isn't overwhelmingly comprehensible (although "what can I say" kind of implies it's comprehensible to someone). 

The fundamental problem remains the same--a beginner trying to understand why different access points yield different information (and the fact that they DO yield different info). 

I'm used to believing an "operation not supported" message, combined with a perpetual vortex of doom doesn't imply "everything is hunky dorky." So ... maybe you can see why I might (and other beginners might) think something funky was going on (and would want to unravel it, so we could really, really understand). 


I do get that you're saying I shouldn't worry any more. But what I'd really like to do is understand. I guess one lesson in this is that I shouldn't trust Nautilus to show me what I have (or don't have) in my system, even for files that are not hidden by the system. 

Thanks for guiding me through the commands.

Oh well...  :-(

---

### Post by wojox on 2012-04-19
> **jps2012 said:**
> Well, there's what distinguishes the experts from the beginners. To me, a system that says one thing in Nautilus, and another thing in a Nautilus window launched from the Terminal, and another thing in Terminal ... isn't overwhelmingly comprehensible (although "what can I say" kind of implies it's comprehensible to someone). 

The fundamental problem remains the same--a beginner trying to understand why different access points yield different information (and the fact that they DO yield different info). 

I'm used to believing an "operation not supported" message, combined with a perpetual vortex of doom doesn't imply "everything is hunky dorky." So ... maybe you can see why I might (and other beginners might) think something funky was going on (and would want to unravel it, so we could really, really understand). 

I do get that you're saying I shouldn't worry any more. But what I'd really like to do is understand. I guess one lesson in this is that I shouldn't trust Nautilus to show me what I have (or don't have) in my system, even for files that are not hidden by the system. 

Thanks for guiding me through the commands.
Why do you have files in roots trash to begin with?

---

### Post by Shazaam on 2012-04-19
> **jps2012 said:**
> Shazzam: I'm not sure what that command is supposed to tell me. Wouldn't it tell me EVERY hidden file on my system? How would that resolve the conflict between bash and Nautilus (please note, I'm not arguing; I'm just ignorant; but trying to change that).

I should have explained better sorry. You could use that command to drill down to your /home trash and /root trash to see if nautilus shows anything.
As far as the differences between the cli and a gui I honestly have no clue. While playing around I have come across many oddities with nautilus and others like fdisk and gparted. Fdisk would show one thing and gparted would show another.

---

### Post by jps2012 on 2012-04-19
That's OK, Shazzam. I know we beginners can be hard to "get through to" sometimes. It's an epistemology problem; people who have a great deal of knowledge can forgot that others lack even the core concepts that explanations are based on. Believe me, those of us who are trying to learn ... envy you. We wish we spoke the lingo--but more than that, we wish we had the foundation the lingo is based on.

---

### Post by jps2012 on 2012-04-19
Wojox: Regarding your question, "Why do you have files in roots trash to begin with?" 

That would be the OS system at work, not a choice on my part. It's not like I went into the command line and executed "dude, just treat my deleted files like they're litter; toss them EVERYWHERE." 

The OS puts them where it thinks they should go, without consulting me. I imagine that if I were capable enough, I could set some kind of script that would force them to only appear in one logical location, that wouldn't serve as a magnet for rhetorical questions about my OS. But alas. I'm stuck for now with what I get. (Not that it's horrific; I'm just trying to understand how these functions work, and I'm making progress, given all the help I'm getting here.)

---

### Post by alphacrucis2 on 2012-04-19
> **jps2012 said:**
> Wojox: Regarding your question, "Why do you have files in roots trash to begin with?" 

That would be the OS system at work, not a choice on my part. It's not like I went into the command line and executed "dude, just treat my deleted files like they're litter; toss them EVERYWHERE." 

The OS puts them where it thinks they should go, without consulting me. I imagine that if I were capable enough, I could set some kind of script that would force them to only appear in one logical location, that wouldn't serve as a magnet for rhetorical questions about my OS. But alas. I'm stuck for now with what I get. (Not that it's horrific; I'm just trying to understand how these functions work, and I'm making progress, given all the help I'm getting here.)


The command line stuff doesn't use trash at all. Trash is implemented in nautilus and some other graphical file managers to mimic trash/can recycle bin type of thing like in windows and apple. Stuff can only get into the root users trash folder if you deleted stuff using nautilus or similar (dolphin etc) running as root. Deleting stuff from nautilus running as a normal user will put the files into that users trash. The OS itself doesn't use any trash folders at all. If the OS deletes a file it's gone (unless you use special recovery tools such as testdisk/photorec).

---

### Post by jps2012 on 2012-04-19
Thanks, alpha. I'm having to guess a little at what the message means, but I think (based on what you said) that files ended up in my root trash folder because I launched Nautilus from the command line, while logged in as root. What I still don't understand, of course, is why Nautilus tells me (when I pull up Trash/ in the GUI) I have 2.8 gigs of files in Trash/, but bash tells me I have zero files.

---

### Post by alphacrucis2 on 2012-04-19
> **jps2012 said:**
> Thanks, alpha. I'm having to guess a little at what the message means, but I think (based on what you said) that files ended up in my root trash folder because I launched Nautilus from the command line, while logged in as root. What I still don't understand, of course, is why Nautilus tells me (when I pull up Trash/ in the GUI) I have 2.8 gigs of files in Trash/, but bash tells me I have zero files.

By bash I guess you mean the ls command. ls is just reporting what the file system says. Nautilus may be reporting its own view of the world which has somehow got out of step with the real situation. I did a google search and I found a similar issue where the gnome config files which specify where the trash is actually located (used by nautilus) had got screwed up with trash pointing at the wrong location. The solution was to delete some gnome config files to force them to be recreated as default but I am reluctant to recommend trying that in case things end up worse.

---

### Post by bab1 on 2012-04-19
Opening a terminal window with *your login* (a *mortal* user) and using ```
gksudo nautilus
```

Launches Nautilus with **root** (the **immortal** user) as owner.  Anything you delete goes in the trash folder owned by root (under the directory /root).

So you can have trash in 2 places; your user trash and the root user's trash using Nautilus.

I think you should think of which user you are operating as; *you* or **root**?

---

