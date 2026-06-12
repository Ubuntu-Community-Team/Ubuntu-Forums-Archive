---
title: "Database rollback vs. export/import on Heroku"
date: 2020-04-10
forum: Programming Talk
---

### Post by Drone4four on 2020-04-10
In the [Heroku Postgres Data Safety and Continuous Protection]("https://devcenter.heroku.com/articles/heroku-postgres-data-safety-and-continuous-protection") doc, it says:

> All Heroku Postgres databases are protected through continuous physical backups. These backups can be retrieved through [Heroku Postgres Rollbacks]("https://devcenter.heroku.com/articles/heroku-postgres-rollback") on Standard and Premium tier databases. However, Hobby tier databases do not offer rollbacks.

I am using the Hobby tier. Does this mean I can’t restore a PG backup? Or as an alternative as described in [Importing and Exporting Heroku Postgres Databases]("https://devcenter.heroku.com/articles/heroku-postgres-import-export"), could I export a copy of my db to my local machine regularly and then in the case of data loss or error, I could just import (upload) it? 

What’s the difference between a database rollback compared to export/import anyways? I've read the documentation linked to above and I am having difficulty understanding the slight distinction.

---

