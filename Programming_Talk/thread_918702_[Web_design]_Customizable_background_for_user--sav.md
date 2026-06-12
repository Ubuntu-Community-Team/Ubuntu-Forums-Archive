---
title: "[Web design] Customizable background for user--saved as cookie or something..."
date: 2008-09-13
forum: Programming Talk
---

### Post by fiddler616 on 2008-09-13
Hello,
I've been scouring Google for a while now, and can't seem to find anything.
Here's the question:
For a given webpage, is it possible to have a--a *thing* where the user can upload a photo--either URL or saved on their computer, pick center/stretch/tile, and then have that be the background on the website they're on.
Obviously, this wouldn't be a good idea for normal webpages, but for stuff like [this]("http://www.andrewmin.com/webx"), it would be quite handy.
And the image would be saved (as a cookie?) on the user's computer, not on the server.
Is this possible/doable? Or am I just crazy? (Probably it's both, but...)
Thanks

---

### Post by Reiger on 2008-09-13
Yes it is: both JavaScript *and* PHP (or any decent CGI language should for that matter) offer you the capability to set a value in a cookie. So that is done easily enough: have a file-upload form which covertly doesn't upload but adjusts cookies using a JavaScript event handler or just a call to your cgi script...

In JavaScript it appears to be very easy: [http://www.quirksmode.org/js/cookies.html](http://www.quirksmode.org/js/cookies.html)
(Google JavaScript Cookie)
In PHP it's also very easy: [http://nl2.php.net/setcookie](http://nl2.php.net/setcookie)
(Google PHP Cookie)

---

