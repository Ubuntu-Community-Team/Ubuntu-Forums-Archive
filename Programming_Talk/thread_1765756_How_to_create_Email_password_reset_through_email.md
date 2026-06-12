---
title: "How to create Email password reset through email?"
date: 2011-05-23
forum: Programming Talk
---

### Post by scott_tiger on 2011-05-23
I am building an application using PHP which requires a login session.
In the forget password link I would require the password reset link to be sent to user's email.

Do we need to use email gateways?
If yes ,which one ,googling doesn't solve the problem and just give me an idea (NOT CODE) how to generate password reset link for all the users through the email.??

---

### Post by Barrucadu on 2011-05-23
Use the mail function.

---

### Post by SeijiSensei on 2011-05-23
I recommend checking out this site to develop some security questions for use in the password reset function:  [http://www.goodsecurityquestions.com/](http://www.goodsecurityquestions.com/)

I'm using some of the more obscure suggestions like "Where were you when you had your first kiss?".

---

### Post by scott_tiger on 2011-05-24
> **Barrucadu said:**
> Use the mail function.
But I think before using mail function, there should be email gateway ??.
I tried using mail function in PHP ,but it didn't worked? Some PEAR package is required for that or some people suggest link it with gmail ??How??Could u elaborate??

---

### Post by satanselbow on 2011-05-24
google is in your area? try  "swiftmailer" 

Little point reinventing the wheel ;)

---

### Post by scott_tiger on 2011-05-24
> **satanselbow said:**
> google is in your area? try  "swiftmailer" 

Little point reinventing the wheel ;)
I will try  "swiftmailer" .I think it will work..Thanx

---

### Post by satanselbow on 2011-05-24
> **scott_tiger said:**
>  Some PEAR package is required for that or some people suggest link it with gmail ??How??Could u elaborate??

You have until my toast pops up... I'm having a rare generous 5 minutes ;)

Scandalous statement coming up: PEAR sucks... it is an unnecessary layer of (not that) badly written code.

You have a database for your logins (users) right?

flow goes like this:

simple html form asking for the email address of the account you want to rest password for.
generate a hash (ie encrypt) that email address (or other field in your users database that is unique to that user)
. Write the hash to extra field in your dB. send an email to that address with a link including the hash as a query string as below - use you own domain / filenames obviously:

```
http://www.imadumbarsewhoforgetmypassword.com/resetpassword.php?var=HASH
```

User clicks the link in the email to go to your site to confirm password change
your "resetpassword.php" checks for the hash in the dB and (if valid) calls your "change password" script.

You can then tidy up by removing the hash from the table - so it does not get reused. How you do the change password is up to you. You could alternatively generate a temporary random password and sent that in the email and have them then change there pass to something they will remember.

That is a pretty simple, reasonably secure way of doing it - there are others...

google "php password reset script" gave me about 1,450,000 results  (0.21 seconds) which was a lot quicker than typing this reply ;)

---

### Post by scott_tiger on 2011-05-25
thanx ...for ur post....You gave me a clear insight of how to reset the password....Thanxx..

---

