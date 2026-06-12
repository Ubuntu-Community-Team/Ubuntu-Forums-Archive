---
title: "Need Help With Moving Multiple Files From Home To Root!"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by Galilei on 2013-07-19
I'm actually using elementary os Luna, but it's a derivative from Ubuntu so you should be able to help me about.
I'm trying to replace files within root directories and it's a real pain, because it requires to use the command line. That's fine, I just need to learn to use the more advanced commands.

Basically I am going to be replacing images at usr/share/games/supertux2/images/creatures/tux/big directory. 

My new images are at home/tuxtiles/big/ directory

What is the command to replace the roughly 19 png images existing in the root directory with the ones in my home/tuxtiles/big directory?

sudo cp -avr home/ tuxtiles/big usr/share/games/supertux2/images/creatures/tux/

doesn't work. I think I'm just writing this slightly wrong. Can you guys help me out?


Thanks!

---

### Post by Boab1993 on 2013-07-19
I think the code you'll be looking for would be 

[SIZE=2]sudo cp -R /[COLOR=#000000]home/tuxtiles/big usr/share/games/supertux2/images/creatures/tux/[/COLOR]  /[/SIZE][COLOR=#000000][SIZE=2]usr/share/games/supertux2/images/creatures/tux/big directory/[/SIZE]

Bit of a beginner at this myself but as far as i know 
cp stands for copy
-R is the flag for remove
the first location is the source folder
the second location is the destination

Hope this helps![/COLOR]

---

### Post by TheFu on 2013-07-19
"/" is the root directory.
"/root" can also be called the root directory, since it is the HOME directory for the root user account.

Directory paths that begin without a "/" are relative from the current working directory.  Run **cwd** or **pwd** to see what the current working directory is.

I find it very hard to believe that any image files are stored in the root directory - either of them.  They might be stored in a "home" directory ... those are usually something like /home/galilei and can be accessed using a ~/ or $HOME/ text expansions. 

Using sudo really shouldn't be necessary, but until file and directory permissions are understood, you might find it easier to accomplish things. It is also dangerous for reasons too hard to explain here.  There are many tutorials on file and directory permissions where you can learn about that stuff.

Oh, and if filenames and/or directories have spaces in them, you need to use "quotes around the entire path/" so the shell doesn't parse each space as a different option.

So looking at your command above and know knowing exactly what you really intend, I can only guess that 
**sudo cp  ~/*png /usr/share/games/supertux2/images/creatures/tux/**
is what you want.  This assumes that the files are in your HOME and not in any subdirectories. If they are in subdirectories, cp cannot be used. Check out the **find** command or perhaps a **tar** command. These should be 1 line command and scriptfu.com might help.

If this isn't clear, a long-listing of the source directory - that means **ls -al** run from the source file directory will help us help you more.

---

### Post by Galilei on 2013-07-19
This is actually working. I placed the files to my home directory and moved them from there. Is there a way to replace the existing files, though? In the folder "big" there's all the images that constitute Tux's animations. I want to replace those with my own. I intend to do this with background, music, and other files as well. Right now the command you're using doesn't replace existing files.

---

