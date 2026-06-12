---
title: "PythonChallenge Level question (Dealing Evil)"
date: 2010-04-08
forum: Programming Talk
---

### Post by vik_2010 on 2010-04-08
I'm doing the python challenge, and so far, so good. 

SPOILER ALERT!

I'm on level 12, and the challenge is to figure out what to do at this website:

[http://www.pythonchallenge.com/pc/return/evil.html](http://www.pythonchallenge.com/pc/return/evil.html)

I needed help and looked it up. Apparently, there are a number of other pics (Evil2.jpg, Evil3.jpg,etc) that are needed to solve the problem. What I gather is that one is supposed to intuitively realize that there should be other jpgs beyond Evil1, and (randomly) check for their existence by typing them in a webbrowser.

My question is: Is there a manner in which one can programmatically check for the existence of certain files on a web server(http server - I think that makes a difference - someone please point out this mistake if i'm wrong), or is guessing and intuition the only way to solve this thing? My understanding is that one can search the directory tree on an FTP server, but I don't know if one can do the same on an http server.

Thanks,

-V

---

### Post by vik_2010 on 2010-04-08
to clarify: the evil1.jpg is in the page source, and I am doing this challenge in python

---

### Post by heikaman on 2010-04-08
you can request the picture and if you get 404 response then it doesn't exist.

---

### Post by vik_2010 on 2010-04-08
yes, but I'm wondering if there's a way to find all the files in a certain directory on a webserver (for example, maybe the runners of the server decided to allow everyone to view it), even if they aren't used in the webpage source.

The reason I'm asking this is because there would have been no way for me to intuit the existence of these other jpegs, since they aren't in the page's source - I would have blindly been poking around for the existence of files on the webserver.

Hmm..Maybe their isn't a way to view a web server's directory's contents, and the challenge was based, in large part, on sheer lucky guesswork. :(

---

### Post by WillFerrellLuva on 2010-04-08
I actually just solved that puzzle a few days ago.  Not sure how much of a hint you want, but it seems you are on the wrong track.  You dont need to systematically search the server for evil files.  

Another hint below:
[COLOR="White"]If you found more then one evil file you are on the right track.  You have to look at those files, they will lead you to getting one more file which is what the bulk of the puzzle is about[/COLOR]

---

