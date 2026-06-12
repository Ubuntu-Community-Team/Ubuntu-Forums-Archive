---
title: "Mozilla wont process my page correctly"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by y-aji on 2008-05-01
Hey all,

Sorry to be a bother as always, I would search for this question, but I dont know how to word it in a few words.  Basically, in my account on hardy heron Mozilla Firefox 3 Beta 5, a few websites do not load correctly.. They load fine on all my friends pc's and even on another account on my computer.  But, my explicit account renders it incorrectly.  Is there anything I can do to reset my Firefox back to how it was when I first started Hardy Heron? I tried uninstalling and reinstalling mozilla, but to no avail.

Thanks (as always),

Keith
ubuntu newcomer

---

### Post by leotemp on 2008-05-01
Thats seems odd, are you sure the sites just arent malformed with bad CSS or invalid markup, firefox tends to render sites better then most and if the designer built them using IE then theres a good chance they missed an error.

---

### Post by y-aji on 2008-05-01
I thought that was the case, initially, but my friend has firefox 3 beta 5 and says it renders just fine on his pc.. Also, I logged into my other account on the same computer, and it renders just fine.  It's an explicit problem on my account.. I thought maybe it was holding an old version of the site or something, but refreshed, cleared my history, cleared all my saved data, reloaded, and still, it looks the same.

---

### Post by y-aji on 2008-05-02
I have messed with it, extensively more.. And still to no avail.  I have realized that it's JUST the images that aren't loading.. The format positions of everything are there, but it's like it doesn't recognize images from my server.  

Is there a way to reset the image cache in linux or something to that effect?  I would assume that it could be some kind of image proxy issue. I've seen that the program "squid" can turn images upside down before delivering them to your pc to be assembled by your browser.. However, to my knowledge I dont run squid and would assume it wouldn't affect myself..  Does linux use anything like this by default?

This is driving me crazy.. I want to just delete and recreate my account, because I know that will fix it, but in trying to learn linux, I feel it very important to be able to fix stuff like this without having to reload accounts.. It would be very hard to talk one of my customers into using Linux if I had to remake their account all the time.

---

### Post by y-aji on 2008-05-20
To anyone that has this issue in the future. I found a simple solution.. (after a ridiculous amount of searching..)  

In Mozilla Firefox, goto Edit>Preferences>Content and search around for "Load Images Automatically" on that screen..
Make sure this is checked and then check the exceptions and see if the problematic site is listed.

I am unsure as to how, but my site was set to not load images for some reason..

I feel violated :o but i probably somehow did this to my own dumb self.

Thanks all for the replies.

---

