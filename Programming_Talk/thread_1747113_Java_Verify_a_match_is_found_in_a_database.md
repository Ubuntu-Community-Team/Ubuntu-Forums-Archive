---
title: "Java: Verify a match is found in a database?"
date: 2011-05-02
forum: Programming Talk
---

### Post by fallenshadow on 2011-05-02
With Java if I was to search a database with something like this:

> SELECT name FROM nameList WHERE name = (?)

How are you supposed to verify if something was found? I honestly have no idea and ive been thinking about this for a good bit.

---

### Post by hoboy on 2011-05-02
Well you need a java class to execute the sql command
here is a nice link

[http://en.wikipedia.org/wiki/Java_Database_Connectivity](http://en.wikipedia.org/wiki/Java_Database_Connectivity)

---

### Post by fallenshadow on 2011-05-02
Yes I have all the code for that done but I don't know how to find out if its found anything.

The above code is executed in a prepared statement.

---

### Post by PaulM1985 on 2011-05-02
Ok.  You read the link.  So... did you read the bit about ResultSets?

Paul

---

### Post by fallenshadow on 2011-05-02
Yeah and ive been trying to get it working all night!

I keep coming up against this error:

> Statement.executeUpdate() cannot be called with a statement that returns a ResultSet.

What does this mean in plain english? I have commented out everything to do with ResultSet, so I don't know how this error is happening! :mad:

---

### Post by r-senior on 2011-05-02
You need executeQuery to run a query that returns a result set. The executeUpdate method is for data manipulation - inserts, updates and deletes.

---

### Post by fallenshadow on 2011-05-03
Ok I got that fixed but the code to verify a match still does not work. Here is what I have so far for it:

[PHP] //TODO: Fix search and match code
 
 ResultSet result
        }
        catch ( Exception exception )//for closing
            {
                exception.printStackTrace();
            } // end catch[/PHP]

---

### Post by r-senior on 2011-05-03
Could you give us a clue? Any error messages?

In the meantime a couple of things I would say were issues:

```
infoTextArea.append( "resultSet.getObject(i)" );
```

This is just going to pass the literal string "resultSet.getObject(i)" to the append method. Are you trying to write a generic thing here, or can you simply get the columns from the result set and do something with them?

If your code throws an exception, your connections don't get closed. Better to put the closing of connections into the finally block of a try-catch-finally.

EDIT: Is this part of a reasonable size project? Will you be writing many more similar pieces of database access code?

---

### Post by fallenshadow on 2011-05-08
All I want is to be able to verify if an SQL statement found something or not. Like if something is found display a message to the user saying so.

Looking at that example it seems like alot of code and I wanted something more like 2-4 lines of code. I don't wanna throw in all that code just for something this small.

At this rate I might abandon the idea of user feedback.

I might be reusing code... I know you will probably suggest functions for them. Have no worries I will put them into functions later. :)

---

### Post by r-senior on 2011-05-08
> **fallenshadow said:**
> All I want is to be able to verify if an SQL statement found something or not. Like if something is found display a message to the user saying so.

Looking at that example it seems like alot of code and I wanted something more like 2-4 lines of code. I don't wanna throw in all that code just for something this small.

At this rate I might abandon the idea of user feedback.

I might be reusing code... I know you will probably suggest functions for them. Have no worries I will put them into functions later. :)
I wasn't going to lecture you about reusing code ;). If there was justification I was going to suggest using Spring JDBC templates. You are absolutely right, there is a lot of code to do something simple, but that's JDBC for you. The Spring JDBC templates were created to remove the need for repetitive JDBC coding.

As an example, here is a snippet from a web service demo I wrote recently. It does essentially what you are trying to do. Not production code and I've cut some corners but it's the principle that I'm trying to show you.:

```

public void createEnrollment(Enrollment e) throws EnrollmentException {

        boolean alreadyEnrolled = 0 < getJdbcTemplate().queryForInt(
	    "SELECT COUNT(*) from ENROLLMENTS "
	+   "WHERE STUDENT_NAME = '" + e.getEnrollee().getName() + "' "
	+   "AND COURSE_TITLE = '" + e.getCourseTitle() + "'"
	);

	if (alreadyEnrolled) {
	    throw new EnrollmentException("You are already enrolled for this course");
	}

        ...

    }

```

I'm not hiding anything from you here. It really is this simple and elegant. All the exception handling and result set processing noise is gone (but the exceptions are still handled).

---

### Post by fallenshadow on 2011-05-12
Fixed it myself! :)

---

