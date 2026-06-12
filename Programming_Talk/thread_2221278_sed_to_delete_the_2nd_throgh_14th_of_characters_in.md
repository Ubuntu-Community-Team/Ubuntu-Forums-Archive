---
title: "sed to delete the 2nd throgh 14th of characters in a line"
date: 2014-05-01
forum: Programming Talk
---

### Post by GrouchyGaijin on 2014-05-01
Hi Gurus,

I was wondering how I could use sed. or another command if it is better suited for the task, to delete a range of characters from each line in a file.

Specifically I am using todo.txt to keep a list of todo items that I display in conky.
I have a script that will take an item from my todo.txt file and copy it in remind format into my reminders file, so I get a popup reminding me to do the task.

Right now the todo2remind script is grabbing the entire todo item.

Example:
```

1 2014-06-01* (E) +conputer Fix Mutt's spell check



```

What I would like is to have only the actual message grabbed. Since I need to know the line number, in this case 1, I'd like to remove the 2014-06-01* (E) (this is different in every line, but the position is the same)
which would leave:
```

+conputer Fix Mutt's spell check

```

Even better would be to get rid of the plus sign and the word that comes directly after it as well (+computer, in this case).

---

### Post by Vaphell on 2014-05-01
```
$ echo "1 2014-06-01* (E) +conputer Fix Mutt's spell check" | sed 's/[0-9*-]*\s*([A-E])\s*+\w*\s*//'
1 Fix Mutt's spell check
```

---

### Post by GrouchyGaijin on 2014-05-01
Thanks man!
How can I save the output as a variable to use elsewhere?
I thought I knew, but keep getting errors.
I mean the:
```
Fix Mutt's spell check 
```
[COLOR=#000000][FONT=Ubuntu Mono]
After looking at what I am trying to do, I realized that I don't need to keep the line number after all.


[/FONT][/COLOR]

---

### Post by Vaphell on 2014-05-01
capture the output with $()

```
stuff=$( sed 's/.*([A-E])\s*+\w*\s*//' file )
```

but do you really need to store it? what's it for exactly?

---

### Post by GrouchyGaijin on 2014-05-01
Hmmm I must be making this more difficult than it needs to be.
The basic idea is that I can take a todo item from my todo.txt file and have it added to my reminders file for use with remind which generates a popup notification.

Here is the original script:

```

#!/bin/bash
cat -n ~/Dropbox/todo/todo.txt
read -p "Enter the line number of the task to add to remind " task
sed -n "$task"p ~/Dropbox/todo/todo.txt
message=$(sed -n "$task"p ~/Dropbox/todo/todo.txt)
read -p "What is the trigger date of the reminder?:" triggerdate
read -p "H0w many days in advance should this appear?" daysadvance
read -p "What is the trigger time of the reminder?:" triggertime
echo "REM $triggerdate +$daysadvance AT $triggertime MSG $message %b (in [_countdown(trigdatetime()-current())])" >> ~/Reminder-files/reminders-general

```

This works but right now I am getting:
```

1 2014-06-01* (E) +conputer Fix Mutt's spell check

```

in my reminder file when I only really want 
```

Fix Mutt's spell check

```

---

### Post by Vaphell on 2014-05-01
```
#!/bin/bash

todo=~/Dropbox/todo/todo.txt
reminders=~/Reminder-files/reminders-general

cat -n "$todo"
read -p "Enter the line number of the task to add to remind: " task
message=$( sed -n "$task s/.*([A-E])\s*+\w*\s*//p" "$todo" )
echo "$message"
read -p "What is the trigger date of the reminder?: " triggerdate
read -p "How many days in advance should this appear?: " daysadvance
read -p "What is the trigger time of the reminder?: " triggertime
echo "REM $triggerdate +$daysadvance AT $triggertime MSG $message %b (in [_countdown(trigdatetime()-current())])" >> "$reminders"
```

---

### Post by GrouchyGaijin on 2014-05-01
Thanks again Vaphell!

It is this part:
```
$( sed -n "$task s/.*([A-E])\s*+\w*\s*//p" "$todo" )
```
that I don't fully understand.

---

### Post by Vaphell on 2014-05-01
you can apply line numbers or regexes to s/// just like you can apply them to p or d. 
1p - print 1st line
1d - delete first line
1s/// - modify first line

/regex/ p - print matching line(s)
/regex/ d - delete matching line(s)
/regex/ s/// - modify matching line(s)

If you want to narrow down to a single line, just put the number in front of s/// and you are golden.
p at the end is to print the result of s/// to offset that -n option.

---

