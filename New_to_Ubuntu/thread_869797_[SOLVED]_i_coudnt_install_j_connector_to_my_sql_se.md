---
title: "[SOLVED] i coudnt install j connector to my sql server"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by dilanka007 on 2008-07-25
hello guys..

i m using ubuntu gutsy, and i am a ubuntu newby as well.
i ve installed mysql 5.1 using apt. andnow i want to install connector/j(Jdbc) to that my sql. before connecting i guess i need to install connector/j. i downloaded the file from mysql site which is a .tar.gz file and it is sitting on my desktop. i have no clue of how to install..
pls help....
thank you in advance...

---

### Post by Iceni on 2008-07-25
> **dilanka007 said:**
> hello guys..

i m using ubuntu gutsy, and i am a ubuntu newby as well.
i ve installed mysql 5.1 using apt. andnow i want to install connector/j(Jdbc) to that my sql. before connecting i guess i need to install connector/j. i downloaded the file from mysql site which is a .tar.gz file and it is sitting on my desktop. i have no clue of how to install..
pls help....
thank you in advance...

What does the archive contain? (yes, tar.gz is like .zip in windows). Extract it:o

---

### Post by dilanka007 on 2008-07-25
actually, i ve downloaded **mysql-connector-java-5.1.6.tar.gz** from mysql site. and now its in my desktop. i did untar it then u get a noraml folder named **mysql-connector-java-5.1.6.**
but i want an A to Z explanation on how to install it in to my systemm. as of now its just a folder sitting on my desktop.
i dont know how to install it using terminal.

i hope u got my problem.
i need a step by step explanation on how to install it.
i face this problem whenever i am to insatll anything which is not on the synaptic pacages.

thank you in advance

---

### Post by Potatoj316 on 2008-07-25
could you paste the output of this terminal command
```
cd mysql-connector-java-5.1.6
ls -l
```

also what is this mysql-connector-java suposed to do?

---

### Post by dilanka007 on 2008-07-25
dilanka@dilanka-laptop:~/applications$ cd mysql-connector-java-5.1.6
dilanka@dilanka-laptop:~/applications/mysql-connector-java-5.1.6$ ls -l
total 948
-rw-r--r-- 1 dilanka dilanka  42179 2008-03-05 16:27 build.xml
-rw-r--r-- 1 dilanka dilanka 164454 2008-03-05 16:27 CHANGES
-rw-r--r-- 1 dilanka dilanka  19451 2008-03-05 16:27 COPYING
drwxr-xr-x 2 dilanka dilanka   4096 2008-07-24 22:10 docs
-rw-r--r-- 1 dilanka dilanka   5256 2008-03-05 16:27 EXCEPTIONS-CONNECTOR-J
-rw-r--r-- 1 dilanka dilanka 703265 2008-03-05 16:27 mysql-connector-java-5.1.6-bin.jar
-rw-r--r-- 1 dilanka dilanka   1310 2008-03-05 16:27 README
-rw-r--r-- 1 dilanka dilanka   1355 2008-03-05 16:27 README.txt
drwxr-xr-x 7 dilanka dilanka   4096 2008-03-05 16:27 src


i want to interface a java programme with a mysql database. for us to do that i need that jdbc installed here.

---

### Post by jamesrfla on 2008-07-25
If you type this command in it will download and install my sql.
sudo apt-get install mysql

---

### Post by dilanka007 on 2008-07-25
hey i have already installed mysql. i want a jdbc to be connected to mysql server where i can inteface it with a java programme.
so i need the j connector to be installed.

---

### Post by jamesrfla on 2008-07-25
> **dilanka007 said:**
> hey i have already installed mysql. i want a jdbc to be connected to mysql server where i can inteface it with a java programme.
so i need the j connector to be installed.

Maybe try sudo apt-get install j connector or sudo aptitude and search for it in their.

---

### Post by Nepherte on 2008-07-25
Aren't you supposed to import that archive in your java program?

---

### Post by dilanka007 on 2008-07-25
hey ya .. may be..
i was not sure abt it..
i thought i need t install j connector ..
cos i have never connected a sql in to a java programme..
but i guess u may be rite..
but can somebody please help me ..
has anybody connected a java programme to a mysql server on ubuntu..
and has he done it by just importing the arcjive file in the java programme or is there anything else to be done

thanks again

---

### Post by Nepherte on 2008-07-25
Jup I did (again, by importing the jdbc library in the java program code). This is an example code of how to accomplish it in java:
```
import java.sql.*;

public class Database {
	
   public Database() {}
   
   public static void main(String[] args) {
   	/** 
   	 * load jdbc driver
   	 */
   	try {
           // The newInstance() call is a work around for some
           // broken Java implementations
           Class.forName("com.mysql.jdbc.Driver").newInstance();
       } catch (Exception ex) {
           // handle the error
       }
       
       /**
        * establish connection & update
        */
       try {
           Connection conn =  DriverManager.getConnection("jdbc:mysql://ertvelde/peno3-cwb2", "xxx", "xxxx");
           //conn.createStatement().executeUpdate("INSERT INTO users(first_name, last_name, country_code) VALUES ('Jimmy', 'Anderson', 'UK');");
           ResultSet rs = conn.createStatement().executeQuery("SELECT * FROM users");
           ResultSetMetaData rms;
       
           while(rs.next()) {
        	System.out.println(rs.getString("first_name") + " " + rs.getString("last_name"));
           }
       } catch (SQLException ex) {
           // handle any errors
           System.out.println("SQLException: " + ex.getMessage());
           System.out.println("SQLState: " + ex.getSQLState());
           System.out.println("VendorError: " + ex.getErrorCode());
       }
   		
   }
}
```

---

### Post by dilanka007 on 2008-07-26
ohh thank you this is great...
where did u locate ur **mysql-connector-java-5.16** folder.
i m struggling a bit with the folder structure in ubuntu..
cos for u to import it in your programme like that it should be in ur java installed folder.
but so far it is great.
and thank you very much

---

### Post by Nepherte on 2008-07-26
You don't have to place the jdbc driver in a specific folder, you just have to add it to your 'java build path' in the program you use to program (that's how I do it anyways, don't know another way). I use eclipse so what I'm about to say only works with that program. Just place it somewhere in your home folder for example, or create a new map for it. Open up eclipse. Right click on the project you are working on and choose properties. Choose Java Build Path in the left menu and the libraries tab at the top. Choose add external jar and point it to mysql-connector-java-5.1.6-bin.jar. Now you should be able to use the library like any other.

---

### Post by dilanka007 on 2008-07-26
thanks i get this solved my problem. i am using netbeans and eclipse. and i guess i got the point now.. thank u again

---

### Post by IAmBecauseWeAre on 2008-08-08
> **dilanka007 said:**
> hey i have already installed mysql. i want a jdbc to be connected to mysql server where i can inteface it with a java programme.
so i need the j connector to be installed.
Download Connect/J from MySql (you probably already did that....)

Unzip it. 

Open a terminal window and sudo -i

Copy or move the unzipped folder to a sensible location, if needed. I chose /usr/local which may or may not be sensible.

Create a link to the folder to ease your typing needs:
 ln -s mysql-connector-java-5.1.6 mysql

Change ownership to root 
 chown root:root mysql-connector-java-5.1.6

When you execute your compiled class, reference the path to the connector jar:
 java -cp .:/usr/local/mysql/mysql-connector-java-5.1.6-bin.jar SomeClassNameGoesHere

This is what I did and it worked. There are no doubt tidier approaches.

Good luck

---

### Post by kabipokotho on 2009-05-11
Hello Everyone!

I'm new to the forum

I just got started on Java programming on my Kubuntu/Ubuntu box
I'm using Linux Netbeans 6.5, MySQL Server 5.1 and JDBC 5.1.6

Now this is what i did...

1 -- I downloaded the Zipped version (Windows) of Connector J from [http://www.mysql.com/](http://www.mysql.com/)
2 -- I unzipped the package and put it on my Kubuntu Desktop.
3 -- I then opened Konsole (Start > Applications > System > Terminal)
4 -- Then i typed the following commands to copy the file into the required directory bellow

kabi@koolhost:~$ cd
kabi@koolhost:~$ cd Desktop/
kabi@koolhost:~/Desktop$ sudo mv mysql-connector-java-5.1.6-bin.jar /usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/ext

[sudo] password for kabi:

kabi@koolhost:~/Desktop$




Those commands should move your Connector J to /usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/ext
This is the location of your extentions to your Java distribution

The assumption is you have successfully installed your Java separately, not with NetBeans for example.


Enjoy

[email]kabipokotho@yahoo.com[/email]

---

