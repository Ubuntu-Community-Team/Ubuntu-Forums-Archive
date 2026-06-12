---
title: "questions from a brand-noob"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by Lammaslehto on 2011-11-19
Hi, I bought a refurbished computer from FreeGeek in Portland Oregon that was already outfitted with Ubuntu. I like the idea of keeping it and learning how to use it and being open source and stuff...but I am lost lost lost. 

Can somebody please help me with
1) finding a driver for my printer/scanner which is a brother mfc-j410w, and tell me how on earth to install it and what program I need to use to scan images? 

and also

2) i am an illustrator and I was using photoshop to  clean up and resize my images. GIMP is similar, right? or is there something better I should look at. and

3) how do I get flash videos to play. 


thank you so much. I heard that this forum was a helpful place to come.

---

### Post by poloshiao on 2011-11-19
> 1) finding a driver for my printer/scanner which is a brother mfc-j410w,  
and tell me how on earth to install it and what program I need to use  to scan images? 

Take a look at this post
[brother mfc-j410w any more suggestion on how to get my printer to work?]("https://answers.launchpad.net/ubuntu/+source/cups/+question/133980") #7

> 2) i am an illustrator and I was using photoshop to clean up and resize my images. GIMP is similar, right? or is there something better I should look at. 
[11 Photos and Graphics]("http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Photos_and_Graphics")

> 3) how do I get flash videos to play. 
[15 Audio / Video conversion]("http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Audio_.2F_Video_conversion")

---

### Post by Miljet on 2011-11-19
> 3) how do I get flash videos to play. 
The Ubuntu-restricted-extras package. It will pull in a lot of libraries and programs that allow you to watch flash videos, play audio CDs, movies on DVD, and lots more essential stuff.

I didn't see what version Ubuntu you have installed so it would be hard to give exact directions. If your version has Synaptic Package Manager, you can find it at System -> Administration -> Synaptic Package Manager. Or you can search the Software Center. Or in any case you can open a terminal and type (or copy and paste) the following, one at a time.
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

