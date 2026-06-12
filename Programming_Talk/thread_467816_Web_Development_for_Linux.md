---
title: "Web Development for Linux"
date: 2007-06-08
forum: Programming Talk
---

### Post by simonfiction on 2007-06-08
Hi,

I'm a web developer who has recently made the move to Ubuntu. I'm completely in love with the OS and am more than pleased with it. I'm trying to persuade the company I work for that it is important we develop our websites to work well not only with windows and mac, but also with linux (probably using a standard ubuntu installation as the standard for testing). I'm currently looking for some advice with multimedia on the web, specifically embedded in a page. What format would you recommend in terms of embedding video or audio that is easily accessible to the user? I'm not happy enough with the buggy nature of real player for linux to stream in the real format, plus this doesn't quite match my minimum requirement of a standard installation of ubuntu. I'm preferably looking for something that is going to work well for ubuntu, windows and mac. Flash seems the obvious choice for video, but still, I'm looking for any other suggestions.

Any advice would be greatly appreciated.

Thanks,
Si

---

### Post by Mickeysofine1972 on 2007-06-08
Hi

I am currently working in this role too and have managed to do excatly what your trying to accomplish.

The main thing to strees to your company is that linux doesn't have the cost but has similar if not superior software than they are already using.

The format I am using and have a lot of success with is flash video, I have been taking company videos and converting them using ffmpeg which is run by a little gui I wrote in qt4 if you would llike a copy I can email it to you in deb format

Mike

---

### Post by cunawarit on 2007-06-08
> I'm trying to persuade the company I work for that it is important we develop our websites to work well not only with windows and mac, but also with linux (probably using a standard ubuntu installation as the standard for testing).

Good luck with that :) In my experience as soon as managers hear that Linux has less than 3% of the desktop market they are not interested. Make sure you point out that Dell has started selling Ubuntu machines, maybe that will persuade them.

Personally I check that the sites I create for work do work OK on Linux even when it is not a requirement. I don&#8217;t loose sleep over little issues though, managers are not interested and money lost over minor issues would be miniscule. You also need to consider your demographic, one of the sites I run now only gets 0.05% Linux visitors... Even as a Linux user I have to admit that spending anything more than 5 minutes accommodating Linux users is a waste of time. More tech oriented sites might have much higher numbers, like this forum for instance the majority will be Linux users. 

> What format would you recommend in terms of embedding video or audio that is easily accessible to the user? I'm not happy enough with the buggy nature of real player for linux to stream in the real format, plus this doesn't quite match my minimum requirement of a standard installation of ubuntu.

I quite like realplayer, I do agree, it is very buggy, but it is better than Flash on slow old machines.

> I'm preferably looking for something that is going to work well for ubuntu, windows and mac. Flash seems the obvious choice for video, but still, I'm looking for any other suggestions.

I agree, version 9 works very well!

---

### Post by emperon on 2007-06-10
My Favorite way to go for web development on linux

1-) Flex front end - Any back end (preferebly .net/mono web services)
2-) Ruby on Rails
3-) Asp.net (mono)
4-) Java stack frameworks

---

### Post by barmazal on 2007-06-10
cunavarit, has a point but again with Ubuntu and restricted formats i could view any website with any content.

---

### Post by viciouslime on 2007-06-10
Embedded ogg theora would be something to consider. Mozilla are looking at integrating support for it in firefox so that firefox users wouldn't even have to download codecs on windows/mac. For those not using firefox, they'd only have to download flash, so I see no reason why they couldn't download ogg theora codecs either.

Failing that though, flash is definitely the way to go, it's the only thing (except ogg theora) that ALWAYS works in linux, or at least always has for me.

---

### Post by ankursethi on 2007-06-10
Flash always works. Everywhere. Unless you want your users to fish around for OGG codecs, you must use Flash. If viciouslime is right about Mozilla, then you should definitely use Theora since it's an open format.

---

### Post by simonfiction on 2007-06-12
Thanks for all your help and suggestions. It's good to see what everyone else is doing as well. Should have a a ubuntu test machine soon which is a start :)

---

