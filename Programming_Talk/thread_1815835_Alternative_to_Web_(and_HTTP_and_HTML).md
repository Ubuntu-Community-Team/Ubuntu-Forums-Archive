---
title: "Alternative to Web (and HTTP and HTML)?"
date: 2011-08-01
forum: Programming Talk
---

### Post by anarkhos on 2011-08-01
Has anyone recently explored creating an alternative to the World Wide Web?  It seems to me that the web and html are a bit like dinosaurs.  I'd be very interested in knowing if someone out there is pursuing a brand new protocol and display language.  

Here me out, please, because I imagine you are thinking I'm completely nuts--maybe I'm only slightly nuts.

For instance, one possible benefit is if a front end was basically a Photoshop/Gimp document with variables embedded.  Then there would be no overhead of doing PSD-to-HTML/CSS conversions.  There wouldn't be a conversion--the front end would always be edited by a program designed for artists--instead of text editors on steroids.

Similar to QT design editor, one can make aspects of the front-end *pixel-perfect*.

Another benefit would be better cross platform display of things that the web still has trouble with, such as fonts.  

I suppose one could say that Flash and Silverlight fulfill what I would like to see.  But they really don't.  For one, a technology which totally stymies SEO will never replace HTML.  There is also the question of allowing small chunks of front-end (such as header/left/center/right/footer) to be brought into a page as the URL changes, IE a templating system. 

In any case, has anyone read about anything similar to what I describe?  Thanks for your time everyone.

---

### Post by soltanis on 2011-08-01
So basically, more media. Isn't that the point of HTML5?

You could make an entire website out of a static image, but then separating the site from the text markup and style sheets which describe it makes it much more difficult to do things like scale fonts to different display sizes, easily change templates and site layouts, and generate dynamic content. I would agree that in many cases, that markup could be simplified, but that's what you get when you grow a set of standards such as HTTP and HTML over almost two decades of development now.

---

### Post by Zugzwang on 2011-08-01
@OP: What you are proposing (as HTML+images replacement) would be highly problematic. While your approach has its merits, it would lead to serious problems with the accessibility of the web pages created that way: users of mobile devices would see a web page that is barely usable at their resolutions as a font size that is suitable for viewing the page on the desktop is too small on a mobile device. The same thing applies for people with their screen far away/very close on the desktop or web users with smaller disabilities (e.g., no good sight), which require the script size to be scalable. Also, there are special devices for blind people to use the internet, which wouldn't be possible in your graphical approach. By the way, what about users with very wide screens? Would you not allow them to use its width by default?

Note that making a web site that is visually appealing in all usage circumstances is one of the reasons why professional web design can be quite challenging.

---

### Post by anarkhos on 2011-08-01
Thanks for the replies.  I think I should have been more specific, I'm sorry.

I wasn't looking to discuss the pro's and con's of HTML or HTTP.  There are more more intelligent people than me that can do that:

[http://www.google.com/search?q=LIMITATIONS+OF+HTML](http://www.google.com/search?q=LIMITATIONS+OF+HTML)
[http://www.google.com/search?q=LIMITATIONS+OF+HTTP](http://www.google.com/search?q=LIMITATIONS+OF+HTTP)

My goal was to see if anyone knew of any next-generation Internet Application protocols/display languages that are being tinkered with.

I personally have very strong doubts that HTML5 or HTML6, or even HTML16 will fully provide solutions to all site developers for the next 100 years.  So, I'd love to know if anyone has worked on or written about alternatives.

thanks all, sorry for the confusion!

---

