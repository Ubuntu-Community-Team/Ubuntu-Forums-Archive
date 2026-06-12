---
title: "HOWTO: ADempiere Installation on Ubuntu 7.04 (with PostgreSQL 8.2 and PL/Java )"
date: 2008-03-16
forum: Outdated Tutorials &amp; Tips
---

### Post by yaloveda on 2008-03-16
[B]
- Requirements [/B][LIST]
[*] [Java JDK for Linux]("http://java.sun.com/javase/downloads/index.jsp")
[*] [Adempiere <VERSION> Zip Archives]("http://sourceforge.net/project/showfiles.php?group_id=176962")
[*] [PostgreSQL]("http://www.postgresql.org/download/")
[*] [Pljava]("http://www.posterita.org/share/pljava.zip")[/LIST]**- Configuring your JAVA HOME and ADEMPIERE HOME **[LIST]
[*] Copy the Adempiere_<VERSION>.zip to your home directory for e.g. /home/user/
[*] Right click on the zip file and do extract here
[*] It will create a folder Adempiere with all the its files and folders[/LIST][LIST]
[*] Go to your home directory /home/user/ on your file browser
[*] Go to View -->> Show Hidden Files on the menu bar ( or simply Ctrl + h )
[*] Open **.profile** file and add the following lines at the bottom[/LIST]export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.00/
 export ADEMPIERE_HOME=/home/user/Adempiere/
 
(change "user" with the name of your user directory and check the java directory to make sure the name is correct)[LIST]
[*] You need to logout and relogin for it to take your JAVA HOME and ADEMPIERE HOME[/LIST]**- Installing and Configuring PostgreSQL for Pljava **[LIST]
[*] Go to System --> Administration -->Synaptic Package Manager
[*] Search for JDK and PostgreSQL and pgAdmin3
[*]Choose sun-6-JDK for java
[*]Choose PostgreSQL 8.2
[*]Choose pgAdmin3
[*] Right Click and do Mark for installation for all of them
[*] Do Apply
[*] It will download and install PostgreSQL, JDK java and PGadmin3 for you
[*] Download the PLjava from [PGfoundry.org]("http://pgfoundry.org/frs/download.php/1597/pljava-i686-pc-linux-gnu-pg8.2-1.4.0.tar.gz")
[*] For 64bit users, download from [pljava64bit]("http://www.simit.com.my/download/pljava-pg8.2-64.zip") from [Sim IT Sdn Bhd]("http://www.simit.com.my/")[/LIST][LIST]
[*] For other versions of PostgreSQL, you can download  pljava at [here]("http://pgfoundry.org/frs/?group_id=1000038&release_id=1024").[/LIST]You will need root rights to proceed[LIST]
[*] Once PostgtreSQL has been installed, Open a terminal
[*] Do ***su*** and and enter your password (to login as root)
[*] Do ***passwd postgres*** to set the user postgres a password which is required
[*] ***gedit /etc/postgresql/8.2/main/pg_hba.conf***
[*] Change the authentication method to **trust**
[*] Add your database host IP under IPv4 if you are on a network (in my case my IP is 192.168.0.161)[/LIST]# Database administrative login by UNIX sockets
  local   all         postgres                          trust
  # TYPE  DATABASE    USER        CIDR-ADDRESS          METHOD
  # "local" is for Unix domain socket connections only
  local   all         all                               trust
  # IPv4 local connections:
  host    all         all         127.0.0.1/32          trust
  host    all         all         192.168.0.161/24      trust
  # IPv6 local connections:
  host    all         all         ::1/128               trust[LIST]
[*] Unzip the pljava.zip to /op/[/LIST]unzip pljava.zip -d /opt/[LIST]
[*] ***gedit /etc/postgresql/8.2/main/postgresql.conf***[/LIST]Look for listen_addresses and uncomment it i.e. remove the **#** and replace **localhost** by a *****[LIST]
[*] For pljava you will need these variable and add these lines to **postgresql.conf**[/LIST]dynamic_library_path = '\$libdir:/opt/pljava'
  custom_variable_classes = 'pljava'
  pljava.classpath = '/opt/pljava/pljava.jar'[LIST]
[*] Now edit /etc/ld.so.conf[/LIST]***gedit /etc/ld.so.conf***[LIST]
[*] Add these lines to ld.so.conf[/LIST]$JAVA_HOME/jre/lib/i386
  $JAVA_HOME/jre/lib/i386/client
  $JAVA_HOME/jre/lib/i386/native_threads
  $JAVA_HOME/jre/lib/i386/server[LIST]
[*] Do **ldconfig** to reload the configuration[/LIST][LIST]
[*] Now restart the PostgreSQL Server[/LIST]su - postgres
  ***/etc/init.d/postgresql-8.2 restart***[LIST]
[*] Now go to Applications --> System tools --> pgAmin III[/LIST][[IMG]http://www.posterita.org/mediawiki/images/1/1e/PgAdmin.png[/IMG]]("http://www.posterita.org/mediawiki/index.php/Image:PgAdmin.png")  PgAdmin III[LIST]
[*] Do a New Server Register Registration[/LIST][[IMG]http://www.posterita.org/mediawiki/images/7/78/Server.png[/IMG]]("http://www.posterita.org/mediawiki/index.php/Image:Server.png")  New Server Registration[LIST]
[*][LIST]
[*]Enter the database host IP
[*]Give a description
[*]Enter the password that you have set for user postgres[/LIST] [/LIST]**- Creating a role and database **[LIST]
[*] Create a role as adempiere with password adempiere and give it all privileges[/LIST][[IMG]http://www.posterita.org/mediawiki/images/5/59/Role.png[/IMG]]("http://www.posterita.org/mediawiki/index.php/Image:Role.png")  New Role[LIST]
[*] Create a database and assign the owner to adempiere[/LIST][[IMG]http://www.posterita.org/mediawiki/images/3/38/Database.png[/IMG]]("http://www.posterita.org/mediawiki/index.php/Image:Database.png")  New Database



 Alternatives:[LIST]
[*] Open a terminal and type in[/LIST][[IMG]http://www.posterita.org/mediawiki/images/b/b5/Postgresql.png[/IMG]]("http://www.posterita.org/mediawiki/index.php/Image:Postgresql.png")  Create User/Role and Database



 **- Installing Pljava **[LIST]
[*] To proceed with pljava installation you will need postgresql.jar
[*] Login as root on a terminal
[*] Copy it postgresql.jar and put it /opt/pljava (do it under root)[/LIST]cp /home/user/Adempiere/lib/postgresql.jar /opt/pljava
  cd /opt/pljava
  java -cp postgresql.jar:pljava.jar:deploy.jar org.postgresql.pljava.deploy.Deployer -database adempiere -user adempiere -password adempiere -install
**- Issues with libjvm.so **[LIST]
[*] Edit /etc/ld.so.conf as root[/LIST]***su***
  ***gedit /etc/ld.so.conf***[LIST]
[*] Replace $JAVA_HOME and put the exact path (/home/user/jdk1.6.0/) and it should be as follows[/LIST]/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client
  /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/native_threads
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/server[LIST]
[*] Do **ldconfig** to reload the configuration[/LIST][LIST]
[*] Install your pljava[/LIST]**- Importing the database dump **[LIST]
[*] Go to pgAdminIII
[*] Connect to the server
[*] Go to Adempiere database and drop cascade sqlj schema
[*] Now you can import your database
[*] Open a terminal and type in[/LIST]su - postgres
  psql -d adempiere </home/user/Adempiere/data/Adempiere_pg.dmp
**- Export/Backup Database **[LIST]
[*] Open a terminal and type in[/LIST]su - postgres
  pg_dump -U username -cif > /home/user/filename.dmp dbname
- **Installing Adempiere **[LIST]
[*] Go to $ADEMPIERE_HOME
[*] Run RUN_setup.sh and enter your credentials, test and save
[*] Once it's done, then run RUN_Adempiere.sh to start Adempiere[/LIST]Credentials:
Java Home: This is the path to your java home, it is suppose to be set automatically.
Adempiere Home: This is the path to your Adempiere home, it is suppose to be set automatically.

Application Server: "Your computer name"
Web Port: 8088
SSL: 4443
Database Server: localhost
Database Type: postgresql
Database Name: adempiere
Database Port: 5432
Database User: adempiere




**- Issues with RUN_Adempiere.sh**
- If you got a "Permission denied" error when you try to install Adempiere , go to Adempiere folder under root and change the permissions of the whole folder to allow it to be installed.[LIST]
[*]Special thanks for RealPSL and Dantam for there help on Ubuntu forums
[*]Most of the components of this guide was taken from [Postirita]("http://www.posterita.org/mediawiki/index.php/PostgreSQL_Installation_on_Ubuntu_%28with_PL/Java%29_for_ADempiere#Installing_Adempiere") and  [URL="http://www.adempiere.com/wiki/index.php/Manual_postgres_setup_in_linux"]Adempiere Wiki 
[/URL][/LIST]

---

### Post by zazuge on 2008-05-11
Hello
there thanks for the howto but i got some problem on
```

java -cp postgresql.jar:pljava.jar:deploy.jar org.postgresql.pljava.deploy.Deployer -database adempiere -user adempiere -password adempiere -install

org.postgresql.util.PSQLException: ERREUR: n'a pas pu charger la bibliothèque «/opt/pljava/pljava.so»: /opt/pljava/pljava.so: undefined symbol: SetUserId
        at org.postgresql.core.v3.QueryExecutorImpl.receiveErrorResponse(QueryExecutorImpl.java:1548)
        at org.postgresql.core.v3.QueryExecutorImpl.processResults(QueryExecutorImpl.java:1316)
        at org.postgresql.core.v3.QueryExecutorImpl.execute(QueryExecutorImpl.java:191)
        at org.postgresql.jdbc2.AbstractJdbc2Statement.execute(AbstractJdbc2Statement.java:452)
        at org.postgresql.jdbc2.AbstractJdbc2Statement.executeWithFlags(AbstractJdbc2Statement.java:337)
        at org.postgresql.jdbc2.AbstractJdbc2Statement.execute(AbstractJdbc2Statement.java:329)
        at org.postgresql.pljava.deploy.Deployer.initJavaHandlers(Deployer.java:474)
        at org.postgresql.pljava.deploy.Deployer.main(Deployer.java:269)
```
and it got nothing to do with libjvm.so
i've found report about pljava being broken and all.
but no solution out there.

---

### Post by gach on 2008-09-29
Am also getting the same error as zazuge. I believe the error is actually in logging in to postgres.

Anyone to come to the rescue!

---

### Post by CodEnemy on 2009-01-18
> **gach said:**
> Am also getting the same error as zazuge. I believe the error is actually in logging in to postgres.

Anyone to come to the rescue!

Make sure you did this step:
```

*  For pljava you will need these variable and add these lines to **postgresql.conf**:

[COLOR="blue"]dynamic_library_path = '\$libdir:/opt/pljava'
custom_variable_classes = 'pljava'
pljava.classpath = '/opt/pljava/pljava.jar'[/COLOR]
```

then restart your postgresql server and execute the command:

```
java -cp postgresql.jar:pljava.jar:deploy.jar org.postgresql.pljava.deploy.Deployer -database adempiere -user adempiere -password adempiere -install
```


it should run with no problems!

---

### Post by johnaaronrose on 2009-04-08
yaloveda,

Followed your Howto using Intrepid with Postgres 8.3. All good until "drop cascade sqlj schema" for database adempiere. Could you explain how this is done?

---

### Post by johnaaronrose on 2009-04-10
CodEnemy,

Got to end of tutorial, only problem was that: whenI start adempiere using RUN_Adempiere.sh, Adempiere Connection window appears. I put in my computer name (JohnLaptop) for Application Server & 8088 for the Application Port. Are these correct? I clicked Test Application Server button and pop window displayed stating that can't connect JohnLaptop:1099 (1099 was Adempiere default Application Port, which I changed).

PS I tried test of pljava install by select & from rv_openitem in sql window of pgadmin3, but it didn't find that table. I got that tip from Adempiere's  'Talk Ubuntu Install Howto' article. Is that test correct?

---

### Post by chokorox on 2009-10-16
im installig the DB  "RUN_ImportAdempire.sh", and start the instalation, but in the middle of instalation broken and close the terminal, the ADempiere data base isn't install, please help!

---

### Post by plavania on 2010-06-15
Please visit the Blog section of Walking Tree on "How To's" of Adempiere. Walking Tree has extensive experience in Adempiere and built there own ERP product EagleRP on top of Adempiere. They have a strong presence in ERP Implementation and Customizations around Adempiere, for more than 4 years now with a clientele from different verticals. By end of 2010, the company is publishing a book on "How To's" for Adempiere to make life easier for all fellow implementers.
Incase you do not find the information that you are looking for already existing on their blog, try posting a question, and you can be assured of a prompt and overwhelming reply.
[http://www.walkingtree.in](http://www.walkingtree.in)
[http://wtcindia.wordpress.com/](http://wtcindia.wordpress.com/)

---

