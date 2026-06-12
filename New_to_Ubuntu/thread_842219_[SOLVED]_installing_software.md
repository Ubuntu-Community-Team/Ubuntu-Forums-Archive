---
title: "[SOLVED] installing software"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by ub007 on 2008-06-27
Hi,

I downloaded osCommerce software -file:gcdb-1.1.6.tar.gz onto my ubuntu desktop.How to i install this?Thanks in advance...

---

### Post by billgoldberg on 2008-06-27
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

look for the source packages.

edit: from what I've read about the program, your going to need a lamp server also.

---

### Post by hyper_ch on 2008-06-27
yuo'll need to have a LAMP setup for OsCommerce...

---

### Post by ub007 on 2008-06-27
Thanks.I have installed LAMP server.
--tried  to install using the link provided,however i get the following error
~Desktop/gcdb$ make
make:***No targets specified and no makefile found. Stop


What do i do now...?

---

### Post by Canis familiaris on 2008-06-27
It it a source or a binary folder?
Could you post the directory listing for the folder.

```
ls
```

---

### Post by ub007 on 2008-06-27
yep sure

administration.php  enternote.php          README
configuration.php   enterpayment.php       resourcemanagement.php
confirm.php         enterresource.php      search.php
createpackage.php   enterticket.php        security
CVS                 enteruser.php          sendbill.php
dbdump              gcdb.css               showaccounts.php
dbint               gcdb.php               showcontacts.php
db.php              gcdb-settings.php      showinvoices.php
db-tools.php        images                 shownotes.php
delete.php          index.php              showpackage.php
description-pak     lang                   showpayments.php
doc-pak             main.php               showprofile.php
edit.php            money.php              showtickets.php
enteraccount.php    newsmanagement.php     stats.php
entercontact.php    packagemanagement.php  tools
entercustomer.php   pack_final.php         usermanagement.php
enterinvoice.php    pack_resources.php
enternews.php       publicprofile.php

---

### Post by ub007 on 2008-06-27
reckon its a source file..

---

### Post by Canis familiaris on 2008-06-27
Go to the CVS directory and try the make command them.

```
cd CVS
make
```

If it does not work can you list all files of CVS folder.

---

### Post by hyper_ch on 2008-06-27
it's a php application... no compilation needed... just a LAMP environment ;)

---

### Post by ub007 on 2008-06-27
nope ,doesn't work..
cd CVS
$ls
Entries  Repository  Root

---

### Post by Canis familiaris on 2008-06-27
I'm afraid I know not much of php application installation.

---

### Post by ub007 on 2008-06-27
hyper_ch,
'it's a php application... no compilation needed... just a LAMP environment'
in that case,Could you tell me how to get it working?

I've got LAMP server installed..This is what i did for that:

2. apt-get install php5-mysql

3. apt-get install libapache2-mod-php5

4. apt-get install (mysql-server) or (mysql-common) or a combination of them

5. apt-get install msql-client-5.0 and set password for root

6. apt-get install phpmyadmin and reconfigured for apache2

---

### Post by hyper_ch on 2008-06-27
how do you run a php file on a webserver?

And did you have a look at:
> **ub007 said:**
> README

---

### Post by ub007 on 2008-06-27
yes i did have a look at README(not much luck there)
i havent the faintest idea of running a php file on a web server.I just wanted to install an ecom software so that I cud load test the web server,havent got much interest in the ecom s/w as such,but need to get it installed anyway to launch a full test on it...

cheers

---

### Post by hyper_ch on 2008-06-27
what does the README say?

---

### Post by ub007 on 2008-06-27
Although a minor version, this release contains a few vital API changes:
  * DB interface supporting: MySQL and Postgresql
  * Greatly enhanced language support

This release is to get some fresh source out instead of by CVS and to
revive the project a bit.  There are bound to be bugs, please post them
in the bug tracker!

Instructions on how to setup MySQL and Postgresql to work with gcdb
is now on the website:  [http://gcdb.sourceforge.net](http://gcdb.sourceforge.net)

---

### Post by hyper_ch on 2008-06-27
normally you run php scripts like this:

(1) copy them into a webfolder path
(2) maybe set permissions (for upload folders and stuff
(3) maybe edit a file called config.inc.php to refelct some stuff like database access
(4) call the index file from the browser...

or you could do a google search with "howto install oscommerce" for example...

and then maybe follow the first link.
> 
[osCommerce Tutorial - Learn howto install & configure : osCommerce ...]("http://www.indichosts.net/tutorials/oscommerce/")
- [ Diese Seite übersetzen ]
Learn how to install osCommerce, change payment methods, add special items via osCommerce tutorial. Find professional osCommerce hosting, etc.
[www.indichosts.net/tutorials/oscommerce/](www.indichosts.net/tutorials/oscommerce/) - 12k - Im Cache - Ähnliche Seiten


---

### Post by manishtech on 2008-06-27
Hope you have installed LAMP,if not installed, then do it...
Start both apache and mysql if not started.
using

[B]sudo /etc/init.d/apache2 restart
sudo /etc/init.d/mysql restart[/B]

I dont remember the exact name of the script, use 
**ls /etc/init.d/apache***
and
**ls /etc/init.d/mysql***
to locate the exact script file name

now extract the tarball inside **/var/www** folder, you need to be root for that,
press Alt+F2 and there type **gksudo nautilus /var/www**

There paste the tarball and then extract. Now you can have a folder named 
/var/www/oscommerce... or something

try to find the config file and change the database configuration to the correct one,if you dont know how to setup,tell now

Now open your webbrowser type localhost and you can see the listing, you can see the folder oscommerce which you untarred
Click on that folder in the browser


It would be better if you know what exactly is osCommerce and how PHP scripts are run before playing with osCommerce. ( Not flaming,just a nice suggestion :) )

---

### Post by manishtech on 2008-06-27
This is a tutorial for setting up LAMP and configuring it too. I wrote this HOWTO long back, and hope its relevant to this date too, except it was written for dapper drake
[http://manishtech.wordpress.com/2007/06/20/settng-up-lamp-stack-on-your-ubuntu-system/](http://manishtech.wordpress.com/2007/06/20/settng-up-lamp-stack-on-your-ubuntu-system/)

And can you tell the name of the config file in osCommerce or post the default contents of the database section?

---

### Post by ub007 on 2008-06-27
thanks a ton mate....i'm tryn it out ...a quick question
how do i extract the tarball into /var/www?

---

### Post by Canis familiaris on 2008-06-27
> **ub007 said:**
> thanks a ton mate....i'm tryn it out ...a quick question
how do i extract the tarball into /var/www?

Open terminal:

```
cd /var/www

```

```
sudo tar xvzf <path of the tarball>
```

You could alternatively drag and drop the tarball onto the terminal precede its name by sudo tar xvzf

---

### Post by manishtech on 2008-06-27
> **ub007 said:**
> thanks a ton mate....i'm tryn it out ...a quick question
how do i extract the tarball into /var/www?
Follow the steps:
* When you are on desktop press the key combination **Alt+F2**
* You will get a run dialog box, now over there type **gksudo nautilus /var/www**
* You will be asked to enter the password, enter it
* Now you would get an instance of nautilus (equivalent of Windows Explorer) running in with root privileges
* Now just copy the tarball and paste it in the folder which you opened
* Right-click on the tarball and select **Extract Archive**

Remember the above method of opening anything with root privileges. You can also open say gedit with root privileges using **gksudo gedit** in the Run Dialog Box

Cheers!

---

### Post by ub007 on 2008-06-27
hey,

that works great!i've got it extracted to /var/www....
Could you plz walk me through the next steps.....I'm a bit lost here & the brains frozen,hehe...

Cheers

---

### Post by ub007 on 2008-06-27
hey,
guess i've got nother issue with it mayb,i try to open the newly extracted folder and it gives me the foll error msg:the folder contents could not be displayed
                                You do not have the neccessary permissions....:(

---

### Post by manishtech on 2008-06-27
> **ub007 said:**
> hey,
guess i've got nother issue with it mayb,i try to open the newly extracted folder and it gives me the foll error msg:the folder contents could not be displayed
                                You do not have the neccessary permissions....:(
Hope you are browsing the folder by nautilus running under root privilig? If its so, then you should get it. If you are running it as a normal user- Means as u browse normally, then you can get those problems.

Open terminal and type there (Applications>Accessories>Terminal)
**sudo chmod -vRc o+r /var/www/*os***

If this step shows error,please post back. After running the above command please post the output of 
**echo $?**

Please execute the  **echo $? **command immediately after the chmod command[B].

IMP:[/B] Besides please give us  the name of the osCOmmerce tarball and folder which u have in /var/www folder

---

### Post by ub007 on 2008-06-27
sudo chmod -vRc o+r /var/www/*os*

chmod: cannot access `/var/www/*os*': No such file or directory

*os*-i dont have that directory at the moment
what i have is
root@ubuntu:/var/www# ls
gcdb  gcdb-1.1.6  gcdb-1.1.6.tar.gz  index.html
root@ubuntu:/var/www# gcdb-1.1.6 was empty,so did the unzipping again...now all the files are in gcdb folder and i can view them:
root@ubuntu:/var/www/gcdb# ls
administration.php  enterpayment.php       README
configuration.php   enterresource.php      resourcemanagement.php
confirm.php         enterticket.php        search.php
createpackage.php   enteruser.php          security
CVS                 gcdb.css               sendbill.php
dbdump              gcdb.php               showaccounts.php
dbint               gcdb-settings.php      showcontacts.php
db.php              images                 showinvoices.php
db-tools.php        index.php              shownotes.php
delete.php          lang                   showpackage.php
edit.php            main.php               showpayments.php
enteraccount.php    money.php              showprofile.php
entercontact.php    newsmanagement.php     showtickets.php
entercustomer.php   packagemanagement.php  stats.php
enterinvoice.php    pack_final.php         tools
enternews.php       pack_resources.php     usermanagement.php
enternote.php       publicprofile.php

---

### Post by ub007 on 2008-06-27
i didnt have a problem opening the folder the 2nd time .......

---

### Post by manishtech on 2008-06-27
> **ub007 said:**
> sudo chmod -vRc o+r /var/www/*os*

chmod: cannot access `/var/www/*os*': No such file or directory

*os*-i dont have that directory at the moment
what i have is
root@ubuntu:/var/www# ls
gcdb  gcdb-1.1.6  gcdb-1.1.6.tar.gz  index.html
root@ubuntu:/var/www# gcdb-1.1.6 was empty,so did the unzipping again...now all the files are in gcdb folder and i can view them:
root@ubuntu:/var/www/gcdb# ls
administration.php  enterpayment.php       README
configuration.php   enterresource.php      resourcemanagement.php
confirm.php         enterticket.php        search.php
createpackage.php   enteruser.php          security
CVS                 gcdb.css               sendbill.php
dbdump              gcdb.php               showaccounts.php
dbint               gcdb-settings.php      showcontacts.php
db.php              images                 showinvoices.php
db-tools.php        index.php              shownotes.php
delete.php          lang                   showpackage.php
edit.php            main.php               showpayments.php
enteraccount.php    money.php              showprofile.php
entercontact.php    newsmanagement.php     showtickets.php
entercustomer.php   packagemanagement.php  stats.php
enterinvoice.php    pack_final.php         tools
enternews.php       pack_resources.php     usermanagement.php
enternote.php       publicprofile.php
Good! Your osCommerce is in the folder named gcdb

So run the command
**sudo chmod -Rc o+r /var/www/*gcdb***
and then immediately
[B]echo $?
[/B]
Additionally post the contents of the file **configuration.php**
so that I can search for database settings.

---

### Post by ub007 on 2008-06-27
Meanwhile i tried this:
1)pointed my browser to 
[http://127.0.1.1/gcdb/](http://127.0.1.1/gcdb/)

got this error msg:

Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'root'@'localhost' (using password: YES) in /var/www/gcdb/dbint/mysql.php on line 27

Warning: mysql_select_db(): supplied argument is not a valid MySQL-Link resource in /var/www/gcdb/dbint/mysql.php on line 28
Need a valid database connection!

It was just a shot in the dark.Appreciate if u can guide me through....

cheers

---

### Post by ub007 on 2008-06-27
ooopss,sent that post b4 seeing ur reply.
root@ubuntu:/var/www/gcdb# echo $?
0



root@ubuntu:/var/www/gcdb# cat configuration.php
<?
# Configuration Page
session_start();

require("gcdb.php");
require("security/secure.php");
adminify($sess_user, $sess_admin);

beginDocument($lConfiguration, $sess_user);

$db = getDBConnection(); 

if ($updater == "config") {
	$result = DBquery("UPDATE Configuration SET Language='$language',SearchBar='$searchbar',CurrencyAfter='$currafter',TaxRate='$taxrate',BillFromAddress='$billfromaddress',BillReplyAddress='$billreplyaddress',BillBcc='$billbcc',BillSubject='$billsubject',BillHeader='$billheader',BillFooter='$billfooter',TicketNotifier='$ticketnotifier',HotTicket='$hotticket'", $db);
	if(!(is_integer($result)) or ($result == 1)) {
		beginPrettyTable("1", $lConfigurationUpdate);
		echo "<tr>\n";
		echo " <td><div class=data>$lConfigUpdateSuccess <a href='main.php'>$lMainPage</a></div></td>\n";
		echo "</tr>\n";
		endPrettyTable();
	} else {
		beginPrettyTable("1", $lConfigurationUpdate);
		echo "<tr> <td><div class=data>$lConfigUpdateFail: ";
		echo mysql_error();
		echo "</div></td></tr>\n";
		endPrettyTable();
	}
} else {

	$result = DBquery("SELECT * from Configuration", $db);
	$myrow = DBfetch_array($result);
	$datSearchBar = $myrow["SearchBar"];
	$datCurrAfter = $myrow["CurrencyAfter"];
	$datTaxRate = $myrow["TaxRate"];
	$datBillFromAddress = $myrow["BillFromAddress"];
	$datBillReplyAddress = $myrow["BillReplyAddress"];
	$datBillBcc = $myrow["BillBcc"];
	$datBillSubject = $myrow["BillSubject"];
	$datBillHeader = $myrow["BillHeader"];
	$datBillFooter = $myrow["BillFooter"];
	$datTicketNotifier = $myrow["TicketNotifier"];
	$datHotTicket = $myrow["HotTicket"];
	openForm("config", $PHP_SELF);
	 makeHiddenField("updater", "config");
	 beginPrettyTable("2", $lConfiguration);
	 beginBorderedTable("2");
	  makeStaticField($lVersion, $myrow["Version"]);
	  makeStaticField($lPersistentConnections, $PERSISTENT);
	  makeDropBox($lSearchBar, "searchbar", $datSearchBar, "On", "Off"); 
	  makeDropBox($lCurrencyAfterAmount, "currafter", $datCurrAfter, "On", "Off");
	  makeDropBox($lHotTicket, "hotticket", $datHotTicket, "On", "Off");
	  makeTextField($lTaxRate, "taxrate", $datTaxRate);
	  makeTextField($lTicketNotifier, "ticketnotifier", $datTicketNotifier);
	  echo "<tr><td><br></td></tr>";
	  makeTextField($lBillFromAddress, "billfromaddress", $datBillFromAddress);
	  makeTextField($lBillReplyAddress, "billreplyaddress", $datBillReplyAddress);
	  makeTextField($lBillBcc, "billbcc", $datBillBcc);
	  makeTextField($lBillSubject, "billsubject", $datBillSubject);
	  makeLargeTextField($lBillHeader, "billheader", $datBillHeader);
	  makeLargeTextField($lBillFooter, "billfooter", $datBillFooter);
	  echo "<tr><td><br></td></tr>";
	  echo "<tr><td><b>$lLanguage:</b></td>\n";
	  echo "  <td><select name='language'>\n";
	  $handle = opendir('lang');
	  echo "<option value='".$myrow["Language"]."'>".$myrow["Language"]."\n";
	  while($file = readdir($handle)) {
			$len = strlen($file);
			if(($file != $myrow["Language"]) && ($len > 4) && (substr($file, ($len - 3), $len) == "php")) {
		 	 echo "<option value='$file'>$file</option>\n";
			}
	  }
	  closedir($handle);
	  echo "</select>\n";
	  echo "</td></tr>\n";
	  makeSubmitter();
	 endPrettyTable();
	 endBorderedTable();
	closeForm();
}
endDocument();
?>

---

### Post by ub007 on 2008-06-27
plz ignore this post of mine,(didnt see ur reply when i had posted it).thanks

' Re: installing software
Meanwhile i tried this:
1)pointed my browser to
[http://127.0.1.1/gcdb/](http://127.0.1.1/gcdb/)

got this error msg:

Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'root'@'localhost' (using password: YES) in /var/www/gcdb/dbint/mysql.php on line 27

Warning: mysql_select_db(): supplied argument is not a valid MySQL-Link resource in /var/www/gcdb/dbint/mysql.php on line 28
Need a valid database connection!

It was just a shot in the dark.Appreciate if u can guide me through....

cheers'

---

### Post by manishtech on 2008-06-27
Actually I require the ***configuration page*** which lists the database information. Its not this
Maybe its this file
**gcdb.php**
OR
**security/secure.php**

Best thing, give me the output of **ls -l**
the above command lists the output of folder in long format

---

### Post by ub007 on 2008-06-27
here it is:

root@ubuntu:/var/www/gcdb# ls -l
total 248
-rw-r--r-- 1 1002 users  2010 2001-05-20 18:15 administration.php
-rw-r--r-- 1 1002 users  3251 2001-05-16 03:39 configuration.php
-rw-r--r-- 1 1002 users  2666 2001-06-01 12:45 confirm.php
-rw-r--r-- 1 1002 users   440 2001-04-29 16:09 createpackage.php
drwxr-xr-x 2 1002 users  4096 2001-08-24 04:54 CVS
drwxr-xr-x 3 1002 users  4096 2001-08-24 04:45 dbdump
drwxr-xr-x 3 1002 users  4096 2001-08-24 04:45 dbint
-rw-r--r-- 1 1002 users  3173 2001-05-16 21:53 db.php
-rw-r--r-- 1 1002 users  2969 2001-05-20 03:31 db-tools.php
-rw-r--r-- 1 1002 users  3144 2001-05-16 03:44 delete.php
-rw-r--r-- 1 1002 users 15164 2001-05-24 17:42 edit.php
-rw-r--r-- 1 1002 users  2039 2001-05-19 19:53 enteraccount.php
-rw-r--r-- 1 1002 users  1128 2001-05-18 02:50 entercontact.php
-rw-r--r-- 1 1002 users  1573 2001-05-16 21:50 entercustomer.php
-rw-r--r-- 1 1002 users   967 2001-05-16 03:39 enterinvoice.php
-rw-r--r-- 1 1002 users   835 2001-05-16 03:39 enternews.php
-rw-r--r-- 1 1002 users   862 2001-05-16 03:39 enternote.php
-rw-r--r-- 1 1002 users  1105 2001-05-16 03:39 enterpayment.php
-rw-r--r-- 1 1002 users   841 2001-05-17 23:19 enterresource.php
-rw-r--r-- 1 1002 users  2275 2001-05-16 03:39 enterticket.php
-rw-r--r-- 1 1002 users  1296 2001-05-17 02:31 enteruser.php
-rw-r--r-- 1 1002 users   727 2001-05-05 04:51 gcdb.css
-rw-r--r-- 1 1002 users 10553 2001-05-17 21:39 gcdb.php
-rw-r--r-- 1 1002 users  1081 2001-05-16 03:42 gcdb-settings.php
drwxr-xr-x 3 1002 users  4096 2001-08-24 04:45 images
-rw-r--r-- 1 1002 users  1724 2001-05-20 18:15 index.php
drwxr-xr-x 3 1002 users  4096 2001-08-24 04:54 lang
-rw-r--r-- 1 1002 users  5399 2001-05-20 17:59 main.php
-rw-r--r-- 1 1002 users  1580 2001-05-04 16:32 money.php
-rw-r--r-- 1 1002 users  1131 2001-06-01 12:45 newsmanagement.php
-rw-r--r-- 1 1002 users  1157 2001-06-01 12:45 packagemanagement.php
-rw-r--r-- 1 1002 users  1221 2001-05-18 00:43 pack_final.php
-rw-r--r-- 1 1002 users  1215 2001-05-19 17:48 pack_resources.php
-rw-r--r-- 1 1002 users 10160 2001-05-20 18:21 publicprofile.php
-rw-r--r-- 1 1002 users   458 2001-08-24 05:09 README
-rw-r--r-- 1 1002 users  1202 2001-06-01 12:45 resourcemanagement.php
-rw-r--r-- 1 1002 users  3046 2001-06-02 03:39 search.php
drwxr-xr-x 3 1002 users  4096 2001-08-24 04:45 security
-rw-r--r-- 1 1002 users  3698 2001-05-20 19:54 sendbill.php
-rw-r--r-- 1 1002 users  1319 2001-05-20 04:02 showaccounts.php
-rw-r--r-- 1 1002 users  1623 2001-06-01 12:45 showcontacts.php
-rw-r--r-- 1 1002 users   819 2001-05-04 16:32 showinvoices.php
-rw-r--r-- 1 1002 users   716 2001-04-29 16:09 shownotes.php
-rw-r--r-- 1 1002 users  1034 2001-05-16 04:06 showpackage.php
-rw-r--r-- 1 1002 users   813 2001-05-04 16:32 showpayments.php
-rw-r--r-- 1 1002 users 18161 2001-06-01 12:45 showprofile.php
-rw-r--r-- 1 1002 users   956 2001-04-29 16:09 showtickets.php
-rw-r--r-- 1 1002 users  2823 2001-05-20 18:15 stats.php
drwxr-xr-x 3 1002 users  4096 2001-08-24 04:45 tools
-rw-r--r-- 1 1002 users  1139 2001-05-02 00:17 usermanagement.php

---

### Post by ub007 on 2008-06-27
output of db.php:

<?
# Obtain global settings for gcdb
require("gcdb-settings.php");

# This program calls abstract DB interfaces

if(!(extension_loaded($RDBM))) {
	echo "<pre>PHP has these loaded extensions:\n";
	print_r (get_loaded_extensions());
        echo "</pre>";
	die ("Support not enabled for $RDBM, <b>gcdb</b> cannot run.\n");
}

# Install the proper DB hooks 
require("dbint/$RDBM.php");

###############################################################################
# DB ABSTRACT INTERFACE TO GCDB API
###############################################################################

# name: getDBConnection
#
# arguments: none
# returns: database handle
#
# desc: I did this so the DB could easily be changed
function getDBConnection () {
	global $PERSISTENT, $DBHOST, $DBUSER, $DBPASSWORD, $DBNAME;

	if($PERSISTENT == "On") {
		$db = rdbms_pconnect($DBHOST, $DBUSER, $DBPASSWORD, $DBNAME);
	} else {
		$db = rdbms_connect($DBHOST, $DBUSER, $DBPASSWORD, $DBNAME);
	}
	checkDBError($db);
	return $db;
}

# name: DBquery
#
# arguments: connection, SQL query
# returns: Result set for select, or 0/1 for everything else
#
# desc: Sends a query to the database
function DBquery($query,$db) {
	$result = rdbms_query($query,$db);
	return $result;
}

# name: DBfetch_array
#
# arguments: Result set
# returns: associative array
#
# desc: Creates an associative array from a result
function DBfetch_array($result) {
	$row = rdbms_fetch_array($result);
	return $row;
}

# name: DBnum_rows
#
# arguments: Result handle
# returns: Number of rows in the result
#
# Returns the number of rows in a result
function DBnum_rows($result) {
	$count = rdbms_num_rows($result);
	return $count;
}

# name: checkDBError
#
# arguments: database handle
# returns: String containing DB Error number and Error String
#
# desc: Checks for an error with the DB and prints the error if it exists
function checkDBError($db) {
	if (!$db) {
		die ("Need a valid database connection!<br>\n");
        }
	$test = rdbms_db_error($db);
	if($test != "") {
		echo "$test<br>";
	}
}

# name: DBinsert_id
#
# arguments: result handle, table name, field name, database handle
# returns: The ID that was assigned by the last insert statement
#
# desc: Returns the ID given to the last insert
function DBinsert_id($result, $table, $field, $db) {
	$num = rdbms_insert_id($result, $table, $field, $db);
	return $num;
}

# name: DBReport
#
# arguments: Result set, Title of action, URL to return to, Text for return link,
#             database handle
# returns: HTML table for showing the result of an update
#
# desc: Uses the PrettyTable functions to generate a table detailing what happened
function DBReport ($result, $title, $return_url, $return_link, $db) {
	global $lUpdateSuccess, $lUpdateFailed;
	if(!(is_integer($result)) or ($result == 1)) {
		beginPrettyTable("1", $title);
		echo "<tr>\n";
		echo " <td><div class=data>$lUpdateSuccess <a href='$return_url'>$return_link</a></div></td>\n";
		echo "</tr>\n";
		endPrettyTable();
	} else {
		beginPrettyTable("1", $title);
		echo "<tr> <td><div class=data>$lUpdateFailed: ";
		echo checkDBError($db);
		echo "</div></td></tr>\n";
		endPrettyTable();
	}
}

?>

---

### Post by ub007 on 2008-06-27
output secure.php

<?
# This chunk of code checks to see if a user has been registered in the session,
# if not, it dies.  Security!

if(!(session_is_registered("sess_user"))) {
	beginDocument("Security", "Not Logged In");
	beginPrettyTable(1, "Security");
	echo "<tr><td class='data'>You are not logged in.  Please <a href='index.php'>Login</a></td></tr>";
	endPrettyTable();
	die;
}
?>

---

### Post by ub007 on 2008-06-27
guess this could be the one:

<?
# gcdb Settings

#----------------------------------------------------------------------------
# Database Settings
#----------------------------------------------------------------------------

# RDBM setting - choose one!
$RDBM = "mysql";
#$RDBM = "pgsql";

# Persistent database connections
$PERSISTENT = "Off";

# Database Host
$DBHOST = "localhost";

# Database User
$DBUSER = "root";

# Database Password
$DBPASSWORD = "hilandresbobo";

# Database for gcdb to use
$DBNAME = "gcdb";

#----------------------------------------------------------------------------
# Customization Settings
#----------------------------------------------------------------------------
# Some of the color settings are in the gcdb.css file

# Name you want pasted all over gcdb's interface, like a Company or something
$BRAND = "gcdb";

# Color of the topbar where the user and brand line
$TOPBAR = "#A74C3A";

# Color of the page background
$BACKGROUND = "#CCCCCC";

# Color of the table headers and borders
$TABLEBORDER = "#A74C3A";

# Color of the tabble innards
$INNERTABLE = "#828282";

?>

---

### Post by ub007 on 2008-06-27
output gcdb.php:

<?
# This file contains lots of functions used by the billing database
# to generate no fun things like tables, forms, and such.
require("gcdb-settings.php");

###############################################################################
# DB INTERFACE
###############################################################################
require("db.php");

###############################################################################
# BILLING FUNCTIONS
###############################################################################

# name: untranslate_interval
#
# arguments: Language version of the Charged field
# returns: DB version of charged field (English)
#  
# desc: This function allows gcdb to have a language neutral way of storing
# desc: the interval for charging an account.
function untranslate_interval($charged) {
	global $lMonthly, $lQuarterly, $lBiannually, $lAnnually;
	if($charged == $lMonthly) {
		return "monthly";
	}
	if($charged == $lQuarterly) {
		return "quarterly";
	}
	if($charged == $lBiannually) {
		return "biannually";
	}
	if($charged == $lAnnually) {
		return "annually";
	}
}
# name: translate_interval
#
# arguments: DB version of charged field (English)
# returns: Language version of the Charged field
#  
# desc: translates the DB interval into a Lang string
function translate_interval($charged) {
	global $lMonthly, $lQuarterly, $lBiannually, $lAnnually;
	if($charged == "monthly") {
		return $lMonthly;
	}
	if($charged == "quarterly") {
		return $lQuarterly;
	}
	if($charged == "biannually") {
		return $lBiannually;
	}
	if($charged == "annually") {
		return $lAnnually;
	}
}

###############################################################################
# DOCUMENT FUNCTIONS
###############################################################################

# name: beginDocument 
#
# arguments: Page title, Username
# returns: None
#
# desc: echos the HTML tags that get the document started, provides a central
# desc: location for the background color, stylesheets, and whatnot.
function beginDocument ($title, $user) {
	
	global $BRAND, $BACKGROUND, $TOPBAR, $sess_lang;

	if(isset($sess_lang)) {
		checkLang($sess_lang);
	}
	echo "<html>\n";
	echo "<head>\n <title>[$BRAND] :: $title</title>\n";
	echo " <link rel=stylesheet href='gcdb.css' type='text/css'>\n";
	echo "</head>\n<body bgcolor='$BACKGROUND' text='black' leftmargin=0 topmargin=0 marginheight=0 marginwidth=0>\n"; 
	echo "<table bgcolor='$TOPBAR' width=100%><tr><td width='80%' align='left' class='header'>&nbsp;&nbsp;$BRAND: $user</td><td width='20%' align='right'>";
	if($user != "Not Logged In") {
  		echo "<a href='main.php'><img src='images/home.gif' width=24 height=24 border=0 alt='Home'></a>";
	}
	echo "&nbsp;&nbsp;</td></tr></table>";
	echo "<table cellpadding=0 width='100%' height='100%' border=0><tr><td valign=top>\n";
}

# name: searchBar
#
# arguments: None
# returns: None
#
# desc: echos the HTML for the search Bar
function searchBar() {
	global $lSearch, $lLast, $lAddress, $lEmail, $lDomain;
	openForm("searcher", "search.php");
		beginPrettyTable("2");
		echo "<tr>\n";
		echo "<td><b>$lSearch</b>: <input name='tosearch' type='text'></td>\n";
		echo "<td valign='center'>\n<select name='searcher' type='text'>\n";
		echo " <option value='last' selected>$lLast\n";
		echo " <option value='address'>$lAddress\n";
		echo " <option value='email'>$lEmail\n";
		echo " <option value='domain'>$lDomain\n";
		echo "</select>\n";
		echo "<input type='image' align='center' src='images/go.gif' value='submit' border=0>\n";
		echo "</td></tr>\n";
		endPrettyTable();
		closeForm();
}

# name: endDocument
# 
# arguments: None
# returns: None
#
# desc: closes all the HTML opened by beginDocument
function endDocument() {
	echo "</td></tr></table></body></html>\n";
}
	

###############################################################################
# TABLE FUNCTIONS
###############################################################################

# name: beginPrettyTable
#
# desc: handle the creation of a pretty, outlined table.  Uses the supplied
# desc: bordercolor, bgcolor, colspan (for header) and text (text of header)
function beginPrettyTable () {
	global $TABLEBORDER, $INNERTABLE;

	# Allow us to take either 1 or 2 arguments
	$numargs = func_num_args();
	if($numargs == 0) {
		die ("Must provide a colspan to beginPrettyTable()\n");
	}
	$arg_list = func_get_args();
	$colspan = $arg_list[0];
	if($numargs > 1) {
		$header = $arg_list[1];
	}
	echo "<table bgcolor='$TABLEBORDER' cellpadding=1 cellspacing=0 border=0>\n";
	if ($header) {
		echo " <tr> <td colspan=$colspan align='right'><div class='header'>$header&nbsp;</div></td> </tr>\n";
	}
	echo " <tr>\n  <td>\n";
	echo "   <table bgcolor='$INNERTABLE' cellpadding=2 cellspacing=0 border=0>\n";
	echo "    <tr>\n  <td>\n";
	echo "      <table bgcolor='$INNERTABLE' cellpadding=2 cellspacing=0 border=0>\n";
}

# name: endPrettyTable
#
# desc: close all tags opened by beginPrettyTable
function endPrettyTable () {
	echo "      </table>\n";
	echo "     </td> </tr>\n";
	echo "   </table>\n";
	echo "  </td> </tr>\n";
	echo "</table>\n";
}

# name: beginBorderedTable
#
# desc: when used in unison with beginPrettyTable, gives a nice visual cue around
# desc: the data inside a table
function beginBorderedTable ($colspan) {
	global $TABLEBORDER, $INNERTABLE;

	echo "<tr>\n  <td>\n";
	echo " <table bgcolor='$INNERTABLE' cellpadding=2 cellspacing=2 border=0>\n";
}

# name: endBorderedTable
#
# desc: close all tags opened by beginBorderedTable
function endBorderedTable () {
	echo "   </td> </tr>\n";
	echo "  </table>\n";
	echo " </td> </tr>\n";
}

###############################################################################
# FORM FUNCTIONS
###############################################################################

# name: openForm
#
# desc: creates a form
function openForm ($name, $action) {
	echo "<form method='post' name='$name' action='$action'>";
}

# name: makeHiddenField
#
# desc: creates a hidden field
function makeHiddenField ($field, $value) {
	echo "<input type=\"hidden\" name=\"$field\" value=\"$value\">\n";
}

# name: makeStaticField
#
# desc: creates an uneditable field
function makeStaticField ($field, $value) {
	echo " <tr> <td><b>$field:</b></td><td><div class='data'>$value</div></td> </tr>\n";
}

# name: makeTextField
#
# arguments: Field label, form name, value
# returns: none
#
# desc: creates a textfield with the supplied paramaters
function makeTextField ($field, $name, $value) {
	echo " <tr> <td><b>$field:</b></td><td><input name='$name' type='text' value='$value'></td> </tr>\n";
}

# name: makeLargeTextField
#
# desc: creates a textarea with the supplied parameters
function makeLargeTextField ($field, $name, $value) {
	echo "<tr> <td valign='top'><b>$field:</b></td><td><textarea name=$name cols='48' rows='15' wrap='physical'>$value</textarea></td></tr>\n";
}

# name: makeDropBox
#
# desc: creates a select control using the supplied options, rearranging them
# desc: according to the first arg passed
function makeDropBox () {
	$numargs = func_num_args();
	if($numargs < 3) {
		echo $numargs."-";
		die ("Must provide arguments to makeDropBox\n");
	}
	$arg_list = func_get_args();
	$field 	= $arg_list[0];
	$name 	= $arg_list[1];
	$current = $arg_list[2];
	echo " <tr> <td><b>$field:</b></td><td><select name='$name'>\n";
	for($i = 3; $i < $numargs; $i++) {
		if($arg_list[$i] != $current) {
			echo "<option value='$arg_list[$i]'>$arg_list[$i]\n";
		} else {
			echo "<option value='$arg_list[$i]' selected>$arg_list[$i]\n";
		}
	}
	echo "</select></td></tr>\n";
}

# name: makeArrayDropBox
#
# desc: creates a select control from an array, but its a special array ;)
function makeArrayDropBox ($field, $name, $current, $array) {
	echo " <tr> <td><b>$field:</b></td><td><select name='$name'>\n";
	$size = sizeof($array);
	for($i = 0; $i < $size; $i += 2) {
		$also = $i + 1;
		if($array[$also] != $current) {
			echo "<option value='$array[$i]'>$array[$also]\n";
		} else {
			echo "<option value='$array[$i]' selected>$array[$also]\n";
		}
	}
	echo "</select></td></tr>\n";
}

# name: makeSubmitter
#
# arguments: none
# returns: none
#
# desc: makes a submit field
function makeSubmitter () {
	echo " <tr> <td colspan=2 align=center>\n";
	echo "  <input type=image type='submit' value='submit' src='images/submit.gif' border=0 alt='Go!'>";
	echo " </td> </tr>\n";
}

# name: closeForm
#
# arguments: none
# returns: none
#
# desc: close a form
function closeForm () {
	echo "</form>";
}
###############################################################################
# SECURITY
###############################################################################
# name: adminify
#
# arguments: User, Admin status
# returns: none
#
# desc: restrict access to a page to only Admins
function adminify($sess_user, $sess_admin) {
	global $lAccessDenied, $lAdminUseOnly;
	if($sess_admin != "Yes") {
		beginDocument("Security", $sess_user);
		beginPrettyTable(1, "$lAccessDenied");
		echo "<tr><td>$lAdminUseOnly</td></tr>";
		endPrettyTable();
		endDocument();
	}
}	
	

###############################################################################
# LANGUAGE API
###############################################################################

# name: checkLang
#
# arguments: Language
# returns: none
#
# desc: Adds content type header for languages that need it
function checkLang($lang) {
	if(isset($HTTPcharser)) {
		    header("Content-Type: text/html; charset=".$HTTPcharset);
	} else {
	    # Ugly hack. Don't use.
	    if($lang == "russian.php") {
		    header("Content-Type: text/html; charset=koi8-r");
	    }
	}
}

if(!(isset($sess_lang))) {
 	$db = getDBConnection();
 	$result = DBquery("select * from Configuration",$db);
	$config_row = dbfetch_array($result);
	require("lang/".$config_row["Language"]);
} else {
	require("lang/".$sess_lang);
}

###############################################################################
# DEBUG API
###############################################################################

# name: pdebug
#
# arguments: string, optional priority
# returns: none
#
# desc: used for sending message in HTML or to syslog for debugging
function pdebug($msg, $pri) {
	$dest = "";
	if ($msg) {
		switch($dest) {
			case "html":
				echo "<!-- $msg -->\n";
				break;
			case "syslog":
				$dpri = LOG_DEBUG;
				if ($pri) {
					$dpri = LOG_DEBUG | $pri;
				}
				openlog("gdbc", LOG_PID, LOG_USER);
				syslog($dpri,$msg);
				closelog();
				break;
		}
	}
}

?>

---

### Post by manishtech on 2008-06-27
Can you give us the link of the tarball from where u downloaded,or it will take ages to find out the config file itself :lol:

---

### Post by manishtech on 2008-06-27
Here is the key solution

[PHP]
# Database Host
$DBHOST = "localhost";

# Database User
$DBUSER = "root";

# Database Password
$DBPASSWORD = "hilandresbobo";

# Database for gcdb to use
$DBNAME = "gcdb";[/PHP]

You need to put the password of root account of mySQL in **$DBPASSWORD** 

Hope you know the password.....

---

### Post by ub007 on 2008-06-27
hehe,smart move

[http://sourceforge.net/projects/gcdb](http://sourceforge.net/projects/gcdb)

---

### Post by ub007 on 2008-06-27
'You need to put the password of root account of mySQL in $DBPASSWORD '

you mean to say i got to edit that file gcdb-settings.php,by changing
$DBPASSWORD = "hilandresbobo";to $DBPASSWORD = "mypassword";
(i know the password,hope so,lmao)

---

### Post by manishtech on 2008-06-27
> **ub007 said:**
> 'You need to put the password of root account of mySQL in $DBPASSWORD '

you mean to say i got to edit that file gcdb-settings.php,by changing
$DBPASSWORD = "hilandresbobo";to $DBPASSWORD = "mypassword";
(i know the password,hope so,lmao)
Yups! Exactly, you need to replace **hilandresbobo** with you password

---

### Post by ub007 on 2008-06-27
Yups! Exactly, you need to replace hilandresbobo with you password 

Yes,Done!what next?:guitar:

---

### Post by manishtech on 2008-06-27
> **ub007 said:**
> Yups! Exactly, you need to replace hilandresbobo with you password 

Yes,Done!what next?:guitar:
Now point your browser to [http://localhost](http://localhost) and you should see the contents on the screen provided the database details you gave are correct

---

### Post by ub007 on 2008-06-27
'http://localhost '

gives me
'It Works'

thats the output of index.html file in the /var/www directory

do i have to make changes in the apache2 conf files?:(

---

### Post by ub007 on 2008-06-27
if so,which file to edit?i remember seeing some conf file where the deault path to look was set to /var/www.....cant remember which file...:(

---

### Post by manishtech on 2008-06-27
> **ub007 said:**
> 'http://localhost '

gives me
'It Works'

thats the output of index.html file in the /var/www directory

do i have to make changes in the apache2 conf files?:(
The folder which you are trying to access does not contain your code,instead your code is in the folder named **gcdb**, so point your browser to
[http://localhost/gcdb](http://localhost/gcdb)

---

### Post by ub007 on 2008-06-27
I get the following errors :(

[http://localhost/gcdb](http://localhost/gcdb)

1049:Unknown database 'gcdb'

Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /var/www/gcdb/dbint/mysql.php on line 61

Warning: require(lang/) [function.require]: failed to open stream: No such file or directory in /var/www/gcdb/gcdb.php on line 337

Fatal error: require() [function.require]: Failed opening required 'lang/' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/gcdb/gcdb.php on line 337

---

### Post by manishtech on 2008-06-27
> **ub007 said:**
> I get the following errors :(

[http://localhost/gcdb](http://localhost/gcdb)

1049:Unknown database 'gcdb'

Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /var/www/gcdb/dbint/mysql.php on line 61

Warning: require(lang/) [function.require]: failed to open stream: No such file or directory in /var/www/gcdb/gcdb.php on line 337

Fatal error: require() [function.require]: Failed opening required 'lang/' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/gcdb/gcdb.php on line 337
Goto mysql and create a database first then access
on the terminal

**mysql -u root -p**

enter the password, then you will be dropped to mysql prompt
over there create the database using this

**create database gcdb;**

now again refresh the browser page

---

### Post by ub007 on 2008-06-27
root@ubuntu:/var/www/gcdb# mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 11
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> create database gcdb;
Query OK, 1 row affected (0.02 sec)

mysql> 
mysql> 
mysql> 
[10]+  Stopped                 mysql -u root -p
root@ubuntu:/var/www/gcdb# 


but still the error:Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /var/www/gcdb/dbint/mysql.php on line 61

Warning: require(lang/) [function.require]: failed to open stream: No such file or directory in /var/www/gcdb/gcdb.php on line 337

Fatal error: require() [function.require]: Failed opening required 'lang/' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/gcdb/gcdb.php on line 337

---

### Post by ub007 on 2008-06-27
I edited the gcdb.php file,no errors,however i get a page wherin i got to input 2 fields
guess the first one is user login
i tried gcdb,localhost n root
n then my mysql password,

nothing seems to work though.....

---

### Post by manishtech on 2008-06-27
What can you see after giving the username and password?

---

### Post by ub007 on 2008-06-27
i give the username and password...//firefox asks whether it should remember the password,lol and the 2 fields(username & password)clears itself-goes blank again(back to the state when i accessed it the first time)......no error msgs...

---

### Post by manishtech on 2008-06-27
I also tried to run it,same problem here....
Looks like there is some problem in the pages itself... I even checked out the source.

Well a bit offtopic, for what u need it? And you should know that its not osCommerce? osCommerce is something different. You mentioned the name of osCommerce on the first post itself.

---

### Post by ub007 on 2008-06-27
'Well a bit offtopic, for what u need it? And you should know that its not osCommerce? osCommerce is something different. You mentioned the name of osCommerce on the first post itself. '


Well,i'm setting up a test network.The purpose is to security/stress test a server.so i thought load testing a web server would be a good starting point.so installed LAMP,n to have something proper on it,i got to host some ecomm stuff onto it--i was searching for free s/w like oscommerce n guess accidently ended up in gcdb(i kept on going thinking gcdb is the dir where oscommerce files were stored,lol)....so basically any decent sw-website with shopping cart, will serve my purpose(really nt bothered much bout the internals of it)...appreciate if u could recommend any sws of the like..

its an interesting project,in the lines of stress testing a server and this is the first stage...we can harden the security of the server as we progress....again suggestions n contributions r welcome always..i could always give u more details on it if ur interested in pen testing n the like...,i'm new to this n kinda tryn to find my feet here,hehe...

Cheers

---

### Post by manishtech on 2008-06-27
Then I can suggest you to try osCommerce, as my experience it works properly.
Again you will have to change the config file in the copy of osCommerce too.

AFAIK, osCommerce is a very dependable project. It had a good user base, have a try and revert back if u have any prob

---

### Post by ub007 on 2008-06-28
Hiya,,

Firstly thanks to manishtech for all the support,appreciate that.
I could install osCommerce and jotting down the steps followed,may come in handy to any1 else attempting the same.

> Manish-you did mention that i would hve to change the configuration files;which i did not but still got osComm to work;is it cz i did part of the set up after pointing to the web browser;plz have a look at the steps and suggest alternate work arounds for a better installation and configuration;ideally would like more of command line stuff than going through the browser..thanks

-**LAMP installation**
I've got LAMP server installed..This is what i did for that:
1.apt-get instal apache2
2. apt-get install php5-mysql
3. apt-get install libapache2-mod-php5
4. apt-get install mysql-server and set password for root
5. apt-get install msql-client-5.0 
6. apt-get install phpmyadmin and reconfigured for apache2

**-downloaded osCommerce**
extracted it to /var/www
steps:
* When you are on desktop press the key combination Alt+F2
* You will get a run dialog box, now over there type gksudo nautilus /var/www
* You will be asked to enter the password, enter it
* Now you would get an instance of nautilus (equivalent of Windows Explorer) running in with root privileges
* Now just copy the tarball and paste it in the folder which you opened
* Right-click on the tarball and select Extract Archive

Remember the above method of opening anything with root privileges
// Reference manishtech

-**created a database**:

mysql -u root -p

enter the password, then you will be dropped to mysql prompt
over there create the database using this

create database osCommerce;

//ref: manishtech

**-access it from a webrowser**

point your browser to [http://localhost/osCommerce-2.....(whateve](http://localhost/osCommerce-2.....(whateve))
the website installation guide withh put u through
*enter the same database name(osCommerce in this case)
*enter the password u set up for root in sql
Thats it!!!!!:popcorn:

---

### Post by manishtech on 2008-06-28
Yesterday late night,I was just wondering why people face problems installation stuffs on web-server, so wrote this some hours back, hope you like it
[http://manishtech.wordpress.com/2008/06/28/running-php-applications-on-linux/](http://manishtech.wordpress.com/2008/06/28/running-php-applications-on-linux/)

Well,if you think I helped you, please press the **Thanks Button**. It would be the first thanks I would get ,its a medal icon next to Quote

---

### Post by manishtech on 2008-06-28
Your illustrations are as seen from the eyes of a newcomer to this arena. Good.... Keep it up...

And if you problems are solved, please mark this thread as SOLVED

And if you can, send a Thanks to me too.... :)

---

### Post by ub007 on 2008-06-28
[HTML]http://manishtech.wordpress.com/2008...ions-on-linux/[/HTML]

informative article i would say.
//its important to know your audience and in this case its linux newbies.windows users r used to- dowload a file,unzip it, double click the exe file ,NEXT,NEXT.....n finally FINISH,they expect it to work that way....so the first confusion is when a newbie tries to execute the tarball rather than just extract it to the var/www/ and point the web browser to it.-pointed out by hyper_ch in page 1 of this thread [HTML]it's a php application... no compilation needed... just a LAMP environment [/HTML]

> spoon-feeding becomes important,but only for the first time
the article is well directed and goes in fair amount of detail in the first part,however culminates in an abrupt ending;to be precise it would be great if you could include some snap shopts of the example u chose to demonstrate.
an experienced user wouldnt be bothered bout the lamp installation n unzipping,he will have no trouble hunting and configuring the required files as well;a newbie will still end up a bit confused unless u include a demo installation.

those r my views on it....keep going mate!applaud ur efforts...

Cheers

---

### Post by manishtech on 2008-06-30
Oh! Does it end abruptly? I will try to have a look at it again and try to modify those which require more importance...

---

### Post by ub007 on 2008-06-30
missed this step in my previous post:
After creating the database
-chmod 777 /var/www/oscommerce-2.2rca.../catalog/includes/configure.php
chmod 777 /var/www/oscommerce-2.2rca.../catalog/admin/includes/configure.php

---

### Post by manishtech on 2008-07-01
> **ub007 said:**
> missed this step in my previous post:
After creating the database
-chmod 777 /var/www/oscommerce-2.2rca.../catalog/includes/configure.php
chmod 777 /var/www/oscommerce-2.2rca.../catalog/admin/includes/configure.php
This is what we call a security loophole
I suppose you change it to 644, for both the files...

---

### Post by ub007 on 2008-07-01
yeppy,ur right!....guess i was too intend on getting the s/w installed..anyways u get the warnings on the website....thanks anyways for pointing that out..cheers..

David

---

