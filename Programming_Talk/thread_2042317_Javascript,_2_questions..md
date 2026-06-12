---
title: "Javascript, 2 questions."
date: 2012-08-14
forum: Programming Talk
---

### Post by DarkAmbient on 2012-08-14
Hey, trying to get a hang on javascript. Some things I havn't understood (fully) yet though.

Q #1: Why do prototypes exist?
Q #2: Is it possible to include (new) javascripts from inside javascripts somehow?
Q #3: Is here anyway I can find out the size of objects? As in a physical size in bits. I'm just curious on this one...

---

### Post by slooksterpsv on 2012-08-14
> **DarkAmbient said:**
> ...

Question #1: **Why do prototypes exist? Isn't normal functions and its properties sufficient? (considering the openness of and how sugar-able the language is)**


I'm not sure why exactly, but in my opinion, to make the code clean.

> 
Pre-Question #2: I'm kinda mimicking classes with js, I don't know if that is proper javascript-coding. But it seems to work. This is how I implements the class-like functions.. (find Question #2 further down)

If it works for you, go for it. I think jquery uses some sort of class-type functionality.

> 

Question #2: **How do I include multiple sourcefiles when needed?**
(This will really be several questions, sorry for that)


No need to apologize, ask as many questions as you need, that's the only way to get answers.

To include multiple JS files you can do the following in the html code:
[php]
<script language="javascript" src="my_code.js"></script>
[/php]

Where **my_code.js** is the javascript file that contains all your functions and what not.

---

### Post by DarkAmbient on 2012-08-16
Hi, thank you for answering. :) My first post was messy, I will edit it in a moment...

Aaand, I'm a bit more at piece with the purpose of prototypes now that I discovered that you can add methods to build-in objects/data-types.

```
Array.prototype.allNumeric = function() {
  // loop through this array, return false encountering non-numeric
}
```

for instance... that and that it is a way to expose local variables via global methods. :)

> If it works for you, go for it. I think jquery uses some sort of class-type functionality.
Nice to hear.. I hate to start doing something one way, only to discover I made it wrong in any way from the start. =)

I think you got me wrong on the include script -part though. I was wondering if it's possible to include scripts-on-demand.. sort of. In C++ (yea I know there's a huge difference) I can add #include <some/file> at the top of each source-file. I would like some equality in javascript.. including everything from the source-file where I initate my "web-based-app" seems messy.

Could point out that I'm working with a (html5) canvas.. So the page itself will never reload.

---

### Post by slooksterpsv on 2012-08-16
[http://stackoverflow.com/questions/950087/include-javascript-file-inside-javascript-file](http://stackoverflow.com/questions/950087/include-javascript-file-inside-javascript-file)

Just found that, it should work if when the first script loads it creates the element of loading the next script file. So tech. you could have it load only when needed (e.g. you click button x, it opens the javascript file and loads x's definitions, and continue from there (not sure if it would work that way, but could)).

---

### Post by DarkAmbient on 2012-08-17
> **slooksterpsv said:**
> [http://stackoverflow.com/questions/950087/include-javascript-file-inside-javascript-file](http://stackoverflow.com/questions/950087/include-javascript-file-inside-javascript-file)

Just found that, it should work if when the first script loads it creates the element of loading the next script file. So tech. you could have it load only when needed (e.g. you click button x, it opens the javascript file and loads x's definitions, and continue from there (not sure if it would work that way, but could)).

Cool, I guess I need to learn some jQuery from here on then. I'm really excited about this, will be fun to see how it works (out).

The size thingie of objects that I asked in first post.. It doesn't seem to be any native functionality for retrieving such... it doesn't really matter though.

I'll consider this thread solved, and thanks again for da input. :)

---

