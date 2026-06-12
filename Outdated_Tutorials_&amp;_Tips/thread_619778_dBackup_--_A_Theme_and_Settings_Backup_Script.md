---
title: "dBackup -- A Theme and Settings Backup Script"
date: 2007-11-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Dr Small on 2007-11-21
I don't get out much, so if I am posting this in the wrong place, please correct me. Ubuntu Forums is a big place, and I get confused easily :)

So, onto the script.

[CENTER][SIZE="4"]dBackup -- A Settings Backup Script[/SIZE][/CENTER]

_What it does_
Creates a tar archive of your .gconf and .themes folders, called dsettings.tar, by selecting "Backup" in the script. It uses zenity for GTK popups of asking you questions and prompting you with information.

To restore your settings, you run the script again and select "Restore" and this will extract the tar over top of your old configuration files of .gconf and .themes

It's basically made for taking your themes and menu settings from one account to another, as that was my original thought plan for all of this, and it worked for me.

_How to use it_
First, after you download it, you need to give it executable permission.
```
chmod +x dbackup
```

Second, in order for it to work properly, I just made it simple, it needs to be in your Home Folder. Example:
```
/home/ubuntu/
```

To run it, open a terminal, and run:
```
./dbackup
```

This will begin the zenity prompts until it completes with creating a backup tar archive file in your Home Folder with you .gconf and .themes folder in it.


Any advice, suggestions, recommendations, ideas, opinions are welcomed. I am a newbie at Bash programming, so you may see some way to improve it. 

[Download dBackup ]("http://php.8ez.com/drsmall/blog/wp-content/dbackup")

Thanks!
Dr Small

---

### Post by durand on 2008-04-19
Sounds like a good idea but surely people can just do it themselves? Maybe if you added scheduling...?

---

### Post by eha1990 on 2009-04-26
I attempted to use your script and I got the following error msg:

```

$ chmod +x dbackup
$ ./dbackup
./dbackup: line 1: syntax error near unexpected token `newline'
./dbackup: line 1: `<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">'

```

I followed your directions to the letter. I downloaded the dbacup script and saved into my home directory, changed the permissions on the file, and then attempted to execute the script at the command line.  I'm interested in backing up my custom theme that I'm using at this time in Ubuntu 9.04.  Please let me know if there is something else that I need to do to make your script work.

---

### Post by pheonix7117 on 2009-08-04
The download link is no longer available, so what is being downloaded is an html site saying something along the lines of "This location/file does not exist."

---

