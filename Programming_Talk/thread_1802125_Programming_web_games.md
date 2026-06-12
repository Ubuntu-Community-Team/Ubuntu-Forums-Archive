---
title: "Programming web games"
date: 2011-07-11
forum: Programming Talk
---

### Post by Mkaveli on 2011-07-11
Hello i was wondering if someone has a answer for me. I want to create web games in Ubuntu because i like the operating system. I have experience with Java, Actionscript, Flash but i dont know wich programs/IDE's to use. so can someone tell me wat the best program language is to make web games in ubuntu.

Thanks.

---

### Post by PaulM1985 on 2011-07-11
For Java I would recommend Netbeans.  I don't have any experience with the other languages tho.

Paul

---

### Post by TwoEars on 2011-07-11
Well, it depends entirely on what you mean by "web games". Also note, the fact that you're using Ubuntu has very little meaning - if you're making a web app, it should be able to run cross platform on any platform that'll support the technology. 
It's possible to create games using just PHP and Javascript, but often Flash and Java are the better alternatives. Again, it depends entirely on what you want to do.

---

### Post by nmaster on 2011-07-11
html5 and javascript would be cool. it doesn't depend on flash so it will work as long as the user has an up-to-date browser.

you can find lots of public domain code to start from just by googling "html5 and javascript games." as an example, Doom was recently ported to javascript: [http://www.readwriteweb.com/hack/2011/05/doom-ported-to-javascript-and.php](http://www.readwriteweb.com/hack/2011/05/doom-ported-to-javascript-and.php)

obviously, you can also make much simpler games to start with.

---

### Post by Mkaveli on 2011-07-11
Thanks for the fast reply. I think I'm gonna try some HTML5 and JS because i am interested in that. The thing is i had a complete AS3 project on my windows computer. My computer crashed and I swore not to use Windows again (Probably temporarily) but i always love working on linux. so now im trying to find programs that can create great web games(Games with Database support, and in the future multiplayer).

---

### Post by HarrisonNapper on 2011-07-12
A combination of languages is always an option. In my case I would be referring to Python on Django or web2py and Javascript with HTML5. Depends on your preferred toolbox. There aren't any good flash IDEs in the repository that I know of and I doubt very many are Linux compatible. Adobe's tools aren't, but there are a few things in there. Unfortunately for professionals working in some industries it's often impossible to have a Linux-only household (usually multimedia related).

---

### Post by nmaster on 2011-07-12
> **HarrisonNapper said:**
>  Unfortunately for professionals working in some industries it's often impossible to have a Linux-only household (usually multimedia related).

so true.  even simple javascript needs to be tested on IE, especially the older versions.  i guess you run this through wine but its still a necessity.

---

### Post by juancarlospaco on 2011-07-12
I dont agree supporting  IE older versions.
Just install Chrome-Frame and ready... 
even the new versions dont know whats a <canvas> or ws://

---

### Post by nmaster on 2011-07-12
> **juancarlospaco said:**
> I dont agree supporting  IE older versions.
Just install Chrome-Frame and ready... 
even the new versions dont know whats a <canvas> or ws://

i don't check the very old versions (ie6, ie7). it would take extra work and i don't do a lot of fancy stuff anyway.  avoiding exotic features makes cross-browser compatibility more likely. but it would be silly to not develop for ie8,ie9.  too many people use ie to ignore it: [http://arstechnica.com/web/news/2011/07/june-browser-stats-rapid-release-edition.ars](http://arstechnica.com/web/news/2011/07/june-browser-stats-rapid-release-edition.ars)

i didn't realize that IE doesn't support canvas.  that's pretty lame, especially since its a great way to make games without Flash.

---

### Post by tauh on 2011-07-12
How about WebGL?

[http://en.wikipedia.org/wiki/WebGL](http://en.wikipedia.org/wiki/WebGL)

[http://learningwebgl.com/blog/](http://learningwebgl.com/blog/)

---

### Post by juancarlospaco on 2011-07-12
> **nmaster said:**
> avoiding exotic features 

i didn't realize that IE doesn't support canvas. 

I think a Canvas is not an exotic feature; 
i dont remeber but if you check SVG compatibility you will find a surprise...

---

### Post by Mkaveli on 2011-07-12
OK now im thinking that HTML5 and JavaScript isn't what i am looking for. I want to create games that make excessive use of a database. Submit and receive scores for example. I really liked how it al worked with AS3 and Flash but i don't think that is a option with ubuntu. Also i would love to have some 3d effects in it. Thanks

---

### Post by TwoEars on 2011-07-12
> **Mkaveli said:**
> OK now im thinking that HTML5 and JavaScript isn't what i am looking for. I want to create games that make excessive use of a database. Submit and receive scores for example. I really liked how it al worked with AS3 and Flash but i don't think that is a option with ubuntu. Also i would love to have some 3d effects in it. Thanks

Look into JQuery for Javascript database transactions. Again, I recommend looking into Java or Flash. I don't really recommend HTML5 just yet, not if you plan on making money, anyway.

---

### Post by juancarlospaco on 2011-07-12
HTML5 got its own Database, Javascript got its own Database, your Backend can have its own Database,
your choice...

HTML5 got Hardware Acelerated 3D.

For an HTML5 Game Example, see: [http://chrome.angrybirds.com/](http://chrome.angrybirds.com/)

---

### Post by myrtle1908 on 2011-07-12
As an aside, you can use RaphaelJS for SVG/VML.  It pumps out VML for the non-SVG browsers like IE6-8.  It's a nice library.

[http://raphaeljs.com/](http://raphaeljs.com/)

Also some nice JS physics stuff here (with Canvas) ... [http://andrew-hoyer.com/experiments/cloth/](http://andrew-hoyer.com/experiments/cloth/).  Works fine in IE9.

---

### Post by myrtle1908 on 2011-07-12
Also, check this out ... [http://www.processing.org/](http://www.processing.org/)

---

### Post by snowz on 2011-12-23
Html5 with Javascript sounds like an interesting thing to learn :)

---

### Post by juancarlospaco on 2011-12-23
Now with Native Client you can code it on C / C++ too, 
theres a framework named pepper, everything open source,
i was wondering if some binding for other languages will arise soon, 
would be nice to have a python wrapper for NaCL :)

---

