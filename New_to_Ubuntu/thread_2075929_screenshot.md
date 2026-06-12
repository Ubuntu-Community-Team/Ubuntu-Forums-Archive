---
title: "screenshot"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by offgridguy on 2012-10-24
Hello;  How do I get a screenshot to thumbnail size, to post in this forum. I have tried shrinking it, then save, but it doesn't come in as a thumbnail when i paste it here.
Any help gratefully appreciated.

---

### Post by wojox on 2012-10-24
I install imagemagick:
```
sudo apt-get update; sudo apt-get install imagemagick
```
Then shrink it with:
```
convert -resize 150x150 screeshot.png thumbnail-screenshot.png
```

---

### Post by offgridguy on 2012-10-25
Thank you for the reply; I tried this but it doesn't seem to want to work for me, it says configuring 
but nothing seems to be happening, how long should it take?

---

### Post by lisati on 2012-10-25
Another option is to upload the screenshot as an attachment, using the "Manage attachment" button below the editor when you're composing a post.

---

### Post by wojox on 2012-10-25
What's configuring offgridguy? The install or conversion? The conversion should be instantaneous. Did you move into the directory the original screenshot is in? Also change screeshot.png to the name of your image and extension.

---

### Post by wojox on 2012-10-25
> **lisati said:**
> Another option is to upload the screenshot as an attachment, using the "Manage attachment" button below the editor when you're composing a post.

+1 much easier.

---

### Post by offgridguy on 2012-10-25
> **wojox said:**
> What's configuring offgridguy? The install or conversion? The conversion should be instantaneous. Did you move into the directory the original screenshot is in? Also change screeshot.png to the name of your image and extension.
The install, it doesn't seem to have installed, can't tell if it has even downloaded
completely .
> 
Another option is to upload the screenshot as an attachment, using the  "Manage attachment" button below the editor when you're composing a  post. 

Thank you lisati, i will try this.  I  won't be able to do anything until later this evening
though, due to job commitments.

---

### Post by offgridguy on 2012-10-25
[attach]226109[/attach]
Works like a charm , thank's again lisati  
So then this looks like i have one primary partition and the 2 smaller ones are inside it.
Would that be correct? Or is it 2 partitions the 2 small ones being in the same partition ?

---

