---
title: "[SOLVED] Black on black text in Firefox"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by HittingSmoke on 2008-08-20
After I installed [this]("http://http://www.kde-look.org/content/show.php/Sweet+Darkness?content=82654") theme some text input boxes in Firefox started displaying black on black text.

[Here is what my password entry boxes and many other text input boxes on various web sites started looking like after I installed this theme.]("http://farm4.static.flickr.com/3219/2781578513_1dd1330ed2_o.jpg") 

I installed Firebug and used Inspect Element to locate the HTML and Style sheet source and as you can see from [this screen shot]("http://farm4.static.flickr.com/3219/2781578513_1dd1330ed2_o.jpg"), by disabling "color: #000000" it makes the text readable in the regular gray that the email input box displays. (indicated by the red circle with a line through it under the style field)

I've tried messing around in Kcontrol to find a setting that will change the text input boxes back to black on white, or at least change all the text to a readable shade of gray to no avail.

If anyone can shed some light on a way to make my KDE theme not effect web pages please share.

At least I know since I changed it temporarily with Firebug that its possible to write a Greasemonkey script for a temporary fix.

Thanks in advance

P.S. Screenshots are linked due to large size, all links go to Flickr

---

### Post by linuxguymarshall on 2008-08-20
Yeah. If there is an answer please someone answer. This is the one problem that drives me away from using darker themes

---

### Post by bodhi.zazen on 2008-08-20
[http://ubuntuforums.org/showthread.php?t=873486](http://ubuntuforums.org/showthread.php?t=873486)

[http://ubuntuforums.org/showthread.php?t=509241](http://ubuntuforums.org/showthread.php?t=509241)

---

### Post by Bradtek on 2008-08-20
One answer is to use a dark theme that does not make your input boxes etc black.

I  use  Slickness (find it at gnome-look.org)
[[SIZE="4"]Screenshot[/SIZE]]("http://img522.imageshack.us/img522/236/screenshot4my0.png")

---

### Post by cdtech on 2008-08-20
This is how I fixed my fonts from being all white. I have no idea how it became that way, unless one of my themes changed it, anyway.

This is how I was able to change the toolbar colors:

You need to create a userChrome.css file (if it's not already created for you)

Open Places > Home Folder

In the folder toolbar select show hidden files

open .mozilla > firefox > *.default (the default folder)> chrome

If you have the userChrome.css file then:

right-click "userChrome.css" and select open with “text editor”

modify the code at the bottom of the page so it looks like this:

menubar, menubutton, menu, menuitem, menupopup, popup > * {
color: black !important;
}

Save the file

When you restart Firefox your font will be black

If you don't see the "userChrome.css" but have a "userChrome-example.css":

right-click "userChrome-example.css" and select open with “text editor”

Modify the code at the bottom of the page so it looks like this:

menubar, menubutton, menu, menuitem, menupopup, popup > * {
color: black !important;
}

Save the file as "userChrome.css"

Restart firefox

If you want the text to be white just add this code:

menubar, menubutton, menu, menuitem, menupopup, popup > * {
color: white !important;
}

Hope this helps.

---

### Post by rossjman1 on 2008-08-20
I have a similar question. In Open Office the tooltips are black with black text, when all other applications have white text with a black background (like it's supposed to be). How do I fix this?

---

### Post by HittingSmoke on 2008-08-20
Thanks a lot! I'm going to try and work this into a Greasemonkey script so I can keep my number of installed add-ons down, Ill post the results when I'm done.

---

### Post by HittingSmoke on 2008-08-20
> **bodhi.zazen said:**
> [http://ubuntuforums.org/showthread.php?t=873486](http://ubuntuforums.org/showthread.php?t=873486)

[http://ubuntuforums.org/showthread.php?t=509241](http://ubuntuforums.org/showthread.php?t=509241)

Ok, I copied the Stylish scrips into Greasemonkey with a few minor edits and edited the forms.css as the tutorial instructs and now I dont have **any** background what so ever on text boxes. It's better than it was since now I can actually see what I'm typing, but a bit annoying as there is no way to tell where text input boxes are without randomly clicking around where I think theyre supposed to be. My google page is literally just a white background with a Google logo on it with a "Google Search button" and an "I'm feeling lucky" button. If I click between them I get a blinking text cursor that floats on the background image.

If anyone who's familiar with Greasemonkey and CSS thinks they can help I would be glad to offer my browser as a guinea pig. I just feel like Stylish is such a useless add-on to be taking up memory when Greasemonkey can do everything it can do and is much more widely used and useful. The Stylish scripts in the first link should be easily convertible over to Greasemonkey but unfortunately I dont know the code itself all that well.

---

### Post by HittingSmoke on 2008-09-02
I still havent found anyone who can help me turn this into a Greasemonkey script but I'm just going to mark it as solved as the Stylish scripts did the trick.

If anyone knows enough about CSS and Greasemonkey i would still appreciate it if this could be converted over.

---

