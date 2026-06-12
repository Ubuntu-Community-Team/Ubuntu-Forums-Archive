---
title: "Moving files from subfolders to main filder; understanding the command"
date: 2015-08-09
forum: New to Ubuntu
---

### Post by mike196 on 2015-08-09
Hello all,

About a year ago I asked a question here about [http://ubuntuforums.org/showthread.php?t=2235792]("http://[URL")]how to move all files from subdirectories out into the main directory[/url].  I had never had a problem with it until today.

My file system is set up as such:
```
.&#9500;&#9472;&#9472; Movies
&#9474;   &#9500;&#9472;&#9472; Movie_A
&#9474;   &#9492;&#9472;&#9472; Movie_B
&#9492;&#9472;&#9472; Television
    &#9500;&#9472;&#9472; Show_Title_A
    &#9500;&#9472;&#9472; Show_Title_B
      &#9474;   &#9500;&#9472;&#9472; Season_1
      &#9474;   &#9500;&#9472;&#9472; Season_2
      &#9474;   &#9500;&#9472;&#9472; Season_3
    &#9500;&#9472;&#9472; Show_Title_C
      &#9474;   &#9500;&#9472;&#9472; Ep_1_Folder
      &#9474;   &#9500;&#9472;&#9472; Ep_2_Folder
      &#9474;   &#9500;&#9472;&#9472; Ep_3_Folder








```

But there are about 30 shows.

I ran the following line (from the above thread) without really understanding it (which is my own fault):

```
sudo find ./ -mindepth 2 -type f -exec mv {} /media/PublicMedia/Television/Show_Title_C \;
```

Now, what I was hoping to have happen was 

```

&#9492;&#9472;&#9472; Television
    &#9500;&#9472;&#9472; Show_Title_A
    &#9500;&#9472;&#9472; Show_Title_B
      &#9474;   &#9500;&#9472;&#9472; Season_1
      &#9474;   &#9500;&#9472;&#9472; Season_2
      &#9474;   &#9500;&#9472;&#9472; Season_3
    &#9500;&#9472;&#9472; Show_Title_C
      &#9474;   &#9500;&#9472;&#9472; Ep_1_Folder
      &#9474;   &#9500;&#9472;&#9472; Ep_2_Folder

      &#9474;   &#9500;&#9472;&#9472; Ep_3_Folder
      &#9474;   &#9500;&#9472;&#9472; Ep_1_File
      &#9474;   &#9500;&#9472;&#9472; Ep_2_File

      &#9474;   &#9500;&#9472;&#9472; Ep_3_File

```

Instead, what I got was

```

&#9492;&#9472;&#9472; Television
    &#9500;&#9472;&#9472; Show_Title_A
    &#9500;&#9472;&#9472; Show_Title_B
      &#9474;   &#9500;&#9472;&#9472; Season_1
      &#9474;   &#9500;&#9472;&#9472; Season_2
      &#9474;   &#9500;&#9472;&#9472; Season_3
    &#9500;&#9472;&#9472; Show_Title_C
      &#9474;   &#9500;&#9472;&#9472; Ep_1_Folder
      &#9474;   &#9500;&#9472;&#9472; Ep_2_Folder

      &#9474;   &#9500;&#9472;&#9472; Ep_3_Folder
      &#9474;   &#9500;&#9472;&#9472; Ep_1_File
      &#9474;   &#9500;&#9472;&#9472; Ep_2_File

      &#9474;   &#9500;&#9472;&#9472; Ep_3_File
      &#9474;   &#9500;&#9472;&#9472; Show_A_Ep_1
      &#9474;   &#9500;&#9472;&#9472; Show_A_Ep_2
      &#9474;   &#9500;&#9472;&#9472; Show_B_Ep_1

      &#9474;   &#9500;&#9472;&#9472; Show_B_Ep_2

```

Except there's about 2200 files.  What's weird, though, is that none of the movie files were moved to that folder.

Now, this is my own fault because I didn't really understand the the command that did this.  That's what I'd like to learn now.  What part of the original command cause all files from all the other shows to be moved from their original directories to Show_Title_C, and what do I change so that this doesn't happen again?

Thanks in advance for the help.

---

### Post by nerdtron on 2015-08-09
```
sudo find ./ -mindepth 2 -type f -exec mv {} /media/PublicMedia/Television/Show_Title_C \;
```
So here, you use the find command
./ --> means that "in this current directory" (you can determine you current working directory by typing the "pwd" command)
-mindepth 2 --> meaning to search files at least one folder down from your current directory
-type f  --> find all files (not direcotries)
-exec mv {} /media/PublicMedia/Television/Show_Title_C   --> move all the matching files to the folder /media/PublicMedia/Television/Show_Title_C

So now, there is no undo command. You can't just revise the find the command to undo the changes. So what do you want to do now?

---

### Post by leunam12 on 2015-08-10
-mindepth 2 is one step down from where you are, you probably thought it was 2 steps down

---

### Post by mike196 on 2015-08-10
> **nerdtron said:**
> ```
sudo find ./ -mindepth 2 -type f -exec mv {} /media/PublicMedia/Television/Show_Title_C \;
```
So here, you use the find command
./ --> means that "in this current directory" (you can determine you current working directory by typing the "pwd" command)
-mindepth 2 --> meaning to search files at least one folder down from your current directory
-type f  --> find all files (not direcotries)
-exec mv {} /media/PublicMedia/Television/Show_Title_C   --> move all the matching files to the folder /media/PublicMedia/Television/Show_Title_C

I can't remember which folder i was in when I ran the command, but from the results, it looks like I was in /media/PublicMedia/Television, hence why only TV shows were moved and not the movies, right?

So if I had been in /media/PublicMedia/Television/Show_Title_C, this wouldn't have happened.

> So now, there is no undo command. You can't just revise the find the command to undo the changes. So what do you want to do now?

Yeah, the first thing I did after saying, "Oh, ****." was to look and see if there was an undo command.  Thankfully, it was a pretty straightforward fix.  Most of the episodes had the name of the show in the file name, so ```
[COLOR=#000000][FONT=Ubuntu Mono]find -type f -iname "*[Tt]itle*" -exec mv {} "/Title" \;[/FONT][/COLOR]
``` did most of what I needed to, and connecting to my Samba share did the rest.

Thanks for the insight on the original command.  One of the good things about Linux is you never make the same mistake twice.  The bad thing is you have to find out the hard way.

---

### Post by leunam12 on 2015-08-11
You don't have to find out the hard way, you can always keep backups of your files and system partition and if something goes wrong, recover from backup. You can also do a test run before running a command on your actual files. Create a few directories with subdirectories inside and some files and run your command. Then, when you are absolutely certain that you are going to get the result that you want, run the command on the actual files.

---

