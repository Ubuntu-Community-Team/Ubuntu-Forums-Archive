---
title: "Counter Strike Server Browser Website"
date: 2007-03-07
forum: Programming Talk
---

### Post by smartbei on 2007-03-07
I have been asked by a friend to help him create a website that would allow users to list their CS:Source server and also search listed servers by current ping, map, etc. He also said that the CS:Source servers generate an HTML page with all of the pertinent information. Without too much trouble I could write a script that processes the HTML page, inserts the data into a database and updates it every couple minutes so the player data, etc. is current. However, I am worried that this will work fine for several, maybe a few tens of servers, and that once it gets up to and over a hundred the time it will take to update all the servers every certain amount of time will be exorbitant.

Any ideas? Is there a faster way to query the servers? Are there ready-made programs that have this functionality?

I could also heavily prioritize the updating - update more popular servers more often, etc.

I had planned to do this in PHP (its what I know best), would doing it in a different language help the performance issue considerably while still remaining practical?

Thanks a lot guys!

---

### Post by pmasiar on 2007-03-07
> **smartbei said:**
> I have been asked by a friend to help him create a website that would allow users to list their CS:Source server and also search listed servers by current ping, map, etc.

I am not sure what is your concern:
(1) performance of the program doing querying? Most of the runtime is spend waitng server response, out of your control and you can hardly do anything about it.
(2) algorithm to gather server info efectively? If you have 1000 servers and average response time is 1 sec, one loop to query then one by one takes about 16 minutes. To beat it up, you have to request info asynchronously, all of them in parallel. It is obviously more work than simply query then synchronuously one by one, each time waiting for the response. Is this what you want?
(3) something else?

---

### Post by smartbei on 2007-03-07
How could I go about querying asynchronously as you mention?

---

### Post by treak007 on 2007-03-07
if you are using a relational database, try to break up the tables by maps or number of players or something so the tables aren't too big. Smaller tables will allow you to query them much faster then querying large tables.  Also, perhaps you could break up the schema so that player data was stored in a different table that is referenced from the main server table, then that data would only be queried if the user specifically asked for it. Perhaps break up the page as well as the database to allow for faster access times and less overhead and also  don't display player data until the user chooses the server they want to see. 

PHP is probably a good choice for a language, especially for mysql interaction.

---

### Post by pmasiar on 2007-03-08
> **treak007 said:**
> if you are using a relational database, try to break up the tables by maps or number of players or something so the tables aren't too big. Smaller tables will allow you to query them much faster then querying large tables.  Also, perhaps you could break up the schema so that player data was stored in a different table that is referenced from the main server table, then that data would only be queried if the user specifically asked for it. Perhaps break up the page as well as the database to allow for faster access times and less overhead and also  don't display player data until the user chooses the server they want to see. 

PHP is probably a good choice for a language, especially for mysql interaction.

As I explained im my previous post in  my "back of the envelope" guess, database access will not be the bottleneck - synchronous HTMP request/response probably will be. Tweaking/optimizing database does not change it in any way.

How to approach it? Checking what asynchonous processing ability/libraries has your preferred development language. This might be good case of selecting appropriate tool for the task - I am not expert in PHP so I have no clue if it is even possible in PHP. Python has threading support and asyncore/asynchat libraries, but I never used them myself so I cannot recommend any. Maybe Java or C/C++ might be more appropriate (much harder - but you are solving hard task). IIRC VB.NET has something rather simple for asyn processing.

Using MySQL is red herring - if done properly, this will be run via cron say every 10 minutes, read source URLS from a text file, and generates HTML page with results. I do not see need for any database. Of course you *could* use database to synchronize requests and gather data, by I do not see it as required - or even helpful. 

If done wrong, every time it runs it will make your server unresponsive by swamping it with couple hundred of processes for couple seconds - which might be not a problem at all for you. The better solution is, the less resources it uses - and more efforts it requires. Only you can tell how much effort you want to invest.

Yes, nobody promised that asynchronous processing will be easy :twisted:

---

### Post by smartbei on 2007-03-12
Well, with a bit of research I found an extremely simple way to do this, using the PHP commands popen() and pclose(). I am testing it out on my own computer with random links from newgrounds, and the problem is not really the processing that might bog down the server, rather the time it takes for the contacted server to respond - which I can't get over no matter how efficiently I do everything else. 

The database is there to make searches simpler. (as was stated in the original post, part of the goal is to have the whole thing searchable). If it was a static page that was browsed it would indeed be much easier to just use a text file for the URLs.

One last question: assuming I want to store the game type, map, ping, number of players, etc. in the database, how would you suggest I should organize the schema? (for greater searching and updating efficiency). Keeping in mind that after a search is entered, the results will include all of the above information. The simplest would be to use a single table that holds all of the information, but would that get overloaded/slow?

Big thanks for all your help guys!

---

### Post by pmasiar on 2007-03-12
> **smartbei said:**
> I am testing it out on my own computer with random links from newgrounds, and the problem is not really the processing that might bog down the server, rather the time it takes for the contacted server to respond - which I can't get over no matter how efficiently I do everything else. 

...exactly as I predicted. :-)  So it looks like you decided not to bother with querying game servers in parallel? 

Did you tried to hit your game servers? what is average response time?

> The database is there to make searches simpler. (as was stated in the original post, part of the goal is to have the whole thing searchable). 

search/query on what?

> One last question: assuming I want to store the game type, map, ping, number of players, etc. in the database, how would you suggest I should organize the schema? (for greater searching and updating efficiency). Keeping in mind that after a search is entered, the results will include all of the above information. The simplest would be to use a single table that holds all of the information, but would that get overloaded/slow?

Do you want to keep history of connections (more complicated), or just last connect (simple)?

---

### Post by smartbei on 2007-03-12
Yes, I am querying the servers in parralel, but even still the response time is relatively slow, since I don't want to flood my server with new processes.

I meant that the game servers that I list in the database should be searchable by name, map, number of players, etc.

Since I am going for the current state of the game server, All I need is the last connect's information.

---

### Post by pmasiar on 2007-03-12
for current info only - you can put all data in one table.

check another thread in forums today about making parallel processes in background to query remote webservers.

---

