---
title: "Beginner Web Development Question"
date: 2009-08-04
forum: Programming Talk
---

### Post by element13 on 2009-08-04
Hey, I don't know if this is the right place to post for an HTML question, so if not I'm sorry.  

So usually I do my web development in Windows, and I'm actually pretty decent at it so I feel kind of dumb asking this.  Anyhow, my internet was going way slow and I figured Ubuntu might be faster, turns out it's just my apartments braodband is sucking for the time being and it's taking 30+ seconds to load any web page.  Anyhow, I copied over my entire folder that I'm working on, but for some reason the images no longer show up.  I'm viewing it in Firefox, the images are in a subdirectory called Images.  The code looks like this:

<img src="images/logo.png"> 
<img src="images/webDesigner.png" class="firstImg"> 
<img src="images/databaseEngineer.png" class="secondImg" > 
<img src="images/EBusinessConsultant.png" class="thirdImg">

It worked perfectly in windows, now I'm getting nothing.  I'm not too familiar with Ubuntu, maybe I have to do the image path different?  Any help would be appreciated, thanks!

---

### Post by bvanaerde on 2009-08-04
Make sure you're not using caps for the folder.
There's a big difference between
> images
and
> Images

---

### Post by element13 on 2009-08-04
Thanks, that solved it.  I didn't realize Ubuntu was case sensitive :)

---

### Post by Wim Sturkenboom on 2009-08-04
Any Linux/Unix is :)

---

### Post by slaiyer on 2009-08-04
which is good practise especially if you are going to host your site on a unix/linux server. save you alot of head ache.

---

