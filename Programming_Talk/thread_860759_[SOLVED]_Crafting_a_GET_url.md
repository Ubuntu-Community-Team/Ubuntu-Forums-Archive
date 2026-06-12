---
title: "[SOLVED] Crafting a GET url"
date: 2008-07-15
forum: Programming Talk
---

### Post by themusicwave on 2008-07-15
Hey everyone,

I am plodding along with my learning and applying of web scripting.

So I have a script that is called by a form using POST.  It validates the input and if valid enters the user info into my database.  It also emails them and me.

Anyways, now I am working what to do with invalid data.  I thought I would be clever and create a URL that contains all the invalid fields like so:

[http://www.mydomain.com/script.py?name=1&email=1&submit=Submit+Query](http://www.mydomain.com/script.py?name=1&email=1&submit=Submit+Query)

The idea is that every field that is invalid will appear in the URL with a value of 1.  I then used an HTTP header to redirect the user to that URL.

like so

print 	"Location: " + url + "\n\n"

The redirect does work, but none of the values are displayed in the address bar.

The plan was for the original script to check to see if it had received any values.  If it had, it would then change the color of those values to red indicating they were wrong last time.

So now my questions are:

1) What happened to the values appended to the URL?
2) How can I throw the user back to the original form on invalid input and indicate which fields are wrong?

Thanks,

Jon

---

### Post by mssever on 2008-07-15
I've successfully used that same basic approach. You probably just have a bug in your code somewhere. Another option is to include that info in your session.

---

### Post by themusicwave on 2008-07-16
Well I got it to work, as you suspected it was an error.

Interestingly, I was creating the url and redirecting fine.  What I failed to remember is the page I redirected to was setup to redirect back to another page if anything went wrong.

Well it saw some form input it didn't like and sent me back to the start of the chain with a new URL. 

That's why I never saw my URL.

So it works now!

---

