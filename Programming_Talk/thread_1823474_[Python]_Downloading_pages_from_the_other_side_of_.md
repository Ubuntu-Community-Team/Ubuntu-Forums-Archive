---
title: "[Python] Downloading pages from the other side of a login"
date: 2011-08-12
forum: Programming Talk
---

### Post by blazemore on 2011-08-12
I am required to download data for processing, but there's a login page which needs to be used before the data can be accessed.

At the moment I'm using the following code:
```

http = httplib2.Http()

login_page_url = 'http://www.example.com/admincp/index.php'   
body = {'login_name': 'admin', 'password': 'admin'}
headers = {'login_name': 'admin', 'password': 'admin'}
response, content = http.request(url, 'POST', headers=headers, body=urllib.urlencode(body))
headers = {'Cookie': response['set-cookie'], 'login_name': 'admin', 'password': 'admin'}

url = 'http://www.example.com/admincp/manage-product.php'   
response, content = http.request(url, 'GET', headers=headers)

```

The field for username is called "login_name" and the field for password is called "password".

However, when I print content, it's just the login page again. I'm not sure what isn't working here, but I suspect it's something to do with a cookie. Can anyone help?

---

### Post by gardnan on 2011-08-12
My guess is that the python library you are using does not automatically save session cookies (cookies that have an expiration time of "0" and usually are meant to be local to a single browser session). However, I don't have much experience with python, so it could be a programming error of some kind.

---

### Post by azzamite on 2011-08-12
Why don't you give this a try
[http://docs.python.org/library/cookielib.html](http://docs.python.org/library/cookielib.html)

You only need to enter the page with firefox and enable "remember me", then convert the cookies to the old txt format and use cookielib to read them and urllib2 to retrieve.

I did that some time ago after trying all the solutions I found for logging in using python and that was the only thing that worked.

If I find the code I'll post it.

---

