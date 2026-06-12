---
title: "Using MySQL JDBC connector, when to disclose source code"
date: 2019-07-02
forum: Programming Talk
---

### Post by Drenriza on 2019-07-02
Hi all!
On [https://opensource.stackexchange.com/questions/8338/using-mysql-jdbc-connector-when-to-disclose-source-code](https://opensource.stackexchange.com/questions/8338/using-mysql-jdbc-connector-when-to-disclose-source-code) i have a question in regards to MySQL JDBC and the GNU GPL V2 License.

My question from opensource.stackexchange
> 
  **Part 1**
  I would like to use MySQL JDBC connector (called connector) licensed  under GNU GPL V2 to exchange data to and from a MySQL database in my  project, as far as i can read, If i add the connector file directly to  my project and i decide to sell a copy of this project/application to be  run on external servers, i would need to disclose my source code if  asked for it.
  As far as i understand this is because the connector file becomes a  part of the larger project/application, and because the connector is  licensed under GNU GPL V2 the entire project/application would need to  be licensed under the same or similar license?
  **Part 2**
  From a thread on stackoverflow i read a comment that said, that if  the connector is part of a separate project and you use that project to  communicate with the SQL server, only the source code for the project  running the connector would need to be disclosed.
  **Question**
  If i use the connector as a datasource managed by the server, so my  project would not directly contain the connector file. Would my project  than still fall under the GNU GPL V2 license?

     
[URL="https://choosealicense.com/licenses/gpl-2.0/"]

Thanks on advanceasd
Best regards!
[/URL]

---

### Post by TheFu on 2019-07-02
Best to get legal advice from a lawyer.

I know very little about java besides it is slow, uses too much RAM and too much CPU and that none of my systems have enough resources to make me a happy developer with java.  Core i7 w/ 16G of RAM wasn't sufficient.  For all my other development work, I use a chromebook since about 2012.

A few decades ago, I worked on the [unixODBC]("http://www.unixodbc.org/") project. This was a "driver manager" for ODBC connections.  Think of it as a middle layer between your code and the ODBC driver.
```

 My program ---- Driver Manager ---- ODBC driver
{my license}       LGPL                GPL
```

By using an LGPL driver manager, you've insolated your code from GPL parts.  The LGPL license does have some mandates.  Users need to be able to relink a newer version of the LGPL code with your program, if they like. This means you have to provide object files and instructions  so they can accomplish that part.  Or just use dlopen() and dlclose() in your code and require the driver manager to be compiled into a shared object.  Sorry that I used C terms. I know C and C++, not Java.
From the unixODBC project page:> 
ALL unixODBC development is and will be distributed under GPL or LGPL. The LGPL on libs will ensure that commercial solutions will be able to utilize unixODBC.

Did I mention that you should check with a real, licensed, lawyer?

---

### Post by Drenriza on 2019-07-12
Thanks for the reply @TheFu
Yes you did mention to contact a license laywer :)

---

### Post by TheFu on 2019-07-12
I am NOT @TheFu.  Don't use social networks myself.  Just wanted to clarify that.

If this is answered as best you can expect here, please mark the thread "SOLVED" using the Thread Tools button near the top. This helps the larger community.

---

