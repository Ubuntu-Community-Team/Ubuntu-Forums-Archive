---
title: "Re: Exit code while using zenity --progress"
date: 2011-10-31
forum: Programming Talk
---

### Post by Zakhafr on 2011-10-31
And there are much more differences, you should read that: [https://wiki.ubuntu.com/DashAsBinSh/]("https://wiki.ubuntu.com/DashAsBinSh/")

As I have the same problem you submited on the 1st post, but don't want to lose compatibility with dash, I'm still figuring out how to solve that. They give a vague hint of a "messy" solution on the page I linked.

---

### Post by sisco311 on 2011-10-31
Please don't bump old threads.

Old thread here: [http://ubuntuforums.org/showthread.php?t=397778](http://ubuntuforums.org/showthread.php?t=397778)

---

### Post by sisco311 on 2011-10-31
Check out:
[http://mywiki.wooledge.org/Bashism?highlight=%28pipestatus%29](http://mywiki.wooledge.org/Bashism?highlight=%28pipestatus%29)
[http://shell.cfajohnson.com/cus-faq-2.html#Q11](http://shell.cfajohnson.com/cus-faq-2.html#Q11)
and
[http://pipestatus.sourceforge.net/](http://pipestatus.sourceforge.net/)

---

### Post by Zakhafr on 2011-10-31
Sorry for the misbehaviour! ](*,)

I'm used to the Ubuntu French forum where it is not considered "out of chart" as the default sort order would show the bumped posts first (they also don't have "archives").

And 1000 thanks for the very useful links, especially the first one that gives some very useful tricks when using a posix shell (dash).
I'll try that immediately on my command | zenity --progress thing to see if that solves the issue.

[Edit] [I]1st solution looked good (named pipes)
```
mkfifo fifo; command2 <fifo & command1 >fifo; echo $?
```
... but does NOT do what is required.
It returns the exit code of the first command of the pipe, that's OK, but not the one of the second command.
In fact, zenity being as command2, if you click "Cancel", this would simply kill the "reader" of the pipe, then the "writer" (your script) is stucked indefinitely.
So that is definitely not a good solution in trapping both an error condition, and the zenity cancel.
This solution is only good when you are 100% sure command2 won't fail, and want to get return code of command1.

I guess I'm stuck with writing the error exit code of the 1st command to a temp file (booh ugly) and test it after the whole pipe exits[/I]

---

