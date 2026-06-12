---
title: "SQL - Using DISTINCT on a specific column instead of all columns"
date: 2008-10-17
forum: Programming Talk
---

### Post by pcman312 on 2008-10-17
I'm currently building a simple bulletin board (think phpBB) for a class project and I'm trying to get a list of all of the boards with the last post attached. However, in my sql call, I am ultimately getting a list of all of the posts under a given board. I could make a couple of sql calls to get this information, but I find it's much nicer if I make the sql do the work for me :p

I am using MSSQL (I don't know the version)

Here's my (asciified) DB:
```
Boards:
  id
  name
  description

Threads:
  id
  boardID -> boards.id

Posts:
  id
  threadID -> threads.id
  userID -> users.username
  subject
  message
  datetime
```

I have this sql call (created in Visual Studio):
```
SELECT     boards.name, boards.description, boards.id, posts.datetime, users.username
FROM         boards INNER JOIN
                      threads ON boards.id = threads.boardID INNER JOIN
                      posts ON threads.id = posts.threadID INNER JOIN
                      users ON posts.userID = users.username
ORDER BY boards.id, posts.datetime DESC
```

and I am receiving the following output (with dummy info):
```

	 DATETIME		 DESCRIPTION			 ID	 NAME		 USERNAME
1	 2008-08-02 20:00:00.0	 This is the general board	 1	 General	 jesse
2	 2008-08-02 19:00:00.0	 This is the general board	 1	 General	 pcman312
3	 2008-08-02 18:30:00.0	 This is the general board	 1	 General	 jesse
4	 2008-08-02 18:00:00.0	 This is the general board	 1	 General	 jesse
5	 2008-08-02 17:00:00.0	 This is the general board	 1	 General	 pcman312
6	 2008-08-03 14:00:00.0	 This is the support board. ...	 2	 Support	 jesse
7	 2008-08-03 13:00:00.0	 This is the support board. ...	 2	 Support	 pcman312
```

but I want it to come out to be like this:
```

	 DATETIME		 DESCRIPTION			 ID	 NAME		 USERNAME
1	 2008-08-02 20:00:00.0	 This is the general board	 1	 General	 jesse
2	 2008-08-03 14:00:00.0	 This is the support board. ...	 2	 Support	 jesse
```

Any help would be greatly appreciated.

---

### Post by pp. on 2008-10-17
My SQL has become a bit rusty. However, I would suggest to have a look into aggregate functions (such as max).

---

