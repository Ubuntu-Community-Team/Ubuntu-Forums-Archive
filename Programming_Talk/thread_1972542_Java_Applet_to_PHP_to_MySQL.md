---
title: "Java Applet to PHP to MySQL"
date: 2012-05-03
forum: Programming Talk
---

### Post by PaulM1985 on 2012-05-03
Hi

I have been working on developing an AI poker player.  The player only knows its own cards and what has been bet (ie only knows what any poker player knows).  I want to test how well it performs by allowing people to play it online.

I will be running the game in an applet.  Results from the game will be posted from the applet to a PHP page which will save the results in a MySQL database.

I was thinking of doing it this way since it means that I don't have to bundle the database JARs with the applet, saving around 5-8MB to be downloaded on accessing the game page, and it also means that I don't have to open up the database to allow changes to be made from many client PCs.

My question is, is this the best way to do it?  I appreciate that people could find out the PHP page that my applet is sending the data and do multiple posts to that page to record false results in my database.  Are there any other potential issues?  Would it be possible to stop this?

Any other general comments are welcome.  I am fixed on using a Java applet since I have already written all the code for the game and I don't have the time for a re-write.  PHP and MySQL are provided by my web-hosting provider so I can't do much about changing them.

Paul

---

### Post by Some Penguin on 2012-05-04
I'd be a bit loathe to put that sort of thing into a Java applet unless planning to make the source code public anyway, since there'd be nothing stopping people from downloading the applet and decompiling the JVM bytecode into something that won't be identical but might still be useful.

Since it seems to not be an option to embed the poker player server-side and only expose a client to the user... you can make it somewhat more inconvenient to spam the results form by having the Java code output not just the game results you want to import, but a unique identifier for that result/set of results, and some non-trivial checksum that accepts all those as input data.  You can either rig the MySQL to reject results with a broken checksum, or later on just filter 'em out yourself w/ when you read 'em later.  The unique identifier for the set is just to provide duplicate detection in case the result(s) don't already have something unique in them.

It's still breakable, since one could decompile the Java bytecode and find the checksumming code, but it's at least a little work to do so, and if anybody's willing to do that I'd be more concerned with them doing so in order to rip off what you've written.

---

### Post by PaulM1985 on 2012-05-04
Thanks for the advice.

I had considered outputting some sort of unique identifier but I haven't fully thought through how it would work yet.

I also appreciate the comments about people being able to decompile my code and rip off my work.  What I am developing is quite sensitive in that it could be used as a basis for a poker bot and I also plan on re-using the code to develop a game for the Android market.  Is there a way I can prevent people stealing my work?

I don't have much time available, since this is a university project, so converting it to a server side application isn't possible in time I have left.

Paul

---

