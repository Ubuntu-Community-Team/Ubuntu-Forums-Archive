---
title: "xml web menu"
date: 2008-01-05
forum: Programming Talk
---

### Post by tjpren on 2008-01-05
Hi, 

I'm wondering if anyone has a link, or good open source code they are willing to share for web page navigation, preferably with an xml file containing the links.

I've found several commercial ones, but they don't provide much help to learn programming from.

I'm using Apache as the web server, and preference would be for php code, although I note that most commercial products seem to have java as the source.

Regards

tjpren

---

### Post by Samhain13 on 2008-01-05
Hi! I've written "something" that sort-of does what you're saying. By "sort-of", I mean I don't think it will do exactly what you're thinking but I would hope that it's close enough.

It's a bit hard to describe but I'd love it if you can take a look at it and give me an opinion.
You can find it here: [http://www.abcruz.com/lunax23/](http://www.abcruz.com/lunax23/)

---

### Post by tjpren on 2008-01-05
Hello Samhain13,

I've had a look at your suggestion and your website - very impressive.  Your way above me, however in the programming stakes.

Your idea is similar to what I've been looking for - your top selection bar "General Information" and "Change log" being derived from from an XML file.  I tried adding another section to your XML to see if it would add another bar.

And following on from this, would be some means of having the selections drop down into more selections or URL's.

You've got the makings of a nice looking product.

Also your own website is very pleasant on the eye - well done.

Regards.

---

### Post by Samhain13 on 2008-01-05
> I tried adding another section to your XML to see if it would add another bar.

I don't believe it's going to work that way. But somewhere in your template, you can write this:

[php]
  $lunaX23->listRelated();
[/php]

By default, it's going to give you an unordered list (ul) with items and links that are derrived from the XML file and give you something like this:

```

      <ul class="navMain">
        <li><a href="/">General Information</a></li>
        <li><a href="/?args=ChangeLog">ChangeLog &amp; Journal</a></li>
      </ul>

```

You can change this behaviour in the class-lunaX23config.php file. You can even write your own method/s if you want something that's extremely different.

Anyway, thanks for checking the thing out. I hope you can find something useful in there. Cheers! :)

---

### Post by pmasiar on 2008-01-05
I looked for many options a while ago, and YUI (Yahoo User Iinterface) toolkit worked best for me (customizable and CSS styles are separated - no clashes with my custom ones). It has all the widgets you may ever need, including Menu:

[http://developer.yahoo.com/yui/menu/](http://developer.yahoo.com/yui/menu/)

---

### Post by tjpren on 2008-01-10
Hello,

Just an update on what I've found-

Its not quite XML, but the configuration for the site all resides in a file.

[http://www.smartmenus.org/]("http://www.smartmenus.org/")

offer a site menu builder, which is free for personal and charity use.

It seems pretty good at this stage, of my evaluation, and is sufficiently open source to allow for customisation.  Its all in Javascript, which is probably OK in that I can run anything I develop on both Apache and IIS.

Regards.

---

