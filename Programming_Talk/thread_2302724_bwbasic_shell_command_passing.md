---
title: "bwbasic shell command passing"
date: 2015-11-12
forum: Programming Talk
---

### Post by m-brooks on 2015-11-12
Apologies if there's a better location for this question - it's an awkward one to fit to the available categories. I chose a programming forum because bwbasic is a programming language (even if the precise question is not about that language per se) and the solution might involve programming (i.e. fixing or improving the bwbasic interpreter).

bwbasic has a really neat feature which is that from within the interpreter you may issue commands which if not recognised by the interpreter get treated as program invocations via the path. I can enter commands such as 'pwd' or 'ls -xF' and get the appropriate responses. So far so good.

However, if I enter 'cd bin' (when I do have a 'bin' subdirectory) and then 'pwd', I always find that I am still sitting in the same directory that I was in prior to issuing the 'cd' command. There is no error returned, whereas if I try to cd to a directory that doesn't exist I do get an error. My conclusion therefore is that the cd command is being successfully executed up to a point, but the pwd command doesn't see the result of this. I suspect that this is something to do with environments. As a wild stab in the dark I tried 'export PWD' but that didn't help.

Can anyone shine some light in this patch of darkness?

Regards,
Michael

---

### Post by spjackson on 2015-11-12
According to the docs for bwbasic, the command to change directory is CHDIR, so I guess that your 'cd bin' is being executed in a child process, and the child process cannot affect the current directory of its parent.

---

### Post by m-brooks on 2015-11-19
Thanks for that. Apologies for taking so long to respond - I expected the forum to notify me by email when someone replied but it never did and so I've only just found your reply.
I guess they created chdir precisely because there was no more elegant way to get around this issue.
Now to find the docs that you mention...

---

