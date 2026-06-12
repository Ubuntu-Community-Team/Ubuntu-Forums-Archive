---
title: "Searching for an engine"
date: 2008-06-04
forum: Programming Talk
---

### Post by x88a on 2008-06-04
i am creating a GUI for a camera.
the video will be shown on a self created web browser.
What is the code for the engine which can display videos in web browsers?
An example of code: Gtk::MozEmbed.new (this is the embedded version of firefox)
TQ

---

### Post by LaRoza on 2008-06-04
Web browsers can't play video (animated gif's, and SVG animations excepting).

You could (should) look at the applications called "cheese" and "camorama".

---

### Post by sq377 on 2008-06-04
And MJpeg: [http://cam1.uat.edu/CgiStart?page=Single&Language=0](http://cam1.uat.edu/CgiStart?page=Single&Language=0)

> What is the code for the engine which can display videos in web browsers?
Most all browsers should be able to do gif/streaming jpgs.  It depends entirely though on what kind of video stream is being sent to you.  You didn't specify what language, but gstreamer is a good library for dealing with video.  If it is a streaming image, mozembed wouldn't be a bad idea.  Good luck.

---

### Post by x88a on 2008-06-04
this is what i want to do.
Create a GUI for an ethernet camera.
This is the camera:-
[http://www.smartnd.com/sites/products/smart_cams/](http://www.smartnd.com/sites/products/smart_cams/)

So i am now planning to create a GUI for it using an internet browser.

Or do you guys have any other suggestions?

TQ

---

### Post by x88a on 2008-06-04
> **LaRoza said:**
> Web browsers can't play video (animated gif's, and SVG animations excepting).

You could (should) look at the applications called "cheese" and "camorama".

can camorama and cheese work with ethernet cameras?

---

