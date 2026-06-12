---
title: "Does anybody know ER-diagrams?"
date: 2007-06-19
forum: Programming Talk
---

### Post by jingo811 on 2007-06-19
Does anybody know ER-diagrams?  I've done some scribbles that I need some help with.  I want to create a voting system similar to that of Digg.com I just don't know how to fit it into the ER- and Relational-diagram.

Give me a sign and I'll juice up all the links to my sketches and notes!

---

### Post by Golyadkin on 2007-06-19
Yeah I know ERDs, let's see it :)

---

### Post by jingo811 on 2007-06-20
I want a vote system like Digg.com in my database.  Need help to put in the [COLOR="Red"]VOTE part[/COLOR] on the right spot in my **ER- and relational diagram** along with the right **Crows notation.**
Or maybe an explanation on how to think to accomplish this.
( I use PHP and MySQL. )

[SIZE="5"][COLOR="Purple"]**1.)** A picture of my **ER-diagram**:[/COLOR][/SIZE]
[IMG]http://tinypics.us/out.php/i5773_tutorials02.gif[/IMG]

[SIZE="5"][COLOR="Purple"]**2.) Vote printout**[/COLOR][/SIZE]
I want it so that only members can vote like how things work in Digg.com when you like or dislike a story.
The difference with my voting system is that I want to be able to get all the Positive and Negative votes and print it out and **calculate the difference** like so:
[IMG]http://tinypics.us/out.php/i5775_math02.gif[/IMG]
I just don't know what **Datatype** to use for this voting part and how to grab and sum up all the votes correctly?

[SIZE="5"][COLOR="Purple"]**3.)**Here's my **Relational diagram**[/COLOR][/SIZE]
[IMG]http://tinypics.us/out.php/i5776_relational01.gif[/IMG]

[SIZE="5"][COLOR="Purple"]**4.)**Picture of my **Link tables**:[/COLOR][/SIZE]
[IMG]http://tinypics.us/out.php/i5774_link01.gif[/IMG]

---

### Post by Golyadkin on 2007-06-20
I don't have much time so I will try to give you some quick help. I will try and help more later.

Okay, lets verbalize your ERD. Your notation is not entirely correct though. The crowsfoot should have a bar if it is "one or more" (looks like this:   --|<- ) and a circle if is it optional, thus "zero or more" (looks like this:   --O<-  )

[LIST]
[*]There are Tutorials, Topics, Categories, Members and Votes.
[*]A tutorial belongs to one category.
[*]A tutorial belongs to one topic.
[*]A tutorial has zero or more votes.
[*]A tutorial is written by zero or more members.
[*]A category can contain zero or more tutorials.
[*]A topic can contain zero or more tutorials.
[*]A vote belongs to one tutorial.
[*]A member can write zero or more tutorials.
[/LIST]

I assume the members are those people who have written the tutorials. 

I redrew a bit, but there still has to come a relationship between the Vote and Tutorial entities. You should decide what you want the relation to be.

[img]http://www.android42.net/got/Diagram1.png[/img]

Now what you want to do is make a "link" table for the voting, if you want to know who voted what, on which tutorial.

Like this:

```
Member <member> votes <vote> on tutorial <tutorial>. (optionally "on <date> <time> from ip address <ip>" so you can check that people don't vote twice)
```

Using three foreign keys. The datatype for vote should be INTEGER if you want people to be able to vote "+100" and "-5" and such. However, digg works with just +1 and -1, so you can also do this with a boolean "1" for a positive vote, and a "0" for a negative vote.

You can then use a simple SELECT query to get the positive and negative votes.
[php]
$positive = mysql_query("SELECT COUNT(`idVotes`) FROM `VotesByMembers` WHERE `vote` = 1;");
$negative = mysql_query("SELECT COUNT(`idVotes`) FROM `VotesByMembers` WHERE `vote` = 0;");
echo "$positive - $negative = " . $positive - negative;
[/PHP]

---

### Post by Golyadkin on 2007-06-20
Oh I just see I forgot the horizontal bars making it mandatory for tutorials to be in a category and topic. Well, this is stuff for you to decide.

Some info on crows foot notation: [http://www2.cs.uregina.ca/~bernatja/crowsfoot.html](http://www2.cs.uregina.ca/~bernatja/crowsfoot.html)

---

### Post by jingo811 on 2007-06-20
Tnx for the guidance I now have a destination.  But it's gonna take a while to melt all this info into my head so I'll be back after some weeks or months.  And ask more questions when I got a handle on the sitaution.

Tnx again you get a star from me :KS because you were quicker to respond than those guys at the Database forums ;)

---

### Post by Golyadkin on 2007-06-20
lol, thanks :) :D you are welcome

The most important thing is to write down what you really want, and the database design will come from that. Start small and expand the functionality later. 

When I started my Bookcase application, it only had books and authors. I expanded it later with publishers, categories and statistics modules.

---

### Post by jingo811 on 2007-06-20
OK it took me less time than weeks and months to raise question marks over my head.

[COLOR="Purple"]**1. First "link table"**[/COLOR]
Is it possible to have 2 "link tables" between 2 entities?
I previously already had a "link table relation" between **(Tutorials)+(Member)** which 
looked like this in order to SELECT the "Author(s)".
```

**(tutorials_member)**
tutorial_id
member_id AS **Author(s)**

```

[COLOR="Purple"]**2. Second "link table"**[/COLOR]
With your suggestion I'm re-using the relations between **(Tutorials)+(Member)** won't it in doing so make my database go crazy and meltdown?
Anyway my second "link table" between the 2 already used entities looks like this.
```
**(tutorials_member_vote)**
tutorial_id
member_id
vote_id
```

[COLOR="Purple"]**3.**[/COLOR]
Since I aliased my **member_id AS Author(s)** do I need to worry about the database not finding member_id in my second link table from **question 2**?

[COLOR="Purple"]**4. Regarding constraining votes from IPs**[/COLOR]
If I only allow 1 vote per IP won't I make a router shared internet household as 1 person which might consist of 4 living persons?
What's a good way to keep ppl from creating several accounts and use them to somewhat control voting.

---

### Post by Golyadkin on 2007-06-21
Some quick answers, will have more time in the weekend:

1. Yes, you can have as many link tables between two entities as you want.
2. You are not reusing a relation, you create another relation. One relation is the relation of being the author, the other relation is of being a voter. Your database knows the difference and everything will work fine. Think of it as the member playing several roles.
3. No need to worry, it is an alias, so you can use both names. However, I am not sure if MySQL likes the parentheses ( and ) in a fieldname. I would simply alias it as "author".
4. You can combine storing a cookie in the visitor's browser with storing the ip address and the code in that cookie into your database. Then when someone visits, you check if the cookie is there and if the ip is in the database, then do not allow voting. If you require members to be registered before they vote, it is super easy. Then all you need to do when checking to vote is do a "SELECT COUNT(member_id) FROM tutorials_member_vote WHERE member_id = 42 AND tutorial_id = 21"  where 42 is the current id of the logged in member and 21 the id of the current tutorial. If the result is larger than zero, that member already voted on that tutorial.

---

### Post by jingo811 on 2007-06-21
> "SELECT COUNT(member_id) FROM tutorials_member_vote WHERE member_id = 42 AND tutorial_id = 21" where 42 is the current id of the logged in member and 21 the id of the current tutorial. If the result is larger than zero, that member already voted on that tutorial.

Your advices is worth more than gold itself, can't wait to see what you're gonna add during the weekends.  In the meantime I'll try and script all the neccessary tables and data and test it in MySQL Query Browser to see if I can get a handle on this voting system.

---

### Post by Golyadkin on 2007-06-21
I can't add much more to those answers there, but in the weekend I have time to answer new questions you might have. Good luck and keep it simple in the beginning.

By the way, I don' t know how proficient you are in PHP, but I have learned everything from scratch from [these two books]("http://www.sitepoint.com/books/phpant1/?SID=af9156da6ea02c36f9dffd53fb44cdd4") and building that bookcase application based on it. You can download example chapters from that website.

---

### Post by jingo811 on 2007-06-22
>  	I can't add much more to those answers there, but in the weekend I have time to answer new questions you might have.
After your sound advices I don't think I'll ever have anymore questions :D at least for months that is.

> Good luck and keep it simple in the beginning.
Yeah I'll play with the functions in MySQL Query Browser and experiment from there.

> By the way, I don' t know how proficient you are in PHP, but I have learned everything from scratch from these two books and building that bookcase application based on it. You can download example chapters from that website.
Tnx for the tip!
It looks like a practical book.

---

### Post by Golyadkin on 2007-06-25
I played around a few minutes and made a simple data structure that will make it easy for you to start. You should be able to import this into a MySQL database and try your queries.

```

-- ----------------------------
-- Table structure for Member
-- ----------------------------
CREATE TABLE `Member` (
  `idMember` int(11) unsigned NOT NULL auto_increment,
  `name` varchar(32) NOT NULL,
  `passwd` varchar(255) NOT NULL,
  PRIMARY KEY  (`idMember`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

```
```

-- ----------------------------
-- Table structure for PlacedVotes
-- ----------------------------
CREATE TABLE `PlacedVotes` (
  `idPlacedVotes` int(10) unsigned NOT NULL auto_increment,
  `idMember` int(10) unsigned NOT NULL,
  `idTutorial` int(10) unsigned NOT NULL,
  `vote` enum('positive','neutral','negative') NOT NULL default 'neutral',
  PRIMARY KEY  (`idPlacedVotes`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

```
```

-- ----------------------------
-- Table structure for Tutorial
-- ----------------------------
CREATE TABLE `Tutorial` (
  `idTutorial` int(11) unsigned NOT NULL auto_increment,
  `title` varchar(255) NOT NULL,
  `link` mediumtext NOT NULL,
  `written` date NOT NULL,
  `updated` date default NULL,
  PRIMARY KEY  (`idTutorial`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

```
```

-- ----------------------------
-- Test Records 
-- ----------------------------
INSERT INTO `Member` VALUES ('0', 'jim', 'secret');
INSERT INTO `Member` VALUES ('1', 'tony', 'alsosecret');
INSERT INTO `Member` VALUES ('2', 'mike', 'hello');
INSERT INTO `Member` VALUES ('3', 'sandy', 'monkey');
INSERT INTO `Member` VALUES ('4', 'steve', 'flower');
INSERT INTO `PlacedVotes` VALUES ('1', '1', '1', 'positive');
INSERT INTO `PlacedVotes` VALUES ('2', '1', '2', 'positive');
INSERT INTO `PlacedVotes` VALUES ('3', '2', '1', 'positive');
INSERT INTO `PlacedVotes` VALUES ('4', '3', '3', 'negative');
INSERT INTO `PlacedVotes` VALUES ('5', '3', '2', 'negative');
INSERT INTO `PlacedVotes` VALUES ('6', '2', '3', 'positive');
INSERT INTO `Tutorial` VALUES ('1', 'Tutorial One', 'http://www.example.com/tutorial/1', '2007-06-04', '2007-06-07');
INSERT INTO `Tutorial` VALUES ('2', 'Tutorial Two', 'http://www.example.com/tutorial/2', '2007-06-11', '2007-06-15');
INSERT INTO `Tutorial` VALUES ('3', 'Tutorial Three', 'http://www.example.com/tutorial/3', '2007-06-10', null);
INSERT INTO `Tutorial` VALUES ('4', 'Tutorial Four', 'http://www.example.com/tutorial/4', '2007-05-08', '2007-05-26');

```

Hope this helps a little.

---

### Post by jingo811 on 2007-06-26
tnx. :p

---

### Post by wolfear on 2007-08-27
hi all.
I am not an expert in Mysql by any means so if I am way off base, forgive me and if you'll let me know the reasoning, maybe I'll learn something.
Only reason I even noticed was I am in process of planning a project where some of the components may be similar to this so it's on top of my brain.

[QUOTE=Golyadkin;2910473]
```

-- ----------------------------
-- Table structure for Member
-- ----------------------------
CREATE TABLE `Member` (
  `idMember` int(11) unsigned NOT NULL auto_increment,
  `name` varchar(32) NOT NULL,
  `passwd` varchar(255) NOT NULL,
  PRIMARY KEY  (`idMember`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

```

Why use int(255) for a password? I would think that even encrypted an int(32) would work.
```

-- ----------------------------
-- Table structure for PlacedVotes
-- ----------------------------
CREATE TABLE `PlacedVotes` (
  `idPlacedVotes` int(10) unsigned NOT NULL auto_increment,
  `idMember` int(10) unsigned NOT NULL,
  `idTutorial` int(10) unsigned NOT NULL,
  `vote` enum('positive','neutral','negative') NOT NULL default 'neutral',
  PRIMARY KEY  (`idPlacedVotes`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

```

I noticed that the "idMember" and "idTutorial" here is int(10) but it is int(11) in the other tables. Will this cause any problems?
Purely for my own information: would a key/value type table setup work or is the auto-incremented primary key required?
```

-- ----------------------------
-- Table structure for Tutorial
-- ----------------------------
CREATE TABLE `Tutorial` (
  `idTutorial` int(11) unsigned NOT NULL auto_increment,
  `title` varchar(255) NOT NULL,
  `link` mediumtext NOT NULL,
  `written` date NOT NULL,
  `updated` date default NULL,
  PRIMARY KEY  (`idTutorial`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

```
Would it be more efficient to have the "updated" field handled automatically by using "on update current_timestamp"?

I realize this is not a production copy of anything, I was just curious.
No offense or critisism(sp?) is intended.

---

### Post by jingo811 on 2007-08-28
Dunno your questions and observations are beyond my experience.  Besides I've been busy messing around with a login system ever since.....
so I have almost forgot about half of the stuff that Golyadkin explained to me :)

---

