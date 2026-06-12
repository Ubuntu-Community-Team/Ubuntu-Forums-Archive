---
title: "Working Mozilla Persona PHP script - but how to securely access the DB?"
date: 2013-03-18
forum: Programming Talk
---

### Post by Ace..... on 2013-03-18
I have a very nice Persona PHP script pack, that verifies the visitors email address, creating and ending a browser session.

Anybody wishing to examine it, [[COLOR=Blue]the zip pack is here[/COLOR]]("http://www.max-haut-debit.fr/persona_php_login_v1-1/index.php")

The issue I'm addressing now is:
How to securely connect to a MySQL DB, and store the email as the userID, using Persona verification as the password?
[INDENT][I]
Ie. the whole point of Persona is that the password is encrypted within the browser, meaning that the website developer need not store user passwords, and the user needs only one password for all Persona enabled sites.[/I][/INDENT]

The difficulty for me researching this is that all the docs I see refer to a password being placed in the table, and any visitor is asked for the password, and if it matches, then the account records are accessible.

Easy to understand, common sense logic.

However, in this case, the DB must trust the email as presented to it.
ie. here is the email..... it matches a record set...... okay you have access to those records.

I noted: [ [COLOR=Blue]http://dev.mysql.com/doc/refman/5.1/en/user-names.html[/COLOR]]("http://dev.mysql.com/doc/refman/5.1/en/user-names.html")

> "you cannot make a database secure in any way unless all MySQL accounts have passwords. Anyone who specifies a user name for an account that has no password is able to connect successfully to the server."

So how can the Persona verified email be used, without a password, using PHP and MySQLi?

Here is the front end code, that launches the scripts and recieves the email variable $email.

[PHP]<?php 
error_reporting(0); 
include 'my_login_php_config.php'; 
$login_content = $email = NULL; 
if (isset($_POST['assertion'])) { 
    require_once($browserid_php); 
    $result = json_decode(Verifier::verify($_POST['assertion'], $_POST['audience'])); 
     
    if ($result->status === 'okay') { 
        $login_content = "<p>Logged in as: " . $result->email . "&nbsp; <a href='javascript:navigator.id.logout()'>Logout</a></p>"; 
        $email = $result->email; 

//HERE IS THE VERIFIED EMAIL ADDRESS. 
//I NEED TO QUERY THE DB TO SEE IF IT EXISTS 
//IF IT DOES, THEN THAT ACCOUNT IS OPENED 
//IF NOT THEN A NEW ACCOUNT CREATED 


    } else { 
        $login_content = "<p>Error: " . $result->reason . "</p>"; 
    } 
} elseif (!empty($_GET['logout'])) { 
    echo("<script> 
    <!-- 
    location.replace($login_page_php); 
    --> 
    </script>"); 
} else { 
    $login_content = "<button id=\"signin_button\" onclick=\"javascript:navigator.id.request()\" ><img src=\"plain_sign_in_black.png\" alt=\"sign in with Mozilla Persona\">&nbsp; (Test the login system for yourself)</button>"; 
} 
?>[/PHP]

---

### Post by dazman19 on 2013-03-19
Query it.
I take it you are more front end dev than back end.. I want to get better at my F/E. 

Your php script needs the credientials to connect to the database.

Also, be very careful when using mysqli, use mysql_query instead if you are running a single query because mysqli can run multiple SQL statements in 1 go. Therefore making SQL injection a lot easier to achieve by any potential attacker.

[PHP]
<?php 
$username = "webuser";
$password = "W3bu5erP@sswoRd!$";
$sqldatabasehost = "127.0.0.1";
$databasename = "dbtogetdatafrom";

$mysqlConnection = mysql_connect($sqldatabasehost,$username,$password);

$dbemail = mysql_real_escape_string($_POST['email']);

$dbresource = mysql_query("SELECT * FROM `tablename` WHERE `tablecolumn_email` = '$dbemail' "); //you can limit this if you want ... 

while($record = mysql_fetch_assoc($dbresource))
{
//the record data will be in the $record array.
//Code to authorize goes here. Mysql has already done the email comparson for you. 
}

?>
[/PHP]

---

### Post by Ace..... on 2013-03-19
Thanks for the response. :)

It appears to be the case that a fairly complex additional script is required for server authentication.


The current script sets up the browser session with a verified email address.
However, as this is open source development, different people have worked on different elements (in different ways).


I've found 2 server authentication scripts, and will post back after contacting the authors. ;)

---

### Post by Ace..... on 2013-03-19
Following discussion & further research:
There are six primary layers of security, that have been identified by Mozilla.

**Layer 1**

With the verified email created within the browser session, the variable can be placed in a $_SESSION, and the DB can be accessed at level one security.

This carries the risk of a malicious user locally injecting code and subverting the Script.
There is no specific data available, on 'how hard to achieve' this is, or the likelihood of your site being breached.
Mozilla documentation implies that the risk is mitigated, by verifying the assertion remotely (discussed below) - the script we're using does 'verify remotely'. But..... there is still a 'category' risk.
The threat is probably best considered in terms of 'data value', or 'high value target'.

The key is to understand that there ain't no password being stored (that could open up more valuable vaults).
But with such a potential malicious attack, you wouldn't want your bank account details stored at this level.

The script presents layer 1 level of security

**Layer 2**

Explicitly specify the audience parameter and verify it.[INDENT]audience: The hostname and port of your website.[/INDENT]

You must hardcode this value in your backend; do not derive it from any data supplied by the user.

Do not trust the Host header sent by the user's browser.
Do not trust an explicit parameter sent by the user's browser, but generated by your JavaScript using, e.g. document.location.
If you trust the user's browser to tell you the audience, then it becomes possible for a malicious web site to reuse assertions for its web site to log into your web site.

The script provides for this - layer 2.

**Layer 3**

Pass the assertion to the server.[INDENT]"When a user tries to log into a website, their browser generates a data structure called an assertion - essentially a cryptographically signed email address. The browser sends this assertion to the web site, which must verify that the assertion is valid before logging the user in."[/INDENT]

This provides the direct handshake between the verified email & the server.

Like...... sending a letter long distance saying "this is from me", or standing in front of the guy, and saying "this is from me".
The latter.... there is no chance of interception, therefore eliminating the risk outlined in layer 1.

This level is still in beta.
The scripts are available, but simply not recommended for live use as yet.
I need to clarify what exactly this means, and when they can be used.

**Layer 4**

Verify SSL certificates

To verify an assertion, you may issue a POST request to [https://verifier.login.persona.org/verify](https://verifier.login.persona.org/verify). You must ensure that your HTTPS request verifies the certificate sent from the server against a trusted root certificate. If you don't, then an attacker could pose as verifier.login.persona.org and issue false verifications.

Check that the library you are using to make the request verifies certificates correctly, and that you are initializing it with the appropriate root certificate(s).

I've seen the code for this, uploaded a few days ago. 
So this is up for inclusion.

**Layer 5**

Implement CSRF protection

In a CSRF (Cross-Site Request Forgery) login attack, an attacker uses a cross-site request forgery to log the user into a web site using the attacker's credentials.

CSRF login attacks, and potential defenses against them, are documented more fully in Robust Defenses for Cross-Site Request Forgery (PDF). They're not specific to Persona: most login mechanisms are potentially vulnerable to them.

From The variety of protection techniques (in that document), one approach is to create a secret identifier in the server, shared with the browser, and require the browser to supply it when making login requests. For example:

As soon as the user lands on your site, before they try to log in - create a session for them on the server. Store the session ID in a browser cookie.
On the server, generate a random string of at least 10 alphanumeric characters. A randomly generated UUID is a good option. This is the CSRF token. Store it in the session.
Deliver the CSRF token to the browser by either embedding it in JavaScript or HTML as a hidden form variable.
Ensure that the AJAX submission or form POST includes the CSRF token.
On the server side, before accepting an assertion, check that the submitted CSRF token matches the session-stored CSRF token.

Also seen the code for this.

**Layer 6**

Content Security Policy (CSP)

Content Security Policy (CSP) is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross Site Scripting (XSS) and data injection attacks. These attacks are used for everything from data theft to site defacement or distribution of malware.

If you use CSP on your site, you may need to tweak your policy to enable Persona. Depending on your policy, you may need to:

Remove inline javascript: URIs and replace them with code loaded from an additional script file. The file can look up elements based on their ID, and then attach to the element by setting onclick or calling addEventListener().
Allow [https://login.persona.org](https://login.persona.org) as both a script-src and frame-src so that your site can load the remote include.js file and that file can communicate with the fallback Persona implementation.
An example Apache configuration might include:

Header set X-Content-Security-Policy: "default-src 'self'; frame-src 'self' [https://login.persona.org](https://login.persona.org) ; script-src 'self' https://login.persona.org"

For a new build site, this would be automatic.
For a large site, all further scripting would be to the new policy, and then roll through the older files.
********

All included, this should be a very secure sytem, with the benefit that this can be 'out of the box', allowing for differing DB structures.

I'll sort out the files & links tomorrow, to allow examination, and to determine how they might be implemented.

Much of the above was gleaned from [https://developer.mozilla.org/en-US/docs/Persona](https://developer.mozilla.org/en-US/docs/Persona)

:)

---

### Post by Ace..... on 2013-03-20
This is the link to a fairly comprehensive library of security scripts relating to the previous post:

[https://github.com/Falco20019/php-browseridlib/archive/master.zip](https://github.com/Falco20019/php-browseridlib/archive/master.zip)

@dazman19

I'd read somewhere on php.net, that MySQL was being deprecated in favour of MySQLi.

[http://php.net/manual/en/faq.databases.php#faq.databases.mysql.deprecated](http://php.net/manual/en/faq.databases.php#faq.databases.mysql.deprecated)

This was what was said on stack:

[INDENT]The design of the mysql_query function is such that you've got to be careful to escape each and every bit of data you're injecting into it, and if you miss even one your entire application can be destroyed by an automatic SQL vulnerability exploit tool.

Both mysqli and PDO support placeholders which are required to ensure that your queries are safe from SQL injection bugs. Calling mysql_real_escape_string on everything is not only tedious, but error-prone, and that's where the problems arise.[/INDENT]

Perhaps therefore the risk you outline has been dealt with.
Also, PHP.net suggest that all new coding be done in sqli or pdo, so I guess we're gonna have to get used to it.

:)

---

