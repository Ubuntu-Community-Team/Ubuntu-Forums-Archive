---
title: "What is the best way to create a PHP login script?"
date: 2008-07-10
forum: Programming Talk
---

### Post by thenetduck on 2008-07-10
Hi I am using PDO's to create a login script and registration script for a small app im created. I was wondering what would be the best way to do this? 

I am not really looking for hard code here, but I would like to be using the correct or a proven method of letting users login that is safe, efficient and secure. as well as letting them register.

Thanks!
The Net duck

---

### Post by Phristen on 2008-07-10
Do you know about sessions?
Basically, you would need to do something like this in your login page:
[php]

$result = $DB->query ("select * from users where login=$login and pass=$pass");
if ($result->num_rows() == 1)
	$_SESSION["login"] = $result->fetch_assoc();
[/php]Once you logout, you can just unset the $_SESSION["login"] array, so you know you logged out.

---

### Post by cycloptivity on 2008-07-11
While that is the simplest way - its insecure in terms of SQL injections and its not quite as simple as unsetting the sessions ( though it does work ish). I am working on a project at [http://svn.the-mesh.org/trac.cgi/browser/trunk/nmt]("http://svn.the-mesh.org/trac.cgi/browser/trunk/nmt") that can show you a login system though its more complicated as we are trying to create a modular login system. The code you would be after however is

```
$hash = sha1($this->DbMakeSafe($_POST['password'].SALT));
				$user = $this->DbMakeSafe($_POST['username']);
				$q = mysqli_query($this->dbc,"SELECT * FROM `users_users` WHERE user='".$user."'") or die('Query Failed<br>'.mysqli_error($this->dbc));
				$r = mysqli_fetch_assoc($q);

```
Taken from [http://svn.the-mesh.org/trac.cgi/browser/trunk/nmt/classes/saauth.class.php?format=txt](http://svn.the-mesh.org/trac.cgi/browser/trunk/nmt/classes/saauth.class.php?format=txt)

- Kahn

---

### Post by jay019 on 2008-07-11
Use mysql_real_escape_string for all user input. If i were to enter username' + 1=1 it would break unless the fields are properly escaped. 

Something like...

[PHP]
$query = sprintf("SELECT * FROM members WHERE id='%s' AND pass=SHA1('%s')", mysql_real_escape_string($memberid), mysql_real_escape_string($pass));

$theSQL = @mysql_query($query);
[/PHP]

Obviously using password salts is better, but the main point is to be sure to sanitize ALL user input.

---

### Post by Phristen on 2008-07-11
>  its insecure in terms of SQL injections Well thanks, but that wasn't the point.
> and its not quite as simple as unsetting the sessions ( though it does work ish).call session_destroy() to be sure.

P.S. And by the way, your html is wrong - it's <br />, not <br>.

---

### Post by cycloptivity on 2008-07-11
yeah my html is pretty dodgy usually its last on the list :P

---

### Post by CptPicard on 2008-07-11
> **Phristen said:**
> P.S. And by the way, your html is wrong - it's <br />, not <br>.

Well, that of course depends on whether it's XHTML or not. In old-fashioned HTML, <br> is legit.

---

### Post by Phristen on 2008-07-11
xhtml is sort of becoming the standard these days, better follow it.

---

### Post by thenetduck on 2008-07-11
Thank you. 
This was all very helpful. I guess I would then have a script at the top of all the pages I want uses to be able to acces that was kind of like an "if" statment it would check to make sure the user is the correct user? 

Once again, thank you for all the help. I am using PDO objects to handle sql injects (for the most part) but need to understand the login logic, then I will be inplementing more secure anti-injection messures. 

Once again thanks,
The Net Duck

---

### Post by Phristen on 2008-07-11
> I guess I would then have a script at the top of all the pages I want uses to be able to acces that was kind of like an "if" statment it would check to make sure the user is the correct user? No, you only need to login once.
$_SESSION array is not local to any page, it will be available in all pages as long as the session is alive.
You need to read some material about session scope variables.

---

### Post by cycloptivity on 2008-07-12
> **Phristen said:**
> No, you only need to login once.
$_SESSION array is not local to any page, it will be available in all pages as long as the session is alive.
You need to read some material about session scope variables.

Yeah essentially all you need to do after going through the login is to check for the $_SESSION['whateveryoucalledit'] which you can do at the top of each page then build an if statement around that.

---

### Post by Mickeysofine1972 on 2008-07-12
I recommend using Code Igniter which makes the handling of this sort of thing very easy and very secure.

It also destroys the $_SESSION and uses its own session handling instead, as well as that, it only stores the PHP session ID in session/cookie and everything else is kept in the database.

If your serious about building secure and well constructed websites/applications I recommend this, its made my working life heaps easier.

Mike

---

### Post by Phristen on 2008-07-12
>  it only stores the PHP session ID in session/cookie and everything else is kept in the databaseWell, to be fair, $_SESSION does the same thing, only it stores its contents in a regular file, not in a database (to which I don't see any big advantage, by the way).

---

### Post by cycloptivity on 2008-07-12
> **Phristen said:**
> Well, to be fair, $_SESSION does the same thing, only it stores its contents in a regular file, not in a database (to which I don't see any big advantage, by the way).

I agree - If your using sessions the only cookie that should be written is the PHP_SESSID. Where it goes on the webserver makes little difference imho

---

