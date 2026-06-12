---
title: "PHP with Ubuntu"
date: 2008-10-25
forum: Programming Talk
---

### Post by jesuisbenjamin on 2008-10-25
Err i am new to all this:

If i am writing in Python, then i use IDLE and it's all cool.
But what if i want to write in PHP? Is there such environment?

:-k

---

### Post by ad_267 on 2008-10-25
Umm so you want to be able to enter PHP code and see the output like running python interactively? Or you just want to be able to type php code with some IDE features?

If you don't need the interactive behaviour you can use gedit, the default text editor. Bluefish is designed for use with PHP. Geany is also good. There's plenty of other options out there.

If you want interactive behaviour I don't know of an IDE that does this. You could use the terminal plugin for gedit. To run php in a terminal you need the php5-cli package and then can run "php --interactive".

---

### Post by LaRoza on 2008-10-25
What exactly are you asking?

You can write code in any editor, gedit with its plugs is very good, in fact, it is one of the best.

You can use php5-cli, see [http://ubuntuforums.org/showthread.php?t=692720](http://ubuntuforums.org/showthread.php?t=692720)

For an interactive prompt: [http://www.phpsh.org/](http://www.phpsh.org/)

---

### Post by jesuisbenjamin on 2008-10-26
> **LaRoza said:**
> 
For an interactive prompt: [http://www.phpsh.org/](http://www.phpsh.org/)

Hey there, thanks for the tips.
The second option is what i am talking about. Only i am not really successful in installing this program... How should i proceed?

---

### Post by jesuisbenjamin on 2008-10-26
Aaah wait a minute:

I think i have misunderstood the whole thing.

So i should write my scrip in Gedit and then run it Terminal just as i wrote my python code in the top window of IDLE and ran it in the interactive shell of IDLE?

So besides from it just being a little less cool to have to switch from Gedit to Terminal, it's all the same right?

---

### Post by cl333r on 2008-10-26
The other day has been released the RC of NetBeans 6.5 which features commercial quality support for PHP for free. I bet you won't be disappointed, I heard a lot of positive feedback on php support.
There's a build of NetBeans with PHP preinstalled:
[http://download.netbeans.org/netbeans/6.5/rc/](http://download.netbeans.org/netbeans/6.5/rc/)

The final release is expected in about 2 weeks.

---

### Post by drubin on 2008-10-26
> **cl333r said:**
> The other day has been released the RC of NetBeans 6.5 which features commercial quality support for PHP for free. I bet you won't be disappointed, I heard a lot of positive feedback on php support.
There's a build of NetBeans with PHP preinstalled:
[http://download.netbeans.org/netbeans/6.5/rc/](http://download.netbeans.org/netbeans/6.5/rc/)

The final release is expected in about 2 weeks.

Please take a look at the stickies for IDE's and working environments. If you are wanting to set up php for use in websites take a look at my sig.

---

### Post by ad_267 on 2008-10-26
Are you wanting to use PHP for web development or something else?

When working with PHP I had a local apache/mysql/php installation and wrote my php in gedit and then just viewed the web page from my web browser.

---

### Post by jesuisbenjamin on 2008-10-28
> **ad_267 said:**
> Are you wanting to use PHP for web development or something else?

When working with PHP I had a local apache/mysql/php installation and wrote my php in gedit and then just viewed the web page from my web browser.

Ha this sounds cool,

Well i am still considering options so as to learn coding with a certain goal: that is writing a multiplayer diplomatic game. I would work on the content and my bro would add the graphic part. 
He has advised me to use PHP to work on the interface (player's side), sql (mysql?) for the database (the 'world' side) and Apache (which i assume to be a server application?).
My knowledge of networking is _very_ limited and as of programming i begun with Python, for which i have a good feel (flexibility and simplicity). I was hoping to continue with Python, and looking at PHP i found it somehow more convoluted or maybe i didn't find any nice tutorial so far.
To answer your question in short: yes, for a web application (the above multiplayer game). And i wonder to what extent it makes a difference for the program whether i use PHP or Python.

---

### Post by howlingmadhowie on 2008-10-28
you'll be looking to put the whole of the game logic on the server, so you'll end up writing a lot of php/python/whatever. 

The trouble with going through apache is that the whole of the logic will be loaded for each refresh and page view. it may be better writing your own application and opening a port to the outside world rather than using apache.

---

### Post by jesuisbenjamin on 2008-10-28
> **howlingmadhowie said:**
> it may be better writing your own application and opening a port to the outside world rather than using apache.

Do you mean that the game logic and interface should be a local program on which is loaded info from the server?

---

### Post by howlingmadhowie on 2008-10-28
i mean to say that apache starts with the php interpreter inside it, but everytime you call a .php page, the php interpreter has to start again and load the whole page and process it to find out what to do. it would probably result in a quicker game if you looked on the php (or python) program you're writing as the server and let it keep running all the time.

---

### Post by jesuisbenjamin on 2008-10-28
> **howlingmadhowie said:**
> It would probably result in a quicker game if you looked on the php (or python) program you're writing as the server and let it keep running all the time.

So there is no need at all to use sql nor apache for the game itself? The whole thing would be in php or python?

I am a bit confused. To be honest i am not so sure as to what the point of using and php and sql and apache is. These are three different codes for one program... I may just as well be ignorant about all this, but it seems more simple to me to use one code only. 
But if i understand what you say correctly, then using php only (in apache) would be good enough, if not better?

---

### Post by howlingmadhowie on 2008-10-28
using mysql to store data is a good idea. an sql database is a method to store and search and combine large amounts of information. you could probably program a customized data storage engine for your application which would be better, but it would be a lot of work. 

what you are basically looking at is an application which does the following:

```

initialize_stuff(game_id)       // takes lots of time, 
                                // building the world and loading data
while action!=QUIT:
  process(action)
store_stuff_and_quit()          // takes lots of time too

```

going through apache would mean that initialize_stuff() and store_stuff_and_quit() would have to be called for every action. 

you could also do it like this:

```

initialize_stuff(game_id)
port=open_port_to_outside_world()
get_action_from_port(port)
while action!=QUIT:
  process(action)
  get_action_from_port(port)
store_stuff_and_quit()

```

you could use html as a protocol, there's nothing wrong with that, it would just be a big waste of time loading and saving stuff with every move.

---

### Post by jesuisbenjamin on 2008-10-28
> **howlingmadhowie said:**
> it would just be a big waste of time loading and saving stuff with every move.

Ok it makes sense. Thanks for the tip.

Another question: Can i do all this locally on my machine while developing or do i need to start including networking right away?

Possibly i could pretend to be all potential users and pretend my computer is the server for as long as i am developing the program? Then i throw the whole thing on a server?

---

### Post by howlingmadhowie on 2008-10-28
that should work :)

---

### Post by jesuisbenjamin on 2008-10-28
> **howlingmadhowie said:**
> using mysql to store data is a good idea. an sql database is a method to store and search and combine large amounts of information. you could probably program a customized data storage engine for your application which would be better, but it would be a lot of work. 



Should i start with making the database of 'World' into SQL? Then how about the game logic --i am getting confused -- should it be done in SQL too or in PHP?

---

### Post by howlingmadhowie on 2008-10-28
the game logic should be in php. the database should be used to save game states and things like that.

what we have is something like this:

```

port=open_port()
until input=get_input(port): wait()
game_id=get_game_id(input)
state=mysql_load_state(game_id)
while action!=QUIT:
  process_action(action)
  get_next_action(port)
  state=update_state(state)
mysql_save_state(game_id, state)

```

---

### Post by jesuisbenjamin on 2008-10-28
i like your code :)

---

### Post by howlingmadhowie on 2008-10-28
if it were only that easy :)

---

### Post by jesuisbenjamin on 2008-10-28
> **howlingmadhowie said:**
> i mean to say that apache starts with the php interpreter inside it, but everytime you call a .php page, the php interpreter has to start again and load the whole page and process it to find out what to do. it would probably result in a quicker game if you looked on the php (or python) program you're writing as the server and let it keep running all the time.

Hey there, i'm trying to dig into information about PHP and SQL, but the whole thing remains mysterious to me. I am advised to install Apache and all (LAMP or XAMP)
Do i really need to install all these programs in order to develop this database and game logic on my computer?
And should i create my 'world' database (SQL) with a PHP code?
If i write my code with Gedit, how can i check the output of my SQL and PHP, should i run it in Firefox? It can't be that simple, can it? 
(Oh! I felt comfortable with IDLE/Python and pressing F5 to see my code do its magic :) )

---

### Post by ad_267 on 2008-10-28
This page explains how to set up Apache/MySQL/PHP on Ubuntu: [http://howtoforge.com/ubuntu_lamp_for_newbies](http://howtoforge.com/ubuntu_lamp_for_newbies)

You can save your file in gedit and then browse to it in firefox to see the output. You don't have to create the database with PHP, usually PHP is used only for updating and getting data from the database. You can create the database from the MySQL command line interface or using a tool like phpMyAdmin which should be available in the repositories.

Maybe do some research on PHP before diving in, here's a good place to start: [http://en.wikipedia.org/wiki/PHP](http://en.wikipedia.org/wiki/PHP)

Oh and I should mention that you can also use Python for web development in the same way as you use PHP if you'd rather not learn a new language. Python also supports MySQL databases and works with Apache.

---

### Post by jesuisbenjamin on 2008-10-28
> **ad_267 said:**
> 
Oh and I should mention that you can also use Python for web development in the same way as you use PHP if you'd rather not learn a new language. Python also supports MySQL databases and works with Apache.

Ha, i know about Django. I'm also looking at it. The thing is i don't know to what extent i'll be able to implement graphics in the interface using Django.

Thanks for the links, i'll take a look at it and hope to feel less confused after reading it :oops:

---

### Post by ad_267 on 2008-10-28
What do you mean by implement graphics?

You can't use 3D or moving 2D graphics with a web application unless you use something like flash.

---

### Post by jesuisbenjamin on 2008-10-28
> **ad_267 said:**
> What do you mean by implement graphics?

You can't use 3D or moving 2D graphics with a web application unless you use something like flash.

Finally i get some information which seems to enlighten my path:
Can i not fully create a web application/program in one single languages?

[LIST=1]
[*]So there is a Server Application running the "site".
[*]The there is a SQL database on which my stats are waiting for action (run by the Server Application?)
[*]There is my code (python or php) which tells what the logic of web application is (ie. game rules).
[*]There is another code which provides a web page (xhtml)?
[*]And if there is some bit of animated graphics i add another code (flash)?
[/LIST]

This looks like a big soup to me.

I started with the idea i could do everything with Python ](*,)

---

### Post by ad_267 on 2008-10-28
Yeah I think that's how it would have to work if you wanted to make this a web application.

I didn't realise you wanted a game with interactive graphics. If you want that it might be better to do this a different way. You could make a client application that does all the graphics and things that communicates with another server application. I would have absolutely no idea how to go about doing this though.

Maybe someone else can enlighten us. This thread is kind of related: [http://ubuntuforums.org/showthread.php?t=916523](http://ubuntuforums.org/showthread.php?t=916523)

---

### Post by howlingmadhowie on 2008-10-28
if you want moving graphics in a web browser you can either use something horrible like flash or get to know javascript and svg. you won't get any 3d acceleration or that stuff out of it though. 

basically a web browser was initially intended to display static pages. the inclusion of javascript and svg means that you can generate and animate graphics, but don't imagine for a second you have the same level of graphical capability as a window on an x-server. it isn't even in the same ballpark. 

so basically, if (pretty primitive) animations would suffice, you can do these with javascript. this of course leaves you with a choice as to where you put the game logic, either in php/python on the server machine or in javascript in the client browser.

this link will get you started with the connection between php and mysql: [http://de.php.net/manual/en/book.mysql.php](http://de.php.net/manual/en/book.mysql.php)

---

### Post by howlingmadhowie on 2008-10-28
> **jesuisbenjamin said:**
> Hey there, i'm trying to dig into information about PHP and SQL, but the whole thing remains mysterious to me. I am advised to install Apache and all (LAMP or XAMP)
Do i really need to install all these programs in order to develop this database and game logic on my computer?
And should i create my 'world' database (SQL) with a PHP code?
If i write my code with Gedit, how can i check the output of my SQL and PHP, should i run it in Firefox? It can't be that simple, can it? 
(Oh! I felt comfortable with IDLE/Python and pressing F5 to see my code do its magic :) )

if you use apache to deliver the page it really is that easy. you just deploy the page and then call it. try the following:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install mysql-server php5-mysql apache2 libapache2-mod-php5

```

and then save the following as /var/www/index.php

```

<?php

echo "<h1>hello world!</h1>";
?>

```

then direct your browser to [http://localhost]("http://localhost")

you should see the world "hello world". if you don't, let me know :)

---

### Post by drubin on 2008-10-29
> **howlingmadhowie said:**
> the game logic should be in php. the database should be used to save game states and things like that.

what we have is something like this:

```

port=open_port()
until input=get_input(port): wait()
game_id=get_game_id(input)
state=mysql_load_state(game_id)
while action!=QUIT:
  process_action(action)
  get_next_action(port)
  state=update_state(state)
mysql_save_state(game_id, state)

```

With php and a web inviroment is it slightly more complicated then that, as most browsers will time out if the connection stays open for longer then 60seconds.

With php you would need to maintain non persistent connections to the database and server side script.


Game flow would be more like.
[LIST=1]
[*]Out put stuff to user
[*]User submits something to the server
[*]Server proccesses that result 
[*]Out put different stuff to user
[*]wait for user to re-submit stuff back.
[/LIST]

---

### Post by howlingmadhowie on 2008-10-29
> **drubin said:**
> With php and a web inviroment is it slightly more complicated then that, as most browsers will time out if the connection stays open for longer then 60seconds.


the browser never waits more than the processing time for an answer.

the important thing to be considered is where is state to be stored? as we have already discarded apache there are 3 possibilities: 

1/ solely in the mysql database. the client application (be it a browser or a dedicated client) just displays whatever the server application fetches from the database. problem here is bandwidth and (to a lesser extent) speed of sql queries.

2/ in the running php process. at the start the data is initialised (one php process per game). state is saved to the database at certain times (quiting the game or when the player selects save). bandwidth could be a problem here. server load could also get interesting if you have 100 different games going on at the same time.

3/ in the client application (my favorite). but now---if we're using a browser---we're talking about a pure javascript application (which is the future anyway).  state gets updated and transferred using ajax. mysql saves take place at certain defined times (i don't intend to save the whole state as cookies!)

---

### Post by jesuisbenjamin on 2008-10-29
Thanks guys, this is very cool. I'll need to digest all this information for now though :)
After looking at all this i'll bother you again i promise ;)

---

### Post by drubin on 2008-10-29
> **howlingmadhowie said:**
> the browser never waits more than the processing time for an answer.
Yes but most browsers would have a time out function if the took tooo long to load. (Thus the problem with a persistent connection 
> 
2/ in the running php process. at the start the data is initialised (one php process per game). state is saved to the database at certain times (quiting the game or when the player selects save). bandwidth could be a problem here. server load could also get interesting if you have 100 different games going on at the same time.

3/ in the client application (my favorite). but now---if we're using a browser---we're talking about a pure javascript application (which is the future anyway).  state gets updated and transferred using ajax. mysql saves take place at certain defined times (i don't intend to save the whole state as cookies!)

2) How is this even possible when php script runs ends, and a new one is created when a user clicks on another link? 

3) HUGE +1 for that. Take a look at the new web applications out there. Gmail was the first to pioneer this type of application and has grown in leaps and bounds(Take a look at the rest that followed)

---

### Post by jesuisbenjamin on 2008-10-31
> **howlingmadhowie said:**
> 

you should see the world "hello world". if you don't, let me know :)

[COLOR="Silver"]i don't :o[/COLOR] **correction**: it does work now.

So where should i start? What i mean to say is: SQL and PHP but both will interact right?
Should one start by writing a database with SQL or with the gamelogic/interface with PHP?
If i want to create a database, the size of which will be relative to the number of players 'joining the game' then i would have to start with PHP and then tell it to tell SQL to make a database?

If it were only about writing in one language i would sort of know what to do... but what bugs me the most is this: i can't grasp how two languages are communicating with each other...

---

