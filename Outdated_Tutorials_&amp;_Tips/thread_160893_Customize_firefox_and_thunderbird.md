---
title: "Customize firefox and thunderbird"
date: 2006-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by adam.tropics on 2006-04-15
The activity indicator in both firefox and thunderbird , aka 'throbber' can be changed to whatever you like, brand /theme your browser!!

For firefox (1.5.01 anyway), go to $~/.mozilla/firefox/*********.default /chrome (your profile folder, and do 

$ gedit userChrome-example.css

add 

/*Throbber Control*/

toolbar #navigator-throbber { list-style-image: url("static.png") !important; }
toolbar #navigator-throbber[busy="true"] { list-style-image: url("animated.gif") !important; }

/*

changing the '("static.png")' and '("animated.gif")' to your desired graphics, which you should save in that folder also. Change the file name to userChrome.css and you're off! (gif or png graphics willd do fine)

restart firefox... hey presto!

For thunderbird the process is similar....

Open the folder ~/.mozilla-thunderbird/*********.default , and create  a folder
called 'chrome'. Then create a file called userChrome.css, and in it put the same....

 
/*Throbber Control*/

toolbar #navigator-throbber { list-style-image: url("static.png") !important; }
toolbar #navigator-throbber[busy="true"] { list-style-image: url("animated.gif") !important; }

/*

..again, copying the graphics to that local folder.

Alternatively, you could use the firefox extension 'ChromEdit' to manipulate these files. However, if using firefox 1.5 or higher, you will need to download the extension to your computer, open it up (the .xpi file is really just a zip file), open 'install.rdf', and edit the 'maxversion' to something lijke 1.6 in order for it to install.

end result...

[IMG]http://img.villagephotos.com/p/2006-4/1171854/Screenshot.jpeg[/IMG]

---

### Post by gorilla_king on 2006-07-11
very cool, i'll have to try it when i get home this afternoon.

---

