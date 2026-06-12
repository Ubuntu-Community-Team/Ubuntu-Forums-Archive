---
title: "[SOLVED] Script Help"
date: 2008-01-19
forum: Programming Talk
---

### Post by kbless7 on 2008-01-19
I have this problem with matlab that I need to change the java on it and launch it from the terminal because it doesn't work otherwise. So I've been working on a scrip to do that, but so far I can't get the java part to execute. 

```
#!/bin/sh
gnome-terminal --export "MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.03/jre"

```

This is the part I'm using to change the matlab java and it works by itself (export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.03/jre) in the terminal but I can't get it to work with the script. It out puts:

```
matt@Matthew:~$ sh .matlab.sh
Invalid argument: "MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.03/jre"

```

What am I doing wrong?
Thanks

-Matt

---

### Post by kbless7 on 2008-01-19
forgot to subscribe

---

### Post by kbless7 on 2008-01-19
Right now I have the script so I can click my matlab icon in kiba-dock. this is what I have in the script

```
#!/bin/sh 
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.03/jre
.matlab/bin/matlab
```

This will open matlab after it changes out the java. Now I want to be able to have it so the terminal will exit with matlab still running, but when I do 

```
.matlab/bin/matlab&
```

it doesn't run or detach the program from the terminal.

HELP PLEASE!!!

---

### Post by naugiedoggie on 2008-01-20
> **kbless7 said:**
> Right now I have the script so I can click my matlab icon in kiba-dock. this is what I have in the script

```
#!/bin/sh 
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.03/jre
.matlab/bin/matlab
```

This will open matlab after it changes out the java. Now I want to be able to have it so the terminal will exit with matlab still running, but when I do 

```
.matlab/bin/matlab&
```

it doesn't run or detach the program from the terminal.

HELP PLEASE!!!

Hello,

Well, I don't believe this is going to work in the manner you expect.  

When you run a script, it creates its own shell as a subshell of the parent shell.  The subshell inherits the shell variables you set, as well as all the variables of the parent.  But, nothing you are doing in that script propagates up to the parent.  Therefore, when you "background" the shell in your script, you are backgrounding the child shell, which is probably why the application appears not to run.  If you looked in your process list, you would see it.  

It's not clear to me why you don't just set the MATLAB_JAVA variable in your login shell in .bash_profile or .bashrc.  Then you can run your application directly, without any fancy footwork.

Otherwise, I think the answer is that you should expect to have the terminal window open until you're done with MatLab.

Thanks.

mp

---

### Post by kbless7 on 2008-01-20
well i do have it set in the .basrc, but i still have to run matlab from the terminal otherwise it just won't run.
I thought running a script was just like typing the stuff into a terminal but its not working out that way.

---

### Post by geirha on 2008-01-20
Right click the desktop and choose Create Launcher. Set the following as the command:
```
bash -c 'MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.03/jre $HOME/.matlab/bin/matlab'
```

I'm assuming here that the path to matlab above, .matlab/bin/matlab, is relative to your homedir. Is matlab really installed in a hidden directory btw? I'd assume it would really be $HOME/matlab/bin/matlab ...

---

### Post by kbless7 on 2008-01-20
> **geirha said:**
> Right click the desktop and choose Create Launcher. Set the following as the command:
```
bash -c 'MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.03/jre $HOME/.matlab/bin/matlab'
```

I'm assuming here that the path to matlab above, .matlab/bin/matlab, is relative to your homedir. Is matlab really installed in a hidden directory btw? I'd assume it would really be $HOME/matlab/bin/matlab ...

Yes it is a hidden directory in my home folder. I didn't want it showing up. That doesn't work. Just like before the pre-menu of matlab shows up and disappears. This is the same problem I've been having all along. The only time it stays up is when I type .matlab/bin/matlab in the terminal

---

### Post by geirha on 2008-01-20
What does that menu look like? What is it asking for?

Try running matlab --help, and see if you can specify the menu-choice on the command-line...

---

### Post by kbless7 on 2008-01-20
> **geirha said:**
> What does that menu look like? What is it asking for?

Try running matlab --help, and see if you can specify the menu-choice on the command-line...

Where whould i run  matlab --help? I have attached the picture of what the pre-menu looks like.

---

### Post by naugiedoggie on 2008-01-20
> **kbless7 said:**
> well i do have it set in the .basrc, but i still have to run matlab from the terminal otherwise it just won't run.
I thought running a script was just like typing the stuff into a terminal but its not working out that way.

After you put the MATLAB_JAVA entry in your startup script, did you reboot?  The reason for the reboot is that you have to restart the GUI in order for it to read the new entry.  There actually probably is a restart command for gnome, which might restart gdm, but I don't know it.  The simplest ploy is just reboot the box.

And no, there are important differences between running a script and typing in a terminal, as you have seen.  Mostly around what I stated earlier.  Just think in terms of the script running in a different shell from the one in which you executed it.

Thanks.

mp

---

### Post by geirha on 2008-01-20
> **kbless7 said:**
> Where whould i run  matlab --help? I have attached the picture of what the pre-menu looks like.

A menu is typically a list of options that you are made to choose from. That window there is what's called a splash screen. I thought maybe you had to choose from some options in order to continue. 

Anyway, do you have any java programs that doesn't work with sun's java 6? If not, you could just set sun's java 6 as the default java version by running ```
sudo update-java-alternatives --set java-6-sun
```

---

### Post by kbless7 on 2008-01-20
> **naugiedoggie said:**
> After you put the MATLAB_JAVA entry in your startup script, did you reboot?  The reason for the reboot is that you have to restart the GUI in order for it to read the new entry.  There actually probably is a restart command for gnome, which might restart gdm, but I don't know it.  The simplest ploy is just reboot the box.

And no, there are important differences between running a script and typing in a terminal, as you have seen.  Mostly around what I stated earlier.  Just think in terms of the script running in a different shell from the one in which you executed it.

Thanks.

mp

I have restarted several times and it does work. The issue I have is that I have to leave a terminal open through the script or I have to start the program through the terminal. It's not the biggest hassle in the world but there has to be an explanation for why it only works through the terminal. 

Plus I don't anything about programming with shells and scripts so I don't know how to think in "terms of the script running in a different shell."

---

### Post by kbless7 on 2008-01-20
> **geirha said:**
> A menu is typically a list of options that you are made to choose from. That window there is what's called a splash screen. I thought maybe you had to choose from some options in order to continue. 

Anyway, do you have any java programs that doesn't work with sun's java 6? If not, you could just set sun's java 6 as the default java version by running ```
sudo update-java-alternatives --set java-6-sun
```

Do you have any clue why the splash screen would just disappear like that and the program wouldn't continue to load?

---

### Post by po0f on 2008-01-21
kbless7,

What about this script?

```
#!/bin/bash

cd ~/.matlab/bin
MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.03/jre ./matlab
```

---

### Post by kbless7 on 2008-01-21
> **po0f said:**
> kbless7,

What about this script?

```
#!/bin/bash

cd ~/.matlab/bin
MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.03/jre ./matlab
```

Currently that does the same thing my script does. Do you know how to make it then quit the terminal but leave the program running?

---

### Post by po0f on 2008-01-21
kbless7,

*Usually*, appending an ampersand to the end of a command should background it, leaving the terminal free (to be closed in this case).  Have no clue why it's not working for you.

Does it work though?  If it works, you can put the script in PATH [1] and just use the "Run Application" dialog (brought up with alt-f2) to run it.


[1] I suggest ~/bin, then make sure the following is in ~/.bashrc / ~/.bash_profile (dunno if it makes a difference either way):

```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

This will prepend ~/bin to PATH, allowing bash to find any custom scripts/programs you want to use before checking the rest of PATH.

Actually, /usr/local/bin would probably be an easier choice; there is more setup work to get it to behave like this IIRC.

---

### Post by popch on 2008-01-21
Shouldn't the ampersand be preceded by a space?

---

### Post by geirha on 2008-01-21
> **kbless7 said:**
> Do you have any clue why the splash screen would just disappear like that and the program wouldn't continue to load?

That's specific to the application. Without knowing how it works, I can't know why. It's possible that .matlab/bin/matlab is a script. Identify what type of file it is with file: ```
file ~/.matlab/bin/matlab
```

If it is a script, open it in an editor and see if you can figure out what it does and what it starts. Normally I would ask you to post the script here, but matlab is not open source, so that might be violating some license agreement.

---

### Post by naugiedoggie on 2008-01-21
> **kbless7 said:**
> I have restarted several times and it does work. The issue I have is that I have to leave a terminal open through the script or I have to start the program through the terminal. It's not the biggest hassle in the world but there has to be an explanation for why it only works through the terminal. 

Plus I don't anything about programming with shells and scripts so I don't know how to think in "terms of the script running in a different shell."

I agree, it's annoying when an application behaves in a manner not readily understood.  Well, one thing you can try is, start the app from a launcher and then after the splash screen appears/disappears, do CTRL-ALT-F1, which will take you to the first virtual terminal.  You should see a login prompt there.  Then ALT-left arrow and you will be at the terminal from which the gdm graphical login is running.  If the crashing of the application wrote any error messages to the stderr output, they may be on that screen.  That may give you a clue as to what is happening.

The usual cause of that kind of behavior is a missing library of some kind.  It is not usual for the application to work from a terminal but not from a launcher in that case, however.

A bit of a long shot, but it takes less than 60 seconds to check it.

Oh yeah, and ALT-F7 to get back to gnome.  ;-)

Thanks.

mp

---

### Post by kbless7 on 2008-01-21
> **naugiedoggie said:**
> I agree, it's annoying when an application behaves in a manner not readily understood.  Well, one thing you can try is, start the app from a launcher and then after the splash screen appears/disappears, do CTRL-ALT-F1, which will take you to the first virtual terminal.  You should see a login prompt there.  Then ALT-left arrow and you will be at the terminal from which the gdm graphical login is running.  If the crashing of the application wrote any error messages to the stderr output, they may be on that screen.  That may give you a clue as to what is happening.

The usual cause of that kind of behavior is a missing library of some kind.  It is not usual for the application to work from a terminal but not from a launcher in that case, however.

A bit of a long shot, but it takes less than 60 seconds to check it.

Oh yeah, and ALT-F7 to get back to gnome.  ;-)

Thanks.

mp

Do I login in and then ALT-left arrow or ALT-left arrow without logging in?
Because I logged in first and it just beeps at me when I try ALT-left arrow

---

### Post by kbless7 on 2008-01-21
> **geirha said:**
> That's specific to the application. Without knowing how it works, I can't know why. It's possible that .matlab/bin/matlab is a script. Identify what type of file it is with file: ```
file ~/.matlab/bin/matlab
```

If it is a script, open it in an editor and see if you can figure out what it does and what it starts. Normally I would ask you to post the script here, but matlab is not open source, so that might be violating some license agreement.

I found out that it is a POSIX shell script text executable with 1725 lines of code. That leaves me pretty lost.

---

### Post by kbless7 on 2008-01-21
> **po0f said:**
> kbless7,

*Usually*, appending an ampersand to the end of a command should background it, leaving the terminal free (to be closed in this case).  Have no clue why it's not working for you.

Does it work though?  If it works, you can put the script in PATH [1] and just use the "Run Application" dialog (brought up with alt-f2) to run it.


[1] I suggest ~/bin, then make sure the following is in ~/.bashrc / ~/.bash_profile (dunno if it makes a difference either way):

```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

This will prepend ~/bin to PATH, allowing bash to find any custom scripts/programs you want to use before checking the rest of PATH.

Actually, /usr/local/bin would probably be an easier choice; there is more setup work to get it to behave like this IIRC.

Sorry, but I'm not to sure what you are trying to say. This is the first programming like stuff I have done in ubuntu so its a little hard to comprehend. Are you saying the make a script file of the code you presented and put it in either directory? Thanks.

P.S. When I put the ampersand in the script it causes matlab to run in the terminal.

---

### Post by wdk on 2008-01-21
If I understand correctly, you want to be able to click on an icon and start matlab.

You should be able to do that if you use the command

matlab -desktop

in your launcher or script. I have no idea if it will work from Kiba Dock (I don't see why not), but it will work from the desktop and the main menu.

You may find more helpful explanations and information in the documentation:
[http://www.mathworks.com/access/helpdesk/help/techdoc/matlab.html](http://www.mathworks.com/access/helpdesk/help/techdoc/matlab.html)
Go to the index and down to the entry for the "matlab function for UNIX" entry.

hope this helps!

---

### Post by kbless7 on 2008-01-21
> **wdk said:**
> If I understand correctly, you want to be able to click on an icon and start matlab.

You should be able to do that if you use the command

matlab -desktop

in your launcher or script. I have no idea if it will work from Kiba Dock (I don't see why not), but it will work from the desktop and the main menu.

You may find more helpful explanations and information in the documentation:
[http://www.mathworks.com/access/helpdesk/help/techdoc/matlab.html](http://www.mathworks.com/access/helpdesk/help/techdoc/matlab.html)
Go to the index and down to the entry for the "matlab function for UNIX" entry.

hope this helps!

I've heard this before but I don't know what it is talking about. As in where would I run matlab -desktop, etc.\


[COLOR="Red"]EDIT: The command in my case is .matlab/bin/matlab -desktop and now I'm free of the terminal. Thanks for all of the help guys.
I'm just back to the java problem. I should be able to just replace the java file under matlab somehow.[/COLOR]

---

### Post by wdk on 2008-01-21
I'm glad the last suggestion worked for you.

For your Java problem, you may find the following post useful:
[http://ubuntuforums.org/showthread.php?t=635142](http://ubuntuforums.org/showthread.php?t=635142)

If you are hesitant to change the actual matlab startup script, a script similar to the one you posted earlier should work:

```

#!/bin/sh
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre
matlab -desktop

```

good luck!

---

### Post by kbless7 on 2008-01-21
> **wdk said:**
> I'm glad the last suggestion worked for you.

For your Java problem, you may find the following post useful:
[http://ubuntuforums.org/showthread.php?t=635142](http://ubuntuforums.org/showthread.php?t=635142)

If you are hesitant to change the actual matlab startup script, a script similar to the one you posted earlier should work:

```

#!/bin/sh
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre
matlab -desktop

```

good luck!

Major kudos. I went off what you did
```

#!/bin/sh
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre
.matlab/bin/matlab -desktop

```
for launcher command I just did
 ```
sh .matlab.sh
```

Everything is just how it should be. Apparently Matlab needs a shell to run unless you do the -desktop commands.

THANK YOU EVERYONE

---

### Post by DaveWard on 2008-04-13
The problem of printing through context menus from Java apps is not limited to Matlab and originates from a badly handled return from cups in Java. The return in question comes from the orientation option,specifically when it is set to “auto”. There are bug reports on the Java and cups bug report systems for this and they will hopefully be handled in the upcoming releases... 

However... 

A work-around which sorts this out on my system is to simply set the orientation in the printer-config to something other than automatic (portrait in my case), You can also do this by adding "Option orientation-requested 3" before /printer in /etc/cups/printers.conf for all the printers on the system. I am not sure what the auto setting does as my printer defaults to portrait anyway so doing this doesn't cause me any issues.  

This is unrelated to the issues of Matlab (or Swing) not working with Beryl/Compiz, which seem to have been fixed in Matlab R2008a.

---

