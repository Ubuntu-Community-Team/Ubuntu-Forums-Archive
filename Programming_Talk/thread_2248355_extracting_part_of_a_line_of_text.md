---
title: "extracting part of a line of text"
date: 2014-10-14
forum: Programming Talk
---

### Post by GrouchyGaijin on 2014-10-14
Hello Programming Gurus,

I am a somewhat obsessive guy when it comes to remembering to do things and getting them done.
As such I have have todo.txt going into Conky so that I can see all of my todo list on the desktop.

I also use Remind and gxmessage to have pop up reminders of things I absolutely do not want to forget.

Example todo list: Below are tasks 4 and 5 of my current list
```

5 (B) +Cartus Presentation Draft III due:2014-10-15
4 (B) +Proofreading Start Therese Article 2 due:2014-10-14

```

I have been using a script to add items from my todo.txt file to my Reminders file (so they appear in the pop up message every few hours.)
```

#!/bin/bash
cat -n ~/Dropbox/todo/todo.txt
read -p "Enter the line number of the task to add to remind " task
sed -n "$task"p ~/Dropbox/todo/todo.txt
message=$(sed -n "$task"p ~/Dropbox/todo/todo.txt)
read -p "What is the trigger date of the reminder?:" triggerdate
read -p "How many days in advance should this appear? Default is 30." daysadvance
daysadvance=${daysadvance:-30}
read -p "What is the trigger time of the reminder?:" triggertime
echo "REM $triggerdate +$daysadvance AT $triggertime MSG $message %b (in [_countdown(trigdatetime()-current())])" >> ~/Reminder-files/reminders-general

```

This works except I would like to eliminate the priority(the letter B), project (+Cartus) and due date from the text that is extracted from the todo.txt file.
In other words, instead of:
```
(B) +Cartus Presentation Draft III due:2014-10-15
```
being added to the Reminders file I would like this to be added:
```
Presentation Draft III
```

---

### Post by Vaphell on 2014-10-14
```
$ echo "5 (B) +Cartus Presentation Draft III due:2014-10-15
4 (B) +Proofreading Start Therese Article 2 due:2014-10-14" | sed -nr "1s/.*[+]\w+ (.*) due:.*/\1/p"
Presentation Draft III
$ echo "5 (B) +Cartus Presentation Draft III due:2014-10-15
4 (B) +Proofreading Start Therese Article 2 due:2014-10-14" | sed -nr "2s/.*[+]\w+ (.*) due:.*/\1/p"
Start Therese Article 2
```

---

### Post by GrouchyGaijin on 2014-10-14
Thanks man, but I am slow.
How can I put your sed command into my script?
Basically, if I choose a task by the task number how do I invoke the sed on that choice?

---

### Post by Vaphell on 2014-10-14
the same way you do sed -n [COLOR="#0000CD"]N[/COLOR]p, but this time with [COLOR="#0000CD"]N[/COLOR]s/.../.../p

```
n=3
sed -n "${n} s/.../.../p" file
```

---

### Post by GrouchyGaijin on 2014-10-15
thanks man

---

