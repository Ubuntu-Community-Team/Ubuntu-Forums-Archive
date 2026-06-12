---
title: "Address Bar Search redirecting to Verizon"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by kari-kun on 2012-09-08
Hello all,

I know this is a common question, and I've searched the interwebs forever for a solution.

FIrstly, my internet provider is Verizon, and for whatever reason, even AFTER going through the **about:config** on my firefox and changed the **keyword.URL** to the Google search, I will still get redirected to the *[http://vrzc.search-help.net](http://vrzc.search-help.net)* site when I type a search keyword into the address bar. (NOT the search bar on the right side of the browser)

What's more is that when I navigate through the Verizon website to 'opt out', halfway through Firefox crashes because of certain scripts on Verizon Support, regardless of what I try to do.

I just recently have gone back to Ubuntu because Windows 7 was dying on me (about time). 

Now,  I haven't messed around with Linux since version 10, but I know how to  use simple terminal commands, and the like. This install was relatively  new, and I've barely gotten all my  documents, etc. from my old Windows moved over. I was just in the  process of installing the essential goods.

But this issue is driving me up a wall and any sort of help would be appreciated. Needless to say, my irritation toward Verizon is beyond measure at the moment...

---

### Post by cryptotheslow on 2012-09-08
I'm not sure this is of any help, but you are not alone with your Verizon woes. Someone else posted recently with the same issue:
[http://ubuntuforums.org/showthread.php?t=2051725](http://ubuntuforums.org/showthread.php?t=2051725)

---

### Post by kari-kun on 2012-09-08
> **cryptotheslow said:**
> I'm not sure this is of any help, but you are not alone with your Verizon woes. Someone else posted recently with the same issue:
[http://ubuntuforums.org/showthread.php?t=2051725](http://ubuntuforums.org/showthread.php?t=2051725)
  I actually stumbled across that thread a while ago. Unfortunately, it doesn't tell me what to do exactly to fix it... :( I *do *hope there's a work-around though.

---

### Post by cool110 on 2012-09-08
Verizon's DNS servers are redirecting you to their search page instead of returning NXDOMAIN.
Change your DNS settings to use Google public DNS (8.8.8.8 and 8.8.4.4) or Level 3 DNS (4.2.2.2 and 4.2.2.1).

---

