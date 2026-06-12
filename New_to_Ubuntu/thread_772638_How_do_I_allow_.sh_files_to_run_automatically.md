---
title: "How do I allow .sh files to run automatically"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Palu on 2008-04-28
I've discovered the joy of making .sh scripts. For other newcomers like me, they are simple text files containing a bunch of terminal commands. You can run the .sh file and it does all the stuff inside. I think you have to make the script executable too (at least I have been) by typing "chmod +x filename.sh" while in the same directory as the script.

**Question**
Now that I've discovered this wonder of time saving reminicent of dos batch files, I'd love to find a way to get rid of the dialog that pops up asking if I'd really like to run the script. If I use these to automate an operation, I'd like it to just do what I've told it to do. How do I do that? Is this the right tool to do such a thing? If it isn't, is there another way?

---

### Post by gardara on 2008-04-28
You can run the script from terminal, then you won't get any questions.

```
./yourscript.sh
```

and this one should work too:

```
sh yourscript.sh
```

I suggest you look at crontab too, if you haven't checked that tool out already. 

[http://en.wikipedia.org/wiki/Crontab](http://en.wikipedia.org/wiki/Crontab)

---

### Post by superprash2003 on 2008-04-28
use this..
echo (password) | sudo -S (command)
and save it as a .txt file .. you can have as many lines as you want..for multiple commands.. then all you need to do is type sh file.txt where file.txt is the file containing the commands.. you can add it as a cron task to automate stuff

---

### Post by superprash2003 on 2008-04-28
use this..
echo (password) | sudo -S (command)
and save it as a .txt file .. you can have as many lines as you want..for multiple commands.. then all you need to do is type sh file.txt where file.txt is the file containing the commands.. you can add it as a cron task to automate stuff

---

### Post by Oldsoldier2003 on 2008-04-28
its bad to leave passwords in plain text files. sudoers is the preferred method and avoids leaving passwords in clear text strewn about the computer.

---

### Post by Palu on 2008-04-28
Thanks. :popcorn:

I'm hoping to do this from only the GUI interface without a prompt. Telling one of my users to use the terminal probably isn't an option. :)

Perhaps a launcher can do most the things I want to do. Mainly I want to make a launcher for Wine apps, which a launcher can do, BUT... for apps using OpenGL I'll also need to shut down compiz for best effects, I think... so it'd be nice to figure this out without making a user go to the terminal to run a script or go through multiple menus.

---

### Post by KIAaze on 2008-04-28
Just create a launcher with the path to the script as command.

ex:
You want to run script.sh which is in your homedir when you click on the launcher: Put in the command "/home/login/script.sh" in the launcher properties.
(The script has to be executable of course.)

To make things cleaner, you can put your script in one of the directories of the PATH variable like /usr/local/bin for example.
Then you just have to write "script.sh" as command.

---

### Post by bodhi.zazen on 2008-04-28
From what you are describing, write a script and once the script is working add a launcher.

If the script is for a single user, put it in ~/bin
If the script is for multiple users, put it in (or link it to) /usr/local/bin

:)

---

### Post by Palu on 2008-04-29
Oh! Snap. :popcorn: That's it!

(Also, I like the popcorn smiley.)

---

### Post by Palu on 2008-04-29
Can I not mark the thread as SOLVED since the bracketed comments are already used to denote type of distro in this forum?

---

### Post by bodhi.zazen on 2008-04-29
> **Palu said:**
> Can I not mark the thread as SOLVED since the bracketed comments are already used to denote type of distro in this forum?

No, this function needs to be re-enabled, we are working in it :)

---

