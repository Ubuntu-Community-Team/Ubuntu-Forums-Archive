---
title: "[PYTHON]What do I infer from % sign?"
date: 2011-05-17
forum: Programming Talk
---

### Post by Ashish Gaurav on 2011-05-17
Hi. I am a newbie to Python and CGI. As a newcomer I admire its simplicity. But as common, I am having a problem. What do we mean by % sign? I know its MODULUS but in some places it cannot be modulus!

See this:
----------------------------------------------------------------------------------------------------
#!/usr/bin/python  # Import modules for CGI handling  import cgi, cgitb   # Create instance of FieldStorage  form = cgi.FieldStorage()   # Get data from fields first_name = form.getvalue('first_name') last_name  = form.getvalue('last_name')  print "Content-type:text/html\r\n\r\n" print "<html>" print "<head>" print "<title>Hello - Second CGI Program</title>" print "</head>" print "<body>" print "<h2>Hello [SIZE=3]%s %s[/SIZE]</h2>" % (first_name, last_name) print "</body>" print "</html>"
------------------------------------------------------------------------
[FONT=Arial]Here, why was %s %s written after Hello, and why, was first_name,last_name written afterward with 5 sign.
Can't seem to understand!

Actually this was in the CGI script.
Please help!(No office work, just my zeal!)
Thanks(I hope I have explained my query well)[/FONT]
:)

---

