---
title: "Passing a URL into a variable for wget"
date: 2012-09-17
forum: New to Ubuntu
---

### Post by TechDawg on 2012-09-17
I am trying to pass a URL into a variable so that I can call it later with wget in order to import dynamic data. Here's my thought process. First, I take a file (stat.txt) that has several lines of different URLs with identifying tags before the http:// and pull out the handful of lines that I need with grep. Then I strip the identifying tags off to obtain the URLs by themselves through sed. Next, I select one at random so that wget can utilize it later and a poor man's version of load balancing (sort and head). Here's the script that I came up with which works as intended (URL is a valid URL in the format of [http://domain.com/folder/stat.txt):](http://domain.com/folder/stat.txt):)

```
grep "url0=h*" stat.txt | sed "s/url0=//g" | sort -R | head -n 1
```

Now the issue is when I try to define a variable using this:
```
SITE=$"(grep "url0=h*" status.txt | sed "s/url0=//g" | sort -R | head -n 1)"
```
It appears to take just fine, but when I call the variable by $SITE it returns:
: No such file or directoryym/servinfo/data.txt
It's like it is trying to do something with the URL but taking the last half of it and appending it to the error message (without a space) instead of just simply printing it. Any ideas on how to define my variable? Also, the next step that I'm guessing would be to call it in the form of:
```
wget -r -nH $SITE
```

---

### Post by TechDawg on 2012-09-17
Guess that I just needed to fully define my logic to see the issue. Here's the resolution that I came up with:
```
grep "url0=h*" stat.txt | sed "s/url0=//g" | sort -R | head -n 1 > SITE
```
Which overwrites the value of the URL into a file instead of a variable each time it is run and therefore I can call wget correctly through:
```
wget -r -nH -i SITE
```

Thanks for letting me get the issue defined and anyone who began to work on the issue at hand. Any ideas though on how to pass that info to a variable would be greatly appreciated out of useful curiosity.

---

