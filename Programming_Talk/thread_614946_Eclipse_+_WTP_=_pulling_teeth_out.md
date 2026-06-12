---
title: "Eclipse + WTP = pulling teeth out"
date: 2007-11-16
forum: Programming Talk
---

### Post by ICEcoffee on 2007-11-16
First off, I'm new to linux. I'm looking for a web development replacement for my WinXP setup, whereupon I mainly used DW8 with a WAMP server.

Searching through the forums, many people have advocted various applications, including, Bluefish, Quanta and for die-hard coders, Gedit. Many people have suggested Eclipse is a 'serious' IDE coupled with WTP for PHP and CSS coding. I think perhaps Quanta may be enough for my needs, but I'm someone that feels he never wants to miss out on anything. 

I've downloaded and installed Eclipse and Java 5, following some forum advice, but I can't find how to load the web tools environment. In fact, I keep finding threads that talk of failed installation, for one reason or another. One person even mentioned the fact that there was an all-in-one sollution that can be downloaded from the WTP site, but I can't find the right page to download from, nothing obvious.

Has anyone come across a how-to for idiots? or a link for the all-in-one page with help notes on how to install? and would I have to uninstall current installed software first?

Thanks for the help and sorry for the long post, I just wanted people to have  as much detail as possible.

---

### Post by CptPicard on 2007-11-16
WTP is for Java web application development.

And yes, it is horribly buggy still (last time I checked) like most Eclipse plugins seem to be... or maybe I just have bad luck.

If you really are into Java web app development (which you don't seem to be), I would recommend Netbeans... that's what I use. It integrates the toolkit so much better.

---

### Post by pmasiar on 2007-11-16
For Java/Struts I used myEclipse (paid plugin), could not figure out WTP.

But then I had luck, boss talked to smart people, and he let me do wep apps in Python/Turbogears. Much simpler and much slicker than Java/Struts IMHO.

---

### Post by ICEcoffee on 2007-11-16
If installing Eclipes with WTP in Linux is buggy and a bit of a hoo-ha, What advantages are there in using Eclipse+WTP?

What is a web developer to do?

I need do develop sites using the usual suspects: XHTML, CSS, PHP, MySQL and sometimes, add a touch of javascript. Any suggestions, that would save me hours in testing the different apps?

---

### Post by CptPicard on 2007-11-16
> **ICEcoffee said:**
> If installing Eclipes with WTP in Linux is buggy and a bit of a hoo-ha, What advantages are there in using Eclipse+WTP?

For you, considering you're a PHP guy, none :)

But if you want something Eclipse-related, try Aptana. Would like to hear how you like it, I haven't bothered messing up Eclipse installation once again with another plugin that doesn't work.

> 
What is a web developer to do?


Lots of good editors in the repositories... hmmh... Quanta and Bluefish come to mind first. And then there's always Kate and gEdit ;)

Btw pmasiar... let's be fair: Struts is archaic. Then again, the more fancy Spring+Hibernate+Wicket approach is hell as well :D

---

### Post by pmasiar on 2007-11-16
PHP? Then you don't need WTP, IMHO - it is for Java.

What to do? learn Python and Turbogears - Model-View-Controller beats any PHP mess. :-)

---

### Post by tenmillionmilesaway on 2007-11-16
The WTP is mainly for the java behind the code, if you want to do php then their is a php plugin for eclipse (think its callled, wait for it, phpeclipse) i havent tested it tho.

If all you want is a html/css/javascript editor then look at aptana which is based off on eclipse and can be installed as a plugin to eclipse or run on its own.

Richard

---

### Post by ThinkBuntu on 2007-11-16
> **pmasiar said:**
> PHP? Then you don't need WTP, IMHO - it is for Java.

What to do? learn Python and Turbogears - Model-View-Controller beats any PHP mess. :-)
I haven't used it, but CakePHP amongst other frameworks is supposed to be very MVC. I hope to use it for my first independently developed web app, whenever "that client" comes along whose problems aren't adequately solved by a well-rounded Drupal installation.

---

### Post by Netom on 2008-02-06
I have been trying to get Eclipse running with WPT and PDT for a while, but cannot get the pluggins installed correctly. Some problems with dependencies.

I'm a PHP developer and I have tried several editors (Bluefish, gPHPEdit, Mozilla Composer, gedit),  but none of them give me the easy way to do thing that DreamWever used to; so I ended installing Wine and DreamWeaver.

Beside some minor integration problems (the color picker does not work well, and it cannot read file directly from Samba shares unless you mount them) it works smoothly.

---

