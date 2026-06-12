---
title: "Photo storage and MySQL with web interface"
date: 2009-07-10
forum: Programming Talk
---

### Post by adelgado on 2009-07-10
Hello, everyone

I am currently developing a system that enables users to upload photos. I'd have a way for them to view the photos too.

I'm using MySQL as the database and a web-based interface.

I'll only access specific sizes of the photos, i.e., I'll only need them in 500x250, 200x100 or 100x50.

I an wondering how should I structure this:

Should I save the images in a BLOB field or should I save their filename on the DB and store them somewhere else?
If I store them on the DB, how can I work out for them to have a permanent link?
Should I resize them to various sizes upon upload and store those or should I resize them on-the-fly according to the size I need?


Thank you in advance for any suggestions!

---

### Post by smartbei on 2009-07-10
Hmmm.... Good questions. I think it depends a lot on what kind of use you are expecting. Are there going to be thousands of uploaded pictures, but relatively few downloads-per picture? Or maybe a small amount of pictures, but several of them will be requested very often.

If you are expecting tons of downloads, maybe you will want to resize your pictures in advance, and only store meta-information in the DB. Otherwise, for easier organization and backup, it might be fine to keep all of the data in the database.

Regardless, you can have a permanent link be whatever you want it to be - I would suggest an id in the databae, since that is the easiest to implement. So the permanent link would look like this: http://<your_website>/photo.php?id=12345

---

### Post by Wim Sturkenboom on 2009-07-10
I don't know if it's the best way, but I would NOT store the photos in the DB.

I don't understand what you mean by '*I only need them in 500x250, ...*'. I suppose that that is the options that the user have to view their pictures in. And what do you mean by 'resize on-the-fly'? Let the server do the resizing or let the browser do the resizing?

If you're considering the browser to do the resizing by means of the  HTML image tag, be aware of some (potential) issues.
[LIST=1]
[*]If the size of the photo is e.g. in a 3:2 ratio and you let the browser resize it to 2:1, it will be deformed.
[*]This is a small problem compared to the fact that the user can upload e.g a 5 megabyte picture and every time it is viewed, the full picture will be loaded by the browser before it will be resized.
[/LIST]
So in my eyes that option is out. And I don't know if a PHP script can resize the photos on-the-fly (you still have the deformation problem).

Hope this helps.

---

### Post by adelgado on 2009-07-10
Hello, smartbei

There will likely be thousands of unique pictures (that is, not counting the resized versions). They will be requested quite often.

So maybe the best way is to keep the filename on the database and the files in some other place.

I will need a good naming scheme to rename the files, as most of the files will be uploaded with names such as 'me2.jpg' and 'DSC-something.jpg'.

I think I'll use one folder and keep the file sizes on its name rather than using a folder for each size.

I was thinking somthing like user_id-md5(oldname)-height_in_pixels.jpg

Ex. 55-c847c4fcd841fc56b4915e466ab50522-220.jpg

That ought to be random enough...


Thank you for your help!

---

### Post by adelgado on 2009-07-10
Hello, Wim

> **Wim Sturkenboom said:**
> I don't know if it's the best way, but I would NOT store the photos in the DB.

I don't understand what you mean by '*I only need them in 500x250, ...*'. I suppose that that is the options that the user have to view their pictures in.

That's correct.

> And what do you mean by 'resize on-the-fly'? Let the server do the resizing or let the browser do the resizing?

I was talking about any of them. Probably the server, as this would reduce bandwidth. But I'll probably store resized versions, anyway.

> If you're considering the browser to do the resizing by means of the  HTML image tag, be aware of some (potential) issues.
[LIST=1]
[*]If the size of the photo is e.g. in a 3:2 ratio and you let the browser resize it to 2:1, it will be deformed.
[*]This is a small problem compared to the fact that the user can upload e.g a 5 megabyte picture and every time it is viewed, the full picture will be loaded by the browser before it will be resized.
[/LIST]
So in my eyes that option is out. And I don't know if a PHP script can resize the photos on-the-fly (you still have the deformation problem).

Hope this helps.

The photo's ratio will be carefully controlled, so I don't think it will be a problem. Thank you for bringing that up.

The full picture download is exactly what sent me away from resizing on the client.

I don't know if a PHP script can resize images on the fly either, but I use Lua anyway; and no, I don't know if it can resize images on the fly, neither. haha


This was helpful :)

---

### Post by Mirge on 2009-07-10
PHP with the GD library can easily manipulating images.

[http://www.vipercreations.com/tutorials/PHP/22/](http://www.vipercreations.com/tutorials/PHP/22/) is one example. Several other examples here: [http://www.google.com/#hl=en&q=resize+images+with+PHP&aq=f&oq=&aqi=&fp=aazfVjAAjGM](http://www.google.com/#hl=en&q=resize+images+with+PHP&aq=f&oq=&aqi=&fp=aazfVjAAjGM)

---

