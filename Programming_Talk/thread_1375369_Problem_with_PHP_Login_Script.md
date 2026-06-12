---
title: "Problem with PHP Login Script"
date: 2010-01-07
forum: Programming Talk
---

### Post by Rob@ThePCWiz.info on 2010-01-07
I created a php login script to set a cookie when a user logs in, THE ONLY THING that does not work, is the password check. users are stored in a folder outside of the web root, called "users" and each user has their own file storing data on them (password, real name, access level)
when i change the line:
```
if($chkpass == $password)
```
to
```
if($chkpass === $chkpass)
```
it will work, so it seems that something is lost in translation.
$password DOES come back as the correct password, but for some reason, there is an error matching the password with the password on file, even if they are the same.
The website is at [www.ThePCWiz.info](www.ThePCWiz.info) and I have setup a demo user.
Username: demo
Password: demo
(the username and password is case-sens.)
I have included the code for the login form below.
Please do not suggest that I use mySQL or any other new form of a database, as I am perfectly happy with the method I have created for myself. Thank you in advance and please post any requests that might help you solve this issue.

**Login Form:**
```

if (isset($_COOKIE["user"]))
{
  echo "Welcome " . $_COOKIE["realname"] . "You are logged in as " . $_COOKIE["user"] . " & Your access level is " . $_COOKIE['access'] . ".";
} else {
  echo "
<form action=login.php method=post>Username: <input type=text name=username> Password: <input type=password name=password><input type=submit value=Login></form>
";
}

```

**Login Script**
```

<?php
$username = $_POST['username'];
$password = $_POST['password'];

if (file_exists("/serv/thepcwiz.info/users/$username.usr")) {
//check password on file and see if it matches given password.
$lines = file("/serv/thepcwiz.info/users/$username.usr");
$l_count = count($lines);
for($x = 0; $x< $l_count; $x++)
{
}

$chkpass = $lines[0];
$usrlvl = $lines[1];
$name = $lines[2];

if($_POST['password'] == "$chkpass")
{
setcookie("user", "$username", time()+7200);
setcookie("access", "$usrlvl", time()+7200);
setcookie("realname", "$name", time()+7200);
echo "Login Sucessful";
} else {
echo "Login Failed!";
}
}

header( 'Location: index.php' ) ;

?>

```

---

### Post by junapp on 2010-01-07
> **Rob@ThePCWiz.info said:**
> 
```
if($chkpass === $chkpass)
```it will work
I hope so.

you might want to echo $password and $chkpass (temporarily, or log it or whatever) to see if you are getting what you think. Maybe trim the objects being compared? does $chkpass contain a line feed or carriage return?

You are setting $password = $_POST['password'];

then later comparing
if($_POST['password'] == "$chkpass")

why not use $password?

Its been a long time for me with php but these are my first thoughts. I'm sure an active php user will help you out quickly.

---

### Post by junapp on 2010-01-07
by the way, if $username.usr does not exist, and the user enters no password, what happens?

---

### Post by Rob@ThePCWiz.info on 2010-01-07
I have echoed them, and it came back fine, they were both read as the same, but the script would not match them up. Also if it does not exist you are returned to the homepage w/o being logged in.

---

### Post by Hellkeepa on 2010-01-07
HELLo!

Oh, my... I won't suggest the use of a (R)DBMS or anything like that, but I will recommend that you use an established CMS.
Learning how to write code is all well and good, but *not* setting the learning code into procution. That's just asking for trouble, and to have your site (or even the server itself) targeted by crackers, bots and all kinds of nasty things. The code above contains absolutely no security, and is open to just about any kind of attack there is. (Well, beside SQL-injections, but that is only becaue you're not using SQL.)

Quick run down of the biggest security flaws:
[list][*]Cookies are sent in clear text over the internet, *and* they're stored in clear text on the users HDD, making them very easy to snatch. Storing any kind of login info in cookies, without heavy encryption, is a gift for hackers.
[*]Cookies are easily changed and/or created manually by the client, making any kind of data stored in them completely unreliable.
[*]No validation of the username, or anything else, means that the attacker can send whatever he likes to your script, and it'll accept it without complaint. This means that your system will execute whatever commands that are sent to it.
[*]No escaping of output data, meaning it's trivial to add any kind of HTML, CSS, JS or whatever to the variables that add content to your page. XSS galore, in other words.
[*]Blindly using the "$username" variable, which btw is not validated, as the filepath. Means an attacker can pick and choose from *any* file on your server's file system.
[*]Storing password in clear text is, again, a giftwrap for attackers. Especially since so many people use the same username & password combination on all of the sites they visit. Always salt the password, using a per-user salt, and use a one-way hashing algorythm before saving them.[/list]
Then we have the logical and syntax issues of your code:
[list][*]This bit does nothing but waste CPU cycles, and then I mean *nothing*.
[php]$l_count = count($lines);
for($x = 0; $x< $l_count; $x++)
{
}[/php]
It's like counting your oranges, before you go and fetch that apple you really wanted. Just delete it.
[*]Checking if the file exists, but not if it's readable.
[*]Instead of checking for if-true, check for if !true, and then show the error message right away. Makes it much easier to read your code, and if the code is written correctly it allows you to "exit early".
[*]Using cookies, instead of sessions.
[*]Also, no aborting the script after "header (Relocate)" calls, which allows the PHP script to continue doing its stuff.
[*]Printing out content before trying to send new HTTP headers. Once you've sent content to the browser, the HTTP headers are sent and no new headers will be accepted.
[*]Using two different files, for what is essentially the same action. Better to do something like this instead:
[php]if (isset ($_POST['submit'])) {
    // Form has been submitted, do whatever.
    // After everything is done, send to confirmation page.
    header ("Location: confirmation.php");
    die();
}

// No form submitted, show the form or whatever it's supposed to do.
[/php]
[*]Using one file per user, instead of one file with one row per user. Read up on the CSV format, for storing data in plain text files.
[*]Static paths to the files means you have to change the code if the host, or even the location to your web root, changes. Use relative paths instead.
[*]Wrapping a variable in quotes. That's like writing 0 + 1 + 0 for each number you're going to write. If the variable's content needs to be a string, then it will automatically be cast as such if it isn't already.
[*]And finally, the "change to fix" you posted at the top of your post.
Of course "$checkpass === $checkpass" is going to work, you're checking if the variable is identical to itself. It cannot be anything else. (Maybe unless we're talking about quantum computing, of course.)[/list]
Now, I know why the password check doesn't work, and it has to do with how "file ()" works. "var_dump ($chkpass)" will also tell you why. The best thing you can do, however, is to bury this script and never use it again. Sit down and read about security, salting, hashing, input validation, output escaping, file system access security concerns, and everything else security-related you might come across. Also, read more code by other people, people who've made secure and successful scripts. There's a whole Fort Knox of wisdom and knowledge in them, which'll help you become a better coder.
Though, before you do that: Remove this script from your host, ASAP. Before someone with less honorable intentions, or even a bot, finds it and take advantages of all the exploits available.

Most importantly: Never give up learning and trying stuff out, just do so in a safe enviroment. ;-)

*Edit, added: I see there's been three posts while I was typing this up. **junapp** got one point I missed in my second list, other than that my post stands unchanged.*

Happy codin'!

---

### Post by Rob@ThePCWiz.info on 2010-01-07
I got it working now, the line that once read:
```
if($password == $chkpass)
```
should have been
```
if("$password\n" == "$chkpass")
```
due to the fact that after each piece of data written into the user file reads a new line. Some reason that new line is read by the script, so by putting a "\n" after the password, it recognizes the password given + the new line (\n).

As far as security, I'm not EXTREMELY worried about security, as even an admin user could not change anything on the site itself. I will however be working on script security to fix some flaws mentioned by the poster above.

---

### Post by Rob@ThePCWiz.info on 2010-01-08
Hellkeepa, I thank you for pointing out the security issues with the cookies not being encrypted. So I have taken the liberty of encrypting them, and then an access script decrypts them for use on the site. Your information has been very helpful.
Now I can sit back, watch a movie, and eat some :popcorn: knowing that my login is secured ( I should hope, if you could point out any flaws please let me know. )

---

### Post by Hellkeepa on 2010-01-08
HELLo!

Well. My point wasn't exactly that you should encrypt the login data in the cookies, it was that you shouldn't have used cookies to store the username and password at all. Also, you should have used sessions to keep track of who's logged in, and their username. The password should never be saved.

As for the part about not even the admin being able to change stuff on the site, I'm afraid that's not entirely true. The point of XSS (amongst other techniques) is to insert HTML/JS code into the page, without having to change the page itself. The only thing that's needed, is a variable that gets assigned input from the user, and printed out on the page without any form of validation or escaping. So if I've signed up as the user "<script>alert ('xss')</script>" that piece of code would have been inserted directly into the HTML code, and as such given a JS alert for every time my name was meant to be displayed on the page.
I've seen entire sites redirected to some disturbing porn sites, just because of this. (And the author's insistence that only using client-side validation was secure.)

And then we have the registration form, which allows me to place any PHP code directly onto your site. Granted, I probably can't overwrite existing files, from the registration form itself, but I can just use it to create a page that will let me do so.
Only reason I haven't done so already, is because you were lucky enough that the host haven't set up a really secure environment on that server. So that the PHP-process isn't running under your username. Though, I'm sure some clever attacker knows a way around that too.

This is why input-validation is so important. Even if you *think* any attacker can't do something, it is only because *you* don't know enough to identify the exploits. I think we both can agree that no-one, either of us included, is smarter than the entire world combined. Right? ;-)

[quote="Rule no. 0"]Don't underestimate the dark side.[/quote]
From "Innocent Code", a book I *highly* recommend for any (and all) web developer, and any other developer for that matter.

PS: [php]"$chkpass"[/php] As I said, completely unnecessary and wasteful.
 
Happy codin'!

---

### Post by junapp on 2010-01-08
excellent points hellkeepa.
although I don't think a full cms is in order, all of the other stuff is quite agreeable. 

@rob: one thing to really watch out for is the desire to say, "it works" and move on. It is only showing you the desired results. That is step one, now lock it down and keep someone from taking over your site. Learn as much as you can from posts like hellkeepa's. He is giving you information that can take years to learn on your own reading through books, and reading through documentation. This type of feedback will greatly improve your coding skills if you follow through and understand why. 

Although I said a full blown cms is not in order, all of the points mentioned above are why after years of using php (and other similar products) I've moved to a platform/framework that assists with many of the issues so I can work on the business of the problem I'm trying to solve instead of worrying so much about the infrastructure (django in my case). Perhaps it is all part of the learning cycle.

Posting your code in this forum is a great way to get fast direct feedback so keep it up.

---

### Post by Hellkeepa on 2010-01-08
HELLo!

You do have a point there, **junapp**. Reason I said "CMS" was because I guessed at what the point of this login script would be, but if no actual content-editing is required then a full blown CMS is not needed. If it's just logins, and some access-control, that we're talking about then just replace "CMS" with "user management system" in my post above. ;-)

Also, your third paragraph hints to a very important point. When learning a programming language it is vital to worry about infrastructure and all the other minor stuff, that is the best way to really learn the language. However, later on, when you do know it, using a framework that deals with all that and lets you focus on creating new functionality is a great help. But only after learning the language, as using it before won't learn you anything about the why's. ;-)
That's one of the reasons why I just rolled my own light-weight framework, an exercise I can more than recommend for the advanced learner.

Happy codin'!

---

### Post by Rob@ThePCWiz.info on 2010-01-10
Thank you guys, I have read all of your guys's input, and decided to use form validation, and I have completely recoded my login system, in order to use sessions rather than cookies, the only thing stored in a cookie now is a session ID that is assigned to the user with an int. between 10000000000 & 99999999999 leaving what?... 89,999,999,999 possibile SessionID's to TRY and find the few that MIGHT log you in as a user? I think that the security has been improved ALOT thanks to you posters. Currently working on validation... should be done in a few moments.

---

### Post by Hellkeepa on 2010-01-10
HELLo!

You are welcome, and it's nice to see that you do indeed take our comments to heart. :-)

I was wondering if you might perhaps post the code you have so far? Sounds like you've rolled your own session-id generator, instead of using PHP's own. Generally it a very bad idea to replace existing security features with self-created ones, as those who've made the ones that are implemented into the language are experts in their fields (and often a collaboration between several experts over many years).

Also, remember to re-generate the session ID on a successful login. Otherwise you'll be vulnerable for session fixating.

Happy codin'!

---

### Post by Rob@ThePCWiz.info on 2010-05-14
Cant really grab the code right now because i moved the site to a different server, however I will take the liberty of at least pasting somewhat of what i remember about how the sessions id's are generated in order to prevent user spoofing.
basically what it does is a 3 part session id.

$password = $_POST['password'];
$a = $_POST['username'];
$b = rand("1000000", "9999999"); //or something like that.
$c = md5("$password");

setcookie("SessionID", "$a.$b.$c", $date()+3600, "/", ".domain.com");

and then the cookie can be read and matched up with the info on the db by doing something like the following to break up the cookie, and then just unmd5 hash the password and verify.

$chk_cookie = explode(".", "" . $_COOKIE['SessionID'] . "");
$userName = $chk_cookie['0'];
$sessionNumber = $chk_cookie['1'];
$password = $chk_cookie['2'];

now this is not the script, but based on that information you should probably be able to write a copy of it that is much better than mine, as it has not been maintained in a long time.

---

### Post by soltanis on 2010-05-14
MD5 is a one-way hash algorithm. But SHA1 is even better (MD5 isn't particularly insecure, but it is vulnerable to the "Rainbow Tables" method which can crack weak MD5'd passwords).

---

