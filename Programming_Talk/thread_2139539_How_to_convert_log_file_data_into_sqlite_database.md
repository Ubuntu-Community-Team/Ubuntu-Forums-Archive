---
title: "How to convert log file data into sqlite database?"
date: 2013-04-27
forum: Programming Talk
---

### Post by Newbie89 on 2013-04-27
previously is [FONT=arial]used log file to save data.[/FONT][FONT=arial] Now I need to identify the variables which need to logged and save into sqlite database.Any idea on how to start?thanks[/FONT]

---

### Post by Martin Witte on 2013-04-27
You can import a comma seperated text file directly in sqllite, see [http://www.sqlite.org/cvstrac/wiki?p=ImportingFiles]("http://www.sqlite.org/cvstrac/wiki?p=ImportingFiles"). So the recipe would be to convert your logfile to a comma seperated file. Next create a table in sqllite with all the attributes of your log file, e.g. severity, date/time, source code line, error mesage. Finally import the logfile

---

### Post by Newbie89 on 2013-04-28
> **Martin Witte said:**
> You can import a comma seperated text file directly in sqllite, see [http://www.sqlite.org/cvstrac/wiki?p=ImportingFiles](http://www.sqlite.org/cvstrac/wiki?p=ImportingFiles). So the recipe would be to convert your logfile to a comma seperated file. Next create a table in sqllite with all the attributes of your log file, e.g. severity, date/time, source code line, error mesage. Finally import the logfile

thanks for the information...can  you show me the example of "create a table in sqllite with all the attributes of your log file, e.g. severity, date/time, source code line, error mesage."
I'm not very know how to do it...thanks.

---

### Post by Bodsda on 2013-04-28
> **Newbie89 said:**
> thanks for the information...can  you show me the example of "create a table in sqllite with all the attributes of your log file, e.g. severity, date/time, source code line, error mesage."
I'm not very know how to do it...thanks.

There is a simple example in the link that was posted. 
I suggest you read that first and then ask for further help if you're still having problems.

Bodsda

---

### Post by Newbie89 on 2013-04-29
Is it just identify the variable in the C file then create a table only to link it?Let say my C file got this variable as shown below:

struct HOST
{
   char Src_MAC[18];
   char Src_IP[16];            
   long int Cap_Bytes;
   int TCP,UDP,ICMP,IP,ARP,OTH_Net, OTH_Trans;   // Protocols
   int ftp,ssh,telnet,domain,www,netbios,other;  // Services   
};

---

