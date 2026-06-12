---
title: "php help..."
date: 2007-09-23
forum: Programming Talk
---

### Post by hockey97 on 2007-09-23
**closed**

---

### Post by LaRoza on 2007-09-23
Look for syntax errors. Missing ;, $ or an unclosed {} may be the cause as it usually is.

---

### Post by hockey97 on 2007-09-23
**closed**

---

### Post by LaRoza on 2007-09-23
The code is difficult to read, and I and I am at a computer I don't normally use. The quotes and single quotes, and the dots, leave a lot of room for error, just check it again, the syntax highlighting will be useful, especially if you put a line break in between strings.

---

### Post by jsmiith on 2007-09-23
around character 177:

ord"]."','"$_POST["e-mail address"]."'
               ^you forgot a dot here

---

### Post by hockey97 on 2007-09-23
I saw my mistake, thanks for the help, lol ya I missed some dot's and also so added some " extra.

and some } were missing like 1 or 2.

but now I corrected them and now error free kinda.

my script is a register script.

I done the mysql stuff correct.

like password wise and data base ect.

well my code first start's off detecting if submit happened,

then it checks if every html input boxes are filled,

and then it also grabs the values of the inputs before the checks.

after that then I connect to mysql and do a if not connect display fail.

after that if it's all good then I check is the user name exist in my database and it will diplay user exist already on the screen if it does.

then if the user name is new then add all the input info into database,
otherswise  you have not input a user name and password

or sign up at  the sign up area.

then after that I make a html letter and send the user w actication link.
that's it

well now you know what my script does one by one,

I not get that error you have not supplied use with  a user name or password

I test it , and I did supply the user name and password to be created.

the } might be the problem I been playing with those around  by the code where it say's you didn't supply use with a user name and password.

when I was playing with the }{ stuff switching them around, I at times got the error to sign up at the sign up area.

So I  will look into it seeing if  I can get it to work.

to me I think my script is failing at the part where it grabs the user input form the html doc.

---

### Post by hockey97 on 2007-09-28
**closed**

---

### Post by mssever on 2007-09-28
Your script is vulnerable to SQL injection attacks. Always validate input. At a minimum, call mysql_real_escape_string() on everything you insert into the DB.

As far as your problem goes, have you dumped the contents of all your variables so you can see what's what? Clearly, some test is failing. You need to find out what the failing values are, then you can know what to fix. I use [php]echo "<pre>".htmlspecialchars(print_r($var_name,true))."</pre>";[/php]to debug PHP. (I save that in a template so I don't have to type it all the time.)

---

### Post by hockey97 on 2007-09-28
**closed**

---

### Post by mssever on 2007-09-29
> **hockey97 said:**
> How to use that, and what does it do??All those functions are documented in the PHP manual. You might want to wrap that in a function of your own for convenience. The point is so that you can see the actual value of any variable or object (or expression) at whatever point that you call that code.

> but do you see any error's ?? what the error I get is that username and password is missing, however when I go to my database mysql, I don't see any data entered into the table.Your code is badly structured and hard to follow (too many blank lines, huge intentation, lines too long to read in the forum's narrow code box), which doesn't motivate me to study it in depth. I didn't see any errors from a quick glance.

> I made another script just made a simple username and password, and also e-mail, and then wanted to see if I made error's, I entered my database  info and stuff and tested that script and it worked, then I log into the database and saw data inserted into the table.You can't debug one script by writing another--unless you replace the buggy one. In all likelihood, a conditional is failing somewhere (returning false when you expect it to be true, or vice versa). It could be that some variable in the conditional has a value that you're not expecting (hence the code I gave you earlier), or it could be that you have a logic error in your conditional. You can test for that by first ensuring that the values are correct, then observing the control flow. Doing something like [php]echo __LINE__;[/php] will prove whether or not PHP reached a given line.

If only there were a decent debugger for PHP...

> i just wanted to know if I made any noob mistakes lol,  I know that something is wrong anywhere before or at where the script that inserts data into my database table,The important thing is learning how to debug. A significant portion of every programmer's time is spent debugging. You can either waste time by scratching your head over some buggy bit of code, or you can arrange for the code to report its state to you--thus making debugging much easier.

---

### Post by hockey97 on 2007-09-30
I  fixed the problem with that, but now another problem.

what does this error mean...

You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''' at line 1

??

---

### Post by mssever on 2007-09-30
It means that something's wrong with your SQL syntax. You didn't say which query produced the error, but I noticed that two of your SQL queries were missing semicolons at the end.

In general, debugging SQL can be harder sometimes than debugging PHP, because MySQL often gives lame error messages. But you can still dump the contents of the actual query to the screen and examine it to see if it's correct. You can also paste the query into phpmyadmin (or the MySQL command line program) and tewak it until it returns no more errors. Then, you'll find out what your bug was.

---

### Post by hockey97 on 2007-09-30
**closed**

---

### Post by mssever on 2007-10-01
> **hockey97 said:**
> I have webmin, if I use the query code would I used it through the terminal. or webmin??

I've never used webmin, so I don't know if it has what you need. Basically, you need some method to more or less directly enter queries and see the results. phpmyadmin is a web-based interface to MySQL that's quite popular and pretty good. If you have it (or if you can install it--it's in the repos), it's a good choice. There are also various GUI front ends to MySQL of varying quality. Then there's the CLI tool, which works well but isn't necessarily convenient. To use it, type ```
mysql --user youruser --password
```

---

### Post by bobbocanfly on 2007-10-01
Or super speedy way to do it (saves some keyboard strokes)

```
mysql -u <user> -p
```

That is probably the best way if you know SQL programming (or whatever you do with SQL). PHPMA = stupidly easy and gives you SQL code when you execute a command so you are learning SQL too.

---

### Post by hockey97 on 2007-10-01
**closed**

---

### Post by mssever on 2007-10-01
> **hockey97 said:**
> the script works, everything get;s to the database.

now do you guy's know if their is any safest method to check each input.
I got 2 input boxes one is for the password and the other is to re-enter the password, i want to do something to check both values, 

like I want to do somthing like if pass!=repass  then say the password dosen't match...
or somthing, and also I want to also stop people from putting php scripts code stuff, to be submitted into my databse.

Be sure to check out [http://www.php.net/manual/en/function.mysql-real-escape-string.php](http://www.php.net/manual/en/function.mysql-real-escape-string.php). In addition, you need to check each value to make sure that it contains only legal values. (You'll have to decide what value are legal, of course.) You need to read up on PHP security, including prevention of SQL injection and XSS attacks (Google these). Basically, the rule is: never trust any user input ($_GET, $_POST, uploaded files, etc.). Always validate.

---

### Post by hockey97 on 2007-10-02
**closed**

---

### Post by LaRoza on 2007-10-02
> **hockey97 said:**
> 
just looking for any tips or suggestion's to help keep hackers away from my database, or website.

You mean "cracker", you'd want a hacker.

For the SQL injection: [http://www.tizag.com/mysqlTutorial/mysql-php-sql-injection.php](http://www.tizag.com/mysqlTutorial/mysql-php-sql-injection.php)

---

### Post by hockey97 on 2007-10-04
right now I notice, that if I have every input box blank, and clicked submit the blanks would be submitted into my database, I had a peice of code where in order for the inputs to be submitted into the database, it first get's checked if the input boxes are blanks and if their are blank boxes it would show a error, fill out the form thing.

is this what your talking about I need the validate my inputs ect...

---

### Post by mssever on 2007-10-05
> **hockey97 said:**
> is this what your talking about I need the validate my inputs ect...

Yes, though depending on your specific case, sometimes blank fields are fine. You don't want to force your users to enter more information than is necessary, else you risk annoying them into leaving. [Jakob Nielson]("http://www.useit.com/") has a great e-mail newsletter that deals with usability issues. You should subscribe.

In addition to checking for blank fields, and being careful to prevent SQL injection, you also need to make sure people can't insert their own Javascript into your site that can steal passwords, cookies, etc. It's called cross site scripting or XSS. Google it for details. The simplest cure is to ban all HTML. For example, you could reject any field that includes the character <. Of course, an outright HTML ban might not work for you, in which case you'll need to devise some other scheme. EDIT: You might also simply run htmlspecialchars() on your input data, which will neutralize any potentially malicious input without rejecting it outright.

---

### Post by hockey97 on 2007-10-12
**closed**

---

### Post by Wybiral on 2007-10-12
Yes, that's how hashing works. If you used salt + md5 to insert the password in the database, then you use salt + md5 to verify the password.

---

### Post by hockey97 on 2007-10-12
[B]
                        Closed[/B]

---

### Post by Wybiral on 2007-10-12
Are you storing the salt in the database? And using the exact same salt when logging in? Other then that, make sure you do them all in the same order. Have you made sure that the data is properly stored in your database? Posting code would help.

---

### Post by hockey97 on 2007-10-12
**Closed**

---

### Post by Wybiral on 2007-10-12
The problem appears to be that you're using two different salts. You need to store the salt with the hash. Also, you should NEVER store the password, only the resulting hash.

When you hash your password, you take that result and store it in your database. You do this because someone who might gain access to your database never gets your users passwords (they just get a bunch of hashes, which is a pain to to obtain the original passwords from). The salt is used to make it even harder for them to obtain the original password, it increases the length (and randomness) of the password.

There's no benefit in generating the salt at login, and this will definitely make it impossible for the password to be correct unless the randomly generated salt just happened to be the same as when the hash was stored (unlikely).

Here's the goal...

Sign up:
1. Generate salt
2. Store salt in database
3. Hash password + salt
4. Store hash

Log in:
1. Grab salt from database for the username
2. Hash login password with the salt
3. Check login hash with database hash

Of course, I'm not a security expert, but this is what I understand from reading various articles on it.

---

### Post by hockey97 on 2007-10-13
**closed**

---

### Post by Wybiral on 2007-10-13
> **hockey97 said:**
> so I have to save the salt in my database??

so I just need to put salt in database becuse what my scripts were doing was making a random  values, which will not allow the true password to be matched.

I got the password hased and save as the password in the database.

you said to use the salt value as the username??
what do you mean by that??

Unless you use a universal salt (the same salt for each password), you need to save each users salt in your database.

Your script wont work in it's current state because you'll never get the same salts since you're generating them on-the-fly (thus the resulting hash will never be the same and the verification will always fail).

You only save the hash, not the password. The entire point of hashing is to not store the actual password in the database, only the resulting hash. Storing the raw password in your database is a major risk to your users.

I meant that you get the salt value stored for that user (not the username itself, but the random salt you generated when registering). Like I said, if you use a different salt for each user, you need to store that salt otherwise you can never reproduce the resulting hash. You pull their salt up when logging in and hash that with the submitted password (from the login page).

For a simple site, you probably wont even need a salt. You may want to get it all up and running before worrying about it, just to make sure the rest of your code is running fine. Then you can add a salt later on to increase the challenge for any potential crackers.

---

### Post by hockey97 on 2007-10-13
Closed

---

### Post by hockey97 on 2007-10-14
**closed**

---

### Post by hockey97 on 2007-10-14
**closed**

---

### Post by CptPicard on 2007-10-14
I am not completely convinced from your explanation that you're doing this the right way...

The idea is that you've got in your user table something like (username, passhash, salt). Salt is unique for each user.

Suppose your hash function is H(x). Now, when you have the user's cleartext password, what you want to put into the passhash field is H(password+salt). (The + could be simple string concatenation).

Now when the user "hockey" logs in by giving given_password, you select the passhash and salt:

```

select passhash, salt from user_table where username='hockey';

```

Then, he's good to go if

H(given_password+salt) == passhash.

---

### Post by Wybiral on 2007-10-14
You need to pull up the salt and hash for the username that's logging in. For instance, if "bob" logs in, you find the database entry where the username is "bob" and grab the salt and hash for bob from the database. Then you use the password that they entered in the login form, hash it with the salt from the database and check that hash with the hash from the database.

Like I said before, you may want to implement this without a salt just to make sure all your code is working, then try adding the salt when it's stable.

---

### Post by hockey97 on 2007-10-14
**closed**

---

### Post by CptPicard on 2007-10-14
Less than a minute of googling finds [this]("http://dev.mysql.com/tech-resources/articles/ddws/index.html").

If you're able to read a book on 3D game engines, you're surely able to read the friendly manual on something as mundane as using php to access a database? :) That's what PHP is mostly used for, and the web is full of tutorials.

---

### Post by Wybiral on 2007-10-14
I suggest you grab some tutorials on MySQL queries and the PHP MySQL functions. This may help: [http://www.tizag.com/mysqlTutorial/mysqlquery.php](http://www.tizag.com/mysqlTutorial/mysqlquery.php)

---

### Post by hockey97 on 2007-10-14
**closed**

---

### Post by #Reistlehr- on 2007-10-14
I've never been so confussed by a question before lol. wow. but here, i think this is what you are trying to do:

Since only one row is going to be affected at ANY intance, you don't need a loop (while).

```

// Runs the query
$Query = mysql_query('select passhash, salt from user_table where username=\'hockey\');
if(mysql_num_rows($Query) != 0)
{
     // If the user exists, then this command
     // will get the row that is affected
     // assign then to the array $Row, with
     // each field set as an array key.
     $Row = mysql_fetch_assoc($Query);

     // Assign a new var, so you can see how it is done
     $PassWithHash = $Row['passhash'];
     if(md5($_GET['Password']) ==  $PassWithHash)
     {
         echo 'HE IS AUTHORIZED!';
     }
}
else
{
     echo 'This user does not exist!';
}

```

I think that should help a little bit. I used a md5 hash instead of your salt, it's quicker. you can change waht you need.

---

### Post by hockey97 on 2007-10-14
Resistless- Thanks yes that's what I wanted to do.

I you made it more clear on how to go abouts with this.

Thanks for all the help guys'  hopefully It will work this time.

THanks :KS:popcorn::lolflag::guitar:

---

### Post by #Reistlehr- on 2007-10-14
Keep us posted!

Good luck.

+1 for PHP

---

### Post by hockey97 on 2007-10-16
**closed**

---

### Post by CptPicard on 2007-10-16
Uh.... I don't know PHP but it seems to me you're querying with plaintext password. ... Why? :confused:

---

### Post by Wybiral on 2007-10-16
> **hockey97 said:**
> can any one see anything wrong with my script???

I right now ran the script and tested it, I get a blank page, then I monkey around with the code getting error's like mysql code is wrong read the mysql manual.

For starters, you should never use two variables with the same name because "password" and "Password" look way too similar. Your variable names should be more descriptive.

Secondly, you're calling login with:
```

login($_POST["username"],$_POST["password"]);

```
Yet you're using:
```

        if(md5($_GET['Password']+$row['salt']) ==  $Password) 

```
To grab the login password? "_GET" and "_POST" aren't interchangeable. Also "+" should be "." because you want to concatenate them.

What are you trying to do? I don't mean for this to sound harsh or anything, but do you fully understand the concept of using a hash? You should not be querying the database for the password (by that I'm referring to "AND password='$password'") because:

A. The password should not be stored in the database.
B. You're asking the database to return "password" even though you already know it, because you're using it to find the database entry in the first place.

Assuming that the contents of "password" in the database is the real password, there is absolutely no point in using md5 anywhere in your code (or a salt for that matter). Also, in this case, the following code will not work because you're checking if a hash is equal to the password:

```

        $Password = $row['password'];
        if(md5($_GET['Password']+$row['salt']) ==  $Password) 

```

Assuming that the contents of "password" in the database is the hash resulting from "md5($password.$salt)" (which it should be) the following logic is happening:

Suppose the use enters the username and password: "bob" and "123"...

You're querying the database for an entry where the contents of "username" is "bob" and the contents of "password" is "123". It shouldn't be "123", it should be the resulting hash from "md5("123".$salt)".

I suggest you get this working without using a hashing function at all (which also means you can get rid of the salt). Then implement it with the hash, but no salt. Then add the salt. But make sure it works at each step, don't try to code it all together.

EDIT:

Also, DON'T mix tabs and spaces!

---

### Post by hockey97 on 2007-10-16
**Closed**

---

### Post by Wybiral on 2007-10-16
> **hockey97 said:**
> 
ok  the code ```
$Password = $row['password.salt'] ;
        if(md5($_POST['Password'].$row['salt']) ==  $Password)
```

the Password var, show's the password hash in the database, the if statement checks the input password bye hashing it and adding salt to it it then check it with the Password in the database plus the salt.

I am not querying a plain text password it is hased, and stored in the database, by the register script.

I have a few questions before I explain, again, what has already been explained.

1. Do you know what the md5 function does?
2. Do you know why hashing algorithms are used?
3. Do you know why salts are used with hashing algorithms?

Once again, I'm trying to be nice and help, but you seemed to ignore a large portion  of what has already been explained to you.

---

### Post by hockey97 on 2007-10-16
**Closed**

---

### Post by CptPicard on 2007-10-16
Further questions... sorry, Wybiral for messing with your pedagoguery ;)

> **hockey97 said:**
> 
1.md5 function does the hashing.


What is hashing? :) What is the benefit of doing something like this?

> 
2.they are used to protect the real password


How?

> 
3.salts are a form of cryptography they encrypt the hash, which md5 is the hash algorithm used to hash the password.


Not really. The salt just adds difficulty to the cleartext password prior to hashing.

> 
I know what I have to do,  first the password in the register page,
has to be hashed and saved in the database, and same with the salt.


Not really. You hash the cleartext password and the salt combined, not the same thing separately for both.

> 
but in the register script I added the hashed password and salt together.


No. You add the cleartext password and the salt together, and then hash.

> 
now in the login script,  I have to grab the hashed password from the database and also the salt, so then I add the hashed password with the salt. Then I grab the user input password, and hashed that password and added the salt from the database, 


No. You add the input password with the salt, then hash, and compare with the hashed value from the database...

You really need to grasp the concept of why this is being done instead of practicing [voodoo programming]("http://en.wikipedia.org/wiki/Voodoo_programming")...

---

### Post by Wybiral on 2007-10-16
> **hockey97 said:**
> yes I do.

1.md5 function does the hashing, and creates the 32 bit hex numbers
2.they are used to protect the real password
3.salts are a form of cryptography they encrypt the hash, which md5 is the hash algorithm used to hash the password. It uses random bits.

I know what I have to do,  first the password in the register page,
has to be hashed and saved in the database, and same with the salt.
but[COLOR="Blue"] in the register script I added the hashed password and salt together[/COLOR].

[COLOR="Red"]now in the login script,  I have to grab the hashed password from the database and also the salt, so then I add the hashed password with the salt[/COLOR]. Then I grab the user input password, and hashed that password and added the salt from the database, 

I then do an IF statement, that if the user's input password hashed plus the salt is that same as the ones in the database then start the sessions with the session variables and the load the profile of that user.

OK, from this post you seem to have a decent idea of what you need (kind of). Unfortunately your code does not convey this message very well. There is one thing wrong with your concept though, I highlighted them in blue and red as a clue.

---

### Post by CptPicard on 2007-10-16
> **Wybiral said:**
> OK, from this post you seem to have a decent idea of what you need (kind of). 

IMO based on that post his idea of what he's doing is pretty much fscked, but let's see if we can enlighten him :)

**Hockey**, a simple exercise. How would you go about implementing just a simple hashed password system, without salting? I'd like to see a few lines of pseudocode just to make sure you've got it :)

---

### Post by hockey97 on 2007-10-16
**Closed**

---

### Post by CptPicard on 2007-10-16
Let's agree on something to make this a bit clearer... the hash value that goes into the database is going to be called $passhash, ok?

> **hockey97 said:**
> 
the red area

what I mean was I just grabbed those values form the database,  not the salt.

It's the latter half of the sentence... give me a really simple pseudocode example of what you mean by this :) (also I have a feeling your sql query is wrong)


> 
the blue, what I am saying is 
```
$salt = md5(rand(1,5000) * rand(1,5000) * rand(1,5000)); 
$password = md5($_POST["password"] . $salt);
```

Yo don't need to hash the salt separately. The whole point is hashing the plaintext password and the salt *combined, together!*. If your point is to just produce random data for the $salt by running something through md5, fine... but you don't need to!

The latter row is okay... what you'd get from the md5 function is the $passhash I mentioned at the top of the post, and that goes into the database. Let's not call the hash of password+salt "password", it's just confusing.

---

### Post by hockey97 on 2007-10-16
**Closed**

---

### Post by hockey97 on 2007-10-18
**Closed**

---

### Post by Wybiral on 2007-10-18
I __think__ it's right. You need to call the resulting hash something other than "password" though, because it's the password hash, not the password, which is really confusing. I know I sound like a teacher, but using proper spelling, capitalization, and punctuation makes it easier for us to read what you write (and thus help you).

If you think it's right, try it. If it doesn't work, let us know what happened.

---

### Post by #Reistlehr- on 2007-10-18
Ok, this is how i would do it personally. In this example i will NOT use salt. It's easier to begin with. This is more secure, and a faster way of doing waht you were attempting, since the password in the mysql database will have an MD5 hash in it, and not plaintext.

```

<?php
// login.php
session_start();
if(isset($_GET["submit"]))
{
	login($_POST['username'],$_POST['password']);
}
function login($username, $password)
{	
	require_once("/var/www/DbConnector.php");
	$db = new DbConnector();
	$db->connect();
	$query = $db->query( 'SELECT username, password FROM members WHERE   username=\''.$username.'\' AND password = \''. md5($password) .'\''');
	if(mysql_num_rows($query) != 0(
        {
        	$_SESSION["password"] = $password;
		$_SESSION["username"] = $username;
		header("Location: Profile.php?id='. $username .');
      		exit;
	}
	else 
	{
		echo "Wrong username or password. Please try again!";
	}
}

?>

```

---

### Post by #Reistlehr- on 2007-10-18
Yeah, check the post above.

---

### Post by hockey97 on 2007-10-19
**Closed**

---

### Post by hockey97 on 2007-10-21
**Closed**

---

### Post by Wybiral on 2007-10-21
> **hockey97 said:**
> here is the error :  Parse error: syntax error, unexpected T_CONSTANT_ENCAPSED_STRING on line 18.

Notice how line 18 doesn't have a closing double-quote?

---

### Post by hockey97 on 2007-10-21
**Closed**

---

### Post by Wybiral on 2007-10-21
> **hockey97 said:**
> isn't line 18 the line that starts with header??

Exactly. There is only one double-quote.

---

### Post by hockey97 on 2007-10-21
**Closed**

---

### Post by #Reistlehr- on 2007-10-21
Yeah my bad. line 18 should read:

```
header('Location: Profile.php?id='. $username);
```

And it's because there was a .' after username which left it open. and not closed. Also forgot to change the beginning double quote to a single. 

I hate double quotes! lol.

---

### Post by hockey97 on 2007-10-21
**Closed**

---

### Post by #Reistlehr- on 2007-10-21
good catch. That's what syntax highlight is good for. Remember the password in the database should NOT be plaintext, but the result of md5(PASSWORD).

EX:

What is should NOT BE : Hockey338
What is should BE : dd8c5d442d5eff2acbcd589524aec232

This is more secure than keeping a plaintext password in the database anyway. If you need to get the md5 of your password, make a blank php doc, or go into your termanl and use echo md5('PUT YOUR PASSWORD HERE'); and then put the retult as your password in the database.

---

### Post by hockey97 on 2007-10-23
**Closed**

---

### Post by #Reistlehr- on 2007-10-23
Glad you got it working..

When i have any $_SESSIONS vars, i always hash the password, but not the username. It makes it easier for me, and it's probably not the best ethic.

---

