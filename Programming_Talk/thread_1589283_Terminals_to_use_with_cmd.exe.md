---
title: "Terminals to use with cmd.exe"
date: 2010-10-06
forum: Programming Talk
---

### Post by vim_lover on 2010-10-06
This is actually a question related to Microsoft Windows.
In Ubuntu we have lot of shells (bash, ksh, csh etc) and lot of terminals (gnome-terminal, konsole, xterm).  We have the option of installing any shell and any terminal we want.
In Microsoft Windows we have the shell called 'cmd.exe' supplied with the operating system.  And also a default terminal supplied with the operating system.  I don't like the default terminal.  I doesn't have adequate functionality.  Is there any other **terminal** that I can replace with the default one? (I don't want to change the shell.  The **shell** will remain as 'cmd.exe')

---

### Post by viralmeme on 2010-10-06
> **vim_lover said:**
> This is actually a question related to Microsoft Windows ..  Is there any other **terminal** that I can replace with the default one?
[A Windows PowerShell Tutorial]("http://www.computerperformance.co.uk/powershell/")

---

### Post by amauk on 2010-10-06
> **vim_lover said:**
> This is actually a question related to Microsoft Windows.You're going to get better, and more informed answers if you ask this on a windows forum

However, you can install cygwin on windows to gain a *nix like environment (Incl. Bash shell, and all the other GNU base utils)

---

### Post by vim_lover on 2010-10-06
I mean 'terminal' not 'shell'
I am not asking to replace the default shell (cmd.exe with powershell or something else).
I am asking to replace only the terminal interface.

---

### Post by apetresc on 2010-10-06
I think you're looking for something like this: [http://sourceforge.net/projects/console/](http://sourceforge.net/projects/console/)

Adds tabs, styling, etc, to any Windows shell including cmd.exe.

---

### Post by Calash on 2010-10-06
Windows XP actually has 2


CMD.exe is 32bit

COMMAND.EXE is 16bit

Not sure if they did away with that in Vista or 7, but I imagine they would.

Funny story, I had a 16bit app that echoed data out to prt1 via the shell.  Turned out that CMD could not process the data because if it being 32bit.  Ended up having to rename cmd.exe and create a batch file that echoed the stream to command.exe.  Worked great for 5 years before they replaced the system....thank god.

There are also some UNIX terminal emulators that will let you perform actions on the main drive.  I will have to look up the names as it has been a while since I used them.


Edit:  Just reread your clarification of Terminal vs Shell.  Most of what is above is useless...sorry about that.

---

### Post by vim_lover on 2010-10-06
[> __]("http://sourceforge.net/projects/console/")_[U][http://sourceforge.net/projects/console/](http://sourceforge.net/projects/console/)_[/U]
Thanks, that exactly I was looking for.  Any more terminals like this?

---

### Post by aditya3098 on 2011-12-06
If you are on Win7, then  to Control Panel->Programs and Features
and click on Turn Windows features on/off. Here, select Subsystem for unix-based applications and click OK. Then in your start menu, go to the subsystem for unix-based applications->download and download and install it. Then you will have a C-shell and a Korn-shell on your copy of Windows!!!

---

