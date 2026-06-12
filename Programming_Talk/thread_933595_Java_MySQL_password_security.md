---
title: "Java MySQL password security"
date: 2008-09-29
forum: Programming Talk
---

### Post by kamaji792 on 2008-09-29
I'm writing writing my interface to a MySQL database in Java.

Currently I hard code the MysSQL user names and passwords into the java.  That means the class files on the client systems have the user names and password in them in an easily readable form.

Is there a better way to doing this?

Thanks in advance.

PS - Obviously the user names are restricted to what they need to do but that still includes the ability to delete records.

---

### Post by DrMega on 2008-09-29
I'm not sure if you can do this in MySQL but what we do at work (.Net and MS SQL) is this:

1. In the database we have a staffmember table, with passwords encrypted
2. We have a user role whose only right is to read the staffmember table.
3. In the client side we have the special user details encrypted in the client side code ( a 3rd party dll decrypts it at runtime).
4. When the app starts and presents the login screen, it has already connected using the user role mentioned in 2 above.
5. When the user puts in their login details, the staffmember table is checked (the only thing the special user role allows) and the password entered by the user is encrypted and then verified against the encrypted one in the staffmember table.
6. If everything checks out, then the DB connection is dropped and the client reconnects using the user's proper account details.

---

### Post by kamaji792 on 2008-09-30
Hmm... logging in.

I think I am coming at this from my brief experience of PHP were you put the user name and password in the file.  This is OK in PHP because the file sits on the server and the user has no access to it.

I guess I need to be thinking about logging in and doing some sort of session management.

Thanks for the reply DrMega.

---

### Post by kknd on 2008-09-30
Here we just ask the login and password, and them connect using them when needed. One DB user for each real user.

---

### Post by drubin on 2008-09-30
Ye I have been wondering this for a while.... I have designed interfaces with web/php scripts that allow the user to access what I would like them to but my java projects that require mysql connections have been limited to simple selects.

This must be a comonly asked question to which there are many answers looking forward to reading some of them.

---

### Post by tinny on 2008-09-30
Let me make sure I understand your requirement.

You are wanting to bundle a database username and password with your application?

What type of application is this? Desktop?

And you want to make it hard for someone to reverse engineer the username and password from this application, right?

---

### Post by drubin on 2008-09-30
> **tinny said:**
> And you want to make it hard for someone to reverse engineer the username and password from this application, right?

Is this even worth it? Java code is very easally decompile able.

---

### Post by tinny on 2008-09-30
> **rubinboy said:**
> Is this even worth it? Java code is very easally decompile able.

A greater level of protection can be offered, however its not 100%.

The OP (and anyone interested) should look into [obfuscation]("http://en.wikipedia.org/wiki/Obfuscated_code"), specifically [string encryption]("http://www.zelix.com/klassmaster/featuresStringEncryption.html").

---

### Post by drubin on 2008-09-30
> **tinny said:**
> A greater level of protection can be offered, however its not 100%.

The OP (and anyone interested) should look into [obfuscation]("http://en.wikipedia.org/wiki/Obfuscated_code"), specifically [string encryption]("http://www.zelix.com/klassmaster/featuresStringEncryption.html").

They are still 100% decriptable... because during run time they are decripted to be used in plain text. Any thing as important as a password is still a bad idea to store in plain text.

Also if you are storing the quries/table/column layout  which means even with out the database username/password, sql injection could be a away to go.

---

### Post by tinny on 2008-09-30
> **rubinboy said:**
> They are still 100% decriptable... because during run time they are decripted to be used in plain text. Any thing as important as a password is still a bad idea to store in plain text.

Also if you are storing the quries/table/column layout  which means even with out the database username/password, sql injection could be a away to go.

:confused:

At runtime, so its only plain text in RAM...? (using the String encryption) I know this is far from perfect but it does greatly increase the level of difficulty for reverse engineering.

---

### Post by DrMega on 2008-10-01
Database security is a massive subject on its own. I reckon all we can do here is give a few pointers. The lengths you go to depend really on how secure the data has to be.

---

### Post by kamaji792 on 2008-10-02
Thanks for all the replies, been a bit busy the last few days so not been able to look at everythign that has been posted.

The system I am setting up is a MySQL database running on a local lan.  Users need to be able to update the database (essentially a list of contacts that only changes slowly over time).  Security is not a big issue.  I only really need to stop people doing things by accident.  That said as I was writing my app I realised I was probably approaching it from the wrong point of view  i.e. doing what I have done the past in PHP.

I guess there must be a way of letting the users log-on to the database and run a session (so the user has to remember the password).  That said again I think does the password get sent over the network un-encripted - are there ways of enabling encription?

Thanks again and all help greatfully received :)

---

### Post by DrMega on 2008-10-02
> **kamaji792 said:**
> 
I guess there must be a way of letting the users log-on to the database and run a session (so the user has to remember the password).  That said again I think does the password get sent over the network un-encripted - are there ways of enabling encription?

If you encrypt the password at client side, and stored the passwords as encrypted strings in a user table in the DB, then that gets round the problem of sending unencryped passwords over the lan.

I'm sure there will be many free encryption libraries for Java, but if not you can always use the weakest but simplest form there is, which is to do a bitwise XOR on each character of the password. You can make it more secure by using a key of more than one byte. Here's the basic algorithm/pseudocode:

```

stringPlainText = "This is my password"
stringEncrypted = ""

for each character in stringPlainText
{
  cNewChar = character XOR nSomeByteSizeInteger
  append stringEncrypted with cNewChar
}

```

To decrypt the string afterwards, use exactly the same algorithm.

It would take any programmer about 30 seconds to decrypt that, but it might slow down those that aren't that interested in the challenge of breaking your code.

You can strengthen the system by changing nSomeByteSizeInteger for each character. For example:

```

stringPlainText = "This is my password"
stringKey = "Zebra"
stringEncrypted = ""
nKeyIndex = 0

for each character in stringPlainText
{
  cNewChar = character XOR ascii code of stringKey at character nKeyIndex
  append stringEncrypted with cNewChar
  increment nKeyIndex
  if nKeyIndex is past end of stringKey
  {
    reset nKeyIndex to 0
  }
}

```

Again, the decryption process is exactly the same as the encryption process.

Obviously what you'd do is implement that pseudo code into a function/method taking two params, being the string to encrypt/decrypt and the key.

I hope my pseudo code makes sense, I don't do Java:)

---

### Post by kamaji792 on 2008-12-03
It's obviously been a while since DrMega posted the last reply and I have been busy doing other thing...

...but thanks any-way DrMega - Can't actually find a way of actually thanking you - possibly becasue this is my thread?  Or maybe because my head is full of fluff, some of which seem to be falling out :P

---

### Post by drubin on 2008-12-03
> **kamaji792 said:**
> It's obviously been a while since DrMega posted the last reply and I have been busy doing other thing...

...but thanks any-way DrMega - Can't actually find a way of actually thanking you - possibly becasue this is my thread?  Or maybe because my head is full of fluff, some of which seem to be falling out :P

You can't thank posts older then 60days.

---

