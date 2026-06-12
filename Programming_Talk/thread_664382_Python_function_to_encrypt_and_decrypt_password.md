---
title: "Python function to encrypt and decrypt password"
date: 2008-01-11
forum: Programming Talk
---

### Post by G|N| on 2008-01-11
Hi,

I want to write a password to a configfile but instead of writing the password as plain text i would like to save it in a human unreadable format.

the security doesn't need to be excellent, but the purpose is that users that open the file can not read the password immediately...

the function also has to be able to decrypt the password again so i can use it in my application.

is there any simple python function for this or a project that uses such a fuction?

thanks

---

### Post by NovaAesa on 2008-01-11
You could use the bzip2 module. The security wont be very high, but the password can definitely be stored in a non-human readable form.

[PHP]>>> import bz2
>>> password = "NoVa52:)"
>>> encrypted_password = bz2.compress(password)
>>> encrypted_password
'BZh91AY&SY\xae\x1d\x86!\x00\x00\x02\x1f\x00\x00 \x12\x10\x00\x01\x01\x00 \x00\xa0\x00"\x06\'\xa8C\x02\x12\xe6\xc0\xf1w$S\x85\t\n\xe1\xd8b\x10'
>>> print bz2.decompress(encrypted_password)
NoVa52:)
>>> 
[/PHP]

---

### Post by G|N| on 2008-01-11
Thank you for your respond and the compression works very good.
but when i write it to a file and after read it and decompress it i get this error:
```

Traceback (most recent call last):
  File "<pyshell#20>", line 1, in <module>
    bz2.decompress(password)
ValueError: couldn't find end of stream

```

This is what i did:
```

>>> f=open("test.txt", "w")
>>> f.write(bz2.compress("mypassword"))
>>> f.close()
>>> w = open("test.txt", "r")
>>> password = w.readline()
>>> w.close()
>>> bz2.decompress(password)
Traceback (most recent call last):
  File "<pyshell#20>", line 1, in <module>
    bz2.decompress(password)
ValueError: couldn't find end of stream
>>> 

```

It works fine if i dont write it to a file

---

### Post by NovaAesa on 2008-01-11
I'll fiddle around with it a bit and see if I can work it out.

---

### Post by NovaAesa on 2008-01-11
Okay, I worked it out. Try this:

[PHP]import bz2
f=open("test.txt", "w")
f.write(bz2.compress("mypassword"))
f.close()
w = open("test.txt", "r")
password = bz2.decompress(w.read())
w.close()
print password[/PHP]

The readline method only reads up to the end of line charactor '\n'. The compressed password had a \n in it, which would have made it read only half of the password and hence raise an error. The read method reads the whole file instead.

EDIT: btw here's a link to the docs for the bz2 module: [http://www.python.org/doc/2.4/lib/module-bz2.html](http://www.python.org/doc/2.4/lib/module-bz2.html)

---

### Post by pmasiar on 2008-01-11
Also, you can store any object as pickle

---

### Post by G|N| on 2008-01-11
The problem is that i also have other fields in the configfile and i acces them using the iniparser module.
so the iniparser module has to be able to get the password and send it to the program where it will be decompressed so i dont think using pickle module is an option.

@NovaAesa: it still doesn't work but currently i am at work and using python for windows...this evening i will try it on linux.

---

### Post by NovaAesa on 2008-01-11
@pmasiar - i think the pickle module stores things as plain text doesn't it? So it might pose a security risk. I think it would store it something along the lines of:
> S'mypassword'
p0
.

@G|N| tell me if it works when you try on Linux. I have never used python on windows so I don't know if there would be any difference.

---

### Post by Wybiral on 2008-01-11
Do you really need to decrypt it, or can you just encrypt the password that the user enters and check that with the previously encrypted password (in the file). This is how almost all password systems work. If you can do this, then I would suggest using [sha]("http://docs.python.org/lib/module-sha.html") or [md5]("http://docs.python.org/lib/module-md5.html"). Both of which are typically used by websites, for instance, to hash passwords for safe storage. They aren't reversible (technically) but you use the same algorithm on the login password so you're comparing the two hashes.

BTW:

NovaAesa, if you change the extension of your "txt" file to "bz2", you can unzip the password with most archiving programs :)

---

### Post by LaRoza on 2008-01-11
I was going to recommmend md5. You can encrypt it (at least, not that I know of) but you can test the hash easily.

---

### Post by G|N| on 2008-01-11
> **Wybiral said:**
> Do you really need to decrypt it, or can you just encrypt the password that the user enters and check that with the previously encrypted password (in the file). This is how almost all password systems work.

the password is used for checking gmail, pop3 and imap accounts so i really  need to decrypt it (i can not send the encrypted password for login)

---

### Post by kevykev on 2008-01-11
A lot of programs simply use base-64 encoding to mask passwords like this. It's low security, only for making them not human readable. In python, you can use the base64 module: [http://docs.python.org/lib/module-base64.html]("http://docs.python.org/lib/module-base64.html") The relevant functions are b64encode(s) and b64decode(s).

If you're writing a gnome app however, a better option might be to use the gnome keyring. If you want to take this approach, this page might help: [http://www.rittau.org/blog/20070726-01]("http://www.rittau.org/blog/20070726-01")

-Kevin

---

### Post by G|N| on 2008-01-11
> **kevykev said:**
> A lot of programs simply use base-64 encoding to mask passwords like this. It's low security, only for making them not human readable. In python, you can use the base64 module: [http://docs.python.org/lib/module-base64.html]("http://docs.python.org/lib/module-base64.html") The relevant functions are b64encode(s) and b64decode(s).

This was exactly what i needed! simple but it works and scares away normal users :)

Thank you all for your replies!

---

### Post by somebodyhelpme on 2008-12-10
if form.accepts(request.vars,session): 
        for table in db.tables: 
            rows=db(db[table].id).select() 
            print rows 
            open(str(os.sep).join([os.getcwd(), 'applications', 
                request.application, 'databases', 
                table+'.csv']),'w').write(str(db(db           
                [table].id).select())) 

I have code above to create a file..
How to create the encrypt and decrytp for the file created?thanks

---

### Post by d3v1150m471c on 2011-11-06
> **NovaAesa said:**
> You could use the bzip2 module. The security wont be very high, but the password can definitely be stored in a non-human readable form.

[PHP]>>> import bz2
>>> password = &quot;NoVa52:)&quot;
>>> encrypted_password = bz2.compress(password)
>>> encrypted_password
'BZh91AY&SY\xae\x1d\x86!\x00\x00\x02\x1f\x00\x00 \x12\x10\x00\x01\x01\x00 \x00\xa0\x00&quot;\x06\'\xa8C\x02\x12\xe6\xc0\xf1w$S\x85\t\n\xe1\xd8b\x10'
>>> print bz2.decompress(encrypted_password)
NoVa52:)
>>> 
[/PHP]

 Thus your password will always be bz2.decompress. so much for encryption. Maybe store an sha-512 sum and do a comparison to validate the data.

---

