---
title: "Linux as &quot;database&quot; server"
date: 2010-07-28
forum: Programming Talk
---

### Post by rensell on 2010-07-28
Good evening everyone. In my office we use software I have written using VB.net which run on our desktop\laptops running windows. I recently converted our file and print server over to linux. It's actually running Ubuntu 10.04. I completed this transfer after changing my home server to Ubuntu.

My primary reason is costs with running Microsoft Servers. The software we run now stores data in Access databases that are stored on the Linux server and runs just fine, but we are "outgrowing" the Access databases - primarily more users connected simultaneously.

My reason for writing tonight is to ask about "porting" an SQL database to my Linux server or is there a sql server application for Linux? I used Access on my desktop to create the DB and moved it to a shared folder on my Linux server, and was wondering if I could do the same for an SQL Database, but I'm currently still researching SQL database(s). Thank you for any input, I appreciate it very much.

-R

---

### Post by jeffathehutt on 2010-07-28
Though I don't know about your specific situation (I know nothing about access), there are many SQL database servers for linux.  mysql, postgresql, and sqlite are some of the more popular ones.  You can find them in the repositories and see if any will fit your needs.:)

---

### Post by lavinog on 2010-07-29
It has been a while since I have messed with access, but I am almost certain that you can connect to a mysql database with access.

---

### Post by v1ad on 2010-07-29
it should be pretty simple. mysql is great for the linux platform. didn't have much experience with it so can't provide much input.

---

### Post by Some Penguin on 2010-07-29
You normally don't port databases as-is because different databases have different formats.

That said, you may be able to coax a SQL dump out of Access which you could then invoke on a MySQL or PostgreSQL server after you've set up the schema. 

Personally I find MySQL slightly friendlier to use in certain aspects (notably, PostgreSQL <= 8.4 does not have an "INSERT OR UPDATE" command, and tends to lack the "DELETE ... CASCADE" idiom)... but MySQL has had some significant quality issues, and it's not obvious to me that Oracle has much of interest in helping MySQL development.

PostgreSQL is not terribly friendly (although much friendlier than Oracle, from what I hear), but is pretty reliable.

Both MySQL and PostgreSQL are pretty common.  So is Oracle, for those willing to pay.

[http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL](http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL)

---

### Post by kalaharix on 2010-07-29
BTW: "...there are many SQL database servers for linux. mysql, postgresql, and sqlite..." Sqlite is not server based and is single user.

I can't comment on vb.net using mySQL but I have converted Access databases to mySQL. You just won't believe the difference in speed. I am continually amazed at the speed with which mySQL can find text in a large string field in a large database. It is just awesome.

I output the Access table as csv and then (for e.g) used the following Gambas code to write to mySQL. You could do the same in any programming language (even Python :p)

```

' Gambas class file
PRIVATE hFileIn AS File
PRIVATE sLine AS String
PUBLIC conn AS NEW Connection

'-------------------------------------------------------
PUBLIC SUB Form_Open()
    WITH conn
      .Type = "mysql"
      .Host = "localhost"
      .Login = "root"
      .Password = "fred"
      .Name = "stock"
  END WITH
  TRY conn.Open
  IF ERROR THEN 
    PRINT "can't open mySQL : "; Error.Text
  ENDIF 
  
END 
'-------------------------------------------------------

PUBLIC SUB btnSupCap_Click()
  DIM spl AS String[]
  DIM j AS Integer
  DIM sql AS String
    
  hFileIn = OPEN "/home/charles/grn/acct97Supplier.csv"
  WHILE NOT Eof(hFileIn)
    LINE INPUT #hFileIn, sLine
    spl = Split(sline,"|")
    sql = "insert into supplier (su_code,su_name,su_closedate,su_dayscredit,su_datedue,su_parent) values ('"
    j = 0
    FOR EACH spl
      sql = sql & spl[j] & "','"
      j = j + 1
    NEXT
    sql = Left(sql, Len(sql) - 2) & ")"
  conn.Exec(sql)
  WEND 
END
'-------------------------------------------------------

```

The csv was produced using an unusual symbol like '|' as separator because one of my descriptive fields had accumulated apostrophes and commas whhich had to be stripped out before forming the sql statement.

---

### Post by rensell on 2010-07-29
Thank you for all the input. Since the first response, I've "played" with a couple options. I first tried postgresql, but didn't like the "commands" that were being used in VB. I then DL'd mySQL and installed it on my laptop (that I use VB on) and it's worked out nicely. I turned off my linux server and booting into my old xp "server" and have set up simple databases to test out VB coding using SQL instead of OLEDB. So far, I'm liking it. 

One thing I did notice, though, is that mysql requires a UN and PW to connect to databases, which could essential bypass my entire login codes in the program, except that I store user information, Name, Phone Number, Various settings, etc. in a table and then test their entry against my table - I've created the table in mySQL, but I must add the users to the mySQL server (I'm using mySQL Workbench) - I'm wondering if anyone knows how (or a place to point me) a way to add users to mysql server via VB program. Because at the moment, When I click "add user" in my program it simply adds a new record to my credentials table. I'd like to continue doing that AND add the user to sql server. Any ideas?

Ray

---

### Post by phrostbyte on 2010-07-29
It's incredibly bad design to have fat client applications point directly to DBs, especially if you use custom authentication. What you should do is expose a service. Look up "service oriented architecture".

---

### Post by rensell on 2010-07-29
phrostbyte,
I've read briefly into service oriented architecture, but not quite sure I understand what it is and how it would apply to my situation.

---

### Post by Some Penguin on 2010-07-29
Exposing a database service directly tends to be extremely brittle (e.g. clients may stop working if you change table layouts or switch machines; these things should really be abstracted) and can be harder to secure (compared to having an intermediate layer which is the only system authorized to interact with the db, and which runs sanity-checking et al on your queries).

---

### Post by phrostbyte on 2010-07-29
I would expose the database through a DAO (data access object). Sometimes this is called a repository object. Then the actions on the business logic (fancy way to say "code that sits in the middle of the GUI and DB") is exposed as service objects, which is exposed through one or more service facades (eg: REST web services). Your VB.NET app interacts with the service facade and not directly with the DB. 

This kind of architecture has a number of advantages 
[LIST=1]
[*] more secure, since you aren't giving users direct access to a DB it is less likely they can screw with what's in it
[*] more maintainable, since there is a separation of concerns, parts can be rewritten without effecting code that exists in other layers
[*] flexibility, should you want to change DB schemas in the future it is trivial if you abstract the database schema from the code that acts on data, and almost impossible if you don't
[/LIST]

---

