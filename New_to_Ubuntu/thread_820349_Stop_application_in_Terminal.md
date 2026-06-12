---
title: "Stop application in Terminal"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by raedbenz on 2008-06-06
HI.,,
how can i stop an application when it run in terminal, what is the command??
for example here the cursor does not write:[ATTACH]73118[/ATTACH]

---

### Post by sayakb on 2008-06-06
Press Ctrl+C to kill the process.

---

### Post by YoG%*@ on 2008-06-06
> **raedbenz said:**
> HI.,,
how can i stop an application when it run in terminal, what is the command??
for example here the cursor does not write:[ATTACH]73118[/ATTACH]


hi,

try ctrl-c or ctrl-d.

hth,
mux

[edit] LinuxIsInnovation was faster... =) [/edit]

---

### Post by raedbenz on 2008-06-06
> **LinuxIsInnovation said:**
> Press Ctrl+C to kill the process.
hi 
non of them worked...

---

### Post by sayakb on 2008-06-06
How do you invoke this program? From a CLI? You need to be in the CLI itself to issue Ctrl+C.

---

### Post by raedbenz on 2008-06-06
> How do you invoke this program? From a CLI? You need to be in the CLI itself to issue Ctrl+C.
HI ..yea thats what i did..i am in the CLI

---

### Post by Rhubarb on 2008-06-06
You could just close the terminal window there.
Press the "X" in the top right hand corner.

---

### Post by raedbenz on 2008-06-06
> **Rhubarb said:**
> You could just close the terminal window there.
Press the "X" in the top right hand corner.

hi
lol, if i close the terminal some applications keep running in background.like minicom when if i close the terminal and renter it, and try to run it, i get error msg that application is locked.

any other solution?!

---

### Post by flyingmachete on 2008-06-06
Hi,

I'm a noob, myself, could this work?

open a terminal (applications > accessories) then:

sudo dmesg (will ask for your password)
run the offending program again,
should get a message saying another instance already running. should list the process number, copy the number

open another terminal and then

sudo kill *process number*

Hope this has been useful

---

### Post by sayakb on 2008-06-06
> **Rhubarb said:**
> You could just close the terminal window there.
Press the "X" in the top right hand corner.
LOL.. he's right.. Ctrl+C doesn't seem to work..

EDIT: Closing the terminal should kill the process after a short period.

---

### Post by hyper_ch on 2008-06-06
is this for a usb wifi device?

---

### Post by hyper_ch on 2008-06-06
```

ps aux | grep APPLICATONNAME

```

That will then pring the PID of all the stuff that's running as "APPLICATIONNAME" and you just need to kill then the according one:

```

kill PID

```

if you don't own the process then you must kill it with sude prepended.

---

### Post by Joshua Netterfield on 2008-06-06
> **raedbenz said:**
> HI.,,
how can i stop an application when it run in terminal, what is the command??
for example here the cursor does not write:[ATTACH]73118[/ATTACH]

If it's really stubborn, you could just close the window...
[ctrl] and [c], both at the same time should work.

If it dosn't work, a more annoying, but more foolproof thing to do is to press [ctrl] and [z] both at the same time, type "ps" (without quotes), find the name of the program which you think you were using, than type "killall -9 NameOfProgram" (without quotes; considering NameOfProgram is the program you were running). It's probably less troublesome to simply close the window though!

---

### Post by sayakb on 2008-06-06
I tried the program myself. Ctrl C/Z/D don't seem to respond.

---

### Post by beanhead on 2008-06-06
I be leave your looking for kill. here is the kill list of commands and what they do.


  Killing and Yanking
       kill-line (C-k)
              Kill the text from point to the end of the line.
       backward-kill-line (C-x Rubout)
              Kill backward to the beginning of the line.
       unix-line-discard (C-u)
              Kill  backward  from  point  to  the beginning of the line.  The
              killed text is saved on the kill-ring.
       kill-whole-line
              Kill all characters on the current line, no matter  where  point
              is.
       kill-word (M-d)
              Kill  from  point  to the end of the current word, or if between
              words, to the end of the next word.   Word  boundaries  are  the
              same as those used by forward-word.
       backward-kill-word (M-Rubout)
              Kill  the  word  behind  point.  Word boundaries are the same as
              those used by backward-word.
       unix-word-rubout (C-w)
              Kill the word behind point, using white space as a  word  bound-
              ary.  The killed text is saved on the kill-ring.
       unix-filename-rubout
              Kill  the  word  behind  point,  using white space and the slash
              character as the word boundaries.  The killed text is  saved  on
              the kill-ring.
       delete-horizontal-space (M-\)
--------------------------------------------------------------------------


If you would like to know more about the shell enter

info bash 

and scroll down with your arrow key, the kill commands are at the bottom.

Hope that helps.

---

### Post by raedbenz on 2008-06-06
> **flyingmachete said:**
> Hi,

I'm a noob, myself, could this work?

open a terminal (applications > accessories) then:

sudo dmesg (will ask for your password)
run the offending program again,
should get a message saying another instance already running. should list the process number, copy the number

open another terminal and then

sudo kill *process number*

Hope this has been useful
HI,,
if u have checked the picture at first thread, the cursor doesn't write on the terminal , i am looking for a method to re-activate the cursor and kill the running process.
i also did what u mention and i did not get this msg " saying another instance already running"
it just minicom started working properly but now i have two terminals opened.
thanks

---

### Post by raedbenz on 2008-06-06
> **beanhead said:**
> I be leave your looking for kill. here is the kill list of commands and what they do.


  Killing and Yanking
       kill-line (C-k)
              Kill the text from point to the end of the line.
       backward-kill-line (C-x Rubout)
              Kill backward to the beginning of the line.
       unix-line-discard (C-u)
              Kill  backward  from  point  to  the beginning of the line.  The
              killed text is saved on the kill-ring.
       kill-whole-line
              Kill all characters on the current line, no matter  where  point
              is.
       kill-word (M-d)
              Kill  from  point  to the end of the current word, or if between
              words, to the end of the next word.   Word  boundaries  are  the
              same as those used by forward-word.
       backward-kill-word (M-Rubout)
              Kill  the  word  behind  point.  Word boundaries are the same as
              those used by backward-word.
       unix-word-rubout (C-w)
              Kill the word behind point, using white space as a  word  bound-
              ary.  The killed text is saved on the kill-ring.
       unix-filename-rubout
              Kill  the  word  behind  point,  using white space and the slash
              character as the word boundaries.  The killed text is  saved  on
              the kill-ring.
       delete-horizontal-space (M-\)
--------------------------------------------------------------------------


If you would like to know more about the shell enter

info bash 

and scroll down with your arrow key, the kill commands are at the bottom.

Hope that helps.

Hi,,,
if u have checked the first thread then u will see that the cursor doesn't write on terminal (not active)

---

### Post by Joshua Netterfield on 2008-06-06
Okay.

Open up another terminal. Run
```
top
```
Find the application you wanted. Either remember the number (PID) or remember the command.

Close top by pressing "q".

If you remembered the number, run
```
kill -9 NUMBER
```
If you remembered the name, run
```
killall -9 NAME
```

That's a bit annoying, but it's all I can think of...

---

### Post by raedbenz on 2008-06-06
> **Joshua Netterfield said:**
> Okay.

Open up another terminal. Run
```
top
```
Find the application you wanted. Either remember the number (PID) or remember the command.

Close top by pressing "q".

If you remembered the number, run
```
kill -9 NUMBER
```
If you remembered the name, run
```
killall -9 NAME
```

That's a bit annoying, but it's all I can think of...
thanks..
this one worked

---

### Post by sayakb on 2008-06-06
> **raedbenz said:**
> thanks..
this one worked
You don't need to kill the process. After you have closed the terminal, the process will be killed automatically unless you launch it by:
```
minicom &
```

---

### Post by vicky.it.bhu on 2009-01-25
> **raedbenz said:**
> hi.,,
how can i stop an application when it run in terminal, what is the command??
For example here the cursor does not write:[attach]73118[/attach]

press  ctrl+z

---

### Post by mistypotato on 2009-02-05
> **Joshua Netterfield said:**
> Okay.

Open up another terminal. Run
```
top
```
Find the application you wanted. Either remember the number (PID) or remember the command.

Close top by pressing "q".

If you remembered the number, run
```
kill -9 NUMBER
```
If you remembered the name, run
```
killall -9 NAME
```

That's a bit annoying, but it's all I can think of...
[B]
This was the ONLY solution that worked for me.
A DEB package installer died during an install and wouldn't close.
This did the tric[/B]k.

---

### Post by KaisaUbun2 on 2012-08-22
> **raedbenz said:**
> hi 
non of them worked...

Pull up the program again in the terminal if it runs in the background. 
Open terminal and type 

```
sudo dmesg
```

then run the program again for instance 

```
sudo Conky
```

after it shows this process now push Ctr+C and it should have a witty message and say Bye! hope that helps

---

