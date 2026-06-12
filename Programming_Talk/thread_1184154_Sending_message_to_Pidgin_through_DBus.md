---
title: "Sending message to Pidgin through DBus"
date: 2009-06-10
forum: Programming Talk
---

### Post by JustAnotherVagueAnon on 2009-06-10
Hello, I've been able to get most things working with DBus, but a question I have is replacing and sending a message upon receiving the SendingImMessage signal.

The prototype for the function pointer for that signal is
sendingMessage(account, receiver, message)

The function to send an IM is PurpleConvImSend(im, message)

Is there a way to satisfy the im parameter with the parameters from sendingMessage?

Btw, I'm using Python but help in any language will help.

---

### Post by khc on 2009-06-11
you cannot replace the message through dbus, you can send another message though. If you need to replace the message, you have to write a plugin.

---

