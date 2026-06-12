---
title: "A send-to-trash command for the shell"
date: 2006-01-31
forum: Outdated Tutorials &amp; Tips
---

### Post by agapito on 2006-01-31
First of all, I'm sorry for posting a howto with such a lame and easily replaceable one line shell script, but I think it will help keep the newbies and the distracted and/or lazy (like me! :)) a bit safer.

Have you ever done a deleted a file in in the shell, only to find out 3 seconds latter that you made a mistake?  ](*,)  This is what I do to keep that kind of trouble away from me:

1. Open you favourite editor and create a file called "del" (or whatever you wish to call it, but i'll use del in this exemple). Let's say it's gedit:

```
gedit ~/bin/del
```

2. Write this there:

```

#!/bin/bash
mv -vi -- "$@" $HOME/.Trash

```

You can see this in the manpage, but anyway:
v      =verbose (i.e. explain what is being done)
i       =interactive ( prompts you before overwriting)
--     = so you won't get in trouble with names that start with a -
"$@" = everything in front of the command (which in this case is our "del" shell script)

3. Save it.

4. Now let change the permissions of the file, so that you can execute it.

```
chmod -v 755 ~/bin/del
```

5. And that's it. Now, you can do things like:

```
 del file1 file2 directory1/  directory2/ -strage_filename 
```

and it all gets send to the Trash (a.k.a. Recycle Bin). ;)


[COLOR="Red"]Note[/COLOR]: I assume you have a "bin" dir in you home directory. If you don't you have two options:
1. Create it...
```
 mkdir ~/bin 
```
and add it to your PATH variable...
```
 echo "export PATH=$HOME/bin:$PATH" >> ~/.bashrc 
```
You must use two > signs ( i.e. >> like above) or else you will overwrite your .bashrc file.
Note that you must restart the terminal, reload the env variables
```
. ~/.bashrc 
```
or do ```
 export PATH=$HOME/bin:$PATH 
```
for the ~/bin directory to be in you PATH variable. 

2. Save your file to /usr/local/bin or /urs/bin modifying the howto accordingly.


**You need more? **
I made a "volume-aware" version of del, which autodetects the volume's Trash directory and deletes to there. It has interactive overwrite and rename, command line options and can be custumized to override the volume default trash directory. I'm attaching it to this howto. You just have to download 
it, extract it (tar xvzf del.tar.gz) and move it to ~/bin, /usr/bin or /usr/local/bin.
For some help do
```
del -h
```

I did a great deal of testing but, since it's a relatively large script it may still have some bugs. I don't expect them to be dangerous because only "mv" command are used, but consider yourself warned. ;)

Any feedback, good or bad, and/or sugestions are **highly** apreciated.
I'm not explaining it step-by-step here, but I'll answer any questions about it.

Enjoy. :D

---

### Post by robert_pectol on 2006-02-02
> First of all, I'm sorry for posting a howto with such a lame and easily replaceable one line shell script...
No apologies necessary. Let's face it, it's easier to remember, "del <filename>" than it is to remember, "mv -vi -- <filename> ~/.Trash" any day! Great little oneliner in my opinion! Sometimes simple solutions work better than complex ones anyway. Thanks!

---

### Post by meborc on 2006-02-02
yeah.... good how-to... i, for one, delete often files that might be needed afterwards... :D ... i guess your solution will prevent a lot of folish things to happen in the future... thanks :)

---

### Post by agapito on 2006-02-02
Thank you both for your feedback. :)

---

### Post by NMUrugbysteve on 2006-02-02
This would be really good to use when installing ubuntu for someone who's computer illiterate. Maybe even put in an alias as "rm"

---

### Post by Subbu.exe on 2006-02-03
Thanks!

---

### Post by BobSongs on 2006-02-08
hehehe. Fun!

Uhm, just one comment. You suggested creating **del** in ~/bin:> ```
gedit ~/bin/del
```I came across these two problems as a newbie.
[LIST=1]
[*]The ~/bin folder doesn't naturally exist. I didn't realise this and initial attempts to save the file were fruitless. Once created **del** was easily saved.
[*]**del** didn't work. But that makes sense as it's not in any path the system uses. When transferred to the system's **/bin** folder it worked perfectly. 
[/LIST]Suggested replacement code:```
sudo gedit /bin/del
```

---

### Post by bored2k on 2006-02-08
```
#!/bin/bash
mv -vi -- "$@" $HOME/.Trash
```
I am **very** against this howto. Say I'm browsing another hard drive and I run that command to delete a file. You know what It will do? It will have to move by file (possibly a big +300mb file) over to where my $HOME partition is. **That's** horrendous. For this to be actually good, a more advanced script would be needed. One that copied the file to a .Trash of **that** particular drive. Not all of us have just one partition.

---

### Post by engla on 2006-02-08
[QUOTE=BobSongs]Suggested replacement code:```
sudo gedit /bin/del
```[/QUOTE]

No, put it in /usr/local/bin/

---

### Post by stalefries on 2006-02-08
Worked great, guys, thanks!

---

### Post by slavik on 2006-02-11
doesn't rm move files there on its own? since it is a system command? and once you rm from trash it actually removes it from the ssytem?

---

### Post by Gandalf on 2006-02-11
[QUOTE=bored2k]```
#!/bin/bash
mv -vi -- "$@" $HOME/.Trash
```
I am **very** against this howto. Say I'm browsing another hard drive and I run that command to delete a file. You know what It will do? It will have to move by file (possibly a big +300mb file) over to where my $HOME partition is. **That's** horrendous. For this to be actually good, a more advanced script would be needed. One that copied the file to a .Trash of **that** particular drive. Not all of us have just one partition.[/QUOTE]
I totally agree with bored2k, I have NFS partitions myself holding everyfile that is large, what if i delete a 1Gb file on my NFS? I have to wait the transfer of 1gb  over a wireless network? nah i don't think so, This script must be more advanced, it must check if the folder holding the file is within the home partition then move it to home, otherwize it must get some information from mtab in order to determine the .Trash path...

---

### Post by agapito on 2006-02-11
Thank you for your comments BobSongs. I always have a ~/bin directory (it really good place to keep my scripts) so I forgot that it doesn't exist. I added a note on this subject to the howto.

As for Bored2k and Gandalf's remarks, they were a great idea and a good incentive. I had some free time and came up with a script that does what they said. Please tell me what you think of it.

---

### Post by bored2k on 2006-02-12
Ok, after testing it out and fixing a silly error I made (**not** opening nano with the **-w** parameter and working with codes is a bad thing), I finally tried this script again. This time around, it's a lot better :-). I was expecting agapito to just set the script to create .Trash dirs, but I guess he knew better ;).

I have one small recommendation for the author. Why print **every** file the script deletes instead of just printing a small but informative message in the veins of "Moved N files to trash.". Heck, most of the similar scripts/applications do not even print any output, but that's just personal preference.

To illustrate my point, consider the following:
```
[white@black D]$ mkdir beta
[white@black D]$ cd beta/
[white@black beta]$ touch 1 2 3 4 5 6 7 8 9 10 andSoOn
[white@black beta]$ ls
1  10  2  3  4  5  6  7  8  9  andSoOn
**[white@black beta]$ [size=3]del *[/size]**
`1' -> `/mnt/baka/.Trash-white/1'
`10' -> `/mnt/baka/.Trash-white/10'
`2' -> `/mnt/baka/.Trash-white/2'
`3' -> `/mnt/baka/.Trash-white/3'
`4' -> `/mnt/baka/.Trash-white/4'
`5' -> `/mnt/baka/.Trash-white/5'
`6' -> `/mnt/baka/.Trash-white/6'
`7' -> `/mnt/baka/.Trash-white/7'
`8' -> `/mnt/baka/.Trash-white/8'
`9' -> `/mnt/baka/.Trash-white/9'
`andSoOn' -> `/mnt/baka/.Trash-white/andSoOn'
[white@black D]$ echo "OH THE HUMANITY"
OH THE HUMANITY

```
Deleting ten (10) mere files just cluttered this relatively small terminal window. Imagine the atrocity that would occur if I decided to delete over twenty (20) files.

By the way, good job agapito :).

---

### Post by agapito on 2006-02-12
Hi!
Line 43 is a comment., so it souldn't give an error... Did you edit it?
I expect the script to detectect the volume on it's own, so you shouldn't have to edit it unless you want to override the location of the trash directory. If you do you must edit these lines:
```

                #directory)
                #trash=
                #;;

```

Example:
```

                /mnt/xxx/D)
                trash=/mnt/xxx/D/.use-this-trash-dir
                ;;

```

Note that the /mnt/xxx/D must be the mount point for a read-write volume, or it won't be detected.

---

### Post by bored2k on 2006-02-12
Yes, it was just a small boo-boo nano without the -w parameter made. Read my above post.

---

### Post by agapito on 2006-02-12
Thank you for your prompt response. :)
Thats a good tip. I like to know where the files are going, so i'll keep the verbose output but just as an option, and implement the "count-deleted-files" feature. Check it out shortly. ;)

---

### Post by agapito on 2006-02-12
I've uploded my new del script wich includes some commnad line options, namely: verbose mode is now optional (using -v or --verbose) and i added a short usage help (using --help or -h).

As a side effect you won't be  able to delete files named like one of the options above( example: --verbose), but who names a file like this anyway. :) 

Win some, lose some. 
Enjoy! ;)

---

### Post by dbw on 2006-02-22
nice work, agapito.

---

### Post by tseliot on 2006-03-05
Guide ported to the UDSF:
[http://doc.gwos.org/index.php/Gnome_A_send-to-trash]("http://doc.gwos.org/index.php/Gnome_A_send-to-trash")

---

### Post by varunus on 2006-03-05
Great howto!  Stops me from messing things up permanently from the console.

One other thing to add:

If you open your ~/.bashrc file using gedit from a terminal:
```
gedit ~/.bashrc
```

Under the aliases section, add the alias 
alias rm='del'

That way, all rm commands will just be del!

I know that some ppl may not want to do this, but you can alias something else to the original rm command if you need it.

---

