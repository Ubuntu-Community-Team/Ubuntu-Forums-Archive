---
title: "switch from one terminal to another"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by defmomo on 2008-04-29
Is there a way to switch from an active terminal to another active one?
And by terminal I mean an ordinary shell session, as in starting gnome-terminal for example and executing a command that is looping, like `watch "dmesg | tail -n 50"`. I'm not talking about Ctrl+Alt+F<num> to leave X and go back.
I need this to access a gnome-terminal session I opened at home through ssh because I need to monitor the progress of the program I launched on it.
I know the vocabular I used might not be completely coherent, so ask a question if you don't understand the question

---

### Post by shearn89 on 2008-04-29
You could have a look at the "screen" package - it allows you to start a terminal, and then "detach" from it, and reattach at a later time. Apart from that, i don't think you can, although I don't know much about ssh.

EDIT: [link to screen manpage]("http://linuxreviews.org/man/screen/")

---

### Post by defmomo on 2008-04-29
This is just what I needed, thx for the help.

---

### Post by shearn89 on 2008-04-29
np. Give thanks if it was useful! (the medal button at the bottom of the post you want to thank).

---

### Post by defmomo on 2008-04-29
done!

---

