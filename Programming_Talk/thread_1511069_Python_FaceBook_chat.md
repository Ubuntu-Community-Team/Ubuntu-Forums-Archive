---
title: "Python: FaceBook chat"
date: 2010-06-16
forum: Programming Talk
---

### Post by chevloschelios on 2010-06-16
Hello

Can you help me? I want to connect my Python Bot to Facebook chat, but i dont know how.

Thank you.

---

### Post by ja660k on 2010-06-16
grrr i wish i wasnt at uni, i want to make an fb chat client too...
there is an open source mac app "adium" it has fb chat... if you dont mind sifting though objective-c code... here is the source...
[http://trac.adium.im/wiki/GettingNewestAdiumSource](http://trac.adium.im/wiki/GettingNewestAdiumSource)

---

### Post by chevloschelios on 2010-06-18
anything else ?

---

### Post by NoBugs! on 2010-06-18
Pidgin has a facebook extension:
[http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/)

---

### Post by chevloschelios on 2010-06-19
but i need python Bot or python facebook status updater.

---

### Post by ja660k on 2010-06-19
okay, so for chat, there is no real set API to send messages and get buddy lists and stuff, so you'll have to do some 1337 haxing

basically any fb chat client does something like this...
[http://github.com/coderrr/facebook_chat/blob/master/chat.rb](http://github.com/coderrr/facebook_chat/blob/master/chat.rb)
that one is in ruby, but that 'mechanize' module is available for python too.

---

### Post by chevloschelios on 2010-06-19
thank you i m going to try it.

---

### Post by ja660k on 2010-06-19
i should add that his blog post
[http://coderrr.wordpress.com/2008/05/06/facebook-chat-api/](http://coderrr.wordpress.com/2008/05/06/facebook-chat-api/)

sort gives method and an explanation for whats going on

---

### Post by chevloschelios on 2010-06-19
I dont understand this Ruby code. Have you got some Python code ??? I just want know how to start.. i find the module pyfacebook but I cant use it

---

### Post by chevloschelios on 2010-06-20
I wrote to my friend - Python Programmer and he said that the best is to use the socket library, but I cant connect python to Facebook. Any solution now ?

---

### Post by ja660k on 2010-06-20
yes... and i believe if you look at the code of the 'mechanize' or urllib code, it will be using sockets...

why reinvent the wheel writing your own socket communication when you can use a module that does it already?

---

### Post by soltanis on 2010-06-21
The Facebook API is mainly served through web pages. You should use urllib.

[http://wiki.developers.facebook.com/index.php/Integrating_with_Facebook_Chat](http://wiki.developers.facebook.com/index.php/Integrating_with_Facebook_Chat)

---

### Post by SledgeHammer_999 on 2010-06-22
Facebook supports chat through the Jabber(xmpp) protocol. It was recently added.
There should be a python library that implements the xmpp protocol. Search for that in google.

---

### Post by chevloschelios on 2010-06-24
I found som Python code. I tried it but it didnt work. Can you try it ? Here is code : [http://omouse.vox.com/library/post/updating-facebook-status-using-python.html](http://omouse.vox.com/library/post/updating-facebook-status-using-python.html)

---

