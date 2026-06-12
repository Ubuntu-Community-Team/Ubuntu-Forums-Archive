---
title: "replace colours in gimp"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Stefanie on 2008-06-19
how do i replace colours in gimp? 
for example this wallpaper [http://gnome-look.org/CONTENT/content-pre1/75393-1.jpg](http://gnome-look.org/CONTENT/content-pre1/75393-1.jpg) is grey and black, let's say I want orange instead of grey and red instead of black (without changing the pattern and the different shades of course).  how can i do this?

---

### Post by golgo13 on 2008-06-20
not sure if thats possible without access to the different layers

---

### Post by Dynaflow on 2008-06-20
Use Select -> By Color to isolate color regions, then use Bucket Fill to fill them in with your preferred colors.

---

### Post by argail1980 on 2008-06-20
that won't give you a decent result I suppose. basically it's done like that, but looking at the picture this will not work. can you get you hands on a vector-based copy of the file, like an Inkscape-svg? 

Otherwise... no chance pal..

---

### Post by aeiah on 2008-06-20
i know what you're after but i cant find it right now. perhaps this will do for this example though, since you're starting off with greyscale.

tools > color tools > colorize
or 
tools > color tools > hue-saturation

---

### Post by drs305 on 2008-06-20
Here are my notes about changing colors in gimp. I don't have access to gimp at the moment but see if this makes sense:

Look at image title -  if not RGB save it as .png or .gif
To change color wherever it is in entire image:
Select 'Color Tool' &#8211; (rectangular 3-color bar on top row)
Click on color to be changed
Select Edit and choose: Clear to eliminate color
Edit and fill with a) foreground color or b) background color

To change color in only one contiguous area:  use the fill bucket

---

### Post by Stefanie on 2008-06-20
ok thanks everybody, i'll give it a try. working with gimp is really difficult i think...

---

### Post by Ixtao on 2011-02-12
> **drs305 said:**
> Here are my notes about changing colors in gimp. I don't have access to gimp at the moment but see if this makes sense:

Look at image title -  if not RGB save it as .png or .gif
To change color wherever it is in entire image:
Select 'Color Tool' – (rectangular 3-color bar on top row)
Click on color to be changed
Select Edit and choose: Clear to eliminate color
Edit and fill with a) foreground color or b) background color

To change color in only one contiguous area:  use the fill bucket
I find this method very effective.. I just zoom in click the colour I want to replace and press Ctrl+, (the shortcut for fill with foreground colour). First it took me ages to do it with the bucket tool ;)

---

### Post by Pyrosopher on 2011-02-12
Hi Stefanie,

I saw this post and thought I'd do a quick tutorial on it since I doubt that you're alone in having the question. 

[http://photodigitalis.blogspot.com/2011/02/changing-background-of-wallpaper.html](http://photodigitalis.blogspot.com/2011/02/changing-background-of-wallpaper.html)

I hope you find this interesting even after so long!

All the best,

Rob

---

### Post by authentictech on 2011-06-22
As this thread is still popping up in Google searches I thought I'd add what I think is a simpler solution than some of the above:

Menu: Colors > Map > Color Exchange...

Obviously, any shading will also have to be replaced manually this way, so perhaps not ideal for the OP.

I'm using GIMP 2.6.11.

---

### Post by ChaosFreak on 2011-12-25
I used to use Paint Shop Pro and they had an awesome tool called "color replacer" which allowed you to select a foreground color and background color and then it would replace one with the other (depending if you left-clicked or right-clicked). You could even set the tolerance. This was a perfect tool for doing this. I haven't found anything in Gimp that comes close. Does anyone know of any tool in Gimp that is comparable? It seems like a very common task. I certainly need it often.

---

### Post by ChaosFreak on 2011-12-25
> **drs305 said:**
> Here are my notes about changing colors in gimp. I don't have access to gimp at the moment but see if this makes sense:
 
Look at image title - if not RGB save it as .png or .gif
To change color wherever it is in entire image:
Select 'Color Tool' – (rectangular 3-color bar on top row)
Click on color to be changed
Select Edit and choose: Clear to eliminate color
Edit and fill with a) foreground color or b) background color
 
To change color in only one contiguous area: use the fill bucket
 
Just followed this method and it works great!!! Thanks.

---

### Post by jtarin on 2011-12-25
At times I find changing the color the most manageable part.......sometimes isolating the area/region can be the labor intensive part. For fine selection at times I use the pen tool and zoom to isolate the region I want to work on. You can grow or shrink the selection region by a determined number of pixels to optimize your selection.

---

### Post by oldos2er on 2011-12-26
Old thread is old. Closed.

---

