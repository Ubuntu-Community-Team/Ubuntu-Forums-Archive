---
title: "[SOLVED] JDBC connection problem in JSP"
date: 2008-07-13
forum: Programming Talk
---

### Post by balagosa on 2008-07-13
If you think I didnt search the net for guides, I found some. Maybe I just did not find the right guide.

[guide1]("http://www.kitebird.com/articles/jdbc.html") <--We are using the same driver "com.mysql.jdbc.Driver"

[guide2]("http://scis.athabascau.ca/html/server/jspdemo.htm")

when I run my JSP file, it will not connect to the database. it stops at "Class.forName..."

I have read in the driver-included pdf file, that i have to copy the mysql.*.jar file to .../WEB-INF/lib. along this folder I also found a catalina.*.jar

My **Connector/J** was downloaded from [www.mysql.com]("http://dev.mysql.com/downloads/connector/j/5.1.html"). 

Possible Causes:
1) I am not doing it right
2) I have not installed the driver correctly

Ways you can Help:
1) Giving me a nice JSP-DBMS tutorial (which includes both JSP and java examples)
2) Correct my errors and explain why I am wrong


Note: I am using tomcat5.5 as web server

My JSP code
```
<%@ page import="java.sql.*"%>
<html>
<head>
<title>JSP Authenticate</title>
</head>
<body>
<%! 
String username;
String password;
%>
<%
username = request.getParameter("user");
password = request.getParameter("pass");

%>
<%
	java.sql.Connection conn;

	   try
           {
               String url = "jdbc:mysql://localhost/experiment1";
		
               Class.forName("com.mysql.jdbc.Driver").newInstance();
		out.println("Databases is Connected"); //<--It does not display this, so meaning an error occurred
               conn = DriverManager.getConnection (url, "root", "root");	       
           }
           catch (Exception e)
           {
               out.println ("Cannot connect to database server"); //<--the error is displayed
           }
           finally
           {
               //if (conn != null)
               //{
               //    try
               //    {
               //        conn.close ();
               //       System.out.println ("Database connection terminated");
               //    }
               //    catch (Exception e) { /* ignore close errors */ }
               //}
           }

%>

</body>
</html
``` 

Note: the **user & pass** variables have nothing to do with the connection. They are variables that I will pass to the database for Querying.

---

### Post by CptPicard on 2008-07-13
Yeah, you are not doing it right. I haven't done this kind of raw jdbc connections for at least 5 years (real-world Java frameworks abstract all that away) so I may be wrong, but the general issue seems to be  that you're not doing anything with the value you get from Class.forName -- you just throw it away. The result of that call is a Class object, which, somehow, is then probably hooked into the DriverManager, from where you can get connections.

Your architecture in general is "this is how you don't do it" anyway though. You would never do all of that per jsp call. The Right Way to go about refactoring your system is to

1) Make the database connection a Tomcat-managed (preferably connection-pooled) DataSource
2) Put your database querying code into a servlet that uses this DataSource
3) Use JSPs only for rendering html.

---

### Post by balagosa on 2008-07-13
off topic: Thanks for the quick reply. Anyways, I had an option to use NetBeans for all the connecting woes. But in order for me to learn, I decided to give manual connection a try. You see this is an assignment given by my professor. He done the connection through this method, and after class he distributed the tutorial but I did not get a copy of it(my regret). So now I am looking over the net for ideas on how he did it.

on topic: I will try to correct my connection using your suggestions. This is just an assignment, so Coding formality/do-nots is not really necessary here. If I were to make a Work Project though, I will not implement this.

---

### Post by xlinuks on 2008-07-13
```

Class.forName( "com.mysql.jdbc.Driver" ).newInstance();

```

---

### Post by balagosa on 2008-07-13
> **xlinuks said:**
> ```

Class.forName( "com.mysql.jdbc.Driver" ).newInstance();

```

for some reason, the "newInstance()" was not included in the code but it was supposed to be there.

Sorry for the missing info. I already edited the above code.

---

### Post by dexter.deepak on 2008-07-13
> **xlinuks said:**
> ```

Class.forName( "com.mysql.jdbc.Driver" ).newInstance();

```

using newInstance() is not a requisite.
why dont you install connector/J through synaptic ?? probably you have not set it up correctly.
and please post the error you get.

---

### Post by balagosa on 2008-07-13
> **dexter.deepak said:**
> using newInstance() is not a requisite.
why dont you install connector/J through synaptic ?? probably you have not set it up correctly.
and please post the error you get.

I did post the error I get as stated by:
out.println ("Cannot connect to database server"); //<--the error is displayed

---

### Post by dexter.deepak on 2008-07-13
try:
```
 conn = DriverManager.getConnection (""jdbc:mysql://localhost/experiment1?user=root&password=root");
```

---

### Post by balagosa on 2008-07-13
> **dexter.deepak said:**
> try:
```
 conn = DriverManager.getConnection (""jdbc:mysql://localhost/experiment1?user=root&password=root");
```

nope, that did not do it. and your code gave me an error due to **...(""jdbc:mysql...** <--the double quotes.

And yes, I tried **...("jdbc:mysql...** before posting this

---

### Post by dexter.deepak on 2008-07-13
please give the error message:
```
out.println(e);
e.printStackTrace();
```

---

### Post by balagosa on 2008-07-13
> **dexter.deepak said:**
> please give the error message:
```
out.println(e);
e.printStackTrace();
```

**java.lang.ClassNotFoundException: com.mysql.jdbc.Driver ** from "e"

So I guess I did not install it right huh?

---

### Post by dexter.deepak on 2008-07-13
yes, the better option is through synaptic.
i think you forgot editing the CLASSPATH in your .bashrc or maybe you forgot to relogin after editing it.

---

### Post by balagosa on 2008-07-13
> **dexter.deepak said:**
> yes, the better option is through synaptic.
i think you forgot editing the CLASSPATH in your .bashrc or maybe you forgot to relogin after editing it.

This is the description of **libmysql-java in Synaptics**
```
MySQL Connector/J is a JDBC-3.0 Type 4 driver, which means that it is
pure Java, implements version 3.0 of the JDBC specification
```

I know JDBC 4.0 is out there so I need advice...still go for Synaptics?

---

### Post by CptPicard on 2008-07-13
Synaptic has nothing to do with it, and in web apps you probably shouldn't rely on the user's CLASSPATH variable, as I suspect Tomcat doesn't care about it.

The issue is certainly that the driver class is not on the app's classpath, so there are essentially two choices... put the driver .jar in your Tomcat's common/lib or server/lib (I forgot which one it should be), or alternatively try sticking the driver into your web app's WEB-INF/lib directory. IIRC the db driver has to be in one of the server's directories though.

---

### Post by dexter.deepak on 2008-07-13
you can edit the classpath by adding a line like this :
```
export CLASSPATH=$CLASSPATH:/usr/share/java/mysql-connector-java-5.0.4.jar:.
```
this is mine, as i have the connector in /usr/share/java
you have to point to the directory, you have used for installing the connector.
after editing,relogin.

---

### Post by balagosa on 2008-07-13
> **dexter.deepak said:**
> you can edit the classpath by adding a line like this :
```
export CLASSPATH=$CLASSPATH:/usr/share/java/mysql-connector-java-5.0.4.jar:.
```
this is mine, as i have the connector in /usr/share/java
you have to point to the directory, you have used for installing the connector.
after editing,relogin.

I have already done this but have not yet relog-in. About the JDBC4.0...should I get it? 

I will post again 8hours from now, must go to sleep.

---

### Post by dexter.deepak on 2008-07-13
yes ,i agree with CptPicard.
i had a habit of compiling my servlets outside my server, so i had to use the classpath too ..
for the current use, place your .jar file in WEB-INF/lib of your appn...but for future, you should have it in common/lib too.

---

### Post by balagosa on 2008-07-13
I got a problem guys. I type in this command:

```
export CLASSPATH=$CLASSPATH:/usr/share/tomcat5.5/server/lib/mysqlconnector-java-5.1.6-bin.jar
```

and relog-in. When logged-on I open up a terminal and type **export**. The classpath is not there, I know something was not done right.

---

### Post by tinny on 2008-07-14
> **CptPicard said:**
> Synaptic has nothing to do with it, and in web apps you probably shouldn't rely on the user's CLASSPATH variable, as I suspect Tomcat doesn't care about it.

The issue is certainly that the driver class is not on the app's classpath, so there are essentially two choices... put the driver .jar in your Tomcat's common/lib or server/lib (I forgot which one it should be), or alternatively try sticking the driver into your web app's WEB-INF/lib directory. IIRC the db driver has to be in one of the server's directories though.

Yeah the classpath is not the way to go.

CptPicard is pointing you in the right direction.
```

WEB-INF/lib/mysql-connector-java-5.0.4.jar

```

Once I have the driver jar in the WEB-INF/lib/ folder this is how I obtain a db connection.

```

            Class.forName("com.mysql.jdbc.Driver");
            
            String dbHost = "localhost";
            String dbPort = "3306";
            String dbName = "testdb";
            String conStr = "jdbc:mysql://" + dbHost + ":" + dbPort + "/" + dbName +";";

            Connection con = DriverManager.getConnection(conStr,"username", "password");

```

Note: you dont need to call "getInstance"

Hope this does the business! :)

---

### Post by balagosa on 2008-07-14
the above suggestion did not work. I am losing hope at this and trying out another alternative. I need to pass this on Wednesday and time is running out.

My alternative:

Create a connection via java. Using JSP's page import, I will be able to connect to the database. **<%@ page import="(import classes)"%>**.

My question: How do I create a home folder for my files(Sorry, noob here)? I am using the **ROOT** folder currently but I would like to have a specific folder per Homework. Will the correct folder be at **/usr/share/tomcat5.5-webapps/(home_folder)**?

---

### Post by balagosa on 2008-07-14
I have found this [site]("http://www.fankhausers.com/tomcat/jdbc/"). But I have no idea how to edit /etc/init.d/tomcat5.5.

---

### Post by CptPicard on 2008-07-14
IMO you shouldn't configure a "production" server with init scripts and the like for development purpose (and I really don't quite understand why you'd have to edit the init script in the first place). You're better off just grabbing a copy of Tomcat from Apache, uncompressing it in your own home directory and running it from there.

An even nicer alternative is using Netbeans which has an integrated Tomcat which is very easy to develop against.

---

### Post by balagosa on 2008-07-14
I am forcing myself not to use NetBeans because I want to do it the hard way. During examinations we will not be allowed to use NetBeans, only the ever-loyal Notepad is allowed.

That is why I am busting my balls for this Connection. One thing I dont like about NetBeans is the crashes which happens every 15mins. It is frustrating when it crashs and I forget to save.

---

### Post by balagosa on 2008-07-14
You know what is weird, NetBeans can connect to database and I dont know how it did. The Connector/J is located at ~/netbeans-6.1/ide9/modules/ext/(Driver).

Be with you peepz in the morning.

---

### Post by tinny on 2008-07-15
> **balagosa said:**
> I am forcing myself not to use NetBeans because I want to do it the hard way. During examinations we will not be allowed to use NetBeans, only the ever-loyal Notepad is allowed.

That is why I am busting my balls for this Connection. One thing I dont like about NetBeans is the crashes which happens every 15mins. It is frustrating when it crashs and I forget to save.

Just get something working! Then reverse engineer it. Small steps.

Crashing every 15 min??? Ive never seen that.

---

### Post by balagosa on 2008-07-15
Big Problem! I do not know what I have done, but now localhost:8180 is showing blank(no content). 

But I know it is running.

The things I have done:
1) ln -s /etc/tomcat5.5/conf /usr/share/tomcat5.5
2) replaced conf.xml (but I stored a back-up and reloaded it)
3) replaced server.xml (but I stored a back-up and reloaded it)

---

### Post by balagosa on 2008-07-15
never mind...got it working again.

I followed a guide located at: Tutorials and Tips.

What is even greater is I got a connection from database!

The Problem before:
on my /usr/share/tomcat/ folder, there should be a **webapps** folder, and as CptPicard said, I must place the driver inside the ../webapps/WEB-INF/lib/ folder. Now, on my new installation of tomcat it was pre-loaded with a webapps folder. Inside ../WEB-INF/lib I placed the driver and VOILA! It worked! 

I entered **locate webapps** in terminal and I located a **/usr/share/tomcat5.5/webapps**. But when i did **ls /usr/share/tomcat5.5/webapps/** it returned a **No directory found.** It is not hidden as I did the latter comman with **ls -A ..**.

I am willing to find out why this is the case but for the meantime, I have no idea. Can anyone help me on this?

---

### Post by balagosa on 2008-07-15
bumperz

:lolflag:

---

### Post by theDaveTheRave on 2008-11-26
Hi all.

I'm having a similar issue, and I don't want to set up a webserver right at this moment... I want to set a little working application to run an auto update of files into a MySQL DBase

However, I haven't had time to really look at this thread, and I get the feeling it May have the solution to my problem... I'll have to work on it tonight / tomorrow.

My boss isn't going to be impressed as I thought that this little application was going to work without any problems.

The reference that I have says nothing about needing to set up a web server for this to work, and as everything is initially going to be on a single terminal for "proof of principle" I see no reason why I should have to :confused:

Right now I'm off home! I'll report back in the morning if things are were a success

however here is my story so far...

I'm trying to connect to a mysql dbqse (ver 6.0) via a little Java progy using JDK6 and all upto date JRE etc:

I keep getting an error for the class not found exception

My environment variables are: (copy and paste from the env variables in XP Pro)

path=C:\Sun\SDK\bin;F:\Devel\Wachabe\GetMySQLUsers;C:\Sun\ConnectorJ\mysql-connector-java-5.1.7\mysql-connector-java-5.1.7-bin.jar

classpath=.;C:\Program Files\Java\jre1.5.0_06\lib\ext\QTJava.zip;C:\Sun\ConnectorJ\mysql-connector-java-5.1.7\mysql-connector-java-5.1.7-bin.jar;F:\Devel\Wachabe\GetMySQLUsers

I have tried all the obvious things from this and other forums.

Ensured that the path to the program is in both fields for path and classpath. but still no luck.

The program will compile fine, I have confirmed that the connector is available in netbeans in the <tools | libraries> section and that it is located in the correct place etc etc.

I have 3 classes. 

---------contains the ,ain class main----------
[code]

package getmysqlusers;

import java.util.Scanner;
import java.sql.*;
import javax.sql.*;

public class GetMySQLUsers {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) throws SQLException 
     {
         //a scanner to read the data in from the cli
         //Scanner readCLI = new Scanner(System.in);

          //get mySQL user name
         // System.out.println("please enter user name"); //will be used to get the details from a GUI eventually
          String readName = new String("MyoGroup");//readCLI.nextLine(); //read the CLI into the variable.

          //get the mySQL pwd
         //System.out.println("please enter your password");
          String readPWD = new String("anonymous");//readCLI.nextLine();//get the next line of CLI data and pass to the new variable.

         ConnectSQL SQL = new ConnectSQL(readName, readPWD);
         
         System.out.println("username is " + SQL.getUser());
         System.out.println("pwd is " + SQL.getPWD());
    }

}
[\code]

---------controls the details of the user etc-------------

[code]
public class ConnectSQL 
{

package getmysqlusers;
import java.sql.*;
import java.sql.SQLException;
import javax.sql.*;
//insert instance variables here.
     
//string variables for holding the user name and pwd, collected from command line initially but later from a GUI login.
private String user;
private String pwd;
private connectToMysql login;//to open the connection to the database

//Call to the constructor


public ConnectSQL(String aUser, String thePWD) throws SQLException//note the try catch is handled in the connectToMysql Class.
{
     user = aUser;
     pwd = thePWD;
     login= new connectToMysql(getUser(), getPWD());
     login.toString();//used for testing.
}



//Methods for this class,  eg setter and getter methods.

public String getUser()//used for getting the user's name
     {
          return user;
     }

public String getPWD()
     {
          return pwd;
     }

}
[\code]

-----------handles the actual connection--- or rather doesn't!!-----------
[code]


package getmysqlusers;

//import getmysqlusers.ConnectSQL.*;//as thi

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import javax.sql.*;


public class connectToMysql 
{
//insert instance variables here.
private Connection con =null; //to hold the connection to the database.

//the connection is made up of 3 components as follows
private String URL; //the URL to the database.
private String schema;//the table schema to use. 
private String uName;//the name of the user.
private String MotDePass;//the users password.



//Call to the constructor <public nameOfClass(variables to pass to class)


public connectToMysql(String name, String pass) throws SQLException
{// grab the name and details from the GetMySQLUsers class.
     setURL("jdbc:mysql://localhost/mysql"); // test using a fixed string.
     setSchema("mysql");
     setUName(name);
     setPass(pass);
     //makeConnection();
     
     
//     String ODBCcon;
//     DBCcon = new String("DRIVER={MySQL ODBC 3.51 Driver}" +
//                   "SERVER=localhost" +
//                   "DATABASE=test" +
//                   "USER=venu" +
//                   "PASSWORD=venu"
//                   "OPTION=3");

//requiruires a try an catch
try{
    
    Class.forName("com.mysql.jdbc.Driver");
    con = DriverManager.getConnection(URL + uName + MotDePass);
}

catch(java.lang.ClassNotFoundException err)
     {    System.out.println("error in connecting.. again! " + err);}

catch(SQLException err)
{
System.out.println("error in connecting to DBase system " + err);
}



}
//Methods for this class,  eg setter and getter methods.
public void setSchema(String schema)
{
schema = new String(schema);
}
//get the DBname to be connected to.
public String getSchema()
{
return schema;
}

//set the URL for the database, if it needs to be changed
public String setURL(String url)
{
URL = url;//new String("jdbc:mysql:/localhost:3306/test1");
return URL;
}


//methods to set a username.
public String setUName(String name)
{
     uName = new String(name);
     return uName;
}
//methods to get a username.
public String getUName()
{
return uName;
}

//methods to set a password ~ it is never required to retrieve a password!
public String setPass(String mdp)
{
MotDePass = new String(mdp);
return MotDePass;
}

//the method to return details of the DB in use and the user who is logged in, overides the toString method of Object
public String toString()
{
String report = new String(getUName() +" is connected to the database " + getSchema());
return report;
}

//this method will make a connection to the database using the required driver.
//public void makeConnection()
//{//requiruires a try an catch
//try{      Class.forName("com.mysql.jdbc.Driver");      }
//catch(java.lang.ClassNotFoundException err)
//     {    System.out.println("error in connecting.. again! " + err);}
//}

}

[\code]

I think I have included everything.

I can confirm that using the username and password is fine in the monitor.

I have also tested this on my Ubuntu desktop and have the same problem, although there I also have an issue with the classpath not being retained? but I can solve that once I understand why I can see the class in the firstplace.

my thoughts are:

should I have the whole of the connectorJ;java file in the same folder as the rest of my package?
should I in fact have it as a class in my package? - this seems a bit ridiculous as I don't need to do this for the other java libraries that I am using!


What I'm going to try;

I'm going to work through the stuff on this thread and see if they solve my problems, but as I said at the top..I wasn't particularly keen on setting up a web server right at this moment!

help is greately appreciated.

for information.

I am developing a system for medical research, and I need to be able to connect to a database that the team is developing. Firstly however I would like to show that I can succesfully connect to MySQL localy and then from anywhere on the network (I intend to create an "applet" of some sort) - but that is a little further down the line, first I need to get this to work so as I can add in some functionality to auto update some tables (better still if I could do it on the fly... but the team insist on using another "closed source" front end for the time being untill I can get this to function satisfactorily (which seems more than fair enough).

thanks again in advance.

David

---

