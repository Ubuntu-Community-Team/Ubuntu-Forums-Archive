---
title: "Beginner: Download webpage + diff compare script?"
date: 2010-07-15
forum: Programming Talk
---

### Post by persofi on 2010-07-15
Hi,

I dont know any programming so I would really appreciate any help :) I want to write the following script for use in Ubuntu: (If possible in Python, because I like open-source)

(1) Download file "www.test.com/test.htm" into a folder called "Folder1" and name the file "abc.htm"

(2) Diffcompare(?) it to an existing file in "Folder2" which is also called "abc.htm".

(3) Write a report into a text file stating if the files are identical, or if there are differences. 

I guess this is not a very difficult script to write? Do you have any tips where I should look to get started?

If my explanations above arent too clear: The function of the script is to compare a larger number of legal statutes in .htm format saved on my hard drive to the recent version on the website I downloaded them from.
The "www.test.com/test.htm" adress never changes, but the content of the files might get updated.
There are about 80 different files, do I need to declare as many different variables?

---

### Post by diesch on 2010-07-15
The easies way is to write a shell script: Use *wget* to download the file and *diff * to compare it.

If you want to do it in Python have a look at *urllib2.urlopen()* for downloading. It returns a file-like object so you can use *.readline()* to read the content line-by-line and compre it with the stored file's content.

In both cases I'd use a map from URLs to stored files (if there'sno simple relation between them); in shell a file with tab separated values should do, in Python a dict is a natural choice.

---

