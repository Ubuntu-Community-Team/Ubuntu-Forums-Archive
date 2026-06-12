---
title: "database design suggestion"
date: 2009-01-23
forum: Programming Talk
---

### Post by sujoy on 2009-01-23
i need an entity's attribute to have multiple values. like say movie genre.
a movie can have multiple genre, a genre can be found in multiple movies, so whats the most efficient way to design the database for it?

i need to able to list all the genre given a movies name as well as list all the movies given the genre.

from what i understood, one way would be
to create a movie table, with id, name, year, director, etc.
to create a genre table with id, genre name.
and then,
to create another table with movie_id and genre_id.

is this an appropriate method of doing it? genre is just an example, directors, cast, alternate names, languages,..... many things will be multi valued for a movie db

---

### Post by pp. on 2009-01-23
> **sujoy said:**
> 
is this an appropriate method of doing it? 

Yes, that's the way it is done.

---

### Post by sujoy on 2009-01-23
> **pp. said:**
> Yes, that's the way it is done.

thank you. i wasnt sure, since i dont have much experience with databases

---

### Post by drumz on 2009-01-23
As pp. said, what you propose is the 'normal' way to handle this and the extra table is generally referred to as an 'association table' since it allows you to associate one or more records from one table with one or more records from another table (n -> n relation instead of the typical 1 -> n in a 'parent -> child' table setup.  'n' is a number, 1 or more indicating how many records in one table have a relation in another table.)

---

