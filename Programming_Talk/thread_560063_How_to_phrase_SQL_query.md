---
title: "How to phrase SQL query"
date: 2007-09-25
forum: Programming Talk
---

### Post by moshy on 2007-09-25
Basically in SQLite, I have two tables:
One is called alphabet and has one column called letter, with all the letters.
The other is called library and has a column called title, with various names.
I need a SELECT query that will return two columns, the first is the letter column and the second, is the number of items in title that start with each letter.

I can do this for only one letter
SELECT COUNT(title)
FROM library
WHERE title LIKE 'a%';

But to do this all at once would be great.

---

### Post by Compyx on 2007-09-26
I don't know about SQLite, but this works with MySQL:

```

SELECT alphabet.letter, COUNT( * )
FROM alphabet
INNER JOIN library ON LEFT( library.title, 1 ) = alphabet.letter
GROUP BY letter

```

---

### Post by moshy on 2007-09-26
Thanks!
It works in SQLite if you change LEFT( library.title, 1 ) to LOWER(SUBSTR(library.title, 1, 1))

---

