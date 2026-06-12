---
title: "any free webhosting with working cURL?"
date: 2011-03-06
forum: Programming Talk
---

### Post by sdowney717 on 2011-03-06
so far tried several, but they dont work.
What I mean is using cURL to retrieve data from the Library of Congress
So use a webservice to GET data, not be a webservice.

---

### Post by conradin on 2011-06-13
ugh, what? You want to use something to get data from the library of Congress. is that correct?
how about a google search using advanced search parameters for the specific site
look at:
[http://googlesystem.blogspot.com/2006/07/meaning-of-parameters-in-google-query.html](http://googlesystem.blogspot.com/2006/07/meaning-of-parameters-in-google-query.html)
 
using that, you could make a bash script to retrieve files. 


without more specif parameters for what youre looking for, I cant possibly write a script for you. Can you give more detail?

---

### Post by BkkBonanza on 2011-06-13
If you're looking for a free server that you can run a script on that uses curl to get data then you could look at [Amazon EC2]("http://aws.amazon.com/free/"). They have a first year free deal for the "micro" instance size that would get you a small server similar to a vps account. If you expect to use a lot of data transfer you may end up paying for that but it would have to be a huge amount to become significant.

Of course, on a EC2 server you can run whatever you want including curl. You can use an premade Ubuntu machine there and install whatever packages you need.

---

