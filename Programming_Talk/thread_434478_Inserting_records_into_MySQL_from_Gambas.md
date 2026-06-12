---
title: "Inserting records into MySQL from Gambas"
date: 2007-05-06
forum: Programming Talk
---

### Post by gary0 on 2007-05-06
Hi all,
I wrote an amateur radio logbook in VB6 some years ago, using both Access and SQL server, (I could switch between them for local and remote), and have decided to rewrite it for linux using gambas. I can retrieve records and search for records no problem (imported data from old vb logbook), but am having problems inserting new records in MySQL.

Here is my sql:

RstCall = ModData.Exec ("INSERT INTO tblLog (MyDate, TimeOn, TimeOff, Callsign, Band, Mode, Power, HisRst, MyRst, QslSent, QslRcvd, WAB, IARU, Comments)" &
  " VALUES ('#" & txtDate.text & "#'," & "'#" & txtTimeOn.text & "#'," & "'#" & txtTimeOff.text & "#'," & "'" & txtCallsign.text & "'," & "'" & txtBand.text & "'," & "'" & txtMode.text & "'," & "'" & txtPwr.text & "'," & "'" & txtHisRst.text & "'," & "'" & txtMyRst.text & "'," & "'" & CkSent.Value & "'," & "'" & CkRcvd.Value & "'," & "'" & txtWAB.text & "'," & "'" & txtIARU.text & "'," & "'" & txtComments.text & "';")
 RstCall.Update

my execute function:

PUBLIC FUNCTION Exec(sql AS String) AS Result
message (sql)       'For Debugging
   RETURN myDB.Exec(sql)
END FUNCTION

I am quite familiar with sql, but this is driving me crazy! I get this error msg:

Query failed: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near " at line 1.

Not sure about the #'s around the date and time fields, maybe [ ]? but have tried these with no luck, so I don't think it's that.

Any help would be muchly appreciated.
Thanks in advance,
Gary.

---

### Post by phossal on 2007-05-06
Wow. I had a similar problem using Perl (and the ODBC wrapper) and MySQL. MySQL uses the quote for time field delineation. However, from Perl, using the ODBC wrapper, it uses '#'. It took me days to figure that out. MySQL wants a date something like this: insert into... values('2007-05-03')...

To test your sql, try leaving the data fields out, or using now(). Then you'll know if it's a character or formatting problem.

---

### Post by gary0 on 2007-05-06
Hi Phossal,
thanks for the quick reply, I tried all your suggestions, and even changed the field data types to VARCHAR(20) (time and date fields), but still no joy :-(

Gary.

---

### Post by phossal on 2007-05-06
Will you do me a favor and translate your code in the previous post into a prompt-like sql statement. Write it out without the variables? Are you supposed to have the terminating ';' ?

[EDIT] In your posted SQL, it looks like you're delineating with both ' and # ?. The double quotes outline your statements, which are joined by the &, so that leaves the ' and # wrapping your variables. Shouldn't it be one or the other?

---

### Post by gary0 on 2007-05-06
> **phossal said:**
> Will you do me a favor and translate your code in the previous post into a prompt-like sql statement. Write it out without the variables? Are you supposed to have the terminating ';' ?

[EDIT] In your posted SQL, it looks like you're delineating with both ' and # ?. The double quotes outline your statements, which are joined by the &, so that leaves the ' and # wrapping your variables. Shouldn't it be one or the other?

Ah, you may have a point there... It was 4 in the morning when I wrote it, will check it out and get back to you.
Gary.

---

### Post by phossal on 2007-05-06
Yeah, I doubt you need the ";" termination, and maybe you've double-delineated. When I write inserts or queries from new languages, I usually start with "clean" statements. Try a single line, into a test table with one field, without concatenating strings. Then troubleshoot bit by bit as you build into it.

---

### Post by gary0 on 2007-05-06
Ok, got it licked. I cut down the sql to 2 fields (callsign and band) and hard coded the values. Also removed the ; from the end of the statement and it worked just fine.

Thanks Phossal for your input, really appreciate it.

Gary.

---

### Post by phossal on 2007-05-06
You're welcome, of course. I'm glad you figured it out.

Cheers!

---

