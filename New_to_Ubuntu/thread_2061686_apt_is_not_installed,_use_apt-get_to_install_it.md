---
title: "apt is not installed, use apt-get to install it??"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by doogsy on 2012-09-23
First off, I'm a casual user of Ubuntu. It's my main OS now, and I know a little bit of terminal commands, but happy just to learn as I go.
However, recently I have no longer been able to receive updates through ubuntu, and have a red 'no entry' sign in my top bar.
Clicking this gives me the following info:
"An error occured. Please run Package Manager from the right click menu or run apt-get in a terminal to see what is wrong. The error message was: 'Error: BrokenCouynt > 0'. This usually means that your installed packages have broken dependencies'
So the first thing I did was try to run the Package Manager. (Not sure what is meant by the right-click menu) Package Manager will not run.
So my next step was to run apt-get from the terminal. Here is what I get:

lee@lee-1015PE:~$ apt-get -f install
The program 'apt-get' is currently not installed.  You can install it by typing:
sudo apt-get install apt
lee@lee-1015PE:~$ sudo apt-get install apt
[sudo] password for lee: 
sudo: apt-get: command not found

I'm stumped, and searching for people who have similar problems is like searching for a pub called "AND" 
I know there has to be a simple fix, maybe downloading apt-get from another source and unpacking locally or something, but I just can;t find an answer.

My current version is 12.04 LTS and im on the netbook version.

---

### Post by jerrrys on 2012-09-23
Hi doogsy, welcome to the forums :)

I thought apt-get was default in all installs.  Where did you download this netbook version?

---

### Post by Mopar1973Man on 2012-09-23
Kinda seem odd that the application installer is missing... I was going to suggest that you might consider re-installing the entire OS again to see if it fixes it or maybe your source is corrupt?

---

### Post by cwsnyder on 2012-09-23
You might also try Synaptic if it is your Main menu > System folder, or again in the terminal```
sudo aptitude install apt-get
```which may work if aptitude is installed instead of apt-get.

I am surprised that even your update process worked if apt-get isn't installed.

---

### Post by doogsy on 2012-09-23
Thanks for the reply.
I've been using ubuntu since 10.04 or earlier, can't remember exactly but for more than a year. I have had no troubles since now, and I think this has happened during an update. It's been like this for a couple of months, but like I said, I'm only a casual user so haven't really bothered trying to fix it. But now I can't install anything...
So in summary, apt has always worked for me, and I've used it often, however, it is now broken.

---

### Post by MC_Claus on 2012-09-23
Perhaps it broke in an update. I have had that happening to me before.

Try downloading apt package from here [http://packages.ubuntu.com/precise/apt]("http://packages.ubuntu.com/precise/apt")

And install it by running ```
sudo dpkg -i <package-name>
```

---

### Post by doogsy on 2012-09-23
Yes, It seems like I might need to reinstall everything. 
@cwsnyder The update process no longer works since this problem arose

---

### Post by critin on 2012-09-23
> **doogsy said:**
> 
"An error occured. Please run Package Manager from the right click menu or run apt-get in a terminal to see what is wrong. The error message was: 'Error: BrokenCouynt > 0'. This usually means that your installed packages have broken dependencies'

So the first thing I did was try to run the Package Manager. (Not sure what is meant by the right-click menu) Package Manager will not run.




Right click menu is clicking the right side of the mouse instead of the usual left.  A  menu will pop up with actions listed.

---

