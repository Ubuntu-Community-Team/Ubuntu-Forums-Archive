---
title: "troubleshooting the css and html of a given web page"
date: 2014-07-22
forum: New to Ubuntu
---

### Post by Drone4four on 2014-07-22
Here is my test case:  [http://www.angeles4four.info/New_look_layouts-mine_TESTCASE/final/](http://www.angeles4four.info/New_look_layouts-mine_TESTCASE/final/)  The html and css can be viewed using the view source feature in your browser.

I got the template out of a magazine and I am now fiddling with the code.   

I am troubleshooting the css. 

I figure I have to find the right selector and input this property and value: ```
text-shadow: 1px 1px 1px rgba(0,0,0,0.8);
```  There are multiple instances of that declaration through out my style sheet.  I've tried adjusting those values without noticing a change.  How do I add a shadow effect to the paragraph elements on top of the images?

I feel embarrassed for being unable to understand what I am trying to do.

I am running Ubuntu 12.04 LTS on my digitalocean droplet.

---

### Post by slooksterpsv on 2014-07-22
You only want to adjust the x and y value, the z value adjusts for blurriness e.g.

text-shadow: **x**px **y**px **z**px rgba(red, blue, green, alpha);

Try looking under and article tag ;-) in a **paragraph** block. Hope that helps.

---

