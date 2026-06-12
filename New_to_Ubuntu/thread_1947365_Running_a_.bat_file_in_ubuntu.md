---
title: "Running a .bat file in ubuntu"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by egdisco on 2012-03-26
I would like to run a .bat file in ubuntu but I am unclear how to. Here is the BAT file.

java -Xmx1G -Xms1G -jar Tekkit.jar nogui
pause

Thank you.

---

### Post by jerome1232 on 2012-03-26
In linux it is called a shell script. All you need to do is open a text editor (Gedit will do) and put something like below, then save the file

```
#!/bin/bash
java -Xmx1G -Xms1G -jar Tekkit.jar nogui
read -p "Press [Enter] key to continue..."
```

Right click it, mark it as executable. Double click it and select run in terminal to run it.

Hope that helps.

---

### Post by MG&amp;TL on 2012-03-26
A few minor enhancements:

-remove "pause" -it's not necessary AFAIK, and it's a "command not found" job on my system.

-#!/bin/bash is a better choice for shell scripts.

---

### Post by jerome1232 on 2012-03-26
I think I misunderstood, if you actually have a .bat file you want to run you can use wine to run it. (I was thinking you simply wanted to create a little script)

If that is the case then you would install wine from the software center and then

```
wineconsole cmd
start filename.bat
```

I took the above instructions from this thread. 
[http://ubuntuforums.org/showthread.php?t=1377214](http://ubuntuforums.org/showthread.php?t=1377214)


edit: Also (if you are creating a shell script) I think the bash equivalent of DOS's pause would be something like

```
read -p "Press [Enter] key to continue..."
```

---

### Post by egdisco on 2012-03-26
> **jerome1232 said:**
> I think I misunderstood, if you actually have a .bat file you want to run you can use wine to run it. (I was thinking you simply wanted to create a little script)

If that is the case then you would install wine from the software center and then

```
wineconsole cmd
start filename.bat
```

I took the above instructions from this thread. 
[http://ubuntuforums.org/showthread.php?t=1377214](http://ubuntuforums.org/showthread.php?t=1377214)


edit: Also (if you are creating a shell script) I think the bash equivalent of DOS's pause would be something like

```
read -p "Press [Enter] key to continue..."
```

I installed wine and did what you said, all fine up until running the file. I started the file and it says it can't find the file. I am in the right directory and it is there. However, Terminal shows this: 
```
fixme:exec:SHELL_execute flags ignored: 0x00000100
wine: cannot find L"C:\\windows\\system32\\java.exe"
```

---

### Post by MG&amp;TL on 2012-03-26
Are you trying to run a .bat file as-is, or trying to use a script to run a java executable?

---

### Post by egdisco on 2012-03-26
> **MG&TL said:**
> Are you trying to run a .bat file as-is, or trying to use a script to run a java executable?

I am trying to run a script using wine to run a java file.

---

### Post by MG&amp;TL on 2012-03-26
Why do you want to run it under wine?

If you have a good reason, go ahead, but if you don't, wine is not the answer. :)

---

### Post by forrestcupp on 2012-03-26
You threw people off when you called a java file a .bat file. You don't want to run a .bat file, but a java .jar program.

Do you have Java installed? If OpenJDK and IcedTea don't work for you, [here is a web site that tells you how to install Oracle Java in Ubuntu.](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by idoitprone on 2012-03-26
[http://wiki.jswindle.com/index.php/Advanced_Wine_User_Information#Running_Batch_or_Bat_Files](http://wiki.jswindle.com/index.php/Advanced_Wine_User_Information#Running_Batch_or_Bat_Files)

```
wine cmd /c foo.bat
```
running .bat file wine

---

### Post by Mark Phelps on 2012-03-26
If you have Java runtime installed under Linux, there would be no point in running that batch file in Wine.  If you insist on running a file to invoke Java, just convert it to a script file (as you were already shown) and run it in Ubuntu.

---

### Post by qyot27 on 2012-03-26
> **jerome1232 said:**
> edit: Also (if you are creating a shell script) I think the bash equivalent of DOS's pause would be something like

```
read -p "Press [Enter] key to continue..."
```
Close.  It's actually
```
read -n1 -r -p "Press any key to continue..."
```
because the -n1 and -r enable it to use any key, rather than just Enter.

You can thankfully take that code snippet, make it into an executable shell script named 'pause' and copy it to /usr/bin.  Voila, 'pause' now exists and works just like you'd expect.  It's a lot easier to remember, too.

---

### Post by idoitprone on 2012-03-26
> **Mark Phelps said:**
> If you have Java runtime installed under Linux, there would be no point in running that batch file in Wine.  If you insist on running a file to invoke Java, just convert it to a script file (as you were already shown) and run it in Ubuntu.

the op loves confusin us
.bat file - windows or dos   - must use wine
.jar file - java  -   must use java

---

### Post by qyot27 on 2012-03-26
> **idoitprone said:**
> the op loves confusin us
.bat file - windows or dos   - must use wine
.jar file - java  -   must use java
It was perfectly clear to me.  But since some of the posts farther up seem to express confusion over what's going on...

The .bat was being used as a shortcut to run the java command, not that the OP was thinking the .jar file was a .bat.  It was a two-line script, the java line and the pause line, they just didn't put code tags around it.  The pause is necessary on Windows because a batch script executed with a double-click will automatically close the Command Prompt when finished, which destroys the ability to see program readout if there was an error.  The pause prevents it from closing so the readout can be viewed (running the script from an open Prompt doesn't close the Prompt).

On Linux, shell scripts are typically executed from an already open Terminal, so the pause would be superfluous unless there was a need for user prep time between operations (for instance, using a shell script to burn multiple CDs/DVDs - you need time to eject and insert discs).  It'd probably still be superfluous if shell scripts automatically launched the Terminal, because it likely wouldn't close the Terminal when finished, thus leaving it open to use for diagnosis (but I'm just guessing).

---

### Post by Jagoly on 2012-03-26
You wouldn't happen to be trying to run anything to do with a minecraft server would you?

---

### Post by egdisco on 2012-03-27
> **forrestcupp said:**
> You threw people off when you called a java file a .bat file. You don't want to run a .bat file, but a java .jar program.

Do you have Java installed? If OpenJDK and IcedTea don't work for you, [here is a web site that tells you how to install Oracle Java in Ubuntu.](http://sites.google.com/site/easylinuxtipsproject/java)

I can't run the .jar file on it's own as it doesn't have a GUI. It has to be opened using a .bat file and run from the CMD.

> **Jagoly said:**
> You wouldn't happen to be trying to run anything to do with a minecraft server would you?

Yes, I am attempting to. I'm trying to run Tekkit. [www.technicpack.net/tekkit](www.technicpack.net/tekkit)

---

### Post by Jagoly on 2012-03-27
Well, than I can help :-)
I've got two craftbukkit (the thing that tekkit is based on) servers, one running on my laptop that I use for playing with friends sometimes, and one running on my actual server at home. There is a bit more involved in running a craftbukkit serer though, tekkit simplifies things.

In nautilus (ubuntu's file manager), create a new directory in you home folder. for this example, Call it, without the quotes, "tekkit"

paste the contents of the tekkit zip file that you downloaded in here

Now, create a new file here called "launch.sh"
Open up that file in gedit (text editor) and paste in:
```
java -Xmx1024M -Xms1024M -jar tekkit.jar
```
and save the file.

now, right click on it, then click properties, then in the permissions tab, check the box "allow executing file as program"

now, open up a terminal (press ctrl+alt+t) and paste in:
```
cd ~/tekkit ; sh launch.sh
```
and press enter to launch tekkit.

If you dont have java installed, then run
```
sudo apt-get install openjdk-6-jre
```

---

### Post by egdisco on 2012-03-29
> **Jagoly said:**
> Well, than I can help :-)
I've got two craftbukkit (the thing that tekkit is based on) servers, one running on my laptop that I use for playing with friends sometimes, and one running on my actual server at home. There is a bit more involved in running a craftbukkit serer though, tekkit simplifies things.

In nautilus (ubuntu's file manager), create a new directory in you home folder. for this example, Call it, without the quotes, "tekkit"

paste the contents of the tekkit zip file that you downloaded in here

Now, create a new file here called "launch.sh"
Open up that file in gedit (text editor) and paste in:
```
java -Xmx1024M -Xms1024M -jar tekkit.jar
```
and save the file.

now, right click on it, then click properties, then in the permissions tab, check the box "allow executing file as program"

now, open up a terminal (press ctrl+alt+t) and paste in:
```
cd ~/tekkit ; sh launch.sh
```
and press enter to launch tekkit.

If you dont have java installed, then run
```
sudo apt-get install openjdk-6-jre
```

Thank you very much for this, it all works (apart from a Tekkit error which I will sort). Thank you all for the help.

---

### Post by Jagoly on 2012-03-29
Blessings of Notch upon you :-)

---

### Post by gradyrus on 2012-12-02
I too am new to Ubuntu I am running 12.10 and i am trying to set up a tekkit server which i am very good at on windows :( I followed your steps and when i type in the terminal to run the launch.sh it comes back and says no such file or directory sh: 0: cant open launch.sh

---

### Post by MG&amp;TL on 2012-12-02
> **gradyrus said:**
> I too am new to Ubuntu I am running 12.10 and i am trying to set up a tekkit server which i am very good at on windows :( I followed your steps and when i type in the terminal to run the launch.sh it comes back and says no such file or directory sh: 0: cant open launch.sh

You haven't got the launch.sh file in the right directory. Check your directory (Use the 'pwd' command) and either use 'cd' or move the file to the right place (the same directory you're in).

---

