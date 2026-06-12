---
title: "Question concerning processes, execl, wait, and pthreads"
date: 2007-11-13
forum: Programming Talk
---

### Post by derrick81787 on 2007-11-13
I'm working in C on a gtk+ interface for the dvd ripping program, HandBrake.  My program is either going to consist of 3 processes (1 for the GUI, 1 to execute the command line backend, and 1 one monitor the ripping progress and relay it back to the GUI) or it will use pthreads.  I would really like to use pthreads, considering that they are more efficient with resources and also make communicating much easier.

My problem is that the command line backend that actually rips the dvd is it's own separate binary, and the only way I know of to execute it and detect when it is finished is to fork(), execl(), and then wait().

I'm wondering if anyone knows what will happen if I call wait() from a thread.  I would hope that only the calling thread would block, but my fear is that it would block the entire process.  I'm also wondering if there is a pthread equivalent of execl() that is designed to be used with threads, because if there is, that would be great.  I've googled all over, though, and I am yet to find the answer to either of these questions.

Anyway, thanks for the help, and any responses are greatly appreciated.

- Derrick

---

### Post by slavik on 2007-11-13
a thread is not a process.
exec says (replace me with this program).

What you can do though, if you are the one writing the ripping backend is isolate it into a single function (not main) and simply have 2 versions of it, 1 as a CLI version and another with the GUI code.

---

### Post by derrick81787 on 2007-11-13
> **slavik said:**
> a thread is not a process.
exec says (replace me with this program).

I understand that. I may have worded the original question badly, but what I meant was that I would like to use pthreads instead of separate processes so that I can share global variables and such. I figured that I would probably need to use another process in order to run the backend program, but I was wondering if it would be possible to use threads for the GUI and the monitoring thread.

> **slavik said:**
> What you can do though, if you are the one writing the ripping backend is isolate it into a single function (not main) and simply have 2 versions of it, 1 as a CLI version and another with the GUI code..

Actually, that's a really good idea.  I don't know why I didn't think of that.  I didn't write the backend, but I do have access to the source code.  I was going to try to use the code, but the problem I had was that the code is extremely complicated, and I thought that I'd be unable to understand it in the amount of time I have to write the code (It started as a personal project, but is now a school project with a due date). Using the method you suggested, I would really only have to call the function and not worry so much how it works.  Thanks a lot for the help.

- Derrick

---

### Post by slavik on 2007-11-13
the only problem when trying to monitor another program happens when the other program is not outputting anything.

imagine running find ... it does not output its progress, although you could probably infer it based on the directory/file it is processing (if it does so in alphabetical order).

now imagine apt-get install or wget ... both output progress which could be captured and processed.

---

### Post by derrick81787 on 2007-11-13
The other program does print a text based progress bar to stdout, along with the speed it is writing, and the current file size.  The only challenge involving that would be how to read its output from stdout, but that doesn't seem like it would be too difficult, once I put a little thought into it.  I imagine I could probably just redirect its output to a file and then read from the correct place in that file (or something like that). There may be a better solution, so I'll just have to look into how everything works and see what I can come up with.  I really appreciate the help.

---

### Post by slavik on 2007-11-13
try running it with redirecting the output to a file, I found that wget prints a whole new line of the progress bar once it is updated ...

---

### Post by derrick81787 on 2007-11-13
> **slavik said:**
> try running it with redirecting the output to a file, I found that wget prints a whole new line of the progress bar once it is updated ...

Great! I have a ton of homework I have to do for school, but later this week (probably Thursday or so) I'll try it and let you know how it goes.  Thanks for all your help.

---

