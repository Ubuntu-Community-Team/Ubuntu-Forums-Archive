---
title: "logon system C#, asp.net"
date: 2011-10-13
forum: Programming Talk
---

### Post by Drenriza on 2011-10-13
Hi all.

On my ASP.NET site, which is a company site for over intranet, i was wondering to make a logon system. But how do you secure such a thing from attackers? What do you need to be aware of.

I was wondering to make a text file in round 1, where it has username + password.
When a user then wants to logon it checks if the username exists and if the expected password match the one the users inputted. And then encrypt the text file.

But how secure is such a method? What do one need to focus on?

As you've probably guessed, i am no security expert ,)=

Thanks on advance.
Kind regards.

---

### Post by Drenriza on 2011-10-17
No one? :(

---

### Post by ve4cib on 2011-10-17
You are correct that you need usernames and passwords stored somewhere.  A database is probably better than a text file, but that doesn't matter too terribly much.

Instead of storing the passwords though, store the checksum of the passwords.  SHA256 is a good, secure choice.  When the user logs in they send their username and password, the server computes the checksum of the provided password and compares it to the one in the DB.  If they match all is good.

You'll probably want to use a session cookie or similar server-side method to prevent a session from being spoofed or hijacked.  This is not my area of expertise though, so I can't offer much advice beyond those keywords.

Finally, if you use HTTP the username and password will be transmitted unencrypted.  For an intranet application this shouldn't be too bad, but if you're paranoid get an SSL certificate and run the application (or at least the login) over https instead of http.

---

### Post by cgroza on 2011-10-17
> **ve4cib said:**
> 
Instead of storing the passwords though, store the checksum of the passwords.  SHA256 is a good, secure choice.  When the user logs in they send their username and password, the server computes the checksum of the provided password and compares it to the one in the DB.  If they match all is good.

I suggest that he the checksum to be done on the client side together with something that makes the username/password hash valid for that specific login only. This will make it more secure in case someone sniffs the connection.

---

### Post by ve4cib on 2011-10-17
> **cgroza said:**
> I suggest that he the checksum to be done on the client side together with something that makes the username/password hash valid for that specific login only. This will make it more secure in case someone sniffs the connection.


That's one option.  But doing hashing in JS isn't easy, and you would still face the issue that a man in the middle could sniff the connection anyway.  That's why encrypting the whole thing via https is a good idea.

---

### Post by Drenriza on 2011-10-18
Hi guys.

Thanks for the notes, its being very helpful in taking a decision on how to accomplish my goal.
Also creating a checksum of the password instead of storing the password is a good idea. I should have thought of that, since i do exactly this when i setup network equipment, with passwords :p

---

### Post by Dragonbite on 2011-10-18
This is actually great information. Is there any code sampling on how to do this or how to get/set passwords as checksums?

On a sort-of related note, I had a site which the user would pass a username/password to the database, and the database would either enter a session variable with the database role's login (which would likely be in the web.config file normally) if successful, or return a failed response.

Is storing the database login credentials in a session variable less secure than in web.config?

EDIT: 
The idea behind this is that depending on what account people log in with, they could get different database logins associated with their session.  That way if you are a peop, you may get the login "intranet_user" while the level above them may be "intranet_manager" as associated database roles.

Also, the login used to test/check that password can be locked down to running only the one single stored procedure of the database so if somebody "gets" it they are very limited in what they can do, while the session variable login information (which is never passed to the user iirc) resides on the server.

Or is my thinking on this worthless?

---

### Post by ve4cib on 2011-10-18
> **Dragonbite said:**
> This is actually great information. Is there any code sampling on how to do this or how to get/set passwords as checksums?

There are literally thousands (of not millions) of C# code snippets online.  I guarantee you that there are samples of doing this.  Google is your friend.


> On a sort-of related note, I had a site which the user would pass a username/password to the database, and the database would either enter a session variable with the database role's login (which would likely be in the web.config file normally) if successful, or return a failed response.

Is storing the database login credentials in a session variable less secure than in web.config?

The way I've always done it is to have the database credentials stored in Web.config, but have the application's account's access restricted to the tables that are specifically required.  The application itself needs access to its own database containing usernames & passwords (and any application-specific user privileges, like accessing/modifying global data available to all users of the system), as well as any other application-specific data.

If the application needs to provide access to external databases then the "Users" table could include columns for that user's DB password and username.  But those fields would be in addition to the application's database, with credentials in Web.Config.

I have no idea what the trade-off in terms of security is.  This is just how we always did it at my old job.  The application's database is accessed with credentials in Web.Config.


> The idea behind this is that depending on what account people log in with, they could get different database logins associated with their session.  That way if you are a peop, you may get the login "intranet_user" while the level above them may be "intranet_manager" as associated database roles.

Depending on what databases are requires for the application this may or may not be useful.  For an intranet web application users will probably log in using their normal desktop user account.  Assuming a Windows environment (given the use of ASP.NET this seems likely) that's not too hard to check, provided there's a domain server of some kind.  The application would need access to that, and could check what the current logged-in user requesting access is.  This bypasses the need for storing usernames and passwords, since the Windows login security is handling that for you.

For a public web application, or a private one with additional security concerns you would probably want to create application accounts that are stored by the server, and can only be accessed/modified by the application admins and by the application itself (e.g. the user changing their own password is allowed).  Obviously writing to the DB needs to be sanitized, and all accesses should have the requests checked to ensure that the user has appropriate permissions.

Web application security is a pretty big field, but there's lots published on the subject, and lots of examples of what to do (and what not to do).  My best suggestion is to look around on Google and see what you can find.

---

