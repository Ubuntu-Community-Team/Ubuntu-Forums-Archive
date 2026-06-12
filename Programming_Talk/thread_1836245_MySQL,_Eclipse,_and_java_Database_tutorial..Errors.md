---
title: "MySQL, Eclipse, and java Database tutorial..Errors"
date: 2011-08-30
forum: Programming Talk
---

### Post by hpng on 2011-08-30
I am following a Java and SQL tutorial.
 The book is called:  MySQL and Java Developer's Guide by  
 Mark Matthews, Jim Cole, Joseph D. Gradecki (2003).
 

 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]All the code and examples in this book can be found on the the support Web site at[/SIZE][/FONT][/COLOR]
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2][www.wiley.com/compbooks/matthews]("http://www.wiley.com/compbooks/matthews").[/SIZE][/FONT][/COLOR]
 

 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]Here is my work setup:[/SIZE][/FONT][/COLOR]
 Eclipse IDE Indigo with JRE System Library (JavaSE-1.6) as default
 Java version on Ubuntu:
 User1:~$ java -version  
 java version "1.6.0_20"  
 OpenJDK Runtime Environment (IcedTea6 1.9.9) (6b20-1.9.9-0ubuntu1~10.04.2)  
 OpenJDK 64-Bit Server VM (build 19.0-b09, mixed mode)  
 

 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]I was to complete a simple  Java database example in Chapter 4 tutorial.  [/SIZE][/FONT][/COLOR] 
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]It is just a check for valid database connection, and it works.[/SIZE][/FONT][/COLOR]
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]I was able to view the installed database server using MySQL Workbench.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]Now I am working on Chapter 5 tutorial codes.[/SIZE][/FONT][/COLOR]
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]I was not able to compile it.  Note:  There are several applications / applets in the chapters.[/SIZE][/FONT][/COLOR]
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]You will need the following screen shot for better handle on my problems.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]A screen shot of the folder for Chapter 5 Project in Ubuntu 10.04:[/SIZE][/FONT][/COLOR]
[COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]([/SIZE][/FONT][/COLOR]See ScreenshotOfJavaTutorialChapter5Foldertree.png[COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2])
  [Can someone explain how I can paste a screenshot into this area rather than[/SIZE][/FONT][/COLOR][COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2] uploading an attachment?]


[/SIZE][/FONT][/COLOR][COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]A screen shot of Eclipse JDT with Chapter 5 project opened and errors shown on :[/SIZE][/FONT][/COLOR]
 (see  

Screenshot-chapter 5 - Java - chapter 5-com-mysql-jca-MysqlManagedConnection.java - Eclipse .png)

 

 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]Note that the original tutorial java project was not modified, and was inserted into eclipse using menu item New>Project>Java Project where I then disabled the 'Use Default Location&#8221; check box, and Eclipse automatically use &#8220;Chapter 5&#8221; as Project name for the new project.  Workspace-JDT is the selected workspace for my Java tutorial when Eclipse opens.  All the database tutorial is inside Workspace-JDT folder.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]Below are examples of the problems showing on the &#8220;Problem&#8221; tab of Eclipse:[/SIZE][/FONT][/COLOR]
 

 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]Example problem #1:[/SIZE][/FONT][/COLOR]
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]Description    Resource    Path    Location    Type[/SIZE][/FONT][/COLOR]
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]The declared package "mysql" does not match the expected package ""  Hello.java    /chapter 5    [/SIZE][/FONT][/COLOR]
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]line 1    Java Problem[/SIZE][/FONT][/COLOR]
 

 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]When I double click the highlighted problem (error) above (screenshot), Eclipse change window pane focus to  editor and display top of Hello.java file with line#1 highlighting &#8220;mysql&#8221; word of the line31 below:[/SIZE][/FONT][/COLOR]
 

 [FONT=Monospace][SIZE=4][COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]**line#1 **[/SIZE][/FONT][/COLOR][COLOR=#7f0055][SIZE=2]**package**[/SIZE][/COLOR][COLOR=#000000][SIZE=2]_mysql_[/SIZE][/COLOR][COLOR=#000000][SIZE=2];[/SIZE][/COLOR][/SIZE][/FONT]
 [SIZE=2][COLOR=#000000][FONT=Monospace]line#2    [/FONT][/COLOR][COLOR=#7f0055][FONT=Monospace]**import**[/FONT][/COLOR][COLOR=#000000][FONT=Monospace] java.sql.*;[/FONT][/COLOR][/SIZE]
 

 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]As a reminder, my project folder for Chapter 5 hierarchy looks like this:[/SIZE][/FONT][/COLOR]
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]HomeFolder\Workspace-JDT\mysql and java\software\chapter 5\com\mysql[/SIZE][/FONT][/COLOR]
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]            \jca[/SIZE][/FONT][/COLOR]
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]            \jdbc\jdbc2\optional[/SIZE][/FONT][/COLOR]
 

 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]As I understand it, the &#8220;Package mysql&#8221; means the Hello.java will be added to folder &#8220;mysql&#8221; after compilation.[/SIZE][/FONT][/COLOR]
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]One of my many questions is:  Do I have to change this[/SIZE][/FONT][/COLOR]
 [FONT=Monospace][SIZE=4][COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]**line#1 **[/SIZE][/FONT][/COLOR][COLOR=#7f0055][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]**package**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]_mysql_[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2];[/SIZE][/FONT][/COLOR][/SIZE][/FONT]
 [FONT=Monospace][SIZE=4][COLOR=#000000][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]to this because my folder hierarchy is different:[/SIZE][/FONT][/COLOR][/SIZE][/FONT]
 [FONT=Monospace][SIZE=4][COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]**line#1 **[/SIZE][/FONT][/COLOR][COLOR=#7f0055][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]**package**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]_mysql_[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2];[/SIZE][/FONT][/COLOR][/SIZE][/FONT]
 [FONT=Monospace][SIZE=4][COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]**package**[/SIZE][/FONT][/COLOR][COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2] HomeFolder\Workspace-JDT\mysql and java\software\chapter 5\com[/SIZE][/FONT][/COLOR][/SIZE][/FONT]
 

 [FONT=Monospace][SIZE=4][COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]Likewise, I also have many error problems ( &#8220;....cannot be resolved to a type...&#8221; ) similar to what is shown below.[/SIZE][/FONT][/COLOR][/SIZE][/FONT]
 

 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]Example problem #2:[/SIZE][/FONT][/COLOR]
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]Description    Resource    Path    Location        Type[/SIZE][/FONT][/COLOR]
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]ConnectionEventListener cannot be resolved to a type    [/SIZE][/FONT][/COLOR]
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]MysqlManagedConnection.java    /chapter 5/com/mysql/jca    [/SIZE][/FONT][/COLOR]
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]line 99    Java Problem[/SIZE][/FONT][/COLOR]
 

 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]This problem tells me that &#8220;ConnectionEventListener&#8221;in following line was not found in any file declaration.[/SIZE][/FONT][/COLOR]
 [FONT=Monospace][SIZE=1][COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif]line #99    [/FONT][/COLOR][COLOR=#000000]    [/COLOR][COLOR=#7f0055]**public**[/COLOR][COLOR=#7f0055]**void**[/COLOR][COLOR=#000000] addConnectionEventListener([/COLOR][COLOR=#000000]_ConnectionEventListener_[/COLOR][COLOR=#000000] arg0) {[/COLOR][/SIZE][/FONT]
 [SIZE=1][COLOR=#000000][FONT=Monospace]        }[/FONT][/COLOR][/SIZE]
 

 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]I am at a lost of what to do since I though my previous Hello tutorial is[/SIZE][/FONT][/COLOR]
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]working and it already has database connection validated.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]Y hunch is that my project folder is different from the author's project folders.  Thus giving me much grief.[/SIZE][/FONT][/COLOR]
 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]I though Eclipse would have been able to resolve the path to all associated files, classes, variables, types....etc when I imported the entire project in one shot.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#272526][FONT=OBPJHF+Formata-Medium, sans-serif][SIZE=2]What do I have to do to eliminate the errors.[/SIZE][/FONT][/COLOR]
 
Cheers.....

---

