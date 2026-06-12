---
title: "Require confirm dialog when closing terminal?"
date: 2015-02-04
forum: New to Ubuntu
---

### Post by ben5 on 2015-02-04
We use ubuntu in a call center and our interviewers keep Xing out of the terminal window when they should just be minimizing it.  Is there a way I can either disable the X (i.e. so one would have to type "exit" in the terminal to close it) or at least show a confirm dialog that requires clicking OK after clicking X to actually close the window?

FYI I am in the gnome fallback desktop... not unity. (Unity is too slow on our machines)

---

### Post by papibe on 2015-02-04
Hi ben5.

Happens to all of us.

My solution: use anything important inside GNU screen. [Here]("http://ubuntuforums.org/showthread.php?t=1957507&p=11839535#post11839535")'s an example of how to use it.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by ben5 on 2015-02-04
I don't have an ubuntu PC in front of me to try this right away.  Would this work for this scenario?

Basically they have a terminal window open and a browser window - they need to easily switch back and forth.  And I specifically use the terminal app and not putty because I need the links in the terminal window to be clickable. 

Also.. I have terminal set up with a login script so that as soon as it is opened it opens an ssh session to our server which opens a software there.  and when that session is closed it exits terminal (because I don't want the people sitting at a plain terminal prompt)

Do you think the screen solution could work for us?

---

### Post by sandyd on 2015-02-04
> **ben5 said:**
> I don't have an ubuntu PC in front of me to try this right away.  Would this work for this scenario?

Basically they have a terminal window open and a browser window - they need to easily switch back and forth.  And I specifically use the terminal app and not putty because I need the links in the terminal window to be clickable. 

Also.. I have terminal set up with a login script so that as soon as it is opened it opens an ssh session to our server which opens a software there.  and when that session is closed it exits terminal (because I don't want the people sitting at a plain terminal prompt)

Do you think the screen solution could work for us?

It depends on your setup.

Basically, the screen command allows you to run processes in the background.

What I *think* you want is to execute a screen session with a wrapper for your script on a terminal startup.

Something like
```

screen -mS worktesttest bash -c 'thisscripttoexecute'

```

This creates a screen called 'worktesttest' that your script (thisscripttoexecute) will execute in. On the end of the script, the screen will automatically close.

To resume the script after closing the window, use

```

screen -R worktesttest
```

I assume you can just do some flowchat logic similar to below
- On Opening terminal, check for existing screens. This can be done with
```

screen -ls
```
- If screen exists, resume screen
- If screen does not exist, create new screen

Side note: It is *required* that the script have something (i.e. user input, etc) that does not end in it exiting to bash. The screen session _will_ close itself once script exits. If you want to read the script output before exiting, there _must_ also be something that stops it from exiting at the end of the script. A bash read user prompt will be probably the easiest way.

---

