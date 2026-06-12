---
title: "Help writing shell script"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by linuxguymarshall on 2008-08-26
I need some help writing a shell script. I need to know where to start. Preferable a guide in a step-by-step guide.

---

### Post by Dr Small on 2008-08-26
What about:
[http://linuxcommand.org/](http://linuxcommand.org/) ?

It should help you get your feet off the ground :)

---

### Post by linuxguymarshall on 2008-08-26
> **Dr Small said:**
> What about:
[http://linuxcommand.org/](http://linuxcommand.org/) ?

It should help you get your feet off the ground :)

The wiki-style how-to is great. Thanks for it.

---

### Post by nicedude on 2008-08-26
Ok fella I will try to help ya but I need some more info than just "I wanna write a script" as that tells me ( or anyone else ) nothing. Thats the same as saying I wanna run a command so can somebody help me write my command ( since bash scripts are just commands ). So if you clue me in on what you want to do I might be able to help.

nicedude

---

### Post by linuxguymarshall on 2008-08-26
I want to write a script that will automate my guide here : [http://ubuntuforums.org/showthread.php?t=894519](http://ubuntuforums.org/showthread.php?t=894519)

---

### Post by kdorf on 2008-08-26
A shell script is almost entirely composed of commands you would type at the command prompt. There are some other nifty features like ifs and loops, which you can learn more about by reading the bash manual.

---

### Post by linuxguymarshall on 2008-08-26
so basically what you are saying kdorf is after i do the ' #!/bin/sh
' or whatever it is at the top I can simply type in commands that follow?

so for example a script for installing wine would simply be 

```
 #!/bin/sh
sudo apt-get install wine

```

---

### Post by RequinB4 on 2008-08-26
> **linuxguymarshall said:**
> so basically what you are saying kdorf is after i do the ' #!/bin/sh
' or whatever it is at the top I can simply type in commands that follow?

so for example a script for installing wine would simply be 

```
 #!/bin/sh
sudo apt-get install wine

```

Yep, that's basically it.  bash (or sh, or whatever script language you are using) usually has more technical stuff (for loops, etc for advanced scripting) but that's esentially all it is - any command will do

funny example

```

#!/bin/sh
sudo apt-get install wine
echo "ZOMG Wine just got installed!"
mkdir randomfolder
cd randomfolder
touch zomgnewfile
rm zomgnewfile
cd ..
rmdir randomfolder
echo "Definitely did NOT just create a folder/file and then delete it"
echo ">.>"

```

etc :lolflag:

---

### Post by nicedude on 2008-08-26
Yep that is how it works but you can run into trouble if you want your script to run things in a terminal and run something else in another terminal etc or in loops and if type functions so read up on BASH and you can figure it out or at least allot of it :-)

---

### Post by linuxguymarshall on 2008-08-26
I have written a bit of it but I have one question. If ´mv´ moves then how do I copy?

---

### Post by nicedude on 2008-08-26
cp is copy

---

