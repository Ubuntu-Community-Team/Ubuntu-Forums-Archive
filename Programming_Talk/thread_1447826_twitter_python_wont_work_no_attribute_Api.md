---
title: "twitter python wont work no attribute Api"
date: 2010-04-05
forum: Programming Talk
---

### Post by jakeeee on 2010-04-05
I'm trying to create a python program that does twitter things lol.
That's the twitter section of my program in the attachment below.
I already imported twitter,
But everytime I try and run it i get this error:

AttributeError: 'module' object has no attribute 'Api'

I have no idea what I did wrong...
If you need more details please let me know.
And if you see any other errors please let me know.
Thank you :)

---

### Post by wmcbrine on 2010-04-05
The error message refers to the line that starts "api = twitter.Api", and it's saying that twitter.Api doesn't exist. If you feel that it does... you didn't by any chance name this file (or another file) "twitter.py", did you? If so, it's confusing Python into loading *that* when you say "import twitter", instead of the package that you're trying to load.

If that's not it, you should tell us the source for the module you're trying to load, since it's not in the standard library.

---

### Post by jakeeee on 2010-04-06
> **wmcbrine said:**
> The error message refers to the line that starts "api = twitter.Api", and it's saying that twitter.Api doesn't exist. If you feel that it does... you didn't by any chance name this file (or another file) "twitter.py", did you? If so, it's confusing Python into loading *that* when you say "import twitter", instead of the package that you're trying to load.

If that's not it, you should tell us the source for the module you're trying to load, since it's not in the standard library.


It has to exist since I got the code right off the page.
[http://code.google.com/p/python-twitter/](http://code.google.com/p/python-twitter/)

And i dont have anythiong named twitter.py

---

### Post by jakeeee on 2010-04-06
Anyone? :o

---

### Post by cdekter on 2010-04-06
Works just fine for me. You must have another file called twitter.py somewhere in your python path masking the real twitter module.

How did you install python-twitter?

---

### Post by jakeeee on 2010-04-06
sudo easy_install python-twitter
I think?
Thats how some website told me to install it.

Anyways,
I did whereis twitter.py
And it said i have it in /usr/local/bin/twitter

theres two things in there:

twitter and twitterbot

Does that help any?

---

### Post by cdekter on 2010-04-06
Well I did exactly the same steps you did, and it works for me :P

---

### Post by jakeeee on 2010-04-06
Hmm...
Well is there any other way i can accsess twitter through ym program without this import?

---

### Post by jakeeee on 2010-04-06
?

---

