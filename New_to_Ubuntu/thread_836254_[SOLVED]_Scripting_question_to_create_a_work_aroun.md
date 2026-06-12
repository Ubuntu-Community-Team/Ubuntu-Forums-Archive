---
title: "[SOLVED] Scripting question to create a work around"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by jasontu on 2008-06-21
Since I can't seem to find a permanent solution to the issue described here: [http://ubuntuforums.org/showthread.php?p=5232098#post5232098](http://ubuntuforums.org/showthread.php?p=5232098#post5232098)

I have decided to ask for some help in automating the work-around I developed.

This may be tricky or it may be difficult.  I hope it can be done without too much hassle.

Here's my goal.  I want to script things so that when I exit wow (or Launcher.exe) being run through wine a file called Config.wtf is deleted in the Program Files/WoW/WTF folder and a file called Config.wtf in a Program Files/WoW/Unused WTF/Baseline Edit is then copied to the /WoW/WTF folder.

Is there a way I can tack those instructions onto a program when it closes?  Even if it is a Wine program?

---

### Post by Hospadar on 2008-06-21
it might be a little easier to do this on startup instead of when you quit wow, but either way it's no big.  Try something like this (you'll probably have to edit the specific paths in the script, I'm just guessing where your wow install is)

This would be a script that starts wow, and then when you quit it, it does your file copying, it might not work because I'm not sure how wow deals with the launcher and whatnot
```
#!/bin/bash
wine ~/.wine/drive_c/Program\ Files/WoW/WoW.exe 
#when wine finishes executing:
rm -f ~/.wine/drive_c/Program\ Files/WoW/WTF/Config.wtf
mv -f ~/.wine/drive_c/Program\ Files/WoW/Unused\ WTF/Baseline\ Edit/Config.wtf ~/.wine/drive_c/Program\ Files/WoW/WTF/Config.wtf

```

If that doesn't work, move the wine command to the end of the script, so the file copying takes place ahead of time.  Note that you will need to use this script to start the game every time you run it.

---

### Post by jasontu on 2008-06-21
I'll give this a shot.  Is there a way I can incorporate all of this code into an icon shortcut or at least a single terminal command?  I have barely started with Linux, but I remember turning stuff like this in MSDOS into a *.bat command.

Thanks!

---

### Post by the_doc on 2008-06-21
You would put all of that into a script file called for example, **script**, then run with ./script.

Of course you'll have to make it executable.

---

### Post by jasontu on 2008-06-21
How do I make a script file and make it an executable?

Sorry very new at this.

Thank you

---

### Post by the_doc on 2008-06-21
Copy the code from post #2 and paste it into a text file and save as **wow** or something.

**Application > Accessories > Terminal** to open a shell, **CD /path/to/wow** to get to the correct directory, then **chmod +x wow** to make it executable.

Then **./wow** to run.

---

### Post by sourchier on 2008-06-21
This is how you make a script. I will call the script "somescript" as an example. Feel free to call the script whatever you want.

1. Open up the gnome terminal.
2. Create the script by typing touch somescript
3. Edit the script by typing gedit somescript (don't forget to save)
4. Make the script executable by typing chmod +x somescript
5. Test the script by typing ./somescript

Opps the_doc beat me to it. :)

---

### Post by the_doc on 2008-06-21
Two replies are better than none! :)

---

### Post by jasontu on 2008-06-21
Okay I opened up gedit and pasted post #2 in and I wanted to run it by you because I made a couple of changes:

> #before wine executes:
rm -f ~/.wine/drive_c/Program\ Files/WoW/WTF/Config.wtf
cp -f ~/.wine/drive_c/Program\ Files/WoW/Unused\ WTF/Baseline\ Edit/Config.wtf ~/.wine/drive_c/Program\ Files/WoW/WTF/Config.wtf
#!/bin/bash
wine ~/.wine/drive_c/Program\ Files/WoW/Launcher.exe 

I changed the "mv" line command to "cp" because if I wanted to use this script more than once I need that file to stay there, and I thought that the mv command would move the file completely (leaving the origin empty)

I also changed the wow.exe to Launcher.exe since that is apparently the command to start the thing up.

Anyone see any issues with this strategy?

---

### Post by jasontu on 2008-06-21
Oh and I saved the text file as WoWLaunchScript in a /Games folder.  So now I just have to make it an executable, right?

On the shortcut icon can I just go to Properties and write ./WoWLaunchScript into the "Comment" field?

---

### Post by the_doc on 2008-06-21
> **jasontu said:**
> Okay I opened up gedit and pasted post #2 in and I wanted to run it by you because I made a couple of changes:



I changed the "mv" line command to "cp" because if I wanted to use this script more than once I need that file to stay there, and I thought that the mv command would move the file completely (leaving the origin empty)

I also changed the wow.exe to Launcher.exe since that is apparently the command to start the thing up.

Anyone see any issues with this strategy?

I don't know how to use Wine so you know more than me on the Launcher.exe issue!  CP isntead of MV sounds fine.

---

### Post by the_doc on 2008-06-21
> **jasontu said:**
> Oh and I saved the text file as WoWLaunchScript in a /Games folder.  So now I just have to make it an executable, right?

On the shortcut icon can I just go to Properties and write ./WoWLaunchScript into the "Comment" field?

If you right click on the desktop and select **Create Launcher**, you could put **./complete/path/to/WoWLaunchScript** in the command text box.

---

### Post by jasontu on 2008-06-21
Thanks for all the help guys!  I think I got this working.  I just placed the script into the quick bar and dumped the old quick launcher.

Now I just have to remember that if I want to make changes to the configuration I have to do textually in the back-up Config.wtf

Thanks, I learned a lot about scripting today!

---

### Post by the_doc on 2008-06-21
Good, glad it worked out!

---

