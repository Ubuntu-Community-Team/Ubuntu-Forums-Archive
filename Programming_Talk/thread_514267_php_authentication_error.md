---
title: "php authentication error"
date: 2007-07-31
forum: Programming Talk
---

### Post by dhtseany on 2007-07-31
Hi all, php problem here.

I'm trying to add some authentication to my website but I'm not getting very far. As far as I can see the following is pretty much right. It's popping up the box asking for the username/pass but doesn't accept what I know is correct. Does anyone see something wrong here?

The MySql db is dbconnect
i hid my password.
The table that the info is stored in is called user
from there the available fields are:
userId
coname
priphone
FirstName
LastName
Addr
City
State
Zip
userName
userPass

I'm 99% positive that the connection to the database is fine. 

Any help would be greatly appreciated.

Thanks,

Sean


```

<?PHP

function displayLogin() {
header("WWW-Authenticate: Basic realm=\"My Website\"");
header("HTTP/1.0 401 Unauthorized");
echo "<h2>Authentication Failure</h2>";
echo "The username and password provided did not work. Please reload this page and try again.";
exit;
}

$db = mysql_connect('p50mysql13.secureserver.net','dbconnectlcs','password') or die("Couldn't connect to the database.");
mysql_select_db('dbconnectlcs') or die("Couldn't select the database");

if (!isset($PHP_AUTH_USER) || !isset($PHP_AUTH_PW)) {
// If username or password hasn't been set, display the login request.
displayLogin();
} else {
// Escape both the password and username string to prevent users from inserting bogus data.
$PHP_AUTH_USER = addslashes($PHP_AUTH_USER);
$PHP_AUTH_PW = md5($PHP_AUTH_PW);

// Check username and password agains the database.
$result = mysql_query("SELECT count(id) FROM user WHERE password='$PHP_AUTH_PW' AND username='$PHP_AUTH_USER'") or die("Couldn't query the user-database.");
$num = mysql_result($result, 0);

if (!$num) {
// If there were no matching users, show the login
displayLogin();
}
}

// All code/html below will only be displayed to authenticated users.

echo "Congratulations! You're now authenticated.";

?> 

```

---

### Post by brooksbp on 2007-07-31
Please provide information about what's wrong, what happens, what doesn't happen, etc...

Are your passwords md5 encrypted before storing in the database?
Do you really need slashes in usernames?

---

### Post by dhtseany on 2007-07-31
I'm attempting to authenticate users. When the click a link on my website ([http://www.lakecs.net/new](http://www.lakecs.net/new)) the username/password box pops up like it's supposed to. However, it will not accept my un/pass combo which i know is correct. you can try it if you want: 

username:md5 password: testpass

I have no idea what the slashes are for. I got this code off of a beginners website. I not new to internet lanuages, but i'm far from an expert.

When I insert the user into the database, I use the following mysql statement:

```


INSERT INTO user (userName, userPass) VALUES ('md5', MD5('testPass')); 


```

And for the username w/o md5 I used:

```


INSERT INTO users (userName, userPass) VALUES ('testUser', 'testPass'); 


```

thanks for replying.

Sean

---

### Post by smartbei on 2007-07-31
Ok, try this:
```

<?php

function displayLogin() {
header("WWW-Authenticate: Basic realm=\"My Website\"");
header("HTTP/1.0 401 Unauthorized");
echo "<h2>Authentication Failure</h2>";
echo "The username and password provided did not work. Please reload this page and try again.";
echo "<br>login=",$PHP_AUTH_USER,$PHP_AUTH_PW;
exit;
}


if (!isset($PHP_AUTH_USER)) {
// If username or password hasn't been set, display the login request.
displayLogin();
}
echo "You're in!";
?>

```
If it keeps prompting you for authentication, then you know the problem isn't the mysql - its that for some reason $PHP_AUTH_USER isn't being set, which is the problem I think.

Regardless, it is considered better practice to use mysql_real_escape_string() instead of addslashes(). Also, since this is a new website and all, consider using a hash of the sha family along with a salt for your passwords. A salt is a randomly generated string of 8 or so characters that you append to every password - it is meant to guarantee that even if a user chooses the same password in multiple websites, you cannot know this by looking at the hash.

**After a bit of searching, I found the problem - $PHP_AUTH_USER and _PW are old. They should be replaced by $_SERVER['PHP_AUTH_USER'] and $_SERVER['PHP_AUTH_PW'] respectively.**

---

### Post by dhtseany on 2007-07-31
Ok forgive my ignorance but can you explain how to update the code with the newer way of doing stuff?

Also, I tried the code you gave me and the same problem continued to occur.

Thanks for you help

**From what I can see this is the affected chunk of code:**

```

if (!isset($PHP_AUTH_USER) || !isset($PHP_AUTH_PW)) {
// If username or password hasn't been set, display the login request.
displayLogin();
} else {
// Escape both the password and username string to prevent users from inserting bogus data.
$PHP_AUTH_USER = mysql_real_escape_string($PHP_AUTH_USER);
$PHP_AUTH_PW = md5($PHP_AUTH_PW);

// Check username and password agains the database.
$result = mysql_query("SELECT count(id) FROM `user` WHERE password='$PHP_AUTH_PW' AND username='$PHP_AUTH_USER'") or die("Couldn't query the user-database.");


```

---

### Post by Wybiral on 2007-07-31
Use $_SERVER["$PHP_AUTH_USER"] and $_SERVER["$PHP_AUTH_PW"] _not_ "$PHP_AUTH_USER" and "$PHP_AUTH_PW".

---

### Post by smartbei on 2007-07-31
The problems were supposed to occur - I just wanted to make sure they did, to isolate the problem.
Here is what the new code should look like:
```

<?php
if (!isset($_SERVER['PHP_AUTH_USER']) || !isset($_SERVER['PHP_AUTH_PW'])) {
	// If username or password hasn't been set, display the login request.
	displayLogin();
} else {
	// Escape both the password and username string to prevent users from inserting bogus data.
	$auth_user = mysql_real_escape_string($_SERVER['PHP_AUTH_USER']);
	$auth_pw = sha1($_SERVER['PHP_AUTH_PW'] + "j5K#63xL");
	// Check username and password agains the database.
	$result = mysql_query("SELECT count(id) FROM `user` WHERE password='$auth_pw' AND username='$auth_user'") or die("Couldn't query the user-database.");
?>

```
Note that because I changed the password hash function and added a salt, there is no chance that it will work - you will need to update the userPass field to use the new hash and salt.

Lastly, it makes sense to put the database connection code in the 'else', since it is a waste to connect to the database if the user didn't submit anything.

Glad I could help.

---

### Post by dhtseany on 2007-07-31
What is "j5K#63xL" vs. md5?

---

### Post by smartbei on 2007-07-31
That is the salt. (The randomly generated string I talked about earlier). sha1 is the replacement for md5, with the main difference being that md5 has been 'broken', meaning that it is less secure.

---

### Post by dhtseany on 2007-07-31
so does that mean that i would have to update the mysql statment i used to add the initial user with md5 to read something like the following? If this is the case, what exactly would I put in place of md5? If i'm totally off to tell me.

```


INSERT INTO users (userName, userPass) VALUES ('testUser', ________ ('testPass')); 

```

**(Note the big open space where md5 used to be)**

---

### Post by Wybiral on 2007-07-31
> **dhtseany said:**
> so does that mean that i would have to update the mysql statment i used to add the initial user with md5 to read something like the following? If this is the case, what exactly would I put in place of md5? If i'm totally off to tell me.

```


INSERT INTO users (userName, userPass) VALUES ('testUser', ________ ('testPass')); 

```

**(Note the big open space where md5 used to be)**

It's usually better to generate a random salt for each user and save that with the account (in your database).

This makes it much harder for people to reverse look-up the hashes.

---

### Post by smartbei on 2007-07-31
It would be:
```

INSERT INTO users (userName, userPass) VALUES ('testUser',sha1('testPass'+'j5K#63xL'));

```

I am not sure about Wybrial's suggestion (though I am by **no** means an expert), as to get access to the hash the attacker must have access to the database row. Assuming he has this, he can see the salt as well. What am I missing?

---

### Post by Wybiral on 2007-07-31
> **smartbei said:**
> It would be:
```

INSERT INTO users (userName, userPass) VALUES ('testUser',sha1('testPass'+'j5K#63xL'));

```

I am not sure about Wybrial's suggestion (though I am bo **no** means an expert), as to get access to the hash the attacker must have access to the database row. Assuming he has this, he can see the salt as well. What am I missing?

Mostly brute force. If they know the salt that's used universally, it's easier for them to begin brute forcing any account they want (because they can always start with the salt).

They can just apply the typical dictionary/brute force with salt+rand and recompile their hash database. With individual salts it's much more difficult.

But yeah... If they get that far, you're in trouble anyway. But it's kind-of a back up measure.

---

### Post by smartbei on 2007-07-31
Ok, I am having fun, so here is the code that has taken all the previous suggestions into account:
```

<?PHP
function displayLogin(){
	header("WWW-Authenticate: Basic realm=\"My Website\"");
	header("HTTP/1.0 401 Unauthorized");
	echo "<h2>Authentication Failure</h2>";
	echo "The username and password provided did not work. Please reload this page and try again.";
	exit;
}
if (!isset($_SERVER['PHP_AUTH_USER']) || !isset($_SERVER['PHP_AUTH_PW'])) {
	// If username or password hasn't been set, display the login request.
	displayLogin();
} else {
	// Escape both the password and username string to prevent users from inserting bogus data.

	// Check username and password agains the database.
	$db = mysql_connect('p50mysql13.secureserver.net','dbconnectlcs','password') or die("Couldn't connect to the database.");
	mysql_select_db('dbconnectlcs') or die("Couldn't select the database");
	$auth_user = mysql_real_escape_string($_SERVER['PHP_AUTH_USER']);
	$result = mysql_query("SELECT id,userSalt,userPass FROM `users` WHERE userName='$auth_user'") or die("Couldn't query the user-database.");
	if (mysql_num_rows($result) != 1) {
		//Username doesn't match anything from the database.
		displayLogin();
	}else {
		$row=mysql_fetch_assoc($result);
		if (sha1($_SERVER['PHP_AUTH_PW'] . $row['userSalt']) != $row['userPass']) {
			//Password doesn't match
			displayLogin();
		}
	}
}
// All code/html below will only be displayed to authenticated users.
echo "Congratulations! You're now authenticated.";
?>

```

Above code I tested using my local mysql database - so it should be fine.

Note that a new field called userSalt should be created in the table.

---

### Post by dhtseany on 2007-07-31
Ok guys first, thank you for all the help I've gotten. 

My next problem I've encountered is I get the error message for not being able to query the database:

```

Couldn't query the user-database.

```


I know that I've got the connection details right, although I've learned that by now that this is not the problem.

Any ideas? I copied the code that Smartbei put back together and this is where I got.

Thanks

**UPDATE: **
I figured out what was wrong with the query; the selected table was wrong. The next issue is the same as the first, it is still denying access. Any ideas?

---

### Post by dhtseany on 2007-07-31
Here is a picture of what my db looks like:

[[IMG]http://img217.imageshack.us/img217/9805/au1ru1.th.jpg[/IMG]](http://img217.imageshack.us/my.php?image=au1ru1.jpg)[[IMG]http://img215.imageshack.us/img215/1368/au2yw4.th.jpg[/IMG]](http://img215.imageshack.us/my.php?image=au2yw4.jpg)

Note that the sql insert query didn't seem to work correctly because I had to manually insert the Salt thing into the table. Hope this helps.

Sean

---

### Post by smartbei on 2007-07-31
In your table you have a userId field instead of an id field, so the query fails. Change either the php or the table structure and it should be fine.

Good idea with the screenshot - wouldn't have been able to spot it other wise.

---

### Post by dhtseany on 2007-07-31
AHHH!!! I KNOW I'M ONLY AN INCH AWAY!!! Haha:)

Anyways, I changed the id field from userId to simply id.

Are you sure it's not something to do with the way I inserted the user's info into the table? Again, I ask because I manually inserted the salt thing into the table.

Check out the screen shot of my table up top with the other screen shot.

Thanks

---

### Post by smartbei on 2007-07-31
It is okay to manually insert the salt into the table, so long as you use the same salt to calculate the hash for the password.

I am not entirely sure from your last post - so it still doesn't work?

---

### Post by dhtseany on 2007-07-31
More screen shots of what I see:

[[IMG]http://img232.imageshack.us/img232/4711/au3wk0.th.jpg[/IMG]](http://img232.imageshack.us/my.php?image=au3wk0.jpg)[[IMG]http://img217.imageshack.us/img217/3498/au4rz3.th.jpg[/IMG]](http://img217.imageshack.us/my.php?image=au4rz3.jpg)

It just keeps popping the login box back. I'm using "testUser" and "testPass" for the login.

Any suggestions? Maybe I setup the table wrong?

---

### Post by smartbei on 2007-07-31
Ok, I found the problem. For some reason, your hash is wrong according to the screen shot. Do this:
Firstly, resize your password field to be at least 40 characters wide - the sha1 hash takes 40 characters. Meaning, no matter what you do it won't be correct unless you fix this.

After that:
Insert a new user. Type in whatever you want for the username. Move to the userSalt field, and bash the keyboard a bit - the length doesn't matter much. 6-12 characters is fine. Move to the userPass field. type in your password exactly as you want it, then copy over the contents of the userSalt field, exactly as they are, and append it to your password text. In the drop-down menu next to the userPass field select sha1.
Submit.

Now try again with the new user. It should work.

I'm off to sleep - 6:00am here - Will check up on the thread later today.

---

### Post by dhtseany on 2007-08-01
Same thing, check out the screen shot and tell me if I'm doing what you told me to do.

Thanks

[[IMG]http://img513.imageshack.us/img513/5997/picture1jk9.th.jpg[/IMG]](http://img513.imageshack.us/my.php?image=picture1jk9.jpg)

---

### Post by smartbei on 2007-08-01
What you need to do is after writing your wanted password in the userPass text field, append the userSalt to it. So, in the screenshot you just posted, the userPass field should be:
> 
password123123123

Then submit. (With the sha1 hash from the drop-down)

Then it should work.

---

### Post by dhtseany on 2007-08-01
Please forgive me if I seem like an idiot, but I have no idea what you mean by append. Here is what I have:

userpass: function field set to "sha1" / vaule: password
usersalt: function field blank / value: abc1234


After I hit go this is what I get:
userpass: vaule is 5baa61e4c9b93f3f0682250b6cf8331b7ee68fd8
usersalt: abc1234

Could you maybe reexplain what you meant? I'm still pretty new to what all this means :)

Thanks,

Sean

---

### Post by dhtseany on 2007-08-01
**** YEAH I GOT IT!!!!

Ok, if someone else was looking for help on this topic, what he meant by append is literally just copy and paste.

For example, do the following:

Password field:

select the function sha1, then type in your password you want.

Lets select the password "trA3etra".

Next, in the userSalt field we leave function alone. We make up whatever salt we want to use. Lets use "GGhh%^y". So before we hit Go, we copy "GGhh%^y" and leave it in the salt field, then add it to the end of our password. Essentially, our password that we submit will read as follows:

trA3etraGGhh%y

If that still doesn't make sense to anyone, I understand it now and I'll do my best to help as well.

Thank you all so much for your help, especially Smartbei. :)

---

### Post by smartbei on 2007-08-01
Sorry about that - [append definition]("http://www.webopedia.com/TERM/A/append.html"). :p

Glad I could help!

---

### Post by dhtseany on 2007-08-03
Actually I have one more question for this topic:

Obviously I can't have every page on my site require authentication. However, I do want the ability to simply display the username on everypage (including those that do not require authentication). 

Any ideas? I know that it will somehow involve echo $_SERVER['PHP_AUTH_USER']; but I'm not 100% sure how to tie it in correctly. 


Thanks

Sean

---

