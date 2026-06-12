---
title: "PHP Authentication"
date: 2007-08-21
forum: Programming Talk
---

### Post by dhtseany on 2007-08-21
Ok I give up. Here is what I need for my website:

1) Username / Password Verification
2) Ability to carry the session across multiple pages.
3) Uses sha1 for password encryption
4) Stores un/pass info in a mysql db

That's it. I'm sure it's not difficult but every tutorial that I've tried has one way or another failed. With that being said, does anyone have a suggestion where I can find a really good tutorial to do this?

Sorry for being such a pest on this topic :)

Sean

---

### Post by Mirrorball on 2007-08-21
1) Create a login form (username, password fields), form method=post.
2) When the form is submitted to a login script, run query: SELECT * FROM users where username = '%s' (substitute $_POST['username'] for %s, escaping quotes for security).
3) If a user account was found and sha1($_POST['password']) == password from database, login: store user ID in the $_SESSION array. Else display login form + error message again.
4) In pages that are restricted to authenticated users, check if $_SESSION['userid'] was set.

Now if you don't understand anything, ask questions.

---

### Post by dhtseany on 2007-08-22
**1:**
```

<form action="index.php" method="post">
Username:<input type="text" name="username"/><br />
Password:<input type="password" name="userpass"/><br />
<input type="submit" name="submit" value="Submit" />
</form>

```

**2:**
```

$user = $_POST['username'];
$pass = $_POST['userpass'];

mysql_query("SELECT * FROM user WHERE Username = '$user'
         AND userpass = '$pass'")

```

**3:** Okay, I'll admit that I'm a bit lost here.

**4:**
```

session_start();

	  if (isset($_SESSION['userName'])) {
	echo $_SESSION['userName']; echo " | <a href='../secure/logout.php'>logout</a>";}
        else {echo "<a href='../secure/index.php'><img src=\"../img/mslock.gif\" width=\"16\" height=\"16\">Login</a>";}

```

So far does it seem like I'm on the right path?

---

### Post by Mirrorball on 2007-08-23
You are on the right path. First, you should always escape any user input with mysql_real_escape_string or other functions that do the same, otherwise it's very insecure:
```

$user = **mysql_real_escape_string**($_POST['username']);
$pass = **mysql_real_escape_string**($_POST['userpass']);

mysql_query("SELECT * FROM user WHERE Username = '$user'
         AND userpass = '$pass'");

```
Second, you said you'd like to store sha1 hashes instead of raw passwords, so what you have in the user table is not the password from the login form. To find a match, you have to do:
```

$pass = mysql_real_escape_string(**sha1**($_POST['userpass']));

```
Third, you find a match, you have to store something in the session:
```

session_start();
$_SESSION['userName'] = $user;

```
If $_SESSION['userName'] has been set, you know the user is logged in.

---

### Post by dodgem on 2007-08-23
mysql_real_escape_string is something i'd never heard about (i'm very new to programming though so no surprise there!)

But my login system uses a js function onClick of the login button to pass the contents of the user and password fields to a backend page in the query string using postdata.  The backend page then checks the db for a match.  I tried entering ```
'' or ''=''
``` as a password and it wouldn't authenticate me...

code snippets:
```
echo "<table border='0'>
	<tr><td><label>Username</td><td><input type='text' id='user' size='9' /></label></td>
	<td><label>Password</td><td><input type='password' id='pass' size='9' /></label></td>
	<td><button onclick='checkUserPass(\"".$session."\"); '>Change</button></td>
	<td><div id='menu'></div></td></tr>
	</table>";
```

```
function checkUserPass(session) { 

	// sets the query string to pass username and password entered along with session id to contentBE.php and outputs the returned menu to the 'menu' div



	var user=document.getElementById('user').value;

	var pass=document.getElementById('pass').value;

	var query='user='+user+'&pass='+pass+'&session='+session;



	xhr.onreadystatechange = function() { 

		if(xhr.readyState == 4) {

			if(xhr.status == 200) {

				document.getElementById('menu').innerHTML=xhr.responseText;

			} 

			else document.getElementById('menu').innerHTML="Error code " + xhr.status;

		}

	}; 



	callBackPage("backend/content2BE", query);

} 
```

```
$user=$_POST['user'];
$pass=$_POST['pass'];
$session=$_POST['session'];

$sql="select UserLevel from DBUser where DBUsername='".$user."' and DBPassword='".$pass."'";
$result=mysql_query($sql);
if (mysql_num_rows($result)) {
	$row = mysql_fetch_array($result);
	$uselvl = $row['UserLevel'];
}
else $uselvl = 0;

$_SESSION['userlevel'][$session]=$uselvl;

if ($uselvl==0) echo "Please enter a valid user name and password.";
else echo "<table><tr><td>Logged in as <b>" . $user . "</b></td>";
```

Is this not allowing the login hack because the password is being handled by a js function?...

Just curious at the moment since my app is going to be used in a work environment on the local network only, but at some point i'll be creating a customer portal to allow them to see the status of their orders and that's going to need securing properly!

---

### Post by LaRoza on 2007-08-23
You are not using $_POST variable, you are using $_GET.

You might want to clean up the JS, so it is all together and not mixed with the XHTML.

You also have a random ; at the end of the function.

---

### Post by dodgem on 2007-08-23
Sorry, missed a bit of code....  xhr is an xmlHTTPRequest object, and ```
function callBackPage(pagename, query) {

	

	xhr.open("POST", pagename+".php",  true); 

	xhr.setRequestHeader("Content-type", "application/x-www-form-urlencoded");

	xhr.setRequestHeader("Content-length", query.length);

	xhr.setRequestHeader("Connection", "close");

	xhr.send(query); 

}
```

sends the data as postdata, not using GET.

But yes, i do have a very random ; in my script ;)  I didn't think the JS was mixed up with the XHTML - the JS functions are in a seperate file to the php files and referenced in the document head.  Maybe i'm getting the wrong end of the stick here... like i said, i'm new to this - i understand programming in theory, but best practice isn't necessarily one of my strong points...

Thanks for the input though :)

---

### Post by LaRoza on 2007-08-23
```
echo "<table border='0'>
	<tr><td><label>Username</td><td><input type='text' id='user' size='9' /></label></td>
	<td><label>Password</td><td><input type='password' id='pass' size='9' /></label></td>
	<td><button onclick='checkUserPass(\"".$session."\"); '>Change</button></td>
	<td><div id='menu'></div></td></tr>
	</table>";
```

You are mixing the event handler with the markup. Ideally, the JS should be in a single file, with just a:
[html]
<script src="script.js" type="text/ecmascript"></script>
[/html]
in the head.

Also, you can handle the form submission, using a valid form, and using the onsubmit event handler. So, if your form had an id of "form",
[php]
document.getElementById("form").onsubmit = function()
{
    //All form handling code here.
}
[/php]
Have the function return false, to prevent submission.

---

### Post by dodgem on 2007-08-23
Ahh ok thanks!  That makes sense.  None of my code uses event handling from the .js file at the moment, it is all inline with the HTML and calls the function which obviously is in the .js file.

I can see how that's tidier, but damnit, there's a lot of work to do to seperate my code now...  Any new code i will try and write that way, and then go back over my work once the project is basically complete.  (I like to do things the right way even if i'm the only one who'll know - but my app needs to be at least partly usable soon...)

Any comment on why my code doesn't allow abuse of the mysql statement to login without a password though?

Thanks again!

---

### Post by Mirrorball on 2007-08-23
Oh, please, please, drop the Javascript. You are only making it harder for yourself. Don't turn what could have been a very simple login procedure into a monster just because Ajax is neat. Of course, feel free to enlighten me if you think I'm being too harsh/stupid.

---

### Post by leibowitz on 2007-08-23
I've been writing this kind of authentification from the past three weeks for a friend.


I would be glad to give the source to anyone. Just tell me if you are interested in something already done, or if you just want to learn how to do it yourself.

---

### Post by Wybiral on 2007-08-23
For the sake of your clients, it's actually a lot safer for the password to never cross wires. Hash the password on the client end BEFORE submitting it to the server. This makes it more difficult on anyone trying to intercept the message.

This site includes a javascript implementation of the MD5 AND sha1 algorithms: [http://pajhome.org.uk/crypt/md5/auth.html](http://pajhome.org.uk/crypt/md5/auth.html)

---

### Post by oxygen on 2007-08-23
> **Mirrorball said:**
> 
If $_SESSION['userName'] has been set, you know the user is logged in.

Is it possible for a user to spoof / fake this? If I'm using shared hosting is there a security issue?

What is the most secure way of checking and storing whether a user is logged in (after going through  the login process)?

---

### Post by dodgem on 2007-08-24
> **Mirrorball said:**
> Oh, please, please, drop the Javascript. You are only making it harder for yourself. Don't turn what could have been a very simple login procedure into a monster just because Ajax is neat. Of course, feel free to enlighten me if you think I'm being too harsh/stupid.
Admittedly it is more complex than it *needs* to be, but tbh, this was the easiest and simplest bit of code to try and get working using Ajax.  When i started the project the entire thing worked by submitting forms to the page they were on and taking the data and processing it on the server before redisplaying the page.  But some things were too hard to get working in a user friendly way - then a friend explained what Ajax does and i realised that the whole app could be made much slicker and easier to write if i used Ajax - so i ajaxed the login page first of all to get an idea of how to do it.  Actually the whole thing has been one long lesson in php, js, and mysql - i'd never used any of them before i began :P

@ Oxygen - i'm certainly no authority on this, but i don't think it would be possible to set $_SESSION['userName'] artificially, because the session variable is stored on the server.  You'd need to somehow insert php code onto the server which set the session variable and i don't see that being possible.

---

### Post by aks44 on 2007-08-24
> **dodgem said:**
> i ajaxed the login page

As a side note: most security-concious users simply disable JavaScript. Whenever they come across a site that *requires* JavaScript before they can even benefit from the site's contents, they just go away and never come back.

(I am one of those security-concious users, and we are not just a dozen out there)

Never forget about that if you're writing a commercial site... every possible bit of money has to be taken. ;)

---

### Post by Mirrorball on 2007-08-24
What aks44 said. First get the simple login working without Javascript, then add Javascript if you are **sure** it makes your site easier to use. Otherwise don't bother. Javascript is always secondary. A lesson that I learned the hard way: the less code you write, the better. [Read me!]("http://gettingreal.37signals.com/toc.php")

---

### Post by oxygen on 2007-08-25
> **dodgem said:**
> @ Oxygen - i'm certainly no authority on this, but i don't think it would be possible to set $_SESSION['userName'] artificially, because the session variable is stored on the server.  You'd need to somehow insert php code onto the server which set the session variable and i don't see that being possible.

Hi dodgem,

I've heard that on shared hosting it's possible for another user to create or access the session data (if they use the same directory or something). That's what makes me think raise the question.

From the PHP manual:
> 
The session module cannot guarantee that the information you store in a session is only viewed by the user who created the session. You need to take additional measures to actively protect the integrity of the session, depending on the value associated with it. 

Assess the importance of the data carried by your sessions and deploy additional protections -- this usually comes at a price, reduced convenience for the user. For example, if you want to protect users from simple social engineering tactics, you need to enable session.use_only_cookies. In that case, cookies must be enabled unconditionally on the user side, or sessions will not work. 

There are several ways to leak an existing session id to third parties. A leaked session id enables the third party to access all resources which are associated with a specific id. First, URLs carrying session ids. If you link to an external site, the URL including the session id might be stored in the external site's referrer logs. Second, a more active attacker might listen to your network traffic. If it is not encrypted, session ids will flow in plain text over the network. The solution here is to implement SSL on your server and make it mandatory for users. 


---

### Post by Mirrorball on 2007-08-25
You can store session information in a database if that worries you. Create a session table with a session ID field as the primary key and another field to store generic data, maybe a serialized $_SESSION array. Then load  session information from the database at each request.

---

