---
title: "HTML image not loading"
date: 2014-01-31
forum: Programming Talk
---

### Post by brick2 on 2014-01-31
I do not seam to be able to load images with html. Bellow is the example of the code.

[HTML]<html>

    <body>
        <img src = "1976_dawn back 2.jpg">
    
    </body>

</html>[/HTML]

First I tried to load the images from diffrent locations by putting in paths, than I tries putting them into the same folder as the html for example:

In /var/www
Images            test.html

In /var/www/Images
1976_dawn back 2.jpg

Than I tried just putting "1976_dawn back 2.jpg" into /var/www

Nothing. My guess was that something was wrong wit hthe premissions so I did chmod 777 "1976_dawn back 2.jpg" , nope still nothing, but, there was one diffrence now. Now I could acces the image manually via firefox as opposed to before when I got denied access.

I am using Ubuntu 12.04
LAMP is installed.

Could anyone help me out here?

Thank you all for your time.

---

### Post by Dennis N on 2014-01-31
As to your code example, the should be no spaces before and after the equal sign. It should be:

```
<img src="1976_dawn back 2.jpg">
```

This image must also be in the same directory as the html file. If not, you need a path to the image (relative or full).

---

### Post by brick2 on 2014-01-31
Yeah I know jsut posted the wrong image here, took one as an example but it still doesnt work without the spaces

---

### Post by brick2 on 2014-01-31
<img src="SpaceBurn.jpg">

---

### Post by brick2 on 2014-01-31
Well after a while I got it working now, so sorry to have wasted time just need to mess around with the premissions of the images. Again sorry for the time and thank you.

---

### Post by Dennis N on 2014-01-31
Then something else is wrong with that line. Is the image it in the same folder as the HTML? Otherwise, it won't be found. Is the file name correct? Linux is case sensitive, so if your image is really Spaceburn.jpg or SpaceBurn.JPG is won't load.

---

### Post by Dennis N on 2014-01-31
> **brick2 said:**
> Well after a while I got it working now, so sorry to have wasted time just need to mess around with the premissions of the images. Again sorry for the time and thank you.

OK. No problem. Good luck with your coding!

---

### Post by ofnuts on 2014-02-01
> **Dennis N said:**
> As to your code example, the should be no spaces before and after the equal sign. It should be:

```
<img src="1976_dawn back 2.jpg">
```

Uh? See [http://www.w3.org/TR/html-markup/syntax.html#attribute](http://www.w3.org/TR/html-markup/syntax.html#attribute)

---

