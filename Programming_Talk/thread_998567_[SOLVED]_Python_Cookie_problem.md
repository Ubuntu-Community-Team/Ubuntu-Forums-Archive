---
title: "[SOLVED] Python Cookie problem"
date: 2008-11-30
forum: Programming Talk
---

### Post by -grubby on 2008-11-30
I'm trying to get cookies to work, and wrote a test script based on several web tutorials I saw. Cookies will not set. They were setting earlier with the same exact method (just setting different values and names, etc). I'm not sure what the problem is

This is the script : 

```
[color=#408080]*#!/usr/bin/env python*[/color]
[color=#008000]**import**[/color] [color=#0000FF]**cgi**[/color][color=#666666],[/color] [color=#0000FF]**os**[/color][color=#666666],[/color] [color=#0000FF]**Cookie**[/color][color=#666666],[/color] [color=#0000FF]**datetime**[/color]

form [color=#666666]=[/color] cgi[color=#666666].[/color]FieldStorage()

cookname [color=#666666]=[/color] [color=#BA2121]"login"[/color]
fieldname [color=#666666]=[/color] [color=#BA2121]"t"[/color]
cookies [color=#666666]=[/color] Cookie[color=#666666].[/color]SimpleCookie(os[color=#666666].[/color]environ[color=#666666].[/color]get([color=#BA2121]"HTTP_COOKIE"[/color],[color=#BA2121]""[/color]))

[color=#008000]**if**[/color] form[color=#666666].[/color]has_key([color=#BA2121]"t"[/color]) :
    [color=#408080]*# Set the cookie*[/color]
    [color=#008000]**if**[/color] form[[color=#BA2121]"t"[/color]][color=#666666].[/color]value [color=#666666]==[/color] [color=#BA2121]"login"[/color] :
        _value [color=#666666]=[/color] [color=#BA2121]"True"[/color]
        cookies[cookname] [color=#666666]=[/color] _value
        expire [color=#666666]=[/color] datetime[color=#666666].[/color]datetime[color=#666666].[/color]now() [color=#666666]+[/color] datetime[color=#666666].[/color]timedelta([color=#666666]730[/color])
        cookies[cookname][[color=#BA2121]"expires"[/color]] [color=#666666]=[/color] expire[color=#666666].[/color]strftime([color=#BA2121]"%a, [/color][color=#BB6688]**%d**[/color][color=#BA2121] %b %Y %H:00:00 GMT"[/color])
        cookies[cookname][[color=#BA2121]"path"[/color]] [color=#666666]=[/color] [color=#BA2121]"/"[/color]
        [color=#008000]**print**[/color] [color=#BA2121]"Content-Type: text/html[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]
        [color=#008000]**print**[/color] [color=#BA2121]"You are logged in, probably. <a href='index.py'>Go check</a>"[/color]
    [color=#408080]*# Unset the cookie (set to False)*[/color]
    [color=#008000]**elif**[/color] form[[color=#BA2121]"t"[/color]][color=#666666].[/color]value [color=#666666]==[/color] [color=#BA2121]"logout"[/color] :
        [color=#008000]**print**[/color] [color=#BA2121]"Content-Type: text/html[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]
        [color=#008000]**if**[/color] cookies[color=#666666].[/color]has_key(cookname) :
            cookies[cookname] [color=#666666]=[/color] [color=#BA2121]"False"[/color]
            [color=#008000]**print**[/color] [color=#BA2121]"Logged out successfully. <a href='index.py'>Go check</a>"[/color]
        [color=#008000]**else**[/color] :
            cookies[cookname] [color=#666666]=[/color] [color=#BA2121]"False"[/color]
            [color=#008000]**print**[/color] [color=#BA2121]"You can't logout if you aren't logged in! "[/color] [color=#666666]+[/color]\
            [color=#BA2121]"<a href='index.py?t=login'>Login</a>"[/color]
    [color=#008000]**else**[/color] :
        [color=#008000]**print**[/color] [color=#BA2121]"Content-Type: text/html[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]
        [color=#008000]**print**[/color] [color=#BA2121]"<a href='index.py'>Go back to main page</a>"[/color]
[color=#408080]*# If not logging in or out*[/color]
[color=#008000]**else**[/color] :
    [color=#008000]**print**[/color] [color=#BA2121]"Content-Type: text/html[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]
    [color=#408080]*# If the cookie is set to True*[/color]
    [color=#008000]**if**[/color] cookies[color=#666666].[/color]has_key(cookname) :
        [color=#008000]**if**[/color] cookies[cookname][color=#666666].[/color]value [color=#666666]==[/color] [color=#BA2121]"True"[/color] :
            [color=#008000]**print**[/color] [color=#BA2121]"You are logged in. <a href='index.py?t=logout'>Logout</a>"[/color]
        [color=#408080]*# If not True*[/color]
        [color=#008000]**else**[/color] :
            [color=#008000]**print**[/color] [color=#BA2121]"You are not logged in, though a cookie is set. "[/color] [color=#666666]+[/color]\
            [color=#BA2121]"<a href='index.py?t=login'>Login</a>"[/color]
    [color=#408080]*# if the cookie is not set*[/color]
    [color=#008000]**else**[/color] :
        [color=#008000]**print**[/color] [color=#BA2121]"You are not logged in. <a href='index.py?t=login'>Login</a>"[/color]

```

Also, yes, I know the code looks bad (HTML and Python in same file, unnecessary vars, etc) but it's just a testing script

---

### Post by -grubby on 2008-12-01
/me bumps thread

---

### Post by -grubby on 2008-12-02
*sigh*... bump

---

### Post by snova on 2008-12-02
First, the header to set the cookie has to come along with the HTTP header, before all the text, which necessitates some kind of buffering. In addition, the Cookie module doesn't send it for you. ;)

This works:

[PHP]
#!/usr/bin/env python
import cgi, os, Cookie, datetime

form = cgi.FieldStorage()

cookname = "login"
cookies = Cookie.SimpleCookie(os.environ.get("HTTP_COOKIE",""))
out = ""

def Send( s ):
    global out
    out += s + '<br/>'

if 't' in form:
    Send( 'Field: yes' )
else:
    Send( 'Field: no' )

if cookies.has_key( cookname ):
    Send( 'Cookie: yes' )
    Send( 'Value: ' + str( cookies[cookname] ) )
else:
    Send( 'Cookie: no' )

if "t" in form:
    if form["t"].value == "login":
        cookies[cookname] = "True"
    elif form["t"].value == "logout":
        cookies[cookname] = "False"

Send( 'New: ' + str( cookies ) )

print "Content-Type: text/html"
print str( cookies )
print
print out
[/PHP]

---

### Post by -grubby on 2008-12-02
Thanks, that solved it.

---

