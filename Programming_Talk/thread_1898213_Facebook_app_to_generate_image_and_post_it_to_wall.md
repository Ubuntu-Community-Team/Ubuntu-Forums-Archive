---
title: "Facebook app to generate image and post it to wall"
date: 2011-12-20
forum: Programming Talk
---

### Post by RobikShrestha on 2011-12-20
For my facebook app, I need to generate an image. Most probably I will use html5 graph and I want to convert it to jpeg or other format through php. Only php gd library is supported by the server. 

How do I do that?

How do the existing facebook apps do that? i.e. generating an image in the server and posting it to user's wall

---

### Post by Zugzwang on 2011-12-21
So you want to describe a new image using HTML5 and render it to a PNG or JPEG? 

HTML rendering is a highly complex thing, so you will probably not have any support for this on the server unless you install additional libraries. It might be wiser if you use the gd library's functions directly to render your new image.

---

### Post by RobikShrestha on 2011-12-22
I just want to know how facebook apps generate images based on user statistics like no. of comments and post the pictures to walls.

I am thinking of generating html5 graph and then allowing users to choose whether or not to publish that graph. For publishing that graph, I need to convert it into image. May be I should do that in the client side but I do not know how to do it.

---

### Post by Zugzwang on 2011-12-22
> **RobikShrestha said:**
> I just want to know how facebook apps generate images based on user statistics like no. of comments and post the pictures to walls.


They will use the Facebook API provided to collect the information.

> 
I am thinking of generating html5 graph and then allowing users to choose whether or not to publish that graph. For publishing that graph, I need to convert it into image. May be I should do that in the client side but I do not know how to do it.

My comment above is still valid for this issue. If it think that it doesn't seem to answer your question, state why this is the case.

---

### Post by RobikShrestha on 2011-12-22
I am not saying your comment is invalid. I am just saying I do not know how to generate and publish images to facebook wall.

I have understood this: 

you are saying that I should learn gd library. Generate a graph using gd (in jpeg format). 

But after that what do I need to do to publish that image into user's walls? Do I need to save that image in the server and provide a hyperlink?? 

Please tell me what and how to do it? I have seen many other fb apps generating images and posting them in fb walls. I have learned the FB API but just can't GET the IMAGE thing!!

---

### Post by Zugzwang on 2011-12-22
So I have no clue about the Facebook API.

However, this is what I've found: [https://developers.facebook.com/docs/reference/api/post/](https://developers.facebook.com/docs/reference/api/post/) - There appears to be the option to add a picture to a post. Apparently, you will need to put the image somewhere on your own servers, and then link to that.

---

### Post by RobikShrestha on 2011-12-22
Thank You so much. I will read it and build the app. Thanks again!

---

