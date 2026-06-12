---
title: "&quot;simple&quot; MySQL problem"
date: 2009-11-03
forum: Programming Talk
---

### Post by Sugz on 2009-11-03
Okay basically, im having a problem during the creation stage of one of my databases.

Basically I have one table (Table X) which contains two attributes, one primary key the other is not really relevant.

The other table (Table Y) Needs to be created from the contents of
Table X, however Table Y contains 3 attributes, one Primary and the other two Attr's contain either one of the the Primary keys from Table X

So.. I effectively want to create Table Y and from a result set of Table X cartesian joined with itself. with a unique attribute to identify each tuple, and two additional fields consisting of the Primary keys of Table X

I am using very small data sets, But I have already explored using CROSS joins, but ended up crashing my home server as a result

Any help will be greatly appreciated, and I apologise if my explanation is unclear.

**Edit on second thoughts here's a 'picture'
```

        Table X 
        Attr1(X_ID) Arrt2(Irrelevant)
           1            xxxxxxx
           2            xxxxxxx
           3            xxxxxxx

        Table Y
        Arrt1(ID)    Attr2(X_ID)    Attr3(X_ID)
            1              1                    2
            2              1                    3
            3              2                    1
            4              2                    3
            5              3                    1
            6              3                    2
```

*The above illustration, is a model of what I am having trouble creating (Table Y)

---

### Post by IllegalCharacter on 2009-11-04
This schema should work fine, and should work with just regular JOINs. What is the query you are trying to do?

---

