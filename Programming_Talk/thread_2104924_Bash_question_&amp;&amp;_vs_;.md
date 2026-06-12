---
title: "Bash question: &amp;&amp; vs ;"
date: 2013-01-14
forum: Programming Talk
---

### Post by ntzrmtthihu777 on 2013-01-14
As the title states. When I started off in ubuntu I would run
```
sudo apt-get update && sudo apt-get upgrade
```when I updated; as I got more comfortable with the terminal I found running
```
sudo apt-get update ; sudo apt-get upgrade
```to be more convenient and quick as the ; key was "right there" without need for shift+7

My question now is is there any practical difference between the two, and if so what is it?
I believe the second code after && only executes if the first gave a return status of 0, whereas using ; is just the same as executing one right after the other, correct? Meaning there is no difference between
```
sudo apt-get update ; sudo apt-get upgrade
```and```
sudo apt-get update
sudo apt-get upgrade
```right?

---

### Post by nothingspecial on 2013-01-14
Yeah, you got it. With && the second command only executes if the first one is successful. You can also use ```
command || command
``` but this only executes the second command if the first one fails.

See here for a good explanation

[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

---

### Post by ntzrmtthihu777 on 2013-01-14
Thank you for the confirmation, and for the additional info; this will be a great help in debugging future bash scripts I write.

If I get your meaning right, I can write a script, for example, that does three things, and set it up like this

```
#!/bin/bash
command1 || exit 1
command2 || exit 2
command3 || exit 3

```
and by the exit code know which command did not work right, right?

---

### Post by ofnuts on 2013-01-14
> **ntzrmtthihu777 said:**
> Thank you for the confirmation, and for the additional info; this will be a great help in debugging future bash scripts I write.

If I get your meaning right, I can write a script, for example, that does three things, and set it up like this

```
#!/bin/bash
command1 || exit 1
command2 || exit 2
command3 || exit 3

```and by the exit code know which command did not work right, right?
Yes... and note that a command that returns 0 is "True", this can be strange sometimes :)

You can also use 
```

command1 || { echo "Command 1 failed"; exit 1; }

```
And no need to lookup what command rc=1 corresponds to (mind the spaces around the braces, and the final semicolon). Or even
```

( command1 && echo "Command 1 worked" ) ||   { echo "Command 1 failed"; exit 1; }

```

---

### Post by ntzrmtthihu777 on 2013-01-14
Ooo... very nice. I can't tell you how useful this would have been when I was writing my UTAU bash tool.

---

### Post by sisco311 on 2013-01-15
> **ofnuts said:**
> 
You can also use 
```

command1 || { echo "Command 1 failed" **>&2**; exit 1; }

```


Fixed. :p

Messages that shouldn't be parsed by default (user prompts, warnings and errors) should be redirected to stderr. ;)

---

### Post by ntzrmtthihu777 on 2013-01-15
> **sisco311 said:**
> Fixed. :p

Messages that shouldn't be parsed by default (user prompts, warnings and errors) should be redirected to stderr. ;)
Exactly why, may I ask? I have done a few bash programs with prompts an never did that and they worked fine. I'm curious as to why.

---

### Post by JKyleOKC on 2013-01-15
> **ntzrmtthihu777 said:**
> Exactly why, may I ask? I have done a few bash programs with prompts an never did that and they worked fine. I'm curious as to why.The main reason is so that these messages don't interfere with using the program as part of a pipeline someday. It becomes important mainly when the script generating such messages is called inside a repeating loop, and usually works properly but sometimes fails. Directing the error messages to stderr keeps them from being passed on through the pipeline; instead they go to the console for viewing.

A more immediate reason is simply to create good habits, so that a script doesn't rise from the dead and bite you painfully in the nether regions, several years after you wrote it.

---

### Post by ntzrmtthihu777 on 2013-01-15
Thank you. I understand "good practice" and try to practice it as much as possible, but I like to know exactly *why* its good practice. [Read: I don't want to do things just because someone tells me to, I wanna know why.]

---

### Post by Tony Flury on 2013-01-17
imagine this scenario - you write a script which processes a file in a certain way - and outputs to stdout - including error messages.

later on you want to use your script in a pipeline : 
```

grap foo.txt bah | myscript | sort >out.txt

```

for example

In that example if your script sends error messages to stdout,  any error messages will get sorted and stored in out.txt.

If your script always sends errors to stderr - as suggested, that pipeline will display the errors on screen - and they wont be sent to sort.

This behaviour is what all the current linux utilies do ; i.e. differentiate errors and output - it is the very reason that stdout and stderr exist and we are able to redirect them separately.

---

