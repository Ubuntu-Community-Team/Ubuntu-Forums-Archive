---
title: "Can't install anything because of &quot;another&quot; open window. BAH"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by papuccino1 on 2008-07-17
This is starting to piss me off.

I just restarted the computer and still it says another application is open:

[IMG]http://i34.tinypic.com/13yh2js.png[/IMG]


What the hell?

How can I fix this crap? I just want to install 1 program. Why is it making things so difficult for me.

---

### Post by RomeReactor on 2008-07-17
Hi. That's probably Update Manager running in the background; it's usually one of the first things that happens after logging in. Just give it a few minutes and then try installing the program.

EDIT: If this behavior annoys you, you can select how frequently you want Update Manager to check for updates: in Synaptic go to 'Settings->Repositories->Updates tab'.

---

### Post by iaculallad on 2008-07-17
As the message says: You have to close all open Synaptics window. Also, try to close all active apt processes in your terminal.

To view and kill active apt processes if any:

```
ps aux | grep apt
kill -9 process_id
```

---

### Post by papuccino1 on 2008-07-17
In English please!

---

### Post by iaculallad on 2008-07-17
> **papuccino1 said:**
> In English please!

When you're finish closing all Active open Synaptics window, then, you could use the terminal to view other active apt processes (if there are any) by inputting the following commands below:

```
ps aux | grep apt
kill -9 process_id
```

---

### Post by steveneddy on 2008-07-17
> **papuccino1 said:**
> This is starting to piss me off.

I just restarted the computer and still it says another application is open:

[IMG]http://i34.tinypic.com/13yh2js.png[/IMG]


What the hell?

How can I fix this crap? I just want to install 1 program. Why is it making things so difficult for me.

Having an attitude won't help your cause.

Using curse words won't help either.

The window says that you have another application open that handles installing software. It also says that you have to close the other application before you can proceed.

Update Manager will be a little orange icon on the top bar with an exclamation mark ( ! ) in the middle. 

The box says that only one can be running at a time.

Update manager will sometimes run at start up.

This is part of the learning process. I hope that you don't continue with this same attitude during the rest of your time learning how to use Ubuntu. 

I think that if you changed the wording of your posts and threads and use less "language" you will get better responses.

Remember that we are all volunteers here. If you want paid support where you can take your anger out on somebody, that is available also.

---

