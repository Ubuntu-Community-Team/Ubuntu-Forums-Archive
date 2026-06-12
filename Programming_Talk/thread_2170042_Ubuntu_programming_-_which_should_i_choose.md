---
title: "Ubuntu programming - which should i choose?"
date: 2013-08-24
forum: Programming Talk
---

### Post by josh17 on 2013-08-24
I want to start developing applications and games for Ubuntu, but I hit a bit of a roadblock because I don't know if I should use c++ or python. I understand both languages work in Ubuntu (please correct me if I'm wrong) and I've taken a look at both languages. But I don't know which one to use, I'm not smart enough to learn both at the same time so I was thinking python as it is easier to learn, but I wanted professional option because I don't want to make a mistake before I even start. If anyone can help me out I'd appreciate it a lot

---

### Post by SweetAurora on 2013-08-24
Take a look here:
[http://developer.ubuntu.com/get-started/](http://developer.ubuntu.com/get-started/)
Canonical gives good resources for developing apps on their platforms, both Mobile and Deskop. Also since Ubunu is moving in the convergence direction, the lessons learned here means easier app intergration in the future with 14.04 and 14.10.

---

### Post by josh17 on 2013-08-25
> **SweetAurora said:**
> Take a look here:
[http://developer.ubuntu.com/get-started/](http://developer.ubuntu.com/get-started/)
Canonical gives good resources for developing apps on their platforms, both Mobile and Deskop. Also since Ubunu is moving in the convergence direction, the lessons learned here means easier app intergration in the future with 14.04 and 14.10.

I just installed that sdk and noticed it says its for phone apps?

---

### Post by akoskm on 2013-08-25
Yes, looks like that one is for phone apps. You have to decide what you want to achieve, games for all platforms, games for PC. First of all, are you sure that you want to focus on developing games?

I personally prefer python over c++, I'm doing full time Java but enjoying python every time I utilize it for a home project. It's a "modern" language and I think you'll have fun learning it.

---

### Post by josh17 on 2013-08-25
> **akoskm said:**
> Yes, looks like that one is for phone apps. You have to decide what you want to achieve, games for all platforms, games for PC. First of all, are you sure that you want to focus on developing games?

I personally prefer python over c++, I'm doing full time Java but enjoying python every time I utilize it for a home project. It's a "modern" language and I think you'll have fun learning it.

Yes I want to develop games for the Ubuntu operating system on PC. That is the goal I wish the achieve. However I won't only focus on games, that's just my main focus.

---

### Post by hakermania on 2013-08-25
> **josh17 said:**
> Yes I want to develop games for the Ubuntu operating system on PC. That is the goal I wish the achieve. However I won't only focus on games, that's just my main focus.

As you are inexperienced right now I don't think that you should start developing games immediately.

I started learning programming through C, which is considered a rather difficult language. If I knew, I would rather have started with Python as well.

Python is a very good language for beginners. I've also worked with the **pygame **module and it keeps things simple in game development.

Also, as it is a script language, it can be developed very quickly because you don't need to wait for compilations to finish.

But, my personal opinion as for python, is that it isn't a very quick language. It is good for simple programs but for something bigger I think that you should use some other language.

For example, take a look at the software-center:

```

file /usr/share/software-center/software-center

```

It is written in python, and I find it to be very unresponsive and slow.

Summing up, Python is a good language to start and you may as well build programs and simple 2D games using pygame (I've built a cat run & jump game for college), but you should try something more efficient (and difficult) if you are planning to build a big program with lots of options etc.

Also, as you will focus on gaming, I'd recommend waiting for the Unity3D game engine to come to Linux. It is nice :)

---

### Post by josh17 on 2013-08-25
I already took a look at python a while back and I feel like I'm ready to move on. The thing is I don't know which one would be more efficient on Linux. And I do plan on building bigger games (most voxel based, inspired by mine craft and cube world and the such) so if I understand your response correctly, I should use c++ if I want to build games like that and if I feel im up for it?

---

### Post by hakermania on 2013-08-25
> **josh17 said:**
> I already took a look at python a while back and I feel like I'm ready to move on. The thing is I don't know which one would be more efficient on Linux. And I do plan on building bigger games (most voxel based, inspired by mine craft and cube world and the such) so if I understand your response correctly, I should use c++ if I want to build games like that and if I feel im up for it?

No, I wouldn't recommend C++ for games.

As for the libraries that exist right now, I would recommend the following:

1: For GUI programs:

C -> If you want native look, using GTK libraries
C++ -> if you want something quick, powerful and cross platform, which lacks the native look most of the times, using Qt libs
Python -> It has bindings for GTK for the native look, but I wouldn't recommend for large projects

2: For command line programs I would recommend all of Python/C/C++/Bash, and it mainly depends on where you are planning to use the program. If it is for your use, Python or Bash would fit best.

3: For games:

Python -> using pygame
Blender -> using the build-in game engine system
Unity3d -> You have to wait for it to come for linux and it is quite expensive, but it is very nice. You can program with UnityScript (Javascript's brother), C# or Boo.
Also, take a look at this: [http://ubuntuforums.org/archive/index.php/t-974144.html](http://ubuntuforums.org/archive/index.php/t-974144.html)

Please don't take the above for granted. They are just my personal opinion.

---

### Post by josh17 on 2013-08-26
> **hakermania said:**
> No, I wouldn't recommend C++ for games.

As for the libraries that exist right now, I would recommend the following:

1: For GUI programs:

C -> If you want native look, using GTK libraries
C++ -> if you want something quick, powerful and cross platform, which lacks the native look most of the times, using Qt libs
Python -> It has bindings for GTK for the native look, but I wouldn't recommend for large projects

2: For command line programs I would recommend all of Python/C/C++/Bash, and it mainly depends on where you are planning to use the program. If it is for your use, Python or Bash would fit best.

3: For games:

Python -> using pygame
Blender -> using the build-in game engine system
Unity3d -> You have to wait for it to come for linux and it is quite expensive, but it is very nice. You can program with UnityScript (Javascript's brother), C# or Boo.
Also, take a look at this: [http://ubuntuforums.org/archive/index.php/t-974144.html](http://ubuntuforums.org/archive/index.php/t-974144.html)

Please don't take the above for granted. They are just my personal opinion.

I was thinking about using blender, I just have no idea how.

---

### Post by lads on 2013-08-27
Hi Josh, the guide [provided above by hakermania]("http://ubuntuforums.org/showthread.php?t=2170042&p=12768736#post12768736") is a very sensible one, stick with it. But I feel you may be putting the cart ahead of the horses; Python can be useful introducing a beginner to OO programming. There are [nice tutorials]("http://www.voidspace.org.uk/python/articles/OOP.shtml") out there that I'd advise you to follow before diving further into the sort of programming you aim at.

---

