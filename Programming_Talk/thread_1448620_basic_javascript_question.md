---
title: "basic javascript question"
date: 2010-04-06
forum: Programming Talk
---

### Post by nonewmsgs on 2010-04-06
the html can bring up the picture just fine but the javascript doesn't??? why?  what am i doing wrong? sg1.jpg, sg2.jpg, etc are all valid picture files in 'Image' Directory.  also what would be the best way to sleep here?



```

<html>
<body bgcolor="White">
<script language="JavaScript">
function preloader() 

{


     // counter
     var i = 0;
               

     // create object
     imageObj = new Image();


     // set image list
     images = new Array();
     images[0]="Images/sg1.jpg"
     images[1]="Images/sg2.jpg"
     images[2]="Images/sg3.jpg"
     images[3]="Images/sg4.jpg"


     // start preloading
     for(i=0; i<=3; i++) 
     {
          imageObj.src=images[i];
     }

}
	//	setTimeout(preloader(), 500);
</script>


<p><Center>

 
<br><br><br><br>

<img height="300" width="300" src="Images/sg2.jpg">
</center>
</body>
</html>

```

---

### Post by nmccrina on 2010-04-06
Are you actually calling the preload function at any point? Maybe do like an "onload" attribute in the body tag or something?

---

### Post by nonewmsgs on 2010-04-06
thank you for your help nmccrina!  i was not calling the function at all.  i now call it but i still get no love.  i tried adding a <script>preloader();</script> and i also tried an onload (with and without quotes).

---

### Post by Compyx on 2010-04-07
The code you provided just loads images into the browser's cache, it doesn't display them. If you're looking for a way to 'animate' the images (I think that's what you intended to use the setTimeout() for) you would have to alter the 'src' attribute of the <img> element with a separate function.

The preloading technique is normally used to avoid 'lag' in rollover-effects such as changing an image when the mouse pointer hovers over it. If you didn't preload the other image, the first time you move the pointer over such an element the image would need to be loaded and you might see the image 'build up' while it's being loaded by the browser. Preloading avoids this problem by forcing the browser to load all the images needed and immediately loosing any reference to the images; but the images are in the cache and that's what the preload was for.

Switching or animating images can be done with setInterval():
```

function switchImage()
{
    // code to update src attribute of img goes here
}

// Somewhere your 'onload' event handler:
setInterval(switchImage, 500);

```

---

### Post by nonewmsgs on 2010-04-09
thank you for letting me know but if you can simplifiy it just a little bit and let me know the scr image i need to change it would help me even more.  

i am going to change my picture and that seperate function will be an easy fix for the 2nd part.  i never did javascript before and all the online tutorials seem to assume some knowledge of a basic thing i don't have.

---

### Post by Compyx on 2010-04-09
Something like this:
[PHP]
<html>
    <head>
        <title>Javascript image thing</title>
        <script type="text/javascript">

            // array holding image names
            var images = [
                'gnome-logo-icon.png',
                'gnome-home.png',
                'gnome-laptop.png'
            ];

            // image array index
            var index = 0;

            // this function preloads the images
            function preloader()
            {
                var imgObj = new Image();
                // iterate images array
                for (var i = 0; i < images.length; i++) {
                    // force browser to load image data into cache
                    imgObj.src = images[i];
                }
            }

            // called every 500ms, displays the next picture
            function updateImage()
            {
                // get reference to image element
                var el = document.getElementById('foo');
                if (el) {
                    // update src attribute of image
                    el.src = images[index++];
                    if (index == images.length) {
                        // reset images index to 0
                        index = 0;
                    }
                }
            }

            // onload event handler
            function onload_event()
            {
                // preload images
                preloader();
                // tell javascript to call `updateImage' every 500ms
                setInterval(updateImage, 500);
            }

        </script>
    </head>

    <body onload="onload_event();">
        <p>Hello World!</p>
        <img id="foo" src="gnome-home.png" />
    </body>
</html>
[/PHP]

---

