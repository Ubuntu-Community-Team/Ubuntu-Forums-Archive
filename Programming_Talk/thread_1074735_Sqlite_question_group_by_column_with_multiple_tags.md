---
title: "Sqlite question: group by column with multiple tags?"
date: 2009-02-19
forum: Programming Talk
---

### Post by Yuzem on 2009-02-19
Suppose that have 2 columns: folders and tags:
```
~/Music|classic,rock
~/Music|classic,rock
~/Pictures|art,photos
~/Pictures|art,photos
~/Pictures|art,photos
```

To know the folder count I do:
```
sqlite3 test.db  "select folder, count(folders) from t1 group by folder"
```
Returns:
```
~/Music|2
~/Pictures|3
```

How can I do the same for tags using only sqlite to get this:
```
art|3
classic|2
photos|3
rock|2
```

Another question, is there any way to get max count for all grouped columns in one single consult?
It should return something like this:
```
2|4
```
Meaning that the first column has 2 unique values (~/Music and ~/Pictures) and the second column has 4 (art, classic. photos and rock)

Many thanks in advance! :)

---

### Post by Yuzem on 2009-02-22
Maybe if I ask in a different way: What is the standard way of storing and counting tags with sqlite?

---

### Post by The Cog on 2009-02-23
I would not put multiple tags in one column. If it were arranged more like this:

```
~/Music|classic
~/Music|rock
~/Pictures|art
~/Pictures|photos
```
then you can do things like:
```
select folder, count(*) from t1 group by folder
select tag, count(*) as numfolders from t1 group by tag order by numfolders limit 1

```
The "limit 1" is mysql's way of getting just the first line. I don't know what the equivalent syntax for sqlite is.
I don't know how to get both maxes at once.

---

### Post by Yuzem on 2009-02-23
Thanks for the answer.
> **The Cog said:**
> I would not put multiple tags in one column.
Yes it seems that that is the way to do it, I have also asked [here]("http://www.nabble.com/Sqlite-question%3A-group-by-column-with-multiple-tags--td22153722.html#a22154607") and I got the same answer.

---

