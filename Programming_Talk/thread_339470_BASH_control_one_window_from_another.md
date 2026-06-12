---
title: "BASH control one window from another?"
date: 2007-01-15
forum: Programming Talk
---

### Post by adamonline on 2007-01-15
Hi,

I don't really know what this would be called, so it's really hard to search for it.  I have a BASH script that will configure a game server, and then runs the server in a new terminal window.  What I'd like to do is send commands to the new window from the original window.  Is this possible?  How would it be done?

Thank you!

---

### Post by Tomosaur on 2007-01-15
I'm not sure I understand. Do you want:

A: To type commands into the newly created server window, and have them repeated in the original window (ie, just listening to the server input).

OR

B: To type commands into one terminal window and have them sent to the server, as if you typed them into the server window?

Either case should theoretically be possible.Case B would be the easiest, using a utility called 'xwit' (you should already have this installed. The drawback is that you need to know the window id of the server window, but this could be overcome fairly easily I reckon. the syntax you should use in your script is:
```

xwit -focus -id <window id here>
<command>

```
this would also just leave focus there in that window, rather than reverting it back to the first one. There may well be a better way to do this, but it's the first on the top of my head without actually programming anything.

Type 'man xwit' to read more about xwit.

---

### Post by adamonline on 2007-01-16
Thanks for the reply, Tomosaur.

Case B is what I'm trying to achieve.

xwit sounds quite promising!  I presume that the script will continue running through the xwit command, so hopefully I can just 'xwit' focus back to the original window.  And if I'm thinking about the right thing, I give the server window an ID when I open it.

I didn't have xwit on my system, so for the sake of future searchers, it was a simple **sudo apt-get install xwit**

Thanks again!

---

