---
title: "Creating posters controller application"
date: 2008-06-12
forum: Programming Talk
---

### Post by Pawka on 2008-06-12
I'm coding poster controller application:

Application downloads poster images with rsync from server. Posters are separated to few parts: for example one poster consists of 3 image files. Then each image should be displayed on separate monitors. Program also downloads XML playlists with posters filenames, how much time show each poster and other data. For example, one poster should be displayed for 2 mins, while another for 5 mins. Application cycles playlist.

Everything looks like quite simple, except few things:
1. I'm thinking about use some image viewer to display pictures. Image viewer maybe should work as server aplication, or have any calls interface to control it from mine main aplication. I'm coding with C++, but it doesn't matter what API program uses. My controller application should send signal to image viewer when it needs load a new picture. It would be nice that viewer also has some effects as fade or other. Maybe anyone knows such image viewer?

2. I don't know how to set image viewer (or viewers) to show pictures on different screens. I need to show 3 pics at once and each of them on different monitors. How to control data output by command line or code on different screens?

At first I was thinking about to set images as desktop backgrounds and set each background to different monitor. But it sounds quite lame :-) If you have other suggestions about my application, I would be verry happy to hear.

---

### Post by Pawka on 2008-06-13
Bump.

---

