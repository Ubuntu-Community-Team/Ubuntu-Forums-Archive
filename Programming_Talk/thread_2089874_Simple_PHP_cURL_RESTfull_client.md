---
title: "Simple PHP cURL RESTfull client"
date: 2012-11-30
forum: Programming Talk
---

### Post by Xender1 on 2012-11-30
So I am trying to broaden my web skills by learning cURL and handling a GET request as JSON. So far I have a database set up that has a table of unique id's and usernames, and another table that references the unique id and has comments about that user. Essentially I want to reference a php script (users.php) with a GET header of either users.php?q=/  this will return all of the users and their id, or also by users.php?q=/userid  and in this case it will return all the comments about that user. 

$ch=curl_init();
curl_setopt($ch, CURLOPT_URL, "example.com");
curl_setopt($ch, CURLOPT_HEADER, 0);
curl_exec($ch);
curl_close($ch);

I understand that that is the basics of the cURL, but am confused as to how to execute it. So I guess stupid question, but for what I am trying to do would I just change "example.com" to users.php?q=/ (or q=/userid)(running this on localhost), check that $_SERVER['REQUEST_METHOD'] was GET and then parse $_GET['q'] to figure out what sql query to ask for and then echo the results of the sql statement?

I have written code in PHP that makes use of GET and POST methods along with interacting with a sql database (using a PDO connection), just confused how to implement this with just one script file and using cURL. Thanks for any help / pointers!

---

