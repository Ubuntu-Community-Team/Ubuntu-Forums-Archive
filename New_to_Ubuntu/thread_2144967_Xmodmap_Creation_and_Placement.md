---
title: "Xmodmap Creation and Placement"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by Jackyboy012 on 2013-05-13
So I have a split space bar on my current keyboard. The new distribution of Ubuntu out of the box allows me to use my left space bar correctly. At the terminal typing :

```
xmodmap -e 'keycode 146 = space NoSymbol space'
```

allows me to use my right space bar correctly. I also believe that using the start up application I should be able to run a script that passes this once I'm logged in. Now on to the question:

I have no idea how to create a script file, if one exists already, where to place this script file or what the proper extension would be if I created the file.

I have read that using something like:

```
xmodmap -e 'keycode 146 = space NoSymbol space' > ~/.xmodmap
```

should create a file in my home directory called /xmodmap but after searching the entire file system nothing shows up. So I don't think that is working.

Obviously I'm new at this at after two attempt on my own I can't seem to get it to work. I would love an explanation of what I am missing/doing wrong. Thanks in advance!

---

### Post by DuckHook on 2013-05-14
Hi Jackyboy012,

Welcome to Ubuntu and the forums.

You are almost there, which is exceptional for a new user. You have likely created .xmodmap properly. However, any file starting with a dot (.), as in .xmodmap, is a hidden file. You have to take special measures to see them. This is not difficult. If using Nautilus, then typing <Ctrl>+<h> will toggle Nautilus between revealing and hiding all hidden files/directories. If looking in a terminal, then:```
ls -a
```...will list "all" files, including hidden ones.

To run your script, you must first make the .xmodmap file executable. The easiest way is with Nautilus. After unhinding it, right click on it, then Properties > Permissions and click "Execute" box. If you prefer the command line, it is:```
chmod +x .xmodmap
```To run it, just do:```
./xmodmap
```

<edit>
Have just read your post more carefully, It is probable that you created a blank file. It is far better to use a text editor to create your scripts. Nothing wrong with using *gedit*. They must begin with:```
#!/bin/bash
```...so your script needs to look like:```
#!/bin/bash
xmodmap -e 'keycode 146 = space NoSymbol space'
```Then save as .xmodmap and follow the steps to make it executable.
</edit>

---

### Post by Jackyboy012 on 2013-05-14
Awesome. Thank you for your help. I was able get everything up and running and seems to run after a restart. One last question:

When using 

```
[COLOR=#000000][FONT=Ubuntu Mono]./xmodmap[/FONT][/COLOR]
```

I get an error 

bash: ./Xmodmap: No such file or directory

Is this common? As far as I can tell the script is actually run even though it says the file can't be found. It's not the capitalization of the X either as that's how I saved it. Also using ls -a confirms that the file is in the current directory.

Other than that it works swimmingly! Thanks again.

---

### Post by DuckHook on 2013-05-14
My bad. Typo. I missed a dot. Because .Xmodmap begins with a dot, it should be:```
./.Xmodmap
```The more interesting thing is your comment that everything worked well anyway. This implies that the script is not really needed. There was no way it could have loaded if my instructions were missing the dot, so any functionality that you have exists without the script having actually run. If so, then the implication is that the script is not needed. The further conclusion is: don't run what isn't needed. Simple is always best.

---

### Post by Jackyboy012 on 2013-05-14
After scrolling through the terminal I forgot that I had run the initial command before starting the project because I naturally use my right thumb for the space bar so doing any significant amount of typing with having to use my left thumb for space becomes tedious.

None the less wouldn't have figured it out with your help. If there was a up arrow I would up vote you sir/ma'am(edit). Thanks!

---

### Post by DuckHook on 2013-05-14
You're welcome! Helping enthusiastic new users is its own reward. I am sure that, as you get more familiar with Linux, you will one day be helping out others as well.

If you are interested in learning more about the command line (which is where all of the power resides in Linux) [this]("https://help.ubuntu.com/community/CommandLineResources") is a great resource. It will be heavy slogging at first, but slow and steady will ultimately get you to a comfort level that is really quite satisfying.

---

