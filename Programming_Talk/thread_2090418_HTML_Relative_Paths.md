---
title: "HTML Relative Paths"
date: 2012-12-02
forum: Programming Talk
---

### Post by DBQ on 2012-12-02
Hi Everybody.

I made a website. The website consists of the root folder and a subfolder called images. 

In my html files (residing in the root directory) I specify the image paths as e.g. <img src="images/someimage.jpg">.

The images show up just fine on my local computer, but they fail to show up when I uploaded them to the server. The server is running Linux.

When, on the server, I move the images to the root directory and change image tags to e.g. <img src="someimage.jpg">, the images show up, just fine.

Can somebody explain why?

Thank You!

---

### Post by TheFu on 2012-12-02
Which web server?  The DocumentRoot and Directory settings in the config file might help if this is apache2
I'd try <img src="/images/someimage.jpg"> in the meantime.

---

### Post by DBQ on 2012-12-02
Thanks for the reply.

I tried using /images/img.jpg, without success.

The server is apache.

I do not have access to the server settings.

---

### Post by marin123 on 2012-12-02
> **DBQ said:**
> Thanks for the reply.

I tried using /images/img.jpg, without success.

The server is apache.

I do not have access to the server settings.

You need to set permissions to images folder and files inside it.

Get to root directory with cd and type
```
sudo chmod -R 755 images
```That should do the trick.

---

### Post by SeijiSensei on 2012-12-02
What do you see if you access http://your.server/images/?

What about http://your.server/images/someimage.jpg?

---

### Post by TheFu on 2012-12-02
You should be able to "see" the settings.  THAT would be a help so you know the document root and directories.  I can see where that information would be provided in a FAQ for the hosting provider.

I always get an ssh shell account for any webhosts that I use so I can see all the settings and more easily manage permissions.  Some hosts require a photo ID scan be provided to get ssh access.

---

### Post by DBQ on 2012-12-02
Changing the permissions helped!

Thank you so much!

---

