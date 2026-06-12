---
title: "MySQL on delete cascade"
date: 2007-06-01
forum: Programming Talk
---

### Post by AZzKikR on 2007-06-01
Not sure whether this belongs in this forum, but here it goes.

I am writing my own 'blog' thang in JSP with MySQL. I have two tables:
[LIST]
[*]article
[*]commentary
[/LIST]

Commentary has a foreign key to article.id, and of course, when deleting one article, I want all it's comments deleted as well. I've tried to do it as follows:
```
create table article (
    id int not null auto_increment,
    title varchar(80) not null,
    subtitle varchar(80) not null,
    content text not null,
    author varchar(40) not null,
    time datetime not null,

    PRIMARY KEY (id)
);

create table commentary (
    id int not null auto_increment,
    article_id int not null,
    title varchar(30),
    content tinytext not null,
    author varchar(40) not null,
    email varchar(50),
    ip varchar(16) not null,
    time datetime not null,

    PRIMARY KEY (id),
    FOREIGN KEY (article_id)
        REFERENCES article(id)
        ON DELETE CASCADE
);
```

This is according to documentation if I am not mistaken (a poster on the MySQL website [also gives a sort of example like this]("http://dev.mysql.com/doc/refman/5.0/en/ansi-diff-foreign-keys.html")). 

However, when deleting article ID 1, refuses to delete all the comments with a foreign key to article id 1. The example of the guy posting that note also doesn't work. Anyone knows what's wrong in this picture?

---

### Post by winch on 2007-06-01
Make sure your tables are using the InnoDB storage engine.
[http://dev.mysql.com/doc/refman/5.0/en/innodb-overview.html](http://dev.mysql.com/doc/refman/5.0/en/innodb-overview.html)
[http://dev.mysql.com/doc/refman/5.0/en/using-innodb-tables.html](http://dev.mysql.com/doc/refman/5.0/en/using-innodb-tables.html)

---

### Post by AZzKikR on 2007-06-02
Hey man, thanks a lot for that hint. It worked. I haven't been into MySQL since 4.x or something, where using that engine wasn't explicitly needed, if I recall correctly...

Thanks again!

---

