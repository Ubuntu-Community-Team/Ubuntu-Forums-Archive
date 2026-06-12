---
title: "having trouble updating IDLE"
date: 2009-07-29
forum: Programming Talk
---

### Post by punkbohemian on 2009-07-29
Recently, I decided to teach myself python. I have been using IDLE as my IDE. I like it because it's simple and straightforward, but still has a couple nice features (like text highlighting). I tried to update python to 2.6.2 (I know 3.1 is out there, but all my python books refer to 2.x), and I did the install, but for some reason IDLE still only registers 2.5.2. I followed the install instructions to the letter, with one exception. The instructions say:

> 
To start building right away (on UNIX): type "./configure" in the
current directory and when it finishes, type "make".  This creates an
executable "./python"; to install in /usr/local, first do "su root"
and then "make install".


For some reason, "su root" didn't work. I got an authentication failure, despite that fact that there's only one password for this computer, and I certainly haven't forgotten it. However, I did "sudo make install" instead, and that seemed to work fine. At least, it *looked* like it was installing.

Can anyone help me bring IDLE up to speed? Thanks.

Side question: I'm also looking for a dark theme for IDLE (i.e. black background, other colors changed to match). I started to manually tinker with the text highlighting options, but all I made was a mess of things. There are only two-built in themes under the configuration, and they both look pretty much the same. Is there a way to find/add more? Thanks.

---

### Post by stevescripts on 2009-07-29
rather than su root - on Ubuntu, type sudo make install 
you will then be prompted for the root password

---

### Post by punkbohemian on 2009-07-29
Yeah, that's what I did. But, when I boot up IDLE, it still references 2.5.2

---

### Post by stevescripts on 2009-07-29
sorry for the brainfart - I should have read the whole post before going off half-cocked ...

Can you post the output of "whereis python" ?

---

### Post by punkbohemian on 2009-07-29
```

pip@Linux-Box:~$ whereis python
python: /usr/bin/python2.5-config /usr/bin/python /usr/bin/python2.5 /etc/python /etc/python2.5 /usr/lib/python2.4 /usr/lib/python2.5 /usr/lib/python2.3 /usr/local/bin/python2.6 /usr/local/bin/python2.6-config /usr/local/bin/python /usr/local/lib/python2.6 /usr/local/lib/python2.5 /usr/include/python2.4 /usr/include/python2.4_d /usr/include/python2.5 /usr/include/python2.5_d /usr/share/python /usr/share/man/man1/python.1.gz
pip@Linux-Box:~$ whereis idle
idle: /usr/bin/idle /usr/local/bin/idle /usr/share/man/man1/idle.1.gz

```

I also posted the output of "whereis idle" since I bet you'd want to know that, too.

---

### Post by punkbohemian on 2009-07-30
*bump*

---

### Post by punkbohemian on 2009-07-31
*bump*

---

### Post by .Maleficus. on 2009-07-31
'/usr/bin/python' is a symlink to '/usr/bin/python2.5'.  If you type 'python' at the command line, you'll probably notice it is still coming up as 'Python 2.5.x' or similar.  Change the symlink '/usr/bin/python' to reference '/usr/local/bin/python2.6' using this:
```
sudo ln -s /usr/bin/python /usr/local/bin/python2.6
```
And then give it a try.

---

### Post by punkbohemian on 2009-07-31
Tried it and got:

```

ln: creating symbolic link `/usr/local/bin/python2.6': File exists

```

Idle is still referencing 2.5.2.

---

### Post by .Maleficus. on 2009-07-31
Heh, I'm on Windows right now so I probably got the order of the files mixed up.  Try switching the two paths around.


Edit:  I forgot to mention, you'll have to delete /usr/bin/python first.

---

### Post by punkbohemian on 2009-07-31
Well, that did something, but I don't know what.

I switched the paths like you said and now IDLE won't start at all. A taskbar item that says "Starting IDLE..." pops up, but then it just disappears.

Additionally, the "Add/Remove Programs" won't start anymore either.

---

### Post by .Maleficus. on 2009-07-31
> **punkbohemian said:**
> Well, that did something, but I don't know what.

I switched the paths like you said and now IDLE won't start at all. A taskbar item that says "Starting IDLE..." pops up, but then it just disappears.

Additionally, the "Add/Remove Programs" won't start anymore either.
That's what I was afraid of.  I'm an Arch user and all our Python programs depend on 2.6, and I guess Ubuntu still depends heavily on 2.5.  You can switch it back by doing replacing /usr/local/bin/python2.6 with /usr/bin/python2.5 in the command I gave you.  I don't have any other ideas unfortunately.

---

### Post by punkbohemian on 2009-07-31
I tried both commands you suggested (and checked IDLE/"Add/Remove Programs" after each), neither of them restored my settings:

```

pip@Linux-Box:~$ sudo ln -s /usr/bin/python /usr/local/bin/python2.5
[sudo] password for pip: 
pip@Linux-Box:~$ sudo ln -s /usr/local/bin/python2.5 /usr/bin/python
ln: creating symbolic link `/usr/bin/python': File exists
pip@Linux-Box:~$ 

```

---

### Post by .Maleficus. on 2009-07-31
Delete '/usr/bin/python'.  Enter 'sudo ln -s /usr/bin/python2.5 /usr/bin/python'.
```
sudo rm /usr/bin/python
sudo ln -s /usr/bin/python2.5 /usr/bin/python
```
  Enter 'ls -l /usr/bin/python'.  The output should look like this:
```
ls -l /usr/bin/python
lrwxrwxrwx 1 root root 24 2009-07-31 07:13 /usr/bin/python -> /usr/bin/python2.5
```
If that is the case, everything should be back to normal.

---

### Post by punkbohemian on 2009-07-31
everything is not back to normal. for some reason it's still referencing 2.6

```

pip@Linux-Box:~$ sudo rm usr/bin/python
[sudo] password for pip: 
rm: cannot remove `usr/bin/python': No such file or directory
pip@Linux-Box:~$ sudo ln -s /usr/bin/python2.5 /usr/bin/python
ln: creating symbolic link `/usr/bin/python': File exists
pip@Linux-Box:~$ ls -l /usr/bin/python
lrwxrwxrwx 1 root root 24 2009-07-31 11:22 /usr/bin/python -> /usr/local/bin/python2.6
pip@Linux-Box:~$ 

```

---

### Post by .Maleficus. on 2009-07-31
Take a look at the output you posted, and read very carefully.  Redo the commands and instead of typing them out, copy/paste them.  That's why I put them in the [code] boxes.


[size=1]Here's a hint:  `usr/bin/python': No such file or directory - you forgot the / in /usr[/size]

---

### Post by punkbohemian on 2009-07-31
It looks like I'm back in (outdated python) business. Thanks for the help. :)

---

### Post by .Maleficus. on 2009-07-31
> **punkbohemian said:**
> It looks like I'm back in (outdated python) business. Thanks for the help. :)
No problem.  Sorry it didn't work out for you.  Is there a particular thing you need 2.6 for?  It was really only released to help transition to 3.x so there aren't any real changes...

---

### Post by punkbohemian on 2009-07-31
I've been teaching myself python and chatting with folks on the boards/IRC from python.org. A bunch of people said I should update to at least 2.6, if not 3.x, and I opted for 2.6 because all my python books reference 2.x. I figured I'd switch to 3.x down the line once I got more comfortable with the language, but I guess that won't be happening unless Ubuntu catches up, too.

---

