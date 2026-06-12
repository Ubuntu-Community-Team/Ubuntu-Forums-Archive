---
title: "How To Fill A Combobox Using A Function From MySQL Table in Gambas?"
date: 2010-12-20
forum: Programming Talk
---

### Post by etdsbastar on 2010-12-20
Hi there,

Can anyone help me regarding the below given function:

```

public sub fillcombo(cmb as combobox, fieldname as string, tablename as string)
         dim rs as result, i as integer
         rs = connection.exec("select * from " & tablename)
         for i = 1 to rs.count
              cmb.add(rs!fieldname)
              rs.movenext
         next
end

```

the above code returns an error "unidentified field: fieldname". could anyone tell us how to resolve the problem.

---

### Post by kalaharix on 2010-12-25
Hi

Is 'fieldname' really the name of a field in your mySQL database?
Substitute the name of one of your fields

---

### Post by kalaharix on 2010-12-25
No, that does not explain the problem very well.

You are defining the data object within the class, but passing the parameter 'fieldname' from outside the class. rs does not have a fieldname 'fieldname'.

1. You can take the data selection out of the combofill class and pass the field into it.
2. You can change rs!fieldname to rs!whatever-your-fieldname and continue deriving everything within the combofill class

---

### Post by etdsbastar on 2010-12-25
> **kalaharix said:**
> No, that does not explain the problem very well.

You are defining the data object within the class, but passing the parameter 'fieldname' from outside the class. rs does not have a fieldname 'fieldname'.

1. You can take the data selection out of the combofill class and pass the field into it.
2. You can change rs!fieldname to rs!whatever-your-fieldname and continue deriving everything within the combofill class

Thanks kalaharix,

But, I couldn't understand what you are trying to explain (better if you give some sample code), secondly the fieldname is a variable which can be changed everytime i call the function.

---

### Post by kalaharix on 2010-12-26
Hi

This is the simplest way to populate a combobox (I used SQLite but that makes no difference).

I am not sure whether that is what you want or whether you specifically want to use an encapsulated Object Oriented class to be called for any field from any table for any combobox.

I must admit I don't use much of the OO properties of Gambas but for my own interest will try and do this over the next few days.

```

' Gambas class file

PUBLIC $hConn AS NEW Connection
PUBLIC res AS Result
'------------------------------------
PUBLIC SUB Form_Open()
    $hConn.Type = "sqlite3"
    $hConn.name = "/home/fred/Dropbox/sqlite3/locl.sqlite"
    $hConn.Open()
    res = $hConn.Exec("select * from operator")
END
'------------------------------------
PUBLIC SUB btnFill_Click()
    FOR EACH res
      ComboBox1.Add(res!o_name)
    NEXT
END


```

---

### Post by etdsbastar on 2010-12-26
Thanks Kalaharix for being so supportive.

I am also trying for this solution, If I will get one, I will surely put the code here for others and specially you.

Bye and take care...

---

### Post by kalaharix on 2010-12-28
The OP also asked this question on a Gambas forum ([www.gambasforum.com](www.gambasforum.com)) and it was answered by Quincunxian. Here is his solution which is easier than I anticipated (story of my life really :))

```

' Gambas class file
'------------------------------------
PUBLIC SUB btnFill_Click()
  'parameters are hardwired in this example but could come from any source
  LoadComboBox("operator", "o_name", "", ComboBox1, 1, "Please choose from:")
END
'------------------------------------
' Intable     - source table in database
' InField     - field within table
' InCondition - if present creates a where filter on select
' InCombo     - target ComboBox
' Clear       - Clears the Combobox first if value 1
' Title       - Adds a title to Combobox if present
'-------------------------------------
PUBLIC SUB LoadComboBox(InTable AS String, InField AS String, InCondition AS String, InCombo AS ComboBox, Clear AS Boolean, Title AS String)
   DIM $hConn AS NEW Connection
   DIM lRec AS Result
   DIM lQuery AS String = "Select * FROM " & inTable
   
  'open the database. LoadComboBox could also inherit an already open database
   $hConn.Type = "sqlite3"
   $hConn.name = "/home/charles/Dropbox/sqlite3/locl.sqlite"
   $hConn.Open()

   IF InCondition <> "" THEN 'add a condition if InCondition not empty
      lQuery &= " WHERE " & InCondition  ' example: "somevalue = 'value'"
   ENDIF 
   
   IF Clear THEN 'clear the ComboBox first if Clear=1 
      InCombo.Clear
   ENDIF 
   
   IF Title THEN 'add a title to the ComboBox if Title is defined
      InCombo.Add(title)
   ENDIF 

   lRec = $hConn.Exec(lQuery) 'query the database with result lRec
   ' add each entry in result to the ComboBox
   FOR EACH lRec
       inCombo.Add(lRec[InField]) 
   NEXT 
   inCombo.index = 0
   $hConn.Close()
END
'--------------------------------------


```

---

### Post by etdsbastar on 2010-12-28
> **kalaharix said:**
> The OP also asked this question on a Gambas forum ([www.gambasforum.com]("http://www.gambasforum.com")) and it was answered by Quincunxian. Here is his solution which is easier than I anticipated (story of my life really :))...

Thanks kalaharix,

It was great example and helped me a lot...

---

