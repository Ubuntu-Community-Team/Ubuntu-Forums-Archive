---
title: "How do I create a shortcut for an application with a ./run command?"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by Chandler Mike on 2008-08-02
I'm trying to create/add a shortcut to my panel, and the command to launch the file is "./run"...

But when I browse to it, all I get is the long filepath and can't figure out what I put at the end to make it launch the application.

Help!

Mike

---

### Post by wdaniels on 2008-08-02
The "." at the start of "./run" just makes the command relative to the current directory. So that needs to be replaced with the full path of the directory from which you normally run the command. If you don't normally add any parameters (after the "./run" command) then it doesn't need any. Just browsing to and selecting the "run" file as you did should produce the correct result in most cases.

---

### Post by Diabolis on 2008-08-02
You have two options, add the folder that contains your script to the PATH environment variable or use the full path like this: ./"full path"/run

---

### Post by Chandler Mike on 2008-08-02
> **Diabolis said:**
> You have two options, add the folder that contains your script to the PATH environment variable or use the full path like this: ./"full path"/run


Couldn't get that to work either.

I guess I should mention this does run in a command window...so what I need this shortcut to do is launch the command window, then load the /run file.

---

### Post by Diabolis on 2008-08-02
To be sure, I just made one like this:
```
/"full path"/script.sh
```

*deleted the dot*

---

### Post by Chandler Mike on 2008-08-03
> **Diabolis said:**
> To be sure, I just made one like this:
```
/"full path"/script.sh
```

*deleted the dot*

That didn't seem to work...

I just need a shortcut that launches a terminal and then loads a file

---

### Post by marshal_mellow on 2008-08-03
> **Chandler Mike said:**
> That didn't seem to work...

I just need a shortcut that launches a terminal and then loads a file

If you create a launcher isn't there a way to specify that it runs in a terminal?

---

### Post by Diabolis on 2008-08-03
Yes, the command is working as I posted it. The problem is that when you execute graphical applications, like gnome-terminal, inside a shell script you have to specify the display that you want to use. Otherwise, the command will be executed but it won't know where to be displayed.

example:
```
DISPLAY=:0 /"full path"/script.sh 
```

---

### Post by wdaniels on 2008-08-03
> **Chandler Mike said:**
> That didn't seem to work...

I just need a shortcut that launches a terminal and then loads a file

In that case try:

```
gnome-terminal -x /path/run
```

You can specify a display with the --display option if you need to.

---

### Post by Chandler Mike on 2008-08-03
> **wdaniels said:**
> In that case try:

```
gnome-terminal -x /path/run
```

You can specify a display with the --display option if you need to.

Damn, I just cannot get this to work. The Gnome terminal launches, but no script runs.

Here is what I have:

gnome-terminal -e tt++ /"home/mike/Two Towers/TT/run.tin"
or
gnome-terminal -x tt++ /"home/mike/Two Towers/TT/run.tin"

Neither work. If you run the "tt++...." part in a terminal that is already launched, then it works fine.

Ugh, sorry guys...I just don't get what I'm doing wrong.

---

### Post by Chandler Mike on 2008-08-03
> **Chandler Mike said:**
> Damn, I just cannot get this to work. The Gnome terminal launches, but no script runs.

Here is what I have:

gnome-terminal -e tt++ /"home/mike/Two Towers/TT/run.tin"
or
gnome-terminal -x tt++ /"home/mike/Two Towers/TT/run.tin"

Neither work. If you run the "tt++...." part in a terminal that is already launched, then it works fine.

Ugh, sorry guys...I just don't get what I'm doing wrong.

I can't even do:

gnome-terminal -x tt++

I tried to setup the launch button to run in Terminal, but that doesn't seem to work either.

---

### Post by wdaniels on 2008-08-03
> **Chandler Mike said:**
> Here is what I have:

gnome-terminal -e tt++ /"home/mike/Two Towers/TT/run.tin"
or
gnome-terminal -x tt++ /"home/mike/Two Towers/TT/run.tin"


You should double quote the whole path:

```
gnome-terminal -x tt++ "/home/mike/Two Towers/TT/run.tin"
```

---

### Post by wdaniels on 2008-08-03
> **Chandler Mike said:**
> I can't even do:

gnome-terminal -x tt++

Probably t++ just exits immediately if you don't give it a file, though I can't say I'm familiar with this program.

---

### Post by Diabolis on 2008-08-03
A long time ago I tried something like that with the terminal with no luck. So I sticked with shell scripts and the DISPLAY environment variable.

---

