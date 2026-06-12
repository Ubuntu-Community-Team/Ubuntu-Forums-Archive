---
title: "[php] - register/login/logout php script"
date: 2011-03-05
forum: Programming Talk
---

### Post by amr rahmy on 2011-03-05
hi, and thank you in advance for your reply.

if i'm going to make a

- register/login/logout (php script(s)) for a website

if there are some instructions - a lot of sites seem to follow a specific protocol, if there is a specific protocol i should follow, please provide a link.

what am i suppose to take into account (for security and validation) other than:

- registration
unique username
at least x number of characters
must start with a character(letter)
registration successful

password
at least x number of characters
must start with a character(letter)
md5 encrypt in database

re-type pass
validate same string as password

email
not sure how to do the confirmation email link and make it secure (is there a default php script or function)

- login
check blacklist
check number of recent access attempts
check if the username exists
verify password
i may add simple question to anti-bot
login
store number of failed attempts
.....
visual validation in client side (javascript) and php validation in server side
cookies and sessions for remember me and log-out

---

### Post by Some Penguin on 2011-03-05
General considerations -- 

(1) link-layer encryption, against e.g. interception of traffic on wire
(2) user authenticating to server
(3) server authenticating to user
(4) security against attacks outside of session (compromise of your server or client's machine, thus how to handle stored information)


(1) and (3) is pretty commonly handled by https connections w/ a signed certificate for the server, should the user choose to handle it; this can cost money (having a widely trusted authority).  Where done, it's pretty strong.  Client certificates are possible too, but rarely used (can be for a service which is only supposed to be accessed via a dedicated client).  

(2) is most commonly addressed w/ just a password (which can be pretty safely transmitted as-is if over SSL.  However, under an ordinary unencrypted session, passwords should NOT be transmitted in cleartext no matter how ridiculously unguessable the password is.  There are fairly ugly ways to handle this like using JavaScript libraries for some challenge-response (e.g. Server stores hash of password using hash function F.  At login time, server generates long random string (challenge), concatenates with F(password), hashes it again with function G, and sends the challenge string to the user's browser; the JavaScript accepts the password, hashes it the same way the server did (F), concatenates it with the challenge string, hashes /this/ (G), and sends the response.  If the password matches, then both should have done G(challenge + F(password)) and the results should match and the password never needs to be sent to the server.  As long as the challenge string is never reused for the same user, and the attacker is not actively intercepting and manipulating traffic (e.g. able to manipulate traffic and take over the connection -- much trickier than mere eavesdropping for attackers who don't control the network infrastructure), an attacker will not be able to log in as the user.  This is a quite old problem and therefore there are probably numerous libraries which will facilitate this.

Of course, anything secret that's being sent *during the session* is still vulnerable to eavesdropping since we're assuming an unencrypted links for this scenario.  Authentication is only part of security.

It is also not entirely unusual for there to be an additional layer, like the user being able to pick an image when creating his account, and to be presented this image when being asked to log in -- this is for the user to be better able to trust the server, as anybody who creates a fake login site would also need to download and match images to user accounts (and a wrong choice of image may be more noticeable than e.g. lack of proper SSL cert).

An alternate approach is to punt entirely on having your own login system and to rely on something like Facebook Connect's OAuth API or one of the various OpenID providers.

Passwords should be stored using strong one-way hashes, *never* plaintext; e-mail registration is common (and temporary passwords being sent to registered e-mail on 'lost my password' is fairly common, although one may also need to answer 'security questions' answered when creating the account).

Length and complexity requirements are not uncommon; must-change-every-so-often is rarer.  Maximum failed logins per day / per IP address is problematic (leads to possible DOS attacks, especially if you're not tracking whether the failed logins are coming from the user's 'normal' IP range).

Oh, and CAPTCHA and other anti-bot measures are sane things to do when accepting registrations.   Detecting 'excess' registrations or register / post-before-reading-any-thread / running away is useful.  Some forums have gone to the degree where the instructions clearly stipulate you MUST first post in given "Hi, I'm new here" sort of thread or you're going to be assumed to be a bot.

---

### Post by amr rahmy on 2011-03-05
thank you for the reply.

i thought certificates is only used in e-commerce sites with credit transactions

one question,

if the registration happens on the client side using javascript with jquery or any kind of ajax, and is processed with php on the server side with a session, how vulnerable would it be?, and what should be encrypted and with what method.

if i can open a session as long as the web browser page is detected to be open on the client side make a new key on the server side with php, and validate the registration. will the user information be vulnerable at any point?

---

### Post by Some Penguin on 2011-03-05
SSL should really be used more often.  Search for information about 'Firesheep' for an example of why. 

Decide /what/ you send and how it's encrypted, before you worry about how you generate things, because it DOESN'T MATTER how secure a secret's generation is if you're sending it plaintext.  Doesn't matter if it's sent via cookie (HTTP header), a different header, a parameter encoded in the URL, or POST parameter; they're all being transmitted, all are vulnerable to interception and you need to consider minimizing the risk of interception for session hijacking.  Doesn't matter if it had to be a 30+ character phrase change-every-month cannot-repeat-last-dozen mangled-via-heavy-JavaScript code; if it's transmitted in cleartext, it can be copied, and you need to figure out how to prevent retransmission of it being useful.

Incidentally, the bit I described above in challenge-response is insufficient to guard against an attack against the server that retrieved the F(password) values, because it's difficult to ensure that the G() function is secret.  So it'd shield against eavesdropping but NOT database compromise (although it still slightly protects the common user who reuses passwords from having the original passwords tried on other sites as well).    The traditional send-password-and-server-hashes-and-compares handles /that/, but then you're up against the eavesdropping problem.

Link-layer encryption is still greatly preferred.

---

### Post by SeijiSensei on 2011-03-05
I'm working on a site with these issues at the moment myself.  You've covered a lot of essentials.  Let me make a couple of specific suggestions:

> 
must start with a character(letter)


Why?  How about "=IamUser1932"?

> password
md5 encrypt in database

I've been using SHA1 in PHP with the "sha()" function, but [this article]("http://stackoverflow.com/questions/2235158/php-sha1-vs-md5-vs-sha256-which-to-use-for-a-php-login") convinced me I should be using SHA256 or SHA512.  

Remember that MD5 or SHA are one-way hashing functions.  You can't recover a hashed password unless you use a symmetric algorithm like [AES256]("http://snipperize.todayclose.com/snippet/php/Encrypt-and-Decrypt-AES-256--17234/").

> email
not sure how to do the confirmation email link and make it secure (is there a default php script or function)

All mail to users should be plain text and contain nothing more than a link back to your web site that requires they log in.  Use a unique GET URL that takes the registrant to his or her personalized confirmation page.  ("Hello, $Username!  Welcome aboard!")

You'll need to create a password recovery mechanism.  I'm using "[security questions]("http://www.goodsecurityquestions.com/examples.htm")" where the registrant chooses a couple of questions like "Where were you when you had your first kiss?" and writes her answers.  Since these are free-text responses, comparing them later on to the entries made for password retrieval is a bit dicey.  I decided to tokenize the string by making it all lower-case and compressing all the spaces.  We'll see how well that works out.

```
$tokenized_answer=strtolower(str_replace(' ','',trim($answer)))
```

I'm open to additional suggestions!

---

### Post by amr rahmy on 2011-03-06
thank you for your replies,

i'm still processing some of the information,

i thought ssl really slows down performance and should not be considered lightly, and also the certificate approval from the client side is not very appealing. (maybe only used as a last resort)

the problems as i see them now

1- do not store passwords in cookies - (maybe generate some kind of hashed id, don't really need to store cookies for this site)

2- session security risk - (maybe generate some kind of generated hash with every session and a time limit and maybe renew the hash every x minutes)

3- data interception between client and server, maybe hash only important information.(i'm still looking for a compression method to send data, so maybe incorporate both)

---

### Post by amr rahmy on 2011-03-06
i thought starting letter would be more compatible for manipulation with different languages, and storing lowercase letters even if the information will be presented on the screen with some uppercase letter for manipulation and search purposes.

---

### Post by SeijiSensei on 2011-03-07
You should definitely read the [sessions section of the PHP manual]("http://www.php.net/manual/en/book.session.php") carefully before you go too far down this road.

> **amr rahmy said:**
> 1- do not store passwords in cookies - (maybe generate some kind of hashed id, don't really need to store cookies for this site)

2- session security risk - (maybe generate some kind of generated hash with every session and a time limit and maybe renew the hash every x minutes)

Just use a session with a reasonably short lifespan like four hours.  All the session cookie should contain is a session ID, typically a hash.  When someone logs in correctly, add a variable to the session indicating that the person is authenticated.  Something like:

```
$_SESSION['authenticated']=1;
```

Check the value of this flag for every page that requires an authenticated user.

You set the cookie lifetime like this:

```

$session_id=sha1(`ps auxw`);
setcookie('mycookie',$cookie_id, time()+4*86400,'/');

```

The first line runs the OS command 'ps auxw' which displays the instantaneous process list on the server.  This is a decently random amount of text which is used to generate an identification hash.  The setcookie() function creates a cookie called 'mycookie' on the visitor's browser that contains the session ID.  It will expire in four hours (4*86400 seconds).

If the browser refuses cookies, you have to pass the session ID in a GET URL.  See [session.use-trans-sid](http://www.php.net/manual/en/session.configuration.php#ini.session.use-trans-sid) for details.

> 3- data interception between client and server, maybe hash only important information.(i'm still looking for a compression method to send data, so maybe incorporate both)

SSL has invisible performance effects and will eliminate the possibility that users' plain-text credentials might be intercepted along the way.  What you're protecting is the username and password transaction.

---

