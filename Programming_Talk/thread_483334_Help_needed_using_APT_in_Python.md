---
title: "Help needed using APT in Python"
date: 2007-06-24
forum: Programming Talk
---

### Post by Warbo on 2007-06-24
Hi, I'm making a tool in Python which involves package management but since I'm not too experienced with it I am having a problem.

I have a set of package names called totalIncludes which need to be downloaded so I'm using apt-get (and postpone which is available here: [http://www.df7cb.de/projects/postpone/](http://www.df7cb.de/projects/postpone/) ). Problem is, I can't get the program to wait until all of the apt-gets have completely finished, it either carries straight on with apt-get still running or gets stuck in an infinite loop. Here's the code I'm using:

def downloadPackages():
[INDENT]global totalIncludes
aptCommand ='postpone --debian apt-get --reinstall --force-yes -dy install '
# FIXME: This could be more optimal
for current in totalIncludes:
[INDENT]out = os.popen(aptCommand + current, 'r')[/INDENT]
waiting = os.popen('postpone --wait /var/cache/apt/archives/lock echo 1', 'r')
while not ('1' in waiting):
[INDENT]print '.'[/INDENT][/INDENT]

downloadPackages = staticmethod(downloadPackages)

This currently gets stuck printing dots forever :( (I tried using a single apt-get line for everything, but the number of packages could easily be too big for a single sh command)

I have been working on this app for weeks and it is almost completely working now, but I just can't work out how to get past this part. Any suggestions would be appreciated, since I really want to give back more to the Free Software community that has given me so much, but I don't want to give back a broken app.

Thanks in advance

---

### Post by pmasiar on 2007-06-24
sure it will get stuck - IIUC 'waiting' has no reason to change. :-)

doc recommenrs to use subprocess - [http://docs.python.org/lib/module-subprocess.html](http://docs.python.org/lib/module-subprocess.html) - but why doing it in so complicated way? Why not just issue synchronized commands, and wait till each one ends?

[http://docs.python.org/lib/node537.html](http://docs.python.org/lib/node537.html)

Do simplest thing which will work first, and optimize when you know what you doing and when you need it.

---

