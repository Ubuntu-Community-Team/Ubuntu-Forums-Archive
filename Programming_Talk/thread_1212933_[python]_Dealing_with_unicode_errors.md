---
title: "[python] Dealing with unicode errors"
date: 2009-07-14
forum: Programming Talk
---

### Post by Pyro.699 on 2009-07-14
Hey,

So im sending information via the ClientForm module and ran into this lovely looking error.

```

  File ".\ClientForm.py", line 3114, in click
    self._request_class)
  File ".\ClientForm.py", line 3322, in _click
    return control._click(self, coord, return_type, request_class)
  File ".\ClientForm.py", line 2465, in _click
    r = form._switch_click(return_type, request_class)
  File ".\ClientForm.py", line 3390, in _switch_click
    req_data = self._request_data()
  File ".\ClientForm.py", line 3364, in _request_data
    return (uri, urlencode(self._pairs()),
  File ".\ClientForm.py", line 189, in urlencode
    v = urllib.quote_plus(str(v))
    
UnicodeEncodeError: 'ascii' codec can't encode character u'\u2122' in position 1783: ordinal not in range(128)

```

Sexxy huh? How would you guys deal with something like this?

here is the urlencode function that the guy built
[php]
def urlencode(query,doseq=False,):
    """Encode a sequence of two-element tuples or dictionary into a URL query \
string.

    If any values in the query arg are sequences and doseq is true, each
    sequence element is converted to a separate parameter.

    If the query arg is a sequence of two-element tuples, the order of the
    parameters in the output will match the order of parameters in the
    input.
    """

    if hasattr(query,"items"):
        # mapping objects
        query = query.items()
    else:
        # it's a bother at times that strings and string-like objects are
        # sequences...
        try:
            # non-sequence items should not work with len()
            x = len(query)
            # non-empty strings will fail this
            if len(query) and type(query[0]) != types.TupleType:
                raise TypeError()
            # zero-length sequences of all types will get here and succeed,
            # but that's a minor nit - since the original implementation
            # allowed empty dicts that type of behavior probably should be
            # preserved for consistency
        except TypeError:
            ty,va,tb = sys.exc_info()
            raise TypeError("not a valid non-string sequence or mapping "
                            "object", tb)

    l = []
    if not doseq:
        # preserve old behavior
        for k, v in query:
            k = urllib.quote_plus(str(k))
            v = urllib.quote_plus(str(v))
            l.append(k + '=' + v)
    else:
        for k, v in query:
            k = urllib.quote_plus(str(k))
            if type(v) == types.StringType:
                v = urllib.quote_plus(v)
                l.append(k + '=' + v)
            elif type(v) == types.UnicodeType:
                # is there a reasonable way to convert to ASCII?
                # encode generates a string, but "replace" or "ignore"
                # lose information and "strict" can raise UnicodeError
                v = urllib.quote_plus(v.encode("ASCII","replace"))
                l.append(k + '=' + v)
            else:
                try:
                    # is this a sufficient test for sequence-ness?
                    x = len(v)
                except TypeError:
                    # not a sequence
                    v = urllib.quote_plus(str(v))
                    l.append(k + '=' + v)
                else:
                    # loop over the sequence
                    for elt in v:
                        l.append(k + '=' + urllib.quote_plus(str(elt)))
    return '&'.join(l)
[/php]

Thanks in advance
~Cody Woolaver

---

### Post by martinpm24 on 2009-07-14
I think you are converting unicode to ascii, thats the problem. You need to replace all str() with unicode()

---

### Post by Can+~ on 2009-07-14
Read: [http://www.python.org/dev/peps/pep-0263/](http://www.python.org/dev/peps/pep-0263/) plus the above post.

Another alternative is to move to Python3, where all strings are unicode by default and bytes and bytearrays are the ol' ascii strings.

So instead of

[PHP]u"I'm unicode!"
"I'm ascii"[/PHP]

is
[PHP]b"I'm ascii"
"I'm unicode!"[/PHP]

---

### Post by Pyro.699 on 2009-07-15
I tried Python3, but found it was really incompatiable with some scripts i had. It was quite confusing to use.

Aside, i changed all variables that were going to be sent to the server, to **unicode()** but that didn't work (Got the same error).

Next, i tried to alter the **urlencode()** function by replacing all **str()** with **unicode()** then i got this error.
```

Traceback (most recent call last):
  File ".\ClientForm.py", line 3114, in click
    self._request_class)
  File ".\ClientForm.py", line 3322, in _click
    return control._click(self, coord, return_type, request_class)
  File ".\ClientForm.py", line 2465, in _click
    r = form._switch_click(return_type, request_class)
  File ".\ClientForm.py", line 3390, in _switch_click
    req_data = self._request_data()
  File ".\ClientForm.py", line 3364, in _request_data
    return (uri, urlencode(self._pairs()),
  File ".\ClientForm.py", line 189, in urlencode
    v = urllib.quote_plus(unicode(v))
  File "C:\Python26\lib\urllib.py", line 1226, in quote_plus
    s = quote(s, safe + ' ')
  File "C:\Python26\lib\urllib.py", line 1220, in quote
    res = map(safe_map.__getitem__, s)
KeyError: u'\u2122'

```

I also made my own **request_class** which is an argument that can be passed to the ClientForm module. I did this so if i needed to add special headers i would be able to do it.
[php]
def request(url, data=None, headers={}, origin_req_host=None, unverifiable=False, add_headers={}):
    req_headers = {
            'Referer': lasturl
        }
    headers.update(req_headers)
    headers.update(add_headers)
    try:
        return urllib2.Request(url, data, headers, origin_req_host, unverifiable)
    except AttributeError:
        return url
[/php]

Thanks once again for your help guys :)
~Cody Woolaver

---

### Post by Pyro.699 on 2009-07-18
Hey guys, just wondering if anyone had anymore information, I'm still getting this error.

---

### Post by smartbei on 2009-07-18
I would solve this by encoding the unicode string. For example, I could encode it as utf8, and in this way turn it into a normal string. For example:
```

## fails, since it is unicode.
ClientForm.urlencode({"a":3, 'b':'aaaa', 'c':u'&#1490;&#1490;&#1490;'})

## works, since it has been encoded
ClientForm.urlencode({"a":3, 'b':'aaaa', 'c':u'&#1490;&#1490;&#1490;'.encode('utf8')})

```
(I am using hebrew as an example because that is what I have here - it doesn't matter).

The question is: What encoding does the site you are requesting from expect? In general, this will be the same as the encoding the page arrives in (See View->Character Encoding in Firefox). Otherwise, I think there can be a 'enctype=' in the form declaration (in html) that specifies what encoding the server expects the reply to be in.

You need to send the data to the server in the correct encoding, otherwise the server will either reject your input, or it might not parse it correctly and arrive at a different result.

---

### Post by Pyro.699 on 2009-07-18
Wow smartbei, your just full of help today :D

Well, im not actually using the ClientForm urlencode method. That method is called when you submit a form.

So:
[php]
form['myInput'] = "Some Text, then &#1490;&#1490;&#1490;"
form.click()
[/php]

Thats when i get the error thrown back at me. Should i do:
[php]
form['myInput'] = "Some Text, then &#1490;&#1490;&#1490;".encode('ISO-8859-1') ##I think thats the right encoding type
form.click()
[/php]

---

### Post by smartbei on 2009-07-18
If you create the string as unicode, then use. Otherwise it will yell at you with something like "ascii codec...".
So:
[php]
## Notice the 'u'
form['myInput'] = u"Some Text, then &#1490;&#1490;&#1490;".encode('ISO-8859-1') ##I think thats the right encoding type
form.click()
[/php]
Should work. Of course, the encoding you chose is for Hebrew, I don't know what language you need to encode ;-)

I help when I can. Actually, I am studying for a test this monday and I am using this forum as a break every so often - that's why I'm here all day :-).

---

### Post by Pyro.699 on 2009-07-18
Well i thank you, i completed the project you helped me with in the other thread. And now im back on my large project.

How would you do that to a variable?
[php]
form['myInput'] = u""+variable+"".encode('ISO-8859-1')
form.click()
[/php]

Or is that where i use **unicode()**
[php]
form['myInput'] = unicode(variable).encode('ISO-8859-1')
form.click()
[/php]

Thanks once again :)
~Cody Woolaver

---

### Post by smartbei on 2009-07-18
Ah, now there is a problem! You need to figure out what encoding the variable is currently in, if it isn't unicode. (Though, reading your error above it appears that it IS unicode...)

Anyway, what you need to do is variable.decode("<encoding>"), which returns a unicode object which you can then encode however you want. For example:
[php]
var = "&#1490;&#1490;&#1490;"
varu = var.decode("utf-8") ## assuming that is what var is currently encoded in
variso = varu.encode("windows-1255") ## re-encode it with a common hebrew encoding
[/php]
You can also use the unicode function:
[php]
varu = unicode(var, 'utf8')
[/php]
It just needs to receive the encoding parameter if the original encoding isn't ansi.
I just noticed that ISO-8859-1 is actually the default (latin1) encoding. This means that it probably won't work, since it pobably does not contain the characters you want. My guess is that you want utf-8, since it is really common nowadays.

---

### Post by Pyro.699 on 2009-07-18
Yeah, i read the wrong line when i was getting the data.

Anyways, i tried a few things for my script and ill post the results.

**form['title'] = unicode(title, 'utf-8')**
```

Traceback (most recent call last):
  File ".\Main.py", line 277, in <module>
    _do()
  File ".\Main.py", line 265, in _do
    script.run(temps[j]['url'], temps[j]['feedback_loc'], posts[i]['title'], posts[i]['message'], 1)
  File ".\script.py", line 183, in post
    form['title'] = unicode(title, 'utf-8')
TypeError: decoding Unicode is not supported

```

**form['title'] = unicode(title).encode('utf-8')**
```

Traceback (most recent call last):
  File ".\Main.py", line 277, in <module>
    _do()
  File ".\Main.py", line 265, in _do
    script.run(temps[j]['url'], temps[j]['feedback_loc'], posts[i]['title'], posts[i]['message'], 1)
  File ".\script.py", line 207, in post
    html = url_open(form.click("submit")).read()
  File ".\ClientForm.py", line 3114, in click
    self._request_class)
  File ".\ClientForm.py", line 3322, in _click
    return control._click(self, coord, return_type, request_class)
  File ".\ClientForm.py", line 2465, in _click
    r = form._switch_click(return_type, request_class)
  File ".\ClientForm.py", line 3390, in _switch_click
    req_data = self._request_data()
  File ".\ClientForm.py", line 3364, in _request_data
    return (uri, urlencode(self._pairs()),
  File ".\ClientForm.py", line 189, in urlencode
    v = urllib.quote_plus(unicode(v))
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe2 in position 1783: ordinal not in range(128)

```The character it is having problems with is: ¢

---

### Post by smartbei on 2009-07-18
First, return the ClientForm.py file to its original state... those are supposed to be 'str' :-).

That should actually solve the problem, as long as you then have:
```

form["title"] = title.encode("utf8")

```
The extra call to unicode isn't necessary, because it appears that title is already unicode.

A word of advice - don't change library's code so quickly. It makes your own code (which relies on them) not cross-platform. Heck, not cross-computer (even with the same platform).

---

### Post by Pyro.699 on 2009-07-18
I forgot to revert it xD

I'm still getting

[B][I]UnicodeDecodeError: 'ascii' codec can't decode byte 0xe2 in position 1783: ordinal not in range(128)
[/I][/B]

---

### Post by smartbei on 2009-07-18
That is odd, because on my end it works fine. I am doing:
```

import ClientForm
f = ClientForm.ParseResponse(urllib2.urlopen("http://www.google.com"), backwards_compat = False)
form = f[0]
form["q"] = "¢"

```
And it works fine. Are you sure that is what it is stuck on?
If yes, please print the whole string and attach it or something - I need to be able to recreate the error :-).

---

### Post by Pyro.699 on 2009-07-18
The actual post body is inappropriate for these forums ^^; But here are all the non [a-zA-Z0-9] Characters (also punction was removed).

> 
â&#8222;¢â&#8222;¢â&#8364;&#8221;â&#8364;&#8221;â&#8364;&#8221;â&#8364;&#8482;â&#8222;¢â&#8364;&#8221;â&#8222;¢â&#8364;&#8221;â&#8364;&#8482;Â®


---

### Post by smartbei on 2009-07-18
That works on my end - no errors at all.
I have no idea what the problem is... Are you sure you reverted all changes to ClientForm and then restarted python?

---

### Post by Pyro.699 on 2009-07-18
Yeah, i went and coppied an unchanged version back into the folder.

I cant even print it to the terminal cause i get:
***UnicodeEncodeError: 'charmap' codec can't encode character u'\u2122' in position 1783: character maps to <undefined>***

The information that i'm getting is stored in a MySQL database, then retrieved via urllib2 through a php script. I dunno if you know MySQL but is there a type of table that i can have it so that the info has to be ascii?

And i just answered my own question, the database type is now ascii_general_ci so i wont have to deal with this problem anymore.

Thanks for your help though.

---

