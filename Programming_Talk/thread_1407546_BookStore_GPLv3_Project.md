---
title: "BookStore GPLv3 Project"
date: 2010-02-15
forum: Programming Talk
---

### Post by mihnea.radulescu on 2010-02-15
Hello everybody!

I have developed a digital book management application called BookStore, written in C# / .NET 2.0, that allows the user to store all of its' digital books (chm, html, doc, odf, pdf, rtf, txt, etc.) in a central single-file database repository, without the need to keep the books as individual files and folders on the disc, thus reducing disc fragmentation and easing content cohesion and portability (by copying the books database to a memory stick, for example).

The books to be imported can be either file-based books (such as a single pdf document) or folder-based books (such as a website offline copy). Books can be loaded one at a time or many-at-once (bulk-load). Once imported, each book can be visualized or deleted.

Each book stored in the system is characterized by 5 attributes: title, set of authors, set of tags, publishing house and year of publishing. Each of these attributes can be set for every book. The user can then query a particular set of books, based upon a combination of the aforementioned attributes. As such, the querying system is very powerful, while retaining its ease of use.

The application supports multi-user access on the same PC, as each user can have its own database, without any interference with the data of other users. Also, since the user is able to select the application's working folders, the solution can be run by any user, irrespective of its privileges on the system.

I would be very happy and grateful to receive any input on my application. Also, programmers are very welcome to contribute code, should they wish to. If you have any desire to do so, I can grant you access rights to the project and your contributions will be acknowledged on the project's page. For example, a Mono port would be very appreciated and not too difficult to achieve.


Project page : [http://code.google.com/p/bookstoredotnet/]("http://code.google.com/p/bookstoredotnet/")


Thank you for taking the time to read my post!

Yours truly,
Mihnea Radulescu

---

