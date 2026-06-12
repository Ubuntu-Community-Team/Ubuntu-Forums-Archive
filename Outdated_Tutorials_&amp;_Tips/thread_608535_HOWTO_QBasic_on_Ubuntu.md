---
title: "HOWTO: QBasic on Ubuntu"
date: 2007-11-10
forum: Outdated Tutorials &amp; Tips
---

### Post by gnarula on 2007-11-10
As a student of Class VIII, I regularly need to check my BASIC Programs on my computer. After having ubuntu installed I needed a gui dialect/interpreter/compiler for BASIC. In Windows, QBASIC did the job for me. I thought of emulating it with Wine at first but after no success i came across "dosbox" which emulates DOS environment.

So heres how to do it:

Open a terminal and type:

```
sudo apt-get install dosbox
```

This should install dosbox on your ubuntu desktop. Next type:

```
wget http://download.microsoft.com/download/win95upg/tool_s/1.0/w95/en-us/olddos.exe
```

Open your home directory and right-click the olddos.exe file. Open it with archive manager. Extract it to a new folder, I suggest QBasic.

Now in the terminal type:
```
dosbox
```

After "dosbox" opens type the following:

```
mount c /home/username/QBasic/
C:
QBASIC.EXE
```

Thats it! Now, U have QBasic running on ur Ubuntu Desktop. Similarly, one can install dos games.

Gaurav

---

### Post by likeachild83 on 2007-11-28
Thanks for posting this. I have to work in qbasic for school and wanted to get my stuff done from home, now I can!

---

### Post by Genecks on 2008-07-07
Call me stupid, but this doesn't work.
How exactly is archive manager going to open and install a .exe?

Annoying, original poster...
**Ok, I got it incase anyone wants to know.**

1. install dosbox as above

> sudo apt-get install dosbox

2. Create a folder in your $HOME directory

I suggest $HOME/.olddos/

> mkdir $HOME/.olddos/

3. Download the olddos.exe file.

> wget [http://download.microsoft.com/download/win95upg/tool_s/1.0/w95/en-us/olddos.exe](http://download.microsoft.com/download/win95upg/tool_s/1.0/w95/en-us/olddos.exe)

4. Copy or move it to $HOME/.olddos/

> cp $HOME/olddos.exe $HOME/.olddos/

5. Go into a terminal and type

> dosbox

6. Now, you should be inside what appears to be a CLI similar to DOS.

[I]* Remember to replace "/username/" with your username, which is shown as the name before the @ whenever you use the terminal. For example, mine is smoke:

smoke@mortalkombat:~$[/I]

Edit and insert the following:

> mount c /home/username/.olddos/

Mine looks like this:
*mount c /home/smoke/.olddos/*

Hit enter.

> C:

Hit enter.



Now, for old time's sake, type the following:

> dir /p

Haha, there go those ls commands. lol.

now type in the following

> olddos.exe

Hit enter.

If you've used DOS before, you should know what to do.
If not... pity... you've been missing all the fun.

> qbasic.exe

Hit enter.

After that, I suggest putting an alias in your $HOME/.bashrc file to QBasic. 
And all seems excellent, I would figure.

* Remove -fullscreen from the below code if you don't want the fullscreen.

> echo "alias qbasic='dosbox ./.olddos/QBASIC.EXE -fullscreen'" >> $HOME/.bashrc

* Note:

[I]If you use the above line of code and don't like fullscreen, manually edit the $HOME/.bashrc file. 
It's not too difficult of a task to remove this one line.

Use gedit to do so.

> gedit $HOME/.bashrc[/I]

Restart the terminal and type...

> qbasic

* It's case-sensitive, meaning use lower-case letters.

If you use qbasic via the aliased command--and then you try to save files inside of qbasic--they will be saved to this directory:

$HOME/.olddos/

Therefore, the need to mount/automount is reduced.

If you are curious about where to put your .bas files, I would put them somewhere in here:

> $HOME/.olddos/
Maybe make a directory:
$HOME/.olddos/qbasic

**For further information try the following:**

Type this in the linux terminal:

> man dosbox

--- Read books on QBasic
--- Visit the dosbox website: [http://www.dosbox.com/](http://www.dosbox.com/)
--- Read another tutorial about DOSBOX (recommended): [HOWTO: Auto mount a drive in DOSBOX](http://ubuntuforums.org/showthread.php?t=171970)

[COLOR="Red"]NOW YOU CAN HAVE GORILLAS THROW BANANAS AT EACH OTHER!!!![/COLOR]
[http://en.wikipedia.org/wiki/Gorillas_(computer_game)](http://en.wikipedia.org/wiki/Gorillas_(computer_game))
--> [http://qbasic.com/classic/c7.html](http://qbasic.com/classic/c7.html)

More QBASIC STUFF!

[http://qbasic.com/](http://qbasic.com/)

---

### Post by -grubby on 2008-07-07
> **Genecks said:**
> Call me stupid, but this doesn't work.
How exactly is archive manager going to open and install a .exe?

It isn't.. Dosbox does that

---

### Post by AlexAfinarul on 2008-09-05
Qbasic can be run on Ubuntu without Olddos or any additional software except for Dosbox. You just install Dosbox sudo aptitude install dosbox
and you can run qbasic in Dosbox as any other DOS program. With Alt+Enter you run it fullscreen. Alt+Enter to exit fullscreen. The .bas files that you create are simply saved on the same folder where qbasic is running (e. g. Desktop.
The .bas files can be compiled with the compiler Firstbas.exe (from another company) but it does not recognize a few Qbasic instructions.

---

### Post by fewt on 2008-09-06
> **gnarula said:**
> As a student of Class VIII, I regularly need to check my BASIC Programs on my computer. After having ubuntu installed I needed a gui dialect/interpreter/compiler for BASIC. In Windows, QBASIC did the job for me. I thought of emulating it with Wine at first but after no success i came across "dosbox" which emulates DOS environment.

So heres how to do it:

Open a terminal and type:

```
sudo apt-get install dosbox
```

This should install dosbox on your ubuntu desktop. Next type:

```
wget http://download.microsoft.com/download/win95upg/tool_s/1.0/w95/en-us/olddos.exe
```

Open your home directory and right-click the olddos.exe file. Open it with archive manager. Extract it to a new folder, I suggest QBasic.

Now in the terminal type:
```
dosbox
```

After "dosbox" opens type the following:

```
mount c /home/username/QBasic/
C:
QBASIC.EXE
```

Thats it! Now, U have QBasic running on ur Ubuntu Desktop. Similarly, one can install dos games.

Gaurav

cd into your home directory and start dosbox.

Use the command: 'config -writeconf .dosboxrc' to create a dosbox config file.

Once you have .dosboxrc you can add your mount and c: command to it at the bottom of the file, then whenever you start dosbox it will automatically put you in that directory.

---

### Post by ALIENDUDE5300 on 2009-02-06
I'm pretty sure that OLDDOS.exe contains an old version of QBASIC... I think the last release of QBASIC was version 7.1, here's a download link that I found for it: [http://members.lycos.co.uk/qbasicturkey/download/qb71.htm](http://members.lycos.co.uk/qbasicturkey/download/qb71.htm) EDIT: Also, how can I get DOSBOX into fullscreen?

---

### Post by Otto-C on 2009-02-19
Ubuntu 8.04.2 got the following:
bill@oldcity:~$ wget [http://download.microsoft.com/downlo...-us/olddos.exe](http://download.microsoft.com/downlo...-us/olddos.exe)
--15:52:00--  [http://download.microsoft.com/downlo...-us/olddos.exe](http://download.microsoft.com/downlo...-us/olddos.exe)
           => `olddos.exe'
Resolving download.microsoft.com... 68.142.101.85, 68.142.101.92
Connecting to download.microsoft.com|68.142.101.85|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:52:00 ERROR 404: Not Found.
bill@oldcity:~$

what next

re-did the wget command and file was downloaded.
Onward and upward.
tia
otto-c

---

### Post by Sam111111 on 2009-04-22
Just wondering - I've got this set up and it's all working [using the second post that has instructions], but I can't find my files to put into the program [my programs that I wrote in Notepad earlier, that is].  Where [or how] can I put my files to see them? Or do I have to set it up a different way?
[I know it's "$HOME/.olddos/", but I can't find it. I'll try making a directory.

*edit*
Nevermind ... got it working. Heh.

---

### Post by mathwizard44 on 2009-04-25
You can also try FreeBASIC. Its syntax can be made compatible with QBasic and it has a Linux version. The project is hosted on Sourceforge: [http://www.freebasic.net/](http://www.freebasic.net/)

---

### Post by Nerv68 on 2009-05-20
I've tried DOSBOX with QBasic and in my experience, it's very glitchy... Theres a program called dosemu that I think works alot better. I use it myself.
```
sudo apt-get install dosemu
```
Then right click on Qbasic.exe and "open with dosemu" :-D

---

### Post by Otto-C on 2010-01-28
Using Ubuntu 8.04 up to date.
How to get my qbasic.exe, qbasic.hlp and qbasic.ini programs
into my dosbox as they are not there doing a dir /p. Also how
to get my programs (.bas) into the dosbox.
tia
otto-c

---

### Post by km0r3 on 2010-03-07
> **Nerv68 said:**
> I've tried DOSBOX with QBasic and in my experience, it's very glitchy... Theres a program called dosemu that I think works alot better. I use it myself.
```
sudo apt-get install dosemu
```Then right click on Qbasic.exe and "open with dosemu" :-D
This is actually better in my opinion!

---

