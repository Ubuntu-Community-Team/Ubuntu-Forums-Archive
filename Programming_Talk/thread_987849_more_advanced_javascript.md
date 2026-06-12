---
title: "more advanced javascript"
date: 2008-11-19
forum: Programming Talk
---

### Post by rtoot3 on 2008-11-19
i would like to learn more advanced javascript with like sliding boxs and tabs and all that stuff, i know basic javascript, but so far the only tutorials i can find are very basic, anyone know a good tutorial?

---

### Post by ufis on 2008-11-20
I do not know about advanced tutorials but here is my advice:

If you are comfortable with the topics covered in [http://www.w3schools.com/js/default.asp]("http://www.w3schools.com/js/default.asp") and [http://www.w3schools.com/htmldom/default.asp]("http://www.w3schools.com/htmldom/default.asp") just google for terms like "javascript visual effects". Look at some of those scripts available and learn by "modification and experimentation".

---

### Post by mike_g on 2008-11-20
I find that probably one of the most usefull things for creating dynamic content is by being to set an elements html content. IE:
```
someelement.innerHTML = "Something new";
```
You can get the element you want by id:
```
someelement = document.getElementById("someid");
```
Or directly through the [DOM](http://www.w3schools.com/js/js_obj_htmldom.asp)

With that you can pretty much change whatever you want. For animations and stuff you might want to look at setting up [timers](http://www.w3schools.com/js/js_timing.asp).

---

### Post by drubin on 2008-11-20
I have personally decided that learning bassic dome javascript is point less for real world development! None of the browsers remotely follow the conventions.

I would suggest using some sort of wrapper to identify elements handle effects. If you would like to learn more about dom start by looking at how these wrapper API's get around the dom with nasty hacks like 
if IE then do else if not FF else lastly give up and return null...

Here are some great ones to try out 
[Jquery]("http://jquery.com")
[mootools]("http://mootools.net")

---

