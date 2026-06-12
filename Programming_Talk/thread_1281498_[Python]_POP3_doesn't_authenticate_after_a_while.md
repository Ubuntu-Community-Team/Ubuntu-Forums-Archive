---
title: "[Python] POP3 doesn't authenticate after a while"
date: 2009-10-03
forum: Programming Talk
---

### Post by fiddler616 on 2009-10-03
Hello,

I'm writing a program that involves repeatedly checking an email address. It executes successfully for a while, but then crashes:
```
No message right now! 196
No message right now! 197
No message right now! 198
No message right now! 199
Traceback (most recent call last):
  File "wikiomatic.py", line 132, in <module>
    message = getMessage()
  File "wikiomatic.py", line 27, in getMessage
    M.pass_("<password>")  
  File "/usr/lib/python2.6/poplib.py", line 189, in pass_
    return self._shortcmd('PASS %s' % pswd)
  File "/usr/lib/python2.6/poplib.py", line 152, in _shortcmd
    return self._getresp()
  File "/usr/lib/python2.6/poplib.py", line 128, in _getresp
    raise error_proto(resp)
poplib.error_proto: -ERR [AUTH] Username and password not accepted.

```
I'm guessing that the problem is that I log in in the getMessage() function, which is repeated many times (199 in this case), and that Gmail throws a fit after a while. It's probably pretty bad for performance, too. I tried moving the authentication code outside of the function (making the POP3 object M global), but that raised a bunch of errors itself.

What should I do?

Thanks.

---

### Post by wmcbrine on 2009-10-05
Put in a nice gap between checks. Several minutes, at least.

---

### Post by j7%&lt;RmUg on 2009-10-05
Try wmcbrines suggestion, it could be gmail closing the connection because it thinks your a bot.

---

### Post by fiddler616 on 2009-10-05
That seems to be working better, but I haven't gone through 200 loops yet, so I may be wrong.
I find it ridiculous that there's not a way to login just once though...
Here's the function:
[PHP]def getMessage():
    t.sleep(120)#Delays login so Gmail doesn't think we're up to any shenanigans.
    M = poplib.POP3_SSL('pop.gmail.com', 995) #Line A
    M.user("<email>")
    M.pass_("<password>")  #Line C
    numMessages = len(M.list()[1])
    message = ""
    for i in range(numMessages):
        for j in M.retr(1)[1]:
            message += j
    M.quit()
    return message[/PHP]
And before I tried moving lines A-C to outside of the function, and it didn't work.

---

### Post by j7%&lt;RmUg on 2009-10-06
So you want to have a separate function for logging in?

Just arrange it so that if login was successful, return true and pass it on to the getMessage() function.

---

### Post by wmcbrine on 2009-10-06
> **fiddler616 said:**
> And before I tried moving lines A-C to outside of the function, and it didn't work.Presumably M.quit() is logging you out again. POP3 isn't designed to be continuously logged in anyway. (If you want that, try IMAP.)

You're still going to want a delay between checks, either way. Even two minutes is a bit short.

---

