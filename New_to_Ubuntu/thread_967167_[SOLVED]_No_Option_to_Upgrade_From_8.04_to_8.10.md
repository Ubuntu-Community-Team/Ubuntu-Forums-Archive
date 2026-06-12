---
title: "[SOLVED] No Option to Upgrade From 8.04 to 8.10"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Jack Bonner on 2008-11-01
The title says it all really, and i'm a little confused. I have no option to upgrade to 8.10 through the update manager. Nothing comes up. I gave it a few days assuming there was a problem server-side, but Google pulls up nothing and i'm stumped. Any ideas?

---

### Post by nerdking on 2008-11-01
> **Jack Bonner said:**
> The title says it all really, and i'm a little confused. I have no option to upgrade to 8.10 through the update manager. Nothing comes up. I gave it a few days assuming there was a problem server-side, but Google pulls up nothing and i'm stumped. Any ideas?

go to administration- software sources- then updates tab.
change release upgrade to normal releases.

---

### Post by Mazza558 on 2008-11-01
try 

> sudo update-manager -d

in the terminal

---

### Post by OrangeCrate on 2008-11-01
> **Jack Bonner said:**
> The title says it all really, and i'm a little confused. I have no option to upgrade to 8.10 through the update manager. Nothing comes up. I gave it a few days assuming there was a problem server-side, but Google pulls up nothing and i'm stumped. Any ideas?

Go to Software Sources > Updates >, and change the option at the bottom from longterm support releases to normal releases.

Edit:

Wow, three of us posting at the same time. It's a wonder the server didn't blow up.

---

### Post by Dark006 on 2008-11-01
Go to System->Administration->Software Sources and then go to the "Updates" tab. Where it says Release Upgrade change from "Long Term Support release only" to "Normal Release". Close and re-try, it should work for you.

---

### Post by CJ Master on 2008-11-01
If your already using 8.10 RC version then there wont be an option, just run upgrade manager like normal.

---

### Post by Jack Bonner on 2008-11-01
> **nerdking said:**
> go to administration- software sources- then updates tab.
change release upgrade to normal releases.

That worked a charm, thanks mate. Also thanks to the others that posted the same solution.

Many thanks, that's been bugging me

---

### Post by OrangeCrate on 2008-11-01
> **CJ Master said:**
> If your already using 8.10 RC version then there wont be an option, just run upgrade manager like normal.

Read title of thread ^.

(But, you're absolutely correct if they are already on Intrepid.)

---

