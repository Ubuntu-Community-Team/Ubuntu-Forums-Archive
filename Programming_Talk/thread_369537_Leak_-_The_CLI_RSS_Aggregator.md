---
title: "Leak - The CLI RSS Aggregator"
date: 2007-02-24
forum: Programming Talk
---

### Post by Note360 on 2007-02-24
Well, here is another one of my apps that will fail and fall of the face of the earth, but whatever I find it usefull. This is just a draft (I may rewrite it in Java for a school project if I cant find a better idea) of what I am calling leak.

leak - leaking extraordinary aggregated knowledge
(The name came before the acronym but CLI apps must have acronyms)

Description - Leak is a very basic, very simple, not very fast, command line rss aggregator writteb in python. It probably isn't the best choice but if your goal is simply to read some feeds then it is pretty good. 

Usage - Some of this isnt found in the -h command

-u url         sets a url to aggregate data from, you can make a list like this [url1, url2, etc]
-i number   goes directly to the posts you specified (only works for one url currently) same listing abilities as -u

If you give no arguments it will look in your .leakrc file

after each post you can do the following. 
q                 quits the program
c or return    goes to next item in feed
g                 opens the item in your webbrowser
n                  goes to the next feed (url)

Their is also a .leakrc, but unfortuantly you have to make it yourself currently, because I didnt make a installation script yet. If this is popular enough i'll make a setup.py.

To install the .leakrc
1) Take the leakrc I packaged with the file and edit it to your liking. The syntax is simple
2) Move it to your home directory and rename it to .leakrc


If you need any help just ask

Have fun!

Oh and it requires python-feedparser (sudo apt-get install feedparser)

---

### Post by rocktorrentz on 2007-02-28
I was looking for an rss reader to stick on my server to automatically download my favourite podcasts. This may be just the right tool.

Thanks
rocktorrentz

---

### Post by Note360 on 2007-02-28
this wont dl anything, but hey if you can find a use for it thatd be great. Tell me what u want and ill adder in when I get time.

---

### Post by TeraDyne on 2007-02-28
> **rocktorrentz said:**
> I was looking for an rss reader to stick on my server to automatically download my favourite podcasts. This may be just the right tool.

Thanks
rocktorrentz

Try [Bashpodder]("http://linc.homeunix.org:8080/scripts/bashpodder/"). It's a CLI podcatcher, and it's really good.

Edit: Whoops. Forgot to mention that I will try this out later, when I get some more free time.

---

### Post by Note360 on 2007-02-28
No problem. It is pretty bad its decent for like a 2 hour run of coding and debugging. I am looking for more features to add in. (eg podcatching). If any one wants to help feel free. I dont think I put in a copyright notice, but it is supposed to be GPL.

---

### Post by Note360 on 2007-03-09
I recently added Podcatching capability. I am trying to figur eout how to make it more interactive personally I think it is perfectly fine now. Any suggestions?

---

### Post by Prophecy67 on 2009-09-07
Is there anything specifically i could drop into rc.d or crontab to run every so often to suck images off of a remote RSS? I've been looking all over for that and i can't appear to find it..

If you're interested it's this URL:

[http://feeds.feedburner.com/4walledImageFeed](http://feeds.feedburner.com/4walledImageFeed)

Hope to hear from you soon.!

---

