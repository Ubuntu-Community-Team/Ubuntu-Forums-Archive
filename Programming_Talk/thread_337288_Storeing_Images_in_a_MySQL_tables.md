---
title: "Storeing Images in a MySQL tables"
date: 2007-01-12
forum: Programming Talk
---

### Post by apjone on 2007-01-12
Can any one please explain how to store an image within a mysql table please. I have read some info, but can not figure it out.

thx

AJ

---

### Post by jblebrun on 2007-01-12
> **apjone said:**
> Can any one please explain how to store an image within a mysql table please. I have read some info, but can not figure it out.

thx

AJ

I believe that you want a field of type BLOB (if I remember correctly.) Then you can store whatever you what in there.

Why do you want to store images directly in the database? Why not keep them in a directory somewhere, and just store references to the filename, instead?

---

### Post by apjone on 2007-01-12
> **jblebrun said:**
> I believe that you want a field of type BLOB (if I remember correctly.) Then you can store whatever you what in there.

Why do you want to store images directly in the database? Why not keep them in a directory somewhere, and just store references to the filename, instead?

Just curios ,  it just bugs me when i cant get something working. lol . 

Thanks mate

AJ

---

### Post by jblebrun on 2007-01-12
> **apjone said:**
> Just curios ,  it just bugs me when i cant get something working. lol . 

Thanks mate

AJ

Ok, well, the field type BLOB (binary large object) lets you store arbitrary binary data (like an image) in the table.

---

### Post by gpolo on 2007-01-12
if you really want to store images in database, I would recommend storing thumbnails of them. And maybe the path to the original image

---

### Post by g8m on 2007-01-13
I have written an application for my dvd collection, which uses mysql.

This runs on a server. I want to be able to see dvd information, which contains the cover 
on my labtop. In my current situation I mount a network share to display the
dvd covers. And I don't like that. It's to complicated. Serving the information
and the images via mysql would be much easier. Now I depend on mysql and
samba for it to run. 

My only reason not to do it through mysql now are my doubts about mysql being
able to serve those images. The images vary from 500kb to 20mb in size.

Would it be feasable to store the images in mysql?

---

### Post by gpolo on 2007-01-13
dvd covers = 500kb to 20mb ? what ?

---

### Post by g8m on 2007-01-13
> **gpolo said:**
> dvd covers = 500kb to 20mb ? what ?

I am not so good in explaining it in english. But I will try. 

I have scanned the covers of my dvd's and stored them on my harddisk as jpg-images.
These images use some space on the harddisk. I think the units for storage is kb (kilobyte)
or mb (megabyte) where 1024 kilobytes is 1 megabyte. I compressed most images
under 1 megabyte. All images are using 330Mb total diskspace.

---

### Post by gpolo on 2007-01-13
ok, i understood now. what are the sizes of these images ? 1mb is a big image. 
So, do you need to store the images in this big size ? It seems too big to be a dvd cover image.

What will you use to add and later show these things ? Are you doing it in PHP ? 
A desktop program ? 

Like I said before, you can scale down all these images automatically before inserting in the mysql table.

---

### Post by g8m on 2007-01-13
I am using C++ with the qt4 libraries.

Yes I know I can compress the images even further, but I opt for quality. Even now if I select a row with a big image, it takes a few seconds to render and display it. 

I accept performance loss, and will accept a 2 second delay for browsing the dvd's.

example [http://img156.imagevenue.com/img.php?image=14511_archief02_122_307lo.jpg](http://img156.imagevenue.com/img.php?image=14511_archief02_122_307lo.jpg)

---

### Post by gpolo on 2007-01-13
1mb for a jpg image of that size is too much, the last tip I could tell you is that you should keep those images in a separate table and all the other data in other table

---

### Post by tribaal on 2007-01-13
If you really want to opt for quality then I guess you should then have only the filename in the database, and store your large file on the filesystem.
Remember that the linux filesystem will be much faster to access than a blob this big.

If you really want to go for the blob option, you better put the image in a separate table (only id and picture fields), like gpolo said it should speed up the whole thing a little bit.

For smaller images (50-100k max) I think it's a possible solution to store images in a database, but in your case I'd really go for the filesystem option.

Hope this helps at all :)

- trib'

---

### Post by winch on 2007-01-13
> **tribaal said:**
> If you really want to opt for quality then I guess you should then have only the filename in the database, and store your large file on the filesystem.

You also need a mechanism to transmit the file from the server to the client. Http would be one option.

---

### Post by g8m on 2007-01-13
I have considered http. I run apache on the server. But I don't know how display it in qt and the second problem would of course be how to upload the images to the server. In my current configuration i can drag an image and drop it into the application.

---

### Post by maddog39 on 2007-01-14
I believe phpMyAdmin has an option when creating tables called like external_type or something like that and you can specify a mimetype for the data that will go in there.

---

### Post by eteran on 2007-01-14
Storing Images directly to the Database is not recommended in General.
You'd better just place a relative or absolute path to the image in the Database.

Considering the size of your application and the resulting database as small, it should be ok to store them in the db. But thats not a good concept.

You might also consider using [sqlite](http://sqlite.org) instead of mysql for your application.

---

