---
title: "Lirc configuration"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by helixed on 2008-04-25
I have a windows media center remote.  I configured this remote to work using MythTV.  The remote works fine in the application.  My question is this:  How can I get the remote to launch an application?

Thanks,

Helixed

---

### Post by helixed on 2008-04-27
Okay, so this one was pretty easy.  There's a program, irexec, which is used to execute programs inside of lirc.  All I had to do was add the following to my /home/helixed/.lircrc file:

# Turn on Elisa
begin
prog = irexec
button = Home
config = DISPLAY=:0 /usr/bin/elisa
end

and then I added the following to my sessions list:

irexec -d /home/helixed/.lircrc

Works perfectly.  I hope this helps somebody else out, because I spent a couple hours trying to figure this out.

helixed

---

