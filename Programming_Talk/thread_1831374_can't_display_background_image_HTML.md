---
title: "can't display background image HTML"
date: 2011-08-23
forum: Programming Talk
---

### Post by matrronchi on 2011-08-23
Hi there everybody,

I'm using a LAMP installation to create some personal sites.
I just can't understand why i won't be able to put a background image in the body section of my site.

Either if I use css or simple HTML when i try to put an image as background the result will be a blank page, or colored if I set a background color.

```
    
<body background="./image.jpg"> 
         
        <p>hello</p> 
     
</body>

``````

index.html:

<head> 
          
         <link href="style.css" rel="stylesheet" type="text/css" media="screen" /> 
      
 </head>

<body> 
         
        <p>hello</p> 
     
</body>

style.css:

body { 
    background-color: #FFFFCC;
    background-image: url(./image.jpg); 
    background-attachment: fixed; 
    font-family: Arial, Helvetica, sans-serif; 
    font-size: 12px; 
    color: #787878; 
}


```Any ideas on what i could be doing wrong?

Maybe there's some kind of module to activate in order to visualize images?

Any help will be very appreciated!!

Thanks!

---

### Post by gmargo on 2011-08-23
Both of those methods work for me.
Have you checked the Apache error log file?

---

### Post by PaulM1985 on 2011-08-23
Is you image.jpg definitely in the same folder as your index.html?  You have probably already checked this, but this sort of thing is the most common problem I have when pictures aren't displaying, the html isn't pointing to the file.

Paul

---

### Post by juancarlospaco on 2011-08-23
**background-image: url(image.jpg);**

---

### Post by matrronchi on 2011-08-24
I solved it.
It was not a path error but a permission problem on the image.
Enabling all actions on the image with chmod 777 image.jpg fixed the problem.

Thanks anyway for helping!!

Bye

---

