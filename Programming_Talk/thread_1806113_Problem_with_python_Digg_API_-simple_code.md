---
title: "Problem with python Digg API -simple code"
date: 2011-07-17
forum: Programming Talk
---

### Post by mikedemon on 2011-07-17
Hello, 
 
I try to fetch some data via the version 2 of Digg's API using python.  The code returns all details of the selected user. However I just want to see the total number of followers this user has. I tried to do it but keep getting errors
 
  up to here works and returns all details as shown below
 
{u'count': .diggstatic.com/user/6754998/r.png'], u'gender': u'', u'diggs': 64104, u'comments': 226, u'followers': 3582, u'location': u'Lahore', u'following': 217, u'submissions': 441, u'icon': u'http://cdn1.diggstatic.com/user/6754998/p.png'}}, u'timestamp': 1310895431, u'cursor': u'', u'version': u'2.0', u'authorized': u'0', u'data': u'users', u'method': u'user.getInfo', u'user': None}
 
I tired to add this line to get the followers but getting error (AttributeError: 'dict' object has no attribute 'followers')
 
fol = user.followers
print fol
u'followers' is not allowed due to quotation mark

---

### Post by cgroza on 2011-07-17
The user variable seems just a plain dictionary. Try:
```

user["followers"]

#and not

user.followers


```Also, I suggest you to not assign to the user variable and use a different one inside the loop to store your data.

---

### Post by mikedemon on 2011-07-17
i tired that but getting KeyError: 'fors' , please help

---

### Post by cgroza on 2011-07-17
Post the output of "print user.keys()" in CODE tags.

---

### Post by mikedemon on 2011-07-17
> **cgroza said:**
> Post the output of "print user.keys()" in CODE tags.
 
hi
 
it says 
 
```
 [ta', u'method', u'user']
```

---

### Post by cgroza on 2011-07-17
Ok, that dictionary has no such key.
I tried to find the documentation for the Digg2 API, but with no luck.

If you could provide me a link where I can find it, I may be able to help you.
Otherwise, I have no clue how that API works.

---

### Post by mikedemon on 2011-07-17
> **cgroza said:**
> Ok, that dictionary has no such key.
I tried to find the documentation for the Digg2 API, but with no luck.
 
If you could provide me a link where I can find it, I may be able to help you.
Otherwise, I have no clue how that API works.
 
Hi
 
Dont the api

---

### Post by TwoEars on 2011-07-17
The reason why user.keys() isn't showing you what you want is because followers is actually based inside a nested dict - to get to it, try -

```

from digg.api import Digg2
digg = Digg2()
 
li=["usq1111"]
 
for user in li:
    #Are you sure this is what you want to do? I don't think it is.
    user= digg.user.GetInfo(usernames="usq1111")
    print user['users']['usq1111']['followers']


```

The original problem you were getting stems from the fact you can't access dict objects in Python using dict.<key>

---

### Post by mikedemon on 2011-07-17
i was not aware of this

---

### Post by cgroza on 2011-07-17
> **mikedemon said:**
> Hi you are very good and i was not aware of this , I got another tiny problem. If the names were coming from a txt file , more then one name 
 
[FONT=Courier New][code][/FONT]
[FONT=Courier New] user= digg.user.GetInfo(usernames=listtextfile))[/FONT]
 
[FONT=Courier New] print user['users'],["What to write here"]['followers']/[code][/FONT]
 
[FONT=Courier New]also want to out the results in txt file file , please help[/FONT]

A user name from the listtextfile

---

### Post by mikedemon on 2011-07-17
> **cgroza said:**
> A user name from the listtextfile
sure@?

---

### Post by TwoEars on 2011-07-17
> **mikedemon said:**
> Hi you are very good and i was not aware of this , I got another tiny problem. If the names were coming from a txt file , more then one name 
 
[FONT=Courier New]```
[/FONT]
[FONT=Courier New] user= digg.user.GetInfo(usernames=listtextfile))[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New] print user['users'],["What to write here"]['followers']/[code][/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]also want to out the results in txt file file , please help[/FONT]
[FONT=Courier New][/FONT]
Something like -

[code]
from digg.api import Digg2
d = Digg2()

names = [x.rstrip() for x in open('usernames.txt').readlines()]
users = d.user.getInfo(usernames=','.join(names))

followers = dict()

for name in users['users']:
    followers[name] = users['users'][name]['followers']

print followers
```

Note this is very crude, and needs cleaning up for production code (it's just an example).

---

### Post by mikedemon on 2011-07-17
Note this is very crude, and needs cleaning up for production code (it's just an example).[/QUOTE]
 
Thanks a Lot, Dont know how to thank you

---

### Post by TwoEars on 2011-07-17
> **mikedemon said:**
> Thanks a Lot, Dont know how to thank you

No worries, that's what these forums are here for.

---

### Post by mikedemon on 2011-07-18
g error: KeyError: 'users' , Want to see the latest items myfollower dugg. From version 1.

---

### Post by TwoEars on 2011-07-18
> **mikedemon said:**
> Can you please help with the following code
 
```
from digg.api import Digg
digg = Digg()
 
li=["usq1111"]
 
for user in li:
 
    user= digg.user.getDugg(username="usq1111",count=1)
    print user['users']['usq1111']['title']
```
 
Getting error: KeyError: 'users' , Want to see the latest items myfollower dugg. From version 1.
 
Can you mix version 1 and 2 in a single program.

I certainly wouldn't recommend it, as version 1 returns XML whereas version 2 returns JSON - something much easier to deal with in Python.

The way you're going to do it is probably going to be through - [http://developers.digg.com/version2/user-getmynews](http://developers.digg.com/version2/user-getmynews)

---

### Post by mikedemon on 2011-07-18
> **TwoEars said:**
> I certainly wouldn't recommend it, as version 1 returns XML whereas version 2 returns JSON - something much easier to deal with in Python.
 
The way you're going to do it is probably going to be through - [http://developers.digg.com/version2/user-getmynews](http://developers.digg.com/version2/user-getmynews)
 
 
Is there a way to do this without authentication requirement. Each time i tired to  authenticate i get the following error
 
HTTPError: HTTP Error 500: Internal Server Error

---

### Post by TwoEars on 2011-07-18
> **mikedemon said:**
> Is there a way to do this without authentication requirement. Each time i tired to  authenticate i get the following error
 
HTTPError: HTTP Error 500: Internal Server Error

No, it's required. What code are you using? (Replacing the key details with <KEY>)

---

### Post by mikedemon on 2011-07-18
I get the error after entering code supplied From Digg, I changed the key and secret

---

### Post by TwoEars on 2011-07-18
> **mikedemon said:**
> I get the error after entering code supplied From Digg, I changed the key and secret
 
 

 
```

from urlparse 
import parse_qsimport sysfrom oauth2 
import Consumer, Tokenfrom 
digg.api import Diggconsumer = Consumer(key='myoauthconsumerkey', secret='myoauthconsumersecret')
 
digg = Digg(oauth_consumer=consumer)
response = digg.oauth.getRequestToken(oauth_callback='oob')
 
request_token = parse_qs(response)print 'Please visit the following URL to authorize this application'print 'http://digg.com/oauth/authorize?oauth_token=%s' % request_token['oauth_token'][0]sys.stdout.write('Type the verification number: ')verifier = sys.stdin.readline().rstrip('\r\n')request_token = Token(request_token['oauth_token'][0], request_token['oauth_token_secret'][0])request_token.set_verifier(verifier)response = digg.oauth.getAccessToken(oauth_token=request_token)response = parse_qs(response)access_token = Token(response['oauth_token'][0], response['oauth_token_secret'][0])print digg.oauth.verify(oauth_token=access_token)print digg.story.digg(id=22091157, oauth_token=access_token)
```

Can you link me to the documentation for this code? It doesn't seem very good to me.

---

### Post by mikedemon on 2011-07-18
File "build\bdist.win32\egg\digg\api.py", line 96, in __call__
raise DiggError('Digg sent status %i for method: %s\ndetails: %s' % (e.code, self.methodname, e.fp.read()))
DiggError: Digg sent status 400 for method: user.getDugg
details: <html><body><b>Http/1.1 Bad Request</b></body> </html>

---

### Post by TwoEars on 2011-07-18
What you should be doing is something like -

```

from digg.api import Digg
digg = Digg()
names = [users.strip()for users in open('usernames.txt')]
for name in names:
    for a in digg.user.GetDugg(username=name ,count=1)['stories']:
        print a['title']
```

Out of curiosity, how much Python experience do you have? I suggest getting a bit more before you start messing around with something like a website's API.

---

### Post by mikedemon on 2011-07-18
[QUOTE=TwoEars;11061106]What you should be doing is something like -
 
 
Hi
 
Thank you. Not much but did years they look bit similar, APIs are diffucult especially diggs one .
thanks for all your help.

---

### Post by TwoEars on 2011-07-18
> **mikedemon said:**
> Hi
 
Thank you. Not much but did VB6 about 4 years they look bit similar, APIs are diffucult especially diggs one . Can understand the code but cant write it. Phyton is very effective will switch to it. Last two question, 1  regarding above code count function does not work. loops forever and Why time stamps are not human readable such as timestamp="1176999607"? means?
 
thanks

I suggest digging into a tutorial or try smaller projects beforehand then, just so you get the basics nailed down.

It loops forever? Are you sure, or is it just taking a long time? At which stage is it looping forever?

Time - [http://en.wikipedia.org/wiki/Unix_time](http://en.wikipedia.org/wiki/Unix_time)

---

### Post by mikedemon on 2011-07-18
> **TwoEars said:**
> I suggest digging into a tutorial or try smaller projects beforehand then, just so you get the basics nailed down.
 
It loops forever? Are you sure, or is it just taking a long time? At which stage is it looping forever?
 
Time - [http://en.wikipedia.org/wiki/Unix_time](http://en.wikipedia.org/wiki/Unix_time)

 
No its fine, thats all i wanted to ask , i ordered a book will start reading very soon. I want to see how Facebooks API looks but will take some time reading the book.
 
thanks again

---

### Post by TwoEars on 2011-07-18
> **mikedemon said:**
> No its fine, thats all i wanted to ask , i ordered a book will start reading very soon. I want to see how Facebooks API looks but will take some time reading the book.
 
thanks again

The Facebook API is very nice indeed, much nicer than Digg. Great documentation and great Python support.

---

### Post by mikedemon on 2011-07-18
> **TwoEars said:**
> The Facebook API is very nice indeed, much nicer than Digg. Great documentation and great Python support.
 
 
Will contact you if i get problems: )) Just kidding, Are you a profesional programmer?  i meant do you do this for living?

---

### Post by TwoEars on 2011-07-18
> **mikedemon said:**
> Will contact you if i get problems: )) Just kidding, Are you a profesional programmer?  i meant do you do this for living?

Of course you can, though you may find posting your questions openly on the forums or the Python mailing lists may solve your problems better in some cases ;) And yes, I am a professional programmer.

---

### Post by mikedemon on 2011-07-18
yjamk upo

---

### Post by TwoEars on 2011-07-18
> **mikedemon said:**
> thanks for being so kind and helpful. One very last question 
 
```
from digg.api import Digg
digg = Digg()
names = [users.strip()for users in open('username.txt')]
for name in names:
    for a in digg.user.GetDugg(username=name ,count=1)['stories']:
        print a['title']
        print a['timestamp']

```
 
I want to capture the time that item was Dugg. i added print a['timestamp'] tired date, time doesnt work , Can you please help me

No worries. :)

If you use "print a" in that loop and post the output here (just from one, not from all of them!), what does it give you?

---

### Post by mikedemon on 2011-07-18
> **TwoEars said:**
> No worries. :)
 
If you use "print a" in that loop and post the output here (just from one, not from all of them!), what does it give you?
 
[COLOR=black][FONT=Verdana]That&#8217;s cleaver, will check it my self next time. It is submit date[/FONT][/COLOR]
 
Thanks again

---

### Post by mikedemon on 2011-07-22
Thanks sorted

---

