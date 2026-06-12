---
title: "Trying to run .bat file."
date: 2016-01-03
forum: New to Ubuntu
---

### Post by Egg_TInker on 2016-01-03
So I'm trying to get a .bat file to start for a game but it opens in a text editor.

So if someone could explain how to get it to run properly, preferably in detail, that would be much appreciated.

and if you need it here's what's inside the file :


@echo off
echo            ******************************************
echo  _______   ______         __       __    ______   _______       
echo /\   __ \ /\  ___\  ____ /\ \     /\ \  /\  ___\ /\   __ \      
echo \ \  \_\ \\ \ \__/ /\___\\ \ \  __\ \ \ \ \ \__  \ \  \_\ \     
echo  \ \  ___ \\ \ \   \/___/ \ \ \/\ \\ \ \ \ \  _\  \ \   __ \    
echo   \ \ \\ \ \\ \ \____      \ \ \_\ \\_\ \ \ \ \____\ \  \_\ \   
echo    \ \_\\ \_\\ \_____\      \ \__________\ \ \_____\\ \______\ 
echo     \/_/ \/_/ \/_____/       \/__________/  \/_____/ \/______/
echo        ___________________________________________________
echo       /\_________________www.ac-web.org___________________\
echo       \/_____________AC Web Ultimate Repack_______________/ 
echo Please dont close Window while MySQL is running
echo MySQL is trying to start
echo Please wait  ...
echo MySQL is starting with mysql\bin\my.cnf (console)


mysql\bin\mysqld --defaults-file=mysql\bin\my.cnf --standalone --console


if errorlevel 1 goto error
goto finish


:error
echo.
echo MySQL could not be started
pause


:finish

**EDIT :**
Thanks for all your input guys/gals, I appreciate it.

So after messing around with it for a while I found the solution.

In the terminal I did *wine cmd* then navigated to the folder containing the .bat file with the *cd* command then ran *start MySQL.bat *and it ran perfectly[I].

[/I]Hopefully someone else finds this useful someday. :)

---

### Post by HermanAB on 2016-01-03
You need Microsoft Windows for that.

---

### Post by buzzingrobot on 2016-01-03
A batch --.'bat' -- file is exclusive to Windows (and DOS, where their use began). They can't run in another operating system. Windows executes them with command.com, which doesn't exist in Linux.

The equivalent in Linux is a shell script.

A package of programs called WINE is available for Linux that may allow some Windows programs to run on Linux. It's not a magic bullet and there's no certainty any given Windows program will execute correctly. WINE is available in the Ubuntu repos. It's site, including a list programs that work with WINE, is here: [URL="https://www.winehq.org/"]https://www.winehq.org/ 


[/URL]

---

### Post by brian-mccumber on 2016-01-03
They will work but you need wine installed like buzzingrobot said, I found this guide if you feel like reading it. But again like buzzingrobot said it may or may not work but experimenting can be fun sometimes if it doesn't break too much stuff even then there is not much you can do to break Ubuntu that can't be fixed one way or another.

[http://www.linux.org/threads/running-windows-batch-files-on-linux.7610/](http://www.linux.org/threads/running-windows-batch-files-on-linux.7610/)

---

### Post by DuckHook on 2016-01-03
Please don't think me overly critical because what follows is not meant in anything but the friendliest way, but you are trying to run without first learning how to even crawl. If you do not understand the nature of bat files to DOS vs shell scripts to Linux, then how on earth are you going to administer and maintain something as advanced and complex as mysql?

Tell us what you are actually trying to achieve. Perhaps we can give you better advice for achieving your end goal rather than getting bogged down in meaningless processes along the way.

---

### Post by brian-mccumber on 2016-01-03
> **siloam said:**
> I don't think it's a good idea to use emulators like Wine to run such scripts.

I noticed that it seemed to be starting an instance of mySql but in the original post he said it was for starting a game which would probably need Wine to run so I just agreed with what buzzingrobot said about using Wine and I also said that it may or may not work. 

So that said that script wouldn't be hard to convert to bash but if it is starting an instance of mySql for a game that runs on Windows it would need to start a sql server through Wine because Windows programs run in Wine do not look for stuff running in Ubuntu only stuff being ran in the emulator.

That batch file may be run from an installation of a Windows game that is installed through Wine so converting to a bash script would not work either in that case.

---

### Post by buzzingrobot on 2016-01-03
I saw the game reference but not the MySQL reference, assuming the batch file launched a Windows game. Hence, Wine.

The ac-web.org contained in the file hypes itself as the "WoW Emulation Source".  There are references to SQL scattered on it, and forum sections about databases and such.  I know zip about games, but if KDE can make a mail client that needs MySQL I guess so can games.;)

---

### Post by grahammechanical on 2016-01-03
AC web Ultimate Repack is, to quote the developers

> AC Web is a community dedicated to World  of Warcraft emulation and private servers. We were originally founded in  2007 by the site owner Jargs, and were one of the first websites to  provide a package of applications designed to simplify the process of  setting up a WoW private server. This package is commonly known as a  &#8220;Repack&#8221;. 


Just so we can know what we are arguing about instead of arguing about what we do not know.

---

### Post by brian-mccumber on 2016-01-03
For the record I wasn't arguing with anyone, I was just pointing out what op had posted about and he said it was for a game so I took his word for it because he is the one trying to install it regardless of the fact that I thought it was also strange that a game would start a sql instance but I have played games that do use a db to store user configs and data before so...

---

