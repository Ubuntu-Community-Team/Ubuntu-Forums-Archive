---
title: "questions about mysql..."
date: 2006-04-14
forum: Programming Talk
---

### Post by orlox on 2006-04-14
I haven't been able to answer myself this questions on mysql...

1._How to delete a database?
2._how to delete a table?
3._When using a text file to insert rows to a table, how can I specify the NULL values?

Can anyone answer this to me?

---

### Post by txinga on 2006-04-14
I know you need phpmyadmin to do it quickly. It's available in Synaptic. Doing it from command line would be painful. From a text file? Hmm... It's all in the line of text for the table insert command. mysql.org is chock full of information. Once you create the table from the text file you can see all of the parameters for the table with phpmyadmin. I would also look at phpmyadmin.net for more information. It's pretty straight forward once it's installed.

---

### Post by LordHunter317 on 2006-04-15
What version of MySQL?

In MySQL 5, you can drop a database with 'DROP DATABASE' if you are sufficently privileged.  In eariler versions, you must use mysqladmin on the command line.

In any reasonable SQL database, you drop tables via 'DROP TABLE', again, assuming sufficent privilege.

As for the third, it depends on the format of the file, MySQL can load several different formats.

---

