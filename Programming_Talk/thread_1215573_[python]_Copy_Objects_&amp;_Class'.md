---
title: "[python] Copy Objects &amp; Class'"
date: 2009-07-17
forum: Programming Talk
---

### Post by Pyro.699 on 2009-07-17
Hey,

I don't know how many of you know about the Client Form Module, it basically takes a ulrlib2.Request variable and extracts all the forms out of it so you can submit post data easier.

Something that I'm having problems with right now is being able to read the html data and parsing the forms.

[php]
html = response.read()
forms = ParseResponse(response, backwards_compat=False, request_class=request)

print html
print forms
[/php]
In this, html would equal the proper html value on the page; and forms would equal []

[php]
forms = ParseResponse(response, backwards_compat=False, request_class=request)
html = response.read()
 
print html
print forms
[/php]
In this, html would equal None; and forms would equal [<ClientForm.HTMLForm instance at 0x00000000033203C8>] which is what it should equal.

So what i need to do is have the same urllib2.request object available for 2 different uses. Reading and Parsing.

Thanks
~Cody Woolaver

---

### Post by Pyro.699 on 2009-07-18
So i found out some interesting information.

This is happening because each class (at somepoint) calls **response.read()** and because this is a buffered function, once it reaches the end of the buffer, it stays there, it doesn't get reset the next time you call it.

This means that if i was to call **response.read()** 2 times in a row, it wouldn't work because the buffer has already reached the EOF marker. So what needs to be done is to have the buffer reset. Or something close to that, im not really 100% if i go that right, i was talking with a friend and heres what he said:

[quote=Friend]
*One option is to wrap your file like object in another object
*ie.
*You store the results of the read inside the class
*and then you override the read method
*In the read method, you return the data if you already have it or use the file object to get it if you don't
[/quote]

That didn't make a great deal of sense to me, but maybe you guys would be able to help me (hes offline now so i cant ask for more detail now).

Thanks once again Ubuntu Forums
~Cody Woolaver

---

### Post by smartbei on 2009-07-18
Here is what I came up with:

```

class ResponseProxy(object):
    def __init__(self, response):
        self.resp = response
        self.data = self.resp.read()
        self.index = 0
        
    def reset(self):
        self.index = 0
        
    def read(self, n = None):
        if n == None:
            self.index = len(self.data)
            return self.data[self.index:]
        
        to_return = self.data[self.index:self.index + n]
        self.index += n
        return to_return

    def __getattr__(self, name):
        if name in self.__dict__:
            return self.__dict__['name']
        else:
            return getattr(self.resp, name)

```
What this does is act as a proxy for the response object. As you can see, it receives it in the constructor, and then redefine it's read to take the data from the then variable we create (self.data).

The tricky part is what we do in the __getattr__. When a __getattr__ is defined, all syntax of the form <instance>.<name> is passed to the __getattr__ method os the <instance>, with the <name> as a parameter. Play around with it a bit (create a __getattr__ that just does 'print name' and you'll get the idea).

Here is the idea - I only want to proxy things that I have defined myself, and leave the rest of the functionality intact. So I check if the requested name is in my class. If so, that is what I return. Otherwise, I return what the caller would expect to receive, an object (be it a method, an internal variable, etc.) from the response object.

What this allows me to do, plainly speaking, is this:
```

resp = ResponseProxy(urllib2.urlopen("http://www.google.com"))
data = resp.read()
resp.reset() ## reset so more reads are possible.
if data == resp.read(): ## see, we read again
    print "Woohoo, we read again!"

```

Note that I actually break a bit of functionality such as readlines, and other methods of the response object that read the data not through the method read. This is because I read all the data beforehand (into self.data), so those methods won't crash, they will just act like the response object is empty. I checked though, the ClientForm module only uses read, so it works fine.

Hope this helps!

---

### Post by Pyro.699 on 2009-07-18
Thank you very much, i already have created a small Request class that i need to use, do you think you would be able to incorporate it into that?

[php]
global request_opener, cookiejar, lasturl
lasturl = ""
cookiejar = cookielib.CookieJar()
request_opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cookiejar))

def url_open(url):
    try:
        req = request(url)
        return request_opener.open(req)
    except urllib2.HTTPError:
        return False

def request(url, data=None, headers={}, origin_req_host=None, unverifiable=False, add_headers={}):
    global lasturl
    req_headers = {
            'User-Agent': 'Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.0.11) Gecko/2009060215 Firefox/3.0.11 (.NET CLR 3.5.30729)',
            'Referer': lasturl
        }
    
    headers.update(req_headers)
    headers.update(add_headers)
    try:
        ret = urllib2.Request(url, data, headers, origin_req_host, unverifiable)
        
        lasturl = url
        return ret
    except AttributeError:
        return url
[/php]

Thanks again
~Cody Woolaver

---

### Post by smartbei on 2009-07-18
Basically, you need to give the class ResponseProxy the actual response object, which in your code is in the function url_open. So it would be:
[php]
global request_opener, cookiejar, lasturl
lasturl = ""
cookiejar = cookielib.CookieJar()
request_opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cookiejar))

##XXX-I added the class declaration
class ResponseProxy(object):
    def __init__(self, response):
        self.resp = response
        self.data = self.resp.read()
        self.index = 0
        
    def reset(self):
        self.index = 0
        
    def read(self, n = None):
        if n == None:
            self.index = len(self.data)
            return self.data[self.index:]
        
        to_return = self.data[self.index:self.index + n]
        self.index += n
        return to_return

    def __getattr__(self, name):
        if name in self.__dict__:
            return self.__dict__['name']
        else:
            return getattr(self.resp, name)

def url_open(url):
    try:
        req = request(url)
        ##XXX-See the following line:
        return ResponseProxy(request_opener.open(req))
    except urllib2.HTTPError:
        return False

def request(url, data=None, headers={}, origin_req_host=None, unverifiable=False, add_headers={}):
    global lasturl
    req_headers = {
            'User-Agent': 'Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.0.11) Gecko/2009060215 Firefox/3.0.11 (.NET CLR 3.5.30729)',
            'Referer': lasturl
        }
    
    headers.update(req_headers)
    headers.update(add_headers)
    try:
        ret = urllib2.Request(url, data, headers, origin_req_host, unverifiable)
        
        lasturl = url
        return ret
    except AttributeError:
        return url
[/php]

By the way - it seems to me to be rather odd that your request function receives both 'headers' and 'add_headers', and then you add 'add_headers' to 'headers'. Shouldn't the calling function deal with that if the calling function wants to add headers?

Also, you don't need to do declare variables global in the global scope (not in a function). The only place you need to declare them is inside a function definition, so that they can be changed.

Hope this works for you. for me it seems to, but I don't have the rest of your code. Glad to help.

---

### Post by Pyro.699 on 2009-07-18
Sorry for what probally is a redundant question, but it doesnt seem to work that well for me.

It tried using this:
[php]
html = url_open("http://www.google.com")
print html.read()
[/php]

Just as a way to test it, and it always returned an empty string.

Thanks again
~Cody Woolaver

---

### Post by smartbei on 2009-07-18
Oops - had a bug in the proxy read method. I set the index before returning the data, so no data was returned. Here is the corrected source:
[php]
import cookielib
import urllib2
lasturl = ""
cookiejar = cookielib.CookieJar()
request_opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cookiejar))

##XXX-I added the class declaration
class ResponseProxy(object):
    def __init__(self, response):
        self.resp = response
        self.data = self.resp.read()
        self.index = 0
        
    def reset(self):
        self.index = 0
        
    def read(self, n = None):
        if n == None:
            ##XXX-the difference is here
            to_return = self.data[self.index:]
            n = len(self.data) - self.index
        else:
            if not isinstance(n, (int, long)):
                raise TypeError("n must be an integer type.")
            to_return = self.data[self.index:self.index + n]

        self.index += n    
        return to_return

    def __getattr__(self, name):
        if name in self.__dict__:
            return self.__dict__['name']
        else:
            return getattr(self.resp, name)

def url_open(url):
    try:
        req = request(url)
        ##XXX-See the following line:
        return ResponseProxy(request_opener.open(req))
    except urllib2.HTTPError:
        return False

def request(url, data=None, headers={}, origin_req_host=None, unverifiable=False, add_headers={}):
    global lasturl
    req_headers = {
            'User-Agent': 'Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.0.11) Gecko/2009060215 Firefox/3.0.11 (.NET CLR 3.5.30729)',
            'Referer': lasturl
        }
    
    headers.update(req_headers)
    headers.update(add_headers)
    try:
        ret = urllib2.Request(url, data, headers, origin_req_host, unverifiable)
        
        lasturl = url
        return ret
    except AttributeError:
        return url
[/php]

Edit: Added a bit of type-checking code... :-)

---

### Post by Pyro.699 on 2009-07-18
Works like a dream man, thanks so much :)

---

