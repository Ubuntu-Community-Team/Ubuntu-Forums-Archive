---
title: "having trouble querying a table with two foreign key refering to the same column"
date: 2008-07-23
forum: Programming Talk
---

### Post by mohtasham1983 on 2008-07-23
Hi,

I have a table called matchResult whose structure is like this:

[PHP]
CREATE TABLE `matchResult` (
  `match_id` int(16) NOT NULL auto_increment,
  `team1` int(3) NOT NULL,
  `team2` int(3) NOT NULL,
  PRIMARY KEY  (`match_id`),
  KEY `team1` (`team1`),
  KEY `team2` (`team2`),
  CONSTRAINT `matchResult_ibfk_1` FOREIGN KEY (`team1`) REFERENCES `teams` (`team_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT `matchResult_ibfk_2` FOREIGN KEY (`team2`) REFERENCES `teams` (`team_id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci;
[/PHP]

As you can see, both team1 and team2 are foreign keys that refer to team_id in teams table.

The teams table structure is like this:

[PHP]
CREATE TABLE `teams` (
  `team_id` int(3) NOT NULL auto_increment,
  `team` varchar(60) collate utf8_unicode_ci NOT NULL,
  PRIMARY KEY  (`team_id`)
) ENGINE=InnoDB AUTO_INCREMENT=112 DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci;
[/PHP]

I'm trying to do a join query so that I can see something like this:

[PHP]
match_id       team1         team2
1              Arsenal       Man U
2              Chelsea       Milan
[/PHP]

I used:
[PHP]
(select m.match_id,t.team from teams t,matchResult m 
where m.team1=t.team_id) UNION (select m.match_id,t.team 
from teams t,matchResult m where m.team2=t.team_id);
[/PHP]

This lists everything in two columns and it's not what I'm looking for.

I'm wondering if it is possible to achieve what I'm looking for in mysql?

Thanks in advance,

---

### Post by pmasiar on 2008-07-23
> **mohtasham1983 said:**
> 
[PHP]
(select m.match_id,t.team from teams t,matchResult m 
where m.team1=t.team_id) UNION (select m.match_id,t.team 
from teams t,matchResult m where m.team2=t.team_id);
[/PHP]


You want those two teams to be independent? So use different aliases for them

[PHP]
select m.match_id,t1.team t2.team 
from teams t1, teams t2, matchResult m 
where m.team1=t1.team_id and m.team2=t2.team_id;
[/PHP]

---

### Post by mohtasham1983 on 2008-07-24
Thanks, I got it working.

---

