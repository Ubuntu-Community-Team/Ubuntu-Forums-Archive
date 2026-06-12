---
title: "Server-side scripting auto-update"
date: 2010-09-19
forum: Programming Talk
---

### Post by jesuisbenjamin on 2010-09-19
hello there,

I am learning slowly a various kind of codes and scripts. I am working on making a browser-based, turn-based version of a risk-like board game.

I created a small database to test and learn on a server (hosted on Zymic).
How to query a database and render the data in a browser is pretty clear to me. However, for a max security and also because it's turn based, i'd like to create a server-side script, which will auto-update the database every 24h. That second part is less clear to me.
How do i make a server-side scripting to perform auto-updates? Where do i put this script on the server? How is it run? (A script on a desktop is run when pressing a button or running a command, how do i make this run automatically on the server then?) 
If you could explain to me the basic principles that would be great thanks, i haven't found this kind of information on-line.

Cheers :D
Benjamin

---

### Post by worseisworser on 2010-09-19
Perhaps you're looking for something like cron?

---

### Post by jesuisbenjamin on 2010-09-20
Hi there,

Thanks for your reply. I assume you are referring to [Cron]("http://en.wikipedia.org/wiki/Cron")?
It sounds pretty much like what i need. I can allow users to send their "orders" to an "order-table" and process the information of the "order-table" to change the "main-table" data which represents the game-board. Would that be a correct interpretation of what you imagine Cron to be doing?

The hic is i cannot use something like cron on a host like zymic, can i? I doubt i can install a deamon on a server other than a server i would have myself in house, or can i?

And does your answer mean that PHP alone cannot do that?

Thanks.
B.

---

