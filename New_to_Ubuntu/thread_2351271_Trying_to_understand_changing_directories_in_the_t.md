---
title: "Trying to understand changing directories in the terminal"
date: 2017-02-01
forum: New to Ubuntu
---

### Post by newbie632 on 2017-02-01
As you read this post please keep in mind that I just started using Ubuntu today. I am a total newbie. Here is my problem. I recently tried to download and install the Tor browser. I placed the downloaded file on my desktop. After I opened the command terminal. As per instructions I found on Youtube. I changed directories to my desktop and now my directory is:

name@name-desktop:~$

How I get back to my original directory? Please help!

---

### Post by howefield on 2017-02-01
Typing

```
pwd
```

and pressing enter will print the current path.

You appear to be in /home/name at the moment.

This page might give you a few pointers : [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by #&amp;thj^% on 2017-02-01
Try this along with the great link that howefield gave you.
```
cd
```
This equals or means change directory and usally takes you back to the default location.
```
cd Desktop
```
Will take you to the Desktop...etc, etc.
Short example:
```
[me@silversurfer Desktop]$ pwd
/home/me/Desktop
[me@silversurfer Desktop]$ cd
[me@silversurfer ~]$ pwd
/home/me


```

---

### Post by ajgreeny on 2017-02-01
Don't forget that this is Linux and in this Desktop is not the same as desktop; Linux is case sensitive, unlike Windows.

---

### Post by newbie632 on 2017-02-01
Sorry guys but neither suggestion is working.I think I messed up bad already.

---

### Post by howefield on 2017-02-01
> **newbie632 said:**
> Sorry guys but neither suggestion is working.I think I messed up bad already.

Would help to know exactly what you want to do.. "*back to my original directory*" - no-one here will know where you started or where you want to go to unless you are a bit more specific. Also, please post terminal input and output back here so others know exactly what you have done, and place the text between [noparse]```

```[/noparse] tags to aid readability.

Perhaps closing your terminal and relaunching would help, generally that would place you in your /home folder. As I said..

```
pwd
```

will tell you where you currently are.

---

### Post by QIII on 2017-02-01
Hello!

Would you please post the exact text of the commands you are issuing and the results being returned?

Thanks.

---

### Post by Bashing-om on 2017-02-01
newbie632; Hello;
Panic not. Just proceed in a calm and orderly fashion.
And, remember - to be new is not a sin ... we were all new at one time .. and believe me we do understand.

This is 'buntu - with a LiveDVD and Good BackUps . You can not mess up so bad that there is no recovery . I promise.

At this point define your problem - exactly .
If it but returning the (P)resent (W)orking (D)irectory to your default location of your /home;
```

cd

```
as advised will do that for you .

And yes, linux is different, and like learning a new language it will take some use and time to learn.
We are here to help you over those rough spots .

[INDENT][INDENT]ask and it shall be given
[/INDENT][/INDENT]

---

### Post by geeksmith on 2017-02-01
You can get back to the previous directory you were in with this command:
```
cd -
```

Changing directories isn't harmful. It's what you do when you're in a directory that might be harmful.

If you're not sure where you were, you can probably scroll up in your terminal window to see. You can also hit the "up" arrow to see previous commands, and possibly find a "cd" command you typed before.

---

### Post by ajgreeny on 2017-02-01
Unfortunately there is no manual **man cd** on my OS at least, which might have helped you, but for example
[LIST]
[*]**cd** will get you back to the default directory, ie, where terminal starts when you open it
[*]**cd  ..** will move you up one level in the system, eg from /home/user/Videos/home-videos to /home/user/Videos
[*]**cd /full/path/to/folder** will take you to that folder in the filesystem
[/LIST]
I hope that helps a little, but as Bashing-om says, don't panic; hang in there and you **will** get the hang of it.

EDIT:
I just remembered a site where you can find lots of help with Linux commands; it shows the man pages of all including **man cd** which I do not have on my system.
[https://ss64.com/bash/cd.html](https://ss64.com/bash/cd.html)
and all other commands are listed at [https://ss64.com/bash/](https://ss64.com/bash/)

---

### Post by jv10 on 2017-02-02
Just for your future reference, you can also List the content of the directory you are in. With:

```
ls
```

It will show you all the folders/files in that directory. I found it easier to navigate with this.

---

### Post by Impavidus on 2017-02-02
> **newbie632 said:**
> I changed directories to my desktop and now my directory is:

name@name-desktop:~$

How I get back to my original directory? Please help!The prompt shows (unless you change it by modifying your .bashrc)```

<user name>@<host name>:<working directory>$
```So that prompt above indicates your working directory is ~, which is short for your home directory, which should be the directory where you started. Maybe you didn't succeed in changing directory? That should've given you an error message.

> **ajgreeny said:**
> Unfortunately there is no manual **man cd** on my OS at least, 

Neither is there on my system, but there is **help cd**. That makes some sense, as cd is a shell build-in and not a separate program that can be installed along with its manual page files.

---

### Post by kpatz on 2017-02-02
How did you download the Tor?  Using a browser such as Firefox?  By default browsers save downloads to the Downloads folder (directory), not Desktop.  So unless you changed where it downloaded to, it may be in Downloads.

Here's more on using directories in the terminal.

The prompt you get in the terminal is in the format **user@host:dir$** where **user **is the username you're logged in as, **host** is the name of the system (what you named it when you installed Ubuntu), **dir **is your current directory (if it's /home/yourusername the directory will appear as a ~).  In fact, any path starting with ~ is relative to your home directory, so ~/Desktop is the same as /home/yourusername/Desktop.

Changing directories is done with the **cd** command.  You can specify a full path starting with / or you can specify a path relative to your current location, so, if you're in your home (~) directory, and you want to go to your Desktop directory, any of these commands will work:

```
cd Desktop
cd ~/Desktop
cd /home/yourusername/Desktop
cd $HOME/Desktop

```
Of course, the 1st of these will only work if you're already in your home directory.

Here I am changing to my Desktop directory on my computer catzfs01:```
kpatz@catzfs01:~$ cd Desktop
kpatz@catzfs01:~/Desktop$

```

If you want to see the full path of where you are, you can use the **pwd **command.```
kpatz@catzfs01:~/Desktop$ pwd
/home/kpatz/Desktop
kpatz@catzfs01:~/Desktop$

```
You can move one level up the tree (say, from ~/Desktop back to ~) by using .. (two periods) as the directory.  You can return to your home directory (~) by simply typing **cd **without any directory.```
kpatz@catzfs01:~/Desktop$ pwd
/home/kpatz/Desktop
kpatz@catzfs01:~/Desktop$ cd
kpatz@catzfs01:~$ pwd
/home/kpatz
kpatz@catzfs01:~$

```

Now, you want to find where you downloaded that Tor browser, right?  If you downloaded it using Firefox, Chrome or Chromium, you can view your download history there.  If not, you'll have to use the find command to find it.  Do you remember what it was named?  Let's say for this example that it's named **tor-browser.tar.gz.**  You can use the find command to look for it.

First, go to your home directory by typing **cd**.

```
kpatz@catzfs01:~/Desktop$ cd
kpatz@catzfs01:~$ 

```
Now, tell find to search for a file named tor-browser.tar.gz.  The "." after find means start searching in the current directory.   You can specify a path instead, or use ~ to search starting in $HOME.
```
kpatz@catzfs01:~$ find . -name tor-browser.tar.gz
./Downloads/tor-browser.tar.gz
kpatz@catzfs01:~$
```In this example, the tor-browser.tar.gz is in the Downloads folder.

If you don't remember the name, and don't have any browser history to find it, you can do a wildcard search by putting a partial file name in single quotes and using * as a wildcard.  Let's say you know the file name had "tor" in it somewhere, so search for that:

```
kpatz@catzfs01:~$ find . -name '*tor*'
./Downloads/tor-browser.tar.gz
kpatz@catzfs01:~$
```There ya go.

---

### Post by ajgreeny on 2017-02-02
> **Impavidus said:**
> <snip>
Neither is there on my system, but there is **help cd**. That makes some sense, as cd is a shell build-in and not a separate program that can be installed along with its manual page files.
Thanks for that info, which I did not even consider, and which is helpful but not quite so clearly stated as the link that I showed [https://ss64.com/bash/cd.html](https://ss64.com/bash/cd.html)

---

