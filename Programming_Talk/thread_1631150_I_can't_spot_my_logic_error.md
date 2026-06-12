---
title: "I can't spot my logic error"
date: 2010-11-26
forum: Programming Talk
---

### Post by Uubnewb on 2010-11-26
Can someone please help me out, I can't seem to spot my logic error.  The method executes fine, but the loop only happens once.  Yet there is two items in the database that matches the criteria.

```
public List<monthlylogger.ProjectBean> getMyProjects(int employeeID) {
        List<monthlylogger.ProjectBean> myProjects = new ArrayList();

        try {
            String getInfo = ("SELECT * FROM tbl_time_logged WHERE fk_employee_id = " + employeeID);
            resultSet = statement.executeQuery(getInfo);

            while(resultSet.next()){
                int fkProjID = resultSet.getInt("fk_projects_id");
                myProjects.add(this.getProject(fkProjID));
            }

        } catch (SQLException ex) {
            this.errorReport("getMyProjects(): " + ex.getLocalizedMessage());
        }
        return myProjects;
    }
```

---

### Post by Arndt on 2010-11-26
> **Uubnewb said:**
> Can someone please help me out, I can't seem to spot my logic error.  The method executes fine, but the loop only happens once.  Yet there is two items in the database that matches the criteria.

```
public List<monthlylogger.ProjectBean> getMyProjects(int employeeID) {
        List<monthlylogger.ProjectBean> myProjects = new ArrayList();

        try {
            String getInfo = ("SELECT * FROM tbl_time_logged WHERE fk_employee_id = " + employeeID);
            resultSet = statement.executeQuery(getInfo);

            while(resultSet.next()){
                int fkProjID = resultSet.getInt("fk_projects_id");
                myProjects.add(this.getProject(fkProjID));
            }

        } catch (SQLException ex) {
            this.errorReport("getMyProjects(): " + ex.getLocalizedMessage());
        }
        return myProjects;
    }
```

I'm only guessing, but it can be the case that resultSet.next() not only tells whether there is a next set, but also selects it. So you never use the first set. In that case the loop can be structured like this:

```
while (1) {
   ...
   if (!resultSet.next()) break;
}
```

You could add some debug print statements to see whether this is the case.

But note that my suggestion fails if the set is empty; you should check for that first.

---

### Post by Uubnewb on 2010-11-26
You're right, resultSet.next() moves to the next record, and if the move was successful it returns true.  However, if I'm not mistaken, the ResultSet's initial position is before the first record.

That being said, I still tried the following code:
```

while (true) {
                if (resultSet.next()) {
                    int fkProjID = resultSet.getInt("fk_projects_id");
                    myProjects.add(this.getProject(fkProjID));
                }else{
                    break;
                }
            }

```

Unfortunately it yielded the same results.  I ran the SQL query in Navicat and got two records returned, so the query seems right.  I'm going to add some more sample data to see if the result changes.

---

### Post by Arndt on 2010-11-26
> **Uubnewb said:**
> You're right, resultSet.next() moves to the next record, and if the move was successful it returns true.  However, if I'm not mistaken, the ResultSet's initial position is before the first record.

That being said, I still tried the following code:
```

while (true) {
                if (resultSet.next()) {
                    int fkProjID = resultSet.getInt("fk_projects_id");
                    myProjects.add(this.getProject(fkProjID));
                }else{
                    break;
                }
            }

```

Unfortunately it yielded the same results.  I ran the SQL query in Navicat and got two records returned, so the query seems right.  I'm going to add some more sample data to see if the result changes.

I meant the test to be at the end of the loop, and ... meant whatever you want to do with the set in the loop.

---

### Post by Uubnewb on 2010-11-26
OK, I added some more sample data.  I ran the query again and got five results.  However, when I ran my program, I still only got one result.

Anything specific I can print out to help find the problem?

---

### Post by Uubnewb on 2010-11-26
> I meant the test to be at the end of the loop, and ... meant whatever you want to do with the set in the loop. 

Oh!  Like a do...while?  I'll give it a try quick.

---

### Post by Uubnewb on 2010-11-26
The do...while loop wielded no results at all.  It seems that for some reason resultSet contains only one record, but for the life of me, I can't figure out why.

---

### Post by Arndt on 2010-11-26
> **Uubnewb said:**
> The do...while loop wielded no results at all.  It seems that for some reason resultSet contains only one record, but for the life of me, I can't figure out why.

So then you do need a next to get started, and your loop was correct to begin with, and my assumption was wrong.

Which entry do you get, out of the five you ought to get? The first, last?

---

### Post by PaulM1985 on 2010-11-26
I am guessing you are using Java.  From the API it says that next() "Moves the cursor froward one row from its current position".  So you will be skipping over the first record, so as you mentioned, I am assuming a do-while should work.

However, what happens if the result set is empty?  I don't know if you get functions will work as expected.  Would you call wasnull()?

This is just a suggestion that you may need to consider.

Paul

---

### Post by PaulM1985 on 2010-11-26
Just seen your post.  Call beforeFirst() on the ResultSet and use:
while(resultSet.next())
{
//doThings
}

beforeFirst() puts you to the start of the result set.

Does this work?

Paul

---

### Post by Uubnewb on 2010-11-26
Thanks for the help guys.  It turned out that my method call inside the loop (in bold text below) re-wrote my resultSet variable since I used the same variable name there.

```
String getInfo = ("SELECT fk_projects_id FROM tbl_time_logged WHERE fk_employee_id = " + employeeID);
            ResultSet res;
            Statement stat = dbConnect.createStatement();

            res = stat.executeQuery(getInfo);

            while (res.next()==true) {
                int fkProjID = res.getInt("fk_projects_id");
                myProjects.add(**this.getProject(fkProjID)**);
            }
```

> 
Which entry do you get, out of the five you ought to get? The first, last? 
I got the first record in the ResultSet.  

> However, what happens if the result set is empty? I don't know if you get functions will work as expected. Would you call wasnull()?
I'm not sure, but I think I'll get a NullPointerException.

> beforeFirst() puts you to the start of the result set.
Doesn't seem like it is neccesary.  I get all the records in the database so I guess the default position must be before the first record.  But I'll put it in anyway (if only for better coding technique).

Once again, thanks for all your help guys.  I really appreciate it.

PS: Sorry for my slow response.

---

### Post by Uubnewb on 2010-11-26
> **PaulM1985 said:**
> I am guessing you are using Java.
Oops, forgot to answer that one.  Yes, I'm using Java. :)

---

### Post by Some Penguin on 2010-11-27
Don't forget to close your Statement (which should also theoretically close the associated ResultSet -- but in practice, you can't necessarily rely on connection pools to properly implement this, so it would be safer to close the ResultSet as well).

If the ResultSet is empty, you're fine, because the next() will simply return false.  If the int value that you requested happens to be null (which might not be permissible; depends on the table definition), you'll get 0 back from the getInt() -- this is detectable via checking wasNull() immediately thereafter.  This is necessary because getInt returns a primitive int, and therefore /cannot/ return a null.

---

### Post by Uubnewb on 2010-11-27
> **Some Penguin said:**
> Don't forget to close your Statement (which should also theoretically close the associated ResultSet -- but in practice, you can't necessarily rely on connection pools to properly implement this, so it would be safer to close the ResultSet as well).

If the ResultSet is empty, you're fine, because the next() will simply return false.  If the int value that you requested happens to be null (which might not be permissible; depends on the table definition), you'll get 0 back from the getInt() -- this is detectable via checking wasNull() immediately thereafter.  This is necessary because getInt returns a primitive int, and therefore /cannot/ return a null.

Thanks for the tip.  I usually just close the connection since that should flag the resultSet and statement variables for garbage collection.  However, you might be right; to be on the save side I'll close them all at the end of the method.

As for the int value:  The table ensures that the value is not null, so I don't really have to worry about that.  The value should never be 0 either, so If push comes to shove I can always insert another check to see if the value is 0.

---

