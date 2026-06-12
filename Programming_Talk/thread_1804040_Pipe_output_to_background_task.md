---
title: "Pipe output to background task"
date: 2011-07-14
forum: Programming Talk
---

### Post by Paddy Landau on 2011-07-14
I have been struggling to find out how to pipe output to a background task. (Maybe it's not possible, though that would surprise me.)

Using Zenity (which sits and waits for input) as an example, I've tried using pipes:
```
exec 7<&0  # Define fd 7
zenity --progress --auto-close --text='Startup up' <&7 &
echo 30 >&7
```I've tried using FIFOs:
```
mkfifo ~/zenpipe
zenity --progress --auto-close --text='Startup up' <~/zenpipe &
echo 30 >~/zenpipe
```(The FIFO doesn't work for the same reason that a file doesn't work; as soon as Zenity sees end-of-file, it assumes there is no more.)

I've tried a host of variations on these themes after lots of Googling. None of them works for one reason or another.

Is there any way to have a background task wait for input, which you can drip-feed to it?

---

### Post by PaulM1985 on 2011-07-14
Is the background task something you have written yourself?

How about having a file which contains the input and your background task watches the file to see if it has changed.  When the file changes, it reads in the commands you want to run.

Alternatively, you could have your program listening on a port, sort of like a server.  You connect to your program, pass it the information, disconnect.

Any of these ideas helpful?

Paul

---

### Post by Paddy Landau on 2011-07-14
Thanks for the ideas, Paul, but actually Zenity is the one I was most interested in.

However, I will take your ideas and see if I can make it work through some type of nested pipe. I'll post if I can figure it out. I was hoping for something simple, though.

---

### Post by Paddy Landau on 2011-07-14
Your ideas have helped me find a reasonable solution; not absolutely ideal, but it works and it's simple.

The idea is to create a file, then have *tail* pipe to Zenity.

```
#!/bin/bash

# Create a temporary file in RAM.
ZENFILE=$( mktemp --tmpdir=/dev/shm zenity-XXXXXXXXXX )

exec 7>${ZENFILE}            # Redirect fd 7 to the file.

# Start Zenity and pipe all redirected output to it as a background task.
tail --follow ${ZENFILE} | \
    zenity --progress --auto-close --title='Testing' --text='Starting up...' &

# Update Zenity...
sleep 2s
echo 33 >&7
echo '#One third done...' >&7
sleep 2s
echo 67 >&7
echo '#Two thirds done...' >&7
sleep 2s
echo 100 >&7                  # This closes Zenity and therefore the background task.

exec 7>&-                    # Close fd 7.
rm ${ZENFILE}                # Remove the temporary file.
```Thanks for the hints.

---

### Post by dethorpe on 2011-07-14
Just a thought, you might be able to use the bash coprocess to do this in a simpler way without the intermediate file:
 
[http://www.gnu.org/software/bash/manual/html_node/Coprocesses.html](http://www.gnu.org/software/bash/manual/html_node/Coprocesses.html)

---

### Post by Paddy Landau on 2011-07-14
Perfect! Here is my revised test script.
```
#!/bin/bash

# Start Zenity as a coprocess.
coproc zenity --progress --auto-close --title='Testing' --text='Starting up...'

# Update Zenity...
sleep 2s
echo 33 >&${COPROC[1]}
echo '#One third done...' >&${COPROC[1]}
sleep 2s
echo 67 >&${COPROC[1]}
echo '#Two thirds done...' >&${COPROC[1]}
sleep 2s
echo 100 >&${COPROC[1]}      # Close Zenity and therefore the background task.
```Thank you.

---

### Post by psusi on 2011-07-14
This also works:

{
bunch
of
commands
} | zenity

---

### Post by Paddy Landau on 2011-07-14
> **psusi said:**
> This also works:

{
bunch
of
commands
} | zenity
I'm aware of that. However, it becomes complicated if you want to be able to output to the terminal from "bunch of commands" (especially so if "bunch of commands" is large and spread over several functions). It's much easier if Zenity is run as a separate process.

---

### Post by psusi on 2011-07-14
> **Paddy Landau said:**
> I'm aware of that. However, it becomes complicated if you want to be able to output to the terminal from "bunch of commands" (especially so if "bunch of commands" is large and spread over several functions). It's much easier if Zenity is run as a separate process.

All programs are always run as separate processes.

If you want the stdout of most of the commands to go to zenity, then for the one you don't, you could redirect the output to stderr, or save the original stdout to another fd and redirect there.

---

### Post by Paddy Landau on 2011-07-14
> **psusi said:**
> All programs are always run as separate processes.

If you want the stdout of most of the commands to go to zenity, then for  the one you don't, you could redirect the output to stderr, or save the  original stdout to another fd and redirect there.
Indeed. However, the solution given by dethorpe is clean, simple, and easy to understand.  Redirecting most commands instead of only specific commands makes it  more complex.

---

### Post by Habitual on 2011-07-14
Paddy:

Nice work!

---

### Post by Paddy Landau on 2011-07-15
> **Habitual said:**
> Paddy:

Nice work!
Thanks; but I couldn't have done it without plenty of help. ;)

---

### Post by Habitual on 2011-07-15
I hear you, I recently started hitting yad (zenity fork) hard and the progress bar during a long function () was baking my banana good. 

I finally went to [http://www.unix.com/shell-programming-scripting/](http://www.unix.com/shell-programming-scripting/) and asked. Got a solution w\in 15m that worked.

I love this stuff.

---

### Post by Paddy Landau on 2011-07-16
@Habitual: Thanks for pointing out yad; I had not heard of it before. I will check it out (I see it has Debian packages). Zenity is good, but it lacks some useful features.

---

