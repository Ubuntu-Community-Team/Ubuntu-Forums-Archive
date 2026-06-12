---
title: "PHP session_start() problem"
date: 2007-01-26
forum: Programming Talk
---

### Post by Kintwa on 2007-01-26
Hi,

I just finished installing a LAMP server from the Ubuntu server CD. I have everything set up and running just right. However, when I try to call the php function, "session_start()", the page will not load. No error messages are outputed, however the browser will continue to show that the page is loading. The effect is similar to creating an infinite loop.

The code that I am using is from another server, where it works fine. I have made no changes to it. If I comment out the session_start() function, the page loads normally (but without sessions).

Anyone have any suggestions on how to fix this?

Thanks

---

### Post by kidders on 2007-01-26
Hi there,

What happens if you try to get PHP to do something more basic, like maybe...

```
<?php
session_start();
if (!isset($_SESSION['hello'])) $_SESSION['hello']=1;
else $_SESSION['hello']++;
die("Visited {$_SESSION['hello']} times.");
?>
```

Also, it's worth asking if you're using the same version of PHP on both servers.

I suppose the most important detail is what exactly is going on... a page might take forever to load because the server is just sitting there, but on the other hand, your browser might be stuck in in an infinite redirect loop.

---

### Post by Kintwa on 2007-01-26
Hi - I just concluded that the function session_start() is not causing the pages to not load. I made some adjustments and now many pages load correctly and fine. However, once I view a few pages, everything stops again. Then the browser will not load any page after that.

I must restart the entire server to get it back to where I can view a few pages before it happens again. Restarting apache does not work.

I have no idea what to do next...

---

### Post by phossal on 2007-01-26
It's likely you have a coding error. Firefox is very good (or bad) about recognizing infinite redirects, and similar errors. If you're loading the session with a lot of variables, you might look for conflicts. You might also consider the *path* you're taking between the *few* pages you say you're able to view. You can usually isolate the problem to a few sections of code based on those simple observations.

---

### Post by kidders on 2007-01-26
Hey again,

It's difficult to know what's going on without a little more detail. :-(

What do the scripts you're running do?
Is it good-quality code?
Was it written for the version of PHP you are running?
Is there anything else involved, such as filesystem/database/network interaction?

Also, when your server appears to lock up, are there any clues about what it might be doing? From your description, it sounds as though a script may be getting trapped in an infinite loop of some sort, eating up your resources to the point where the web server can't function any more.

Can you post some of the problem code, or maybe some of the tweaks you've made to get your session management working?

---

### Post by Kintwa on 2007-01-26
Thanks for the replies!

I just ran a memory test on my RAM. Apparently I have bad RAM. I replaced the faulty stick with another, and everything is running great!

Thanks!

---

