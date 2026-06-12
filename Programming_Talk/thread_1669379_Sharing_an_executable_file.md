---
title: "Sharing an executable file"
date: 2011-01-17
forum: Programming Talk
---

### Post by japhyr on 2011-01-17
Hello,

I am in a school environment, with about 12 Ubuntu 10.04 Desktop machines, all connected to a Windows-administered network.  I have a script that I want to be able to run on any machine on my network.  

I created a simple hello.sh script on one Ubuntu machine.  I shared the containing directory, and that directory is now visible from any other Ubuntu machine.  However, permissions are visible only on the host machine.  All of the other machines list "unknown" for this file's permissions.

Is there a way to share an executable file between Ubuntu machines on a Windows network?

---

### Post by geirha on 2011-01-17
I'm guessing this is smb/cifs sharing? Where does it say unknown on permissions? What does ls -l on the file say?

---

### Post by japhyr on 2011-01-17
I'm not exactly sure what you mean by cifs sharing.  I right click on the directory I want to share, choose "Sharing Options", and enable sharing.  I believe it is samba that handles the sharing.

ls -l /path/filename:
```
-rwxr-xr-x 1 my_username my_username 41 2011-01-17 12:05 hello.sh
```

---

### Post by endotherm on 2011-01-17
it is normal that permissions cannot be evaluate on the share, but based on your ls -l output, that the "other" group has read and execute, it shoudl work.

one of the odd things I had to come to terms with in ubuntu, is that no applications are share-aware. they don;t attempt to make connections by themselves. they leave that to the operating system. windows does the same but they hide it from the user more than ubuntu does. 

when you connect to a share in ubuntu, by default, the share is mapped to a folder in your home named '.gvfs', in a folder formatted like "<ShareName> on <servername>". note the spaces. that can wig some apps and scripts out. 

anyway, the point is, that when you access a network file via smb, your local application (in the case the terminal) thinks it is accessing a file stored in .gvfs, not one on a remote box. if you want to evalutate the permissions, check there. 

also clicking on scripts often does not bring up a window as you woudl expect. you can either launch it from within a terminal , or create a launcher that runs an "Application in Terminal", to make sure your output isn't coming up and disappearing faster than your eye can register.

---

### Post by japhyr on 2011-01-17
That is pretty helpful.  I was not aware of the role the ~/.gvfs directory played in sharing folders. The output I just listed came from the computer hosting the script. I could not get any permissions to show up on any of the client computers.

Using what you said about .gvfs, I opened  a  terminal on a client machine and cd'd to the .gvfs directory, then into the shared folder.  Running ls on the client computer gave me the permissions '-rwx------', but the username associated with the file  is my username on the client computer.

So I can run the shared script two ways: by cd'ing into the .gvfs directory to the shared directory and then running the script, or from any directory with '~/.gvfs/shared_dir\ on\ host_comp_name/hello.sh'.

But I cannot navigate to the .gvfs folder in nautilus and double click the file  to run it.  Is there any way to let this happen, perhaps by changing ownership on the host machine?

---

### Post by endotherm on 2011-01-18
well, first off, what users and groups are involved in the scenario? who(real people) needs to run the program,and what user account will they be using?
the answer to that will drive much of the configuration. 

I just put a little hello world up on one of my fileservers, and I can browse to it, but I can't find any way to make it come up and stay via a double click, though when I did a right click -> "open terminal here" the pwd was "~/.gvfs/myshare on myserver$" and the script executed fine with ./hello.sh
can you do the same with your script from the cli? if so, then the problem isnt permission to execute, but something about the execution environment itself. 

 as for permission, you do need permission to execute both on the underlying filesystem, and in samba, so be sure that samba is allowed to execute. I am used to classic samba, rather than the gui usershare configuration, so I can be of little help to you there, but you may get some useful info from 
```

testparm -s
net usershare info
cat /etc/samba/smb.conf

```

go ahead and post those back if you cannot run your script from the cli. 
if you can execute it via the command line, then this thread may have the answer you need: [http://ubuntuforums.org/showthread.php?t=883499](http://ubuntuforums.org/showthread.php?t=883499)

---

### Post by japhyr on 2011-01-19
The script I want to run configures the desktop environment on a set of Ubuntu computers in my classroom.  When I teach technology-focused classes, students learn to configure computers manually, so keeping things consistent and up to date is easy. When I am not teaching tech-focused classes, it is much harder to keep different machines consistent, especially as we add features and programs.  The script allows me to quickly get all the machines in my classroom back to the same state.

I write and develop the script as an administrator on one machine.  I want to share that with all the other machines, so I or a student who works from an administrator account can run the script on each of the 12 other machines.  Right now we do this by walking a USB stick around the room.

I can run the hello.sh file from the command line on any machine now.  I can teach students to do this as well, but it is not nearly as efficient as double clicking the file or adding a launcher to the panel.

The script runs from the command line, but will not run from a launcher.  I right click on the top panel, create a launcher, choose 'Application in Terminal' for the type, and give the same command that works in the terminal: '~/.gvfs/shared_dir/hello.sh' The popup error message reads "There  was an error creating the child process for this  terminal."

Should this launcher work, given that I can run the script from the command line?

---

### Post by endotherm on 2011-01-20
the error message is because of the "~/" at the beginning of the path. apparently ~ is not valid when evaluated from a launcher. 
try replacing the ~/ with /home/<username>/
and be sure in your launcher to enclose the entire path in double quotes (") to deal with the spaces in the path. yes your script should execute, though the window will just flash up and close automatically. I thought the launcher would solve that, but my tests show that is not the case.  if you want the script window to stay open, add a line like this at the bottom of your script:
```
read -p 'press any key to exit'
``` you may be able to get rid of the launcher entirely if that works for you, both in form and function. 
[http://www.cyberciti.biz/tips/linux-unix-pause-command.html](http://www.cyberciti.biz/tips/linux-unix-pause-command.html)

note, that the user will have to navigate to the share (mounting it) before the .gvfs path is valid. perhaps a better idea is to address how the share is mounted to your system. here is an howto on how to mount shares "permenately" using smbmount and configuring your fstab. [http://ubuntuforums.org/showthread.php?t=255872](http://ubuntuforums.org/showthread.php?t=255872)

also there are ways to run your script [at regular intervals, at specific times]("http://ubuntuforums.org/showthread.php?t=102626"), or upon specific events like [logout]("http://www.linuxquestions.org/questions/linux-desktop-74/run-script-on-gdm-logout-634678/"). combined with smbmount, you could run a local script to connect to your share and execute your script with no intervention on anyones part.

---

### Post by japhyr on 2011-01-20
Thank you.  The class I teach related to this question is one in which high school students take donated computers, and refurbish them by learning to install Ubuntu.  It has been a successful class so far, but I'm always looking for ways to strengthen the class and make the Ubuntu computers more and more useful to students and staff.

What you have shared is enough to let me create an efficient way of maintaining the computers at a high level of functionality.  When I teach the class again next year students will probably learn some of these skills related to maintaining a network of computers, rather than just learning to maintain a single computer.

---

### Post by japhyr on 2011-01-20
double post

---

