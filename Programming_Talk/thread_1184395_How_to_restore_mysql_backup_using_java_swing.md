---
title: "How to restore mysql backup using java swing"
date: 2009-06-11
forum: Programming Talk
---

### Post by sthiranga on 2009-06-11
I want restore mysql backup file(c:/backup.sql) using java swing. 
 it's work with dos prompt like this 
 mysql -u uname -ppword Dname<C:/backup.sql 
  
 how can i execute this in java swing. 
 can anyone help me..

---

### Post by froggyswamp on 2009-06-11
Swing is a GUI package and has nothing to do with restoring MySQL backup files. You have to elaborate better what you mean, what you tried, where you failed and what was the error message.

---

### Post by sthiranga on 2009-06-11
I used this java code to get backup file 

try {
          Runtime.getRuntime().exec("C:\\Program Files\\MySQL\\MySQL Server 5.0\\bin\\mysqldump -u root -p123 example -r C:/backup.sql");
}catch(Exception e){
        e.printStackTrace();
 }
it's work fine...create backup.sql file

when i tried to restore using this java code  no errors,nothing happen,database not restore

try {
          Runtime.getRuntime().exec("C:\\Program Files\\MySQL\\MySQL Server 5.0\\bin\\mysql -u root -p123 example < C:/backup.sql");
}catch(Exception e){
        e.printStackTrace();
}

any sugestion ...

---

### Post by froggyswamp on 2009-06-11
What does Swing have to do with this? I don't see any mention of it in your code.

---

### Post by sthiranga on 2009-06-11
Any way, i want to backup and restore(import and export)  MYSQL database using java application(if swing that better) please help me

thank you

---

### Post by prabhurangan on 2009-06-11
@Sthiranga:

I too was struggling with this issue, but luck on myself, found this piece of code working fine. 

String[]  executeCmd   =   new String[]{"mysql", databaseName, "-                       -user=" + userName, "--password=" +                      password, "-e", " source c:/data/sample.sql" };
Process         runtimeProcess  =   
                        Runtime.getRuntime().exec(executeCmd);
processComplete                 =   runtimeProcess.waitFor();

[Note:  this 'processComplete' is an integer variable which is by default '0', and when the runtime process gets executed, if it is successfull, the process will return '0' otherwise it will return '1'.

By this we can handle the situation from where we call this method.

Hope you would have understand, with this solution.

Regards,
Prabhu

---

### Post by sthiranga on 2009-06-11
@Prabhurangan

It's work.
Thank u very much.
I was struggling two days.thank you very much.

---

### Post by sthiranga on 2009-06-11
now i'm tring remote mysql restoring in java
this is the mysql command.It's work fine and restore in windows dos prompt 

mysqldump -u user -ppword --host=10.1.1.2 Dbase | mysql -u root -p123 -c Dbase

I try it in java code and again it's not work

can anyone help me..
thanks.

---

### Post by Zugzwang on 2009-06-11
> **sthiranga said:**
> I try it in java code and again it's not work

can anyone help me..
thanks.

You should read from the Error- and Output-streams of the process to see if the execution results in an error message. Use e.g. google for details.

---

### Post by moizraj on 2010-05-17
Hello Sir,


  I tried your code accordingly but there is no response.

processComplete return 2

my code :-

    String[] executeCmd = new String[]{"mysql", dataname, "- -user=root", "--password=admin", "-e", "D:\\Backup\\data.sql" };
            Process runtimeProcess =
            Runtime.getRuntime().exec(executeCmd);
            processComplete = runtimeProcess.waitFor();

Please help me out ........

Thanks in advance..

---

### Post by vagelism on 2012-03-15
Try this tutorial.
It will help you.

[http://sandeepsharma11.blogspot.com/2011/02/mysql-database-backup.html#comment-form]("http://sandeepsharma11.blogspot.com/2011/02/mysql-database-backup.html#comment-form")

---

