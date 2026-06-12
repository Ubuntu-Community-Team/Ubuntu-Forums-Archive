---
title: "Executing Commands Through .py script INTO a terminal"
date: 2007-12-22
forum: Programming Talk
---

### Post by family on 2007-12-22
I have a Python script and I need to run a command in the terminal from inside it. For example, how would one os.system("apt-get install sudo") and have a terminal pop-up? Python-apt would be ideal if it worked;
```

import apt # it is installed, version 0.02
sudo = apt.CacheFile()['sudo']
sudo.markinstall([autoinstall==1])
# nothing works, tried many variations on this, lack of documentation is APPALLING

```
I have all of the deps for Python-apt too...

Then I tried the vte emulator. No go. Vimsh? No. Commands module? No.

I need my script to be "Run", not "Run in terminal" at startup because mainly 'newbies' will be using it and it has a GUI (which 'clashes' with a terminal according to them).

Please help... I need to _have a terminal open up when I issue os.system commands..._

---

### Post by Quikee on 2007-12-22
Look at "/usr/share/doc/python-apt/examples/inst.py". This is an example provided with python-apt.

---

### Post by family on 2007-12-22
Thanks man! I'll take a look! :)

---

### Post by family on 2007-12-22
Erm, I got it to work, I think;
here's some code and IDLE's output. Btw: a terminal still does not pop up :(.
```

import apt, sys, copy # time and os have already been imported next to the start of the script
       from apt.progress import InstallProgress
       class TextInstallProgress(InstallProgress):
               def __init__(self):
                       apt.progress.InstallProgress.__init__(self)
                       self.last = 0.0
               def updateInterface(self):
                       InstallProgress.updateInterface(self)
                       if self.last >= self.percent:
                               return
                       sys.stdout.write("\r[%s] %s\n" %(self.percent, self.status))
                       sys.stdout.flush()
                       self.last = self.percent
               def conffile(self,current,new):
                       print "conffile prompt: %s %s" % (current,new)
               def error(self, errorstr):
                       print "got dpkg error: '%s'" % errorstr
       cache = apt.Cache(apt.progress.OpTextProgress())
       fprogress = apt.progress.TextFetchProgress()
       iprogress = TextInstallProgress()
       pkg = cache["sudo"]
       pkg.markInstall() # "sudo.markInstall failed...

```
On the bright side, this method works! But who would do all of that when a simple os.system('cmd') works?

Any other suggestions? My script works if I can get my users to edit file permissions to make it executable, and run it in the terminal.... But no one reads the docs....

---

