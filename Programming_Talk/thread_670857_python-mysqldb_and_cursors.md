---
title: "python-mysqldb and cursors"
date: 2008-01-17
forum: Programming Talk
---

### Post by dcroxton on 2008-01-17
I am feeling like an idiot on this one, but I can't find the answer.  I can import MySQLdb (I've read threads about people who have problems), and I can open a connection.  BUT...my connection objects never have a cursor() method.  Everything I've read says that they should.  If they don't, that would be fine, but how would I create a cursor?  The query() method says to use cursor(), but there is none!

Sincerely,
Derek

---

### Post by ghostdog74 on 2008-01-17
show your code , if any

---

### Post by pmasiar on 2008-01-17
[ActiveState recipe](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/65235) shows proper usage. DB API is documented: [http://www.python.org/dev/peps/pep-0249/](http://www.python.org/dev/peps/pep-0249/)

[this page](http://dustman.net/andy/python/MySQLdb_obsolete/doc/MySQLdb-3.html#ss3.3) says that "MySQL does not support cursors". I use fetchone()/fetchall() row on executed statement.

---

### Post by btlee on 2008-01-18
here is my code.

#!/usr/bin/python
# coding=euc-kr

import MySQLdb, cgi

db = MySQLdb.connect (user = a.dbusername(), passwd = a.dbpasswd(), db = a.boardname())
c = db.cursor()
key = "%" + key_value + "%"
ref = compile("'")
key = ref.sub("\\'", key)
query = "SELECT no,date,title,author,journal,year,vol,page,spare3 FROM " + a.tablename() + " WHERE " + menu + " LIKE \'" + key + "\' ORDER BY no DESC"
c.execute (query)
k = c.fetchall()

In the above code, several lines were dropped out for my privacy.
Helps

---

### Post by RIchard James13 on 2008-01-18
[PHP]    def getDatabaseConnector(self):
        try:
            self.conn = MySQLdb.connect (host = self.txtDBComputer,
                                 user = self.txtUserName,
                                 passwd = self.txtPassword,
                                 db = self.txtDBName)
        except MySQLdb.Error, e:
            print "Error %d: %s" % (e.args[0], e.args[1])
            # TODO fix this so it does not dump the user out of the program
            sys.exit (1)

    def dropTable(self, txtTableName):
        if self.conn == None:
            getDatabaseConnector()
        cursor = self.conn.cursor()
        cursor.execute ("DROP TABLE IF EXISTS " + txtTableName)
        cursor.close()[/PHP]

This is some of my code. Definitely a cursor in there.

---

### Post by dcroxton on 2008-01-18
Wow, I got more responses to this one post than to my last 5 questions on Ubuntu forums. :)

I was using MySQLdb.connection(), not MySQLdb.connect().

Thanks for the help.  I told you all I was being stupid, I just couldn't figure it out!

Sincerely,
Derek

---

