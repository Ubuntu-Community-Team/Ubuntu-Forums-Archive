---
title: "&quot;installed&quot; a game &quot;my way&quot;, not the &quot;right way&quot; - menu link won't work"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Andre-D on 2008-05-15
Wanting to support games for Linux - I bought "Gish"
- it was a simple tar file with everything in it, no install. (too simple)

   
I thought is should go into /usr/games - but that required SUDO, so I chose to keep it for itself.

I extracted it into /home/andre/Public/gish  "public" sounded like "all users on this machine"

The game works fine when executed from the folder it is in - via Nautilus or terminal.

The game does NOT work fine, is missing graphic objects, when executed from the panel, where I made a link to "/home/andre/Public/gish/gish"

Why?  - how to fix ?

Thanks

---

### Post by nowshining on 2008-05-15
start the game from the terminal and if no graphics show, etc.. exit out of the game - are there any errors in the terminal? if so post them.

---

### Post by Andre-D on 2008-05-15
executing it from terminal works fine I executed like:
cd Publish/gish
./gish

If fails if executed like:
Public/gish/gish

---

### Post by Oldsoldier2003 on 2008-05-15
> **Andre-D said:**
> executing it from terminal works fine I executed like:
cd Publish/gish
./gish

If fails if executed like:
Public/gish/gish

try making the launcher command .sh /full/path/to/gish

---

### Post by Andre-D on 2008-05-16
> andre@Ubuntu:~$ sh /home/andre/Public/gish/gish
/home/andre/Public/gish/gish: 1: Syntax error: "(" unexpected


This error makes no sense to me

---

### Post by hyper_ch on 2008-05-16
are there install instructions? Please post them :)

---

### Post by Andre-D on 2008-05-16
nope - it's only "uncompress" - and some requred audio librarys, I have them, and if executed from the folder, everything works - only not from link.
 - you can pick up a demo here: [http://www.chroniclogic.com/index.htm?gish.htm](http://www.chroniclogic.com/index.htm?gish.htm)

I am sure you'll get the same result then.

---

### Post by hyper_ch on 2008-05-16
You did install

openal, vorbis and ogg libraries?

and you also made sure that opengl runs on your vide card?

---

### Post by Andre-D on 2008-05-16
> **hyper_ch said:**
> You did install

openal, vorbis and ogg libraries?

and you also made sure that opengl runs on your vide card?

Yes, because , (as I wrote before), when the file "gish" is executed from nautilus, OR from terminal ,after CD'ing to the folder where the files are, then it works *perfectly* fine, with video, sound & everything.

When executed from a link in panel, OR from another folder, like 
"/home/andre/Public/gish/gish" ,then it's missing graphics, and is a complete mess.

My guess, it does not find it's files unless I do "cd /home/andre/Public/gish" first, then "./gish"

---

### Post by ad_267 on 2008-05-16
create a bin folder in your home directory if there isn't one already. In that create a file called launchgish and in that file put

```
#!/bin/bash
cd /home/yourname/Public/gish/
./executable_name
```
(replacing yourname and executable_name)

Now to start gish just run launchgish and change any launchers to run this command.

If you want all users to have this then you will need to move the script into /usr/bin

This is needed because the game isn't installed so looks for files it needs from the current directory.

---

### Post by Andre-D on 2008-05-16
thanks - this should have worked: (launchgish)
> #!/bin/bash
cd /home/andre/Public/gish/
./gish

The last two lines works in terminal - anytime, just fine.
However, this file does not work when executed from Nautilus , no new window appears, and no process "gish" is running.

maybe something wrong with the first line ?

Thank you for helping - I think this is the right approach-

BTW: I made /home/andre/bin  - not /home/bin - I assume the first is the best practice ?
No other users are important, that I can figure out myself later :)

Thanks for helping - what's the next step ?

---

### Post by ad_267 on 2008-05-16
Did you make the file executable?

Try running it from a terminal and see what error you get.

---

### Post by Andre-D on 2008-05-16
> **ad_267 said:**
> Did you make the file executable?

Try running it from a terminal and see what error you get.

I did not make it executable, did this now, and it works just fine now.

Thank you very much  - I am learning from this.

---

