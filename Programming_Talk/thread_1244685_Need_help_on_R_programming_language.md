---
title: "Need help on R programming language"
date: 2009-08-19
forum: Programming Talk
---

### Post by tezer on 2009-08-19
Hello
I am trying to do some simple calculations using this language (t-test for a number of vectors). But have some questions (don't know how to load labelled vectors to use the labels as variables).
Is there anyone who has some experience with R?
Or could you direct me to a forum where I can ask my questions?

Thanks.

---

### Post by LasherHN on 2009-08-19
If you have your data in a text file, for example a file named mydata.txt:

```
x y z
1 1 1
1 2 3
3 4 5
1 2 8
7 5 3
3 4 5
5 6 7
1 2 3
3 2 1
4 3 2
5 3 8
1 3 4
```

you can do in R the following command:
```
newdata=read.table('mydata.txt',header=T)
```

This will load your data into a data frame called newdata.

To do a t-test with the column of x, for example, you can do:
```
t.test(newdata$x)
```

Hope that helps, a site I sometimes use for help is [http://finzi.psych.upenn.edu/search.html](http://finzi.psych.upenn.edu/search.html)

---

### Post by tezer on 2009-08-19
Great! Thank you. But is it possible to do if my vectors do not have headers, but labels in the first column:

aaa 1, 2, 3, ...
bbb 4, 5, 6, ...

---

### Post by LasherHN on 2009-08-19
Well I look up a little bit the help on read.table and there I couldn't found a direct way to do it.

A work around that I can think of can be done if you have your file like

aaa, 1, 2, 3, ...
bbb, 4, 5, 6, ...

instead of

aaa 1, 2, 3, ...
bbb 4, 5, 6, ...

so you have your labels separated from your data.
If you can do that you can do the following:
```
newdata=read.table('datafile.txt',sep=",",row.names=1)
newdata=as.data.frame(t(newdata))
```

What this does is read the file using the first column as names, then t() calculates the transpose of a matrix (R converts the dataframe to a matrix) then as.data.frame will convert the transposed matrix to a dataframe again.

---

### Post by tezer on 2009-08-19
Thank you very much indeed!

---

### Post by rlzyoner on 2009-08-21
I've got to use R next year in college, can you guys point to any good resources for it ? 
I'm programming for a few years now but will be an R newbie
Cheers

---

