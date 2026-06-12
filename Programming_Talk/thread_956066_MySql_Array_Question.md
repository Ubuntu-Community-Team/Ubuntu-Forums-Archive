---
title: "MySql Array Question"
date: 2008-10-22
forum: Programming Talk
---

### Post by Black Mage on 2008-10-22
I am trying to figure out how to design a database and I have come across using arrays in mysql. Basically what I am trying to create is a field that can hold multiple values without limit. For example, a table is created like this:

Primary Key: User_ID
First_Name
Last_Name
Favorite_Movies[1...x]

The x represents any amount of favorite movies. So I was wondering would an array be the best way to store infinite number of someone's favorite movies? And this is a MySQL database.

---

### Post by billvb on 2008-10-22
> **Black Mage said:**
> I am trying to figure out how to design a database and I have come across using arrays in mysql. Basically what I am trying to create is a field that can hold multiple values without limit. For example, a table is created like this:

Primary Key: User_ID
First_Name
Last_Name
Favorite_Movies[1...x]

The x represents any amount of favorite movies. So I was wondering would an array be the best way to store infinite number of someone's favorite movies? And this is a MySQL database.

Suppose you want to search users by favorite movies?  You could probably do it but it would likely be pretty awkward.

Its better to make a new table, call it favorite_movies and have it pair a user_id with a movie title).  This is the relational database model and its very important to learn about.

Therefore, if you want to get all of a users favorite movies, the query looks like:
```

SELECT favorite_movies.movie_name from favorite_movies WHERE user_id = <id of user we want to find favorite movies of>
```

This query will return an list of movie names.

Alternatively:
```

SELECT userid FROM favorite_movies WHERE movie_name = 'batman'

```
to select users whose favorite movie is batman

---

### Post by kernelhaxor on 2008-10-23
> **billvb said:**
> Suppose you want to search users by favorite movies?  You could probably do it but it would likely be pretty awkward.

Its better to make a new table, call it favorite_movies and have it pair a user_id with a movie title).  This is the relational database model and its very important to learn about.

Therefore, if you want to get all of a users favorite movies, the query looks like:
```

SELECT favorite_movies.movie_name from favorite_movies WHERE user_id = <id of user we want to find favorite movies of>
```

This query will return an list of movie names.

Alternatively:
```

SELECT userid FROM favorite_movies WHERE movie_name = 'batman'

```
to select users whose favorite movie is batman

Thats the ideal solution!

While designing a database, you want to make sure your tables are 'flat' as you get a lot more control and flexibility over your data.

---

### Post by drubin on 2008-10-23
This is called [Data Base normalization]("http://en.wikipedia.org/wiki/Database_normalization")  Have a read through that it might help you on your path.

---

