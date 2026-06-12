---
title: "create a website for all resolutions"
date: 2009-05-04
forum: Programming Talk
---

### Post by enduser000 on 2009-05-04
Hello,
    I have a friend that maintains a site and I want to get my own up sometime this summer so I am posting to ask about a problem that he's had that I'd both like to help him fix, and avoid myself.  How do you make a website for all resolutions?  ubuntuforums.org is a great example of this.  We're both going to have our sites in php too, if that helps.  Anyone know the best way to do this? Thanks,

enduser

---

### Post by hessiess on 2009-05-04
Just use the useural CSS layout techniques but use relative units (i.e. %) instead of fixes units such as pixels or EM.

There are lenty of examples on here
[http://www.oswd.org/](http://www.oswd.org/)

download the source and get hacking ;)

---

### Post by Nevon on 2009-05-04
Making a layout that works in all resolutions is a very, very hard thing to do. At least if you want to include static images in your layout. Because what do you think would happen if you had an image that was 500px wide and someone came to your site with a resolution of 800x640? Most likely the parent element of the image would be resized until it was too small to hold the image, which in turn would make the image "pop out" from its parent.

If you're not using any images, it's super easy. Just use relative measurements instead of fixed ones. For example % instead of px or ems.

---

### Post by enduser000 on 2009-05-04
Hey,
   So is there a good way to do it with images?  Cuz my friend uses a lot of em on his page, and I'll use a few--but I'll try to keep it simple so it works better.  Maybe there's a simple way to use gradients and backgrounds to avoid problems?  Anyways I'm gonna start soon and I'll let you know what I find,  Thanks for your help so far!

enduser

---

### Post by Reiger on 2009-05-04
To some extent or another: yes.

The good news: you could use SVG, which is called Scalable out of Scalable Vector Graphics for a reason. :)
The bad news: support is limited to browsers like Opera and Safari (I expect Firefox too). But the big missing player here is Microsoft with old & outdated but for goodness knows why still used versions of IE.

The good news: you can use relative width & height style properties on images to scale them; might be tricky to calculate right though (it's easy to get glitches due to rounding errors). The bad news: a raster image (PNG, BMP, GIF, JPEG) may scale really badly towards lower resolutions (try to view a 1920x1200 pic scaled to 1024x768 ); and higher resolutions are bound to be troublesome... Especially when you facto in the difference between aspect ratio (as in the example of 1920x1200 vs. 1024x768 ). There is a reason that Gnome/KDE etc. use multiple icon sets for various resolutions. ;)

---

### Post by hockey97 on 2009-05-05
it's a hard topic. I tried to find the answer myself. 

what I had trouble was that the elements on the page would resize and reposition. 

They often collide with other elements. What I done to just avoid elements from resizing and making the layout look ewwish.

I used javascript, php, and css,html .

what I did was used javascript to grab the internets browsers screen width and height.

I then passed it to php which passed it to the html and loaded it in the css code.

This css code then loads that value into the height and width of the <html> tag. 

This just cause the elements to not resize. It would make the website scrollable if the website is bigger then the resolution of the persons monitor. 

This is what I am using. It's not the best but at least avoids my elements from colliding with other elements. 


If you really want to make the design fit with otherpeoples resolution.


you need to use some math. Plus you need to have the css values for height and witdh and position to be variable.

then based on the persons height and width you then can make your own math to caculate  where each element is supposed to be  and also resize the element so it  the site would resize  and reposition based on the users resolution.

It's hard. My simple solution is just have the <html> tage a width and height to what reolution your site was developed with. 

This will make people that dosen't have your resoltuion to either scroll or their will be more space on the sides if the users resolution is higher then yours.

I think that is the simple solution. It's not the best but you will have to wait until all browsers follow the standards.

I wouldn't spend my time trying to do the math and figuring out the best way to do that. 

I would rather leave it to the makers of the web browsers.

---

### Post by enduser000 on 2009-05-05
Ok,
  I think what I'm going to try to do is write most of the site in html then have a separate html page for the middle of most of my pages.  I'm going to try to use php to get their resolution, then maybe I'll have php generate a new page for certain resolutions (with certain values).  My images are going to need to be scaled down a bit anyways, as they are a bit bigger than they should be.

I want to point out ubuntuforums.org again.  I'll probably be using a few more images then this, and my friend on his page uses many more, but theire resizes and everything.  The only time it looks weird is when you make it really small, which I would be okay with.  Anyways, thenks for your help, I'll post a link in a few months so you all can see ^^,

enduser

PS any advice is still appreciated, thanks.

---

### Post by enduser000 on 2009-05-06
Hello,
    So I've been coding a very little bit and have found out how I kind of want to do this. I've noticed that if I use ```
<img height="33%" ...
``` or ```
<style="height: 33%;" ...
``` it resizes the image accordingly.  I am ok with this and want to go this route.  My only new questions are these:

What about text?  How can I make it look ok with text? can I make the text resize? what about people who put their text larger?

and the question about overlapping images, which I posted [here]("http://ubuntuforums.org/showthread.php?p=7227462#post7227462") because it doesn't have a lot to do with the sites resolution.

Thanks for your help so far!

enduser

---

### Post by enduser000 on 2009-05-25
[SOLVED] - thank you for your help,

enduser

---

