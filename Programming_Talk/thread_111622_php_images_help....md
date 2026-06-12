---
title: "php images help..."
date: 2006-01-02
forum: Programming Talk
---

### Post by grim918 on 2006-01-02
im having a small problem with displaying images. when i use the <img> tag to display images, sometimes they wont load when i try to view the page.
i was wondering if images or the directory that they are in need to have permissions set so that the images will load. here is an example of something that i tried:

i created an images directory and i put a picture in there image_name.gif
then i created a copy of that same picture and put it in the same directory but i renamed the picture to 001.gif. here is how i did this

sudo cp /images/image_name.gif /images/001.gif

then i check to see if the picture is in the directory and yes it is.

i then create a simple html page to display the images.
<img src="/images/image_name.gif" />
<img src="/images/001.gif" />

this is where i run into a problem. image_name.gif will load and display on the browser but 001.gif will not load. does anyone know what is going on here

---

### Post by Neeko on 2006-01-02
Are the permissions the same on each file? The web server needs read permissions (I think). Open a term window and do:
```
ls -la
``` and compare group permissions.

---

### Post by grim918 on 2006-01-02
yes the read permissions on the files are the same. i chmod 644 the files so that they have read permissions. i just dont know why the copied picture wont load and the other one is ok. i get this problem with many other images that i try to display.

---

### Post by Neeko on 2006-01-02
Have you tried emptying your browser cache before loading the page?

---

### Post by grim918 on 2006-01-03
how do i empty the browser cache before loading the page. i dont know how to do that.

---

### Post by Swab on 2006-01-03
[QUOTE=grim918]how do i empty the browser cache before loading the page. i dont know how to do that.[/QUOTE]

If you are using firefox, click on the edit menu > preferences > privacy ... then click the clear cache button.

---

### Post by kperkins on 2006-01-03
try ***not*** using sudo to copy the file.  If you use sudo to cp it, then root owns it, and not the user (you) who originally put it in the folder.
I just tried this and even sudo cp'ing I could see the both pics, so now I'm at a loss, myself.  I can't figure what the problem could be, even though it does sound like a permissions issue. Of course I did this on my own comp, a webserver might not let you read files ownd by root if your not in the group.

Are you doing this on your own computer, or a web server?  Is there an .htaccess file in the folder?  That's all I've got.

---

### Post by grim918 on 2006-01-03
i am in the /var/www/ directory so i cant copy a file in here unless i use sudo. unless there is another way of doing it that i dont know of. i am going to try the  empty cache idea though. ill see how it goes. it really does sound like a permissions problem though. i cant find anything on the web on it though.

---

### Post by grim918 on 2006-01-06
i dont know what happend but i just left off this subject while i worked on other parts of my website. when i came back to it, it was working. i dont know what happend but im glad it now works. thanks for the help. problem solved.

---

