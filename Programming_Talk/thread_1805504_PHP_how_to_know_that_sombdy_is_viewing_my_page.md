---
title: "PHP: how to know that sombdy is viewing my page?"
date: 2011-07-16
forum: Programming Talk
---

### Post by honeybear on 2011-07-16
Hello,

I have a code for a notepad online, and I would like to know is sombdy is still being seeing the webpage to know if I can work and update the page. 

I know how to check the IP of the person, but how to know that he is gone and not seeing or working on the webpage?

Any hints are welcome

---

### Post by mikejonesey on 2011-07-16
all webstats are based upon the next request, they don't actually checkwhen the user is browsing a page or not, if you wanted you could acomplish this using ajax but I think you may break some privacy rules...

to set this up you would have a ping like script in the ajax (running every few secs), then the php page being requested would update the database with info to state the webpage is being accessed by ...ip

---

### Post by conradin on 2011-07-16
I think the std method is to write a cookie to that persons computer and update the cookie frequently, then send the cookie data back when they navigate away. or something like that.

---

