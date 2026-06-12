---
title: "blogging in php"
date: 2007-07-31
forum: Programming Talk
---

### Post by sdmike on 2007-07-31
Is there a package like phpbb where I can load the software onto my website so I can have my own blog in my site?

---

### Post by roncrump on 2007-07-31
I think there are lots.

Personally I use [wordpress]("http://wordpress.org"): under active development, lots of users, customisable, lots of plugins. Make sure you use take anti-spam measures (eg akismet plugin), but that would apply whatever blogging software you choose.

If you'd like to see where I use it, look at [http://newenglandnomads.net]("http://newenglandnomads.net").

Ron.

---

### Post by nitro_n2o on 2007-07-31
you can also use drupal drupal.org

---

### Post by Modred on 2007-07-31
[http://www.opensourcecms.com/](http://www.opensourcecms.com/)

They have a large number of PHP-based content systems, categorized by primary function.  There are 15 blogging applications, plus many CMS frameworks, like Drupal, can also be used for blogs (on another note, many people use WordPress as a basic CMS and more than just a blog, so this trend goes both ways).

Each product on that site should have a live demo online that you can try, so play around with several of them and find the one that you like.

---

### Post by bbzbryce on 2007-08-01
I second wordpress. Just make sure to get the wp_cache plugin otherwise your server will likely crash during a surge of traffic.

---

### Post by bobbocanfly on 2007-08-01
<shamelessPlugging>
I am writing one at the moment. The only difference to every other package available is that poor people can use it as it uses XML files as the database instead of MySQL. Its called Blinkwalla (Bobbos Linkwalla, sad i know)(Based on Linkwalla for which there is a demo at [http://www.benbrophy.com](http://www.benbrophy.com)).
</shamelessPlugging>

---

### Post by smartbei on 2007-08-01
Wordpress is by far the most used comprehensive blogging package for PHP. Others are also available (Drupal, Joomla, etc.) but these are meant to be online portals, with an optional blog component.

bobbocanfly's shamelessPluging (:)) sounds interesting, I would be interested in taking a look at it when it is done.

---

### Post by Note360 on 2007-08-01
that Blinkwalla or whatever it is looks really cool. Who develops it?

---

### Post by b20963a2 on 2007-08-01
Wordpress +1

---

### Post by bobbocanfly on 2007-08-02
> **Note360 said:**
> that Blinkwalla or whatever it is looks really cool. Who develops it?

Wow! I thought i'd get flamed for plugging that. Ok, Blinkwalla is currently my ittle toy, based on a Blog engine called Linkwalla, which is unique as it uses Flat XML files to hold all the data in. Linkwalla isnt currently under any development so with the permission of the Linkwalla developer, decided to fork a new version Blinkwalla. Currently Blinkwalla is just Linkwalla with a pile of extra code on it and not very stable, but yesterday i began writing Version 0.2 totally from scratch which will hopefully add MySQL support to the engine. It is only developed by me at the moment but i am searching for people to help me out. The website is at [http://www.sourceforge.net/projects/blinkwalla](http://www.sourceforge.net/projects/blinkwalla)

</lifeStory>

Time for me to go and actually write some code :D

---

### Post by kknd on 2007-08-02
I use and like Wordpress for blogging =). For content management there are other alternatives, like pmwiki and so.

---

