---
title: "Instant Messenger in Bash"
date: 2011-08-11
forum: Programming Talk
---

### Post by RobbyHawkes on 2011-08-11
Just for fun I tried to make an instant messenger in bash. It works, after a fashion..it's very simple, users just ssh into a server and run the script from there.

The problem may be fundamental to bash itself, but it's more than likely that I don't know what I'm doing. The program works by appending new messages (plus a handle and timestamp) to a file, which it scans every whatever-fraction-of-a-second to see if it's changed. If it has, the script echos the difference between that file and a duplicate made after the previous scan scan to stdout. In a nutshell.

The problem is that in bash anything entered at the command line is displayed on the screen, meaning your own messages are duplicated. I know this could be done more easily in almost any other programming language, but where's the fun in that? ;)

Does anyone have a way around that? I'm prepared to post the code, but it's not well commented and is probably still a buggy mess..

Thanks in advance.

Rob

---

### Post by cgroza on 2011-08-11
Why don't you redirect the unwanted output to /dev/null?

---

### Post by RobbyHawkes on 2011-08-11
Hi, cgroza,

Thanks for your reply.

I did try that,  but didn't have any luck..probably because I don't really understand how. 

How would one redirect stdin from a 'read' to /dev/null?

---

### Post by hakermania on 2011-08-11
My guess is: use grep -v "Your entered text here" to prevent your entered text to be displayed
For example, if you use this command to display the differences:
```

diff file1 file2

```
use this to prevent showing the duplicate:
```

diff file1 file2 | grep -v "Entered text"

```

Im not sure how's your application working but I think this is gonna work!

---

