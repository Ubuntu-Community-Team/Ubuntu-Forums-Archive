---
title: "Terminal For Beginners (Updated)"
date: 2008-10-01
forum: Outdated Tutorials &amp; Tips
---

### Post by anotherdisciple on 2008-10-01
*My favorite thread I have ever read on Ubuntu Forums is "Terminal for Beginners" by a guy named Kyral. I have decided to post a rewrite of his tutorial because his was written in 2005, and no one can comment on that thread anymore! I want some of the people who are new to Ubuntu to have a good place to learn about the terminal and why it is so useful. Also, I want this thread to be a place to request tutorials about other things that can be done through the terminal. If it seems like I'm just rewording his thread&#8230; I am&#8230; I do not intend to plagiarize his work; most of this is using his examples through my terminal. I have also _added some information_ that I think is useful. So here it is&#8230; Terminal For Beginners (Updated).*

The terminal is an extremely useful tool for getting things done quickly on your Linux system. It makes installing programs, deleting files, writing to files, etc. much faster in many cases. Most former Windows users are scared off when they are given advice on the forums that involves using the dreaded terminal, but it's not really as complicated as it sounds.


**Starting Your Terminal**

Let's start by opening a terminal:[INDENT]
**Ubuntu users:** (Applications > Accessories > Terminal)

Your default terminal is the Gnome Terminal.

**Kubuntu users:** (KMenu > System > Konsole)

Your default terminal is the Konsole.

**Xubuntu users:** (Applications > Accessories > Terminal)

Your default terminal is the Xfce Terminal[/INDENT]
When I open my terminal I get this:

```
nick@ubuntu:~$
```Let's break down what this means. The part before "@" is your username, in my case, nick. The part after "@" and before the colon ":" is they name of your machine, in my case it's my laptop called "ubuntu". The part between the colon and the "$" is very important, this is your working directory. Your working directory is the directory (folder) that you are currently "in".

Yours is probably like mine and says "~"&#8230; This is an alias for your current home directory. So really I'm in /home/nick. The "$" means you are a user, "a #" means that you are in a root terminal. I wouldn't suggest working in a root terminal.

So let's put it all together&#8230; this means that I am logged in as nick, at the machine named ubuntu, and I'm in the home directory. Simple enough, right?

**Navigating**

Now, how do we navigate around in this thing? I have a folder called "Music" in my home directory, so let's go there. We will use the cd (Change Directory) command to get there. Here is an example:

```
nick@ubuntu:~$ cd Music
nick@ubuntu:~/Music$
```Did you notice that my command prompt changed? The last part now says "~/Music" which means that I am now working in my Music folder, and the prompt tells me this so I don't forget. Cool huh? By the way, the terminal is case sensitive, so CAPS do matter. "Music" and "music" are two different things.

If I were using the GUI (Graphic User Interface &#8211; All those fancy windows, buttons, and such.) I could see what files were in that folder. How can I do that in the terminal? It's simple, use the ls (List) command! Let's try it&#8230;

```
nick@ubuntu:~/Music$ ls
12 Stones              Five Iron Frenzy  Of The Son
Audio Adrenaline       Forgiven          Party Music
Autumn Ashley          Great Days End    Point Blan_k
Because We're Loved    Jacob's Well      Radio Deadspace
Ben Harper             James Taylor      Relient K
Blank Blue Sky         Jars of Clay      Sevenglory
Bondservant            Jennifer Knapp    Shane and Shane
Bondservant Rough Mix  Jeremy Camp       SiDE Walk Slam
Casting Crowns         Jonah 33          The Migraines
Creed                  Kutless           The White Scarf Scandal
Dane Cook              Matchbox 20       Third Day
DC Talk                Michael Jackson   Vroom
Disciple               Mike Lee          Vroom Compilation
Everybodyduck          Mitch Hedburg     Warren Barfield
Family Force 5         Nirvana
nick@ubuntu:~/Music$ 
```The ls command shows you what is in your working directory. Do you see how that works? Speaking of the working directory, what if you forget? Yeah the prompt tells you, but there is another way to know. It's the pwd (Print Working Directory) command. This may sound useless right now, but if you ever decide to write a script, you may find this to be a useful tool.

```
nick@ubuntu:~/Music$ pwd
/home/nick/Music
nick@ubuntu:~/Music$

```Neat huh? You'll notice that right now the prompt and the output of pwd seem to say different things, but remember when I said that "~" is an alias to your home directory? So they basically say the same thing. No matter where you are in the file system, using cding to "~" will bring you back to your home directory, so remember that if you get lost. Watch&#8230;

```
nick@ubuntu:~$ cd /usr/bin
nick@ubuntu:/usr/bin$

```Hey wait! I'm stuck in /usr/bin, but how do I get back to the home directory? You probably already know, but I'll give you an example anyway.

```
nick@ubuntu:~/Music$ cd ~
nick@ubuntu:~$ pwd
/home/nick
```See? We're back at our home directory again.

It's probably a good time to mention that there are two ways to specify where you want to go. You can specify an absolute location, or you can specify a location relative to your working directory. If that is confusing, don't worry, examples are coming&#8230;

Remember when I cd'd to Music? That was relative to my current working directory. Music was a directory in my working directory, even though it's really /home/nick/Muisic, but the shell knew where I was and just sent me there. Now when I changed to /usr/bin, it was outside my home directory, so I had to use an absolute location (some people call it an absolute path in case you ever see someone tell you to navigate to /path/to/file) notice the leading /. That tells the terminal to start looking at the "root" directory (not to be confused with the superuser Root). Maybe this will clear it up&#8230;

```
nick@ubuntu:~$ cd /
nick@ubuntu:/$ ls
bin    dev   initrd          lib         mnt   root  sys  var
boot   etc   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  initrd.img.old  media       proc  srv   usr  vmlinuz.old
```Welcome to the base of your filesystem, the "root" directory. The location of every other file on your Linux computer is defined in relation to this. Now, let's get back to home! I bet you have that mastered by now!


Now, before we start doing things with files, there are a few aliases that I haven't mentioned yet.

".." refers to the directory directly "above" the working directory.

```
nick@ubuntu:~/Music/Vroom$ cd ..
nick@ubuntu:~/Music$
```

See what happened? I was in ~/Music/Vroom and I jumped "up" one level. This is very useful when you are in one directory, but you want to be in another directory that is in the same directory above you. Like this:

```
nick@ubuntu:~/Music$ cd ../Documents
nick@ubuntu:~/Documents$
```

See that? I changed from /home/nick/Music to /home/nick/Documents. Also, notice that it's an example of a relative location. Relative to ~/Music, ~/Documents is up one. Get it? Got it? Good!

Another alias, "." refers to your current working directory. Now you may be thinking, "Why do I need that?" Well, if you are asked to run an executable file, you are going to have to specify the absolute path to it, otherwise its going to go look for it in /usr/bin, /usr/sbin, and a bunch of other predefined places. By sticking a "./" in front of the filename, you just did give it the absolute path, using an alias, which is usually much easier and shorter. However, don't confuse this with files and directories that begin with a period. A period in front of a file means that it is hidden and won't show up in a normal ls command, or in the GUI. You have to use the ls &#8211;a( command for that in the terminal. And hitting (Ctrl + H) will show them in the GUI.


Well, now you should feel comfortable navigating around with the terminal; let's put that knowledge to use!


There are three basic commands for file operations. cp (Copy), mv (Move), and rm (Remove, which means to Delete). cp and mv work in similar ways, so we'll cover those first.

**Copying Files**

Let's take a look at what's in my home folder...

```
nick@ubuntu:~$ ls
Customizations  Documents  Music     Screenshot.png  Videos
Desktop         Downloads  Pictures  Tux Guitar
nick@ubuntu:~$

```

I'm pretty organized, so I had to take a screenshot to give you a simple example :D. So, let's make a copy of that screenshot.

The syntax for cp is:
```
cp [options] <location of file> <where you want the copy to be made>
```

So, you're probably wondering what "options" are. Well, they are options that effect how cp does what it does. If you ever wonder about the syntax and options of a command you can view the manual page for that command right from your terminal!

Just type:

```
man <command>
```

Oh, and you hit "Q" to exit that manual page. It took me a while to realize that... I used to just exit the terminal and open a new one :-?.

Common Options are:
[INDENT]-i (Interactive, Asks you to confirm every action)
-r (Recursive, Includes all the files, folders, and sub-folders, Required for directories.)
-v (Verbose, Tells you more about what it is doing.[/INDENT]


Now, we can use either relative or absolute paths (Remember those?). So, example time. Let's copy Screenshot.png to Screenshot2.png...

```
nick@ubuntu:~$ cp -v Screenshot.png Screenshot2.png
`Screenshot.png' -> `Screenshot2.png'
nick@ubuntu:~$

```

I used the verbose option to show you how it works. If I hadn't used it the second line wouldn't be there. Let's take a look at our Home folder now...

```
nick@ubuntu:~$ ls
Customizations  Documents  Music     Screenshot2.png  Tux Guitar
Desktop         Downloads  Pictures  Screenshot.png   Videos
nick@ubuntu:~$

```

... and there it is! Simple enough, right?

Now let's remove it!

**Removing Files**

rm uses this syntax:

```
rm [options] <path to file>
```

Some common options for rm are:
[INDENT]-f (Force; Force it do delete; This is needed for directories)
-i (Interactive; Same as cp except it's more important in this case)
-r (Recursive; Same as cp)
-v (Same as cp)[/INDENT]

In order to delete important system files on Linux you have to run the command as root (Using sudo... we'll get to that later). Now, look at those options and guess what this command would do (**Never run this command!!!**).

```
rm -rf /
```

You guessed it! It would delete EVERYTHING! You would need to hit Ctrl+C really fast, or you'd lose it all! (Ctrl+C kills any command in progress and returns you back to the prompt) I intentionally left sudo out of that command just in case someone wanted to try it.

Anyways, let's remove that screenshot copy. This time we'll use an absolute path instead of using an alias or removing it relative to our working directory. Oh, and we'll use the interactive option too.

```
nick@ubuntu:~$ rm -i /home/nick/Screenshot2.png
rm: remove regular file `/home/nick/Screenshot2.png'? y
nick@ubuntu:~$

```

Now it is deleted, and it asked my permission first. That's a good safe-guard to use. Some people even make an alias that always applies the interactive option to the rm command, but we'll talk about aliases later.

**Moving Files**

Let's look at mv. The syntax for mv is pretty much the same as cp...

```
mv [options] <location of file> <place where you want to put it>
```

... it has all the same options as cp, and some more. Check out the manual page... remember how do do that?

You can use mv to rename also. You can either move the file and keep the same name, or you can change the name. Let me show you... This time I'll use the verbose option and a relative path.

```
nick@ubuntu:~$ mv -v ./Screenshot.png ./DesktopPicture.png
`./Screenshot.png' -> `./DesktopPicture.png'
```

See... the verbose option told me what the command did, and the "./" made it relative to my working directory. The file was moved from /home/nick/Screenshot.png to /home/nick/DesktopPicture.png ... so basically I just renamed the picture. Get it?

You can move directories too. Here is an example... I have a folder "/home/nick/Documents/Excel Sheets", but I don't actually have any Excel files, so let's rename that folder to "Spreadsheets".

Now is a good time to talk about "escaping". Since that folder has a space between Excel and Sheets, we need to escape the space. If we did this...

```
mv -r /home/nick/Documents/Excel Sheets
```

... it would confuse what you are trying to say. It would try to move a folder called "Excel" to your working directory and rename it to "Sheets". Try it out sometime if that is confusing. So, how do we get it do recognize that space? We escape it with a "\". Let me show you...

```
nick@ubuntu:~$ mv  /home/nick/Documents/Excel\ Sheets /home/nick/Documents/Spreadsheets
nick@ubuntu:~$ cd Documents
nick@ubuntu:~/Documents$ ls
Julie's Documents  Nick's Music  Spreadsheets
Nick's Lessons     Product Keys  Word Documents
nick@ubuntu:~/Documents$
```

See, it changed the name of the folder. You could also use quotes to make it recognize that space. It would look like this...

```
mv /home/nick/Documents/"Excel Sheets" /home/nick/Documents/Spreadsheets
```

See? However, if want to _remove_ or _copy_ directories that have files in them... you will have to do it to the files in that folder too. So, you'll have to use the -r option.

**Uses For The Recursive Option**

So, if I wanted to delete that Spreadsheets folder I would have to do this:

```
rm -r /home/nick/Documents/Spreadsheets
```

That would delete the folder and all the files and all the sub-folders in it.

**Tab Completion**

Now for a time saver, tab completion. If you type out the first few characters of a path or command and hit tab, the terminal will try to complete the name for you. If its obvious what you want it will instantly complete it for you, saving you a lot of typing. If it's not so obvious, either type a few more characters and try again, OR hit tab once more and it will call up a list of possible completions.

For instance, if I want to type /home/nick/Documents... I could just type ~/Doc and hit tab. It would finish it for me. I needed Doc because I have other files or folders that start with "D". If I tried to type ~/D and hit tab a few times it would show me that I have 3 folders that start with D... let me show you:

```
nick@ubuntu:~$ cd /home/nick/D
Desktop/   Documents/ Downloads/
nick@ubuntu:~$ cd /home/nick/D
```

See? Tab completion, aliases, and relative locations are great time savers!



WOW! This has been a longer project than I thought... I now have even more respect for Kyral! lol! I think I'm going to do like him and do a part 2 and 3 since there is much more information to cover.

However, I want to know if this is helping people, and if it is worth the effort. His post was awesome to me, so I hope this is a good learning experience for the "Absolute Beginners". Let me know what you think!

---

### Post by anotherdisciple on 2008-10-01
If people are interested... I will add some things to this post:

-Wildcards
-Bash Aliases
-Sudo Commands
-Making Directories and Symbolic Links
-Updating and Upgrading
-Permissions
-Input/Output Redirecting
-And whatever others suggest!

---

### Post by walkingthecow on 2008-10-01
sed, awk, regular expressions, nohup, crontab, find, maybe some real terminal functions. No offense, but if you don't know ls, cd, grep, cat, vi, and other extremely basic terminal commands, you really have no place installing/using linux. Use a free shell and teach yourself some basic first.

---

### Post by puleo1333774 on 2008-10-01
> **anotherdisciple said:**
> If people are interested... I will add some things to this post:

-Wildcards
-Bash Aliases
-Sudo Commands
-Making Directories and Symbolic Links
-Updating and Upgrading
-Permissions
-Input/Output Redirecting
-And whatever others suggest!

can you post them please

---

### Post by anotherdisciple on 2008-10-02
> **walkingthecow said:**
> sed, awk, regular expressions, nohup, crontab, find, maybe some real terminal functions. No offense, but if you don't know ls, cd, grep, cat, vi, and other extremely basic terminal commands, you really have no place installing/using linux. Use a free shell and teach yourself some basic first.

Haha... you sound a little like an elitist... no offense. As Linux gets more popular there will likely be a large number of people who don't know how to use the terminal. However, they should learn it, because it fast and efficient in most cases. I've only been using Linux for a year now, and I think the terminal is one of my favorite parts of Linux.

Cat, grep, and vi(m) are good suggestions... thanks!

I'll try to get working on this over the weekend. That's 2 days away for me... I have a busy work schedule, but I will work on this soon.

---

### Post by imperius69 on 2008-10-02
Thanks for your tutorial, you should continue, newbies (like me) will/do appreciate.

one thing:

> See that? I changed from /home/nick/Music to /home/nick/Documents. Also, notice that it's an example of a relative location. Relative to ~/Music, ~/Documents is up one. Get it? Got it? Good!

didnt get this part, think it is "wrong" (typo or forgot something) on your post since the example dont shows any Document folder. :confused:

btw, what about creating folders and files?

---

### Post by anotherdisciple on 2008-10-02
> **imperius69 said:**
> Thanks for your tutorial, you should continue, newbies (like me) will/do appreciate.

one thing:



didnt get this part, think it is "wrong" (typo or forgot something) on your post since the example dont shows any Document folder. :confused:

btw, what about creating folders and files?



Good catch! Thanks... I fixed it in the original post.

---

### Post by natebenn on 2008-10-02
This was helpful to me as a total noob in the terminal world so thanks for the guide. I'm looking forward to learning more about using the terminal as I'm sure it's very powerful/useful. Thanks again.

---

### Post by sertse on 2008-10-03
Hey, just what to say, nice guide! helped a lot.

You may be interested to know there as a distro / Ubuntu remix called "INX" that has implemented some of this in a more interactive form. As in a series of exercises for you work through, rather than just reading a guide.

[http://inx.maincontent.net](http://inx.maincontent.net) 

or our chat at #inx at irc.freenode.org 

Again, thanks for te guide and couldn't wait till the next part

---

### Post by bundo on 2008-10-03
$ sudo rm -rf / 
commmand in the debian & ubuntu 
It is impossible

anotherdisciple Try on !

---

### Post by trustintrance on 2008-10-03
nice work!

---

### Post by kevdog on 2008-10-03
The addition of symbolic links and discussion of file permissions and making files executable would be good!!

---

### Post by anotherdisciple on 2008-10-03
> **bundo said:**
> $ sudo rm -rf / 
commmand in the debian & ubuntu 
It is impossible

anotherdisciple Try on !

REALLY?!?! I am tempted to try it, but I don't know if I trust anybody enough to potentially erase everything... haha...

Have you tried it before?

---

### Post by RequinB4 on 2008-10-03
At the very end, it might be prudent to show how easy it is to turn these commands into simple bash scripts.

Also, if you add too much stuff you might want to put a disclaimer that the guide goes from the beginning to the end in simple language - its not excluding things because they're too "hard" to articulate, it's teaching how it works.

---

### Post by bundo on 2008-10-04
> **anotherdisciple said:**
> REALLY?!?! I am tempted to try it, but I don't know if I trust anybody enough to potentially erase everything... haha...

Have you tried it before?

I had to try # rm -rf /
redhat distribution possible (centos...)
but
ubuntu , debian is impossible  : Were can not in command

The message
$ sudo rm -rf / 
rm: cannot remove root directory `/'

coreutils : remove.c
> 
 if (x->root_dev_ino)
    {
      if (cache_fstatat (AT_FDCWD, filename, &st, AT_SYMLINK_NOFOLLOW) != 0)
	{
	  if (ignorable_missing (x, errno))
	    return RM_OK;
	  error (0, errno, _("cannot remove %s"), quote (filename));
	  return RM_ERROR;
	}
      if (SAME_INODE (st, *(x->root_dev_ino)))
	{
	  error (0, 0, _("[COLOR="Red"]cannot remove root directory %s"[/COLOR]), quote (filename));
	  return RM_ERROR;
	}
    }


[IMG]http://ubuntu.or.kr/download/file.php?id=907[/IMG]

---

### Post by imperius69 on 2008-10-09
> **RequinB4 said:**
> At the very end, it might be prudent to show how easy it is to turn these commands into simple bash scripts.

totally agree with this :popcorn:

---

### Post by soho2014 on 2008-10-12
This was mostly a review for me, from stuff that I learned about Unix more than 25 yrs ago, but it was still quite helpful, thanks.:guitar:

---

### Post by sd401k on 2008-10-17
Great tutorial, I've been looking for something like this. Great use of examples, you should be a tech writer. You'd be great at that. Thanks again and I look forward to learning more about this fantastic OS.

---

### Post by meindian523 on 2009-01-03
> **bundo said:**
> I had to try # rm -rf /
redhat distribution possible (centos...)
but
ubuntu , debian is impossible  : Were can not in command

The message
$ sudo rm -rf / 
rm: cannot remove root directory `/'

coreutils : remove.c

I think what you need for that is ```
sudo rm -rf /*
```.Not that it means you should try  it though.

---

### Post by qns8dn3 on 2009-01-03
This is good job, Kyral and anotherdisciple.
I'd like to list things that I think should be added and that would help beginners.

*** How to copy some command from a web page and paste in to the terminal**
This should be mentioned for people wondering why Ctrl-V doesn't paste commands. Also to encourage readers to try commands from tutorials on the web.

*** How to copy some text from terminal and paste to somewhere else.**

*** using > and >> to save command output to files.**
Why would beginners need > and >>? Alice asks "my new keyboard doesn't work in Ubuntu! ..." in a forum. Bob replies "post the output of lspci command and the output of ...". Alice types lspci and other commands in a terminal and the outputs are too long. She has to manually copy paste those outputs if she doesn't know about > and >>. Mentioning > and >> would help lots of Alices.

*** danger of rm**
You should mention that files removed with rm cannot be recovered from Trashbin. Also mention trash-cli.

*** searching thru command history using Ctrl+R**
Terminals are less scary once one knows Ctrl+R.
Also add these
up, down : moving up and down thru command history
Ctrl+O : useful for running a sequence of commands again from command history.

*** which man page to read in order to learn about these terminal things in detail**
Beginners who want to learn more will enter 'man terminal' and the shell will answer 'No manual entry for terminal'. (For anyone wondering, the answer is: man bash)

*** various help commands : apropos, --help, man, info**
"Give a man a fish; you have fed him for today. Teach a man to fish ; and you have fed him for a lifetime"

*** GUI applications to read man pages and info pages**

*** the locate command**
Alice is following a tutorial on how to use X forwarding. The tutorial says "... Add blah blah blah to /etc/pew-ssh/ssh_config ..." but Alice finds that her Ubuntu system doesn't have the file called /etc/pew-ssh/ssh_config and that's because the tutorial is written for another Linux distribution called PewLinux and PewLinux and Ubuntu place ssh_config in different paths. But knowing the locate command, Alice can quickly find where the file is in her Ubuntu system. If she didn't know locate, she would use Places > Search for files ... and it's slow.

I don't know if you are going to introduce grep, but if you are going to, then also introduce ack-grep which is an easier alternative to grep.
If you will introduce diff, also introduce kompare which is a GUI alternative to diff.

Ok adding all of these seems like a lot of work. Not exactly. For example, you don't have to write how to read info pages with Konqueror, you can just add a link to a relevant entry in Konqueror documentation.

---

