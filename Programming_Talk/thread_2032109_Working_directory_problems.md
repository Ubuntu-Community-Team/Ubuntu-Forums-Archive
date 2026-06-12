---
title: "Working directory problems"
date: 2012-07-23
forum: Programming Talk
---

### Post by Aleksandar222 on 2012-07-23
I have a problem with working directories.
This is the script I use to start my application.

```
[INDENT]export LD_LIBRARY_PATH=/opt/ewns-viewer
export GSETTINGS_SCHEMA_DIR=/opt/ewns-viewer 
/opt/ewns-viewer/ewns-viewer
[/INDENT]
```

When I start it using start in terminal from the alert box, everything goes fine.
But I when I start it without the terminal my program fails to work because 
PWD equals HOME.
I am using the .desktop file with terminal set to true and it works,with terminal set to false it fails.The .desktop file calls the run script.

I am using Posix.chdir before I do the work in some directory (That is what works when run script called with terminal)

---

### Post by Bachstelze on 2012-07-23
Just put a cd command at the top of your script?

---

### Post by Aleksandar222 on 2012-07-23
The catch is that the directory the stuff will be done in is selected inside the program and then chdir is called and things are done.
That works fine when the run script is called from terminal.
But it does not go wel when running it without terminal.

---

### Post by spjackson on 2012-07-23
> **Aleksandar222 said:**
> The catch is that the directory the stuff will be done in is selected inside the program and then chdir is called and things are done.
That works fine when the run script is called from terminal.
But it does not go wel when running it without terminal.
It's a bit hard to guess what's going wrong inside your program without some code. Maybe you are using a relative path that doesn't resolve. What error code does your chdir call return? If you were using C, I'd ask about errno, but I've no idea what language you are using.

---

### Post by trent.josephsen on 2012-07-23
I'm not sure why starting in the terminal or not should have an effect on $PWD or $HOME. I'm using XFCE so maybe that's a factor, but those don't seem to change no matter what options I alter.

In any case, your program is fragile, and it's not the .desktop file that needs fixing. I looked at your program code and noticed this:

```
      Environment.set_variable("PWD",DIRECTORY,true);
```

I don't know anything about Vala, but I don't see where you're spawning any new threads or processes, so I don't see why you should want to do that... but the lack of comments and inconsistent indentation deterred me from pursuing that line of inquiry.

I also noticed that there's no shebang line in your run script. What interpreter should run it?

---

### Post by trent.josephsen on 2012-07-23
> **spjackson said:**
> It's a bit hard to guess what's going wrong inside your program without some code. Maybe you are using a relative path that doesn't resolve. What error code does your chdir call return? If you were using C, I'd ask about errno, but I've no idea what language you are using.
Google turned up [http://bazaar.launchpad.net/~ajovanov93/ewns-viewer/trunk/files/125](http://bazaar.launchpad.net/~ajovanov93/ewns-viewer/trunk/files/125), which is what I was commenting on

---

