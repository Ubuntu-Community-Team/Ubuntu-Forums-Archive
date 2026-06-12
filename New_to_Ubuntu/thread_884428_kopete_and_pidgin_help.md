---
title: "kopete and pidgin help"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Zopiac on 2008-08-09
i just need some general help with kopete. i am running it in a gnome environment, after which pidgin kept freezing my comp ('nother story). heres my todo list:

1. The bubbles that pop up; i need them to fade away after about 8 seconds
2. the colors; AUGH it looks horrible; how do i get the window colors to match my dark gtk theme???
3. the bubble even comes up when the message window is active; DO NOT WANT

heres the 'other story': i was perfectly fine using pidgin, when i tried to make it start hidden, it began freezing my comp at random; force logout took a long time to work even! well i undid what i tried (i bellieve it was pidgin %u or -u, i tried both of these) and went back to having in the startup programs just 'pidgin', but it didnt fix it. it might not have been that, anyways. any ideas?

---

### Post by Zopiac on 2008-08-09
so today when i logged in, with the autostart command of /usr/lib/kde4/bin/kopete -caption "%c" %u, to see if anyone was online. the thing is, kopete didnt show up. at all. i tried opening it in gnome-do, but it did not appear! so i used the above command in the terminal, and here was the output:

zopiac@zopiac:~$ /usr/lib/kde4/bin/kopete -caption "%c" %u
kopete(6920): Communication problem with  "kopete" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." " 

zopiac@zopiac:~$ 


:( what happened and how do i fix it?

---

### Post by Zopiac on 2008-08-09
bump :/

---

