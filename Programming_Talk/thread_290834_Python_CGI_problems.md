---
title: "Python CGI problems"
date: 2006-11-01
forum: Programming Talk
---

### Post by ironfistchamp on 2006-11-01
Hey all

I am creating a website for working with a MySQL database. I am using Python to do all the interaction with the database itself. I have run into two large problems. 

The first is that I have one page that loops through a query to print out form for each row. Each row has two submit buttons. When I click either one it goes to my second CGI page. I have printed out the contents of cgi.FieldStorage() but all it returns is (None, None, []). It appears that nothing is getting passed at all. 

My second problem is that I need to detect which submit button was used using only server-side Python scripting. I assume that if we solve the first problem the second one should follow quite easily. 

Any help that can be given would be great. 

Thanks

Ironfistchamp

First page:
```



#! /usr/bin/python
print "Content-type: text/html\n\n"

import MySQLdb
import cgi


try:
	connection=MySQLdb.connect(host="localhost", user="XXX", passwd="XXX", db="memoryclub")
	cursor=connection.cursor()	
	
	    
except:
    	print "Could not connect to database!"


form = """
<html>
<head>
</head>
<body>
<FORM method="POST" action="recordmanip.cgi">
<p>Name:<input type="text" name="name" value="%s"></p>
<p>Address 1: <input type="text" name="addr1" value="%s"></p>
<p>Address 2: <input type="text" name="addr2" value="%s"></p>
<p>Town: <input type="text" name="town" value="%s"></p>
<p>City: <input type="text" name="city" value="%s"></p>
<p>Postcode: <input type="text" name="postcode" value="%s"></p>
<p>Telephone Number: <input type="text" name="telnum" value="%s"></p>
<p>Date Of Birth: <input type="text" name="dob" value="%s"></p>
<p>Carer Name: <input type="text" name="carer_name" value="%s"></p>
<p>Carer Relationship: <input type="text" name="carer_rel" value="%s"></p>
<p>Emergency Contact Number: <input type="text" name="emer_contact" value="%s"></p>
<p>Medical History: <input type="text" name="med_history" value="%s"></p>
<p>Medication: <input type="text" name="medication" value="%s"></p>
<p>General Practicioner: <input type="text" name="gp" value="%s"></p>
<p>Social Worker: <input type="text" name="social_worker" value="%s"></p>
<p>CPN: <input type="text" name="cpn" value="%s"></p>
<p>Total Donations: <input type="text" name="total_donations" value="%s"></p>
<p>Other Services: <input type="text" name="other_services" value="%s"></p>

<p><input type="submit" value="Edit" name="edit">
<input type="submit" value="Delete" name="delete"></p>
</FORM>
</body>
</html>""" 



sql_stmt = 'select * from member'

cursor.execute(sql_stmt)

result = cursor.fetchall()


for record in result:
	print form % (record[0],record[1],record[2],record[3],record[4],record[5],record[6],record[7],record[8],record[9],record[10],record[11],record[12],record[13],record[14],record[15],record[16], record[17])


```

Second Page:

```

#! /usr/bin/python
print "Content-Type: text/html"
print
print
import cgi
import MySQLdb


try:
	connection=MySQLdb.connect(host="localhost", user="XXX", passwd="XXX", db="memoryclub")
	cursor=connection.cursor()	
	
	    
except:
    	print "Could not connect to database!"


fs = cgi.FieldStorage()


print fs

```

---

### Post by DaveBorealis on 2006-11-01
Hello,

It's been a couple years since I've done cgi, however it seems that your second page is not reading in the query string and parsing out the environmental variables passed by the first page.  

Unfortunately I'm not sure how it's done in python; I've only used perl for cgi.

Best regards,
Dave

---

### Post by ironfistchamp on 2006-11-02
Thank you for your reply. After a few hours thinking and trying some ideas I have come up with a way to do it. I use a single page which checks for certain keys in the FieldStorage() variable I have defined. I have almost finished it. I just need to get the edit part working.

I will post the code back on here just in case someone is interested.

Thanks again

Ironfistchamp

---

