---
title: "Using bash commands to do a operation dependant file copy?"
date: 2010-06-30
forum: Programming Talk
---

### Post by BastardNamban on 2010-06-30
I just recently learned what bash commands are- I'd been using some before I realized they had a name.

I have a common problem- I am copying large amounts of files (~70 GB) to a new 10.04 install for my younger brother. I was just wondering, is there a way to "schedule" the copy of a folder to a specific location- and have it be time dependent on when a current file copy operation ends? That way, it would copy when one finishes- in the middle of the night, and finish while I sleep.

I'm sure everyone must be doing this, but I can't figure out how- I'm really, really green with bash commands- I've used linux for a few years now, but not much in terminal.

I figure "-n" or "watch" commands might be involved. Any ideas? Thanks if you can assist a total newb to this stuff, I'm reading guides on bash, but I don't see anything about this kind of operation.

---

### Post by trent.josephsen on 2010-06-30
```
cp -a /my/file /some/destination1; cp -a /my/folder /some/destination2
```
will run the second copy only after the first completes, but if you're copying multiple files to the same location you can copy them all at once; i.e.
```
cp -a /my/file /some/destination; cp -a /my/folder /some/destination
```
is the same as the following:
```
cp -a /my/file /my/folder /some/destination
```

Handy tip:  If you're copying large amounts of data from one filesystem to another (e.g. from your regular hard drive to a backup disk), keep in mind that you can **cp** an entire directory tree at once and then rearrange the contents in a matter of seconds once it's on the secondary filesystem, even if the initial copy took hours to complete.  That's because when you use **mv** to move files or directories within a filesystem, all you need to do is edit the file metadata; no copying of the file contents is necessary.  (When you use **mv** to move a file from one filesystem to another, it's actually a copy-then-delete method.)  Not sure if this makes sense, but it's true (unless you're using some exotic or very stupid file system).

---

### Post by dwhitney67 on 2010-06-30
Use the "at" command.  For example:
```

echo "scp -r SomeFolder brother@remotehost:" | at 01:15 

```
This command will recursively secure-copy the folder with the name 'SomeFolder' to the home-folder of user 'brother' at the remote system identified as 'remotehost', beginning at 1:15am.

You can verify the "at" jobs using the command "atq", and if something is not to your liking, you can remove a job using "atrm <jobid>".

---

### Post by BastardNamban on 2010-06-30
I may have been unclear-

I'm copying different folders from an external drive to the same location- the desktop. The folders are not the same thing. I am doing one at a time because it goes quicker not overloading the computer, or so I thought- in any case, one operation is 3 hours in, so I can't go back.

I want to schedule the final folder, different from what I am currently copying now, when the current copy operation ends, to copy to the same location- the desktop.

Does that help?

> is the same as the following:
```
cp -a /my/file /my/folder /some/destination
```

Handy tip:  If you're copying large amounts of data from one filesystem to another (e.g. from your regular hard drive to a backup disk), keep in mind that you can **cp** an entire directory tree at once and then rearrange the contents in a matter of seconds once it's on the secondary filesystem, even if the initial copy took hours to complete.  That's because when you use **mv** to move files or directories within a filesystem, all you need to do is edit the file metadata; no copying of the file contents is necessary.  (When you use **mv** to move a file from one filesystem to another, it's actually a copy-then-delete method.)  Not sure if this makes sense, but it's true (unless you're using some exotic or very stupid file system).


I do already know that, that's ok, you didn't know I knew, once on another drive you can organize it quickly. But is that> -a a quantifier that does the operation when all running ones end?

[U]
dwhitney[/U]- I don't want a specific named time to start the operation- I want to start the second copy to start when the first one ends- I don't know the exact time it will complete. Is there a way to do that?

It says, ie: "3 hours 10 secs remaining", but it may actually take longer (maybe I open something else that bogs down the processor, so it takes longer and I don't notice, et al) so I just want the second thing to start as defined by the actual end of the first operation- have the computer start the second thing whenever the first thing ends, be it by my canceling, an error, or accidental operation, whatever.


To both: I get that I could run it all together- but in this case, I already started a long operation that's quite a bit through. I don't want to cancel it, or be awake and here to do the second copy whenever the first thing ends. THAT's the problem- I want to schedule something with an arbitrary start time- whenever something else happens, in this case, when the first operation ends. Not at a specific named time like 1:30 am, as I may not always know when something will finish.

I know I probably overexplained that.

---

### Post by BastardNamban on 2010-07-01
I apologize if I over-explained myself, or if you guys understood and I just didn't understand you- but I give up for now.

I will check back tomorrow morning- I gotta get some sleep. I'll just que the next copy tomorrow, probably after the other one will have finished as I slept.

It will be good to know your answers for future use though. Now that I know the "code" is called bash, I'm going to master it! I'll find everything I can on bash and learn how to use the terminal more. I think it would help me do more in the long run.

Thanks for any more help, goodnight.

---

### Post by soltanis on 2010-07-01
Welcome to the world of awesome: "whoa you mean my shell is a programming language?! whaaat"

If you've already started the first cp command and you want to run your next command after it finishes, how about this?

```

cmd="cp /path/to/files/* ."
while [ true ]; do
    pgrep cp &> /dev/null
    if [ $? -ne 0 ]; then
        $cmd
        break
    fi
    sleep 60
done

```

Replace the text after the = sign in the "'s with the appropriate cp command. Whitespace is important (unlike in many other languages); there needs to be no whitespace between the cmd and the = sign, and there has to be spaces between the ['s and the ]'s (it has to do with how the shell parses commands).

Basically what that will do is loop until it sees that there are no processes with the name "cp" running on the system, then will run cmd and then exit the loop; otherwise it will wait one minute and then run again.

Other solution is to schedule the command using at.

Other solution is also wake up tomorrow and run the command yourself, especially because I haven't actually tested this code (hopefully it won't run you in an infinite loop, but if it does, a good Ctrl-C will stop it).

---

