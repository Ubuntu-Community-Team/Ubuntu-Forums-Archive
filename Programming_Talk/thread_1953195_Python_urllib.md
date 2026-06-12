---
title: "Python urllib"
date: 2012-04-05
forum: Programming Talk
---

### Post by Eremis on 2012-04-05
Hi everyone,

I am trying to make a script to login into my "check card balance" service for my university using python. Basically it's a web form where we fill-in our PIN and PASS and it shows us how much $$$ is left on our card (for food)...

This is the webpage: [http://www.wcu.edu/11407.asp](http://www.wcu.edu/11407.asp)

This is the form I am filling:
```

<FORM method=post action=https://itapp.wcu.edu/BanAuthRedirector/Default.aspx><INPUT value=https://cf.wcu.edu/busafrs/catcard/idsearch.cfm type=hidden name=wcuirs_uri> 
<P><B>WCU ID Number<BR></B><INPUT maxLength=12 size=12 type=password name=id> </P>
<P><B>PIN<BR></B><INPUT maxLength=20 type=password name=PIN> </P>
<P></P>
<P><INPUT value="Request Access" type=submit name=submit> </P>
</FORM>

```

As you will see the fields i need to fill in are:
```
<input maxlength="12" size="12" type="password" name="id">
<input maxlength="20" type="password" name="PIN">
```

then I need to press the button:
```
<input value="Request Access" type="submit" name="submit">
```

When i do this in my browser, this takes me to another page where it shows my balance and id in simple html...

So I tried to write a python script that would give the the html of that page (so I could parse out the amount of $$$ left and print it to the screen)

This is what I have so far:

```

import urllib                                                                   
import urllib2                                                                  
import sys                                                                      
import cookielib                                                                
import hashlib                                                                  

cookieJar = cookielib.LWPCookieJar()                                            
opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cookieJar))           

opener.addheaders = [('User-agent', "Mozilla/5.0")]                             

username = "xxxxxxxxx"                                                          
password = "xxxxxxxxx"                                                             
action   = "https://itapp.wcu.edu/BanAuthRedirector/Default.aspx"        

print hashlib.md5(hashlib.md5(password).hexdigest()).hexdigest()                                                         
url = "http://www.wcu.edu/11407.asp"                                            
form = {"action" : action,                                                      
        "id" : username,                                                        
        "PIN" : password}                                                       

encodedForm = urllib.urlencode(form)                                            
request = urllib2.Request(url, encodedForm)                                     
page = opener.open(request)                                                     
contents = page.read()                                                          

f = open("mycatpage.txt", "w")                                                  
f.write(contents)                                                               
f.close()

```

Why does't this work:confused:

Thanks for your help

---

### Post by troymius on 2012-04-05
I would be quite afraid to put password in clear text into the script.

---

### Post by Eremis on 2012-04-05
I know I am not concerned about this, yet...
I will fix this later... and have it prompt to a pass or use a key...

Why does not work though?
I get back the same login page...

---

### Post by Eremis on 2012-04-05
Got a diffident version of the script to work, but the page I get gives me a weird error...

Script that works:
```

from urllib import urlopen, urlencode
myId = '<your_id_here>'
myPin = '<your_pin_here>'
data = {
            'id':myId,
            'PIN':myPin,
            'submit':'Request Access',
            'wcuirs_uri':'https://cf.wcu.edu/busafrs/catcard/idsearch.cfm'
        }

url = 'https://itapp.wcu.edu/BanAuthRedirector/Default.aspx'
response = urlopen(url, urlencode(data))
open("mycatpage.txt",'w').write(response.read())

```

Now I get a weird error page, which says:

```

Server Error in '/BanAuthRedirector' Application.
Description: An application error occurred on the server. The current custom error settings for this application prevent the details of the application error from being viewed remotely (for security reasons). It could, however, be viewed by browsers running on the local server machine. 

Details: To enable the details of this specific error message to be viewable on remote machines, please create a <customErrors> tag within a "web.config" configuration file located in the root directory of the current web application. This <customErrors> tag should then have its "mode" attribute set to "Off".



<!-- Web.Config Configuration File -->

<configuration>
    <system.web>
        <customErrors mode="Off"/>
    </system.web>
</configuration>

Notes: The current error page you are seeing can be replaced by a custom error page by modifying the "defaultRedirect" attribute of the application's <customErrors> configuration tag to point to a custom error page URL.


<!-- Web.Config Configuration File -->

<configuration>
    <system.web>
        <customErrors mode="RemoteOnly" defaultRedirect="mycustompage.htm"/>
    </system.web>
</configuration>

```

---

### Post by troymius on 2012-04-05
What if you load a page on the same website but an unsecured page (no https)? Will you still get the same error?  

See I am not expert in this. But for example, in a script I wrote last year (I used the "mechanize" Python module) I had a line that made the web server think that my script is actually Firefox:

   br.addheaders = [('User-agent', 'Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008071615 Fedora/3.0.1-1.fc9 Firefox/3.0.1')]

I would imagine that https would be careful not to serve scripts but only browsers (even though as you can see it can be fooled). But again it is just one of a million possible things and what do I know. Sorry.

---

### Post by Eremis on 2012-04-05
hum.... let me try....

---

### Post by Eremis on 2012-04-05
When I try http, I get:

The page must be viewed over a secure channel

The page you are trying to access is secured with Secure Sockets Layer (SSL).

How would I make it think I am using firefox like you did?

---

### Post by Eremis on 2012-04-05
This is another version I wrote but this gives the errors:

```

Traceback (most recent call last):
  File "checkbalance3.py", line 21, in <module>
    open("mycatpage.html", 'w').write(page = opener.open(request))
  File "/usr/lib/python2.7/urllib2.py", line 400, in open
    response = meth(req, response)
  File "/usr/lib/python2.7/urllib2.py", line 513, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.7/urllib2.py", line 438, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.7/urllib2.py", line 372, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 521, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 500: Internal Server Error

```

The code is:
```

from urllib import urlopen, urlencode                                           
import urllib2                                                                  
                                                                                
opener = urllib2.build_opener()                                                 
opener.addheaders = [('User-agent','Mozilla/5.0 (X11; Linux x86_64; rv:2.0.1) Gecko/20110506 Firefox/4.0.1')]
                                                                                
myId = 'xxxxxxxx'                                                              
myPin = 'xxxxxxxxx'                                                                
                                                                                
data = {                                                                        
            'id':myId,                                                          
            'PIN':myPin,                                                        
            'submit':'Request Access',                                          
            'wcuirs_uri':'https://cf.wcu.edu/busafrs/catcard/idsearch.cfm'      
        }                                                                       
                                                                                
                                                                                
url = 'https://itapp.wcu.edu/BanAuthRedirector/Default.aspx'                    
                                                                                
request = urllib2.Request(url, urlencode(data))                                 
open("mycatpage.html", 'w').write(page = opener.open(request))  

```

---

### Post by troymius on 2012-04-05
> **Eremis said:**
> When I try http, I get:

The page must be viewed over a secure channel

The page you are trying to access is secured with Secure Sockets Layer (SSL).

How would I make it think I am using firefox like you did?

Well thats in a way good news: the https version apparently entered the ID and password correctly... 

Again, I used "mechanize", you are using "urllib", therefore I don't know how you can specify a browser etc. Its been so long ago I cannot remember why I used mechanize and not anything else. But it took me a while to make it work for sure :-)

---

