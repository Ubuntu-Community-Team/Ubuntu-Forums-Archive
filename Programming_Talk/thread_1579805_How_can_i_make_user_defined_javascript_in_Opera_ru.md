---
title: "How can i make user defined javascript in Opera run for www.google.com?"
date: 2010-09-22
forum: Programming Talk
---

### Post by cdiem on 2010-09-22
Hello,

I'm playing with user-defined javascript in opera (sadly I'm not good with it). For example, the following javascript:
[PHP]
(function() {
 
    function backgroundToGreen(){
        document.body.style.background = "green";
    }

    document.addEventListener('load', backgroundToGreen(), false);

})();[/PHP]
runs ok when used against e.g. [http://dev.opera.com/articles/view/introduction-to-user-javascript/](http://dev.opera.com/articles/view/introduction-to-user-javascript/)
but has no effect whatsoever when being run against [www.google.com](www.google.com). Both wait for the DOM to load, as far as I can tell. Why doesn't it change the background to blue on [www.google.com](www.google.com) (and a few other websites)?

---

### Post by Colonel Kilkenny on 2010-09-22
Just a guess: you're targetting body element and Google has something on top of it. White div element which is covering the whole body element perhaps?

OR

I'm not very familiar with UserJS and how it works with events but another guess would be that Google actually has builtin eventhandlers which do stuff. Which could mean that your function might get called first and after that Google is doing something for the same element and therefore your changes might not be visible. Or something like that.
Google has the fade-in effect nowadays in front page, that might be one cause?

Perhaps you could debug it with Opera Dragonfly. Ctrl+Shift+I should open it and if I remember correctly the scripts tab will show you userjs scripts as well.

edit. Another option: UserJS isn't executed on secured pages ([https://)](https://)) because of security reasons. This is something you have to change manually from opera:config.

---

### Post by Reiger on 2010-09-22
A reason might be that some sites do not define styles for the body element and hence document.body.style is undefined. As a result document.body.style.background = "green" fails with little more than a warning/error message written to the error console.

---

