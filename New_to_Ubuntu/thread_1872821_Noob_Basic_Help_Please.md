---
title: "Noob Basic Help Please"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by GapToothedGypsy on 2011-10-31
Hi guys,

Another Noob here. By way of getting to learn how to find my way around in Ubuntu I would like to do a small project. So could someone please explain to me how I can get Ubuntu to start a program like TSClient on boot and when it exits Ubuntu is shut down.

Presumably I would need to create a script and run it, but I have no idea where to start or where the script should be placed.

Any help gratefully accepted.


Regards


GTG

---

### Post by nothingspecial on 2011-10-31
Thread moved to Absolute Beginner Talk.

---

### Post by Paddy Landau on 2011-10-31
You don't say which version of Ubuntu you are using.


[LIST]
[*]Go to your Startup Applications.
[*]Press *Add*.
[*]In *Name*, type anything you like (e.g. TSClient).
[*]In *Command*, type *tsclient*.
[*]In *Comment*, type anything you like.
[*]Press *Add*.
[/LIST]

Now, tsclient will start every time you log in (not when you boot the computer, but when you log in). As soon as you log out, Ubuntu will automatically ask it to close.

---

### Post by BenB1 on 2011-11-14
Not sure if it is a consideration, but one could use [ssh]("http://alturl.com/wnro8") for such things. I admit feeling afraid of the idea of remote terminal being open the whole time as suggested by the op. Security is something which yells at me right away. And I am meaning [security]("http://alturl.com/ecgt9") for both parties here, the server and client. Ssh could provide better security as far as transfer, also allow a server administrator to establish boundaries. Just some humble musings, take or leave as you shall as it is certain ymmv.

---

