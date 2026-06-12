---
title: "Lost my file"
date: 2022-01-30
forum: New to Ubuntu
---

### Post by sdantonio on 2022-01-30
Ok, this is a post that I'm actually embarrassed to post, but I lost a file

I installed JJazzLab and now then I look in "show application" I can't find anything.  It did start once automatically when I first installed it, but I don't have any way of finding an icon or anything else to start it from.

I'm running Focal Fossa

Thanks
Steven

---

### Post by KBar on 2022-01-30
It's perfectly fine. Things like this can happen to anyone. Fret not, if it wasn't removed at some point, it can be found.

It [looks like]("https://www.jjazzlab.com/en/download/") the app is distributed as a single ZIP archive. It has six directories inside and the binary resides in *bin/jjazlab*. Before being able to start the app, the archive needs to be unzipped. Now that we're equipped with this knowledge, we can start our searching mission.

Open *Terminal*. Type in the following:
```
locate 'bin/jjazzlab'
```
…and press _Enter_ to execute. If it doesn't locate anything or complain about something, run another command:```
find ~ -maxdepth 4 -iname '*jjazzlab*'
```

The **find** command should work, assuming you unzipped the archive to your home directory.
[HR][/HR]
Alternatively, if you feel like this is too complicated for you, you can start a search within the *Files* app itself. The instructions can be found [here]("https://help.ubuntu.com/lts/ubuntu-help/files-search.html.en"), which is also accessible on your desktop.

---

### Post by Impavidus on 2022-01-31
"Show application" will show the applications that, simply speaking, have been properly registered with the tool showing this "show application" menu. To do so, the installer must have left a .desktop file in one of the directories searched by the tool showing the menu. This .desktop file gives the path to the executable file, the name, the icon and some additional information. Maybe the installer didn't do this, in which case the application is installed, but cannot be started from the GUI. You can start the application from command line or you can create the .desktop file yourself.

---

### Post by ActionParsnip on 2022-01-31
How did you install the application please? What steps did you take?

---

### Post by sdantonio on 2022-01-31
Hi

KBar, I know where the folder and the bin file are, thats not the problem. I was expecting to see a icon for it in my installed prograns (as I do with blue griffon and some of the other programs I have already installed)

Parsnip, this is what I did

I navigated to the bin file, right click on it and select "Properties." Click on the "Permissions" tab and place a check  next to the option labeled "Allow Executing File as Program,"

I opened a terminal session and type "sudo" space, then dropped the bin file into the terminal window.

Back in the terminal window I clicked enter, then entered my password when asked.  

At this point JJazzLab opened up and I assume that this installed it as a program on the computer.

I just went through these steps again to conform that they work, and they do.

Looking at it I'm now wondering if I just ran it from the terminal window instead of installing is

---

### Post by schragge on 2022-01-31
Unless it installed a .desktop file, you wouldn't see it in Applications. A .desktop file would usually be installed to **/usr/share/applications**, or to **/usr/local/share/applications**, or to **~/.local/share/applications**.

[The installation instructions]("https://jjazzlab.gitbook.io/user-guide/installation#linux-instructions") just say
> Start JJazzLab using **bin/jjazzlab** in the installation directory.
so I presume the .desktop file is not there. Arch Linux package in AUR ships with a [.desktop file for JJazzLab]("https://aur.archlinux.org/cgit/aur.git/plain/jjazzlab-x.desktop?h=jjazzlab-x-bin") which you may use as a base for your own. For that to be used unchanged, you'll have to symlink the jazzlab executable to a directory on your PATH. Alternatively, you may specify the full path to it in the **Exec=** line inside the .desktop file.

---

### Post by TheFu on 2022-01-31
I'm just here to say that I lose files _all - the - time_.  I cannot help with GUI stuff. I don't really use it. Typically launch programs from a terminal (xterm is used here) so I have more control.

I've been losing files for decades, so it isn't just mid-life memory issues. ;)

Icons don't start program. That isn't how Linux/Unix works.  There aren't any extensions mandated for programs either. That's a MS-Windows thing, not Unix/Linux.  The name you saw may not be the name of the program.  There is likely a .desktop file. Some GUI programs do make use of specific file extensions though really every file should have a header which says what type of file it is so that extensions aren't necessary.
PDF data files (.pdf), don't need any extension on Linux systems to be read and used. The extension is just for human convenience. There is a command which looks that the file header - something called a "magic number" - which is used to determine the type of a file. For example, 
```
$ file LVM-Diag.[COLOR="#FF0000"]png[/COLOR]
LVM-Diag.[COLOR="#FF0000"]png[/COLOR]: PNG image data, 631 x 641, 8-bit/color RGBA, non-interlaced
```
Now I'll rename that file and run the command on the new filename.
```
$ mv LVM-Diag[COLOR="#FF0000"].png[/COLOR] LVM-Diag
$ file LVM-Diag
LVM-Diag: PNG image data, 631 x 641, 8-bit/color RGBA, non-interlaced
```
No extension, but I can still view it in an image viewer because the "magic number" for the file hasn't changed.
[https://en.wikipedia.org/wiki/File_format#Magic_number](https://en.wikipedia.org/wiki/File_format#Magic_number) has more than even I care to know about this. ;)

I'd use **locate** or **find**.  Locate is the file was on the system before 6am today - the updatedb process runs at around 6:30am here. If it is newer, then it hasn't been indexed, so either I need to force an indexing (sudo updatedb) or use find.  The find command I'd use for a new file would be:
```
$ find / -type f -mtime -1 -iname \*jjazz\*
```
Let that run for a few minutes.
It looks only for files - not directories or symlinks - that are modified less than 1 day ago with a case insensitive name somewhere in the file name.  The first 2 conditions really improve the speed, since 99.999999% of files will not be recently modified. Sometimes I lose huge files, so I'd use a -size parameter too. Looking for files larger than 500MB is really useful sometimes.

There are other search tools that index the content, not just the filenames.  Recoll is one. It is like having a personal google on your computer. The indexes can be large, but the lookup performance is very nice. I use it on my NFS server which has almost 40TB of storage:
```
$ du -sh /d/D2/recoll-index
2.5G    /d/D2/recoll-index
```
It knows how to pull metadata from media files, as well as office files and emails.  That can be handy. There is a CLI interface, but also a GUI interface for when more complex searching is desired.  There are other tools like recoll. What I like about recoll is that I control when the indexing happens and the CLI interface.

---

### Post by KBar on 2022-02-01
> **sdantonio said:**
> KBar, I know where the folder and the bin file are, thats not the problem. I was expecting to see a icon for it in my installed prograns (as I do with blue griffon and some of the other programs I have already installed)Ah, sorry. You have to be a bit more specific, though.

> I opened a terminal session and type "sudo" space, then dropped the bin file into the terminal window. Back in the terminal window I clicked enter, then entered my password when asked.  That's not a good practice. Moreover, it doesn't help you much but sure has huge security implications.

[HR][/HR]
schragge provided a good solution. Alternatively, there is also [this]("https://askubuntu.com/questions/64222/how-can-i-create-launchers-on-my-desktop") question on AskUbuntu. Although it may be a bit outdated, it should still work and help you create a .desktop entry for any app.

More information:

[LIST]
[*][Desktop Entry Specification]("https://specifications.freedesktop.org/desktop-entry-spec/latest/") 
[*][Another question on AskUbuntu]("https://askubuntu.com/questions/281293/creating-a-desktop-file-for-a-new-application") 
[*][A deprecated guide on Community Wiki]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles") 
[/LIST]

---

### Post by The Cog on 2022-02-01
> I opened a terminal session and type "sudo" space, then dropped the bin file into the terminal window.
Starting things with sudo is the bad practice that KBar is referring to. sudo is the equivalent of "run as administrator" in Windows. Programs don't generally need the elevated privilege, and it can cause problems if they then drop files that you as a normal user cannot access. Just enter the name of the executable, without the leading "sudo".

---

