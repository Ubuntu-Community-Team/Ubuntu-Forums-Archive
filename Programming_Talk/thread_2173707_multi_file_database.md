---
title: "multi file database"
date: 2013-09-10
forum: Programming Talk
---

### Post by ki4jgt on 2013-09-10
Would a multi file database be good to run a website on with multiple users? For example, each user has a file in which is a python dictionary containing their password, email and personal information. The file is named by the username. Users would be split up into groups of 1000 and placed in folders called user.number where number is the group the user fits in. Services provided by the site would have their own folders as well. Sorry to post this but the only file based db i can find online is flat file.

---

### Post by ofnuts on 2013-09-11
You know, databases were invented for a reason...

EIther you site has 50 users and you can live with such a scheme or it reaches significant size and then you discover you have to relate services to users which will be hard to do efficiently if all the info is scattered over fthousands of files.

If you don't want to to get burdenerd with a real dabase server (at least at the beginning) then there are embeddable database libraries such as SQLite.

---

### Post by ki4jgt on 2013-09-11
> **ofnuts said:**
> You know, databases were invented for a reason...

EIther you site has 50 users and you can live with such a scheme or it reaches significant size and then you discover you have to relate services to users which will be hard to do efficiently if all the info is scattered over fthousands of files.

If you don't want to to get burdenerd with a real dabase server (at least at the beginning) then there are embeddable database libraries such as SQLite.

Well, technically "they've already got this" has ruined more inventions than mother nature has good ralationships. SQLite has a high read rate with low write rate. Only one record can be written to it at a time. While on the other hand there are numerous databases that are schemaless and are faster and more organized than their relational counter-parts because of it. MongoDB for one which tries to replace MySQL is in no way relational. It basically does what I posted except it does it in a database file. There are some cases where it's not desired but. . . it has the best of speed, agility, scalability, and in my opinion data storage and retrieval. No SQL.

---

### Post by ofnuts on 2013-09-12
> **ki4jgt said:**
> Well, technically "they've already got this" has ruined more inventions than mother nature has good ralationships. 

But "reinventing the wheel" has killed very many programming projects...

---

### Post by ki4jgt on 2013-09-12
Only because developers got tired of messing with the new model of the wheel. Instead of just conceptually throwing it together, they want it perfect out of the box. The wheel needs to be rewritten from time to time. I mean, look at it. We went from wood to metal (I'll never believe they had a stone wheel LOL). Now we have the metal wheel with a bit of rubber around it. We've had that for how many years now? I'm sorry but we're using concepts from thousands of years ago and telling ourselves over and over again not to remake them into something better because of the fear that they could be made worse. That's not only bad programming, it's bad science. What, are all the successful wheels going to vanish off the face of the Earth b/c you decided to try something new? For evolution of the physical and conceptual world to take place, one must have a set of ideas one can draw on. In the world today, Austrailia is one of the only countries where natural evolution is taking place b/c it's the only place that's isolated from the rest of the world and off doing it's own thing. Also, where do programmers get these cracks? Is there a programmer's bible or something? I've heard that phrase a million times and I still don't get why one cannot "reinvent the wheel." What's wrong with it. All the wheel needs is a couple of fundamental concepts to work. You're not really reinventing anything, just reassessing it. It must allow for ease of transport via removing the obstacle of the ground holding it back, voala, you now have air lifted crates that can be pulled around buildings by handles and glide above the ground. All one can do is try. The air-gliding works or it doesn't. Later you can throw in all the pretty details. Now, you just want one or two things. Sure, it's a pain in the butt but someone's gotta do it or else we'll all be stuck using "wheels." Computers being fully conceptual machines, this thread should be treated as a concept. Conceptually, what mathematically prevents (since computers work on math) me from achieving faster results with this idea? I've been trying to get this community to have discussions like this for years but all the time I hear that same old argument "don't reinvent the wheel." What will happen if I reinvent the wheel? Is the wheel god gonna come down from the sky and strike me for touching his sacred invention? So, what have I got to lose if I reinvent the wheel? Time? I have plenty of that. Headache? I'm learning something and it's a fun project. I'm not discovering that something won't work. I'm discovering WHY it doesn't work (which is something a LOT of computer students today DON'T want to know at all). All the other wheels aren't going to disappear just because I invented an air-lift. It's always, what does this equal? What does this equal? but never, why does it equal that? Conceptually, a database is just a file with information that a piece of software searches on your behalf. That's the basic idea behind the wheel. Then, someone discovered tiny (under-the-surface) modifications could be made that allowed the database (wheel) to be better (like allowing the wheel to float on air by using rubber to trap that air) but the database has never left it's original intended function, just like an airlift doesn't lose the purpose originally given to the wheel. It just changes the tiny modifications a bit. The airlift still rides on air (just like any other modern wheel) but it's by reassessing the wheel that we found out, it's the air and NOT the wheel itself that makes the invention. Now, we can give way to other means of air transport because of that. I don't know. These are just my ramblings at 4 in the morning. I just don't see how so many people can convince themselves to just accept that the world is built on man-made concepts and that we should go head-over-heels out of our way to preserve those concepts, lest we lose our way in the forest of ignorance. Each path we take through the forest get's us a better map of what we're dealing with and it's not like I'm asking that the wheel be reinvented. I'm just asking, conceptually, what's wrong with the wheel I invented?

---

### Post by trent.josephsen on 2013-09-12
Save the ranting for your blog.

If you think you have an idea that can improve on the *many* already existing database engines out there, then just say what it is and maybe someone can tell you whether splitting a database over hundreds (maybe millions?) of files is a good way to go about it. Or write code to do it both ways and see what's better.

Your original post seemed to imply that you didn't have any particular design in mind beyond "one file per user", which, to me, sounds like it would be prohibitively slow at large scales unless you had a very fast index. Even then, traversing a filesystem doesn't come for free, which is why existing DBs mostly try to use a few large files in the same directory and not a million small ones scattered around.

Exactly what limitation(s) of existing DB engines / DBMSes are you trying to overcome?

---

### Post by ki4jgt on 2013-09-13
Sorry, I didn't mean to "rant." I've just been having a hard time. Originally when I started computers it was because I could make them mine. I could hack them, build them, destroy them, blah blah blah. I saw them for what they were from the ground up. When I learn a concept, I like learning it from the ground up so I can build the system how I want it. Recent events however have made me very insecure about myself and in turn, I usually spout that off to others. It's life. I know. Anyway, I'm not looking for any advantages. I want to create god aweful computer concepts, just to say I did and learn WHY they didn't work instead of just taking someone's word for it. I literally want to do stupid stuff for the educational value and if I'm lucky develop something so rediculously simple that it "just works" for no reason. I want to test the concepts of reality and make sure we're not just telling ourselves over and over that those are the concepts that work. I want to press my computer to the limits and be king of my domain. In all honesty that is. So, if I must answer your question, I'm trying to overcome the concepts of one-size-fits-allism in databases. I'm curious and baffled that every time I get on a computer forum I get answers such as "Don't reinvent the wheel" or "that'll never work" but no one telling me why. It messes with me that everyone who is an expert on a machine based purely on concepts can tell me nothing more than what I'm doing will never work or not to redo something b/c it's too much of a hassel. My purpose for the database format though is purely educational. I don't want anything out of it and I have nothing to lose if I do implement it. I just want to learn. Which is my point in posting it here. I wanted to compare notes with other people.

---

### Post by ofnuts on 2013-09-13
When you asked you question, it wasn't "writing a hypothetical database system for fun or education'", it was "using a database system for a real web server". In which case, people like me who have been developing web servers know what the database ends up being used for, and it would take you years of development before you reach that kind of functionality. Because the big point of DBMS is that they somewhat separate the data from the methods to retrieve it. The mindset is really "Store the data first and let's think about what we can so with it later".  

Of course in an ideal world, you can code up a whole computer yourself Torvalds-like if your are good enough. But even Linus Torvalds didn't wite the whole of Linux by himself (he didn't even write it completely from scratch), he only wrote single-handed the first releases of the kernel. Then he got some help from other programmers and some code from the GNU foundation was added in. It will take you several months to reach the functionality and reliability of an Arduino board. 

You forget that you stand on the shoulders of giants, or more accurately, on a big anthill created over the years by armies of coders. You will never really start from scratch anyway. What do you want to start with:
[LIST]
[*]sand
[*]silicon
[*]discrete transistors
[*]integrated circuits
[*]circuit board
[*]whole machine
[*]machine code entered with switches (hello, the 60's)
[*]assembler (and editor)
[*]compiler
[/LIST]

---

### Post by trent.josephsen on 2013-09-13
> **ki4jgt said:**
> I'm curious and baffled that every time I get on a computer forum I get answers such as "Don't reinvent the wheel" or "that'll never work" but no one telling me why.

Okay, fair enough. I am no database expert, but here's my answer to that question:

Think about how you would write code for a database engine like that. What operations are going to be easy? If the database is spread over many files, maybe you can parallelize it on the file level, which would be a good thing if your typical use case is updating thousands of users' data at once. But what about a query like... "Find all the users who live in Seattle"? If each user's data is in a separate file, and they're separated into directories by (say) user ID, there's no way to do that except to open every single file, seek to where the city name is defined, and check if it says "Seattle". That's not a quick operation. You could, perhaps, have index files that speed up the process by storing UIDs by city name, but indexing a database is really the same problem as creating the database to start with. Even if indexing was instantaneous, you'd still be losing time by calling out to the OS to traverse a filesystem and open a file for every result, so in the end you'd be losing to the guy who put his whole database in one flat file.

Relational databases work because each table in a (well-designed) database is orthogonal to all the other tables; they don't contain extraneous information, and all the data pertaining to a particular "thing" (city, user ID, name, whatever) is found in the same place, so it's quick to search. Given that, breaking a table over several files only makes sense if the size of the table is itself a performance penalty when stored in one file.

As for reinventing the wheel? It turns out that sometimes, wheels work really well, even if you have to grease them once in a while :)

---

