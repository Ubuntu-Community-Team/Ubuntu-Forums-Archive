---
title: "[Python] Not Everything from STDERR/STDOUT Being Redirected"
date: 2011-12-09
forum: Programming Talk
---

### Post by dodle on 2011-12-09
I've got a class that redirects stdout/stderr to itself:

[php]class OutputLog(wx.TextCtrl):
    def __init__(self, parent, id=-1):
        wx.TextCtrl.__init__(self, parent, id, style=wx.TE_MULTILINE|wx.TE_READONLY)
        self.SetBackgroundColour(u'black')
        self.SetForegroundColour(u'white')
        self.stdout = sys.stdout
        self.stderr = sys.stderr
    
    def write(self, string):
        self.AppendText(string)
    
    def ToggleOutput(self, event=None):
        if (sys.stdout == self):
            sys.stdout = self.stdout
            sys.stderr = self.stderr
        else:
            sys.stdout = self
            sys.stdout = self[/php]

The problem is that not everything is redirected to it. It works when I use the "print" function, but not for system calls or errors.

Here is an example:
[php]...
    self.outputlog = OutputLog(self)
    self.outputlog.ToggleOutput() # Set stdout/stderr to print to log
...
  def PrintSomething(self, event=None):
    print 'Hello from Python'
    os.system('echo "Hello from system"')
    subprocess.Popen(['echo', 'Hello from subprocess'])
    print hello # Force a NameError[/php]

"Hello from Python" is printed in the output log, but "Hello from system", "Hello from subprocess" and the error traceback are printed in the system terminal. Is there a way to redirect all of this as well?

**----- EDIT -----**

I figured out how to manually do tracebacks, but it would be nice if all tracebacks were automatically sent to the OutputLog:

[php]...
    try:
      print hello
    except NameError:
      traceback.print_exc(file=sys.stdout) # Can also use "file=self.outputlog"[/php]

**----- EDIT -----**

Okay, figured out how to get it from os and subprocess modules, although once again it is not automatic, I have to put the output into a variable then print it:

[php]...
    o = os.popen('echo "Hello from system"').read()
    print o
    s = subprocess.Popen(['echo', 'Hello from subprocess'], stdout=subprocess.PIPE, stderr=subprocess.PIPE)
    print s.stdout.read()[/php]

I'm not going to mark this thread as solved for a couple of days in case someone has a better answer. Is there a way to redirect the output of [color=red]os.popen[/color] or [color=red]subprocess.Popen[/color] without having to put it into a variable?

---

### Post by StephenF on 2011-12-10
If you want to globally specify the IO streams you can do so at launch time or by writing a simple launch script.
```

$ python 2>&1 >myfile
Python 2.7.2 (default, Oct 24 2011, 11:20:40) 
[GCC 4.5.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import os
>>> os.system("echo hello")
>>> 
$ cat myfile
hello
0

```
The 0 is the return value from os.system which Python prints by default in interactive mode.

---

### Post by Bodsda on 2011-12-10
> **dodle said:**
> 
[php]...
    o = os.popen('echo "Hello from system"').read()
    print o[/php]

I'm not going to mark this thread as solved for a couple of days in case someone has a better answer. Is there a way to redirect the output of [COLOR=red]os.popen[/COLOR] or [COLOR=red]subprocess.Popen[/COLOR] without having to put it into a variable?

Your almost there, what happens if you don't do the variable assignment?

```

[COLOR=#000000][COLOR=#0000BB]print os[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]popen[/COLOR][COLOR=#007700]([/COLOR][COLOR=#DD0000]'echo "Hello from system"'[/COLOR][COLOR=#007700]).[/COLOR][COLOR=#0000BB]read[/COLOR][COLOR=#007700]()[/COLOR][/COLOR]

```

Bodsda

---

### Post by dodle on 2011-12-11
> **StephenF said:**
> If you want to globally specify the IO streams you can do so at launch time or by writing a simple launch script.

That's sounds pretty good, I'm going to look into that.

**@Bodsda**
I knew that I could use the print function without first putting the output into a variable, but I wanted it to go to stdout/stderr without having to call the print function at all.

---

