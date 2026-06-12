---
title: "background jobs as part of another job"
date: 2009-07-30
forum: Programming Talk
---

### Post by flylehe on 2009-07-30
Hi,
In a bash script there are several background jobs. When running this script in a shell, how to control those background jobs? i.e. suspend, resume, type "jobs" to get info...
I tried but it doesn't work as I paste the content of the script into the shell and run it. Why?
Thanks and regards!

---

### Post by Dill on 2009-07-30
For controlling background jobs, [this]("http://web.mit.edu/gnu/doc/html/features_5.html") might help.

I'm not sure I quite understand the second part of your question. Are you trying to copy some code you wrote and paste it here or paste something from the web into the Terminal?

To copy something *from* the shell, try *Ctrl+Shift+C*; to paste something *into* a terminal, try *Ctrl+Shift+V*.

... or did you mean something else entirely?

Cheers,
Dill

---

### Post by flylehe on 2009-07-30
Sorry I didn't describe my question clearly. I mean:
I have a bash script whose content is calling several jobs in background.
If I paste the content of the script into the shell and run it, then I can use the job control commands to play with the background jobs in the content.
But if I run the background jobs by running the bash script in the shell, I cannot control the jobs in the shell directly. In this case, how to?

---

