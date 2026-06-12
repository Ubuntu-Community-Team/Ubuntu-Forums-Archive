---
title: "python and sudo"
date: 2008-03-11
forum: Programming Talk
---

### Post by themusicwave on 2008-03-11
I am working on a small program in python that needs to be run as sudo to work correctly.

I was wondering, is there a way to hook into the sudo dialog that often pops up when I run apps?

It would be nice to pop it up right when the application starts if they aren't root.

Also, is there an easy way in python to tell if the user is root.  I seem to remember a file somewhere that did this, but the details elude me.

Thanks,

Jon

---

### Post by tseliot on 2008-03-11
> **themusicwave said:**
> I was wondering, is there a way to hook into the sudo dialog that often pops up when I run apps?
You can use either "gksudo" or "kdesu".

> **themusicwave said:**
> Also, is there an easy way in python to tell if the user is root.  I seem to remember a file somewhere that did this, but the details elude me.
you can try to open a file to which only root have write access.

[PHP]try:
    open('/var/log/Xorg.0.log', 'w')
except IOError:
    pass#the user doesn't have root permissions[/PHP]

or you can [check the user id]("http://docs.python.org/lib/os-procinfo.html"). It depends on what you're trying to do.

---

### Post by themusicwave on 2008-03-11
Thanks!

I got it work work, I wrote two functions isRoot and promptRoot so I can now see if the user is root and make the user root by poping up the dialog

import os

def isRoot(self):
        
        root = True
        try:
            open('/dev/core', 'r')
        except IOError:
            root = False
            
        return root
    
def promptRoot(self):
        root = True
        
        try:
            os.popen("gksudo cat /dev/core")
        except:
            root = False

Then I can simply do the following:

if not isRoot():
   root = promptRoot()
   if root:
      command
  else
      print "Could not become root"!

Thanks again for the help.

---

### Post by imdano on 2008-03-11
It's probably easier to just do
[php]
if os.getuid() != 0:  # uid is always 0 for root
    root = promptRoot()
else:
    root = True

if root:
    command
else:
    print "Could not become root"[/php]

---

### Post by themusicwave on 2008-03-12
I did play with the getuid method, but I never made the connection that root is always 0.

That would be a better solution since it will work even if the file isn't there.  Also, it is a bit cleaner.

Any thoughts on cleaning up promptRoot?

---

### Post by imdano on 2008-03-12
Usually the behavior (at least that I've observed, and use in my own code) when a program that needs root access determines it doesn't have it is tell the user that the program requires root to run properly, then exit.

---

### Post by themusicwave on 2008-03-12
Some programs do throw up the prompt though as well.

For instance Synaptic throws up the prompt right away.

To me it is much easier to throw up a prompt if the program has a GUI.  This way even if it is run by clicking an icon it will still work.

If the program immediately exits if it isn't root, then that forces the user to start it from the command line.  This isn't a difficult task by any means, but is a bit of an inconvenience.

The way I have it written, if the user runs it as root, they will not get the prompt.  If they don't then they will.  If they fail to gain root through the prompt then the program will notify them and exit.  It seems like a reasonable solution.

---

### Post by imdano on 2008-03-12
When I run synaptic without root it tells me I won't be able to appy any changes, but it will run anyway.  Running it from the System menu does bring up a prompt, but that's because it's calling "gksu synaptic".  I don't think programs normally try to elevate themselves to root.  You don't have to run from the console if you just make the .desktop file run the command "gksu yourprogram" instead of just "yourprogram".

---

### Post by themusicwave on 2008-03-12
Good point

I will have to think about that one, I am starting to agree with you....

Well at least now I know how to do it just for curiosity sake

---

