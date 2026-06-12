---
title: "Splitting output of a shell script"
date: 2013-06-06
forum: Programming Talk
---

### Post by Ranko Kohime on 2013-06-06
I am writing a shell script that requires input from the user, and I would like for some functions of the script to execute in the background while receiving input from the user.

I can of course achieve this using either an ampersand, or with the coproc command, but this results in the messages from the background processes spamming into the terminal where I'm asking for the user's input.  I'd like to avoid that, but at the same time, the messages may prove to be useful, so what I'd like to do is split the terminal, in the way that screen or tmux do, sending the messages to one pane, and keeping the questions on another.

The assumption is that tmux or screen would not necessarily be available, (the script needs to operate without root privileges, therefore no apt-get'ing)

Is there a way to achieve this?

---

### Post by Vaphell on 2013-06-06
can't you redirect background stuff to a file to suppress it and run tail -f on that file in another terminal?

---

