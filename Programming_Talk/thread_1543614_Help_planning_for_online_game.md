---
title: "Help planning for online game"
date: 2010-08-01
forum: Programming Talk
---

### Post by jesuisbenjamin on 2010-08-01
Hello there,

I already posted about this subject quite a while ago and i was really busy with my studies so i couldn't focus much on programming. Although i have learnt quite a bit since then, i am still a newbie in programming. Yet i have this idea boiling in my head since long and i need to bring it out there.

I would like to bring online a strategy/diplomacy board game i have developed. To start with i would like it to have the form of a map with which players could interact and play. It would not be a real time game, but a turn-based game like most diplomacy games.

Now before i begin learning the adequate programming languages and modules it is quite important i have a good idea of the overall structure of the program.

How i believe it should be built so far is:
[LIST]
[*]Have a server to host the program, i will have to pick up free and small to start with i imagine (i am a student and have no money to invest). I have seen some options on [http://www.free-webhosts.com/free-mysql-database.php](http://www.free-webhosts.com/free-mysql-database.php).
[*]Have a database with MySQL (i thought of one table with the information regarding the map and another table for user-accounts).
[*]Have a program which will produce the interface in a browser while rendering the table data into a map and allow interaction with the database. (Java, Action-Script?)
[*]There will be some more annex programs needed, perhaps to create user accounts (?)
[/LIST]

How far am i from the reality? I have read quite a bit on [http://www.w3schools.com/](http://www.w3schools.com/) so i have some idea of what SQL can do. I am less sure as to what language i should use for the game interface (Java, Action Script, etc?)
Where do i need to start building this project? Do i use the table as the center or should i start from an interface? I am not really sure as to how raw SQL data is handled or displayed in a browser.

If you have any feedback or advice, please let me know, i would really appreciate it. From my humble knowledge of programming it does not seem like a tremendously difficult project to realise, but i'll need some support for sure :)

Thanks.
Benjamin

---

### Post by lykeion on 2010-08-01
Hi Benjamin,
This seems like an interesting project. Here are my thoughts:

> **jesuisbenjamin said:**
> Now before i begin learning the adequate programming languages and modules it is quite important i have a good idea of the overall structure of the program.
I would agree that planning is key in game development, but really you need to know a programming language before you can write a game. That knowledge will also structure your planning when developing a project like this.
> **jesuisbenjamin said:**
> I have read quite a bit on [http://www.w3schools.com/](http://www.w3schools.com/) so i have some idea of what SQL can do. I am less sure as to what language i should use for the game interface (Java, Action Script, etc?)
I'd use the programming language I'm most familiar with. It takes quite a while to learn a new one.

> **jesuisbenjamin said:**
> Where do i need to start building this project? Do i use the table as the center or should i start from an interface?
You seem to focus a lot on the database and SQL. This is secondary, the game itself should be your first focus.

> **jesuisbenjamin said:**
> I am not really sure as to how raw SQL data is handled or displayed in a browser.
Frankly I don't understand this question.

> **jesuisbenjamin said:**
> From my humble knowledge of programming it does not seem like a tremendously difficult project to realise, [...]
To me it sounds like quite an ambitious project, especially as you also plan to learn a programming language in the process.

The next steps I'd take is to look on similar projects and pickup tips from them. Here are some I found (maybe they can give you some help):

**_[Risk]("http://freshmeat.net/projects/risk")_** (written in Java)
**_[WebDiplomacy]("http://sourceforge.net/projects/phpdiplomacy/")_** (written in PHP)

You should study both interface and the code.

---

### Post by jesuisbenjamin on 2010-08-02
> **lykeion said:**
> 
I would agree that planning is key in game development, but really you need to know a programming language before you can write a game. That knowledge will also structure your planning when developing a project like this. I'd use the programming language I'm most familiar with. It takes quite a while to learn a new one.

All i know is python, i played around with SQL and read some Java programming tutorials which make me think languages are not so different from one another. If i want to make a browser-based interface, Java or Action Script will be more suited than Python i guess. Knowing what i want to use a language for also helps me parsing and concentrating on the tutorials i really need.

> **lykeion said:**
> 
You seem to focus a lot on the database and SQL. This is secondary, the game itself should be your first focus.

What do you mean by game? The game is already made. It already exists as an (unpublished) board-game and i have a good draft of how i could put the game data into a table and what kind of functions would be necessary to interact with it. I mention SQL etc because i need to learn how it works and how to write a proper script for it to work into a browser.

> **lykeion said:**
> 
Frankly I don't understand this question.

Let's put it this way: how is the information stored into a SQL database published into a browser? I have played around with SQL on W3 and in my terminal, but i don't know how it actually becomes a reality on a browser.

> **lykeion said:**
> 
The next steps I'd take is to look on similar projects and pickup tips from them. Here are some I found (maybe they can give you some help):

Yep, i know phpdiplomacy. It's great but not satisfying (this is why i want to make my own) but indeed they might want to help me with my project.

Thanks for your reply.
Benjamin

---

### Post by lykeion on 2010-08-02
> **jesuisbenjamin said:**
> If i want to make a browser-based interface, Java or Action Script will be more suited than Python i guess.True, and I'd select Java but that's only because I'm more familiar with it. About pros and cons with Flash and Java for game development: **_[http://www.gamedev.net/community/forums/topic.asp?topic_id=553077](http://www.gamedev.net/community/forums/topic.asp?topic_id=553077)_** (Also check other articles on gamedev.net, it's a good resource)

> **jesuisbenjamin said:**
> What do you mean by game? The game is already made. It already exists as an (unpublished) board-game and i have a good draft of how i could put the game data into a table and what kind of functions would be necessary to interact with it.In that case my next step would be to create some kind of simple prototype for the game using pen and paper. Sketch every single "window" of the game (login, join game, game interface, help page, game over, etc) with all buttons/interactions outlined. Then I'd think of what information has to be passed to and from the game server for every user interaction (like username, score, move, etc).

> **jesuisbenjamin said:**
> Let's put it this way: how is the information stored into a SQL database published into a browser? I have played around with SQL on W3 and in my terminal, but i don't know how it actually becomes a reality on a browser.Basically you write code to a) connect to the database b) execute a SQL query c) retrieve the results d) process the results
An example would be to store hiscores in a database. When game ends a hiscore table may be shown, and to get the data for this table you'd make a SQL query.
But you could also store the hiscores in a simple text file. This may be simpler. I'd think on each field I was thinking on to put in a database, and say why would I need to have this in a database. What are the benefits and what are the drawbacks?

---

### Post by simeon87 on 2010-08-03
You may also want to consider using HTML 5; it's not mainstream yet but it'll be the future of web-based games so it's worth looking into. At least you won't have to redevelop or face difficulty with integrating it with the rest of the website.

---

### Post by Some Penguin on 2010-08-03
> **jesuisbenjamin said:**
> Hello there,
I
[LIST]
[*]Have a server to host the program, i will have to pick up free and small to start with i imagine (i am a student and have no money to invest).
[/LIST]


Clients should practically never talk to databases.  It's exceedingly brittle and makes it far harder to validate anything.  For instance, for a client to be able to write a database means that the client now must have all the information required to make changes to the relevant tables.  This might make it essentially impossible to prevent cheating, for instance, unless you're VERY good and thorough about writing in-database constraints and extremely paranoid trigger functions.

If you're thinking servers, perhaps think about Apache or Apache Tomcat (if you want a browser-based setup instead of e.g. designing your own lighter-weight server on raw sockets or the like).

> 
[LIST]
[*]Have a database with MySQL (i thought of one table with the information regarding the map and another table for user-accounts).
[/LIST]


I find it very unlikely that you'll have much need for a full relational database.  Range queries?  Foreign key constraints?  Large-scale B-trees?  Query logs?  Even if you have e.g a map with five hundred territories, with a dozen variables each; and several hundred pieces with a few variables each -- for modern systems, that's basically nothing.

Tomcat with a REST-based API, and some primitive authentication, OTOH...

Also, incidentally, you haven't said whether a single server should be able to support multiple concurrent games.

> 
[LIST]
[*]Have a program which will produce the interface in a browser while rendering the table data into a map and allow interaction with the database. (Java, Action-Script?)
[/LIST]


Meh.  You could probably get away with HTTP/1.1 image-maps and forms.  Ugly but it'd work... if you do the rest right.

More important is that you nail down the protocols involved.

> 
[LIST]
[*]There will be some more annex programs needed, perhaps to create user accounts (?)
[/LIST]

How far am i from the reality? I have read quite a bit on [http://www.w3schools.com/](http://www.w3schools.com/) so i have some idea of what SQL can do. I am less sure as to what language i should use for the game interface (Java, Action Script, etc?)
Where do i need to start building this project? Do i use the table as the center or should i start from an interface? I am not really sure as to how raw SQL data is handled 


The interface... meh.  That's not the interesting part.

Properly controlling access to game state -- defining protocols for what is legal, and an authentication scheme to prevent players from accessing what they shouldn't know or changing things that they shouldn't change; perhaps couple this with appropriate notifications (sending e-mails, etc); that is trickier.

---

