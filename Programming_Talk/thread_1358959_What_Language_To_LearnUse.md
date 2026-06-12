---
title: "What Language To Learn/Use?"
date: 2009-12-19
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-12-19
Ey guys, I would say I am at an intermediate programming level, I have a lot of experience with Python, moderate experience with C/C++ and Obj-C and I am a complete noob when it comes to animation or anything web-related for that matter. 

Anyways, I am wondering what programming language I should use for 3D images that can be manipulated by the user in a web page? I hear Open GL is really solid, but can that be used for web pages? Flash seems to be the most popular, but I think I read somewhere awhile ago that flash is going to die in the long-run. I have also looked into SVG a little bit, but it seems that flash would be better over the two. If anyone has any suggestions for me I would greatly appreciate them and thank you!

Oh and if you have any recommendations for a newcomer in this area, that would be great!

---

### Post by e=mc^3 on 2009-12-19
Hello,

Exactly, what do you want ? Do you want to learn to use a tool to build something or do you want to learn to build a tool ?

If you want to learn to use a tool then relax and take a look at flash. One of my friend is a developer and he said that flash now support 3D, but i dont know if its good enough. 

If you want to learn to build the tool, then u gotta learn a lot, like some basic about 3D programming. There are a lot of book about that.

Personally i think that even when you are just want to learn to use a tool, it's a big help if you know the theory behind it.

---

### Post by StunnerAlpha on 2009-12-19
Thanks for the speedy response. I want to learn a language(lets say flash) to create a 3D environment that the user can interact with(like a flash based game) that is viewable and useable through a browser.

---

### Post by Some Penguin on 2009-12-19
If you're focused primarily on developing simple web applications, then Flash is a reasonable tool with pretty decent authoring stuff, from what I hear.

If you're looking for something that will be more general, but will still run reasonably in a browser without worrying too much about browser compatibility matrices or demanding that users load unusual plug-ins, you might want to consider Java.  OpenGL bindings do exist for Java, for instance -- see [http://download.java.net/media/jogl/demos/www]("http://download.java.net/media/jogl/demos/www/")/

That said, Java is not necessarily a great choice of language to start with, if you have no experience with other languages, because it might teach you to rely too much on java.util instead of learning how to implement basic structures, and also because writing in a lower-level language that requires you to do your own memory management (such as C) would force you to learn more concepts and to develop habits that will be more transferable to other systems.

---

### Post by nvteighen on 2009-12-19
Uh... I feel you've answered your own question yourself... :) You want a Flash-like environment... well, then the best choice is Flash and that's all.

---

### Post by grayrainbow on 2009-12-19
> **StunnerAlpha said:**
> Ey guys, I would say I am at an intermediate programming level, I have a lot of experience with Python, moderate experience with C/C++ and Obj-C and I am a complete noob when it comes to animation or anything web-related for that matter. 

Anyways, I am wondering what programming language I should use for 3D images that can be manipulated by the user in a web page? I hear Open GL is really solid, but can that be used for web pages? Flash seems to be the most popular, but I think I read somewhere awhile ago that flash is going to die in the long-run. I have also looked into SVG a little bit, but it seems that flash would be better over the two. If anyone has any suggestions for me I would greatly appreciate them and thank you!

Oh and if you have any recommendations for a newcomer in this area, that would be great!
Most of the stuff will 'going to die' in the long run, just like every living creature on that planet :)
Given that most interactive web pages nowadays are with flash, given that flash could be use not only for web stuff, I would say that flash is pretty solid, but of course it will be replace by something in the future, just like everything else(even C may be replaced after 100 years, who knows). Otherwise I don't know exactly the state of moonlight, but you could look at it, but just like java applets which are rarely-rarely used(almost not used) it could be not 'the best' technology to learn.

P.S. OpenGL could be used by your browser to allow flash stuff to look good, but you probably won't care about it.

---

### Post by StunnerAlpha on 2010-07-10
Ey guys, been awhile but I have come back to pondering about this and finally begin and I came upon JavaFX([http://en.wikipedia.org/wiki/JavaFX](http://en.wikipedia.org/wiki/JavaFX)). What do you guys think of it? Does it have 3D graphic support?

Ideally I would do this project in HTML 5, but that isn't out yet and by the looks of it Adobe Flash is on its way out, so I would rather not learn a proprietary and dying technology. But, yeah any input would be greatly appreciated! Thanks! :)

---

### Post by myrtle1908 on 2010-07-10
JavaScript!

[http://www.andrew-hoyer.com/experiments/cloth](http://www.andrew-hoyer.com/experiments/cloth)

Use Chrome

---

### Post by crush304 on 2010-07-10
i haven't done anything with web 3D but take a look at

webgl: [http://www.scriptol.com/programming/webgl.php](http://www.scriptol.com/programming/webgl.php)

---

### Post by phrostbyte on 2010-07-10
Java is a better language for Web 3D kind of stuff, as it natively supports OpenGL and Flash doesn't.

---

### Post by soltanis on 2010-07-10
WebGL + Javascript

---

### Post by StunnerAlpha on 2010-07-10
Awesome guys! That's just what I am looking for! Thanks to everyone who responded.

---

### Post by TimTimTimma on 2010-07-10
If you are wanting to "program" a GUI of sorts, you might see better results with java that way you can avoid browse based compatibility issues. However, if you are looking for more of a design angle you would have more fun using Flash.

One thing I haven't seem yet though is anyone suggesting Ajax. With Ajax you can use javascript for the programming aspect, xml/php for the handling of events and distribution of data and finally mysql/postgre for the storing/retrieving all the necessary data.

---

### Post by StunnerAlpha on 2010-07-11
> **TimTimTimma said:**
> If you are wanting to "program" a GUI of sorts, you might see better results with java that way you can avoid browse based compatibility issues. However, if you are looking for more of a design angle you would have more fun using Flash.

One thing I haven't seem yet though is anyone suggesting Ajax. With Ajax you can use javascript for the programming aspect, xml/php for the handling of events and distribution of data and finally mysql/postgre for the storing/retrieving all the necessary data.

Thanks for the input man. Think of what I want to do as more of like a game. Would this still be the way to go? I appreciate that you brought up the point about java being compatable across all platforms, but then again I really don't want the user to have to install anything to use what I am making. It should be more of a "plug and play" type thing with any browser, but I am willing to make compromises as I realize I cannot get the best of everything by choosing a particular approach.

---

