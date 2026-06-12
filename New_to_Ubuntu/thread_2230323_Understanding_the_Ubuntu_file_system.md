---
title: "Understanding the Ubuntu file system"
date: 2014-06-18
forum: New to Ubuntu
---

### Post by hill0093 on 2014-06-18
In Windows 7, I kept all my files in a tree except for downloads.
But I don't understand the Ubuntu file system.
With the tree, I can back up the whole tree or branches.
As I understand Ubuntu, the files are kept in workspaces ??
How do I transfer my files to Ubuntu in a way that makes good sense ??
When I backup in Ubuntu, can I choose a workspace to backup ??

---

### Post by yancek on 2014-06-18
The root of a Linux filesystem is indicated by the forward slash (/) so that if you open a terminal and type:  ls / you will see all the upper level directories.  Running that command on any of these directories will show their sub-directories.  User data is usually in the /home/username directory although you can create other directories or partitions on which to hold them.

> As I understand Ubuntu, the files are kept in workspaces ??]

I don't know what you mean by that.  I've never heard it referred to in that manner unless you mean the /home directory?  I'm not really sure what you mean by a 'workspace'.  Usually, one would backup data to another drive or some other medium.  In order to back up system files, you would need to have root/administrator privileges.

---

### Post by robin7 on 2014-06-18
In your /home directory, Ubuntu creates folders by default as follows:
[B]Downloads
Pictures
Videos
Documents
Music[/B]

You can direct most browsers to put any files you download from the web into your Downloads folder, and move them from there to wherever you please using a file manager (Thunar in Xubuntu, PCManFM in Lubuntu, etc).

---

### Post by PondPuppy on 2014-06-18
It may be confusing that the default view in the Nautilus file manager isn't as clearly a tree view as is Windows Explorer. Nevertheless, if you go to the Documents folder you can create a sub-folder, just as in Windows. Folder/sub-folder/sub-folder/files. The logical structure is there, but many Linux file managers don't show it the same way Windows does.

---

### Post by yancek on 2014-06-18
The root of a Linux filesystem is indicated by the forward slash (/) so that if you open a terminal and type:  ls / you will see all the upper level directories.  Running that command on any of these directories will show their sub-directories.  User data is usually in the /home/username directory although you can create other directories or partitions on which to hold them.

> As I understand Ubuntu, the files are kept in workspaces ??]

I don't know what you mean by that.  I've never heard it referred to in that manner unless you mean the /home directory?  I'm not really sure what you mean by a 'workspace'.  Usually, one would backup data to another drive or some other medium.  In order to back up system files, you would need to have root/administrator privileges.

---

### Post by The Cog on 2014-06-18
I don't know what you mean by "workspaces" either. But in Linux, each user has their own area, a subdirectory under /home. For example, my home directory is /home/steve and I keep all my documents and files in there, in /home/steve/Documents, /home/steve/Music etc.

---

### Post by claracc on 2014-06-19
Ubuntu organizes its files also in a hierarchical tree, as windows does. One of the difference is the name of directories in this tree (also the security and permissions of such directories).

Please, read: [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview) I think it will clarify the item.

---

### Post by col48 on 2014-06-19
In Nautilus, you can see the tree structure by choosing View>List, as distinct from View>Icons and the contents of folders/subfolders/sub-subfolders etc by clicking on them.

In Ubuntu, a Workspace is nothing to do with the way files or folders are organised.  Each Workspace is a desktop display.  A running program which has a display window (ie not the background ones) puts that window into a Workspace - normally the one which was showing when the program started.  you can move a display which has the focus to a diffrent Workspace by right-clicking on its tab in the taskbar and choosing one of the relevant options.  The Workspaces are shown (for me) in miniature at the far right of the taskbar, with the one currently showing highlit; clicking on one of the others switches the display to that one.  Rightclicking any of the miniatures offers "Preferences" where (amongst other things) the number of Workspaces can be altered.

No doubt other people use them differently, but I tend to use them to group related running tasks together - if I get asked to interrupt one activity to do something else urgently, I do the new work in a fresh Workspace to keep it away from the other task.  A word of warning, though: if (say) Libreoffice crashes, all instances die - whatever Workspace they are in.  Workspaces are for organising what you see, and do not reflect how the computer is functioning behind the scenes.

---

### Post by Tropicalbound on 2014-06-19
Hill0093, workspaces is a feature you turn on that allows you to split the desktop into quadrants.  For example, you can have an email client open in the upper left quadrant, a web browser open in the upper right quadrant, and so on......but it has nothing to do with the filesystem.

TB

---

### Post by hill0093 on 2014-07-02
If I interpret you correctly, "ls /" lists the names of 
the top level directories and files.
Are blues directories, are greens executables, are whites texts?
What does "ls" alone give?
And how do I get some desired details about the items?
Like size, dates, etc.?

---

### Post by Iowan on 2014-07-02
**man ls** will provide lots of information about the ls command itself.
> **hill0093 said:**
> What does "ls" alone give?
The contents of the current directory
> **hill0093 said:**
> And how do I get some desired details about the items?
Like size, dates, etc.?**ls -l** provides a "long" listing.
I habitually use **ls -al**

---

### Post by ubudog on 2014-07-02
> **hill0093 said:**
> If I interpret you correctly, "ls /" lists the names of 
the top level directories and files.
Are blues directories, are greens executables, are whites texts?
What does "ls" alone give?
And how do I get some desired details about the items?
Like size, dates, etc.?

Yes, "ls /" lists the top-level directories, which make up your filesystem.

The ls command alone lists the directory contents of the current directory that you are in.  By default in Ubuntu, when you open a terminal, you will be in your home directory, but you can always check what directory you are in using the "pwd" command.

The ls command has many options that you can append to it, such as -l, which can be used to show you more information.

Type "man ls" in a terminal for complete documentation on how to use it.  The "man" command can be used to find documentation on most programs in Ubuntu.

---

### Post by ubudog on 2014-07-02
> **Iowan said:**
> **man ls** will provide lots of information about the ls command itself.

The contents of the current directory
**ls -l** provides a "long" listing.
I habitually use **ls -al**

^ this :D

---

### Post by Dennis N on 2014-07-02
Also worthy of mention is the **tree** command. It needs to be installed first, I believe.

one level of folders starting from /
```
tree / -d -L 1
```

two levels of folders starting from /etc
```
tree /etc -d -L 2
```

for full information on many other options, **man tree**

---

### Post by monkeybrain20122 on 2014-07-02
> **PondPuppy said:**
> It may be confusing that the default view in the Nautilus file manager isn't as clearly a tree view as is Windows Explorer. Nevertheless, if you go to the Documents folder you can create a sub-folder, just as in Windows. Folder/sub-folder/sub-folder/files. The logical structure is there, but many Linux file managers don't show it the same way Windows does.

I find the layout in Windows explorer a lot more confusing. In Linux (not just Ubuntu) your home branches off into subdirectories with good logical names like Documents, Downloads, Music, Videos etc and you can create more. The layout of linux file managers are a lot more transparent .

---

### Post by yancek on 2014-07-02
If you type:  ls with no other parameters, it shows the contents of the current directory you are in.
On my Ubuntu 12.04, the color scheme you refer to is the same, blue=directory, green=executable, whit=text file.  I did see one purple entry, a .tiff file.

I don't really see the organization in windows.  I guess the User folder which then has the users listed is similar to the /home directory on Linux.

---

### Post by JeQhdMD on 2014-07-02
Here is another approach which I recommend you try - - in Windows, to see and navigate through the "tree" of folders and files, you use a graphical program called "Microsoft File Explorer" . . . . you need the equivalent program in Linux.  If you use the default desktop for Ubuntu, you should open the "Nautilus" file manager.  It displays the Linux File Tree in an easy to use format.   If you use the KDE desktop (as in Kubuntu), you would use the "Dolphin" file manager.

These file managers actually show you quite a bit more data about the folders and files in the entire file system tree,. owner, permissions, etc.

After learning the gui file manager tools, you can experiment with the CLI (command line interface) or aka "Terminal", "Console", "Konsole" commands.

---

### Post by hill0093 on 2014-07-02
Sounds good, but I don't know how to access "Nautilus".
If I type Nautilus, it says "command not found".

---

### Post by ubudog on 2014-07-02
> **hill0093 said:**
> Sounds good, but I don't know how to access "Nautilus".
If I type Nautilus, it says "command not found".

Whenever you open your file browser, you're using nautilus.

You can launch it from the terminal by typing (lowercase) "nautilus".

---

### Post by JeQhdMD on 2014-07-02
Hill0093 . . you're questions are quite "unusual" to say the least.  Are you running the standard Ubuntu install, which provides for the desktop called "Unity"???

If you are, then you should see a bunch of icons on the leftmost side of the screen, and one of those icons looks like a file drawer (or something similar).   Perchance, are you running a different desktop?  Are you running a "server" version of Ubuntu instead of the standard gui desktop.   Are you even running Ubuntu?

---

### Post by Topsiho on 2014-07-03
In Windows you have a file system for every drive: for C: you have a file system rooted (starting) at C:\, for "drive" D: rooted at D:\, and so on. The "drives" are not necessarily physical drives, but may be partitions on the same physical drive. It is a very confusing story.

In Linux there is only ONE filesystem, starting at /, everything else hanging under it as subdirectories. Even when you have multiple, real, drives....
You can see the top level subdirectories, as has been said before this, using the terminal command ls (the terminal is so much easier here).
Nearly all of them belong to the system and should not bet tampered with if you don't know exactly what you do. Fortunately you only can change them with a password (the one you entered during the install). Tampering here might easily ruin your system.
Installing software fom the Ubuntu repositories changes the system, and you need the main password here.

The directory where  *** your personal files*** are put, is the directory /home/yourusername, yourusername being the name you use to log in.

That is the ONLY directory in which you can do anything that you want to do: creating directories, subdirectories, subsub.... etc. Putting files in them, changing them, removing and you name it.

Even in someone else's /home/someoneelsesname you can not do this without knowing their password.

Hope this helps :)

Topsiho

---

### Post by buzzingrobot on 2014-07-03
Hill0093, the Linux filesystem is hierarchical. The root of the tree is the "/" directory.  All other directories are children of "/".

An "ls /" on my system displays the names of the top-level directories immediately beneath "/":
```

bin  boot  dev  etc  home   lib  lib32  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var 

```

Remember that a file manager is just an application that will display the directory tree and its contents as its developers chose to display it. So, what you see in a file manager may or may not reflect the actual hierarchy. For example, Linux file managers often do not show a directory called "/" but choose to label it "File System" or "Computer" or something else that's apparently intended to make Windows users feel more comfortable. File mangers also typically default to giving prominence to the user's home directory which can create the illusion that that dirctory is the beginning of the hierarchy.

---

