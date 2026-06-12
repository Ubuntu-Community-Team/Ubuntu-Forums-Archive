---
title: "Time to make Chrome Default Browser for Ubuntu"
date: 2010-05-25
forum: Recurring Discussions
---

### Post by WV2MJR on 2010-05-25
Time for Ubuntu to ditch FireFox as it's default Browser
 
 
[http://www.neowin.net/news/chrome-v50-released-stable-versions-for-mac-and-linux-included](http://www.neowin.net/news/chrome-v50-released-stable-versions-for-mac-and-linux-included)
 
"In its fastest iteration yet, Chrome, with its new V8 JavaScript engine improvements, boasts a 30% to 35% speed improvement over the last version"

---

### Post by colorlessprism on 2010-05-25
im not sure how i can help you...


[LIST]
[*]Chrome and Chromium are not the same thing. Chrome is a non-free  build of the Chromium project.
[/LIST]

[LIST]
[*]It is impossible to ship Google Chrome as a  default web browser without compromising licensing
[*]However we have a section in the software center where  people can opt-in to have things like Skype, Adobe Reader, and possibly  Google Chrome. 
[*]The  distribution models of Chromium and Ubuntu/Debian couldn’t be more  different, but since Evan Martin from upstream Chromium attended the  Ubuntu Development Summit we have begun to identify how we can make this  work. Expect more progress here in the future. 
[*]The switch to Chromium has ***only*** been identified as possible  choice on the Ubuntu Netbook Edition. 
[*]WE LOVE  FIREFOX. Mozilla is one of our most important upstreams and we will  continue to work with them as we have in the past.  Improving Chromium  in Ubuntu helps Firefox because they both believe that competition is  the best way to drive the web forward. For example we use CouchDB as our  default for “sqlless databases”, but work (or plan to work) with  MongoDB and Cassandra as well. We ship and integrate puppet by default  but that doesn’t stop us from making sure Chef is well supported. No  sane operating system vendor would want to artificially limit what  developers can do on their platform.
[/LIST]

---

### Post by WV2MJR on 2010-05-25
> **colorlessprism said:**
> im not sure how i can help you...
 

[LIST]
[*]Chrome and Chromium are not the same thing. Chrome is a non-free build of the Chromium project.
[/LIST]
[LIST]
[*]It is impossible to ship Google Chrome as a default web browser without compromising licensing
[*]However we have a section in the software center where people can opt-in to have things like Skype, Adobe Reader, and possibly Google Chrome.
[*]The distribution models of Chromium and Ubuntu/Debian couldn&#8217;t be more different, but since Evan Martin from upstream Chromium attended the Ubuntu Development Summit we have begun to identify how we can make this work. Expect more progress here in the future.
[*]The switch to Chromium has ***only*** been identified as possible choice on the Ubuntu Netbook Edition.
[*]WE LOVE FIREFOX. Mozilla is one of our most important upstreams and we will continue to work with them as we have in the past. Improving Chromium in Ubuntu helps Firefox because they both believe that competition is the best way to drive the web forward. For example we use CouchDB as our default for &#8220;sqlless databases&#8221;, but work (or plan to work) with MongoDB and Cassandra as well. We ship and integrate puppet by default but that doesn&#8217;t stop us from making sure Chef is well supported. No sane operating system vendor would want to artificially limit what developers can do on their platform.
[/LIST]
 
I heard that Windows 7 EU edition gives you the option to choose what browser to install [as it's default]. Is it possible for Ubuntu to do the same?

---

### Post by Elfy on 2010-05-25
moved to recurring discussions

---

### Post by jerenept on 2010-05-25
EPIPHANY if you want speed. It's Opensource and crazy fast.

---

### Post by lovinglinux on 2010-05-25
I disagree. Firefox is still a much better browser IMO. For me, the only advantage of Chrome would be the speed, which [I have serious doubts if it is really significant in the real world](http://lovinglinuxblog.blogspot.com/2010/05/browser-speed-test.html).

For users like me that like extensions (I have more than 50 installed), Chrome is not an option yet. Some popular Firefox extensions are already available for Chrome, but is not uncommon to be crippled versions. Besides, installing malicious extensions for Chrome is easier, due to how Google approaches the distribution of third-party extensions. Basically they are not reviewed by Google staff, while all hosted Firefox extensions are, including new versions of already approved extensions.

I have tried to develop some Chrome extensions, but it doesn't even allow me to install any of them. This possibly happens because Chrome is not playing well with KDE, but IMO is premature to think about including Chrome as default. Besides, Chrome is pushing Mozilla into making Firefox faster and better. Although Firefox javascript engine is not as fast as Chrome, Mozilla has managed to make it faster on every major release. They are also introducing new interesting features, like plugin process isolation, that prevents the browser from crashing if you try to view a bad flash video.

There is another thing to consider. Chrome is fast, but it lacks several features available in Firefox. Do you thing it will remain fast once it starts to grow and include new features?

---

### Post by colorlessprism on 2010-05-25
as i stated earlier, i will continue to use FF. it seems like i will try <insert new browser> and always come back to FF. put all the browsers in the repos, 'cause i will continue to try whats new (hey thats how i found Firefox many years ago), but nothing has been proven over and over like firefox. 

if you think about it, we want a distro "that works" and to do that we cannot put things in by default that do not even fit the same licensing or model of ubuntu let alone debian. we have quality software because of standards, if we throw anything and everything into the mix you get <insert lame OS here>. 

linux is like legos, everyone builds the picture on the box, but eventually you decide you want to it be different, to be better. by customizing your lego creation it is exactly what* you* want, but may not be what *i* want. a typical user may not even *want *to change his legos, he may be happy having a creation that works just like the box said it would.

all the linux community wants is to create a really good, fully-featured, free operating system. if that means ubuntu becoming the most popular OS, then that's great. if that means ubuntu has the most intuitive, user-friendly interface ever created, then that's great, but you can have neither without test cases, and i haven't seen one on chrome/chromium.

---

