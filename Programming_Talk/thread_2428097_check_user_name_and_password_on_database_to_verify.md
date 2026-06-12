---
title: "check user name and password on database to verify the dataset"
date: 2019-09-30
forum: Programming Talk
---

### Post by dilbert_one on 2019-09-30
good dayx dear experts  hello to everyone, ;) 




i have a php-scritp that does not log to the mysql-db. it throws errors all the time: 


```
 please fix the following errors  Try again! Connection with database failed.
Reason: SQLSTATE[HY000] [2002] No such file or directory

```

i am not sure what goes on - if


my guesses 
- i use wrong credentials: 
- Socket-Problems - i.e. with the sockets cf  [https://stackoverflow.com/questions/1435445/error-on-creating-connection-to-pdo-in-php](https://stackoverflow.com/questions/1435445/error-on-creating-connection-to-pdo-in-php)
vgl pdo_mysql.default_socket=/opt/lampp/var/mysql/mysql.sock 

as for **the credentials**: i think i can check them with a script: 

As you see, this form authenticates the user through check_user-pass.php.  Well - It should  look for those credentials on my database; if they exist, returns OK, else returns value NO.
So my question is: exactly what code should I include in check_user-pass.php? 
I tried to add more code but couldn't do that as well! My current code is:

**note: **The name in you form is user_name but in your script you look for username



```


$username=$_POST['username']; 
should be

$username=$_POST['user_name']; 
EDIT:
If you use crypt to encrypt your password before you put them in the database, try this

$sql="SELECT * FROM $tbl_name WHERE username='$username'";
$result=mysql_query($sql);

// Mysql_num_row is counting table row
$count=mysql_num_rows($result);
// If result matched $username and $password, table row must be 1 row
if($count==1){
    $row = mysql_fetch_assoc($result);
    if (crypt($password, $row['password']) == $row['password']){
        session_register("username");
        session_register("password"); 
        echo "Login Successful";
        return true;
    }
    else {
        echo "Wrong Username or Password";
        return false;
    }
}
else{
    echo "Wrong Username or Password";
    return false;
}
EDIT: myBB seems to use a crapload of md5 hashing for their passwords, try this

$sql="SELECT * FROM $tbl_name WHERE username='$username'";
$result=mysql_query($sql);

// Mysql_num_row is counting table row
$count=mysql_num_rows($result);
// If result matched $username and $password, table row must be 1 row
if($count==1){
    $row = mysql_fetch_assoc($result);
    if (md5(md5($row['salt']).md5($password)) == $row['password']){
        session_register("username");
        session_register("password"); 
        echo "Login Successful";
        return true;
    }
    else {
        echo "Wrong Username or Password";
        return false;
    }
}
else{
    echo "Wrong Username or Password";
    return false;
}


```

[B]ideas and questions 
[/B]

well i just want to verify a set of user-credentials: 

- no encryption - what i want to do is ** just a check of a given set of credentials**
- this is what i want to do and everything should be fine.

as for the credentials: i think i can check them with a script: 

As you see, this form authenticates the user through check_user-pass.php.



**_Idea:_** It looks for those credentials on my database; if they exist, returns OK, else returns value NO.
So my question is: exactly what code should I include in check_user-pass.php?






regards


**update: **


i can do this with a spimple test the connection script too: 



```


<?php
if(function_exists('mysqli_connect')){
if(!($link = mysqli_connect('localhost','username','password','my_db'))){
die('could not connect: ' . mysqli_error($link));
}
} else {
die("don't have mysqli");
}
echo 'connect successfully';
mysqli_close($link);
```

---

### Post by slickymaster on 2019-09-30
Thread moved to **Programming Talk** for a better fit

---

### Post by dilbert_one on 2019-09-30
hello dear slickymaster

many many thanks for your help - have a great day

---

### Post by sdsurfer on 2019-09-30
The question (or questions) are a bit confusing. Are you asking to solve the database connection problem, or validate passwords, or both? (I'm assuming both)

The link you referenced is discussing PDO and you're not using PDO here, you are using native MYSQL connection methods. But let's start from scratch.

**#1 Database connection issues:** another point of confusion is you say you are getting an error but

> i can do this with a simple test the connection script too: 

So does that work? Also note that you are using mysql[SIZE=4]**i**[/SIZE] in your test connection script and mysql (without the i) in your "password" script. They are not the same thing (but, credentials in one should work in the other.)

If it does, there is something in your "password script" that is not configured properly. Compare the two, you will find something different. If you search fo HY000 2002 you will find a variety of explanations as to the ***meaning*** of the error but it boils down to one thing: from your PHP script the connection is being refused. It could be anything - you haven't granted privileges in the database to the user making the request, a localhost connection issue, or as mentioned above, you just have a broken connection or typo in your code (if the test script works,) or a variety of other things.

> So my question is: exactly what code should I include in check_user-pass.php?

***#2 To do what, exactly?*** Just get it to work, validate user credentials against a database? If that is the case, see below after the following advice.

You appear to be new at PHP, and if this is an exercise in learning, all well and good, but you very well may be at the ***beginning of building very bad habits.*** The following advice may hopefully steer you down the right path(s.)

What you are planning here is to directly take input from a form via method $_POST and query your database with it. Back up a step and do a couple searches for "PHP SQL Injection." Supposing I do something bad like enter this into my password field:

```
abcd1234' or 1=1 or username='
```

or

```
abcd1234'; drop table users;
```* (It's an easy guess the users table is named . . . users, another common early mistake)*


This potentially turns the password query to

```
SELECT * FROM users WHERE username='$username' or 1=1 or username=''
``` *(Because 1=1 is always true, can potentially display all users in the table*)

or

```
SELECT * FROM users WHERE username='$username'; drop table users;
```* (Just deleted the entire users table.)*

The second thing can be gleaned from this statement in your code sample:

> EDIT: myBB seems to use a crapload of md5 hashing for their passwords, try this

There is a ***reason*** there is a lot of hashing, and the people who wrote myBB (and just about every other software out there) are very smart, most of them far smarter than myself (and I've been doing this for over 25 years.) You would do well to learn from them. That being said, the approach here is very old-school and prone to bugs and errors. As mentioned, if this is a learning exercise, all well and good, and I for one will do what I can to help you through it, but this code should never be on a modern site in production.

With all that out of the way, if you're asking how to validate user credentials from a login form, and you're not willing to use a framework that is already built, tried, debugged and tested by Very Smart Programmers,

- Filter your input - learn how to do this first.

- There are two popular approaches (and there are more) to "look up" and compare user password input against a database value:
-- Use PHP native hashing algorythms to store and compare the passwords (as you appear to be doing here)
-- Leverage MYSQL encrypting functions to do the same thing. This moves the encrypting responsibility to the database layer, simplifies your code, and avoids having to update the code if a particular PHP method evolves or becomes deprecated.

- We can continue using legacy methods (mysql_query(), etc.) but it would be in your interest to learn more modern methods. A lot of developers don't like PHP PDO, but it's something used quite often because it eliminates a lot of the issues with user input and has other advantages.

So let's get question #1 answered, does your test connection script work? From there we'll help you get this running - **assuming** this is not code you would ever use anywhere on a live site. :-)

---

### Post by SeijiSensei on 2019-09-30
Why on earth are you storing the password in the session? Beyond the initial authentication, you don't need to keep it around. Just store a flag that indicates if the user is authenticated.

```

$myuser=trim($_REQUEST['username'];
$mypass=trim($_REQUEST['password'];
$_SESSION['auth']=0;
$_SESSION['user']="";
$check_auth=mysql_query(etc.);
if ($check_auth) {
    $_SESSION['user']=$mypass;
    $_SESSION['auth']=1;
}

```

Don't forget to trim() the username and password before checking in case the user enters extraneous spaces.

Next, are you using the password itself as a salt for [crypt()]("https://www.php.net/manual/en/function.crypt.php")? No one uses DES anymore because it's insecure. If you want to create a password hash use [sha1()]("https://www.php.net/manual/en/function.sha1.php"). I use the concatenation of the username and password with a third known string like "let's hash this password!" as the input to the sha1 function.

```

$shacheck=$myuser.$mypass."let's hash this password!";
$check_auth=mysql_query("select * from somedatabase where passhash='$shacheck';");

```

If you want to be able to decrypt the passwords, you need a symmetric function like Rijndael-256. I've used that in combination with a  fixed secret key and base64 encoding with functions like these:

```

function b64_encrypt($string,$key) {
    # encrypt a string with Rijndael-256 and $key
    # return the base64 encoding of the encrypted result

    # from the PHP manual
    $td = mcrypt_module_open('rijndael-256', '', 'ecb', '');
    $iv = mcrypt_create_iv (mcrypt_enc_get_iv_size($td), MCRYPT_RAND);
    mcrypt_generic_init($td, $key, $iv);

    # use base64 encoding here
    $encrypted_data = base64_encode(mcrypt_generic($td, $string));

    mcrypt_generic_deinit($td);
    mcrypt_module_close($td);

    return $encrypted_data;

}

function b64_decrypt($string,$key) {

     # convert a base-64 encoded string into a Rijndael-256
     # cipher then decrypt using $key

     $td = mcrypt_module_open('rijndael-256', '', 'ecb', '');

     $iv = mcrypt_create_iv (mcrypt_enc_get_iv_size($td), MCRYPT_RAND);
     mcrypt_generic_init($td, $key, $iv);

     $decrypted_data = mdecrypt_generic($td, base64_decode($string));

     mcrypt_generic_deinit($td);
     mcrypt_module_close($td);

     # trim any padding
     return trim($decrypted_data);

}

```

Converting to base64 let's you store the encrypted password as a varchar field.

---

### Post by sdsurfer on 2019-10-01
All of the mcrypt() functions are deprecated as of PHP 7.1, some removed, some deprecated as early as 5.5.0, and reliance on them "highly discouraged." See any of the links on the mcrypt() page.
[URL="https://www.php.net/manual/en/book.mcrypt.php"]https://www.php.net/manual/en/book.mcrypt.php

[/URL]Also, it's bad practice to access superglobals directly, filter them instead.

```
$myuser=trim(filter_input(INPUT_POST, 'username', FILTER_SANITIZE_STRING));
``` *(Or INPUT_GET, REQUEST is not supported)*

At any rate, the code in the original post looks to be nicked from an old sample somewhere, as a learning exercise, all good. My point was to not learn the wrong way, even if you get it to work. :-)

---

### Post by SeijiSensei on 2019-10-02
Thanks. I haven't used any symmetric functions for a few years now. It appears libsodium is the preferred replacement for mcrypt.

I also haven't seen the filter_input() function before. Usually I subject inputs to my own filtering, but I'll take a look at that function.

---

