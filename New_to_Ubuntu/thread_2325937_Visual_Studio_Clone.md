---
title: "Visual Studio Clone"
date: 2016-05-26
forum: New to Ubuntu
---

### Post by JoAnn_Donaldson on 2016-05-26
Is there a form of Visual Studio for Linux that runs on Ubuntu?
I am a retired DEA Software Engineer/CSI and have a lot of utilities and programs written in C#
that I would like to see if I could get running on my Ubuntu system.

---

### Post by QDR06VV9 on 2016-05-26
Well i do not know how well it runs yet but that said have a look at the two links below

How to install Visual Studio Code on Ubuntu: [http://askubuntu.com/questions/616075/how-to-install-visual-studio-code-on-ubuntu](http://askubuntu.com/questions/616075/how-to-install-visual-studio-code-on-ubuntu)

And from Microsoft: [https://code.visualstudio.com/Docs/editor/setup](https://code.visualstudio.com/Docs/editor/setup)

---

### Post by grahammechanical on 2016-05-26
Yes. And there is a Ubuntu tool call Ubuntu Make that will install Visual Studio and keep it up to date. This blog post from 30th April 2015 records the release of Visual Studio for Linux and support for Visual Studio being added to Ubuntu Make

[http://blog.didrocks.fr/post/Ubuntu-Make-0.7-released-with-Visual-Studio-Code-support](http://blog.didrocks.fr/post/Ubuntu-Make-0.7-released-with-Visual-Studio-Code-support)

This explains all about Ubuntu Make & how to install it.

[https://wiki.ubuntu.com/ubuntu-make](https://wiki.ubuntu.com/ubuntu-make)

[https://wiki.ubuntu.com/ubuntu-make](https://wiki.ubuntu.com/ubuntu-make)

This lists some of the developer IDEs available through Ubuntu Make

[http://blog.didrocks.fr/](http://blog.didrocks.fr/)

Regards.

---

### Post by JoAnn_Donaldson on 2016-05-27
Thanks for the reply. I have both VS 2008 and VS2010. Are both supported?

---

### Post by Omar_Jair on 2016-05-27
I also know a very good IDE that can help you, MonoDevelop offers a customizable IDE to write apps in C#, C++ and VB, you can try it, it runs on console and comes with GTK that allow you to make form applications.:KS

---

### Post by tdawgf on 2016-06-03
> **JoAnn_Donaldson said:**
> Thanks for the reply. I have both VS 2008 and VS2010. Are both supported?

First off, you are getting some slightly misunderstood advice (I believe). As it stands currently, it appears that, at least in some distros, Visual Studio 2010 express edition has been successfully run with wine. I wouldn't place all my faith in it though. What people are replying yes about is a tool called Visual Studio Code. This is a whole different beast from what you are looking to install. From my experience it has worked well, but it is not a full fledged IDE in the same vein as Visual Studio. It was released, if my memory serves me correctly, right around the same time as the dot net core was made available to Linux. 

Judging by your original post, and your later reply,  I believe you are looking for something different. I suggest you take a look at MonoDevelop. This works fairly similarly to older versions of Visual Studio. Some people, myself included, use it often enough. A word of advice though. If you won't have straight up access to WinForms and WPF are not necessarily going to function with Mono (It has been hit or miss with me trying to get my old apps to run and I am in the web dev world now).

If you need any help, message me and I will do everything I can to guide you to answers.

---

