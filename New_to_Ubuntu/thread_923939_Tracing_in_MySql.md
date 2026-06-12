---
title: "Tracing in MySql"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by cearlp on 2008-09-18
Is there a trace mechanism in MySql? A SELECT statement from the command line works but the same select statement from a PHP script does not find any records. Connection to the database seems to succeed and echo statements in the PHP script display everything as expected in the html output, even the select statement, but nothing is returned from the mysql object call. I am running apache2, php5 and Mysql on Ubuntu 8.04. Any suggestions would be appreciated.

---

### Post by jamesrl on 2008-09-19
Could you post your php script, and the output from it?  Can you try a really simple query e.g. 'select * from your_table_name LIMIT 2'?  I'm not aware of a trace function for debugging mysql queries, but haven't had any problem using php5 with mysql or sqlite.

---

### Post by cearlp on 2008-09-19
I have tried very simple select statements, but nothing is ever returned. I think my interface to MySql must be incorrectly setup, but I don't know how to confirm that. Here is the relevant portion of the php script called from an html form action:

<html>
<head>
        <title>Member Information Results</title>
</head>
<body>
<?php
        //create variable names
if (!get_magic_quotes_gpc())
{
        $fnm = addslashes($_POST['$fnm']);
        $lnm = addslashes($_POST['$lnm']);
} else {
        $fnm=$_POST['fname'];
        $lnm=$_POST['lname'];
}

if (!$fnm || !$lnm)
{
        echo 'A full name is required';
        exit;
}
echo 'fname = ', $fnm;
echo '<br>lname = ', $lnm;

$db = mysqli_connect('localhost', 'root', 'rootpw', 'members');
if (mysqli_connect_errno())
{
        echo 'Error: Could not connect to the Members Database';
        exit;
}
$query = sprintf("select * from members where fname='%s'and lname ='%s'",
        mysql_real_escape_string($fnm),
        mysql_real_escape_string($lnm));
echo '<br>Query = ', $query;
$resuslt = mysql_query($query);
If (!$result)
{
        echo '<br>Query failed!';
        exit;
}  
$num_results = $result->num_rows;
if ($num_results == 0)
{
        echo '<br>No maching record(s) found.';
        exit;
}
$row = mysql_fetch_assoc($result);
...
...
...
I hope this is enough to show what I am doing (wrong?).

---

