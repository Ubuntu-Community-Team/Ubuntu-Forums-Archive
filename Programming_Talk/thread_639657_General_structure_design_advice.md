---
title: "General structure design advice"
date: 2007-12-13
forum: Programming Talk
---

### Post by sweRocker on 2007-12-13
Hi, 

I have some questions about database design!

This is what I would like my software to do when finished (se the** illustration** in the end of the post): 
[LIST=1]
[*]The user browses through a database of "example files" and selects the things he or she finds most interesting to learn. This will be the "user defined goal".
[*]The user opens the "course" and starts climbing through a "branch" of "nodes". It is not possible to skip one node, and as the user finishes one node, it changes color.
[*]Each node consists of several steps. Each such step contains a short piece of instructions and perhaps an image or a definition. 
[*]If something is unclear, the User simply writes a question which will then be sent to the author of the node. The answer will be posted in some forum or so. If it is a already answered question the user will be answered immediately. 
[/LIST]

Of course  I have no plans on doing all of this at the same time. My first step is to create a database where the tree structure is stored, including all the images, text and word definitions. 

I have some experience in Java, SQL and open-office database, but I have never really managed to integrated them all. So I thought I should start with the database. 

---> Right now I need some help with the database design. How shall I organize the data and its dependencies so that it will be possible to build the interface software in a simple way on top of it? Is my choice of variables good or should I add something?

**Attachment** (an illustration to all of this): [http://groups.google.com/group/anotherubuntustuffgoup/web/enbild.pdf](http://groups.google.com/group/anotherubuntustuffgoup/web/enbild.pdf)

---

### Post by aks44 on 2007-12-13
IMHO you may want to merge your 5 first tables into one, so that you can build a real tree :
```
Table tree
----------
id
parent (points to another tree.id, 0 if it is in the root)
name
ordr (order of the node inside the parent)
```

This way your tree can be any depth, instead of a fixed 5 levels (even though 5 levels make sense *now* you may want to change that later, this table structure allows that). Also, the leaf items (currently, Definition / Image / Text) are not restricted anymore to leaves, they can "cohabit" with other nodes at the same level.
You may also want to have an additional "type" field so that you can display each node in various ways.

I suggested the "ordr" field so that you can force the display order of nodes instead of relying on a sorting algorithm. But of course you can always decide that some nodes will be sorted by name, in which case you'd use the same order for every node (think about something like **ORDER BY ordr, name**).


Now when it comes to your 3 leaf items tables... I'm unsure whether they could be merged into 1 table or not. More info on that (point 3) would help. If each item will have *at most* *one* definition / image / text then you've got a winner (NULL is your friend :)).


Concerning your point 2, you'll have to make a table containing user / node associations, to be able to track who finished what (thus you'll also need a "users" table but I guess you already figured that ;)).

Point 4: in your "tree" table you'd have to store some info on the node's author (author id + separate authors table?). IMHO you'd be better off having a specific forum thread *per* tree node.


> If it is a already answered question the user will be answered immediately.Good luck with that, how are you gonna compare the user's (natural language) question with the ones already in the database? At best you can automate a search function, but don't expect too much here.


Hope this helps.

---

### Post by pmasiar on 2007-12-13
It is great idea, but it will be very hard to make it happen.

Mind you, not because of programming: because of need to provide original content. Who is going to write it? 
- You? Good luck with that, will take you years, and will be hard to match quality of other courses available for free. 
- Other people? But they already started, and have own websites. They might object you grabbing ("stealing") their content, they want you to link to them.

I recommend to solve different problem, which is more solvable: Get a wiki, collect links to good arrticles, write as much original content as you want, and let people comment on it and contribute. By the time you have enough links and articles for 5-10 "goals", you will be much better programmer than you are now (sorry but unlimited hierarchical tree is not that hard - you are not ready for coding yet).

Don't try to automate something which you cannot to do manually, you will fail. Also, don't build website in Java - in Python or Ruby it is ten times simpler, trust me.

You can get wiki for free, see wiki in my sig.

---

