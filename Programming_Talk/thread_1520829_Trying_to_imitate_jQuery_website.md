---
title: "Trying to imitate jQuery website"
date: 2010-06-30
forum: Programming Talk
---

### Post by vik_2010 on 2010-06-30
I was looking at the jQuery website, and trying to replicate it using only their icons, but not looking at their source code.

I had two big questions that I wasn't able to find out.

1] The navigation bar at the top: 
At the top of the website they have a navigation bar in which the links, when highlighted, display a light blue bar a couple pixels below.

     I know there is a

                a:hover {text-decoration:none;}

but I don't think that's it. The bar is displayed a lot lower than that css tag permits, and it comes in a bright-blue color completely different from the color of the text. How would you replicate that? Perhaps there are a number of different ways, but any would be acceptable. I don't think its Javascript, because the lines still come even with No-Script active.
Also, how to you get that dark line at the bottom of the bar separating it from the rest of the header? All i was able to manage was {background-color:#[some hex number];} inside a table i created specifically for the nav-bar, but my website still lacked that emphatic divider between the bar and the rest of the header.

2] Half way down the site they have a box in which they show "who else is using jQuery." They show a bunch of different icons for companies/sites like BOA, MLB, Drupal, etc. Looking at the source, I saw that all they did was create a series of tags like so:

<a href = "****">[Company name here]</a>

but didn't have any <img> tags at all. How do did they get the logo images when their source just makes it seem as though they're listing a bunch of hyperlinks?

Thanks,

-V

For example, here is there source for question 2]:
						<li><a href="[http://www.google.com]("http://ubuntuforums.org/view-source:http://www.google.com/")" class="jq-google" title="Google">Google</a></li>
						<li><a href="[http://www.dell.com]("http://ubuntuforums.org/view-source:http://www.dell.com/")" class="jq-dell" title="Dell">Dell</a></li>
						<li><a href="[http://www.bankofamerica.com]("http://ubuntuforums.org/view-source:http://www.bankofamerica.com/")" class="jq-boa" title="Bank of America">Bank of America</a></li>
						<li><a href="[http://www.mlb.com]("http://ubuntuforums.org/view-source:http://www.mlb.com/")" class="jq-mlb" title="Major League Baseball">Major League Baseball</a></li>
						<li><a href="[http://www.digg.com]("http://ubuntuforums.org/view-source:http://www.digg.com/")" class="jq-digg" title="Digg">Digg</a></li>

---

### Post by myrtle1908 on 2010-06-30
Consider using Firebug to assist you here.

[http://www.getfirebug.com](http://www.getfirebug.com)

You can easily inspect DOM elements, style, javascript etc.  See attached screenshot.

Good Luck

---

### Post by vik_2010 on 2010-07-01
thanks, i'lll take a look at it.

---

### Post by Mr. Picklesworth on 2010-07-01
The &#8220;Who's using jQuery&#8221; links are using a technique called CSS sprites:
[http://css-tricks.com/css-sprites/](http://css-tricks.com/css-sprites/)

The blue bar is probably a border, and you can achieve a soft glow with the CSS3 drop-shadow property (although that only works in some browsers).

---

