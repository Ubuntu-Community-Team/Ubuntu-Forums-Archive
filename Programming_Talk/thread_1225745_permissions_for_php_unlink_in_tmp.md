---
title: "permissions for php unlink in /tmp"
date: 2009-07-28
forum: Programming Talk
---

### Post by milton1 on 2009-07-28
I am trying to use php to get a csv file to delete from /tmp if it is present, then recreate from a sql query. I can get the query to create the file if it is not already there, but I can't seem to delete old versions of it. here is my code for delete/create:

```
	$query="select projectNumber, firstName, lastName, title, description, category1, category2, category3 from projects into outfile '/tmp/scifairexport.csv' fields terminated by ';' lines terminated by '\n'";
	$expfile='tmp/scifairexport.csv';
	if(file_exists($expfile)){unlink($expfile);}
	mysql_query($query);

```

Just as a note, I am not missing a '/' in $expfile; I have created tmp as a symlink in the website directory.

If the file already exsists, I get this error:

Warning: unlink(tmp/scifairexport.csv) [function.unlink]: Operation not permitted in export.php on line 20

Obviously, this is a permissions issue, but why can I not delete something from /tmp? Isn't tmp read/write for all users? It seems to be so, when I check the permissions. Any thoughts on what I am missing?

---

### Post by milton1 on 2009-07-28
Just one more piece of info, here are the permissions on the output file:

-rw-rw-rw- 1 mysql    mysql     544 2009-07-28 19:27 scifairexport.csv

---

### Post by miklcct on 2009-07-29
To unlink a file, you need the write permission from the DIRECTORY, not from the file.

---

### Post by milton1 on 2009-07-30
> **miklcct said:**
> To unlink a file, you need the write permission from the DIRECTORY, not from the file.

yeah, I gathered that much already, but why would the web server not have write permissions to /tmp?

---

### Post by milton1 on 2009-07-30
OK, I have a working theory: it seems that files written to /tmp by one user cannot be modified by another, even if the file is rw. My file is written by mysql, and the unlink command is called by www-data. Any thoughts on how to get around this little problem?

---

### Post by milton1 on 2009-07-30
I think I may have solved it. Placing a subdirectory within /tmp, with full permissions, I am able to remove files written to this subdirectory by another user. I will test this on my development machine later today and post the result.

---

### Post by milton1 on 2009-07-30
> **milton1 said:**
> I think I may have solved it. Placing a subdirectory within /tmp, with full permissions, I am able to remove files written to this subdirectory by another user. I will test this on my development machine later today and post the result.

This fixed the problem.

---

