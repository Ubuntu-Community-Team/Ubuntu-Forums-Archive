---
title: "Large queries in libmysql-java"
date: 2007-08-22
forum: Programming Talk
---

### Post by apetresc on 2007-08-22
So here's the scenario. I'm writing a large-ish Java project which operates on a MySQL database. The actual operation of the program only requires it to perform the occasional small query ... an INSERT here, an UPDATE there, a SELECT or two. I have no problems running this part.

However, I would like to use JUnit to exercise this code, and in order to do that I need to create a temporary "test database", populate it with typical data, and run tests against it. So I laid out the test database and used mysqldump to produce the following SQL file:```
-- MySQL Administrator dump 1.4
--
-- ------------------------------------------------------
-- Server version	5.0.38-Ubuntu_0ubuntu1-log


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;

/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;


--
-- Create schema shogi_test_db
--

CREATE DATABASE IF NOT EXISTS shogi_test_db;
USE shogi_test_db;

DROP TABLE IF EXISTS `shogi_test_db`.`Users`;
CREATE TABLE  `shogi_test_db`.`Users` (
  `user_id` int(10) unsigned NOT NULL auto_increment,
  `user_name` varchar(25) character set utf8 NOT NULL,
  `user_password` varchar(25) character set ascii NOT NULL,
  PRIMARY KEY  (`user_id`,`user_name`)
) ENGINE=MyISAM AUTO_INCREMENT=2 DEFAULT CHARSET=latin1;
INSERT INTO `shogi_test_db`.`Users` (`user_id`,`user_name`,`user_password`) VALUES 
 (1,'admin','admin');



/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
```
In the JUnit code, I have the following setUp method:```
    protected void setUp() throws Exception {
        // Start connection and load schema
        
        BufferedReader in = new BufferedReader(new FileReader(new File(pathToTestSchema)));
        String sqlQuery = "";
        String line;
        while ((line = in.readLine()) != null) {
            sqlQuery += line + System.getProperty("line.separator");
        }
        System.out.println(sqlQuery);
        in.close();
        
        String dbUrl = "jdbc:mysql://" + dbHost + "/";
        
        Class.forName("com.mysql.jdbc.Driver").newInstance();
        Connection conn = DriverManager.getConnection(dbUrl, dbUser, dbPass);
        
        Statement stmt = conn.createStatement();
        boolean rc = stmt.execute(sqlQuery);
        
        conn.close();
    }
```
I know the sqlQuery is read correctly, thanks to the print, but running this test gives:
```
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '; /*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 S' at line 7.
```
Of course, the SQL syntax *isn't* incorrect (I can run it from a mysql prompt without any problems), and my guess is that Statement.execute() is only meant to operate on *single* statements, rather than a whole file of them.

My question then becomes, what part of the JDBC Connector library can I use to execute this entire file of queries wholesale into MySQL? I looked through the obvious parts of the library documentation, but found nothing obviously useful. I could use mysqldump or the prompt but I'd rather set it up straight from JUnit every time the test is run.

Any help would be appreciated :D Thanks.

---

### Post by kidders on 2007-08-23
Hi there,

Unit testing isn't really something that deserves a *huge* amount of time imo, so I would consider avoiding the issue altogether, rather than getting bogged down by it. For your purposes the "/* ... */" statements are  unimportant, as all they seem to do is preserve aspects of the server environment that may or may not (in your case "not" hehe, as far as I can tell) be changed by the intervening statements.

You should then be free to tokenise what's left by ';' (but *not* '\;'), and execute each statement sequentially.

[SIZE=1]Incidentally, on a completely unconnected subject, I notice that the repeated calls to System.getProperty("line.separator") are not necessary. Strictly speaking, even one of them is not required, since it's the server's line terminator that you'd be most interested in ... not the client's.
[/SIZE]

---

### Post by apetresc on 2007-08-23
> **kidders said:**
> Unit testing isn't really something that deserves a *huge* amount of time imo, so I would consider avoiding the issue altogether, rather than getting bogged down by it. 
Hehe, nevertheless it's something I'd rather not do without :)

> For your purposes the "/* ... */" statements are  unimportant, as all they seem to do is preserve aspects of the server environment that may or may not (in your case "not" hehe, as far as I can tell) be changed by the intervening statements.
The /* ... */ are not really a problem, if I tokenize by newlines, they are executed safely (albeit they do nothing). However, for example, the ```
--
-- Create schema shogi_test_db
--
```
lines DO cause problems, and although I can get around this manually, I can't help but think that if the mysql client can interpret them, these Java binding should be able to do it too.

> You should then be free to tokenise what's left by ';' (but *not* '\;'), and execute each statement sequentially.
I did it slightly differently, as follows:```
    protected void setUp() throws Exception {
        // Start connection and load schema
        
        String dbUrl = "jdbc:mysql://" + dbHost + "/";
        
        Class.forName("com.mysql.jdbc.Driver").newInstance();
        Connection conn = DriverManager.getConnection(dbUrl, dbUser, dbPass);
        Statement stmt = conn.createStatement();
        
        BufferedReader in = new BufferedReader(new FileReader(new File(pathToTestSchema)));
        String sqlQuery = "";
        while ((sqlQuery += in.readLine()) != null) {
            if (!sqlQuery.isEmpty()) {
                if (sqlQuery.endsWith(";")) {
                    stmt.execute(sqlQuery);
                    System.out.println(sqlQuery);
                    sqlQuery = "";
                } 
            }
        }
        
        in.close();
        conn.close();
    }
```
Except for the aforementioned lines that start with "---". Manually filtering that is too ugly. I'm sure there's got to be a way to make the bindings accept things the client would accept...

> [SIZE=1]Incidentally, on a completely unconnected subject, I notice that the repeated calls to System.getProperty("line.separator") are not necessary. Strictly speaking, even one of them is not required, since it's the server's line terminator that you'd be most interested in ... not the client's.
[/SIZE]
Hm, that's interesting. Wouldn't it be a safe assumption that the JDBC library would take care of low-level details like line endings? Which I guess makes my use of it unnecessary at worst, but hey, this is a Unit test, not exactly performance-critical :)

Thanks for your feedback so far!

---

### Post by kidders on 2007-08-23
Hmm...

Comments are something you *do* need line breaks for.

To be honest, I would have instinctively opted for a StreamTokenizer for this job. Alternatively, you could whip comments out with a regular expression, or an "if blah.startsWith()". It certainly seems strange that JDBC is objecting to them.

---

