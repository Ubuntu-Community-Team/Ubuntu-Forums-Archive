---
title: "How do you make a .sh file"
date: 2011-03-04
forum: Programming Talk
---

### Post by TheAJGman on 2011-03-04
I don't know if this is the right spot but I want to know more about making .sh files. I hear there similar to batch files in windows and want to learn more. Can you please tell me some of the basic commands and what they do. Also I'm planning to use these to run commands atomaticaly so I don't have to be half way through a command and then have to enter sudo password.

---

### Post by Vox754 on 2011-03-04
> **TheAJGman said:**
> I don't know if this is the right spot but I want to know more about making .sh files. I hear there similar to batch files in windows and want to learn more. Can you please tell me some of the basic commands and what they do. Also I'm planning to use these to run commands atomaticaly so I don't have to be half way through a command and then have to enter sudo password.

It's a very broad topic to be covered.

By .sh files, I will assume you mean a shell script.

A shell script is the same as a "batch" file in Windows: a collection of commands placed in a file, that are executed in order.

However, Linux shell scripts are very powerful, the shell language is actually a full programming language, having variables, simple arrays, associative arrays, flow control (if, for, while), function definitions, command substitution, glob expansion, mathematical operations, and may things.

There are many shells (programming languages), one of the most basic is simply the POSIX shell "sh", which is a standard. In the open source world, however, predominates the GNU "bash" shell, which is compatible with "sh", but also provides many more features. Therefore, nowadays it is very commonly accepted that the "shell" refers to "bash".

Experts, however, know and can use other flavors, such as "tcsh", "ksh", "zsh", etc. I suggest you focus on learning "bash".

To have a look, see this thread: [http://ubuntuforums.org/showthread.php?t=1699516](http://ubuntuforums.org/showthread.php?t=1699516)

Some individual running some commands and testing for some files, operating on them, etc. It's not that hard.

Take a look at this guide: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

In order to do complex operations that require super user privileges you should run your script with "sudo" from the beginning, only one password is needed at that time.
```

sudo bash my_script.sh

```

It is lame to include "sudo" inside the script.

If you don't require high privileges just run the script with the normal user.

This is a clear distinction from Windows, where the normal user was a super user and therefore could do whatever. Linux tries to enforce security by only modifying important system files, if it is the super user the one doing it.

It also depends on what you want to do. If you need to re-run a script several times, always run by root, perhaps you should schedule it through "cron", a program specifically designed with this in mind.

---

### Post by ve4cib on 2011-03-04
Basically everything you've ever seen done in a terminal can be included in a shell script.  All the terminal is is an interactive script interpreter, just like the Python interpreter.  (Well, not exactly, but close enough for this example.)

Basic commands you definitely need to know if you don't already:

**Change Directory**
cd /path/to/directory -- change the current working directory to somewhere else
cd .. -- move one level up the directory tree

**List Contents of a Directory**
ls -- list the contents of the current folder
ls /path/to/directory -- list the contents of a specific folder

**Create Directory**
mkdir /path/to/directory -- create the specified folder

**Copy, Move, & Delete Files**
cp file1 file2 -- copy file 1 to a new file called file2
mv file1 file2 -- move file1 to file2 (rename the file)
rm file1 -- remove (delete) the specified file
rm -r /path/to/directory -- recusively delete an entire directory and its contents

Those are certainly among the most common commands you're ever going to run into.  Obviously there are lots, lots more.  If you can tell us what it is you want your scripts to do we may be able to give you more specific advice, and point you in the direction of the appropriate manual pages for the commands you're likely to need.

---

### Post by rg4w on 2011-03-05
One of my favorite sites for getting started with shell scripts:
[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by hakermania on 2011-03-05
The answer is simple:
SH files are bash scripts.
They are plain text script and by giving chmod +x filename.sh you make them executable.

---

### Post by TheAJGman on 2011-03-05
Could some one upload say a fake commuter virus. Because that's how I learned how to make batch files.

---

