---
title: "gnome-terminal: need to have it run a program when opened"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by mikex on 2008-05-23
Somehow I can't seem to make it work. When I click open the terminal, I want the terminal to open and run a text-based program in the terminal window. The documentation says you can use the -e or -x option (still not clear what the difference is) to have the terminal run a program. But I haven't been able to make these options work. The program won't run inside the terminal window when opened. Normally I change to the program's directory then run it like this:

./prog.exe

I can configure the terminal to automatically change to the correct directory, but not execute the program.

---

### Post by decoherence on 2008-05-23
> I can configure the terminal to automatically change to the correct directory, but not execute the program.
what method did you use?

if you want the command to run in a login shell (ie, when you hit Ctrl Alt F1 and log in to the console) you want to edit a file in your home directory called .profile. If you want it just to run in a terminal emulator (like Terminal) you edit .bashrc

simply place the commands you would like to run at the end of either of these files.

---

### Post by NormR2 on 2008-05-23
For those of us new to Linux, it would help if you posted the contents of the script you're trying to run. I don't have enough experience to image what you're doing wrong.  If I could get your script I could try it on my system to see what is happening.

---

### Post by drs305 on 2008-05-23
It would be helpful to see the script, but here is another way to do the same thing (if I understand what you want).

Rt Click on the top or bottom panel, select Add to Panel, Custom Application Launcher. Select Run in Terminal, name it, and put the command of the text-based app in the run command.

Of course, you may want a script to run automatically at a given time or event, but if you just want to start an app with a terminal this is one way to do it.

---

### Post by sayakb on 2008-05-23
I think you should create a GUI launcher at a nautilus having:
```
gnome-terminal command
```It should work when called from a nautilus window\


EDIT: Ignore this.. doesn't seem to work either ;)

---

### Post by mikex on 2008-05-23
Right-click on the terminal icon on my desktop
click on properties
click launcher tab
enter a command:

gnome-terminal --working-directory=/home/mike/folding

^ that works fine

if I add either the -e or -x option to run the folding@home client like this

gnome-terminal --working-directory=/home/mike/folding -e ./FAH504-Linux.exe 

it doesn't work

Why?

---

### Post by drs305 on 2008-05-23
> **mikex said:**
> 
gnome-terminal --working-directory=/home/mike/folding -e ./FAH504-Linux.exe 
Why?

Well, it looks like you are trying to run a windows program (.exe).  Those programs won't run in linux unless you run it through something like 'wine'.
Even the -e (execute) extension won't allow you to run it normally in ubuntu.

---

### Post by gandaran on 2008-05-23
can you give details on this program ' FAH504-Linux.exe ' if it's a windows program you won't be able to run it, .exe programs you can only run them under wine.

---

### Post by y-lee on 2008-05-23
I agree with drs305 it does look like you are trying to run a windows program, judging by the exe. But if you want gnome terminal to stay open after running a script or a linux command, you have to set this in your profiles preferences.

Open gnome-terminal and click on **Edi**t and then **Profiles**. You should have at least one profile, *Default*. click it and choose **Edit**. Click on the **Title and Command **tab and change *When the command exits* to *Hold the Terminal open*.

---

### Post by starcannon on 2008-05-23
Its the folding at home binary, while it has .exe as a file extension it is working like a .bin or .run file.

a quick read of the help file at folding at home showed it needs to be set to executable:

```
sudo chmod a+x ./FAH*
./FAH*
```

It runs fine.

To make a desktop or menu icon for this just right click on the desktop and select:
```
Creat Launcher
```
Then in the drop down menu for Type:
```
Application in Terminal
```

Then Give it a Name:
```
Folding @ Home
```

Then for Command:
Browse to where you have the FAH504-Linux.exe
Select it, click Open
Click OK

Click the Springboard Icon on your desktop and it will open and run in the terminal.

GL hope that helped.

---

### Post by mikex on 2008-05-24
That works except for one problem. It doesn't seem to be running in the folder it exists in, because it starts as if I am a new user again and asks for a user name, etc. If I open a terminal and change to the directory the folding program is in, like I've been doing, the program picks up where it left off from, like it should. How do I make it run in the directory it's supposed to be running in?

---

### Post by RomeReactor on 2008-05-24
Hi. With the launcher set to 'Application in Terminal', fill the command section like this:
```
sh -c "cd /home/mike/folding && ./FAH504-Linux.exe"
```

---

### Post by mikex on 2008-05-24
> **RomeReactor said:**
> Hi. With the launcher set to 'Application in Terminal', fill the command section like this:
```
sh -c "cd /home/mike/folding && ./FAH504-Linux.exe"
```

Yes that works, thanks. Where are those commands documented? I clicked on help in the launcher but nothing like that shows up!

---

### Post by RomeReactor on 2008-05-24
I've not seen them documented, just found them some time ago.

Glad you got it working!

EDIT: On the other hand, try 'man sh'. And [LinuxCommand]("http://linuxcommand.org/") is a good place to get acquainted with the terminal, though I don't know if that particular command is explained there

---

