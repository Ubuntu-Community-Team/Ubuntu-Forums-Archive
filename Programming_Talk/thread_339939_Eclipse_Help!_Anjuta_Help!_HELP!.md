---
title: "Eclipse Help! Anjuta Help! HELP!"
date: 2007-01-16
forum: Programming Talk
---

### Post by nick.inspiron6400 on 2007-01-16
Hi,

I have been trying to get eclipse to work, but i have little success. Once i open eclipse i get a message about No Java Development kit or Java Enviroment.

How do i resolve this? I did try Anjuta with Glade but i had alot of problems, with the glade plugin in not working. How do i resolve this aswell?

I have never programmed before in Linux, so i am very new!

If you need any more infomation just ask!

Thanks!

Nick,

---

### Post by Mirrorball on 2007-01-16
phossal wrote these instructions for installing Java and Eclipse, have a look at them:
[http://www.ubuntuforums.org/showpost.php?p=1978966&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1978966&postcount=2)

---

### Post by phossal on 2007-01-16
The JDK, eclipse and Tomcat tutorial thread is here: [full thread]("http://ubuntuforums.org/showthread.php?t=332674").

I used Anjuta before switching to gedit. I read something recently about Anjuta being updated, and updated in the repositories before development of the new release was finished. It's caused a lot of problems. You may find more by searching for Anjuta alone.

[edit] Mirrorball, I noticed you had some trouble launching C++ programs from eclipse. Were you able to resolve the problem?

---

### Post by Mirrorball on 2007-01-16
I was having this problem at work and I'm home now. I left work without being able to solve it. At first my old Eclipse installation was giving me a different problem (and it was working perfectly in 2006, it must have been an update that broke it), so I reinstalled it. But my C++ programs aren't launching now. I reinstalled Java as per your instructions (except that it was the amd64 version), but it didn't work.

---

### Post by lloyd mcclendon on 2007-01-16
search around here for automatix, download that and use it to get java and lots of other good stuff set up.

then go to [www.yoxos.com/ondemand](www.yoxos.com/ondemand) to download a vanilla eclipse with any plugins you want (cdt plugins if you're doing c++), and run tar -xzvf /path/to/eclipse/eclipse*.tar.gz .. do not use the ubuntu package as everybody has had nothing but problems with it.

then paste this in a file called eclipse in your path

```
#!/bin/bash

eclipse_dir="~/eclipse"
eclipse="${eclipse_dir}/eclipse"
eclipse_args="-vmargs -Xverify:none -XX:+UseParallelGC -XX:PermSize=40M -XX:MaxNewSize=64M -XX:NewSize=64M -Xmx512m -Xms512m"

${eclipse} ${eclipse_args} $* &
```

tweak the path and arguments as needed and then just type eclipse and it will work

---

### Post by phossal on 2007-01-16
> **lloyd mcclendon said:**
> search around here for automatix, download that and use it to get java and lots of other good stuff set up.

then go to [www.yoxos.com/ondemand](www.yoxos.com/ondemand) to download a vanilla eclipse with any plugins you want (cdt plugins if you're doing c++), and run tar -xzvf /path/to/eclipse/eclipse*.tar.gz .. do not use the ubuntu package as everybody has had nothing but problems with it.

then paste this in a file called eclipse in your path

```
#!/bin/bash

eclipse_dir="~/eclipse"
eclipse="${eclipse_dir}/eclipse"
eclipse_args="-vmargs -Xverify:none -XX:+UseParallelGC -XX:PermSize=40M -XX:MaxNewSize=64M -XX:NewSize=64M -Xmx512m -Xms512m"

${eclipse} ${eclipse_args} $* &
```

tweak the path and arguments as needed and then just type eclipse and it will work

That's a good *beginner* method? If so, that's a good way to *teach* it? Every post I've seen from you is reckless or offensive. Perhaps you should e-slap *yourself*. Can you do *that* with automatix? Before you reply with something obnoxious, why not just reformat your post so it makes sense - so a *beginner* could use it?

Something about the way you write, even when you're not blatantly offensive (which I much prefer), leaves people feeling like you're just trying to cause trouble. Why is that?

---

### Post by lloyd mcclendon on 2007-01-16
welcome to my ignore list

how is that not helpful?  it's not rocket science and he is doing programming so i assued that they would be able to figure it out with some help from google.  there's not much to it really, i didn't see the need to spend 1/2 hour on a post with colors to explain a simple process.  sorry.  maybe i shouild edit that so google doesn't pick that unhelpful post up.  and sorry for writing with a more advanced style than what you prefer.

---

### Post by phossal on 2007-01-16
I wasn't exactly saying your writing is *too advanced*. Regardless of what I think, you can scan the replies to your posts and count how many "Thank you" or "Screw you" responses you get. Not a lot of people seem enthusiastic about you dropping by. Perhaps you're too advanced for us all. Perhaps we should all be e-slapped. If you dismiss me as simple, what about the *other* people who feel the same way?

You could take my bit of (admittedly) unpleasant advice and try to improve your style. Or not.

---

### Post by lloyd mcclendon on 2007-01-16
or i could just ignore your crazy ***

---

### Post by phossal on 2007-01-16
I didn't mean to offend you. The way you write sucks, and it makes your advice (which might otherwise be valuable) almost completely useless. It doesn't mean you're a bad person. Other things about you make you a bad person. 

Ignore me though. Plenty of us are ignoring you. ;)

---

### Post by nick.inspiron6400 on 2007-01-17
> **lloyd mcclendon said:**
> search around here for automatix, download that and use it to get java and lots of other good stuff set up.

then go to [www.yoxos.com/ondemand](www.yoxos.com/ondemand) to download a vanilla eclipse with any plugins you want (cdt plugins if you're doing c++), and run tar -xzvf /path/to/eclipse/eclipse*.tar.gz .. do not use the ubuntu package as everybody has had nothing but problems with it.

then paste this in a file called eclipse in your path

```
#!/bin/bash

eclipse_dir="~/eclipse"
eclipse="${eclipse_dir}/eclipse"
eclipse_args="-vmargs -Xverify:none -XX:+UseParallelGC -XX:PermSize=40M -XX:MaxNewSize=64M -XX:NewSize=64M -Xmx512m -Xms512m"

${eclipse} ${eclipse_args} $* &
```


tweak the path and arguments as needed and then just type eclipse and it will work


I am very new to Linux ( didn't you know that?) And new to Linux programming and your post makes no sense.

I sorted out Eclipse, with some googling!

Now for Anjuta, i want to design the interface how do i do that?

Thanks,

Nick,

---

### Post by dnordberg on 2007-06-24
thanks lloyd mcclendon, what you said worked fine. Was having trouble installing WTP but now its ok.

Your advice was good, maybe a bit to advanced for some of these users (though i cant see how).

Anyway, i used to run eclipse 3.2 like this:

/usr/bin/eclipse -vm /usr/lib/jvm/java-6-sun/bin/java

Does adding these args still help??

And by the way, what does XX:+UseParallelGC do?

---

