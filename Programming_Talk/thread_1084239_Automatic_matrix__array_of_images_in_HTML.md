---
title: "Automatic matrix / array of images in HTML?"
date: 2009-03-01
forum: Programming Talk
---

### Post by QwUo173Hy on 2009-03-01
I have quite a few images in a folder, of the same dimensions. I want to make a 3 X 11 array on a webpage but all editors I've looked at will only make a table OR insert individual images. No array option.

Bluefish comes close but it generates thumbnails, which I don't want and doesn't put them in a table of any kind.

Is this possible without banging out all that code by hand?:confused:

Thanks,
Jarlath

---

### Post by cph05a on 2009-03-01
I can't think of anything using just html, but you could generate the html table from an array using javascript pretty easily.

---

### Post by rharriso on 2009-03-01
Is using php an option?.

I'm not sure if javascript lets you read files, something to do with security and whatever.

But if you are running this server side, you could just use php loop through all the files in the directory and create a table for all the images.

---

### Post by QwUo173Hy on 2009-03-03
I don't know javascript or php so I just did it the long way. It wasn't too painful actually. OpenOffice has a Block Select option that lets you truncate absolute paths over many lines of html simultaneously.

Thanks for your help folks.

---

