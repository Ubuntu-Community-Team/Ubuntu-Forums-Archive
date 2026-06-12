---
title: "Rounded Corner &lt;div&gt; with background image"
date: 2008-12-19
forum: Programming Talk
---

### Post by Tux.Ice on 2008-12-19
I would like to know how to do this: 

I have this website: [http://go-techo.com/](http://go-techo.com/) As you can see, the corners are rendered using javascript, but they have white pixels around them because the JS can't handle a background image. How can I replace the corner images with this image ([http://go-techo.com/img/nav_corner_let.png](http://go-techo.com/img/nav_corner_let.png)) and the various rotations of it? I have tried a few tutorials on the net, but none of them seem to work, Help would be appreciated :D

---

### Post by mssever on 2008-12-19
> **Tux.Ice said:**
> I would like to know how to do this: 

I have this website: [http://go-techo.com/](http://go-techo.com/) As you can see, the corners are rendered using javascript, but they have white pixels around them because the JS can't handle a background image. How can I replace the corner images with this image ([http://go-techo.com/img/nav_corner_let.png](http://go-techo.com/img/nav_corner_let.png)) and the various rotations of it? I have tried a few tutorials on the net, but none of them seem to work, Help would be appreciated :D
Browsers typically are bad at manipulating images. I suggest storing PNGs of the corners in the proper size and rotations and just linking to them. Trying to manipulate a single image with JavaScript is just borrowing trouble.

---

### Post by Tux.Ice on 2008-12-19
I'm not trying to manipulate it with the Javascript, I don't know how to link to it, and add rounded corners to a <div> that alreday has a background image.

---

