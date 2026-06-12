---
title: "Transfer skype history from Windows to Ubuntu?"
date: 2014-10-29
forum: New to Ubuntu
---

### Post by armid on 2014-10-29
How I can transfer skype history from Windows to Ubuntu? I tried to  copy main.db file from Windows to Ubuntu (/home/.Skype folder) but when I  run Skype, it's shutdown.

  I find this answer [Transfer Skype history from Windows to Ubuntu]("http://askubuntu.com/questions/410503/transfer-skype-history-from-windows-to-ubuntu")
  I just run sudo apt-get remove Skype, then I manual delete ~/home/.Skype folder. Then I run sudo apt-get install Skype. Then I copy Skype folder from Windows to ~/home/ folder, rename it.
  Run Skype. Skype runs, and shutdown at once

---

### Post by yancek on 2014-10-29
You might take a look at the link below.  I don't use skype so have no idea if this works.

[http://askubuntu.com/questions/410503/transfer-skype-history-from-windows-to-ubuntu](http://askubuntu.com/questions/410503/transfer-skype-history-from-windows-to-ubuntu)

---

### Post by armid on 2014-10-29
Yes, I saw this question, and I tried to do that steps. But after< Skype runs and shutdown at the same time .

---

### Post by Habitual on 2014-10-29
The linux flavor of Skyperious can import the main.db into your current db.
See [http://forums.linuxmint.com/viewtopic.php?f=47&t=175719&p=908954#p908954](http://forums.linuxmint.com/viewtopic.php?f=47&t=175719&p=908954#p908954) for the steps.

---

### Post by armid on 2014-10-30
Can anybody help me.

I do this steps

cd Downloads
wget [http://erki.lap.ee/downloads/skyperious/skyperious_3.2-src.zip](http://erki.lap.ee/downloads/skyperious/skyperious_3.2-src.zip)
unzip skyperious_3.2-src.zip
cd skyperious_3.2
sudo apt-get install wx2.8-i18n libwxgtk2.8-dev libgtk2.0-dev python-wxgtk2.8 python-wxtools  python-pip

Then I run

username@username-home:~/Downloads/skyperious_3.2$ python src/main.py
username@username-home:~/Downloads/skyperious_3.2$ 

But nothing doing. If I right understans should be open some tool which can help me

---

### Post by Habitual on 2014-10-30
> **armid said:**
> Can anybody help me.

I do this steps

cd Downloads
wget [http://erki.lap.ee/downloads/skyperious/skyperious_3.2-src.zip](http://erki.lap.ee/downloads/skyperious/skyperious_3.2-src.zip)
unzip skyperious_3.2-src.zip
cd skyperious_3.2
sudo apt-get install wx2.8-i18n libwxgtk2.8-dev libgtk2.0-dev python-wxgtk2.8 python-wxtools  python-pip

Then I run

username@username-home:~/Downloads/skyperious_3.2$ python src/main.py
username@username-home:~/Downloads/skyperious_3.2$ 

But nothing doing. If I right understans should be open some tool which can help me

Look in your notification area for the blue S icon.
Skyperious needs Python 2.7 or 2.6

run ```
python -V
```in terminal. What's the output?

You may also need to 
```
sudo apt-get install python-pyparsing
``` before running it.

I suggest reading the entirety of [http://forums.linuxmint.com/viewtopic.php?f=47&t=175719](http://forums.linuxmint.com/viewtopic.php?f=47&t=175719)

---

### Post by armid on 2014-10-31
> in terminal. What's the output?
Python 2.7.8

> sudo apt-get install python-pyparsing

done

> Look in your notification area for the blue S icon.

Do you meen this panel?

[IMG]https://dl.dropboxusercontent.com/u/16833006/Screenshot%20from%202014-10-31%2007%3A50%3A59.png[/IMG]

Ubuntu 14.10

---

### Post by Habitual on 2014-10-31
> **armid said:**
> Do you meen this panel?

[IMG]https://dl.dropboxusercontent.com/u/16833006/Screenshot%20from%202014-10-31%2007%3A50%3A59.png[/IMG]

Ubuntu 14.10

Uh, not exactly. I use Xfce4 so I am not sure where the indicator should show up on that desktop
here's what I have installed 
[ATTACH=CONFIG]257642[/ATTACH]

Have a look at ~/Downloads/skyperious_3.2/README.md
### Ubuntu/Debian ###

* run `sudo aptitude install wx2.8-i18n libwxgtk2.8-dev libgtk2.0-dev`
* run `sudo aptitude install python-wxgtk2.8 python-wxtools`
* run `sudo aptitude install python-pip`
* download and extract the Skyperious source
* open a terminal in the extracted directory
* run `sudo pip install -r requirements`

Launch skyperious.sh. <-- I get "bash: ./skyperious.sh: /bin/bash^M: bad interpreter: No such file or directory" on that one even though there are no ^Ms shown.
Nor did dos2unix on it help.
This did help...
vi skyperious.sh and in vi 
```
:set fileformat=unix
``` and ZZ to save and exit the file, then it runs fine.

Hope that helps.

---

### Post by armid on 2014-10-31
```
* run `sudo aptitude install wx2.8-i18n libwxgtk2.8-dev libgtk2.0-dev`
* run `sudo aptitude install python-wxgtk2.8 python-wxtools`
* run `sudo aptitude install python-pip`
* download and extract the Skyperious source
* open a terminal in the extracted directory
```

done

But then I can't launch skyperious.sh (maybe it launches but I can't found it)

------------------
I try to merge 2 database on Windows (skyperious also works on Windows). Merge was successful, but when I copy main.db to Ubuntu and run Skype, its crashed at once.

---

### Post by Habitual on 2014-10-31
yes, but did you also run ```
sudo pip install -r requirements
```?

Also. are the skype versions on both systems ***identical*** (down the the last .xx)?

---

### Post by armid on 2014-11-01
```
mipars@mipars-home:~$ cd Downloads/skyperious_3.2/
mipars@mipars-home:~/Downloads/skyperious_3.2$ sudo pip install -r requirements
[sudo] password for mipars: 
Could not open requirements file: [Errno 2] No such file or directory: 'requirements'
Storing debug log for failure in /home/mipars/.pip/pip.log
mipars@mipars-home:~/Downloads/skyperious_3.2$ ^C
mipars@mipars-home:~/Downloads/skyperious_3.2$ 

```

In this directory I have requirements.txt file but not requirements

If I modified command and run

sudo pip install -r requirements.txt

I receive

```
Downloading/unpacking PIL (from -r requirements.txt (line 1))
  Could not find any downloads that satisfy the requirement PIL (from -r requirements.txt (line 1))
  Some externally hosted files were ignored (use --allow-external PIL to allow).
Cleaning up...
No distributions at all found for PIL (from -r requirements.txt (line 1))
Storing debug log for failure in /home/mipars/.pip/pip.log
mipars@mipars-home:~/Downloads/skyperious_3.2$ 


```

---

### Post by Habitual on 2014-11-01
Then I don't know, sorry.

You could try copying your main.db from Linux to Windows and do the merge there?
Are they identical skype versions?

---

### Post by armid on 2014-11-01
Thank you for trying to help.

Linux 4.3.0.37
Windows 6.3

---

### Post by Habitual on 2014-11-01
> **armid said:**
> Thank you for trying to help.

Linux 4.3.0.37
Windows 6.3
skyperious can merge two main.db files via the command-line, but I haven't tried to do so from a c-line.

but the syntax seems to be:
python src/main.py merge FILE1 FILE2

So, as an exercise, let's try this:
Shutdown|Exit your Linux Skype.

Copy the Windows main.db to ~/Downloads/skyperious_3.2 and name it winmain.db
Copy the Linux main.db to ~/Downloads/skyperious_3.2 and name it linmain.db

in the ~/Downloads/skyperious_3.2 run
```
python src/main.py merge winmain.db linmain.db
```

New filename will be chosen automatically. so do an 
```
ls -al *.db
```  and look for the one **not named** *winmain.db* or *linmain.db* in the skyperious_3.2 directory.
Copy that new file to your ~/.Skype directory and name it main.db.
Fire up Skype. Look for signs of Windows chat history.

Please let us know.

---

### Post by Habitual on 2014-11-01
Just found this that may help you get a gui'fied version of the app shown on your desktop
```
python src/main.py gui
```

Hope that helps.

---

