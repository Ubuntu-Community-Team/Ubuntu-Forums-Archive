---
title: "How to find files in Ubuntu?"
date: 2024-08-03
forum: New to Ubuntu
---

### Post by firesdhgsht on 2024-08-03
Hello.
I installed catfish, fsearch, dolphin, searchmonky, recoll, file search, plasma search. None of these tools finds anything that I am looking for. They display random files or not a single one. Examples:

1. files modified after 1. Jan 2024: no files found, or in searchmonky: 20 files between 2013 and 2024
2. *.*: no files found
3. *: no files found
4. "": no files found

How is this possible? I have to go back to Windows just because Ubuntu has no working file search?

---

### Post by currentshaft on 2024-08-03
.

---

### Post by firesdhgsht on 2024-08-04
> **currentshaft said:**
> And you don't need to threaten going back to Windows, no one will care if you do, I promise.

:lolflag: It is not a threat. It is a fear :)

I entered 

```
find . -type f -newerct 2024-01-01

```

into all the programs I have but still no results.

---

### Post by euol on 2024-08-04
Try using this instead of newerct:

find . -type f -newermt 2024-01-01

---

### Post by firesdhgsht on 2024-08-04
Same result, no files found. No matter if I use catfish, fsearch, dolphin, searchmonky, recoll, file search, plasma search ...

---

### Post by tea for one on 2024-08-04
> **firesdhgsht said:**
> Same result, no files found. No matter if I use catfish, fsearch, dolphin, searchmonky, recoll, file search, plasma search ...
Ah, but did you open a terminal and enter the command?

---

### Post by firesdhgsht on 2024-08-04
No, how do I install that "terminal"?

---

### Post by TheFu on 2024-08-04
There are lots of ways to find things in Linux/Unix.  Remember that Linux is always a multi-user system, so if your account doesn't have access to know about the files you are looking for, then no command should display those to you.

The **find** command is quite extensive, but the manpage is complex and scary, so just search the web for "Top 50 Linux Find Commands" to see examples. [https://www.baeldung.com/linux/find-command](https://www.baeldung.com/linux/find-command) might be useful.  **find** scans from the directory you specify in the command. You can specify multiple directories or just use '/' and have it scan everything. Almost any property of a file or directory can be specified in the command, but it does take a little thought to look for exactly what you want.  I have about 20 different **find** commands that get used enough to have memorized over the decades, but often just get everything with the -ls option and use **egrep** to filter for and remove things in the list returned by find.  Because find scans the file system, the performance of the storage will matter. OTOH, the results should be accurate at the time.

The **locate** command is bonehead simple when all you know is part of a filename.  Locate is part of **updatedb** and scans the entire file system, building a DB of all files on it that aren't on temporary storage.  The DB gets updated daily via cron, but you can force a **sudo updatedb** to run.  locate returns answers nearly immediately since it doesn't have to scan the entire file system, but just a DB.  If the files I seek have been on the system longer than 1 day, I'll start with locate.

**Recoll** is like a personal google for our computers.  It uses helper tools to look inside files for the content. It also creates an indexed DB full of the contents and file properties. Recoll needs to be updated manually. This can be accomplished through the GUI Recoll tool as needed, or you can create a script and run that script automatically via cron daily or weekly or monthly.  Recoll indexing is much heavier than locate's indexing, so I run it weekly in the middle of the night.  On a system with about 45TB of storage, the recoll index can be large:
```
$ du -sh recoll-index/
12G     recoll-index/
```
OTOH, searching for stuff based on what's inside is google-fast.

So, if I wanted to find all the modified files (not directories) in 2024, I'd use **find** and the mtime option.  I think this is the command:
```
$ find / -type f -mtime -$(date "+%j")
```
If I wanted lots of time data along with the filename output, I'd add the -ls option:
```
$ find / -type f -mtime -$(date "+%j")  -ls 
```

Another way to to this that is less efficient would be 
```
$ find / -type f   -ls |egrep -w 2024 
```
However, that will find files with 2024 in line, not just part of the date, so if a file size is 2024 or an inode is numbered 2024, those will be found too.  

**egrep -w** looks for entire words, but it doesn't count numbers or punctuation, so '431**2024**' will be found too. Best to use the -mtime option with days ago calculated. Beware that **find** calculates "days" in a non-intuitive way. Best to carefully read the manpage about that, if you really care.

You can use explainshell.com to see what each option does if using the actual manpage on your system is scary. However, the local manpage will have documentation for the correct version of the programs on your system. No website will have that exact documentation. Most of the time, commands and options don't change too much, but over 5+ yrs, they do, often adding new options that are more convenient.

For example, I've been using find for 30 yrs and had never seen the -newerct option.  So, I just checked and it isn't in the find command on my 20.04 or 22.04-based systems.  So, either that option is a mistake or it is VERY new.

BTW, Linux/Unix doesn't really care about extensions. That's a common mistake made by people used to non-Unix-based OSes.  "*.*" just insists that a file have a '.' in it. It won't find any files without a '.' in the name, which would remove nearly all compiled programs from being found.  Use "*" if you want to find all files, or better, don't bother trying to specify any name at all.  

Always remember that Linux names are case-sensitive, so if you don't know the exact case for a filename/directory name, it is best to force a case-insensitive search.  That applies to locate, find, grep, egrep, and bash scripts (more things too).

---

### Post by tea for one on 2024-08-04
> **firesdhgsht said:**
> No, how do I install that "terminal"?
Its nigh on impossible to explain but there is a hidden bit of Ubuntu wizardry.
Press these three keys simultaneously;-
```
Ctrl Alt T
```

---

### Post by yancek on 2024-08-04
>  No, how do I install that "terminal"? 				

If you can't manage the suggestion in post 9, if you have a recent Ubuntu installed (you failed to indicate your release version) you should be able to left click on the Activities tab generally shown in the upper left of the Desktop, type in terminal and hit the Enter key.  Based on what you have posted, you need to do a lot of reading as this is very basic.  You could start with the Desktop Guide at the link below.

[https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)

---

### Post by TheFu on 2024-08-04
> **firesdhgsht said:**
> No, how do I install that "terminal"?

This is long, since installing a terminal will likely not be all that helpful to someone who doesn't know what a terminal program is and how to use it at a beginner lever.

'terminal' is a type of program, not a specific program.  There must be 50 different 'terminal' programs and at least 1 is already installed on your system, usually based on the DE.  Often, in the _Administration_ or _System_ menu, there will be something with "term" or "terminal" in the name.  Because the menu name and the program name seldom match in Ubuntu, it is hard to guess what your system calls it.   Gnome Terminal, LXTerm, Mate-Terminal, xterm, uxterm, and many, many, others.   Non-Linux computers might use something like PuTTY.  While PuTTY is available on Linux, almost nobody uses it there, since every other terminal program is more standard and has great features already.

A terminal is a text command window with great power.  Sorta like the old MS-Dos command prompt, but much, much, more flexible.  MS-Windows added at tool they call "PowerShell" in their attempt to provide a Unix terminal-like interface.

In Unix-like OSes, a terminal window usually provides the interface to your shell.  On Ubuntu Desktop variants, the default shell program is bash, but there are 20 others and you can change the shell for your userid, if you like.   On an Ubuntu Server, which doesn't have any GUI, the shell is all we get after login. No GUI. Just a blank screen with something like this:

```
thefu@deneb:~$
```
That is a shell command prompt. It awaits a command, which there are many thousands of possible commands, each command has 1-50 options.  So, '**find**' is a command.

Underneath the GUI you are used to seeing/using, the shell is the main tool on your system.  Entire books have been written about using shells and getting the most from your shell of choice.  sh, ksh, bash, zsh, fish, csh, tcsh, [https://tldp.org/LDP/Bash-Beginners-Guide/html/sect_01_01.html](https://tldp.org/LDP/Bash-Beginners-Guide/html/sect_01_01.html)  has more, if you care.   A more friendly way to learn about the shell and how to use it is in this no-hassle, free, PDF book, [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php)  I've used that book in my Beginning Linux classes at the local University.  A dead tree version can be bought in almost any book store, or the free PDF is fine too.

---

### Post by firesdhgsht on 2024-08-04
Thank you for all the suggestions but I need to get work done, I cannot read 20 pages beginner guide just to find some files. I just want a simple input field where I can put in ***.*** and restrict the result by date. Simple, you know, like usable for the average human, simple like in Windows 3.1. I am definitely not using that terminal like I want to code BASIC on a C64 :D

---

### Post by firesdhgsht on 2024-08-04
Oh here is my system: Intel multicore, 32 GB RAM, Kubuntu 24.04, Plasma 5.27.11, Kernel 6.8.0-39

---

### Post by firesdhgsht on 2024-08-04
Thank you for the "dead tree version" help :D But really, I just want to compile a list of files across multiple folders that I have worked on in the past 6 months. I am a user. I open the machine get things done and close the thing. I thought someone here might have the same approach and figured out how to use Linux like a normal computer :)

---

### Post by oldfred on 2024-08-04
I just do not find it difficult to open terminal and copy paste a command into terminal.
I often have to edit line but save those I use into a file.

[FONT=monospace][COLOR=#000000] ```
find /home/$USER -name "*.txt"  -newermt "2024-01-01" -exec ls -ils {} \;[/COLOR]

```

You can then easily edit date or file name to include or exlude those you do not want.


[/FONT]

---

### Post by VMC on 2024-08-04
> **firesdhgsht said:**
> Thank you for all the suggestions but I need to get work done, I cannot read 20 pages beginner guide just to find some files. I just want a simple input field where I can put in ***.*** and restrict the result by date. Simple, you know, like usable for the average human, simple like in Windows 3.1. I am definitely not using that terminal like I want to code BASIC on a C64 :D

Why again did you leave Windows? Installing Linux without any knowledge of its usage is going to take sum time, as in research, and reading.

 [Linux For Dummies]("https://www.dummies.com/article/technology/computers/operating-systems/linux/linux-for-dummies-cheat-sheet-209505/") perhaps.

---

### Post by firesdhgsht on 2024-08-04
> **VMC said:**
> Why again did you leave Windows? Installing Linux without any knowledge of its usage is going to take same time

... because just like I do not need to read the 400 pages manual on a Volvo only because I drove a Merc before :)

So I opened that "hideous" terminal and got my list of files (I still cant believe that there is no GUI that can do that, unreal ](*,) ). How do I move that list to Dolphin so I can create a zip? Thanks

---

### Post by Holger_Gehrke on 2024-08-04
> **firesdhgsht said:**
> How do I move that list to Dolphin so I can create a zip? Thanks

Why go to that trouble when you can just let 'find' do it ? 'find' has an option '-exec' which will execute a program with the found files as parameters. So you could run
```

find /home/$USER -name "*.txt"  -newermt "2024-01-01" -exec zip archive.zip \{\} \+

```
and that should produce an archive.zip in the current working directory with all the files 'find' has found .

And switching operating systems isn't like switching to a different brand of the same product, it's more like going to a different country ... a lot of things might be similar, but there are differences. With Linux the command line - which Windows has mostly abandoned - is alive and well and considered the ultimate power tool. This is mostly because it's a lot easier to write tools that work from the command line then to write a GUI tool. Also a GUI just doesn't make much sense for some simple tools, e.g. 'wc' (word count) which counts characters, words, and lines in a simple text file. With a GUI that kind of program will only exist as an option in some larger program.

Holger

---

### Post by Dennis N on 2024-08-04
You say you tried it, but actually FSearch can be used to create a text file listing all the files that meet a desired last modified criteria within a certain folder (like your home folder) OR within a selection of multiple folders.

---

### Post by bobunderwood99 on 2024-08-04
.

---

### Post by ActionParsnip on 2024-08-05
I recommend the find command in terminal, super simple and fast
```

find / -type f -newermt '01 Jan 2024 00:00:01'[FONT=inherit]
[/FONT]
```[FONT=inherit]
Will give only files from only this year[/FONT][/COLOR]
Obviously change "/" to the folder you want to search. Eg:
```

find $HOME -type f -newermt '01 Jan 2024 00:00:01'

```
Will search your users home and display only files that have been modified this year

Other options include:
```

-newerXY reference
          Compares the timestamp of the current file with reference.   The
          reference  argument  is  normally the name of a file (and one of
          its timestamps is used for the comparison) but it may also be  a
          string  describing  an  absolute time.  X and Y are placeholders
          for other letters, and these letters select which time belonging
          to how reference is used for the comparison.


          a   The access time of the file reference
          B   The birth time of the file reference
          c   The inode status change time of reference
          m   The modification time of the file reference
          t   reference is interpreted directly as a time

```

---

### Post by TheFu on 2024-08-05
> **firesdhgsht said:**
> ... because just like I do not need to read the 400 pages manual on a Volvo only because I drove a Merc before :)

So I opened that "hideous" terminal and got my list of files (I still cant believe that there is no GUI that can do that, unreal ](*,) ). How do I move that list to Dolphin so I can create a zip? Thanks

You don't need to do that.  Just feed the list of files from the **find** output into the zip program.  BTW, it works the same on DOS/Windows in the command prompt there too.

When I was knew to UNIX, I often asked small questions because my history with OS/2, MS-DOS and TSO/ISPF had my mind thinking that the way those OSes forced things to be done was the only way.  Alas, an old guy slapped me and said, to ask questions for what my final goal was, since putting 10 small steps together to accomplish things the MS-Windows way was seldom the way anyone would do it on UNIX.  So, I started asking for the final goal, instead of asking for individual steps.

If you are trying to copy files off to be shared with other people, there are better ways.
If you are trying to make backups or backups of recently changed files, there are better ways.

Just sayin'.

There is a problem feeding filenames/directories that begin with a '/' into any archive program.  The full path will be retained, which means it will want to be restored to exactly the same place.  On a different computer, the exact directories won't exist and many not be something your userid can create.  This is one of the reasons that Unix-like OSes use different archive tools that other OSes.  On Linux, there are many different versions of ZIP - and some aren't compatible with that other OS at all.   Instead, if you have 500MB of files are less, I'd strongly suggest using a tgz archive for sharing files.  GNU Tar is good at this sort of stuff and if you save the exact command to a file, called a script, you'll be able to run it over and over and over and over and get the same results for years.  Tar isn't a good backup tool for a number of reasons.  It used to be the standard backup tool used when HDDs were 1-2GB in size, total.  Now that we have 4G-20TB HDDs, the tar storage format isn't a good choice, I'm afraid. It has many of the same problems that ZIP has for larger data.

By using a little script, you can automate the running of the backup so it is done when you aren't there, once a day or once a week. Having consistent, correct, results. is very important.  It is harder to automate GUI stuff, which is why Unix people prefer using CLI tools and scripts.  We won't accidentally forget to check a box in the GUI and end up with results that aren't what we need.  Consistency matters.

To be honest, I don't know if there is a GUI program that will do what you want.  I've never bothered looking. Most of my computers don't have any GUI, so I can learn 1 way to accomplish a goal that works everywhere, of I can learn 1 way that only works on 2 of my computers, maybe.  Of course, your needs are different.    Google found Ark - which is a KDE program: [https://opensource.com/article/22/2/archives-files-linux-ark-kde](https://opensource.com/article/22/2/archives-files-linux-ark-kde) and [https://docs.kde.org/stable5/en/ark/ark/ark.pdf](https://docs.kde.org/stable5/en/ark/ark/ark.pdf) Looks like Ark and Dolphin integrate together in KDE.  Might be useful for your needs.  IDK.  It may not.
> 
Advanced Batch Mode
Ark has an advanced batch mode to manage archives without launching a graphical user inter-
face. This mode allows you to extract or create archives and add files to them.
The batch mode is documented in Ark’s man page  
[https://manpages.ubuntu.com/manpages/noble/en/man1/ark.1.html](https://manpages.ubuntu.com/manpages/noble/en/man1/ark.1.html) is the manpage for the 24.04 version of ARK.  The manpage is also on your computer.  Just use **xman** to find it.

---

### Post by firesdhgsht on 2024-08-06
Thank you for all the hints and explanations. 
When I asked the question I was hoping for 1 single reply "go there, check this box, done" :D ... now we have a 3 pages thread :lolflag:

"So, I started asking for the final goal, instead of asking for individual steps."
... that is probably still the problem with Linux. As a layman user I do not want to ask questions, nowadays I expect a common tool like a laptop to be self explanatory at least for the rudimentary daily tasks. 

Nevertheless I dug deeper and figured out that KFind is the best option. It does not take "/*" but it takes "" to find all files created/modified in a given time span. The problem is, that KFind cannot distinguish between created and modified. Anyway, I go with that for now. Ark is used in Dolphin for archives and works great.

---

### Post by TheFu on 2024-08-06
> **firesdhgsht said:**
>  
"So, I started asking for the final goal, instead of asking for individual steps."
... that is probably still the problem with Linux. As a layman user I do not want to ask questions, nowadays I expect a common tool like a laptop to be self explanatory at least for the rudimentary daily tasks. 
 

And we still don't know your end goal ....

---

### Post by currentshaft on 2024-08-06
joy

---

### Post by firesdhgsht on 2024-08-08
Laziness is my sole motivation to use a computer. What's your point?

I paid good money for my Linux laptop. I think I am "entitled" to expect it can find a file.... without me having to learn terminal commands.

---

### Post by aljames2 on 2024-08-08
The Linux desktop environment GUI tools give you maybe 5% of the power of what your Linux laptop is capable of.  Some here may correct me which I welcome…it may be 1%.

Your complex search criteria & package need is not a basic thing and most GUIs are not written to anticipate all variations of complexity a user may need or expect. In these cases you need to learn (with patience), how to leverage the more capable commands under the hood. Raising the hood on occasion in Linux is really a pre-requisite. All the folks here have given you the solution, it just works. 

In hindsight, if I were in your shoes again, the first five things I would learn in Linux are: 1) Linux permissions, 2) pwd command, 3) cd command, 4) ls command, & 5) find command

---

### Post by firesdhgsht on 2024-08-09
Thank you for the encouragement. But I am really an end user. I know  that Linux is safer than any other OS and that is why I use it. I know  not to log in as root but this is how far I go. I have no time to learn  any terminal command, I need to get things done, I want to grab the  picture I need with my clumsy finger on the touchscreen, throw it on the  hard drive, unplug the drive, close the lid and go. I was told that  works with Linux, hence here I am, even if I leave 95 % performance on  the table :grin:

---

### Post by currentshaft on 2024-08-09
4

---

### Post by yancek on 2024-08-09
Do you know if your Kubuntu installed entirely on a single partition 
If you have multiple partitions or multiple hard drives with multiple partitions with data on which to search, are they accessible (mounted)?
Do you know what the owner:group is for any other partitions if there are any?  Owner:group and permissions on Linux are a big part of what makes it more secure.  You need to be aware of this.

Have you read the page at the link below "File Searching on Kubuntu"?  It is 5 steps.

[https://www.ubuntubuzz.com/2021/10/file-searching-on-kubuntu.html](https://www.ubuntubuzz.com/2021/10/file-searching-on-kubuntu.html)

---

### Post by firesdhgsht on 2024-08-16
It is only one single partition. 
Thanks for the link. Yes I did that. I go with KFind for now.

BTW, I didnt buy a Ferrari, I dont care about performance, I got a Volvo with 9 airbags (Linux) because I care about safety :)

---

### Post by wyattwhiteeagle on 2024-11-20
> **firesdhgsht said:**
> ...I got a Volvo with 9 airbags (Linux) because I care about safety 
Even a Volvo with 9 airbags (Linux) comes with an owner's manual (Terminal).
How little would you know about that Volvo without just as much as simply opening the owners manual!
That is unless you're the designer and manufacturer of that 9-airbag Volvo.
That's just as much safety as the 9 airbags on any make/model.


If you never learn one single terminal command, you're bound for Linux trouble guaranteed.
Some of the Linux maintenance require's you to use the terminal and terminal code's at least once.


PS. I'm an end-user too and I hate doing things the way you describe here.


Rule of thumb 1: Gotta maintain it if you wanna keep usin' it.
Rule of thumb 2: If you want our help, you gotta meet us half way.

This thread is full of info from people trying to help you. And half blindedly at that.
Linux is not a "here's the one thing with all the tricks to fix all your problems" kind of system.
And you won't get such rediculous "one trick fixes all" answers here.

---

