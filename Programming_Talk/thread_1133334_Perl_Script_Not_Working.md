---
title: "Perl Script Not Working"
date: 2009-04-22
forum: Programming Talk
---

### Post by theb@ssm@n on 2009-04-22
When I enter the basic "Hello World" program in perl:

> #!/usr/bin/perl

print "content-type: text/html \n\n";

print "Hello, Perl!";


I get an error:

> Warning: unknown mime-type for "content-type: text/html \n\n" -- using "application/octet-stream"
Error: no such file "content-type: text/html \n\n"


I tried a google search, but no site has any answers.

Thanks

---

### Post by ghostdog74 on 2009-04-22
you are doing CGI programming right?

---

### Post by theb@ssm@n on 2009-04-22
> **ghostdog74 said:**
> you are doing CGI programming right?
Yeah

---

### Post by Arndt on 2009-04-23
> **theb@ssm@n said:**
> When I enter the basic "Hello World" program in perl:




I get an error:




I tried a google search, but no site has any answers.

Thanks

Where do these error messages appear? (The forum doesn't seem to include quotes in quotes in my reply - you could use the CODE tags instead.)

Does the script work if you run it from the command line?

---

### Post by theb@ssm@n on 2009-04-23
> **Arndt said:**
> Where do these error messages appear? (The forum doesn't seem to include quotes in quotes in my reply - you could use the CODE tags instead.)

Does the script work if you run it from the command line?

no that is where I am running it from

---

### Post by Arndt on 2009-04-24
> **theb@ssm@n said:**
> no that is where I am running it from

Is there a difference if you invoke it (I'll call it "prog.pl") as

```
./prog.pl
```

or as

```
perl prog.pl
```

or as

```
/usr/bin/perl prog.pl
```

?

Or do you invoke it in a different way? Perhaps like this

```
sh perl.pl
```

? In that case, you don't run Perl at all, but the shell, which will call the program 'print'.

---

### Post by AnuChet on 2009-05-06
hey.. im new to perl as well as linux :confused:
 what does it mean when ./prog.cgi does not work but perl prog.cgi works?
also, a simple hello world like :
#!/usr/bin/perl
print "Content-type: text/html\n\n";
print "hello world\n";

works when i view from my browser but when i do this: 

#!/usr/bin/perl
print "Content-type: text/html\n\n";
print "<HTML><HEAD><TITLE>example</TITLE>
</HEAD>";
print "<BODY>";
print "This is the body on normal font";
print "</BODY></HTML>";

and view it on the browser, it says 
**Internal Server Error**

 The server encountered an internal error or misconfiguration and was unable to complete your request.
 Please contact the server administrator,  webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.
 More information about this error may be available in the server error log.
  Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch Server at localhost Port 80

but i can alsways see my first hello world program working! 
:(

---

### Post by stevescripts on 2009-05-06
file permissions ?

---

### Post by AnuChet on 2009-05-06
777

---

### Post by lvleph on 2009-05-06
```
chmod 777 prog.cgi
```
Just incase the 777 comment was not clear.

---

### Post by AnuChet on 2009-05-07
yeah.. thats what i did.... strangely.. that doesnt seem to work

---

