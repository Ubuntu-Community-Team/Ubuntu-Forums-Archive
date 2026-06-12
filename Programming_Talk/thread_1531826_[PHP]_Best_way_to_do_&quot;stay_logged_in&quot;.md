---
title: "[PHP] Best way to do &quot;stay logged in&quot;?"
date: 2010-07-15
forum: Programming Talk
---

### Post by ELD on 2010-07-15
Well after searching the net i am a little torn on how to implement a "stay logged in" feature which i have been planning for GamingOnLinux since i added a login system.

I want it to be simple but secure, some sites say confirm the cookie by ip address, some say via browser string...some say both.

Just wandering if anyone knows a good and up to date tutorial for a php stay logged in feature?

---

### Post by Barrucadu on 2010-07-16
I don't know about tutorials, but the way I've typically seen it done is to set a cookie containing an authentication code. This authentication code is then stored in a database along with the corresponding credentials, and possibly (part of) the IP address for extra security.
Then, whenever someone with an authentication cookie visits the site, you simply look up the credentials in the database and all is wonderful. If the owner of the cookie doesn't visit in *x* days (or gets a new cookie set), you remove it from the database to avoid wasting space.

---

### Post by ELD on 2010-07-16
Do you think a reasonable way to do it would be to md5 the session id into the cookie, insert a table row is say table "sessions" which stores their user_id, ip and that md5 session as well and checks they all match...would that be reasonably secure?

---

### Post by slavik on 2010-07-16
simple one:
on login:
- generate a random uuid, this is now the session id
- store the uuid in a cookie (this will get passed back as a header) with now()+X as expire date
- store the uuid with user id in a database

on visit:
- grab the the session id from the browser if there is one, otherwise point to login page (this is for your protected stuff)
- find the uuid in the database and lookup the user id
- if user logs out, remove the session from database and present proper page

Keep in mind that the browser itself will get rid of the cookie and the user's session will be lost. The other way to do it is to store the date of creation in the DB and timeout the session by yourself.

You will need this authentication code on every page that is supposed to care about the user id or is supposed to be protected.

You can also set referrer headers so that when directing someone to login, they will get directed back once doing so (in case the user has a direct address to a logged in page).

---

### Post by ELD on 2010-07-16
Yeah you're basically saying what i did store the session id in the database and match it up. Would it not be better to check I.P as well?

Edits:

Yeah i know checks need to be on every page...there are already checks for the sessions since i stated before i already have a login system, i'm just adding a stay logged in feature.

As for the headers i was thinking about adding something like that with a simple sorta "return to what you where doing" link.

---

### Post by slavik on 2010-07-16
as for adding IP, yes you can do that.

cookies are passed through headers no matter what, if you want to add a "last visited link" in headers/cookie, go ahead and do that.

cookie is a workaround http's statelessness.

---

### Post by lisati on 2010-07-16
> **ELD said:**
> As for the headers i was thinking about adding something like that with a simple sorta "return to what you where doing" link.
Depending on the context, one option might be to make a note of the page that referred the visitor to the login/logout page and use that to help decide where to send the person after a successful login/logout. It's easy enough to find out:
[PHP]$httprefi = getenv ("HTTP_REFERER");[/PHP]

---

### Post by Hellkeepa on 2010-07-21
HELLo!

Just remember that a lot of people are behind proxies, invisible or otherwise. Some even behind a proxy cluster, like AOL customers. This means that several users can have the same IP, as they're using the same proxy, and one user can have several IP-addresses in a single session (jumping between proxies in a cluster).

Referers are also something that both browsers and security software might filter out, and as such is not reliable either.

Also, saving the password and username, even as a hash, is something I'd be very careful about. Do keep in mind that cookies are indeed stored as pure text on the clients computer, and that they are also sent in clear text over the internet (unless you use SSL).
In short, if an attacker can get at the session ID cookie, then the attacker can get the rest of the cookies as well. Without any extra work.

Happy codin'!

---

### Post by ELD on 2010-07-21
I would of course never store the password even secured in a cookie, it would have a person identifyer for them nothing more.

---

### Post by Barrucadu on 2010-07-21
Of course, but a cookie containing something like this would be pretty hard to get the pasword from:
[php]$code = sha1(md5($username . $password . $firstXDigitsOfIP));[/php]
Especially if you use a salt as well.

---

### Post by ELD on 2010-07-23
Really is no need to put a password in a cookie though.

---

