---
title: "Web dev in linux"
date: 2009-08-11
forum: Programming Talk
---

### Post by nipunreddevil on 2009-08-11
What would be an ultimate package for web development on linux.
Like on windows photoshop+flash+php+dreamweaver is generally used.

---

### Post by furuno on 2009-08-12
It depends on what platform you're using for your web development and your "primary" task (e.g. web programmer / designer).

For example, as an Java web programmer, I'm using these :
- NetBeans IDE as my integrated development environment, it also handle HTML quite well.
- Sun GlassFish Application Server as the server, I'm using the one bundled with NetBeans for simplicity sake thought...
- XAMPP it provides easy installation and nice tools for MySQL.
- Apache Wicket Web Application Framework, it's my favourite Java MVC framework.

Recently, I'm learing Ruby on Rails, and here's what I'm used :
- GEdit, yes it's that simple.
- Terminal for running Rails script and Rake commands.
- Obviously, Ruby on Rails framework itself.

For PHP, I guess these will do :
- NetBeans IDE, it also includes PHP support.
- XAMPP, all-in-one server for Apache, MySQL & PHP (and more).

Of course, NetBeans is not the only IDE around that you can use as Dreamweaver replacement. There's also Aptana Studio, Eclipse, and many other. Aptana is more HTML and web development specific thought...

If you're more into design then I guess you'll need GIMP, as a replacement for Photoshop. For flash, well, I just don't want to recommend people to use flash on their website. Flash is a propietary technology and require a specific browser plugin, not too mention it needs quite a processing power. I think that AJAX is a  much better solution for creating Rich Internet Application (RIA), or mabe the upcoming HTML5 standard.

---

### Post by nipunreddevil on 2009-08-12
does ajax give same visual appeal as Flash?

---

### Post by AliTabuger7 on 2009-08-12
What are you really looking for in your set up?

If you like the full studios/suites, you could try Aptana.

Really, all you end up using is a text editor though.

I'm a pretty established web developer. I made [http://spreadubuntu.neomenlo.org/](http://spreadubuntu.neomenlo.org/) which is up for the official domain name now.

I find suites like that to be bulky and unnecessary. I use nautilus (file manager) and gedit (text editor). Its actually really nice in the newer versions of Ubuntu, since you can edit the document and save it just like it was on your own hard drive, even if its on FTP.

Every now and then, you might want to optimize an image. You'd want GIMP for that, and this plugin [http://www.getdeb.net/app/GIMP+%22Save+for+Web%22+plugin](http://www.getdeb.net/app/GIMP+%22Save+for+Web%22+plugin)

I think you'll find that even though GIMP is slightly confusing at first, it does everything you need or want it to do.

I don't know what to do about flash, it's best to avoid flash whenever possible anyway.

Hope that helps.

---

### Post by nipunreddevil on 2009-08-12
All i wish to do is to make a personal website.don't know where to get started.Some one recommended PHP.What all tools are most commonly used by beginners?and i intend to add features like drop boxes for additional visual appeal

---

### Post by AliTabuger7 on 2009-08-12
Depends on the site, but it's almost always best to start with a framework like Drupal, Wordpress, or Joomla depending on the purpose. It makes it easier to expand and maintain, while still allowing you to customize the appearance. Or you could just keep it really easy and use one of their great themes.

Again, it depends on what you want to do with it.

---

### Post by nipunreddevil on 2009-08-12
> **AliTabuger7 said:**
> Depends on the site, but it's almost always best to start with a framework like Drupal, Wordpress, or Joomla depending on the purpose. It makes it easier to expand and maintain, while still allowing you to customize the appearance. Or you could just keep it really easy and use one of their great themes.

Again, it depends on what you want to do with it.
But all these are for general public who have no programming experience.
I am a programmner and love to code.Would you still recommend using these?

---

### Post by froggyswamp on 2009-08-12
For PHP I'd certainly suggest NetBeans (heard lots of good comments about PHP support in NetBeans).

Java - NetBeans (or Eclipse)

But, with flash development on Linux you're out of luck - there's nothing that can match Adobe Flash CS4, Dreamweaver and alike. Adobe is creating a flash plugin for Eclipse to run on Linux, but it's far from what you have with Adobe's professional software suits.

---

### Post by Zeroangel on 2009-08-12
As a web developer who writes in HTML and PHP, I would have to recommend Quanta Plus (sudo apt-get install quanta) -- which is far superior to ANY free HTML that i've used in Windows (Arachnophilia, 1st Page 2000, CuteHTML, etc)

-- syntax coloring for HTML/PHP/CSS and other web programming/markup languages 
-- customizable for snippets and code templates 
-- project management with local/remote website synchronization and one click upload
-- Preview prefix (ie: [http://localhost/projectname/](http://localhost/projectname/)) allowing one to preview PHP and other server processed pages on a local webserver.
-- Rudementary WSIWYG capability

Be warned its a KDE3 app, so the interface will look out of step with your current themes, but that can be fixed.

As far as graphics go, you could go for the GIMP, but I prefer Photoshop as it's more polished and can accomplish more things than the GIMP can, but in half the time. CS2 can be installed via the wine-doors application.

> does ajax give same visual appeal as Flash?
Yes it can. You can use AJAX not only to animate things, but to get things to interface more seamlessly. Like for example, if you were to click on 'edit' your own post, your post would change to a box that you can type into -- without having to reload the page. That's javascript at work, which is a key component of AJAX. Facebook chat uses AJAX to display the chat box on the screen without reloading the page or causing any interruption to what your doing. And numerous sites use AJAX for pop up navigations and to use effects such as tabs and things that expand and disappear. These are far superior to flash for the reason that the content can be indexed by search engines and the data it contains can be more easily passed to other things.

---

### Post by AliTabuger7 on 2009-08-12
> **nipunreddevil said:**
> But all these are for general public who have no programming experience.
I am a programmner and love to code.Would you still recommend using these?
Yes. You don't want to waste time coding the login button, or user tracking. You want to code features right? Drupal is probably the best choice for a programmer. 

Javascript/AJAX is a much better solution than flash in most cases.

---

### Post by airtonix on 2009-09-16
> **AliTabuger7 said:**
> Yes. You don't want to waste time coding the login button, or user tracking. You want to code features right? Drupal is probably the best choice for a programmer. 

Javascript/AJAX is a much better solution than flash in most cases.

gogogo drupal + jquery.

only problem I'm having with gedit right now is its dependance on gvfs and in turn, the inability gvfs has to deal with ftp servers that have connection and timeout restrictions.

gvfs likes to create lots of connections.

---

### Post by Can+~ on 2009-09-16
I use Fireworks running on Wine to handle web graphics, never liked Inkscape.

---

### Post by sunchiqua on 2009-09-16
Standard set of tools:

[LIST]
[*]Gedit
[*]NetBeans
[*]Firebug ( Firefox add-on )
[*]GIMP
[/LIST]

Not sure if I'll ever be able to get the same speed/quality ( GIMP ) as it was on Photoshop, but .. I like it :)

---

