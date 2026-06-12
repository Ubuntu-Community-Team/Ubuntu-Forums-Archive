---
title: "Setting up my server"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by moose4204l on 2008-08-06
Ok, I just installed all of the Server CD. I want to know how to set it up to be able to stream videos from it. Thanks!

---

### Post by moose4204l on 2008-08-07
bump

---

### Post by AdamWood on 2008-08-07
What type of videos are you planning to stream?
Do you know which software you'll be using to do the streaming?
How about the client that will be receiving the stream?

---

### Post by moose4204l on 2008-08-07
no i do not. All i know is i have the Ubuntu server cd installed and I want to stream my ripped DVDs so I can watch them from another ubuntu laptop either in another room or at my girlfriends house. Also, I might set up a youtube type server for a friends small business without all the bells and whistle youtube has. my main goal as of now is just to get streaming dvds.

---

### Post by Dr Small on 2008-08-07
You can use VLC to do the streaming, and VLC on the clients end to watch the stream.

---

### Post by hyper_ch on 2008-08-07
either install samba server and make the server available on the network or use nfs or use sshfs :)

If you need to also share with windows computers, use samba.

---

### Post by AdamWood on 2008-08-07
If you're going to connecting from a Windows machine then choose SAMBA over NFS.

You don't need a lot of software to "stream" dvds. Just a file server so you can get to the ripped ISO. NFS is perfect and easy to set up if you only plan to use Linux for everything, otherwise if there is a mix or a chance of adding windows in the future then take an extra 15 mins to set up SAMBA. There's loads of guides on the web but just ask again if you need help.

---

### Post by moose4204l on 2008-08-07
how do i get the server running. what do i need to do and how do i do it. sort of a step by step starting after installation if you can

---

### Post by hyper_ch on 2008-08-07
there are many howtos on that....

---

### Post by tamoneya on 2008-08-07
> **moose4204l said:**
> how do i get the server running. what do i need to do and how do i do it. sort of a step by step starting after installation if you can

hope this helps: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by moose4204l on 2008-08-09
basically, i want to be able to go to a webpage thats on my server, from any computer, and be able to browse and stream the videos from there. How do i do that. I checked how-to's and i am confused. Need a bunch of help

---

### Post by tamoneya on 2008-08-09
okay if you want webpages you need to install apache.  Then you could just type in the local IP of your computer in the web browser of the others.

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop)

---

### Post by spiderbatdad on 2008-08-09
This tries to be the simplest how-to to set up apache. Any video files you put in bowseable folders or in the root document, if it is indexable, will be browseable. [http://spiderbatdad.wordpress.com/basic-apache2-how-to/](http://spiderbatdad.wordpress.com/basic-apache2-how-to/)

---

### Post by cariboo on 2008-08-09
If you didn't install it during the initial installation, you need to install the LAMP server. at the command line type;

```
tasksel
```

To administer your server I would suggest a web based administration suite like webmin it is available here:

[http://www.webmin.com/](http://www.webmin.com/)

Here is a webmin howto:

[http://skullbox.net/webmin.php](http://skullbox.net/webmin.php)

Running a web based administration suite will save you from having to run a gui pn your server.

I stream video from my server, it is pretty simple to set up, I created a web page for the various types of tv shows and movies I have on my server, Now all I have to do is click on a link and the video starts playing in my web browser.

I would also suggest start reading the server forum to get info on port forwarding, dynamic dns and any other issues that arise during setup.

Jim

---

### Post by spiderbatdad on 2008-08-09
You do not need LAMP to run an apache server for the simple purpose of hosting files accessible through the web. All you have to do is install apache and point it to the folders/files you want to share. Even without an html page, you can still have indexes that the browser sees.

---

