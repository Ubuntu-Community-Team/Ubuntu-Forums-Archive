---
title: "Python and mechanize login script need help!"
date: 2012-04-10
forum: Programming Talk
---

### Post by Eremis on 2012-04-10
Hi fellow programmers!

I am trying to write a script to login into my universities "food balance" page using python and the mechanize module...

This is the page I am trying to log into: [http://www.wcu.edu/11407.asp](http://www.wcu.edu/11407.asp)
The website has the following form to login:

```

<FORM method=post action=https://itapp.wcu.edu/BanAuthRedirector/Default.aspx><INPUT value=https://cf.wcu.edu/busafrs/catcard/idsearch.cfm type=hidden name=wcuirs_uri> 
<P><B>WCU ID Number<BR></B><INPUT maxLength=12 size=12 type=password name=id> </P>
<P><B>PIN<BR></B><INPUT maxLength=20 type=password name=PIN> </P>
<P></P>
<P><INPUT value="Request Access" type=submit name=submit> </P></FORM>

```

From this we know that I need to fill in the following fields:
1. name=id
2. name=PIN

With the action: action=https://itapp.wcu.edu/BanAuthRedirector/Default.aspx

This is the script I have written thus far:

```

#!/usr/bin/python2 -W ignore

import mechanize, cookielib
from time import sleep

url   = 'http://www.wcu.edu/11407.asp'
myId  = '11111111111'
myPin = '22222222222'

# Browser
#br = mechanize.Browser()
#br = mechanize.Browser(factory=mechanize.DefaultFactory(i_want_broken_xhtml_support=True))
br = mechanize.Browser(factory=mechanize.RobustFactory()) # Use this because of bad html tags in the html...

# Cookie Jar
cj = cookielib.LWPCookieJar()
br.set_cookiejar(cj)

# Browser options
br.set_handle_equiv(True)
br.set_handle_gzip(True)
br.set_handle_redirect(True)
br.set_handle_referer(True)
br.set_handle_robots(False)

# Follows refresh 0 but not hangs on refresh > 0
br.set_handle_refresh(mechanize._http.HTTPRefreshProcessor(), max_time=1)

# User-Agent (fake agent to google-chrome linux x86_64)
br.addheaders = [('User-agent','Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/535.11 (KHTML, like Gecko) Chrome/17.0.963.56 Safari/535.11'),
                 ('Accept', 'text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8'),
                 ('Accept-Encoding', 'gzip,deflate,sdch'),                  
                 ('Accept-Language', 'en-US,en;q=0.8'),                     
                 ('Accept-Charset', 'ISO-8859-1,utf-8;q=0.7,*;q=0.3')]

# The site we will navigate into
br.open(url)

# Go though all the forms (for debugging only)
for f in br.forms():
    print f


# Select the first (index two) form
br.select_form(nr=2)

# User credentials
br.form['id']  = myId
br.form['PIN'] = myPin

br.form.action = 'https://itapp.wcu.edu/BanAuthRedirector/Default.aspx'

# Login
br.submit()

# Wait 10 seconds
sleep(10)

# Save to a file
f = file('mycatpage.html', 'w')
f.write(br.response().read())
f.close()

```

Now the problem...

For some odd reason the page I get back (in mycatpage.html) is the login page and not the expected page that displays my "cat cash balance" and "number of block meals" left... 

Does anyone have any idea why? Keep in mind that everything is correct with the header files and while the id and pass are not really 111111111 and 222222222, the correct values do work with the website (using a browser...)

Thanks in advance :p

---

### Post by Eremis on 2012-12-01
Bump

---

