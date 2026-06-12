---
title: "POST with Python Example?"
date: 2007-12-02
forum: Programming Talk
---

### Post by Majorix on 2007-12-02
Could someone please post a working post example that logs in on a site? It can be any site, I will sign up if I have to. I have tried on myself, but I couldn't figure out. And an example I got doesn't work...

---

### Post by Majorix on 2007-12-02
OK I am trying to login to this form:
[PHP]        <form method="post" action="/login.dt">
        <tr> 
          <td width="160"><img src="/templates/notloggedin/images/topsection/leftknight.jpg" width="160" height="93"></td>

          <td align="center"><img src="/templates/notloggedin/images/topsection/mainheader.jpg" width="431" height="93"></td>
          <td valign="top" align="right" width="160">
            <img src="/templates/notloggedin/images/login/emailhead.gif" width="160" height="12"><br>
            <input type="text" name="email" style="border: 0px; background-color: #576D54; font-size: 8pt; color: #FFCC66; width: 160px; height: 14px"><br>
            <img src="/templates/notloggedin/images/login/passwordhead.gif" width="160" height="12"><br>
            <input type="password" name="password" style="border: 0px; background-color: #576D54; font-size: 8pt; color: #FFCC66; width: 160px; height: 14px"><br>
            <a href="forgotpassword.dt"><img src="/templates/notloggedin/images/login/forgotpass.gif" width="160" height="20" border="0"></a><br>
            <input type="hidden" name="submit" value="TRUE">
            <input type="image" src="/templates/notloggedin/images/login/login.gif" style="border: 0px"><a href="register.dt"><img src="/templates/notloggedin/images/login/joinnow.gif" width="81" height="15" border="0"></a>

          </td>
        </tr>
        </form>[/PHP]
using this code:
[PHP]import urllib, urllib2, cookielib
cj = cookielib.CookieJar()
opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cj))
urllib2.install_opener(opener)
login_data = urllib.urlencode({'email' : "myEMail", 'password' : 'myPass'})
resp = opener.open("UrlOfTheSite/login.dt", login_data)
file_to_write = open("test.html","w")
file_to_write.write(resp.read())
[/PHP]

But it says I don't have cookies enabled. I tried this on another site and it said the same too. Obviously there is a problem with the cookies but I can't see what it is. I got most of the code from the net so I am not sure why they fail.

Any help?

---

### Post by Majorix on 2007-12-03
*bump*

---

### Post by cwaldbieser on 2007-12-03
> **Majorix said:**
> *bump*

Without knowing the site and having a login there to work with, it is hard to tell you what is not working.

These URLs may help:
[http://www.linuxquestions.org/questions/programming-9/automatic-submissions-357799/]("http://www.linuxquestions.org/questions/programming-9/automatic-submissions-357799/")


If the site is one where anybody can create an account, give the URL, and I will see if I can figure out what exactly you need to POST in order to log in.

---

### Post by Majorix on 2007-12-03
The site url is [http://www.darkthrone.com/](http://www.darkthrone.com/) . Thanks for caring.

Meanwhile I am also working. I have managed to use the browser cookies to interact with the site, but that's not producing portable code.

---

### Post by cwaldbieser on 2007-12-03
> **Majorix said:**
> The site url is [http://www.darkthrone.com/](http://www.darkthrone.com/) . Thanks for caring.

Meanwhile I am also working. I have managed to use the browser cookies to interact with the site, but that's not producing portable code.

If you use "curl" at the command line, you can log in like:
```

$ curl -d 'submit=TRUE&email=user%40yahoo.com&password=secret&x=49&y=11' -L 'http://www.darkthrone.com/login.dt'

```
You need to replace "user%40yahoo.com" with the real email address and "secret" with the real password.  Notice that the strings are url encoded (@ == %40).

You could use pycurl to achieve the same thing, but urllib should be up to the task.
```

>>>import urllib
>>>f = urllib.urlopen("http://www.darkthrone.com/login.dt", "submit=TRUE&email=user%40yahoo.com&password=secret&x=49&y=11")
>>> f.geturl()
'http://www.darkthrone.com/members.dt?session=14ed6d471e2a4f220fc9e58bd2a51827'
>>> f2 = urllib.urlopen(f.geturl())
>>> s2 = f2.read()
>>> len(s2)
29335
>>> fout = file("/home/carl/temp/webworx/out2.html", "w")
>>> fout.write(s2)
>>> fout.close()

```

---

### Post by Majorix on 2007-12-04
Thanks a lot for the code, I will try to use as soon as I am back home, now I have to go to school in a few mins.

Thanks again :)

---

### Post by Majorix on 2007-12-04
> **cwaldbieser said:**
> If you use "curl" at the command line, you can log in like:
```

$ curl -d 'submit=TRUE&email=user%40yahoo.com&password=secret&x=49&y=11' -L 'http://www.darkthrone.com/login.dt'

```
You need to replace "user%40yahoo.com" with the real email address and "secret" with the real password.  Notice that the strings are url encoded (@ == %40).

You could use pycurl to achieve the same thing, but urllib should be up to the task.
```

>>>import urllib
>>>f = urllib.urlopen("http://www.darkthrone.com/login.dt", "submit=TRUE&email=user%40yahoo.com&password=secret&x=49&y=11")
>>> f.geturl()
'http://www.darkthrone.com/members.dt?session=14ed6d471e2a4f220fc9e58bd2a51827'
>>> f2 = urllib.urlopen(f.geturl())
>>> s2 = f2.read()
>>> len(s2)
29335
>>> fout = file("/home/carl/temp/webworx/out2.html", "w")
>>> fout.write(s2)
>>> fout.close()

```

Does this code work with cookies? I somehow doubt that. It will fetch a new sessionid everytime it tries to connect to the server, and that would be pretty resource-consuming, especially with a sensitive language like Python...

---

### Post by smartbei on 2007-12-04
Ummm... You appear to misunderstand both the problem and the problem you think is the problem :D.

The real problem is that assuming it fetches a new sessionid everytime it connects to the server, it just means that you will have a hard time browsing the website with the program because it will constantly have to log in (because the session key was not saved).

The supposed problem is that python is a sensitive language, etc. For this task, the limiting factor will not be Python (really the computer's CPU) - it will be your internet connection. Fetching a new sessionid has pretty much no effect on the amount of processing done on an incoming webpage/data stream/etc.. Also, (and perhaps more importantly) Python is by no means a 'sensitive' language, unless you define sensitive as 'anything slower than C'. For nearly all uses, the bottleneck will not be Python. Besides, the library doing the little crunching that there is in your application is curl, which is written in C AFAIK.

Now that we have that clear: Most servers also have the option of recieving the session key through 'get' (though I am not sure how it is supposed to be formatted).

---

### Post by Wybiral on 2007-12-04
> **smartbei said:**
> Besides, the library doing the little crunching that there is in your application is curl, which is written in C AFAIK.

This is indeed something that I don't think people take into consideration enough when discussing interpreted languages. The only reason using Python would cause any noticeable degradation in runtime efficiency is if you were using really tight loops INSIDE Python.

The primary causes for concern for runtime efficiency in Python are probably loops and mathematical operators (primarily because they are abstracted from the machine code operations being performed).

But using compiled libraries (as a large number of Python libraries are) is really no difference than if you had used the library from a C program. You're calling the exact same functions.

---

### Post by Majorix on 2007-12-04
> **smartbei said:**
> Ummm... You appear to misunderstand both the problem and the problem you think is the problem :D.

The real problem is that assuming it fetches a new sessionid everytime it connects to the server, it just means that you will have a hard time browsing the website with the program because it will constantly have to log in (because the session key was not saved).

The supposed problem is that python is a sensitive language, etc. For this task, the limiting factor will not be Python (really the computer's CPU) - it will be your internet connection. Fetching a new sessionid has pretty much no effect on the amount of processing done on an incoming webpage/data stream/etc.. Also, (and perhaps more importantly) Python is by no means a 'sensitive' language, unless you define sensitive as 'anything slower than C'. For nearly all uses, the bottleneck will not be Python. Besides, the library doing the little crunching that there is in your application is curl, which is written in C AFAIK.

Now that we have that clear: Most servers also have the option of recieving the session key through 'get' (though I am not sure how it is supposed to be formatted).

I think you misunderstood me in a way too.

What I am saying is, even though you might have a sessionid, if you don't have a cookie you can't connect to the website. Most (including this) websites need a cookie to interact with the end-user's computer.

---

### Post by smartbei on 2007-12-04
No, I rather think I got it :). Anyway, here is a proof-of-concept that will get you the session key and then you can use it to navigate the site, sending the session key as part of the website request (get).
```

data = {"submit":"True","email":"<YOUR EMAIL>","password":"<YOUR PASSWORD>"}
f = urllib.urlopen("http://www.darkthrone.com/login.dt", urllib.urlencode(data))

s_key = f.geturl().split("session=")[1]

print s_key #session key

```
Say you want to go to the attack page:
```

import urllib

data = {"submit":"True","email":"<YOUR EMAIL>","password":"<YOUR PASSWORD>"}
f = urllib.urlopen("http://www.darkthrone.com/login.dt", urllib.urlencode(data))

s_key = f.geturl().split("session=")[1]

print s_key

data = {"session":s_key, "mode":"attack"}
page = "userlist.dt"
f2 = urllib.urlopen("http://www.darkthrone.com/"+page+"?"+urllib.urlencode(data))

f3 = open("test.txt","w")
f3.write(f2.read())
f3.close()

```
The above code goes there, and saves it to a file.

---

### Post by Majorix on 2007-12-04
OK I will try the script the first job in the morning. Thanks for going there and writing a script that would help me :)

---

### Post by Majorix on 2007-12-06
OK I have tested the code and it seems to work. Thanks a ton, smartbei.

What I have learned: Cookies aren't necessary to interact with the site. But then why is there a whole cookielib to deal with cookies? I don't get it.

---

### Post by smartbei on 2007-12-06
You have your conclusion a bit off :). Session keys are normally stored as cookies, but can be sent using a get request (as part of the request sent to the server). However, a website developer may choose to write other things to cookie. For example, the 'Remember Me' checkbox next to most login forms uses a cookie to store some kind of identification in a (hopefully :D) hashed/encrypted format, and then uses this information to automatically log you in across seperate sessions.

Anyway, glad I could help.

---

### Post by Obzolete on 2013-02-24
Made a little stream ripper in Python, which catches audio stream data from a Shoutcast/Icecast server to file.

[http://flux.serverpit.com/paste/srip.html](http://flux.serverpit.com/paste/srip.html)

---

### Post by sisco311 on 2013-02-24
Old thread closed.


[[img]http://ompldr.org/tYnpyNw[/img]](http://ompldr.org/vYnpyNw)


From the [code of conduct](http://ubuntuforums.org/index.php?page=policy) that you agreed to when you created your account:

> 
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.


---

