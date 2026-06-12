---
title: "Take a screenshot of a java applet and crop image"
date: 2011-03-28
forum: Programming Talk
---

### Post by diabolicalangle on 2011-03-28
Ok here's what I'd like to do:

Take a screenshot, or some other way of saving the visual output of a java applet (
[http://www.nextbus.com/googleMap/googleMap.jsp?a=georgia-tech&r=blue&s=nortavea&r=red](http://www.nextbus.com/googleMap/googleMap.jsp?a=georgia-tech&r=blue&s=nortavea&r=red)), and saving that as an image, without having to manually do it (open browser go there, and take a screenshot).

I guess this would be most easily done using a script of some sort, but I have no idea how to go about doing this.. 

I would like to do this, so I can use this image to update my conky every 30 secs or so (got that part figured out :smile:). 

I got this as a suggestion:

If the webpage doesn't have an API so that you programmatically can get an image, you'd still have to open a browser.
With that in mind you could create a script that would
* Open the page in a browser
* Save a screenshot image using ImageMagick/import (or any other screenshot grabbing with CLI)
* Close the browser

Suggestions:
Install **imagemagick** and use the *import* command to grab a screenshot
Maybe install **wmctrl** and use it to run the script in another workspace (don't know if it would work though)

Not sure about how to go about implementing the suggestion. The only programming experience I have is a little bit with python, and html.

Thanks a ton for your help and time!

UPDATE:
Figured out how to open in new window with wmctrl, so now all i need help on is how to take a screenshot of the window through script/bash!

---

### Post by diabolicalangle on 2011-03-28
UPDATE 2:

I got how to take the screenshot of the object through -import (imagemagick), however it is only able to take the screenshot if the browser is on the same workspace. Does anybody know of any method to take a screenshot of a window on another workspace without going to that workspace?

Another idea I have is to open the browser starting minimized (got that part), but I'm having troubles figuring out how to take a screenshot of a minimized window.

Any solutions or tips would be very helpful!

---

### Post by supergirlkara on 2011-04-06
Maybe it would be easier to log packets with wireshark and see where the java applet is downloading the image and then downloading it yourself via your script. Screenshot code from my experience only works on the visible workspace, and windows. A screenshot captures only what prt scrn button can capture. I hope this helps you.

---

