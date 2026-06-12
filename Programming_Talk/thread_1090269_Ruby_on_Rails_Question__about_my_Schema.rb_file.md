---
title: "Ruby on Rails Question : about my Schema.rb file"
date: 2009-03-08
forum: Programming Talk
---

### Post by thenetduck on 2009-03-08
Hi 

I am trying to change my schema.rb file so that I have different fields in my database. So I change it, save it then run "rake db:migrate" but it reverts my schema.rb file back, saving over the old stuff! Am I doing something wrong? 

The Net duck

---

### Post by Tibuda on 2009-03-08
If I'm not wrong, the schema.rb is auto-generated, so you have to edit the migrations definitions. If you want to add new columns to a table, you better create new migrations. Another option is migrate your DB to version 0 and migrate to last version again, but it will clear your database.

---

