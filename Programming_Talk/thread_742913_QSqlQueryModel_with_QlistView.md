---
title: "QSqlQueryModel with QlistView"
date: 2008-04-02
forum: Programming Talk
---

### Post by peterbrewer on 2008-04-02
Hi I am doing a database project as part of my uni course using SQLite, Python and PyQT.

One of the things I want to list all the items (only one column of) in a table  using QListView.

I have been using QSqlQueryModel to produce the model for QListView though it isn't working.

The code I am using to set up the model is:
```
        self.model = QSqlQueryModel
        self.model.setQuery("SELECT companyName FROM suppliers");
```

and it produces the following error:
> TypeError: first argument of unbound method QSqlQueryModel.setQuery() must be a QSqlQueryModel instance

Could anyone offer any suggestions on how to solve this or explain why this is happening.

Many thanks for any help.

---

