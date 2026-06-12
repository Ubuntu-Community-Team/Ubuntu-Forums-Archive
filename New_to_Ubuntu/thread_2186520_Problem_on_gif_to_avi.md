---
title: "Problem on gif to avi"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by Portaro on 2013-11-07
I have a script that convert Gif image on the same directory to an avi, I also used this script in past and works but now he dont work ->

there are this erros on terminal launching ->

> /home/joao/Novo/GIF_convert_to_AVI
convert: unable to open image `*.gif':  @ error/blob.c/OpenBlob/2587.
convert: missing an image filename `converted_image/converted%05d.jpg' @ **error/convert.c/ConvertImageCommand/3011.**
ffmpeg version 0.8.8-4:0.8.8-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Oct 22 2013 12:35:42 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
converted_image/converted%05d.jpg: No such file or directory


I also try use convert to make the job but the file dont work i have this errors on launching on terminal->
$**conver**t /home/joao/Novo/converted_image.gif /home/joao/Novo/**image.mpeg**


> convert /home/joao/Novo/converted_image.gif /home/joao/Novo/image.mpeg
**convert: delegate failed `"ffmpeg" -v -1 -mbd rd -trellis 2 -cmp 2 -subcmp 2 -g 300 -pass 1/2 -i "%M%%d.jpg" "%u.%m" 2> "%Z"' @ error/delegate.c/InvokeDelegate/1058.**


I need this script works because i need make the gif appear on the init of avideo .

What can i do?

Use ubuntu 12.04 with kernel 3.2, because ati catalyst for hd 2400 series dont work in the last bunstu.

I need solve this problem so please help.

---

### Post by Portaro on 2013-11-18
I find the problem, i need to  change the permission on this folder for some reason i need do permissions to group users on the folder and then works well.

---

