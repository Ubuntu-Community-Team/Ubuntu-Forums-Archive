---
title: "Adobe Reader in Ubuntu 12.04"
date: 2012-07-31
forum: New to Ubuntu
---

### Post by Ditchdoc7893 on 2012-07-31
Hello. Most recently I have been using both 10.04 and 10.10 and have been able to easily install Adobe Reader 9 from either the software center or via synaptic. I have not been able to successfully find it in either place with 12.04. Does anyone have a solution to install Adobe Reader in 12.04? Thanks!

Ryan

---

### Post by yuvraj23 on 2012-07-31
Its there at software centre. Try to update your system first

---

### Post by Ditchdoc7893 on 2012-07-31
I have tried but I actually just posted another post with the error message that I get when I attempt to update the system. When I run from a terminal sudo apt-get update, I receive the following message:

E: Malformedline 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

When I try to update by going to the Update Manager, I receive the error:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 60 in source list /etc/apt/sources.list (dist parse)'

Any ideas? Thanks.

---

### Post by blueshead on 2012-07-31
This worked for me..

[http://www.techheadz.co.uk/222.html]("http://www.techheadz.co.uk/222.html")

---

### Post by Ditchdoc7893 on 2012-07-31
I am returned the following error:

Error: 'deb [http://archive.canonical.com/precisepartner](http://archive.canonical.com/precisepartner)' invalid

---

### Post by Ditchdoc7893 on 2012-08-01
After correcting my sources.list file in /etc/apt I was able to update my system. After this, I was able to install Adobe Reader 9 using sudo apt-get install acroread

I will mark this post solved.

---

