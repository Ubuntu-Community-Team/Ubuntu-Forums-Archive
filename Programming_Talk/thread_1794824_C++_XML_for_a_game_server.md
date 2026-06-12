---
title: "C++ XML for a game server"
date: 2011-07-01
forum: Programming Talk
---

### Post by Pierrick584 on 2011-07-01
Hello, as another post says. i'm working on an mmorpg right now, actualy, currently i'm working the basic class, and a kind of working text-rpg-combat just to prepare and test out the combat system of the soon-to-eventualy-maybe game.

I arleady saw an mmorpg server using XML to store data about character class, spells, and more. But, this game does not actualy get that much player per server, so i were wondering if XML could ever slow down (in long term, considering the server would get an extremely huge ammount of players online)  and, if yes, what would you guys recommand me to save such data in a way that i could change them without recompiling, or, does keeping 100% of these data in the code would be the only way performance-wise?

Obiviously database could be another alternative, but if i'd do that, i'd prefer to keep two separate database, one for the actual... usual database stuff, and another one for the things that i think about putting in XML, is that easy to manage two different connection to databases?

The other reason i'd prefer not use database, is that i'd then have to develop applications to access these data, as i find phpmyadmin not convenient enough for this specific task.

Thanks in advance to whoever will help out on this! :)

---

### Post by cgroza on 2011-07-01
XML should be fine for smaller projects. It will save you a lot of troubles with all the existing parsers out there. For bigger projects, I would pick a database.

---

### Post by Pierrick584 on 2011-07-01
Thanks, and about the dual database, would it cause any issue?

---

### Post by PaulM1985 on 2011-07-01
Why not keep everything in the same database?  You can use different tables for different things.  If you wanted to keep things separate from an organisational point of view, you could give the database table names short prefixes for the different organisational area that they relate to. 

Paul

---

### Post by Pierrick584 on 2011-07-01
Thats much more of a kind of security measure, split content and eventual player's data, and also beacause i might try to go for a kind of complex server structure, splitting the server in a few server comunicating, and each application would need only a limited ammount of information, witch would be splitted on different database...

You dont need to tell me, thats WAY overkill, yet, makes it interesting and definitively gonna learn alot in the process, and on top of that, would give alot of possibility for expanding if this project ever get big

---

### Post by PaulM1985 on 2011-07-02
I have learnt in the past that it is usually better to have a plan in mind that will allow for expansion, but stick with what you need.  Maybe go for a simple implementation for now.  Security isn't a massive issue at the minute, since you don't actually have anything.  Get something simple running then refactor and improve it.

I found this link amusing, it sort of talks about how to over develop something when only a simple solution is needed at the time.
[http://chaosinmotion.com/blog/?p=622](http://chaosinmotion.com/blog/?p=622)

Paul

---

### Post by PaulM1985 on 2011-07-02
Here is an idea how you could implement this if you wanted to keep the storage of the information separate.

Create a class for reading and writing (general access) for each of the data sets that you want to keep separate.  Whenever you want the data in your game, you access it via these classes. If you decide you want to change the storage mechanism (use DB instead of XML etc) you only have to change the implementation of the access class for the related data.

Paul

---

### Post by Pierrick584 on 2011-07-02
Hrm, i kind of planned to do that arleady, but never though about changing the content of it if the load is too big... yeah i guess thats an idea, thanks!

on a side note... dint realy get an answer, it is possible to keep two completely different connection to two different mysql server stimultanously?

---

### Post by PaulM1985 on 2011-07-03
It looks like you should be able to make more than one connection.  [http://stackoverflow.com/questions/274892/how-do-you-connect-to-multiple-mysql-databases-on-a-single-webpage](http://stackoverflow.com/questions/274892/how-do-you-connect-to-multiple-mysql-databases-on-a-single-webpage)

That being said, I don't know much about this sort of thing. This is just something I found.

Paul

---

