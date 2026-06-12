---
title: "dhtml script for creating screenshot"
date: 2007-06-11
forum: Programming Talk
---

### Post by mhancoc7 on 2007-06-11
I hope this is the right place to ask this question. :)

I have built a little web page for building Ubuntu Avatars. You can check it out here.
 ( [Ubuntu Avatar Builder]("http://www.whatwouldjesusdownload.com/drag/drag2.html") )

I would like to be able to add a button to allow the user to take a screenshot of the "work area" and save it to their desktop. For now I have just included simple instructions for making the screenshot and then the user must use GIMP to crop out the rest of the page. It would be nicer if some of the work could be automated.

Any ideas or advice is appreciated.

Thanks in advance, Jereme

---

### Post by Max_Might on 2007-06-11
I think this is not possible ...

---

### Post by aks44 on 2007-06-11
> **Max_Might said:**
> I think this is not possible ...

I am *sure* it is not possible ;)

---

### Post by WW on 2007-06-11
If I *had* to make something work, I would look into a CGI script.  The web page would pass back to the server the locations of all the graphical elements (or just those that are within a certain region). The CGI script would then use a graphics library (imagemagick comes to mind) to build a single image from the pieces that are in the prescribed region.

Of course, you might not want to (or be allowed to) burden your server with CGI scripts, in which case this suggestion is no help. :(

---

### Post by mhancoc7 on 2007-06-11
> **WW said:**
> If I *had* to make something work, I would look into a CGI script.  The web page would pass back to the server the locations of all the graphical elements (or just those that are within a certain region). The CGI script would then use a graphics library (imagemagick comes to mind) to build a single image from the pieces that are in the prescribed region.

Of course, you might not want to (or be allowed to) burden your server with CGI scripts, in which case this suggestion is no help. :(

I can use CGI, I just do not know where to begin. :confused:

Jereme

---

### Post by tturrisi on 2007-06-12
I'm not sure why a user would even need a screenshot of the work area!
The user may wish to be able to preview a larger scale image of what he has created, whch could easily be done by displaying the image inside html tags and setting the ```
style="width:xx height:xx:"
```.  The preview could work much the same way this forum preview works.

---

### Post by mhancoc7 on 2007-06-19
> **tturrisi said:**
> I'm not sure why a user would even need a screenshot of the work area!
The user may wish to be able to preview a larger scale image of what he has created, whch could easily be done by displaying the image inside html tags and setting the ```
style="width:xx height:xx:"
```.  The preview could work much the same way this forum preview works.

I am not sure I follow. The idea is to be able to download the created avatar easily. For now I have instructions for the user to take a screenshot and crop out the avatar. I would prefer that at least some of the work, "cropping", was done automatically.

Jereme

---

### Post by tturrisi on 2007-06-19
Seems to me you should be able to track the coordinates of the objects as well as the object ids placed onto the drawing area if the drawing area was a grid (x & y).  This data should be available via the DOM.   When the user is finished he clicks a button that executes a function which grabs the objects by id that are on the grid, along with their relative positions and then displays them in a popup window assembled.  The key would be to have the same image dimensions for all objects so as to be able to more easily assemble them by grid position, and to use a grid with finite dimensions.  The present drawing area could be scaled 2x or 4x 0r 10x the actual generated icon.

You'd also need to add error checking so the user can have only one of each object type, i.e. one face only, one mustache only, one mouth only, etc.

---

### Post by bcnaat on 2008-04-22
This was fun, thanks! Will post my avatar in a moment.

---

