---
title: "Layout problem and some sql questions!"
date: 2007-03-07
forum: Programming Talk
---

### Post by jinxen on 2007-03-07
[Java programming]

Hi! **My first question** lies in the layout section. When i add components to a Container like this one.

```

Container regWinCont = regWin.getContentPane();
regWinCont.setLayout(new GridBagLayout());
GridBagConstraints g1 = new GridBagConstraints();

```

And then add for example a textfield. like this.

g2.gridx = 0;
g2.gridy = 1;
regWinCont.add(nameTxt. g2);

And so on.. My question is, how do i get them aligned to the left? Instead of now when they are aligned to the center. It all looks weird if a got textfields with diffrent lenghts :)

My **second question** is about sql (postgresql). How do i in java do for example. I want so do a search. select name, publischer from people. And if someone types in the name 'Tommy' in a textfield i would like my program to search a sql database and show the answers in a result field of some kind. How do i do that?

Im thankful for any answers!

Cheers, Tommy

---

### Post by treak007 on 2007-03-07
For your second question, java has the JDBC, which stands for java database connection interface. Look in java.sql . This contains support for ResultSets, Statements and Prepared Statements. What you could do is create a prepared statement and then insert the variables for the information into the prepared statement. You could also just create a string of the sql query by using the string + operator. For example:
```

ResultSet answer = <connection_variable>.execute("SELECT * from + table_name + " where" + <other stuff>);

```
You will store the result of executing that query as a ResultSet variable. The ResultSet class has methods to retrieve the information from the results of the query.

---

### Post by jinxen on 2007-03-07
yes, jdbc i know and i am using it (at school). Ok, i will try that. That sound great! Thanks for the help! If anyone know the answer to question 1, please don't be scared ;)

---

### Post by jinxen on 2007-03-07
i solved the problem to question 1.

g1.anchor = GridBagConstraints.NORTHWEST;

and g1 is a GridBagConstraints object.

Cheers

---

