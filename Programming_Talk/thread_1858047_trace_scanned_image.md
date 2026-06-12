---
title: "trace scanned image"
date: 2011-10-11
forum: Programming Talk
---

### Post by Xender1 on 2011-10-11
I have a picture that is black and white and is an outline of objects. I have lots of these and what I did was scan them into my computer and now I just need the outline of it on the computer and not the original picture. I was wondering if there already is some easy way to do this or i feel like writing a piece of code would not be that hard (and would be fun).

Anyone have any suggestions on where to begin? I was thinking of going pixel by pixel and if its white place a white pixel in a new image at same coords and if its black on my new image i will put a black pixel there. Is this possible or should i just open gimp and start tracing by hand?

---

### Post by Erdaron on 2011-10-11
I think you can automate this in GIMP by using thresholds - everything above a certain pixel value is white, and everything below a certain pixel value is black.

This wouldn't be too difficult to implement in a script. For every pixel, just compare its value to some threshold. [PIL]("http://www.pythonware.com/products/pil/") (if you are using Python) might have built-in function that will do that, but I'm not sure - I've only used it for the most basic opening and writing of images.

Binary operations like that are better done by code. You will likely make lots of mistakes doing this by hand.

---

### Post by ofnuts on 2011-10-11
> **Xender1 said:**
> I have a picture that is black and white and is an outline of objects. I have lots of these and what I did was scan them into my computer and now I just need the outline of it on the computer and not the original picture. I was wondering if there already is some easy way to do this or i feel like writing a piece of code would not be that hard (and would be fun).

Anyone have any suggestions on where to begin? I was thinking of going pixel by pixel and if its white place a white pixel in a new image at same coords and if its black on my new image i will put a black pixel there. Is this possible or should i just open gimp and start tracing by hand?if what you mean is going from the left picture to the right one:

[IMG]http://imgur.com/TWVj8[/IMG][IMG]http://i.imgur.com/TWVj8.png[/IMG]

- Use "Select by color" (on black, here), which will select the whole object
- Select/Border, use a width which is twice the line thickness you want (the "border" will straddle the existing selection limit, so half the border will be on the background)
- Invert selection
- Delete

It is otherwise easier that most people think to redraw the image with "paths" in the Path editor tool using the existing scan as a guide. I've done it often in Gimp but I believe it can also be done in InkScape, which may be another good choice depending on the envisioned use of the picture.

---

### Post by 11jmb on 2011-10-11
If you are looking to write your own program to do what ofnuts described, there are some fairly simple edge detection algorithms to do this.

[http://www.owlnet.rice.edu/~elec539/Projects97/morphjrks/moredge.html](http://www.owlnet.rice.edu/~elec539/Projects97/morphjrks/moredge.html)

gradient and laplacian methods are very simple. For a black/white image, it can be even easier, something like:

```

//loop through bit map
if(img[x][y] != img[x-1][y] || img[x][y] != img[x][y-1])
    edge[x][y] = true;
```

EDIT: I should note that this simple function will only work for black and white images that are very low detail (like the car above) if you are looking to do edge detection on an image that is more complex, use a more standard function. also, if you want to draw thicker lines like above, just set adjacent elements in edge to true as well

---

