---
title: "Clear saved session"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Meetloaf13 on 2008-09-12
Hello,

I was toying with the session settings and I saved a session.

Every time I start up now it opens a couple file browsers and firefox, I would like to stop this from happening.  I unchecked the Automatically saved session thing (not that it would matter).

I also tried to remove the .gnome2/sessions/ folder as indicated in the thread below, but such folder did not exist.
[http://ubuntuforums.org/showthread.php?t=523906](http://ubuntuforums.org/showthread.php?t=523906)

Any clues?
Thanks!

---

### Post by Pro-reason on 2008-09-13
> **Meetloaf13 said:**
> Hello,

Every time I start up now it opens a couple file browsers and firefox, I would like to stop this from happening.  I unchecked the Automatically saved session thing (not that it would matter).

As well as unchecking that box, click on the “Remember Currently-Running Applications” button underneath it.  It will then save the current state.  Obviously, you should close down Firefox and suchlike first.

---

### Post by steve228 on 2009-11-03
I have the same problem.

I made sure and un-ticked the "Automatically remember running applications..." and every time I boot up, several instances of various programs appear...

I clicked the "Remember currently running applications" once, and now every time it does this... 

I haven't a clue how to resolve this... hopefully someone can help with this problem

---

### Post by Barriehie on 2009-11-03
When presented with the login screen, i.e. where it's waiting for your username press F10 and you should see session options.  Select one other than 'Last Session' and this will be your new session.

Barrie

---

### Post by steve228 on 2009-11-03
I found a workaround.  I typed it into the terminal, and it was a success. 

```

rm -R ~/.config/gnome-session/saved-session

```

---

### Post by Barriehie on 2009-11-03
> **steve228 said:**
> I found a workaround.  I typed it into the terminal, and it was a success. 

```

rm -R ~/.config/gnome-session/saved-session

```

Try the F10 thing!

Barrie

---

### Post by yamat on 2009-11-17
Hi,

Thanks for the tip.  I had the same problem.  I followed the instruction:

rm -R ~/.config/gnome-session/saved-session

and it worked.

Also, I think for good order, it also makes sense deleting:

rm -R /home/yannis/.config/session-state

which seems to be saving the state of various applications (e.g., Nautilus) so that they can be restored on every new session at the state they were during saving them.

Thanks.

---

### Post by steve228 on 2009-11-19
Your welcome. If it fixed your problem, go ahead and click 
Thread Tools -> Mark as Solved

So other people who have the same problem know that theres a solution in this thread.

---

### Post by yamat on 2009-11-26
OK thanks for the tip.
Have a nice day.

---

