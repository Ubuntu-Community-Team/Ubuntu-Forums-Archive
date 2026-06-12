---
title: "PHP File Mis-Information"
date: 2012-10-28
forum: Programming Talk
---

### Post by OldManRiver on 2012-10-28
All,

The PHP manual and all the HOWTOs I have read, all have the same mis-information in them about getting a full file name with path.

The closest I get, searching for the answer is from:

[http://stackoverflow.com/questions/4049856/replace-phps-realpath/13110493#13110493](http://stackoverflow.com/questions/4049856/replace-phps-realpath/13110493#13110493)

And that code assumes the local file exists only in the "localhost" or the "/var/www" directory, which is totally not true.  

**Note:**
Have no clue what that would be ("localhost") on Windows.  Assume it would be where you installed your WAMP server.

My file is:

/data/mysql.user.sql

On the form it is called with:

<input type='file' id='pfile' name='pfile' value='Browse'>

Method is "POST" so as you know the $_POST['pfile'] contains only:

mysql.user.sql

When I pass the file to the "truepath" function, from the URL, via:

    $rlpath     = truepath($_POST['pfile']);

I get the rendering of:

var/www/Projects/mysql.user.sql 

I've solved this problem many times before, but when I forget and have to look up HOWTOs do this, the last thing I want is #$%^& crap and mis-information!

Since the "realpath" in PHP no longer works and no one has attempted to fix it, we need to correct the PHP manual and all the forums and blogs with this mis-information crap.

The disturbing part is this is a known bug since PHP 5.3.0.  Almost makes you want to go back to 5.2.x or 4.x.x, so you know your code will work.

I still have not found a good working function to fix this and render a good full path and filename.

If you have one, please submit and help me get both the "realpath" function fixed in the base PHP code and the manuals fixed also.

There is a way to get this using JavaScript at:

[http://stackoverflow.com/questions/4176377/how-to-get-the-full-path-of-the-file-from-a-file-input](http://stackoverflow.com/questions/4176377/how-to-get-the-full-path-of-the-file-from-a-file-input)

With code of:

var pfullfile=$('#pfile').attr('value');

but I'm not good at passing JavaScript vars back to PHP.

All help on this appreciated.

Cheers!

OMR

---

### Post by OldManRiver on 2012-10-28
All,

I also assume this could be done with some implementation of the following linux shell commands:

```

   exec('updatedb');
   exec(locate $_POST['pfile']);

```
but not sure just how to implement this and capture the results other than to pipe to a file and interrogate that file.

Of course will not work on Windows and processing time goes to crap, so not fond of doing this.

Any ideas appreciated!

Cheers!

OMR

---

### Post by dazman19 on 2012-10-29
If you are uploading the file from a form you can use a
<form name="something" enctype="multipart/form-data">

when you submit it it will go to the server in the $_FILES array.

You can get the name which will write it to the /tmp folder (usually depending on your web server settings)

the file name will be in $_FILES['something']['tmp_name']

its details will be in the $_FILES array.

use a function like move_uploaded_file() so it is where you want it.

personally i would write a function to solve that problem for me so i never have to worry about it again.

---

### Post by greenpeace on 2012-10-29
+1 for <form name="something" enctype="multipart/form-data"> and then getting the details from $_FILES.

There are a lot of tutorials around covering the basics of uploading using PHP.. is that what you're doing?  Here's a good one

[http://www.dreamincode.net/forums/topic/19948-file-uploads-tutorial/](http://www.dreamincode.net/forums/topic/19948-file-uploads-tutorial/)

Sticking to PHP for this will be much easier than messing with **exec**, and javascript, being a predominantly client-side language, isn't really the tool for the job.

---

### Post by OldManRiver on 2012-10-29
> **greenpeace said:**
> +1 for <form name="something" enctype="multipart/form-data"> and then getting the details from $_FILES.

There are a lot of tutorials around covering the basics of uploading using PHP.. is that what you're doing?  Here's a good one

[http://www.dreamincode.net/forums/topic/19948-file-uploads-tutorial/](http://www.dreamincode.net/forums/topic/19948-file-uploads-tutorial/)

Sticking to PHP for this will be much easier than messing with **exec**, and javascript, being a predominantly client-side language, isn't really the tool for the job.

GP,

Yeah and I do not want anything to do with uploads, they do not cover what I need at all.  What I need is for PHP to split my ultra large .SQL file from "mysql_dump", where I need to split out every table and for one table I have with excess of over 1 million records, I must chop that up to less than 2,000 records in each file.  

Though MySQL says it will import, from command line, that is a total lie.  Exports great, but can never import.  File is just too large and MySQL times out everytime.  Increasing the parms in the my.cnf file to run for over 30 minutes, which is what is needed, causes MySQL to error, so that approach doesn't work either.  Splitting up the file into workable chunks of data is the only way.

The file will not process without the complete file name and will loose itself in the processing, without all the file info, so this limitation is a complete road block.

I remember solving this years ago, when "realpath" was working, but the suggestion to include the enctype="multipart/form-data" in my FORM declarative did not work, and completely killed my form.

Correction, got the form back, but now will never set my $_POST vars.

Any other suggestions?

Cheers!

OMR

---

### Post by OldManRiver on 2012-10-30
All,

Does what I'm looking for exist in the  PEAR extensions libs?

Cheers!

OMR

---

### Post by dazman19 on 2012-10-30
You want this command line: 
```

exec("mysql -u user -ppassword database < file.sql");
```

you have probably already tried this, but... read on..

Make sure your max_allowed_packet size is something mega large like 64mb or more.

What will probably be causing mysql to cr@p itself is the fact that your table with like a million records will be doing 1 massive insert. And the size of that insert will exceed the max allowed packet size for a query.

if mysql did a seperate insert for each record you would be there all day doing the import, so the dump manages the staggering of records for you with 16MB it might do say 2000-3000 at a time. But you would have trouble importing this onto another server with a max_allowed_packet size of 8MB.

On the server where the dump was taken in the /etc/mysql/my.cnf look for this:

[mysqldump]
quick
quote-names
max_allowed_packet      = 16M

Then on your server set it to MORE than that. (Because 64bit servers/32bit servers have different ideas about what 16M is when it comes to mysql).

On your server you want to set the max_allowed_packet (but not for the [mysqldump] section, you want to set it for the general setting under [mysqld].

Then import the file in 1 go. It will work, I do it all day everyday with massive files (50gb+).

Remember to restart the mysql daemon.

---

### Post by greenpeace on 2012-10-30
> **OldManRiver said:**
> I do not want anything to do with uploads, they do not cover what I need at all.  What I need is for PHP to split my ultra large .SQL file from "mysql_dump", where I need to split out every table and for one table I have with excess of over 1 million records, I must chop that up to less than 2,000 records in each file.  

Apologies, it wasn't clear what exactly the task was from your original post.  

> **OldManRiver said:**
> I remember solving this years ago, when "realpath" was working, but the suggestion to include the enctype="multipart/form-data" in my FORM declarative did not work, and completely killed my form.

Correction, got the form back, but now will never set my $_POST vars.


Is the "method=" attribute on the <form> element sent to "POST" or "GET"?  If it's not included then "GET" is the default.  File information will be included in the $_FILES array.

To be honest, I still don't understand what you're working on... Though it sounds like a task better done from a dedicated tool, rather than a webpage; especially if there is the possibility of crashing MySQL! :)

gp

---

### Post by OldManRiver on 2012-11-02
> **dazman19 said:**
> You want this command line: 
```

exec("mysql -u user -ppassword database < file.sql");
```

you have probably already tried this, but... read on..

Make sure your max_allowed_packet size is something mega large like 64mb or more.

What will probably be causing mysql to cr@p itself is the fact that your table with like a million records will be doing 1 massive insert. And the size of that insert will exceed the max allowed packet size for a query.

if mysql did a seperate insert for each record you would be there all day doing the import, so the dump manages the staggering of records for you with 16MB it might do say 2000-3000 at a time. But you would have trouble importing this onto another server with a max_allowed_packet size of 8MB.

On the server where the dump was taken in the /etc/mysql/my.cnf look for this:

[mysqldump]
quick
quote-names
max_allowed_packet      = 16M

Then on your server set it to MORE than that. (Because 64bit servers/32bit servers have different ideas about what 16M is when it comes to mysql).

On your server you want to set the max_allowed_packet (but not for the [mysqldump] section, you want to set it for the general setting under [mysqld].

Then import the file in 1 go. It will work, I do it all day everyday with massive files (50gb+).

Remember to restart the mysql daemon.

dazman19,

The size of the file, using mysql_dump is over 100GB, not MB, so what is your advice on that. Oh! Due to ongoing problems with updates on Ubuntu, which keep trashing my laptop machine, where I do my dev work, I lost somewhere between 30-50% of the data, so file would be somewhere around 200GB is all data was present.

I've been looking at some of the PHP written MySQL backup routines, but none that I see have the option of a display screen with the dump from "SHOW DATABASES:" that will include the size of the DB or when selecting via "USE myDB" the tables and their size using the "SHOW TABLES;"

All that can be done in the right SQL queries, and could be a way to:
[LIST]
[*]Run standard "Export" on DB and tables that are small enough,
[*]Run "SELECT * FROM mytable;" on files exceeding the limitations, so they can go into "MyTable_Export_(nnn).sql" for as many times as needed to complete the export.
[/LIST]
If the screen controlling the latter, allows for the setting of the "backup directory", then the Import for any restore would be, just find all .sql files listed in the "backup directory" and import one-by-one.

I'm trying to determine what queries are needed and what pre-existing MySQL backup source will be the easiest to mod.

Oh on the change of "my.cnf" for "max_allowed_packet = 16M" I tried setting this larger, but anything over 32M mysql will die and not operate at all.  If I need to exceed this then I would have to read up on other ways to work with mysql parms to make this work and that would be more effort that writing a PHP script to parse out the "Exports".  

There is only one table in the entire dump that exceeds the limitations, so allowing the PHP screen to execute:
```

mysql_dump > mydbname.sql
or
mysql_dump > mydbname.tablename.sql

```
Would let me capture, upfront, all the DB info, except the large table in question.

If I can then capture this "fullpath" that I need, I can setup to open and read the large file and parse it into small files that will not exceed the limitations, then problem solved, but since "realpath" no longer works I can not get this info correctly from PHP.

Thinking I will need to use the JavaScript approach.  Been trying but not succeeding!

Really want the "realpath" function fixed, so anyone that knows how to put pressure on our PHP guru's pleas do!

Cheers!

OMR

---

### Post by pkadeel on 2012-11-02
What I have understood is that

[LIST=1]
[*]you have a very large database and you want to divide it into small chunks to be able to restore it through your website's management panel otherwise the php script dies at 30 secs limit.
[*]you probably have allocated a specific location to store that backed up data. apparently you are storing it within the www root which is browsable to public and hence is very unsafe location.
[*]you want to enter just the file name and want php to find it and pre-pend actual path to it. but in that case it means you are not saving your files at a fix location.
[/LIST]
Now realpath() is to resolve symbolic links like (./../../filename) but not to find a file on your server.


To solve your path problem if the location folder is fixed, you can either pre-pend it by hard coding the backup path in your script or put a file in the backup folder with following code and then include that file in you script which receives the posted form.
[PHP]
define("_BACKUP_PATH", dirname(__FILE__) . '/');

[/PHP]
Now that constant holds the full path of your backup location. just pre-pend it to your  uploaded filename.

In case I misunderstood the problem and infact you want to build a full backup and restore script, even then it is not as hard as you are thinking and does not need any changes at the backend if your php settings on the host allows set_time_limit() function. [COLOR=#000000][FONT=verdana][/FONT][/COLOR][COLOR=#000000][FONT=verdana][/FONT][/COLOR]

---

### Post by OldManRiver on 2012-11-02
> **pkadeel said:**
> What I have understood is that

[LIST=1]
[*]you have a very large database and you want to divide it into small chunks to be able to restore it through your website's management panel otherwise the php script dies at 30 secs limit.
[*]you probably have allocated a specific location to store that backed up data. apparently you are storing it within the www root which is browsable to public and hence is very unsafe location.
[*]you want to enter just the file name and want php to find it and pre-pend actual path to it. but in that case it means you are not saving your files at a fix location.
[/LIST]
Now realpath() is to resolve symbolic links like (./../../filename) but not to find a file on your server.


To solve your path problem if the location folder is fixed, you can either pre-pend it by hard coding the backup path in your script or put a file in the backup folder with following code and then include that file in you script which receives the posted form.
[PHP]
define("_BACKUP_PATH", dirname(__FILE__) . '/');

[/PHP]
Now that constant holds the full path of your backup location. just pre-pend it to your  uploaded filename.

In case I misunderstood the problem and infact you want to build a full backup and restore script, even then it is not as hard as you are thinking and does not need any changes at the backend if your php settings on the host allows set_time_limit() function. [COLOR=#000000][FONT=verdana][/FONT][/COLOR][COLOR=#000000][FONT=verdana][/FONT][/COLOR]

pkadeel,

No it does not!  The "__FILE__" only works for files found in the "/var/www" localhost or DocDirectory, not for anything else.  Additionally this is not looking for anything on the server side, but on the user/client side and will not process at all if it fails the "file_exists" test.  Without the full path this test will **"ALWAYS"** fail.

So the "truepath" or "realpath" must be rendered to process that files at all!

Hope that explains it a little better.

Oh realpath used to do this and was not limited to just symlinks.

Cheers!

OMR

---

### Post by OldManRiver on 2012-11-02
All,

I found the SQL Query:
```

SELECT `table_schema`, `table_name`, sum( data_length + index_length ) / 1024 / 1024 "Data Base Size in MB"
FROM `information_schema`.`tables` GROUP BY `table_schema`; 

```

Gives me the DB size, so now looking for same type of query to determine table size for the large DB that exceeds the MySQL specs.

Cheers!

OMR

---

### Post by pkadeel on 2012-11-02
> **OldManRiver said:**
> pkadeel,

No it does not!  The "__FILE__" only works for files found in the "/var/www" localhost or DocDirectory, not for anything else.  Additionally this is not looking for anything on the server side, but on the user/client side and will not process at all if it fails the "file_exists" test.  Without the full path this test will **"ALWAYS"** fail.

So the "truepath" or "realpath" must be rendered to process that files at all!

Hope that explains it a little better.

Oh realpath used to do this and was not limited to just symlinks.

Cheers!

OMR
The understanding that __FILE__ works only inside /var/www/ is wrong. It depends from where the include call is made. If the call is made from within /var/www/ then the returned value will be the full file path. I know that because I am practically using this it on my server.

Having said that, now you say that this search or what ever is to be made on the client side and you also said a couple of posts above that you are not uploading any file then what exactly you want to do? Because PHP won't help you on client side.

---

### Post by pkadeel on 2012-11-02
> **OldManRiver said:**
> All,

I found the SQL Query:
```

SELECT `table_schema`, `table_name`, sum( data_length + index_length ) / 1024 / 1024 "Data Base Size in MB"
FROM `information_schema`.`tables` GROUP BY `table_schema`; 

```Gives me the DB size, so now looking for same type of query to determine table size for the large DB that exceeds the MySQL specs.

Cheers!

OMR
[PHP]
    function GetTablesInfo() { 
        $tstatus = array(); 
        $result = $this->query('SHOW TABLE STATUS'); 
        if ($result) { 
            while ($row = $result->fetch_object()) { 
                $tstatus[$row->Name] = $row; 
            } 
            $result->free(); 
        } 
        return $tstatus; 
    }
[/PHP]
The returned array will give you all the info for tables inside the connected database.

SHOW query has many other variants aswell

---

### Post by dazman19 on 2012-11-04
I would just modify the query you have got only slightly.

```
SELECT `table_schema`, `table_name`, sum( data_length + index_length ) / 1024 / 1024 as "Data Base Size in MB"
FROM `information_schema`.`tables` WHERE `table_schema` = 'yourdatabasename' GROUP BY `table_name`;
```

It worked for me when i ran it on my db. :D

The mysql specs are here. [http://dev.mysql.com/doc/refman/5.0/en/table-size-limit.html](http://dev.mysql.com/doc/refman/5.0/en/table-size-limit.html)
```

+--------------+------------------------------------+----------------------+
| table_schema | table_name                         | Data Base Size in MB |
+--------------+------------------------------------+----------------------+
| ezymerged    | animal                             |           0.14062500 |
| ezymerged    | animalcolour                       |           0.03125000 |
| ezymerged    | animalmasterproblem                |           0.04687500 |

```

Because you already know the table size in MB you can output tables bigger than lets say 1g e.g. here is my output:

then export the table that is too big to a single file. And then drop it, then export the rest of the database.

I am about 90% sure the problem you got is either you are exceeding the limits of Linux 2.2-Intel 32-bit kernel OR you are exceeding the maximum packet size because there is probably a blob in your table that is taking up a very large amount of space, in which case you will need to increase the max packet size, possibly even more than 16mb or 32mb. If the  blob is too big then there is no way you can have a single insert statement to load data into it because you will exceed the max allowed packet size. This guy set his to 500MB [http://stackoverflow.com/questions/8062496/how-to-change-max-allowed-packet-size](http://stackoverflow.com/questions/8062496/how-to-change-max-allowed-packet-size)

ALSO if you have loads of records in 1 table, you may want to remove the index's use mysql workbench to generate the  create statement for you, and then do an ALTER TABLE for the index's on after you have loaded the dump in. Because if you dont then after every insert mysql will try to add to the index and it will go super slow. 

lastly if you are having a php timeout problem then use set_time_limit(0); at the top of the script.

---

### Post by OldManRiver on 2012-11-05
> **pkadeel said:**
> The understanding that __FILE__ works only inside /var/www/ is wrong. It depends from where the include call is made. If the call is made from within /var/www/ then the returned value will be the full file path. I know that because I am practically using this it on my server.

Having said that, now you say that this search or what ever is to be made on the client side and you also said a couple of posts above that you are not uploading any file then what exactly you want to do? Because PHP won't help you on client side.
pkadeel,

OK you assume and "include" or "require" statement, there is none, at least not now and the path must render from the "FORM" which will always be in the "/var/www" dir, unless you have a non-standard alias, which occurs less than 15% of the time.

As for design of this app, I originally was going to put it into one single file, now I have decided on the following:
[LIST]
[*]Screen file (parse_sql.php),
[*]Class Object File (parse_sql_class.php),
[*]Config File (config.php),
[*]Processing File (parse_sql_proc.php).
[/LIST]
The screen will contain/gather all the setup info, with Run, Cron, and Restore buttons, the input field for the path, etc.  It will write this to config.php and processing will call both config and class to process.  Putting the screen info into the config file will allow the cron to run with commandline PHP.

For right now, since there is no effective way to get the realpath from the <input type='file'> field, when browsing for the file '/backups/DB Backups/Dumps'.  Will change that to get the real and full filename, when I recall how this is done, again!

I now have the 2 functions for sizing DBs and Tables of:
```

		function _GetDBSize($db_max) {
			$this->_Connect();
			$v_ray = array();								// Set output array
			$value = array();								// Set array for small DBs
			$large = array();								// Set array for large DBs
			$sqlvl = "SELECT `table_schema`, ".
						"sum( data_length + index_length ) / 1024 / 1024 ".
						"`db_size` FROM `information_schema`.`tables` ".
						"GROUP BY `table_schema`;"			
			if (!($result = $this->_Query('$sqlvl'))) { return false; }  // end if !result
			while ($row = mysql_fetch_row($result)) {
				if ($row['db_size']>$db_max) {
					$large[] = $row;
				} else {
					$value[] = $row;				
				}
			}  // end while $row
			$v_ray = array(0=>$value,1=>$large);
			return $v_ray;
		}  // end function _GetDBSize

		function _GetTBLSize($db_max,$tbl_array) {
			$this->_Connect();
			$v_ray = array();								// Set output array
			$value = array();								// Set array for small DBs
			$large = array();								// Set array for large DBs
			$sqlvs = "SELECT `table_schema`, , `table_name`".
						"sum( data_length + index_length ) / 1024 / 1024 ".
						"`db_size` FROM `information_schema`.`tables` ";						
			$sqlve = "GROUP BY `table_name` ORDER BY `table_schema` , `table_name`;";
			foreach ($tbl_array as $key => $val) {
				echo "K=> $key V=> $val <br>";
			}
			//return;
			if (!($result = $this->_Query('$sqlvl'))) { return false; }  // end if !result
			while ($row = mysql_fetch_row($result)) {
				if ($row['db_size']>$db_max) {
					$large[] = $row;
				} else {
					$value[] = $row;				
				}
			}  // end while $row
			$v_ray = array(0=>$value,1=>$large);
			return $v_ray;
		}  // end function _GetTBLSize

```

Working on the rest of the code.

Oh the reason to get the full filename with path, is when I release this to the user community, everyone will have a different idea of where they want their backup directory, so must be able to browse to and find via the displayed PHP/HTML FORM.

Cheers!

OMR

---

### Post by OldManRiver on 2012-11-09
Anyone,

Got an answer on, the original Q "how to get the REAL fullpath and filename?"

Cheers!

OMR

---

### Post by OldManRiver on 2012-11-09
All,

OK found this info at:

[http://stackoverflow.com/questions/81180/how-to-get-the-file-path-from-html-input-form-in-firefox-3](http://stackoverflow.com/questions/81180/how-to-get-the-file-path-from-html-input-form-in-firefox-3)

Which says this is a security issue from FireFox meeting the "Secure Mode" mandate and only applies in Ver 3.0 and newer.  I'm developing with FF 16.0.x.

I'm going to put the Q out on the Mozilla-FireFox forum, to see what they can tell me about this.

Looks like I also need to add it as a "Bug" to the PHP Bug Tracker as this problem is not going away and needs a REAL fix.

Cheers!

OMR

---

### Post by OldManRiver on 2012-11-25
> **pkadeel said:**
> What I have understood is that
To solve your path problem if the location folder is fixed, you can either pre-pend it by hard coding the backup path in your script or put a file in the backup folder with following code and then include that file in you script which receives the posted form.
[PHP]
define("_BACKUP_PATH", dirname(__FILE__) . '/');

[/PHP]
Now that constant holds the full path of your backup location. just pre-pend it to your  uploaded filename.

In case I misunderstood the problem and infact you want to build a full backup and restore script, even then it is not as hard as you are thinking and does not need any changes at the backend if your php settings on the host allows set_time_limit() function. [COLOR=#000000][FONT=verdana][/FONT][/COLOR][COLOR=#000000][FONT=verdana][/FONT][/COLOR]
pkadeel,

This cannot be "pre-pended", it comes from the HTML form and must have the entire path to work.  I put the code from the first 3 file in Pastbin at:

[http://pastebin.com/drxeiCvS](http://pastebin.com/drxeiCvS)

Of course it is not done, cannot get past this problem; therefore can't step through any processing code since I can never get a good filename to process.

Cheers!

OMR

---

### Post by OldManRiver on 2013-02-19
All,

I saw some code where the issue is fixed with "flash" script. Wondering if any have insight to that?

Cheers!

OMR

---

### Post by OldManRiver on 2013-06-29
All,

I would think every developer out there would understand this problem, as it's simple, the user at the browser is being asked for a file in the backup directory on his/her machine, has nothing at all to do with the server doing the processing, because we are still in the input form on the browser with no submit yet (yea client side - does it need javascript? Even javascript has no answer, been asking there also, seems to be a FireFox issue, been told only Flash resolves this.).

Since the file and backup directory are user defined, there can be over a billion possibilities and only the user knows that, so they "browse" via the button to the file.

Furthermore the file will never be in /var/www or any other localhost config, so the file must be validated before attempting FTP/Upload of it to a remote or server directory.

Without a "FullPath" or "RealPath" the file can never be validated and therefore never can be processed.  This should be part of every "file upload" function set and PHP needs to support this out onto the client side, with some sort of extension, even though PHP is supposed to be 100% server side, some things just can not be done without client side support!

This is a PHP 101 requirement, so why no solution to an everyday problem?  I have a suspicion that the frameworks have solved this problem, so looking in different frameworks to see how they handled this issue.

Cheers!

OMR

---

### Post by SeijiSensei on 2013-06-29
> **OldManRiver said:**
> Since the file and backup directory are user defined, there can be over a billion possibilities and only the user knows that, so they "browse" via the button to the file.

I'm with you so far.  

> Furthermore the file will never be in /var/www or any other localhost config, so the file must be validated before attempting FTP/Upload of it to a remote or server directory.

Now I'm starting to be lost.  Are you asking for this validation to occur before the file is uploaded?  If so, PHP cannot accomplish that as it is server-side only.  You would have to write a Javascript routine to do whatever validation is required before the file is uploaded.

If by "validation" you mean the type of checking described in Example #2 of [this page](http://www.php.net/manual/en/features.file-upload.post-method.php) (file size, mimetype, etc.), then the code presented there gives you a template.  If you mean something more sophisticated than that ("does the table have the correct number of fields", or something similar), you would have to do that either with JS before the file is sent, or in PHP before the [move_uploaded_file()]("http://www.php.net/manual/en/function.move-uploaded-file.php") function is called.  Until then the file is stored in the temporary location defined by [upload_tmp_dir](http://www.php.net/manual/en/ini.core.php#ini.upload-tmp-dir) in php.ini.

What am I missing?

---

### Post by trent.josephsen on 2013-06-30
> **OldManRiver said:**
> I would think every developer out there would understand this problem, as it's simple, [...]

This **should be** part of every "file upload" function set and **PHP needs to support this** out onto the client side, with some sort of extension, even though PHP is supposed to be 100% server side, some things just can not be done without client side support!

This is a **PHP 101 requirement**, so why no solution to an **everyday problem**?  I have a suspicion that the frameworks have solved this problem, so looking in different frameworks to see how they handled this issue.
(emphasis added by me)

This entire thread exhibits the X-Y problem. You have some need (X) that only you understand, you have some preconceived notion about how it needs to be solved (Y), and instead of asking about X, you are asking about Y. This often leads to frustration for you and confusion for anyone trying to help, because when you ask about Y it misleads people into thinking you have a Y-type problem, when in fact you have an X-type problem. On the other hand, when people suggest ways to solve a Y-type problem, few if any of their solutions will be relevant to what you are trying to do.

I am not an expert in PHP or web development, but such experts do exist and there are even some in this forum. If you want to solve X, you would do well to ask about X and listen to the advice you receive. Despite reading the whole thread, I'm still not sure exactly what X is and I agree with SeijiSensei that your last post does nothing to clear things up. You also said earlier that you had found the answer to your original question, so is the problem you're having now the same, or different?

---

### Post by OldManRiver on 2013-07-02
SS/TJ,

Hey glad to see your responses!  Means someone is following and thinking about what I'm saying.

First understand that exporting the data using "mysqldump" does not have a problem as mysqldump bypassing the my.cnf file and settings, so Size of dump does not matter and that can be set, by the user in the form, to goto any directory on his/her local machine, directly, but must run via Linux command line (not sure how you do this in Windows) to bypass all the browser, PHP and MySQL settings in the config files.  Therefore download of an entire HUGE DB is totally possible.

Where the problems exist is in uploading this as a backup to a selected remote server.  I do have the following BASH script with allows a direct backup to any remote server, but backup is spread out in multiple files and my goal is only one file:

```
#!/bin/bash
#
# This Bash script will automatically take care of backing up all your critical 
# information so that in a disaster you can setup your site(s) on a new server. 
#
# Obviously you will need to offload the backups to a different location from 
# time to time.
#
# This script takes care of :
#    * apache configuration files
#    * crontabs
#    * /home/WWW (or wherever you keep your content / code)
#    * /etc
#    * MySQL (All DBs)
#    * it will also Rotate the MySQL query log if you have it running for debugging / dev.

# The following lines allows this script to be called with "NOHUP" background processing
# and with passing of the 4 critical secure vars.
# Format:
#       bash nohup backup_critical.sh -b '/data/Backups/' -h 'localhost' 
#					-u myuserid -p mypassword > /logdir/bg_process.log
#
#		Processing log 'bg_process.log' keeps any background processing returned errors

clear;
while getopts b:h:p:u: option
	do
		case "${option}"
			in
				b) BACKUPDIR=${OPTARG};;
				h) MHOST=${OPTARG};;
				p) MPASS=${OPTARG};;
				u) MUSER=$OPTARG;;
		esac
done


echo "";
# Rotate the MySQL query log
echo '' > /usr/local/mysql/var/mysql_queries.log
#
MYSQL="$(which mysql)"
MYSQLDUMP="$(which mysqldump)"
GZIP="$(which gzip)"
NOW=$(date +"%d-%m-%Y")
TAR="$(which tar)"

# Next line commented out to keep from deleting the backup dir
#[ ! -d $BACKUPDIR ] && mkdir -p $BACKUPDIR || /bin/rm -f $BACKUPDIR/*

echo ""
echo "apache configuration files are being backed up: "
$TAR -cjf $BACKUPDIR/apache_conf.tar.$NOW.bz2 /usr/local/apache/conf
#
echo ""
echo "crontabs are being backed up: "
$TAR -cjf $BACKUPDIR/crontabs.tar.$NOW.bz2 /var/spool/cron
#
echo ""
echo "/home is being backed up: "
$TAR -cjf $BACKUPDIR/home.$NOW.tar.bz2 /home
#
echo ""
echo "/www is being backed up: "
$TAR -cjf $BACKUPDIR/www.$NOW.tar.bz2 /var/www
#
echo ""
echo "/etc is being backed up: "
$TAR -cjf $BACKUPDIR/etc.$NOW.tar.bz2 /etc
#
echo ""
echo ""
#
echo "mySQL backup script has been started."
echo "The following databases are being backed up: "
echo ""
echo "--------------------------------------------"
echo ""
#
DBS="$($MYSQL -u $MUSER -h $MHOST -p$MPASS -Bse 'show databases')"
for db in $DBS
do
echo $db
FILE=$BACKUPDIR/$db.$NOW.gz
$MYSQLDUMP -R -u $MUSER -h $MHOST -p$MPASS $db | $GZIP -9 > $FILE
done
```



SS,
Your statement:
> Until then the file is stored in the temporary location defined by upload_tmp_dir in php.ini.
Will this autoload to there without clicking any submit button, so can the the test on the file be:

```
"if (file_exists($php_upload_path.$myfile)) { do_something; }"?
```

from the server side and run a javascript to validate on the client side, before clicking the submit?

How would you then query the javascript, with PHP to make sure the file is there before allowing "submit" actions?

Also since the files I'm dealing with exceed all PHP upload and FTP limits, need a pre-processor to "SPLIT" the files into managable sized subfiles.

TJ,

What I found is that past FireFox 3, FF is truncating the path, yielding only the filename.ext.  Files will upload/download well if a.) They exist in the localhost directory tree, even under subdirectory or alias, b.) are hardcoded into the processing code, c.) passed as vars that contain the entire file path.

What no longer works is the location of files or entire directories, on the client machine that can allow processing (uploading or otherwise), outside the definitions above, so now any HTML form needing both a path dir and file from one "<INPUT>" line or capturing the path/dir and file in 2 seperate "<INPUT>" fields.

In my personal current case I am processing DB backup files in access of 4GB, so have to be broken down on the client side as: a.) They are too large to FTP or upload, b.) They are too large for MySQL to process them.  Remember I'm designing my process to support all users, so the majority will only have the default PHP.ini and My.cnf settings, so limited at 2-8Mb and 60 seconds of processing on any transfer or interaction with the DB.

Sure will have to go outside of native PHP to do this, but still a problem needing a resolution, regardless of technology.  Hope you have some suggestions!

Cheers!

OMR

---

### Post by SeijiSensei on 2013-07-02
Am I correct in concluding that you are trying to let random people upload 10GB MySQL backups?  That seems like asking for trouble to me.

If you asked me how to do this, I'd use mysqldump to create the backup and rsync to move it between machines.  I wouldn't have any web-based method for this at all.

Why don't you step back for a second and explain exactly what you are trying to do?  Why do you need a web application for this?  Aren't backups and restores of this magnitude something only a competent administrator should be doing?  I certainly think so.

I'd probably automate the entire process with cron and shell scripts, too.  I don't see much reason for human intervention except when something crashes, and then only an administrator should be involved.

---

