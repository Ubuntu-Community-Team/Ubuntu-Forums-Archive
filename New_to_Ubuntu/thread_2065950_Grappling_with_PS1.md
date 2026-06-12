---
title: "Grappling with PS1"
date: 2012-10-03
forum: New to Ubuntu
---

### Post by Swiftie on 2012-10-03
Maiden post: I'm not new to Linux, but new to ubuntu (and new here). 

I have a logon on my friends Ubuntu server (in his garage). When I logon, my command prompt is:

$
So, if I try to see the content of PS1 it goes like this:
$ echo $PS1
$
$

So, how would I change PS1 so that I get (say) the present working directory before the "$ "?

Under other linuxes, I'd have used something like:
PS1="\W $ "

... but this just changes my prompt to "\W $ "

---

### Post by The Cog on 2012-10-03
I think you may be using the **sh** shell rather than the **bash** shell. Try running bash as a subshell and setting PS1 in that.

---

### Post by Swiftie on 2012-10-03
> **The Cog said:**
> I think you may be using the **sh** shell rather than the **bash** shell. Try running bash as a subshell and setting PS1 in that.
Excellent suggestion; right first time, thank you. 

I'll email my friend and ask him to switch me to the bash shell. 

You've also answered my next two questions, which would have been:

1. Why doesn't the "Up arrow" key recall my commands?
2. Why is the "alias" command not recognised?

Do these forums support "This is the answer" marking?

---

### Post by The Cog on 2012-10-03
Oh, good.

There is an option to mark the thread as solved in **Thread Tools** near the top of the page.

---

