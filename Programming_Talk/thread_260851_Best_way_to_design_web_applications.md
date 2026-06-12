---
title: "Best way to design web applications?"
date: 2006-09-19
forum: Programming Talk
---

### Post by hagen00 on 2006-09-19
Hi 

Very general title, but I actually mean the following. My question is bascially about preventing duplication of code and best practice for designing your website. 

In designing web apps, I usually design them by including the content in the main index page. In this way my index page contains all the graphics and layout and the functional stuff is included i.e. [www.site.com/index.php?pg=aboutus](www.site.com/index.php?pg=aboutus)

The other way to design a web site would be to call seperate pages [www.site.com/aboutus.php](www.site.com/aboutus.php) and [www.site.com/contactus.php](www.site.com/contactus.php) etc and then include the graphics and other stuff in each page e.g. 
[PHP]include_once('includes/topgraphic.inc');[/PHP] 

What do you guys 'n gals reckon. Option top or option bottom. Any other better way to lay out websites?

Thanks

H

---

### Post by tminuszero on 2006-09-19
Ummmm .. neither. And both.

It all depends on the project - small projects that don't change don't need a huge solution, and either one that you choose will work.

Your first solution can work, but I would fiddle with the Apache rewrite rules some so you have better URL's. For instance instead of domain.com/index.pgp?pg=whatever make it resolve as domain.com/whatever . That jsut makes it easier to keep up with, link to, and maintain.

For larger projects, or sites that change often, you want to separate content from presentation as much as possible. You could use MVC (Model-View-Controller) architecture. [Ruby on Rails]("http://www.rubyonrails.com"), [Django]("http://djangoproject.com") and [CakePHP]("http://cakephp.org") all follow this structure. There's some others, also.

---

### Post by hagen00 on 2006-09-20
Thanks for the reply. However, what is the point of rewriting the URL? Just because it looks cooler? Won't necessarily make it more search engine friendly i think. But I've been wanting to use mod_rewrite for a while, but have never really gotten it right. It seems to be a huge nightmare. 

Can anyone give me the rewrite condition and rule for rewriting mysite.com/index.php?pg=aboutus into mysite.com/aboutus

What if more than one parameter is passed in the URL, will that then break the rewrite rules?

Thanks

H

---

### Post by tminuszero on 2006-09-20
I'm not sure about looking *cooler* - that's really subjective. But it does help with SEO (in my opinion) and it's just cleaner in case your site/application changes in the future. And personally I find it easier to figure out a link to [www.domain.com/products/cat8/desc](www.domain.com/products/cat8/desc) rather than [www.domain.com/index.php?pg=products&category=8&sort=desc](www.domain.com/index.php?pg=products&category=8&sort=desc)

I'll look around for that rule for you - I've used it in the past, but it I don't have it in front of me it's lost :)

---

### Post by skymt on 2006-09-20
mod_rewrite is great for making urls you can actually *say*. For example, would you rather say "go to http://www.example.com/coolstuff/index.php?page=foobar" or "go to example.com/foobar"?

---

### Post by tminuszero on 2006-09-20
Here's some examples, and I hope someone with more experience than me chimes in to make sure these are right :confused: 

```
RewriteRule ^photos/([0-9]+)/([0-9]+) index.php?section=Photos&action=ViewImage&ImageID=$2&album=$1
```

This URL:

[COLOR="Blue"]photos/12/432[/COLOR]

Rewrites to:

[COLOR="Blue"]index.php?section=Photos&action=ViewImage&ImageID=432&album=12[/COLOR]

After that you can assign other rules to the same URL. For instance:

```
RewriteRule ^photos/([0-9]+)/ index.php?section=Photos&action=ViewAlbum&ImageID=$1
RewriteRule ^photos/ index.php?section=Photos
```

---

### Post by tminuszero on 2006-09-20
Here's a [great cheatsheet]("http://www.ilovejackdaniels.com/apache/mod_rewrite-cheat-sheet/") that may help you out.

Also, in the examples I provided above, the ([0-9]+) portion is a regular expression for a number of a length of 1 digit or more. If you want to include letters, you have to do something like this: ([A-Za-z0-9]+)

---

### Post by hagen00 on 2006-09-21
Cool :) thanks very much. The cheatsheet is especially nice. I've always wanted something like that to help me out with RegEx

---

### Post by tminuszero on 2006-09-21
Funny you should say that - the same guy has a [cheatsheet just for RegExp]("http://www.ilovejackdaniels.com/cheat-sheets/regular-expressions-cheat-sheet/"). :)

---

