---
title: "What is wrong with this sql query?"
date: 2009-01-18
forum: Programming Talk
---

### Post by esafwan on 2009-01-18
This query is returning SQL syntax error.... mysql! its in gambas
Please help!
```

 sql = "insert into students( 'fname' ,'lname' ,'father' ,'mother' ,'guardian' ,'dob' ,'identity' ,'note1' ,'phone' ,'phone2' ,'mobile' ,'email' ,'address' ,'paddress' ,'adate' ,'agrade' ,'hobbies' ,'skills' ,'note2' ) values( 'fname' ,'lname' ,'father' ,'mother' ,'guardian' ,'dob' ,'identity' ,'note1' ,'phone' ,'phone2' ,'mobile' ,'email' ,'address' ,'paddress' ,'adate' ,'agrade' ,'hobbies' ,'skills' ,'note2' )"


```


the whole block

```

 PUBLIC SUB btnSave_Click()
 
DIM fname AS String = txtfname.text
DIM lname AS String = txtlname.text
DIM father AS String = txtfather.text
DIM mother AS String = txtmother.text
DIM guardian AS String = txtguardian.text
DIM dob AS String = txtdob.text
DIM identity AS String = txtid.text
DIM note1 AS String = txtnotes.text
DIM phone AS String = txtaphone.text
DIM phone2 AS String = txtaphone.text
DIM mobile AS String = txtmobile.text
DIM email AS String = txtemail.text
DIM address AS String = txtaddress.text
DIM paddress AS String = txtpaddress.text
DIM adate AS String = txtadate.text
DIM agrade AS String = txtagrade.text
DIM hobbies AS String = txthobbies.text
DIM skills AS String = txtfname.text
DIM note2 AS String = txtnotes2.text
 
 
 
  DIM sql AS String

  IF btnAdd.Enabled = FALSE THEN
    sql = "insert into students( 'fname' ,'lname' ,'father' ,'mother' ,'guardian' ,'dob' ,'identity' ,'note1' ,'phone' ,'phone2' ,'mobile' ,'email' ,'address' ,'paddress' ,'adate' ,'agrade' ,'hobbies' ,'skills' ,'note2' ) values( 'fname' ,'lname' ,'father' ,'mother' ,'guardian' ,'dob' ,'identity' ,'note1' ,'phone' ,'phone2' ,'mobile' ,'email' ,'address' ,'paddress' ,'adate' ,'agrade' ,'hobbies' ,'skills' ,'note2' )"

    MyRS = MyConn.Exec(sql)
    btnAdd.Enabled = TRUE
  ELSE
  
''''''''''''''''''''''
'Updating''''''''''
''''''''''''''''''''''
    sql = "update students set "
    sql = sql & "fname = '" &
    fname
    sql = sql & "',lname = '" &
    lname
    sql = sql & "',father = '" &
   father
    sql = sql & "',mother = '" &
    mother
    sql = sql & "',guardian = '" &
    txtguardian.text
    sql = sql & "',dob = '" &
    dob
    
    sql = sql & "',identity = '" &
    identity
    sql = sql & "',note1 = '" &
    txtnotes.text
    sql = sql & "',phone = '" &
    phone
    
    sql = sql & "',phone2 = '" &
    phone2
    sql = sql & "',mobile = '" &
    mobile
    sql = sql & "',email = '" &
    email
    sql = sql & "',address = '" &
   address
    sql = sql & "',paddress = '" &
    paddress
    sql = sql & "',adate = '" &
    adate
    sql = sql & "',agrade = '" &
   agrade
    sql = sql & "',hobbies = '" &
    hobbies
    sql = sql & "',skills = '" &
    skills
     
    sql = sql & "',note2 = '" & note2 & "' where id = " & vCari
    MyRS = MyConn.Exec(sql)
  ENDIF
  getData
  fillUpListBox                                   

 CATCH
  Message.Error(Error.Text & "add/update")
 END                                           



```

---

### Post by CodeBird on 2009-01-18
> 
sql = "insert into students( 'fname' ,'lname' ,'father' ,'mother' ,'guardian' ,'dob' ,'identity' ,'note1' ,'phone' ,'phone2' ,'mobile' ,'email' ,'address' ,'paddress' ,'adate' ,'agrade' ,'hobbies' ,'skills' ,'note2' ) values( 'fname' ,'lname' ,'father' ,'mother' ,'guardian' ,'dob' ,'identity' ,'note1' ,'phone' ,'phone2' ,'mobile' ,'email' ,'address' ,'paddress' ,'adate' ,'agrade' ,'hobbies' ,'skills' ,'note2' )"

first of all you should remove the quotes from the first part of the query:
> 
sql = "insert into students( fname ,lname ,father,mother ,guardian ,dob ,identity ,note1 ,phone ,phone2 ,mobile ,email ,address ,paddress ,adate ,agrade ,hobbies ,skills ,note2) values( 'fname' ,'lname' ,'father' ,'mother' ,'guardian' ,'dob' ,'identity' ,'note1' ,'phone' ,'phone2' ,'mobile' ,'email' ,'address' ,'paddress' ,'adate' ,'agrade' ,'hobbies' ,'skills' ,'note2' )"

like this your query will work, but it will not insert the values of the variables but it will insert the words fname lname father mother... don't forget to do it like u've written the variables in the update

---

### Post by The Cog on 2009-01-18
Shouldnt that be something like:
> insert into students values (fname ,lname ,father,mother...
or perhaps:
> insert into students ( 'fname' ,'lname' ,'father'...) values (fname ,lname ,father...

---

### Post by kpatz on 2009-01-19
INSERT INTO table_name (col1, col2 ...) VALUES (val1, val2...)

The column names (col1, col2) cannot be in quotes.  Depending on the SQL database engine you're using, you may put them in backticks (MySQL) or square brackets (SQL Server) if any column names conflict with reserved words.  But most of the time, you would just list them without any quoting.

The VALUES are expressions, which may be literals, or functions that return values.  If they're string literals (or date literals), you would enclose them in quotes.

So, for example, if product_name is a string type (varchar, text, char) and the price is a numeric type (decimal, number, money):

```

INSERT INTO my_table (product_name, price) VALUES ('Eggs', 2.95);

```

In your VB.NET example, you would build your SQL string much like you did in your Update statement, for example:

```

sSQL = "INSERT INTO my_table (product_name, price) VALUES('" & ProductName & "'," & ProductPrice & ")"

```

---

