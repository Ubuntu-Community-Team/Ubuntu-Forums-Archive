---
title: "odbc in Ubuntu?"
date: 2010-02-05
forum: Programming Talk
---

### Post by JayKay3000 on 2010-02-05
I've got a program in java that can create and edit databases using SQL and  you can also select different databases and see them within the program.

It is currently running on the microsoft odbc driver in windows.

For kicks i though i'd see if I could get it to run under ubuntu but the ODBCconfig does not seem to find any drivers. I've been to the package manager and grabbed a bunch of odbc stuff but only a sqllite has so far shown up.

I've also tried the program. Databases Access Properties which does see the ODBC drivers but when I add the connection string jdbc:odbc:network_ports.mdb the program says 'cannot find the driver'

Would installing the Real Ms office under wine allow this driver to be seen or is there a Open Office driver.

Dunno if anyone can point me in the right direction. I'm pretty sure I just need the right driver.

Thanks

Joss.

---

### Post by Ferrat on 2010-02-05
you need JDBC, I think that is what you are looking for it's a Java connection to SQL.

---

### Post by resander on 2010-02-05
I have used odbc from Ubuntu 8.10 using the free unixODBC driver that can be installed from the Ubuntu Synaptic Manager. I believe it available in other distros too. I used unixODBC to connect my own programs (written in C++) to databases. 

I first obtained the shared objects driver libraries from the database vendors. That was easy, just went to their websites and downloaded. The difficult bit was finding what configuration parameters to use in odbc.ini and odbc.inst files. The vendor documentation did not tell you much for Linux or gave wrong information. After about three weeks of scouring the web I managed to connect to Oracle Express, DB2, SQL Anywhere, MySQL and Mimer SQL via the unixODBC driver. A real nightmare!

I have not had any luck running any programs of note under Wine except Solitaire. Check at winehq.org if the MS Office programs work. 

I don't know if unixODBC supports Java. unixODBC.org where the free unixODBC driver comes from has a mailing list. Just send an email and ask.

I have zero knowledge of Java or JDBC, but you may be lucky and find that JDBC hides all ODBC driver complexities.

---

### Post by oldfred on 2010-02-05
Just as in windows you have to separately set up your ODBC connections so you can use them. You did not say which SQL database you want to connect to.

see A neophyte's guide in 
[http://www.unixodbc.org/](http://www.unixodbc.org/)
Doing this as root will create and edit the /usr/local/etc/odbcinst.ini (for the driver info) and /usr/local/etc/odbc.ini (for the system DSN) files.

[http://www.easysoft.com/developer/interfaces/odbc/linux.html](http://www.easysoft.com/developer/interfaces/odbc/linux.html)
[http://www.easysoft.com/developer/interfaces/odbc/linux.html#dsn_install_unixodbc](http://www.easysoft.com/developer/interfaces/odbc/linux.html#dsn_install_unixodbc)

Uses a different database but shows the screens and porcess you have to go thru to set up an ODBC connection.

For a different database sqlite but shows ODBCConfig
[http://schoolsplay.wikidot.com/wiki:howtoopendatabaselinux](http://schoolsplay.wikidot.com/wiki:howtoopendatabaselinux)

---

### Post by resander on 2010-02-05
Was curious and used the Synaptic Manager on my Ubuntu 8.10 to search on jdb. Found some JDBC drivers for MySQL, Postgres and SQL Server. Then searched on db and found sun-javadb-core that contains the database server, JDBC and some utilities. There is some documentation too in sun-javadb-javadoc and libc3p0-java-doc.

My guess is that these files are to be installed and used for Java instead of unixODBC, but again I don't know, so it may still be wise to find out if unixODBC can be used for Java.

I don't know if JDBC also uses odbc.ini and odbc.inst configuration text files. If it does you can use a simple text editor like gedit to define them. There is no need to use GUI front ends like odbcconfig that only builds the text. I found that some odbc gui frontends (don't remember which) were buggy and could not generate correct texts.
My guess though is that JDBC handles the configuration differently.

---

