---
title: "Emacs and GCC problems"
date: 2005-05-29
forum: Programming Talk
---

### Post by kenux on 2005-05-29
Ok im trying to get EMACS and GCC installed. I used the sudo apt-get install gcc for gcc and i thought that worked to get the whole gcc package installed. This then allowed me to go through the process of installing emacs. But when i go to run emacs i get this error.

"emacs: Cannot open termcap database file"

then also when i go to compile with g++ i get this error:

"bash: g++: command not found"

Any help on getting this stuff up and running. Im new to the whole linux thing and thought i could figure it all out but im having troubles.

Thanks
Ken

---

### Post by tread on 2005-05-29
sudo apt-get install build-essential

and 

sudo apt-get install emacs21

should get you set.

---

### Post by kenux on 2005-05-29
i can compile now but i still cannot use emacs.

i still get the same error:

"emacs: Cannot open termcap database file"

But at least im getting further along. I have only tried to install this stup and have updated firefox, so it is a clean install.

Thanks,
Ken

---

### Post by jerome bettis on 2005-05-29
sudo apt-get install termcap-compat

---

### Post by kenux on 2005-05-29
tried that but got couldnt find termcap-compat when i tried to run it

---

### Post by LordHunter317 on 2005-05-29
[QUOTE=kenux]tried that but got couldnt find termcap-compat when i tried to run it[/QUOTE]
 How did you install emacs?  sudo apt-get install emacs21 should get you the latest version of emacs.  If you're getting that error and that's what you did, there's a packaging bug somewhere.

More details are helpful.  **I cannot stress enough** how critical is when something isn't working, to post more than this.  Don't post just the error message.  That doesn't tell anyone anything.  You have to post what you did to get that message as well.

---

### Post by jerome bettis on 2005-05-29
you don't need to run it it just fixes that problem in emacs.  if it didn't install edit /etc/apt/sources.list and uncomment all those repositories.

---

### Post by kenux on 2005-05-29
Ok so what i did to install emacs was first i installed the gcc compiler by going into the terminal and using "sudo apt-get install gcc" then after this i did "sudo apt-get install build-essential" then i did "sudo apt-get install emacs21" so after that all was installed.

But run i go to run emacs from the terminal i get the "emacs: Cannot open termcap database file" error, so there isnt that much that im doing. But i can run emacs from applications->accesories->emacs 21 but i would like to be able to run it from the terminal. 

This was a clean install so there shouldnt be any thing conflicting. Also this time i turned on my comp and my resolution can only be set to 640X480 so now i have something else to try and fix.

Ken

---

### Post by LordHunter317 on 2005-05-29
[QUOTE=kenux]Ok so what i did to install emacs was first i installed the gcc compiler by going into the terminal and using "sudo apt-get install gcc" then after this i did "sudo apt-get install build-essential" then i did "sudo apt-get install emacs21" so after that all was installed.

But run i go to run emacs from the terminal i get the "emacs: Cannot open termcap database file" error, so there isnt that much that im doing. But i can run emacs from applications->accesories->emacs 21 but i would like to be able to run it from the terminal. 

This was a clean install so there shouldnt be any thing conflicting. Also this time i turned on my comp and my resolution can only be set to 640X480 so now i have something else to try and fix.

Ken[/QUOTE]
 Did you manage to uninstall ncurses-base somehow?  That would cause the error you're seeing.  Other than that, you may have an environment issue, post the output of 'printenv'.

---

### Post by kenux on 2005-05-29
Here it is, its frustrating because i can run it from the app menu but not terminal:

ken@kenux:~$ printenv
SSH_AGENT_PID=6555
TERM=xterm
DESKTOP_STARTUP_ID=
SHELL=/bin/bash
GTK_RC_FILES=/etc/gtk/gtkrc:/home/ken/.gtkrc-1.2-gnome2
WINDOWID=46137417
USER=ken
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.ogg=01;35:*.mp3=01;35:*.wav=01;35:
GNOME_KEYRING_SOCKET=/tmp/keyring-Eai08R/socket
SSH_AUTH_SOCK=/tmp/ssh-RUUFsD6510/agent.6510
SESSION_MANAGER=local/kenux:/tmp/.ICE-unix/6510
USERNAME=ken
DESKTOP_SESSION=default
PATH=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
GDM_XSERVER_LOCATION=local
PWD=/home/ken
LANG=en_US.UTF-8
GDMSESSION=default
HOME=/home/ken
SHLVL=1
LANGUAGE=en
GNOME_DESKTOP_SESSION_ID=Default
LOGNAME=ken
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-fGl8LRN855
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/home/ken/.Xauthority
_=/usr/bin/printenv

---

### Post by kenux on 2005-05-29
also i am just trying to compile and run a little test program of hello world and this is my code

  #include <iostream>
  int main()
    {
    cout << "Hello, World\n";
    return -1;
    }

and this is my results from compiling

ken@kenux:~$ g++ test.cpp -o test
test.cpp: In function `int main()':
test.cpp:4: error: `cout' undeclared (first use this function)
test.cpp:4: error: (Each undeclared identifier is reported only once for each
   function it appears in.)

i mean it just the standard libraies shouldnt they be installed.

Thanks
Ken

---

### Post by LordHunter317 on 2005-05-29
[QUOTE=kenux]i mean it just the standard libraies shouldnt they be installed.[/quote]No, it means just what it says.  You forgot to import the standard namespace.  If the header defining that stuff was missing, you would get a different error.

Anyway, what about the package?  There's nothing wrong with your environment so I don't know why emacs is attempting to look at legacy termcap stuff.

---

### Post by kenux on 2005-05-29
Any way to make that compiling error go away?

---

### Post by toojays on 2005-05-29
Either add "using namespace std;" after you include the header, or refer to cout as std:cout.

---

### Post by kenux on 2005-05-29
haha thanks, we didnt have to use that in my programs a school.

NBow if only i can get this emacs thing up and running from the terminal i would be happy.

Ken

---

### Post by toojays on 2005-05-30
Is it possible that you have some termcap config files in your home directory which are complicating issues? This would only happen if you copied your home directory over from another computer or OS. Have you tried running emacs as another user?

---

### Post by kenux on 2005-05-30
Well it was a clean install and i havent used linux before. So i just reinstalled it and used the synaptic to get all the programs i wanted and now it works fine.

Ken

---

### Post by kenux on 2005-05-30
also is there a way to make it so that you do not have to type "./" before you want to run a program that i have compiled.

Ken

---

### Post by toojays on 2005-05-31
Yes, there is a way (add . to the path), but it's considered bad form on a multiuser system due to the security risk.

---

### Post by LordHunter317 on 2005-05-31
[QUOTE=toojays]Yes, there is a way (add . to the path), but it's considered bad form on a multiuser system due to the security risk.[/QUOTE]
 In fact, it's such bad form it'd be better to not even mention it at all.

---

### Post by jerome bettis on 2005-05-31
yeah plus it's a lot more work then just typing ./

two extra buttons won't kill you.  you could also make a ~/bin directory, put that in the path and then do gcc x.c -o ~/bin/x  if you wanted but ./ is still easier.

---

### Post by ocorrain on 2005-06-14
[QUOTE=kenux]Ok so what i did to install emacs was first i installed the gcc compiler by going into the terminal and using "sudo apt-get install gcc" then after this i did "sudo apt-get install build-essential" then i did "sudo apt-get install emacs21" so after that all was installed.


But run i go to run emacs from the terminal i get the "emacs: Cannot open termcap database file" error, so there isnt that much that im doing. But i can run emacs from applications->accesories->emacs 21 but i would like to be able to run it from the terminal. [/QUOTE]

I take it you've compiled an emacs from source with gcc, and also installed
the Ubuntu packaged version.

In that case you've got two versions of emacs, one in /usr/local (from the
source build), and one in /usr (from the package). The application launcher
points to the latter, but when you type "emacs" into the shell, it attempts
to run the source compiled one, which is broken (/usr/local/bin appears
before /usr/bin in your execution). Typical Unix confusion (sigh).

If you want to compile a working emacs from source (CVS for example), you'll
need to install these packages:
[list]
[*]termcap-compat
[*]xlibs-dev
[*]build-essential
[/list] 

To run your Ubuntu package from the command line, specify /usr/bin/emacs, and
you should be fine.

---

### Post by danish_demon on 2006-01-10
alright, i am having the same problem as the person who started this thread.  however, when i try to do the "sudo apt-get install emacs21" command, it gives me this output:
> 
sudo apt-get install emacs21
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package emacs21


any ideas?  i did a google search on installing emacs first and followed those instructions (which involved obtaining files from gnu's ftp server, a "./configure" command, followed by a make and make install (i think there was a "compile" in there as well).  those operations completed without any errors, but lots of warnings about "signage" for parameters in various functions/files.

EDIT:  i was browsing through the forum some more and stumbled upon a link to a site that enables using extra repositories.  once i did that and then tried the "sudo apt-get install emacs21" again, it worked.

---

### Post by danish_demon on 2006-01-10
alright, now i have another issue, but one that i think is probably a little bit simpler.  how do i set up my system so emacs opens up in its own window.  i'm a real noob here when it comes to setting up a linux system, but i am used to being able to type something like "emacs foo &" and foo pops up in its own window.

EDIT:  again, i've solved my own problems.  it's amazing what simply writing out a problem does for your motivation to solve it yourself.  i promise no more questions in this thread (at least for now... :)  )

---

### Post by coredump on 2006-01-10
Could you tell us how you solved the emacs-in-a-window question?  I'm sure other would like to know, too.  Did you run 'xterm' and give it your 'emacs' command as an argument (with a '-e' option?)?

---

### Post by danish_demon on 2006-01-10
i realized that typing "emacs" in the terminal started one version of emacs (the one, i believe, i downloaded myself via gnu) and typing "emacs21" started the version i got with ubuntu via apt-get install emacs21.  the emacs21 version is the one that allows windowing, so i simply set up a bash alias that went: alias emacs='emacs21'

problem solved.  thanks for having me explain things; i imagine it is something that others may run into.

---

