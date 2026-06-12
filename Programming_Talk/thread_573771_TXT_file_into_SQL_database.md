---
title: "TXT file into SQL database"
date: 2007-10-12
forum: Programming Talk
---

### Post by TreeFinger on 2007-10-12
I was thinking tonight that I'd like to make a C++ program that will have the user enter multiple lines of input data. I would like to insert this data into an SQL database to perform queries on. I am guessing I would save input information from the program to a text file and then insert it into the database. Could anyone shed some light on how to go about doing this? If you know any good examples feel free to post :)

---

### Post by LaRoza on 2007-10-12
I never used C++ with MySQL, but I see no reason to use a text file for this. If you want an easier time with this, you can use a scripting language like Python or PHP. Both make databases easy to work with. I am not pushing another language, only telling what I use with MySQL. For more information, my wiki has plenty on MySQL and Python, and PHP (which works with MySQL by itself.

If the mysql libraries for C++ are anything like Python's, it should be easy, just store the input in a string, watch out for sql injection, and insert it into the database.

---

### Post by jayaramk on 2007-10-12
yah there's a solution to it.... if ur gonna use mysql then 

mysql employees <employee.txt -u username -p 

employees is the database name and the file name is employee.txt!!! username is ur username with which you would be logging into mysql........

before u do all this u must navigate to the path where the employee.txt is present in the terminal... and the proceed with the command given above!!!

---

