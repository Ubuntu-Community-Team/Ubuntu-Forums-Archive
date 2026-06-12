---
title: "mono on dapper - trying to install mysql into gac."
date: 2006-03-21
forum: Programming Talk
---

### Post by lee_connell on 2006-03-21
I used gacutil -i MySql.Data.Dll and it said it installed properly and I do see it in /usr/lib/mono/gac however I can't create a script and reference that file when I compile it, it doesn't know where it is.  

Also MonoDevelop doesn't see it in Help -> About -> Versions.

What is going on here?  I did post to mono-list and haven't gotten a response yet.  Hoping someone here may know.

thanks!

---

### Post by Mickeysofine1972 on 2006-06-20
Me too!

I've never had this problem installing other scripting and databse stuff, only with mono!

Mike

---

### Post by lee_connell on 2006-06-20
Yeah, I've posted in mono-list and no one can even acknowledge the issue?

A bit of a turn off using mono.  If you get anywhere please let me know.

---

### Post by Brainjar on 2006-09-16
I've the same problem. Is there any solution ? 
Thanks.
Brainjar.
](*,)

---

### Post by gmclachl on 2006-09-16
I have installed it without any problem. Use 

  gacutil -i 

 then you need to copy the .dll to /usr/lib/mono/1.0 (or 2.0) 

 George

---

### Post by j o e l on 2007-02-03
I don't know if any of you were ever able to get this working or not, but I was experiencing similar problems.  Here's what I did to get it working on my old Xubuntu box...

1. Downloaded the latest [connector]("http://dev.mysql.com/downloads/connector/net/1.0.html") from MySQL's Web site.  I downloaded the file without the installer.

2. Unzip the file to whatever directory you choose.  Let's say /home/joeblow/downloads/, so you end up with /home/joeblow/downloads/mysql-connector-net-1.0.9-noinstall/ after the extraction.

3. Change to your gac directory.  On my xubuntu box, it is /usr/lib/mono/gac.  I'm sure it is the same across all the *ubuntu versions, but check to make sure.

4. From /usr/lib/mono/gac (or whatever it is on your box), type the following:
sudo gacutil -i /home/joeblow/downloads/mysql-connector-net-1.0.9-noinstall/MySql.Data.dll -check_refs -package MySQLConnector1.09

5. Restart MonoDevelop.

6. From within your current project, right-click on the References folder and select "Edit References".

7. Choose the .NET Assemblies tab and navigate to your gac folder to select the  - in our example, /usr/lib/mono/gac, to locate the MySql.Data folder.

8. cd to MySql.Data and the following direcories until you find the MySql.Data.dll file.  On my box it was /ust/lib/mono/gac/MySql.Data/1.0.9.0__c5687fc88969c44d/.

9.  Add it to the Selected References and click Ok.

This is what worked for me.  I hope it helps someone else.

---

