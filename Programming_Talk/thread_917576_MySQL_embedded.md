---
title: "MySQL embedded"
date: 2008-09-12
forum: Programming Talk
---

### Post by pshah.mumbai on 2008-09-12
For those who want to install the embedded mysql database in their software, you need to install the "libmysqlclient15-dev" package

Its install the library at the following place :

/usr/lib/mysql/libmysqld.a

I will keep this post update on how to get QT working with embedded mysql for reference in future.

:)

---

### Post by cb951303 on 2008-09-12
nice thread. however sqlite is better than mysql almost in every aspect when it comes to the embedded database solutions :popcorn:

---

### Post by stevescripts on 2008-09-12
> **cb951303 said:**
> nice thread. however sqlite is better than mysql almost in every aspect when it comes to the embedded database solutions :popcorn:

+1 (big time ;) )

Steve

---

### Post by tinny on 2008-09-12
> **cb951303 said:**
> nice thread. however sqlite is better than mysql almost in every aspect when it comes to the embedded database solutions :popcorn:

Ummm... continue please...

You cant just say these things and then assume that it becomes the truth. Back it up.

---

### Post by LaRoza on 2008-09-12
> **tinny said:**
> Ummm... continue please...

You cant just say these things and then assume that it becomes the truth. Back it up.

sqlite is a C library that is very easy to use with little overhead. MySQL is a database server.

What do you think is best for embedding?

---

### Post by tinny on 2008-09-12
I once looked at using MySQL embedded for a Java desktop application. This was a commercial application and we discovered that using MySQL embedded would cost us 15% of the per until price of each application we sold.

E.g If we sold the software for $100 we would have to give MySQL AB $15.

We ended up using Java DB (Derby DB).

Always read the fine print.

---

### Post by tinny on 2008-09-12
> **LaRoza said:**
> sqlite is a C library that is very easy to use with little overhead. MySQL is a database server.

What do you think is best for embedding?

Thank you. I just get frustrated with factless posts.


sqlite, hypersonic, Derby DB etc.... Are all better than MySQL for this. MySQL is about 50MB installed, right? Derby DB is about 2MB.

---

### Post by mike_g on 2008-09-12
SQLite is very nice, easy to use and small; the .so is around 250K and it does all you would expect for a small db. Its completely free too apparently:
[http://www.sqlite.org/copyright.html](http://www.sqlite.org/copyright.html)

---

### Post by LaRoza on 2008-09-12
> **tinny said:**
> Thank you. I just get frustrated with factless posts.

Why? What evidence is there?

> 
sqlite, hypersonic, Derby DB etc.... Are all better than MySQL for this. MySQL is about 50MB installed, right? Derby DB is about 2MB.
MySQL is just too much, no matter its size. It is a server and multiuser.

Is this Derby DB available for more than one language/platform?

---

### Post by tinny on 2008-09-12
> **LaRoza said:**
> Why? What evidence is there?


:lolflag: I have a bruise on my head from hitting it against a wall. 

> **LaRoza said:**
> 
MySQL is just too much, no matter its size. It is a server and multiuser.


Yep. The only reason we even considered it was for political reasons. (The "manager" had heard of this thing called MySQL)

> **LaRoza said:**
> 
Is this Derby DB available for more than one language/platform?

FYI
Derby DB is written in 100% Java. So if you want to include it in your Java projects you just import a Jar file etc..

Not sure about other languages. Derby can run in server mode so I guess anything could connect to it.
E.g
[http://www-128.ibm.com/developerworks/db2/library/techarticle/dm-0505gibson/](http://www-128.ibm.com/developerworks/db2/library/techarticle/dm-0505gibson/)

EDIT: Before anyone jumps on the "J" word, im not saying that Java + Derby is the best setup.

---

### Post by cb951303 on 2008-09-12
> **tinny said:**
> You cant just say these things and then assume that it becomes the truth. Back it up. 
...I just get frustrated with factless posts.

actually the post doesn't need to be backed up. mysql and sqlite has different objectives thus there is no point in trying to prove that sqlite is better than mysql in its own area which is 'embedded databases'. 

don't be a fanboy. we all use mysql, there is nothing wrong with it. are you satisfied :lolflag:

---

### Post by tinny on 2008-09-12
> **cb951303 said:**
> actually the post doesn't need to be backed up. mysql and sqlite has different objectives thus there is no point in trying to prove that sqlite is better than mysql in its own area which is 'embedded databases'. 

Thats more like it :)

> **cb951303 said:**
> 
don't be a fanboy. we all use mysql, there is nothing wrong with it. are you satisfied :lolflag:
:confused: fanboy?

Maybe you should read all of the thread. ;)

---

### Post by drubin on 2008-09-12
> **tinny said:**
> Thank you. I just get frustrated with factless posts.


sqlite, hypersonic, Derby DB etc.... Are all better than MySQL for this. MySQL is about 50MB installed, right? Derby DB is about 2MB.

tinny Have you ever used [hsqldb]("http://hsqldb.org/") I find it easy to used simple and very light weight handles nicely with upto 50k rows per table. (That is all the project required).

---

### Post by tinny on 2008-09-12
> **rubinboy said:**
> tinny Have you ever used [hsqldb]("http://hsqldb.org/") I find it easy to used simple and very light weight handles nicely with upto 50k rows per table. (That is all the project required).

Yep, its very good. When developing web apps I use it for a local build environment with Maven. (Jetty + hsqldb) I haven't tried embedding it...

BTW: hsqldb is the new name for hypersonic. (I think)

---

### Post by drubin on 2008-09-13
> **tinny said:**
> Yep, its very good. When developing web apps I use it for a local build environment with Maven. (Jetty + hsqldb) I haven't tried embedding it...

BTW: hsqldb is the new name for hypersonic. (I think)

When ever I develop smallish desktop apps in java I use it as my DB engine pretty small light weight and FAST! also no server software needed.

---

### Post by mikejg on 2009-05-03
hello i try writing a programm which uses mysql embedded like amarok 2. The system ist kubuntu 9.04 and libmysqlclient16-dev. After compiling i get the first warning

/usr/lib/mysql/libmysqld.a(ssl.o): In function `yaSSL::read_file(yaSSL::SSL_CTX*, char const*, int, yaSSL::CertType)':
(.text+0x2191): warning: memset used with constant zero length parameter; this could be due to transposed parameters

the programm stops with a segfault because init_server_mysql returns != 0;

here ist the code

static char *server_options[] = { "mysql_test",
                                  "--defaults-file=/home/drue/amarok/my.cnf",
                                  "--loose-skip-innodb",
                                  "--datadir=/home/drue/amarok/mysqle" };
int num_elements = sizeof(server_options)/ sizeof(char *);

static char *server_groups[] = { "libmysqld_server", "libmysqld_client" };

int main(void)
{
   mysql_server_init(num_elements, server_options, server_groups);
   mysql = mysql_init(NULL);
   mysql_options(mysql, MYSQL_READ_DEFAULT_GROUP, "libmysqld_client");
   mysql_options(mysql, MYSQL_OPT_USE_EMBEDDED_CONNECTION, NULL);

   mysql_real_connect(mysql, NULL,NULL,NULL, "amarok", 0,NULL,0);

   mysql_query(mysql, "SELECT * FROM genres");

   results = mysql_store_result(mysql);

   while((record = mysql_fetch_row(results))) {
      printf("%s - %s \n", record[0], record[1]);
   }

   mysql_free_result(results);
   mysql_close(mysql);
   mysql_server_end();
   return 0;
}


for compiling i use

g++ test1_libmysqld.c -o test1_libmysqld -lcrypt -lz `/usr/bin/mysql_config --include --libmysqld-libs`

have any one an idea

thanks mike

---

