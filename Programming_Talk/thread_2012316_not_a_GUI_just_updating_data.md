---
title: "not a GUI just updating data"
date: 2012-06-28
forum: Programming Talk
---

### Post by woshidon on 2012-06-28
I am a simple engineer, I have written a lot of C but I am also relatively new to Linux.

I need to write some Linux based software that I can use to input data to a buffer area which will be sent to a controller automatically at precise intervals. I also need to display the results of the last packet of data from the controller as it comes in.

A small box or command line would be fine for the outgoing data but I would like the incoming stuff to replace the last data that arrived in the same position on the screen.

Is there a simple way to accomplish this?

I appreciate your help.

Woshidon

---

### Post by spjackson on 2012-07-01
It sounds like you should use the ncurses library.

---

### Post by woshidon on 2012-07-02
Thanks for the help. I read your reply and got started and forgot to acknowledge you.
Thanks again.

---

### Post by sudodus on 2012-07-02
Or simply use cursor control with ANSI escape sequences.

[[COLOR="Red"]_http://en.wikipedia.org/wiki/ANSI_escape_code_[/COLOR]]("http://en.wikipedia.org/wiki/ANSI_escape_code")

Use the following examples to translate from the general text in the wikipedia page to useful commands.

```
alias cls='echo -e "\0033[2J"'
alias red#='echo -e "\0033[31m###############\0033[30m"'
alias redtext='echo -e "\0033[31m"'
alias reset='echo -e "\0033[0m"'
```

---

