---
title: "PHP capture"
date: 2010-07-13
forum: Programming Talk
---

### Post by sheffrem on 2010-07-13
Hi guys, i have this small school project on linux to do but im in need of help. Im writing a php code that will help me capture test result from [www.speedtest.net](www.speedtest.net). what this site does is to test your internet connection. i want to write a script to auto start the test and output the result in a text file. Im not asking to do my homework but just need guidance.
What is the best approach to take. Pls help as im a bit confused.
Thanks in advance.

---

### Post by collinge on 2010-07-13
Hey, not sure about the php output, but I did some research. 

Try this stuff 

[http://www.opensourcetesting.org/performance.php]("http://www.opensourcetesting.org/performance.php")

[http://microsoft_rules.ubuntuforums.org/showthread.php?t=308040](http://microsoft_rules.ubuntuforums.org/showthread.php?t=308040)

good luck

---

### Post by Hellkeepa on 2010-07-14
HELLo!

**sheffrem**: You do realize that speedtest.net uses Flash to test with, right? Which means that you'll have to have your PHP code be able to execute the flash code, and then capture whatever it outputs.
I'd go with the links **collinge** posted, unless you want to try to implement a flash player in PHP.

Happy codin'!

---

### Post by sheffrem on 2010-07-14
Thank you very much for your helps.So what language is best suited for this job ? any idea will be welcomed.:D

---

### Post by sheffrem on 2010-07-14
Thank you very much for your helps.So what language is best suited for this job ? any idea will be welcomed.:D

---

### Post by sarim on 2010-07-14
hi,

I think Implementing flash in php will be a very hard thing as i feel it's impossible.
You can use another website that can test without flash.

May be libcurl module of php can help.

---

