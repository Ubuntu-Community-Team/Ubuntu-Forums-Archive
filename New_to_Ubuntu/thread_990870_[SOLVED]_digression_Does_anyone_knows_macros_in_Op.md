---
title: "[SOLVED] digression: Does anyone knows macros in OpenOffice?"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by krtica on 2008-11-23
I'm sorry if this is not place for this question, but there is no so many people on the OpenOffice forum, and most of "open-source-software-experienced-people" are here. And, also, I'm really in haste and scramble. (English is not my first language, sorry. :D)

I wanna to make macro in **OpenOffice base** (3.0), which will get data from random record from table and put it in textboxes.
I never used macros before.
I googled a lot, and I was able to write this:

```
Sub Main
DBContext=createUnoService("com.sun.star.sdb.DatabaseContext")
If not DBContext.hasByName("testdb") then
MsgBox ("Connection failed!" , "Error!") : End
End If
DataSource=DBContext.getByName("testdb")
ConnectToDB=DataSource.GetConnection ("","")
SQLResult=createUnoService("com.sun.star.sdb.RowSet")
SQLQuery="SELECT ""ID"", ""JBRTR"", ""OZB"" FROM ""testtable"""
SQLResult.activeConnection=ConnectToDB
SQLResult.Command=SQLQuery
SQLResult.execute
SQLResult.Last
Rows=SQLResult.getRow
Do
RandomID=Int(Rnd()*Rows)
SQLResult.Absolute(RandomID)
JeBrTrans=SQLResult.getString(2)
OzBa=SQLResult.getString(3)
Loop While isEmpty(JeBrTrans)
msgBox( JeBrTrans & " , " & OzBa )
ConnectToDB.close
ConnectToDB.dispose()
End Sub
```

I assigned this macro to button, and when I click on it I'm getting msgBox with wanted results.

But I'm TOO STUPID to put those results in textBoxes on same form from where I click on Button.
I really tried to do it myself, but without any success.
So, if anyone is merciful enough to tell me what is exact code, because I'm unable to figure it out.

Thank you. Thank you very much.

PS: I'm really sorry if Ubuntu forum is not a place for tthis question. :oops:

---

### Post by SamNSane on 2008-11-23
The Ubuntu forums are a pretty good place to look for information on a wide variety of operating system, hardware / driver, and general software issues. However, you might find people who are particularly adept concerning this matter at [http://www.oooforum.org/]("http://www.oooforum.org/"). You'll notice they have a forum specifically relating to Base and another forum specifically relating to macros.

I hope you find help!

---

### Post by krtica on 2008-11-23
I knew that I'll found help. :)
I was on wrong OpenOffice forum. :D
Thank you.

---

### Post by SamNSane on 2008-11-23
> **krtica said:**
> I knew that I'll found help. :)
I was on wrong OpenOffice forum. :D
Thank you.

You're welcome.

Oh, and please don't call yourself stupid. Some of us are worse at writing macros than you are. It makes us feel pretty dumb. I once unleashed one of my macros on a large production spreadsheet (Lotus 123, a long time ago) without adequate testing. Let's just say it's a good thing we had a backup. (Unfortunately, the backup was about a week old. That one incident led me to become obsessive about backups, which now get done several times every day on critical data.)

---

