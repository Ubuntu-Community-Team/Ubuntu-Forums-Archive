---
title: "mysql my php"
date: 2009-07-08
forum: Programming Talk
---

### Post by georgerobbo on 2009-07-08
I've just started getting my head around MYSQL databases and using PHP to model the database. I was wondering what is the best method of selecting information from the database. 
 
[PHP]
<?php
%con = mysql_connect("localhost","george","password");
if (!$con)
{
die ('Could not connect: ' . mysql_error());
 
mysql_select_db("wp_content", $con);
$return = mysql_query("SELECT * FROM wp_content");
 
while ($row = mysql_fetch_array($return))
{
echo $row['intro'];
}
 
mysql_close($con);
?>
[/PHP]

---

### Post by CrazyMonkeyFox on 2009-07-08
Well you pretty much got it, its just a matter of understanding what it is you're doing. I create a function for connecting to the database and selecting the table which you can put on your page, or in a function library.
[php]
function connect_to_database( $host, $user, $password, $dbname )
    {
        // Try to connect to database
        $dbconnection = mysql_connect( $host, $user, $password );
        if ( ! $dbconnection )
        {
            die();
        }
        // Try to select database
        $dbselection = mysql_select_db( $dbname );
        if ( ! $dbselection )
        {
            die();
        }
        return $dbconnection;
    }
[/php]Above, before all the die functions feel free to redirect to an error page or whatever, its not too hard, figure you can get it yourself.

[php]
$dbconnection = connect_to_database( 'localhost', 'george', 'password', 'wp_content');

$retrieve_sql = "SELECT * FROM wp_content"; 
    $dbretrieve_result = mysql_query( $retrieve_sql );
    if ( ! $dbretrieve_result )
    {
        die();
    }
    if ( mysql_num_rows($dbretrieve_result) != 0 ) 
    {
        while ( $row = mysql_fetch_assoc($dbretrieve_result) ) 
        {
            echo "<p>{$row['intro']}</p>";
        }
    }
    mysql_free_result( $dbretrieve_result );
    mysql_close( $dbconnection );
[/php]As I said pretty much what you had, just utilising my function, and also a few error preventatives.

[php]
if ( ! $dbretrieve_result )
    {
        die();
    }
[/php]If for some reason it can't connect, it exits the operation.

[php]
if ( mysql_num_rows($dbretrieve_result) != 0 ) 
[/php]If the table exists, but has no actual information in it, i.e an empty set. This prevents it displaying nothing, and being happy about it : )

[php]
mysql_free_result( $dbretrieve_result );
    mysql_close( $dbconnection );
[/php]Just as a matter of hygiene, its nice to clean up. The first command just clears the variable of any value, and the last one closes the connection succesfully.
If theres any specifics feel free to ask. : )

---

