---
title: "Best way to do this?"
date: 2009-10-23
forum: Programming Talk
---

### Post by matmatmat on 2009-10-23
I'm thinking of a program that gets passed a file of data, eg:
```

Name Score
Bob 2
Mat 3
Jane 7

```
then makes a table like this:
```

|------------|
|Name |Score |
|-----|------|
|Bob  |2     |
|Mat  |3     |
|Jane |7     |
|------------|

```
the number of fields may be more than two.
My idea was:
```

get 1st line
scanf("%s", string);
int a = spaces_count(string);
a++;
if (a == 2){
    scanf("%s %s", num[0], num[1]);
}

```
Is there a better way?

---

### Post by MadCow108 on 2009-10-23
your solution will not work for arbitrary field numbers
better read the whole line and tokenize it using the field delimiter (see strtok)
or read single characters and check for the field delimiter to split fields

---

### Post by Can+~ on 2009-10-23
If you mean a "table" as in a relational-database table, you may consider parsing it with the database engine.

In MySQL: [http://dev.mysql.com/doc/refman/5.0/en/mysqlimport.html](http://dev.mysql.com/doc/refman/5.0/en/mysqlimport.html)

And if you still want to do it via an ad-hoc method, I would suggest using a scripting language.

---

