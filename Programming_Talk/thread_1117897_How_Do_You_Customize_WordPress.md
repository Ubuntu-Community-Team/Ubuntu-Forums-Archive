---
title: "How Do You Customize WordPress"
date: 2009-04-06
forum: Programming Talk
---

### Post by SuperMike on 2009-04-06
I'm a PHP developer. I have my own way of customizing WordPress, where I convert it from a blog engine and into a CMS to give a small business a "web presence" site with a contact form, calendar, and a newsletter signup.

The problem I'm having is that I stay fairly "canned" because I have found a theme that is customizable -- however some clients want something exotic. I mean, some clients may have already gotten a web designer to draw up a PSD or TIFF image, and then want me to convert that into a WordPress theme.

I can handle the PSD to XHTML/CSS chopping okay, but the problem I have is understanding the WP object model to pull the "Pages" and menu navigation feature into the XHTML. That is why I have been going with the canned approach of just customizing an existing theme and then commenting out Posts and Comments and Plugins.

So, what links do you have that can show me how to take *any* XHTML/CSS theme and attach it to a WP site?

---

### Post by SuperMike on 2009-04-07
I found my hope and inspiration here:

[http://www.jestro.com/web-design/convert-xhtml-css-to-wordpress/](http://www.jestro.com/web-design/convert-xhtml-css-to-wordpress/)

**This jestro guy gets a medal.** That code right there lets me take any XHTML/CSS template and convert it into a WordPress template.

Inside my template files, I also commented out comments and posts and stuck only with "Pages".

The next thing I did to my new theme was replace "the_content(...)" call from my index.php. I grepped for the function declaration of "the_content()" and then cut and paste that code. I didn't just want to paste it into index.php, so I made index.php include a file called content-hook.php, and that's where I pasted it. Next, right before the "echo $content" statement, I added this line:

$content = preg_replace('/\{([-A-Z0-9]+)\}/e','file_get_contents(TEMPLATEPATH . \'/hook-$1.php\')',$content,1);

What this does now is allow my pages in WordPress to support a template system where I can type in:

{CONTACT-FORM}

Once it sees this in all uppercase as an alphanumeric (plus hyphen) phrase in curly braces, it knows to try and call "hook-CONTACT-FORM.php" from the TEMPLATEPATH (my template's path).

This lets me insert PHP code right where I need it without having to mess with building a plugin and an admin interface, which would be overkill for just adding a contact form.

From there, I make the contact form use jQuery and AJAX to call a file from TEMPLATEPATH for inline form field validation, inline form posting, and an inline posting response.

Now, if I *did* need an admin interface, then yes, I'd be finding out how to copy and modify some existing plugin code.

Some people would just shrug their shoulders and go find a suitable plugin. However, from what I've seen, I have not been impressed with the quality of plugins used in WordPress. I have decided to just build my own stuff.

Another thing I noticed was that WP version 2.7 is a whole lot better than previous versions because it allows you to reorder your pages with a number, rather than in alpha order.

One thing you should also know is that you can make a functions.php page in your template folder and these will automatically be called by WP. (I haven't tested that, but someone told that to me.)

Some things I'm working on now:

* Making a tab bar that let's the end user add pages that can get added to the tab bar, and pages that are hidden from that bar but still able to be called if you know the path. Also, one might want to make the tab bar a little more exciting with some jQuery pizazz.
* Switching from ugly URLs (?p=2) into handsome URLs (/contact).
* Securing the wp-admin interface.
* Reading up on other .htaccess hacks for WP.

I'll address that a little later.

---

### Post by s.fox on 2009-04-07
Hi,

Thank you very much.  That link is incredibly helpful.  Next time I need to do something similar I will try out the guide.

Thank you.

---

