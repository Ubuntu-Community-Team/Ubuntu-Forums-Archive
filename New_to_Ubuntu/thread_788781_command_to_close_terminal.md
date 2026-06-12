---
title: "command to close terminal"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by akimatsu123 on 2008-05-10
Hi,

sorry for the very n00b question, but what is the command to close the terminal? (as in the command i would type if i want to exit out of the terminal). i tried all i could think of. "quit" "stop" "exit" so on and so forth, none of them gave me the right one. 

if you are wondering why i don't just press the close button, i'm writing a console C++ program, and i need the terminal to close automatically after i finish. 

thanks,

---

### Post by Xiong Chiamiov on 2008-05-10
Using Konsole in KDE, exit works just fine, and exit 0 is what I throw at the end of my shell scripts.

---

### Post by El Lance-O on 2008-05-10
'exit' would be the appropriate command, although I don't know why it wouldn't work.

You might have to check with what you are using to write the code with.

---

### Post by sdennie on 2008-05-10
It sounds like you want to kill the parent shell from a C++ program.  I'm not sure if that's possible but, why not instead just start your terminal non-interactively with your C++ command (see the man page for your terminal (probably -c or -e)).  That way it will close when your C++ program exits without any intervention on your part.

For example, for gnome-terminal:

```

gnome-terminal -e "sleep 2"

```

Bringups a terminal for 2 seconds and then closes it.

---

### Post by akimatsu123 on 2008-05-10
thank you all for your response. the program does something, then i want it to say "press any key to exit" at the end, and then when the user is done reading the output, he/she can just press any key to kill the terminal. 

i realize that i can probably accomplish this with "pkill terminal" except i didnt think force quitting was a good idea. 

"exit" does nothing. i go into the terminal, type exit, and it just gives me a new line.

---

### Post by Xiong Chiamiov on 2008-05-10
Have you changed the shell you're using from the default?

---

### Post by akimatsu123 on 2008-05-10
i don't think so. is there a way i can check?

---

### Post by akimatsu123 on 2008-05-10
nvm, i fixed it. my terminal was set to hold the terminal open even when the command finishes (under current profile --> Title and Command)

thanks for your help.

---

### Post by brettg on 2008-05-10
I think you should rethink your idea about closing the terminal, it's not good practice. If somebody runs the command from the command line it will close their session. Major annoyance. You should let Windows users be dictated to and let linux user control their computers 

It is not necessary anyway, the shell will shut automatically if you run the app from the gui anyway. The only reason it wouldn't is if the shell was already running. 

Create an icon for the app, click "run in terminal" and away you go.

---

