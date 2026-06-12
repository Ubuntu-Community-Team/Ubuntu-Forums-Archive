---
title: "SQL - user created SQL (java)"
date: 2010-02-19
forum: Programming Talk
---

### Post by JayKay3000 on 2010-02-19
Hi! This is a sample of part of a program that can take a user inputted SQL statement such as INSERT INTO tableName VALUES() or SELECT * FROM tableName

You can also get the application to run prepared sql statements.

Here is  that bit of code:

```
  public void executeSQL() {

	 String query = command.getText();
         String query1 = SELECT * FROM coresw01
	 
    if(query == null||query.length() == 0) {     // If there's nothing we are done
      return;
    }
    try {
    	//If query1 is typed then this statement will be executed.
      model.setResultSet(statement.executeQuery(query));	
  	//if set to query, all kinds of sql commands can be entered.
      status.setText("Resultset has " + model.getRowCount() + " rows.");
      System.out.println(status);
    } catch (SQLException sqle) {
      status.setText(sqle.getMessage());        // Display error message
    }
  }

```

The problem. I've been messing around trying to get full user input. I have 6 input boxes (for each db column) and i'm trying to get it to execute an insert query by simply typing the table name and the data.

Is this possible. I still have some ideas I can try but I was wondering if anyone can put me on the right track as i'm getting a bit narrow minded pawing over these 6 lines of code.

Thanks in advance for any tips or help or pointers in the right direction.

---

### Post by Some Penguin on 2010-02-19
> **JayKay3000 said:**
> Hi! This is a sample of part of a program that can take a user inputted SQL statement such as INSERT INTO tableName VALUES() or SELECT * FROM tableName

You can also get the application to run prepared sql statements.

Here is  that bit of code:

```
  public void executeSQL() {

     String query = command.getText();
         String query1 = SELECT * FROM coresw01

```

     
That's not valid Java.

> 
```

    if(query == null||query.length() == 0) {     // If there's nothing we are done
      return;
    }
    try {
        //If query1 is typed then this statement will be executed.
      model.setResultSet(statement.executeQuery(query));    
      //if set to query, all kinds of sql commands can be entered.
      status.setText("Resultset has " + model.getRowCount() + " rows.");
      System.out.println(status);
    } catch (SQLException sqle) {
      status.setText(sqle.getMessage());        // Display error message
    }
  }

```The problem. I've been messing around trying to get full user input. I have 6 input boxes (for each db column) and i'm trying to get it to execute an insert query by simply typing the table name and the data.

Is this possible. I still have some ideas I can try but I was wondering if anyone can put me on the right track as i'm getting a bit narrow minded pawing over these 6 lines of code.

Thanks in advance for any tips or help or pointers in the right direction.

Of course it's *possible -- *the database doesn't care how you created your queries, so long as they're correct SQL.   Just use a StringBuilder to create the query string, and execute it using a Statement.   That doesn't mean that it's actually advisable to do so.


[ttp://xkcd.com/327/](ttp://xkcd.com/327/)

---

### Post by JayKay3000 on 2010-02-20
Nevermind. haha, just as I was preparing a reply I got it to work. Not perfectly but does what I was trying to do.

Was having trouble with all in one statements

So Created two queries:
```
String query1a = "INSERT INTO " +item1.getText();
String query1b = "VALUES" +item2.getText();
``` 

Then just executed those queries:
```
model.setResultSet(statement.executeQuery(query1a + query1b));

```

This ofc only uses two of my input boxes item1 & item2 but it's a start.

At least you can now type the table and the data without having to think about what sql to put in.

Still can't belive it took me 2 days to work that out! I may still pass this bloody diss yet](*,)

Whenever I post on this forum I end up working my thing out by myself. :lolflag:

Thanks for the input anyway!

---

### Post by Some Penguin on 2010-02-20
I would really, really recommend that you throw some quoting around the user-supplied input.

Specifically:

Replace any occurrences of " in the user input with two double quotes "" (or disallow them entirely...)
Put quotes around the user input.

Otherwise, you're asking r an eventual "<table name>; UPDATE <table name> SET " etc.

---

