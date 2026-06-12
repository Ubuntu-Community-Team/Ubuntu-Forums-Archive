---
title: "Php Store Locator"
date: 2007-03-30
forum: Programming Talk
---

### Post by habtish on 2007-03-30
Hello Everyone, 

Let me start this post by saying that my expertise + experience in php amounts to 0.

At work, I have a .dbf (foxpro) database that has store information (store name,street,city,state,zip) of retailers that our displays are in. What I am trying to do is get some sort of store-locator script up on our website that queries the .dbf (which can be converted to a sql script if needed) and displays available displays for a given zip code.

I have been looking at some open source projects and my attempt to get one of them (googlestorelocator) to work has miserably failed.

How should I go about tackling this? Any advices, comments, anything is helpful.

I know I could have/should have posted this on a more php based forum, but I feel I am a part of this community and would like to see the kind of comments I get from the Ubuntu community first.

TIA

---

### Post by Mirrorball on 2007-03-30
I don't think PHP has a driver for a Foxpro database, therefore I would first install MySQL and transfer the data to it. Then I would learn PHP and a little SQL. It's not difficult if you already know other programming languages.

---

### Post by habtish on 2007-03-31
> **Mirrorball said:**
> I don't think PHP has a driver for a Foxpro database, therefore I would first install MySQL and transfer the data to it. Then I would learn PHP and a little SQL. It's not difficult if you already know other programming languages.

Yeah I uploaded the dbf as a.csv file onto my ubuntu box and imported that into sql.. but I didn't have any experience with SQL to be able to continue. I have followed a link on the forums here on how to start learning a programming language [I am not a programmer, granted I took VB and C++ in college, barely passed them ]

In theory, writing a php script to query the database should be simplistic i assume. Given my limited knowledge, I thought it be best to adopt a similar project rather than attempt to write the whole thing from scratch.

---

### Post by Mirrorball on 2007-03-31
It's very simple, but not so simple that you can do it with no knowledge of PHP and SQL. I'd either get someone to write the script for me or I'd take the time to learn PHP and SQL.

---

