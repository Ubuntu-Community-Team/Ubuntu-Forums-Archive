---
title: "mysql db creation for usage in rubyonrails in ubuntu"
date: 2010-06-23
forum: Programming Talk
---

### Post by railsfan on 2010-06-23
**Topic: mysql db creation for ruby on rails usage in ubuntu**
 
hi there
this is my first post. pardon me if there are any mistakes.
i have installed ubuntu 10.04 lucid
and rails 
here is the screen output from ubuntu (guest is ubuntu. host is winxp)
[EMAIL="root@ubu***-laptop:/home/myuser/www/myapp"]root@ubu***-laptop:/home/myuser/www/myapp[/EMAIL]# rails -v
Rails 2.3.8
[EMAIL="root@ubu***-laptop:/home/myuser/www/myapp"]root@ubu***-laptop:/home/myuser/www/myapp[/EMAIL]# ruby -v
ruby 1.8.7 (2010-01-10 patchlevel 249) [i486-linux]
i have also installed mysql.
I have installed mysql workbench to create mysql data model and to create mysql table creation scripts.
I prefer to generate db creation scripts this way so that i could keep them separate for design purposes.
here is the q.
would u recommend script/generate to generate tables in mysql or would u recommend this way of keeping the create tables script separate via anytool / text file.
thanks in advance.

---

### Post by hanniph on 2010-06-23
You should take a look at migrations. These are a very convenient way to specify your model structure. Migrations also lets you experiment because you can rollback to previous model versions and they are DB independent, so you're not bound to just MySQL (as with manual creation scripts). IMHO migrations are the way to go here :)

[PHP]
script/generate migration
[/PHP]


Check out [Rails guides]("http://guides.rubyonrails.org/migrations.html"), [docs]("http://api.rubyonrails.org/classes/ActiveRecord/Migration.html") and [some railscasts]("http://railscasts.com/episodes?search=migration") for a more detailed guidance

---

