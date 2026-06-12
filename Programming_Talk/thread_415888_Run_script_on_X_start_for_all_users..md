---
title: "Run script on X start for all users."
date: 2007-04-20
forum: Programming Talk
---

### Post by musther on 2007-04-20
I have a script which I wish to run when x starts.  I know I could add it to my session, but I want to make it happen when any user logs in, and I don't want to add it to every users gnome session.

Any idea how I can do this?

---

### Post by kerry_s on 2007-04-20
You can use /etc/rc.local to start apps, they will run as root, if you need it to run as a particular user use->

sudo -u user_name command_to_run &
otherwise
command_to_run &

---

### Post by musther on 2007-04-20
I'm sorry, I forgot to add that it has to run when X has started as it uses zenity to communicate with the user.

---

### Post by kerry_s on 2007-04-21
In that case you would have to use the session startup manager. I don't think there's a way to run anything inside a users session from outside of the session.

Wait, i think you might be able to get what you using the /usr/share/xsessions/gnome.desktop

make a little script that starts the gnome session and runs your script after and point gnome.desktop to your script. Just a thought.

---

### Post by superfunkymonkey on 2007-12-05
Hey buddy,

If you use GDM (the default) as your graphical greeter you can write whatever bash script you want in any of these files.

/etc/gdm/PreSession/Default
/etc/gdm/PostSession/Default
/etc/gdm/PostLogin/Default
/etc/gdm/Init/Default

The file you choose to edit dictates what stage your script will be executed at.

Matt

---

### Post by musther on 2007-12-05
Thanks for answering my really old thread!  I did finally find this out from some other source, but thanks anyway, it's nice to know there are people helping on way old threads.  :-)

---

