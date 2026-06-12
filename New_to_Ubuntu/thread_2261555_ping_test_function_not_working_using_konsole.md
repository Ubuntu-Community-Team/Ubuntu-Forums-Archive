---
title: "ping test function not working using konsole"
date: 2015-01-19
forum: New to Ubuntu
---

### Post by gregory10 on 2015-01-19
need to know:
1. How to open a pre-set bash session in a new terminal as part of the script.
2. Part of the original test script is not working: it's the part that test's if the internet connection is open.

I tried many commands with both but nothing works so far. though I am sure there are simple ways to do it
just like the ones I have tried so far.
```

+ remotehost=google.com
+ '[!' 'trigger]'
/home/gregory/Documents/bashtutes/bashtutes.sh: line 20: [!: command not found
+ echo
```
So the function trigger is not working and trigger is this function below:
```

wtime=60
#
remotehost=google.com
function trigger {
  ping -qc 3 "$remotehost" >/dev/null   
  return $?                              
}
```
I need someone to tell me what is wrong with this function please
the '!' is supposed to work but bash seems to be saying there is no such command but it's there in the manual 
It should be that it results true if the term it's used in is false. In this case if google is pinged and there is ping return from google site then it's false
and if there is not then it is true. Maybe I have it wrong but I don't think so.

For the other I get the impression that something needs to be stored in an apropriate file
.profile or .profilerc
I think they are the files that need editing but where are they how do find them
I tried a lot of things.

I need to know how to edit those files and also the command to use to open the new tab once the profile is there to be opened using a command in the terminal
and also I need a function that test pings google to check if the internet connection is running: one that will  --->> if 'yes' then 'blah' else 'blah'. <<---

To know the answer to just one of these two things would be good progress
If anybody can help please do. the test function would be a good start.
This is the first part of the script I am working on here below:
```

#!/bin/bash


function openffox () {
    konsole --new-tab -e firefox http://google.com/ https://wiki.ubuntu.com/CustomXSession 
    return $?
#
echo "the internet connection is now opened all url's declared (the request message is sent to web services) firefox is set"
#
}


# wtime=60
#
#remotehost=google.com
function trigger {
#  ping -qc 3 "$remotehost" >/dev/null    
ping google.com -c 1
# ping "$remotehost" -c 1
return $?                              
 
}


if [! trigger]; then  # from bash -c help =====>   [! expression]  True if expression is false.
echo
echo "internet connection is closed; check to see if you are connected to a network or the modem is plugged in: try opening the connection manually"
echo
echo "Your internet connection is closed and you cannot have your internet session unless you connect to the internet; no internet: firefox is closed"
echo
else
echo
echo "Internet connection good to go, opening instance of firefox"
echo
openffox;
echo
echo "firefox running, browser set to go: your webpages are ready, you can do your research"
fi
# test it with this below
# bash -x ~/Documents/bashtutes/bashtutes.sh

```
If I test this script it all seems fine if I am connected to the internet because firefox opens the webpages
but the ping to test if the internet connections is open does not work. Bash is overiding and continuing with the rest of the script because it can't operate the command.
```

gregory@gregory-Satellite-L500:~$ bash -x ~/Documents/bashtutes/bashtutes.sh
+ '[!' 'trigger]'
/home/gregory/Documents/bashtutes/bashtutes.sh: line 23: [!: command not found
+ echo


+ echo 'Internet connection good to go, opening instance of firefox'
Internet connection good to go, opening instance of firefox
+ echo


+ openffox
+ konsole --new-tab -e firefox http://google.com/ https://wiki.ubuntu.com/CustomXSession
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
+ return 0
+ echo


+ echo 'firefox running, browser set to go: your webpages are ready, you can do your research'
firefox running, browser set to go: your webpages are ready, you can do your research
gregory@gregory-Satellite-L500:~$ 

```

There are other parts to the script I am writing. It is supposed to be that if the test ping works it continues opening the pages but if not only does the other functions
which will be included later after I get this working properly. thanks for any help. It is appreciated.

I really hope someone can help
the commands work well on their own but put them in a function and it changes things with the interpreter for some reason
thanks again
G

---

### Post by Holger_Gehrke on 2015-01-19
Regarding 1)
The window with the tabs is not the bash -- it's 'konsole'. The bash is just the program executing the commands you type into the window. So opening a tab with specific settings is not covered in the help for the shell it's in the manual for 'konsole' or it's help-file. Execute 'man konsole' in the bash to read the manual page for 'konsole', if it's anything like the page for gnome-terminal (which I am using) it answers this and many other questions in excruciating detail. If you do need to change settings for the shell itself (environment variables, shell options, aliases, predefined functions or stuff like that) the files '~/.bashrc' or '~/.profile' are the right place. The dot at the beginning of the names of these files makes file managers and the shell not show these files unless explicitly told to do so. The option '-a' to the 'ls' command makes it show hidden files, the option in file managers is different for each one ...

Regarding 2)
I already answered that in a post in the old thread, which I started writing before you opened this one.

---

### Post by gregory10 on 2015-01-23
@Holger_Gehrke
thanks for your answers to both of the remaining parts of my original question on the other thread.
I wasn't able to get this part of the script working. And found that there is not a manual for konsole like there is for gnome terminal.
I am able to open another tab manually, on that is set up with distinctive colours for the project I am working on.
I had a time limit for the script and in the end went with what I had because partly thanks for you giving your answer I am able
via the shortcut key sequence I setup and using the arrow keys to scroll through the command list with on click I can now open
all the apps I need for any given project with all the files inside them. Opening in a seperate tab means when I close the terminal
all the apps close as well and also get prompted to save any of my work that has not been saved in each if I have forgotten.

I am able now to teach the use of Linux as the most powerful organisational tool in the history of the world.
thanks again your answers really helped me to get my resolve.

All the best to the year ahead to everyone here
G

---

