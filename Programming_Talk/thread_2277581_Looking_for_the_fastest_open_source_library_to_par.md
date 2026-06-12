---
title: "Looking for the fastest open source library to parse CSV file in Java"
date: 2015-05-09
forum: Programming Talk
---

### Post by Jerry_Sivan on 2015-05-09
I would like to to read and process huge CSV files with millions of records, which we collected from the communications carriers' network.


Here is my logic as a simplified procedure:
1) Read the CSV file with FTP protocol
2) Parse the CSV file with my own logic, such as combination, duplicates deletion and so on.
3) Store the parsed data into the MySQL database.
4) Do analysis based on the MySQL database.
5) Generate report as Excel,PPT,Word.


Currently we are using the library JavaCSV, but it's not good enough for my project. The fastest library I could find recently is uniVocity-parsers at [https://github.com/uniVocity/univocity-parsers](https://github.com/uniVocity/univocity-parsers).


Do you have any other suggestion? Thanks.

---

### Post by Lars Noodén on 2015-05-09
My mysql is quite rusty but wouldn't step #2 be doable by and in MySQL itself?

[https://dev.mysql.com/doc/refman/5.5/en/load-data.html](https://dev.mysql.com/doc/refman/5.5/en/load-data.html)

---

