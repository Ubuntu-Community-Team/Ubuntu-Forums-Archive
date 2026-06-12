---
title: "confused by cd in terminal"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by scientist1971 on 2008-05-13
well I suppose its about time to get this sorted...6 weeks of ubuntu and I want to claer up some terminal stuff
I installed sopcast command line from here
[http://www.ubuntu-unleashed.com/2008/02/howto-watch-p2p-tv-with-sopcast-with.html](http://www.ubuntu-unleashed.com/2008/02/howto-watch-p2p-tv-with-sopcast-with.html)
and as usual with this kind of thing I get stuck where instructions say something like:
 and cd into that directory using terminal
I know where the folder is in ubuntu
places --> home folder --> documents --> sp auth --> sp-sc-auth
but through the terminal?!? no idea
some help would be appreciated (the more simply explained the better for a newbieish terminal user) thanks

---

### Post by Joeb454 on 2008-05-13
What is the exact name of the 2 folders/files in your Documents folder?

It's actually quite important ;)

---

### Post by ayenack on 2008-05-13
OK so you need to go to **Applications>Accessories>Terminal** and open an terminal.

Then do this.

**cd /home/YOUR_USER_NAME_HERE/Documents/sp_auth/sp-sc-auth**

And that should take you to the desired folder. If this does not then open an terminal type cd and drag and drop the folder into the terminal and press eneter.

---

### Post by Joeb454 on 2008-05-13
> **ayenack said:**
> 
**cd /home/YOUR_USER_NAME_HERE/Documents/sp_auth/sp-sc-auth**


You could save time by simply typing ```
cd ~/Documents/sp_auth/sp-sc-auth
```

If there is a space in any of it encase it in "quotes" like that :)

---

### Post by mapes12 on 2008-05-13
cd is the command line to change directory. Exactly like windows.

This doc will guide you what to do:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by pedro_orange on 2008-05-13
Did you know you can press Tab to finish off names of things in terminal?

For example:


Say we're in home dir:

```
pedro@pedro-laptop:~$ 

```

Now I want to move into my Documents directory. I'm already in my home dir (I can tell from the tilde ~ in the prompt) & I know Documents sits in home.
So I do a quick ls to check:

```
pedro@pedro-laptop:~$ ls
Desktop    Examples  Pictures  Public     Videos
Documents  Music     Podcasts  Templates
pedro@pedro-laptop:~$ 

```

So now I know where I'm going all I do is use the change directory (cd) command to change my current directory:

But! I can cheat!

I can type 'cd Do' without the inverted commas, hit tab and it fills in the "Documents/" for me.

Remember it's case sensitive. And; don't just presume D will tab to Docments/ cause there is a folder called Desktop there. ls is your friend!

---

### Post by ayenack on 2008-05-13
> **Joeb454 said:**
> You could save time by simply typing ```
cd ~/Documents/sp_auth/sp-sc-auth
```

If there is a space in any of it encase it in "quotes" like that :)

Yep.


@scientist1971
BTW In case you don't know `cd` stands for change directory and the `~` tells Ubuntu to direct the command towards the current users home directory.

---

### Post by TheKeyMaker on 2008-05-13
Hi!

Hopefully I can clear this up a little bit for you.
First I just want to make sure you know how to get to the terminal.
The terminal program is located in your **applications menu** and then look under **accessories**.

Now that you have the terminal open you can use the cd command.
The cd command stands for change directory, so really instead of clicking into the file which you were doing with the graphical user interface, you are now just opening the directory through the cd command. 

So now with the folder you wanted to get to, you would just type:

**cd** ~/Documents/sp\ auth/sp-sc-auth

Then it should change your directory. You have to put forward slashes in where you haves a space. Here is the form post that talks about that:
[I]
[http://ubuntuforums.org/showthread.php?t=541547](http://ubuntuforums.org/showthread.php?t=541547)
[/I]
I would recommend that if you created these folders, that you user the "_" underscore instead of space. 


You can print you working directory then by typing in **pwd**. Or you can view whats in the directory with the **ls** command.

Hope that helps!

---

### Post by scientist1971 on 2008-05-13
thank you everyone for the clear explanations
:)
will try it now

---

### Post by scientist1971 on 2008-05-13
mmm
I tried cd/home/richard/documents/sp-auth/sp-sc-auth
and got
bash: cd/home/richard/documents/sp-auth/sp-sc-auth: No such file or directory
richard@richard-laptop:~$ 

I went up through the folders and I definately got the order and spellings correct (which I know is important ;)

---

### Post by scientist1971 on 2008-05-13
ok then I tried opening cd and draging the folder into the terminal  
which looked like it worked but..

richard@richard-laptop:~$ '/home/richard/Documents/sp-auth/sp-sc-auth' 
SC Version: 3.0.1  Build time: 2008-03-20 11:25
Usage:
./sp-sc [-T] [-t seconds] [-u username:password] [-n out:total] [-x suffixname] [-a [http://auth_url]](http://auth_url]) <sop://url> <localport> <playerport>
richard@richard-laptop:~$ sudo cp sp-sc-auth /usr/bin/sp-sc
[sudo] password for richard:
cp: cannot stat `sp-sc-auth': No such file or directory
richard@richard-laptop:~$

---

### Post by aeiah on 2008-05-13
> **scientist1971 said:**
> mmm
I tried cd/home/richard/documents/sp-auth/sp-sc-auth
and got
bash: cd/home/richard/documents/sp-auth/sp-sc-auth: No such file or directory
richard@richard-laptop:~$ 

I went up through the folders and I definately got the order and spellings correct (which I know is important ;)

you need a space between cd and /home (actually, you dont need to use the /home/richard/ bit since a terminal defaults to the home directory already when you open it.

if you have the upper/lowercase correct, what you should type is ```
cd documets/sp-auth/sp-sc-auth
```

---

### Post by pommattski on 2008-05-13
> **scientist1971 said:**
> I tried cd/home/richard/documents/sp-auth/sp-sc-authThe space after the "cd" (change directory) command is important.
So, assuming the rest of your path is correct, try```
cd /home/richard/documents/sp-auth/sp-sc-auth
```

... and yes, the case is also important: If the documents folder is actually **D**ocuments, you must use the same.

---

### Post by aeiah on 2008-05-13
> **scientist1971 said:**
> ok then I tried opening cd and draging the folder into the terminal  
which looked like it worked but..

richard@richard-laptop:~$ '/home/richard/Documents/sp-auth/sp-sc-auth' 
SC Version: 3.0.1  Build time: 2008-03-20 11:25
Usage:
./sp-sc [-T] [-t seconds] [-u username:password] [-n out:total] [-x suffixname] [-a [http://auth_url]](http://auth_url]) <sop://url> <localport> <playerport>
richard@richard-laptop:~$ sudo cp sp-sc-auth /usr/bin/sp-sc
[sudo] password for richard:
cp: cannot stat `sp-sc-auth': No such file or directory
richard@richard-laptop:~$

right. change from your home folder (which you are in by default in the terminal) to your sp-auth folder in your Documents folder:
```
cd Documents/sp-auth/
```

list the contents of the directory, just to make sure you're in the right place
```
ls
```

make a directory to copy your file into
```
sudo mkdir /usr/bin/sp-sc
```

copy the file
```
sudo cp sp-sc-auth /usr/bin/sp-sc
```

---

### Post by ayenack on 2008-05-13
Try this.

**cd /home/richard/Documents/sp-auth/sp-sc-auth**

You have to make sure that all these are directories and not files. So if sp-sc-auth is a file instead of a folder/directory it will not work. Be sure to use capitol `D` in Documents.

---

### Post by scientist1971 on 2008-05-13
ok tried the cd space and Documents (which worked thanks) but it turns out sp-sc-auth is not a directory as specified in the original webpages instructions so still confused I'm afraid

richard@richard-laptop:~$ cd /home/richard/Documents/sp-auth/sp-sc-auth
bash: cd: /home/richard/Documents/sp-auth/sp-sc-auth: Not a directory
richard@richard-laptop:~$ cd documets/sp-auth/sp-sc-auth

---

### Post by scientist1971 on 2008-05-13
richard@richard-laptop:~$ cd Documents/sp-auth/
richard@richard-laptop:~/Documents/sp-auth$ ls
Readme  sp-sc-auth
richard@richard-laptop:~/Documents/sp-auth$ sudo mkdir /usr/bin/sp-sc
mkdir: cannot create directory `/usr/bin/sp-sc': File exists
richard@richard-laptop:~/Documents/sp-auth$

---

### Post by Joeb454 on 2008-05-13
What happens if you do ```
./sp-sc-auth
```

Also does the Readme help at all?

---

### Post by aeiah on 2008-05-13
> **scientist1971 said:**
> richard@richard-laptop:~$ cd Documents/sp-auth/
richard@richard-laptop:~/Documents/sp-auth$ ls
Readme  sp-sc-auth
richard@richard-laptop:~/Documents/sp-auth$ sudo mkdir /usr/bin/sp-sc
mkdir: cannot create directory `/usr/bin/sp-sc': File exists
richard@richard-laptop:~/Documents/sp-auth$

just copy it over after you've tried to create the directory and see if it works.

---

### Post by ayenack on 2008-05-13
Try this.

**cd /home/richard/Documents/sp-auth**

And let me know what happens.

---

### Post by scientist1971 on 2008-05-13
richard@richard-laptop:~$ ./sp-sc-auth
bash: ./sp-sc-auth: No such file or directory
richard@richard-laptop:~$ 


richard@richard-laptop:~$ cd /home/richard/Documents/sp-auth
richard@richard-laptop:~/Documents/sp-auth$

---

### Post by scientist1971 on 2008-05-13
the read me says:
SopCast client version 3.0.1 library dependency
If you don't have stdc++ 5 in your system, please download the libstdcpp5.tgz from
[www.sopcast.com](www.sopcast.com), and copy the
libstdc++.so.5
libstdc++.so.5.0.1
to /usr/lib/

The copy command must be:
cp -a libstdc++.so.5* /usr/lib
With '-a' parameter, and you must login as root.

1. sp-sc-auth

A simple example of sp-sc command line.
./sp-sc-auth sop://broker.sopcast.com:3912/6001 3908 8908 > /dev/null &
Start to transfer channel 6098, and you can play it on 8908 with VLC or mplayer
by open the url: [http://localhost:8908/tv.asf](http://localhost:8908/tv.asf)

Thanks and enjoy it.

---

