---
title: "how to open program from terminal ?"
date: 2011-12-13
forum: New to Ubuntu
---

### Post by ahmedsmot on 2011-12-13
guys i learned to install programs using the command " apt- get install " in terminal so after that how i open the program or where i can find it ?

---

### Post by lisati on 2011-12-13
If the installation placed the program in the "execution path", then typing the program's name at the command prompt should work.

---

### Post by N00b-un-2 on 2011-12-13
depending on the program it installs a binary executable.  for example, to open gedit for terminal it's just gedit.  try typing in the name of the program.  if it's not an executable binary, but what you typed is similar to a real command it might offer you help.  Odds are though that the application (if it is a GUI application and not a command line application) should have added entries to your menu.  Then there is always alt+f2, kickoff, gnome-do, dash, etc...

---

### Post by papibe on 2011-12-13
Let's say you install asunder to rip CDs.
```
sudo apt-get install asunder
```
Now you can launch it using the GUI by taping the super key and star writing asunder until the icon appears.

Alternatively, you can launch it in the terminal like this:
```
asunder
```
or like this if you want to keep working in the terminal:
```
asunder &
```
I hope it helps.
Regards.

---

### Post by josephmills on 2011-12-13
> **ahmedsmot said:**
> guys i learned to install programs using the command " apt- get install " in terminal so after that how i open the program or where i can find it ?

Hello there in Ubuntu/GNU/Linux there are permissions and each permission has a job to do. As you guessed there is a permisssion called execute More about permissions can be found here. 
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

lets say I just installed links to my system 

elinks(

ELinks is an advanced and well-established feature-rich text mode web (HTTP/FTP/..) browser. ELinks can render both frames and tables, is highly customizable and can be extended via Lua or Guile scripts. It is quite portable and runs on a variety of platforms. Check the about page for a more complete description.)

to install (one way with apt )```
sudo apt-get install elinks notify-send
```

now that I have installed it I can run it two ways first I could find the binary cd to that dir and run ```
./elinks
```as it ./ means in the currebt directory 
Or the easy way just run the name of the program in this case it is elinks 

lets take this a step further say I wanted to ummm... find the UTC time and did not know about the command ```
date -utc
```

but I do know about this site that offer that for me. 
[http://tycho.usno.navy.mil/cgi-bin/timer.pl](http://tycho.usno.navy.mil/cgi-bin/timer.pl) 
but I do not want to open browser each time. so I can use elinks for this with a script. frist thing I do is open a text editor
 and  add ```
#!/usr/bin/env bash
```  as the top line. then I add my seript 
```
var=$( elinks http://tycho.usno.navy.mil/cgi-bin/timer.pl | awk '/UTC/ {print $6 $3 $5}');notify-send "The current $var" 

```

so the whole script will look like this 
```
#!/usr/bin/env bash
var=$( elinks http://tycho.usno.navy.mil/cgi-bin/timer.pl | awk '/UTC/ {print $6 $3 $5}');
notify-send "The current $var"

```

So I save the txt document as UTC  that is it **NO .sh** Just plain old UTC not UTC.sh

so I now have to make script be able to execute so I open my terminal and cd to where the script is and run the command ```
sudo chmod +x UTC
``` I know cd to the correct place that has my script and run ```
./UTC
``` or move the script to a bin folder and just do command ```
UTC
```
Please see [http://mywiki.wooledge.org/BashGuide/CommandsAndArguments](http://mywiki.wooledge.org/BashGuide/CommandsAndArguments)

ok now that we did all that pleaser open terminal and type in ```
date --universal 
```

---

