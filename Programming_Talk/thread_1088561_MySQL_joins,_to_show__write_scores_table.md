---
title: "MySQL joins, to show / write scores table"
date: 2009-03-06
forum: Programming Talk
---

### Post by null-cipher on 2009-03-06
I need a bit of help designing my database for my website.
I am looking to create a system where a user can log into my website, and submit the scores from the latest LAN.

So in presentation, the table would look something like:
[HTML]
<table>
  <tr>
     <th colspan="3">NAME OF GAME</th>
  </tr>
  <tr>
     <td>&nbsp;</td>
     <td>Player 1</td>
     <td>Player 2</td>
  </tr>
  <tr>
     <td>Frags:</td>
     <td>1</td>
     <td>3</td>
  </tr>
  <tr>
     <td>Deaths:</td>
     <td>3</td>
     <td>1</td>
  </tr>
</table>
[/HTML]
And for submission, I would have PHP output a form, where instead of values it would have input boxes (for the names of the players, their scores, and what type of score).

Does anybody have any idea for how I can pull this off? Because I am frankly at a loss!
Thanks in advance.

---

### Post by simeon87 on 2009-03-06
I'd say the following tables at minimum:

- players (each person involved)
- matches (contains all matches played, e.g. DeathMatch in UT at 11 pm, etc )
- matchstats (for each match, the statistics per player)

So the players table could contain the following columns:

- player_id
- name_of_player
- (other info per player)

Matches table:

- match_id
- name_of_game_played
- date
- (other info per match)

Match statistics table:
- match_id
- player_id
- frags
- deaths
- score
- (other stats per player per match)

The match statistics table would have foreign keys to the match_id in matches and player_id in players.

---

### Post by drubin on 2009-03-06
That being said this *could* be done in a single table but this 3 tables represents a DB in the 3rd normal form. Also this way is the prefered way of doing it.

This might be worth [reading]("http://en.wikipedia.org/wiki/Database_normalization") to explain why we would do this
and this [http://dev.mysql.com/tech-resources/articles/intro-to-normalization.html](http://dev.mysql.com/tech-resources/articles/intro-to-normalization.html)

---

### Post by null-cipher on 2009-03-06
I would certainly agree with normalising, I have been using MySQL (and SQLite to a lesser extent) but my prowess with SQL is still fairly limited.

Thanks for the suggestions!

---

### Post by drubin on 2009-03-06
> **null-cipher said:**
> I would certainly agree with normalising, I have been using MySQL (and SQLite to a lesser extent) but my prowess with SQL is still fairly limited.

Thanks for the suggestions!

once you get the hang of it, it is easy :) 

Do your self a favor and read up on Indexing. It will help you with db design. Because you base your design on the data you need to pull out. ie the queries.. when you know the queries you work out how you can index those queries to make it super fast and good.

If they don't index well then your DB design is not the greatest. Don't base your queries on your design but your design on your queries..

---

### Post by null-cipher on 2009-03-06
Sounds like solid advice to me! To be honest I'm only really starting out, and I do like learning these tips from people rather than books. :D

Also, could I trouble you to show me what a SELECT from the tables suggested above would look like? Still trying to wrap my head around it.

---

### Post by drubin on 2009-03-06
> **null-cipher said:**
> Sounds like solid advice to me! To be honest I'm only really starting out, and I do like learning these tips from people rather than books. :D

Also, could I trouble you to show me what a SELECT from the tables suggested above would look like? Still trying to wrap my head around it.

1) Learning from people is good. but doing is always the best. :)))
 	
>  players (each person involved)
- matches (contains all matches played, e.g. DeathMatch in UT at 11 pm, etc )
- matchstats (for each match, the statistics per player)

So the players table could contain the following columns:

- player_id
- name_of_player
- (other info per player)

Matches table:

- match_id
- name_of_game_played
- date
- (other info per match)

Match statistics table:
- match_id
- player_id
- frags
- deaths
- score
- (other stats per player per match)


[PHP]SELECT p.name_player,m.frags FROM players AS p INNER JOIN matches AS M (m.player_id=p.player_id) WHERE p.player_id=1[/PHP]

That should give you each plays name and their frags. Take a look athte manual for mysql joins it should be rather helpful. 

I haven't tested the above code in any way

---

### Post by null-cipher on 2009-03-06
Thanks a lot for your help! This is why I love open source, the community is just great.

I think I have SELECT-ing sorted now, but just to be more of a pain, do you have any pointers on getting my data into the "match statistics" table?
```

+-----------+---------+------+-----+---------+-------+
| Field     | Type    | Null | Key | Default | Extra |
+-----------+---------+------+-----+---------+-------+
| match_id  | int(11) | NO   | PRI | NULL    |       |
| player_id | int(11) | NO   | PRI | NULL    |       |
| frags     | int(5)  | YES  |     | NULL    |       |
| deaths    | int(5)  | YES  |     | NULL    |       |
+-----------+---------+------+-----+---------+-------+

```
That's a DESCRIBE of the table I'm using. The match_id and player_id columns refer to the appropriate keys in the other 2 tables.

---

