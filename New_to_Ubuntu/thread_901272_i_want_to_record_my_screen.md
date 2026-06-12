---
title: "i want to record my screen"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-08-26
i want to produce a small video tutorial for my friend. what software should i use to record my screen. i used recordmydesktop or some similar software... the output came with very bad quality....
i have 2gb RAM and 3Ghz processor..

suggest me

---

### Post by luckydeveloper on 2008-08-26
i didnt buy and install any nvidia/or any other video card.. i have only the card that came inbuilt with my pentium Dcore processor

---

### Post by overdrank on 2008-08-26
> **luckydeveloper said:**
> i want to produce a small video tutorial for my friend. what software should i use to record my screen. i used recordmydesktop or some similar software... the output came with very bad quality....
i have 2gb RAM and 3Ghz processor..

suggest me

Hi and since you mentioned it, what is the model of the graphics card? 
Are you having any other graphics issues like with videos and such? 
You may try and reduce the area of recording. There is Istanbul 
[https://help.ubuntu.com/community/Istanbul](https://help.ubuntu.com/community/Istanbul)

---

### Post by luckydeveloper on 2008-08-26
i dont know how to check the model...how should i check it

---

### Post by billgoldberg on 2008-08-26
If you want to create a video tutorial I suggest using [Wink]("http://linuxowns.wordpress.com/2008/08/24/create-a-video-tutorial-or-record-desktop/").

It will allow you to add text to the "video" and remove parts of the video, ...

You can save the vid as .swf.

You will need to open that .swf with firefox (vlc, ... will not display it correctly).

Example of a video created with Wink.

[http://rhinoweb.us/howtopuppyircgaim.htm](http://rhinoweb.us/howtopuppyircgaim.htm)

---

### Post by Xiangxianni on 2008-08-26
Yes,I think it's easy to use Istanbul.
Here is a simple guide to use Istanbul in Ubuntu
[http://www.admin-faq.cn/to-create-a-screencast-in-ubuntu](http://www.admin-faq.cn/to-create-a-screencast-in-ubuntu)

---

### Post by -Zeus- on 2008-08-26
to find out your video card, install this;
```
sudo apt-get install sysinfo && sysinfo&
```

When the thing starts, go to "graphics card" and see what it says.

---

### Post by jakupl on 2008-08-26
I have also tried to make tutorials, but i could not find any decent movie editing software.

---

### Post by starcannon on 2008-08-26
*Record My Desktop* is easy to use and in the repositories.

```
sudo apt-get install recordmydesktop
```

or alternately search it in the synaptic package manager.

Works great, but runs from command line.

To use its default settings, capturing everything on the screen. CTRL-c to make it stop, then it will encode and save the movie(can take some time depending on how long you let it run)
```
recordmydesktop ~/movie_name.ogg[code]

to find out what all you can make it do.

[code]recordmydesktop --help
```

```
man recordmydesktop
```

Theres some decent editors out:[[COLOR="DarkOrange"][SIZE="3"]Cinerella[/SIZE][/COLOR]]("http://heroinewarrior.com/cinelerra.php3") is one that I like. There is another thats kinda like the free one in windows XP but I forget its name.

---

