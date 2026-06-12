---
title: "Problem with background command in bash"
date: 2010-08-17
forum: Programming Talk
---

### Post by Lazypete on 2010-08-17
Im having a issue with background command.

Let's say I run this:

output=`su - mqm -c "runmqlsr -t TCP -p 1414 -m LABGFA10 &"`

This would run the runmqlsr command under the user mqm with a few parameters
and send the output of the command in $output

My problem is when I run this it never return, because the command is a non interactive but yet non demonized command.

If I run this command on the shell manually it wont return, thats why I want to run it in the background.

But then again, when run in the background the script doesn't continue after launching that command.

Why?

Ok one step at a time...

If I run this by hand in the shell

runmqlsr -t TCP -p 1414 -m LABGFA10 &

it wont return to the user@host> until i hit enter

so when run in the background it still wait for some stupid "enter" to return to the script and continue.


Has anyone ever lived that problem?

It **** me off and Im having this issue with a lot of commands..
It would be worth much for me to have a solution...

Thanx everyone in the community :D

---

### Post by geirha on 2010-08-17
Well, with output=`...` you're telling the shell to read all output of the command inside `` into the variable output. So of course it has to wait for the subshell to end before it can be sure all the output has been read.

Try:
```
#!/bin/bash

# open a new file descriptor (3) connected to the output of the command «su - mq...»
exec 3< <(su - mqm -c "runmqlsr -t TCP -p 1414 -m LABGFA10)

# read one line from fd 3 (will block until a whole line is available)
read -u3 

echo "first line of output is: $REPLY"

```

---

### Post by Lazypete on 2010-08-18
Geirha thank you very much.

Your script didn't work, but it might just be because im not on Ubuntu, the shell may have subtle variance. In your code my shell didn't like the parenthesis.

But no matter, I didn't actually need the output that much, so just by telling me that the grabbing of the output was causing my problem, I just removed the output=`` and it worked well.

I'll just make a check once I started it to see if it really did start, then I'll be okay without the output.

Thank you very much.

---

### Post by geirha on 2010-08-18
If it complained about the parenthesis, you probably ran it with the wrong shell. Did you possibly run it with sh instead of bash? If you were on a non-linux system, it's also very likely there's no bash installed at all.

An easy way to grab the output is to just redirect it to a file.

```
su - mqm -c "runmqlsr -t TCP -p 1414 -m LABGFA10" >/var/log/mq.log 2>&1 &
```

---

