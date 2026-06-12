---
title: "Install LedgerSMB on Ubuntu Dapper"
date: 2006-12-02
forum: Outdated Tutorials &amp; Tips
---

### Post by brucehohl on 2006-12-02
Ledger-SMB ([www.ledgersmb.org](www.ledgersmb.org)) is recent fork of SQL-Ledger ([www.sql-ledger.org)](www.sql-ledger.org)).  It is an accounting application for small businesses.  It uses PERL, PostgreSQL, and Apache.  I think this package is interesting and promising.

=============================================
Install of Ledger-SMB on Ubuntu Dapper 6.06.1 
=============================================

1- Used Synaptic to install following and dependencies: 
    Apache2 2.0.55
    PostgreSQL 8.1.4
    postgresql-client 7.5.16.1
    wwwconfig-common 0.0.44
    Perl 5.8.7
    libdbd-pq-perl 1.43
    libdbi-perl 1.50
    libmime-lite-perl 3.01
    libmodule-build-perl 0.26
    libhtml-parser-perl 3.48
    libversion-perl 0.52


2- Download liblocale-maketext-lexicon-perl_0.62-1_all.deb from:
    [http://packages.ubuntulinux.org/edgy/perl/liblocale-maketext-lexicon-perl](http://packages.ubuntulinux.org/edgy/perl/liblocale-maketext-lexicon-perl)

    move to /opt/ledgersmb
    # mkdir /opt/ledger-smb
    # mv liblocale-maketext-lexicon-perl_0.62-1_all.deb /opt/ledgersmb


3- Download ledgersmb-1.1.99b3-debs.tar.gz from:
    [http://sourceforge.net/project/showfiles.php?](http://sourceforge.net/project/showfiles.php?) \
    group_id=175965&package_id=208359&release_id=465891

   move to /opt and extract:
    # mv ledgersmb-1.1.99b3-debs.tar.gz /opt
    # tar -zxvf ledgersmb-1.1.99b3-debs.tar.gz
    # mv /opt/ledgersmb-1.1.99b3-debs/* /opt/ledgersmb
    # rmdir /opt/ledgersmb-1.1.99b3-debs

   
4- Install packages with dselect:
    # dselect
    [1] Access
        Mounted File System
        Q1 - none
        Q2 - /opt/ledgersmb
        Q3 - scan
        Answer none to final four questions

    [2] Update

    [3] Select
        Use + to select package(s)

    [4] Install

    [5] Quit

   
5- edit /etc/ledger-smb/ledger-smb.conf
    change made as follows:
    set "latex :"
    set "DBPassword = admin"


6- PostgreSQL setup:
    [1] Set DB access:
        /etc/postgresql/8.1/main/pg_hba.conf
        local   all   all                   trust

    [2] Create ledgersmb user
        # su postgres
        $ createuser -P ledgersmb
        password = admin
        superuser = y
    
    [3] Create PostgrSQL database
        # su postgres
        $ createlang plpgsql template1
        $ createdb -U ledgersmb ledgersmb

    [4] Set up the users tables using provided file:
        $ psql -U ledgersmb ledgersmb
        ledgersmb=# \i /usr/share/ledgersmb/sql/Pg-central.sql

    [5] Set the admin password:
        $ psql -U ledgersmb ledgersmb
        ledgersmb=# update users_conf set password = md5('admin');
        

7- Company and User setup:
   Connect to: [http://localhost/ledger-smb/admin.pl](http://localhost/ledger-smb/admin.pl)

    [1] To set up a company:
        Click "Pg Database Administration" link.
        Host = localhost
        Port = 5432
        User = ledgersmb
        Password = admin
        Connect to = template1
        Superuser = ledgersmb
        Password = admin
        Click "Create Dataset"

    [2] Create Dataset = abc_company
        Chart of Accounts = US_Manufacturing
        Click "Continue"
        If successful a success page will appear.
        Click "Continue" to return to admin.pl

    [3] Click "Add User"
        Login = jsmith
        Password = jsmith
        Name = Joe Smith
        Company = ABC Company

        Driver = Pg
        Host = localhost
        Dataset = abc_company
        Port = 5432
        User = ledgersmb
        Password = admin

        Account type = Administrator
        Click "Save"
        
8- Login access: 
    Local:
    [http://localhost/ledger-smb/login.pl](http://localhost/ledger-smb/login.pl)
    login with user "jsmith" created above

    Local network:
    http://<IP_or_hostname_where_installed>/ledger-smb/login.pl
    login with user "jsmith" created above

9- Now go read /usr/share/doc/ledger-smb/LedgerSMB-manual.pdf.gz

---

### Post by GOwin on 2007-01-20
Too bad it's not available in the repositories yet. 

Debian packages are [availabe](http://sourceforge.net/project/showfiles.php?group_id=175965) from the project website:

---

### Post by sirmrmatt on 2007-02-27
I am trying to follow the above instructions on Edgy and am getting an error. At this point:

```

[4] Set up the users tables using provided file:
$ psql -U ledgersmb ledgersmb
ledgersmb=# \i /usr/share/ledgersmb/sql/Pg-central.sql
```

I get: ```
/usr/share/ledgersmb/sql/Pg-central.sql: No such file or directory
```

Any ideas?

---

### Post by sirmrmatt on 2007-03-02
I replaced all of the entries in the above tutorial from ledgersmb or ledger-smb

to ledger-smb only. Usernames, folders, etc. Kept it standard and it installed fine. Tutorial seems to drift in and out of using either.

Anyhow, now my problem is that Ledgersmb keeps saying "Access Denied!" when I try to logon to the admin.pl page. I keep typing "admin" as my password, which is what I set in the

```

[5] Set the admin password:
$ psql -U ledgersmb ledgersmb
ledgersmb=# update users_conf set password = md5('admin');
``` 

Any help?

- Matt

---

### Post by dominiquec on 2007-07-25
Hi, all,

I'm posting my own installation notes for LedgerSMB 1.2.7 on Ubuntu 6.06 LTS Server.  I still have to go through a second pass to make sure everything is correct.  I'm reasonably sure it is.


LedgerSMB 1.2.7 Installation on Ubuntu 6.06 LTS Server
======================================================
These are my installation notes for LedgerSMB 1.2.7 on Ubuntu 6.06 LTS Server, specifically, on a VMWare image of that version of Ubuntu.  The particular kernel on this image, verified through uname -a, is Linux ubuntu 2.6.15-26-server #1 SMP.

The steps below were lifted by and large from the INSTALL document of LedgerSMB, annotated for clarity.  The supplement is intended for people who are fairly familiar with Ubuntu system administration but do not as yet have deep expertise in LedgerSMB, Perl, Apache, and PostgreSQL.

My ultimate aim is to produce a automatic install script for LedgerSMB on a non-Internet connected Ubuntu server.  Not quite there yet, but this influences my decision to eschew interactive methods (e.g., CPAN) in favor of scriptable commands.

Download
========
For convenience, download the following components from their respective locations before proceeding:

LedgerSMB 1.2.7 	
([http://downloads.sourceforge.net/ledger-smb/ledgersmb-1.2.7.tar.gz](http://downloads.sourceforge.net/ledger-smb/ledgersmb-1.2.7.tar.gz))

Perl Config::Std Module 
([http://search.cpan.org/CPAN/authors/id/D/DC/DCONWAY/Config-Std-v0.0.4.tar.gz](http://search.cpan.org/CPAN/authors/id/D/DC/DCONWAY/Config-Std-v0.0.4.tar.gz))

Perl Class::Std Module 	
([http://search.cpan.org/CPAN/authors/id/D/DC/DCONWAY/Class-Std-v0.0.8.tar.gz](http://search.cpan.org/CPAN/authors/id/D/DC/DCONWAY/Class-Std-v0.0.8.tar.gz))

Perl Build Module 	
([http://search.cpan.org/CPAN/authors/id/K/KW/KWILLIAMS/Module-Build-0.2808.tar.gz](http://search.cpan.org/CPAN/authors/id/K/KW/KWILLIAMS/Module-Build-0.2808.tar.gz))

Perl Locale::Maketext::Lexicon Module
([http://search.cpan.org/CPAN/authors/id/A/AU/AUDREYT/Locale-Maketext-Lexicon-0.64.tar.gz](http://search.cpan.org/CPAN/authors/id/A/AU/AUDREYT/Locale-Maketext-Lexicon-0.64.tar.gz))

Perl Test::Tester Module
([http://search.cpan.org/CPAN/authors/id/F/FD/FDALY/Test-Tester-0.104.tar.gz](http://search.cpan.org/CPAN/authors/id/F/FD/FDALY/Test-Tester-0.104.tar.gz))

Perl Data:: Dump Module
([http://search.cpan.org/CPAN/authors/id/G/GA/GAAS/Data-Dump-1.08.tar.gz](http://search.cpan.org/CPAN/authors/id/G/GA/GAAS/Data-Dump-1.08.tar.gz))

Perl Test::Trap Module
([http://search.cpan.org/CPAN/authors/id/E/EB/EBHANSSEN/Test-Trap-v0.0.23.tar.gz](http://search.cpan.org/CPAN/authors/id/E/EB/EBHANSSEN/Test-Trap-v0.0.23.tar.gz))


Installation Part 1: Installing the Prerequisites and Code
==========================================================

0) Enable your server to retrieve from Universe and Multiverse repositories

In your favorite text editor, uncomment the following lines

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main universe



1) Install the LedgerSMB prerequisites.  

sudo apt-get install apache2 libdata-dumper-simple-perl libdbd-pg-perl libdbi-perl libhtml-linkextractor-perl  libhtml-parser-perl liblocale-maketext-lexicon-perl libmd5-perl libmime-lite-perl libmodule-build-perl libnet-tclink-perl libparse-recdescent-perl libversion-perl perl-modules postgresql-8.1 wwwconfig-common


2) Install Config::Std

	tar xzvf Config-Std-v0.0.4.tar.gz
	cd Config-Std-v0.0.4
	perl Makefile.PL
	make
	sudo make install

3) Install Class::Std

	tar xzvf Class-Std-v0.0.8.tar.gz
	cd Class-Std-v0.0.8
	perl Makefile.PL
	make
	sudo make install

4) Install Module::Build

	tar xzvf Module-Build-0.2808.tar.gz
	cd Module-Build-0.2808
	perl Makefile.PL
	make
	sudo make install

5) Install Locale::Maketext::Lexicon

	tar xzvf Locale-Maketext-Lexicon-0.64.tar.gz
	cd Locale-Maketext-Lexicon-0.64
	perl Makefile.PL
	make
	sudo make install

6) Install Data:: Dump, Test::Tester, and Test::Trap.  These are not absolutely essential but some parts of the Build test will fail if these are not present.



7) Unpack LedgerSMB, move the resulting directory to /var/www, and change ownership of files to www-data.

	tar xzvf ledgersmb-1.2.7.tar.gz
	sudo mv ledgersmb /var/www
	sudo chown -R www-data.www-data /var/www/ledgersmb



Installation, Part 2: Setting up the Database
=============================================

1) Set the password for PostgreSQL

	sudo -u postgres psql template1 (brings you to the Postgres interactive terminal)
	ALTER USER postgres WITH PASSWORD '*postgrespwd*> ';
	\q

2) Create the ledgersmb role in PostgreSQL:

	createuser --no-superuser --createdb --no-createrole -U postgres -h localhost --pwprompt --encrypted ledgersmb 

This will prompt for passwords: the first time, for the role ledgersmb's new password; the second time, for verification; and the third time, for the postgres password (see 1) to actually execute the command.

Note: with the default PostgreSQL installation in Ubuntu, add '-h localhost' to specify the local machine.  PostgreSQL will complain that authentication failed if this is not done.

3) Create the ledgersmb database.

	createdb -U ledgersmb -h localhost -O ledgersmb ledgersmb

4) Create the tables in the ledgersmb database using the database setup script.

	psql -U ledgersmb -h localhost -d ledgersmb -f /var/www/ledgersmb/sql/Pg-central.sql


5) Change the ledgersmb role's password.

	psql -U ledgersmb -h localhost -d ledgersmb
	UPDATE users_conf SET password = md5('ledgersmbpwd') where id=1;
	\q


Installation, Part 3: Setting up the Application
================================================
1) Create the ledgersmb.conf file.

	cd /var/www/ledgersmb
	sudo cp ledgersmb.conf.default ledgersmb.conf

Then, edit ledgersmb.conf so it reflects the following:

	[globaldb]
	DBname		= ledgersmb
	DBhost		= localhost
	DBport		= 5432
	DBUserName	= ledgersmb
	DBPassword	= ledgersmbpwd

2) Create the Apache configuration file using the given script.

	cd /var/www/ledgersmb
	sudo sh configure_apache.sh

The following dialog ensues:

	Which user does your web server run as?
	www-data
	Where do we copy the ledgersmb-httpd.conf file to?
	/var/www/ledgersmb
	Please restart your web server for the changes to take effect.

You need to copy the resulting ledgersmb-httpd.conf file to /etc/httpd.conf

	sudo cp /var/www/ledgersmb/ledgersmb-httpd.conf /etc/apache2/httpd.conf

3) Check the dependencies.

	cd /var/www/ledgersmb
	sudo perl Build.PL
	./Build test

If there are any errors, you can pipe the output to file, which you can then send to the LedgerSMB mailing list for consultation.

	./Build test > ~/build-result-summary.txt	
	./Build test 2> ~/build-result-detailed.txt	


4) Finally, restart the Apache server.

	sudo /etc/init.d/apache2 restart

---

### Post by bigbrownepaul on 2007-07-31
Thanks for the excellent write up if you need any testing of your script done just let me know

---

### Post by w_m0zart on 2007-08-16
Corrections in previous posting from dominiquec makes this posting unnecessary. Lot's of thanks goes to dominiquec for the clear step by step procedure about installing LedgerSMB.

---

### Post by dominiquec on 2007-08-22
Hi, Mozart,

Thanks very much for looking through the write-up and pointing out the typos.  Much appreciated.

One other crucial typo I made was in "Setting up the Application", number 2.  It should be

sudo cp /var/www/ledgersmb/ledgersmb-httpd.conf **/etc/apache2/httpd.conf**  

The changes in the httpd.conf file allow Apache to process the .PL files correctly.

---

### Post by w_m0zart on 2007-08-23
After the step by step procedure from dominiquec, I came closer, but not completely. Now Perl files were executed by Apache, instead of asking to save them. However invoking "http://localhost/ledgersmb/admin.pl" threw an "Internal Server Error".

Checking the Apache error log file in "/var/log/apache2" revealed following error:

Can't locate version.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/local/share/perl/5.8.7/Config/Std.pm line 3.
BEGIN failed- -compilation aborted at /usr/local/share/perl/5.8.7/Config/Std.pm line 3.
Compilation failed in require at LedgerSMB/Sysconfig.pm line 8.
BEGIN failed- -compilation aborted at LedgerSMB/Sysconfig.pm line 8.
Compilation failed in require at /var/www/ledgersmb/login.pl line 52.
BEGIN failed--compilation aborted at /var/www/ledgersmb/login.pl line 52.
[Fri Aug 24 04:12:37 2007] [error] [client 127.0.0.1] Premature end of script headers: login.pl

Searching Google for the "can't locate version.pm" resulted in advices about fixing something in cpan. (Same advice was by the way given in the Install text in ledgersmb-1.2.7.tar.gz). What I did was:

sudo cpan
get ExtUtils::MakeMaker
make ExtUtils::MakeMaker
test ExtUtils::MakeMaker
install ExtUtils::MakeMaker
get version
make version
test version
install version
exit

I guess the first four related to ExtUtils::MakeMaker were not relevant the my error and could be omitted. (But I have no chance to test this anymore)

Then after restarting Ubuntu, I typed [http://localhost/ledgersmb/login.pl](http://localhost/ledgersmb/login.pl) in a browser and lo and behold it seemed to work! It showed a proper LedgerSMB login screen.

But...

Checking the dependencies with:
$ perl Build.PL
Checking prerequisites...
 * Optional prerequisite Parse::RecDescent is not installed

Showed I do not have RecDescent installed. Why not install this rightaway with cpan:

sudo cpan
get Parse::RecDescent
make Parse::RecDescent
test Parse::RecDescent
install Parse::RecDescent
exit

Then again checking the dependencies with:
$ perl Build.PL
Checking prerequisites...
Looks good

Let's hope my computer is right. Can someone confirm my observations and conclusions?

---

### Post by clee991 on 2007-08-25
Thanks for the detailed install . i have followed it carefully, installing to feisty but I am getting > Error! 

No GlobalDBH Configured or Could not Connect when I go to [http://localhost/ledgersmb/login.pl](http://localhost/ledgersmb/login.pl)

My ledgersmb.conf contains

> [globaldb]
DBname = ledgersmb
DBhost = localhost
DBport = 5432
DBUserName = ledgersmb
DBPassword = ledgersmbpwd

How do I track down the error source from here?

Chris

---

### Post by DavidTangye on 2007-08-27
There is info about this near the very end of the INSTALL file in the installed software directory.

---

### Post by clee991 on 2007-08-28
I got things working by doing a re-install of postgres but now ...

(I posted the following to the [email]ledger-smb-users@lists.sourceforge.net[/email] since it was quiet on this topic here)

I have completed a new install of LedgerSMB 1.2.7 (and dependencies) on a stable install of Ubuntu 7.04 using the procedure laid out on [http://ubuntuforums.org/showthread.php?p=3232208](http://ubuntuforums.org/showthread.php?p=3232208)  with the variation of installing PG 8.2 rather than 8.1

I can open [http://localhost/ledgersmb/admin.pl](http://localhost/ledgersmb/admin.pl)

I can create users (which subsequently are listed in the admin page) but get an error when saving , such as

> Error!

FATAL: password authentication failed for user "trp"

When I go to [http://localhost/ledgersmb/login.pl](http://localhost/ledgersmb/login.pl) I cannot log in and get

> Error!

bin/login.pl:336: Access Denied!

I have messed up permissions somehow? - some guidance to correct would be greatly appreciated.

---

### Post by dominiquec on 2007-08-28
Hi, Clee: sorry about the lack of responses.  I'm working on other things right now, but I'll get back to reviewing my procedures later this week.  I hope to put together an apt installable version, but on 6.06.

You're right to bring it to the LedgerSMB mailing list, though.  Past the install point, I'd refer it to those guys.

Seems to me from your error messages, though, that its with the password / permission on your database.  I'd check that out first.

---

### Post by clee991 on 2007-08-29
I figured it out - a careful re-read of the 'install' document and more careful attention to settings in the db settings in admin.pl got it up and working

---

### Post by sgtrock on 2007-10-08
Hi, all.

I've gotten LedgerSMB 1.2.8 up.  However, I'm running into a problem creating a company.  It keeps failing with the following error message:

> psql:sql/Pg-database.sql:825: ERROR: language "plpgsql" does not exist
HINT: Use CREATE LANGUAGE to load the language into the database.

Does that make sense to anyone?

TIA

---

### Post by dominiquec on 2007-10-09
Hi, Sarge:

Didn't encounter this in my install, and all I used were defaults.

In any case, a quick google revealed this: [http://archives.postgresql.org/pgsql-sql/2003-05/msg00451.php](http://archives.postgresql.org/pgsql-sql/2003-05/msg00451.php)

Seems its something you have to do with PostgreSQL.

---

### Post by digitalhillbilly on 2007-10-26
Though I would post cause this is a great thread. I'm building a sweet little suite of apps on top of Ubuntu for small businesses in my region. Thanks dominiquec your install instructions worked great on Gusty.

I do have one little problem I'm working through though - if any here have some advice, I'd greatly appreciate it. The installation went smoothly, I logged into the administrator panel and created a new dataset, again, no problem. However, I'm trying to create a new user (through the admin panel) and I get this:
```

Error!

could not connect to server: Connection refused Is the server running on host "localhost" and accepting TCP/IP connections on port 5423? 
```

any tips?

dh

btw... thanks again

---

### Post by digitalhillbilly on 2007-10-26
addendum to my last post:

After a night of blissful slumber and my brain refreshed, I remembering the correct password plus  leaving the port field empty worked and it's all running smoothly now.. 

Cool!

---

### Post by kiranpvsr on 2010-11-12
Hi Clee,

Can you post what did you do to solve the Global DBH error?

---

