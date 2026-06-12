---
title: "Noob question - Not understanding navigating the directories"
date: 2024-01-10
forum: New to Ubuntu
---

### Post by tense95 on 2024-01-10
Hello all,

Just started with Linux a couple hours ago, I apologize for the trivial nature of this question. I'm a beginning IT student, and don't understand why Ubuntu is giving me errors. Opening up the terminal 'ls' I see the directories listed below such as Desktop, Documents, Downloads, Music, Pictures etc. For a test assignment we created a blank document called 'mysuperduperfile' this was created at the instruction of Linuxjourney.com  the file is located in my documents folder. When trying to navigate to the Documents directory it keeps telling me "No such file or directory"

For example..

cd /Documents

I get the error code. "bash: cd: /Documents/: No such file or directory

This confuses me because Documents is clearly a directory as it was just listed a line above. The current assignment has us looking up 'less' such as ... [COLOR=#333333][FONT=Menlo]$ less /home/pete/Documents/text1

[/FONT][/COLOR]if I try this command exactly and replace 'pete' with my users name it gives me an error that no directory was found.

---

### Post by SeijiSensei on 2024-01-10
/Documents would be a directory under the root of the file system, /.

You want the Documents directory under your $HOME. To see your home directory, enter
```
echo $HOME
```

The quickest way there is "cd" with no arguments.

Just a heads-up. There are only two places where you can write files by default, the temporary directory /tmp, and your "home directory" /home/username. /tmp is destroyed after a reboot.

---

### Post by Rubi1200 on 2024-01-10
This article give a nice overview of the directory structure in Linux:
[https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/](https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/)

---

### Post by ajgreeny on 2024-01-10
You need to learn the differences between absolute and relative pathways to directories when using the terminal or command line.
When you open a terminal from the menu or with Ctrl+Alt+T it will open in your home folder, ie /Home/username
To go to your own Documents folder you simply use **cd Documents** as you are already in the /Home/username directory and Documents is a subfolder of that, ie, /Home/username/Documents

Learning the whole filesystem hierarchy and how it fits together is extremely important for users along with Linux file permissions and in many ways it is a much more simple and logical system than that of Windows which is where you probably came from.
See:-
[https://linuxhandbook.com/linux-directory-structure/](https://linuxhandbook.com/linux-directory-structure/)
[https://www.linuxfoundation.org/blog/blog/classic-sysadmin-absolute-path-vs-relative-path-in-linux-unix](https://www.linuxfoundation.org/blog/blog/classic-sysadmin-absolute-path-vs-relative-path-in-linux-unix)
There many others you will find with a simple search **absolute vs relative paths**

---

### Post by The Cog on 2024-01-10
Nothing's wrong with the posts already here, but I'll just add my little bit.
When as process (e.g. a terminal session) is running, it has a "working directory", a place somewhere in the directory structure. When you start a terminal, it defaults to working in your home directory which is /home/yourname. You should always know what your current working directory is. You can find what it is with the command **pwd**. 
Let's look at creating a file - where will it be created? 
If you just give the name myfile, it will be created where you are - in your current working directory.
If you name Documents/myfile, that means inside the Documents folder which is in your current working directory.

Now we introduce the leading slash (/). This has a special meaning and means that you are not starting from your working directory, you are starting from the very top directory, the root directory. So the leading / means "From the top" rather than "From where you are". It's known as an "absolute path" rather than a "relative" path. 

So the absolute path to your file is /home/yourname/Documents/myfile and you can use that name regardless of your working directory location. In your home directory (/home/yourname) you can use the name Documents/myfile. If you changed your working directory into the Documents directory with the command "cd Documents" (cd = Change Directory) then you are already in Documents so you just call it myfile.

Hope that makes sense. Note there is also the notation ".." meaning the directory above, or "up a level" so to change back up into your  home directory from your Documents directory would be "cd ..".

---

### Post by TheFu on 2024-01-10
The way that directories work in Linux is exactly the same as they work in UNIX, MacOS, MS-Windows and MS-DOS.  Nothing new at all.  In fact, you can use / as a directory separator under MS-DOS or MS-Windows and it works fine.

You just need to learn the difference between absolute and relative paths.  To point and any specific directory, there are an infinite number of ways because it is possible to mix absolute and relative paths.  It doesn't happen very often, but sometimes it is useful.

The commands to know are:
pwd <----- present working directory, AKA CWD - Current Working Directory.  **Your shell prompt shows this**.
cd  <----  change directory

I usually show a bunch of shortcuts to a home directory. So, these are all the same, if your username is "joe"

```
cd           # changedir to the current user's HOME.
cd $HOME     # changedir to the current user's HOME. It is an environment variable set at login.
cd ~         # changedir to the current user's HOME.
cd ~/        # changedir to the current user's HOME. 
cd ~joe      # changedir to the "joe" username's HOME - this is a password entry lookup.
cd /home/joe # Lots of assumptions
```
All but the last are GUARANTEED to work on any Unix-like system, the last one will usually work, but not always.  There is **nothing** special about /home/ and it is not required to place user  HOME directories there.  The passwd db entry is the only place that matters for where a HOME directory is for any password.  This can be in /etc/passwd or LDAP or x.500 or some other directory service in a corporate environment.

Ok, so my shell prompt shows this:
```
tf@hadar:~$
```

Let's break that down.
[LIST]
[*]tf  = my username
[*]@ separator between username@hostname
[*]hadar = the hostname
[*]: separator between pwd and 
[*]~ = pwd (in this case, my HOME)
[*]$ = I'm not running as root. Just a normal userid.  root's shell prompt would have a "#" character.  Books use this slight difference to denote commands run as a normal user and commands run as root (or with sudo elevation).
[*]
[/LIST]

So, if I 
```
cd /etc
```
my prompt changes to 
```
tf@hadar:/etc$
```

This default prompt is extremely helpful.  It is exactly the format needed for scp or rsync to copy files to/from other computers.  That stuff is for later, but you'll probably want to master rsync. It is a top 5 Unix tool, ever.

---

### Post by ajgreeny on 2024-01-11
The thing that nobody has mentioned so far, unless I just missed it, is that Linux filesystems are case sensitive unlike Windows, so /home/username is not the same as /Home/username; the latter will not normally exist in the filesystem but the former using /home is the default.

---

### Post by ActionParsnip on 2024-01-11
You want
```

cd Documents

```
not
```

cd /Documents

```

When you run the first command, you will move into the folder based on your terminal if it exists when you run 'ls'. the second command means there is a "Documents" folder in the root of the file system, which by default there is not

---

### Post by TheFu on 2024-01-11
```
cd Documents
```
is dependent on the cwd/pwd.  The safe way to get there is to use one of these:
```
cd $HOME/Documents
cd ~/Documents

```assuming the current user's version is what you want.  For other users, if directory and file permissions are set to allow it, then 
```
cd ~smith/Documents
```
can be used.

Think of "~" has "home directory of" ....

---

### Post by pushbike06 on 2024-01-12
May suggest that the enquirer should down load a copy of the Linux Command Line manual. My copy is TLCL-13.07.pdf, I would guess that there is a later edition? and also a copy of Core GNU utilities
for version 8.22, 13 December 2013, or later version.

---

### Post by TheFu on 2024-01-12
+1 

Get it here: [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php)

I've never seen/used Core GNU utilities, the manpages for all of them should be installed on the system already.  Any Beginning Unix book from 1990 on for $0.50 at a used bookstore should be close enough to flip though all the main commands.  They are in /usr/bin/ if you just want to start looking at the manpages for each - perhaps 5 per day.

---

