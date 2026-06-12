---
title: "Beginner Web Page Designing"
date: 2010-07-17
forum: Programming Talk
---

### Post by psycho5 on 2010-07-17
Hello All,

I would like some recommendations on any software that is very user friendly and helps in designing a web site. Something that might have some templates to choose from. My web coding skills are extremely novice, and I wanna design an online store that should work in theory. Are there any applications that can help me with this? I searched in Software Center and found Bluefish, but that seems to be for experienced web designers. 

Also, I'd like to apologize to the admins if this post is under the wrong category.

---

### Post by sandyd on 2010-07-17
> **psycho5 said:**
> Hello All,

I would like some recommendations on any software that is very user friendly and helps in designing a web site. Something that might have some templates to choose from. My web coding skills are extremely novice, and I wanna design an online store that should work in theory. Are there any applications that can help me with this? I searched in Software Center and found Bluefish, but that seems to be for experienced web designers. 

Also, I'd like to apologize to the admins if this post is under the wrong category.
A) First, this is under the right category :)

B) Have you considered using any of the PHP turnkey site scripts out there? Their really easy to use, and they have millions of free templates on the net.

Joomla, Drupal, and e107 are some of them.
Most webhosts support php/mysql these days, and will therefore run those sites properly. A good starting point would be 000webhost

---

### Post by DanielWaterworth on 2010-07-17
php is a hideous language, it really is.

---

### Post by sandyd on 2010-07-17
> **DanielWaterworth said:**
> php is a hideous language, it really is.
unfortunately, the forum your surfing right now runs on it.

---

### Post by DanielWaterworth on 2010-07-17
I have no problem using web apps that someone else wrote using it. I'm just more likely to eat a pair of socks than program in it myself.

---

### Post by sandyd on 2010-07-17
> **DanielWaterworth said:**
> **I have no problem using web apps that someone else wrote using it.** I'm just more likely to eat a pair of socks than program in it myself.
Which is what im telling the OP to do. I told him/her to use php scripts such as joomla/drupal for their site. Those don't require any programming knowledge at all to design the site, nor does it require the editing of php.

---

### Post by DanielWaterworth on 2010-07-17
> **carlee said:**
> Which is what im telling the OP to do. I told him/her to use php scripts such as joomla/drupal for their site. Those don't require any programming knowledge at all to design the site, nor does it require the editing of php.

I suppose, but if you felt like you wanted to change any of the underlying system or do anything more advanced, you wouldn't have a choice but to face php.

This may sound like an odd argument, but I suppose it stems from one of the reasons I use open-source software. If I use exclusively open-source software then I know that it's possible to change any of the underlying code if I need to - all the way down to the operating-system.

If I used php, I'd see it as a barrier. It would be more difficult to control the system however I want. This problem isn't as big for beginners, but many beginners become advanced users in time.

Unfortunately and regrettably, I can't offer an alternative for beginners, this is the biggest flaw in my argument.

---

### Post by xsinsx on 2010-07-17
I agree with carlee on this using Joomla or Drupal maybe your best bet until you feel you wanna take a leap into learning HTML/CSS and php or one of the alternatives to it. But i agree Joomla is a nice alternative.

---

### Post by digitalcitizenx on 2010-07-17
bluefish

```
sudo apt-get install bluefish
```

---

### Post by sandyd on 2010-07-17
> **psycho5 said:**
> Hello All,

I would like some recommendations on any software that is very user friendly and helps in designing a web site. Something that might have some templates to choose from. My web coding skills are extremely novice, and I wanna design an online store that should work in theory. Are there any applications that can help me with this? I searched in Software Center **and found Bluefish, but that seems to be for experienced web designers. **

Also, I'd like to apologize to the admins if this post is under the wrong category.

> **digitalcitizenx said:**
> bluefish

```
sudo apt-get install bluefish
```.

---

### Post by CptPicard on 2010-07-17
Well.. in my mind it is not reasonable to expect to run a web store without the ability to hack even those turnkey solutions. Otherwise you really are totally locked to what they provide...

In general I fully agree with Daniel regarding the PHP bit though...

---

### Post by donsy on 2010-07-17
> **DanielWaterworth said:**
> This may sound like an odd argument, but I suppose it stems from one of the reasons I use open-source software. If I use exclusively open-source software then I know that it's possible to change any of the underlying code if I need to - all the way down to the operating-system.Which open-source software would you recommend for a small store-front application that uses a MySQL customer and product database?

---

### Post by Krupski on 2010-07-17
> **DanielWaterworth said:**
> php is a hideous language, it really is.

I really wish that web servers used plain old interpreted C as a language instead of "pseudo-C" abominations like PHP and Javascript.

---

### Post by Krupski on 2010-07-17
> **donsy said:**
> Which open-source software would you recommend for a small store-front application that uses a MySQL customer and product database?

I run a little message board using PHPBB3 which is an open source, free message board system written in PHP and HTML.

You will find, however, that if you want to setup and run a "website", you are going to have to learn a lot of little things.

If you're interested, take a look at my site... this is what PHPBB3 looks like (note that PHPBB3 supports MANY different themes... you are only seeing one of them): **[COLOR="Blue"]_[http://three-dog.homelinux.com/phpBB3/index.php](http://three-dog.homelinux.com/phpBB3/index.php)_[/COLOR]**

And, if you want to look into it, here's where to get the PHPBB3 message board software: [B][COLOR="Blue"][U][http://www.phpbb.com](http://www.phpbb.com)
[/U][/COLOR][/B]

You can customize the look and feel of the board, and you can add features to it, but you WILL need to get your hands dirty and learn some PHP, Javascript and HTML. You also will need to know how to setup a LAMP (**L**inux **A**pache **M**ySQL **P**HP) server (Ubuntu Server is ideal for this) in order to run ANY message board software.

Prepare to climb an initially steep learning curve... it's tough, but it's also fun.

Good luck!

-- Roger

---

### Post by CptPicard on 2010-07-17
> **Krupski said:**
> I really wish that web servers used plain old interpreted C as a language instead of "pseudo-C" abominations like PHP and Javascript.

How would it help to remove pretty much everything except basic control structures and introduce totally irrelevant to webapps yet bug-prone things like pointer handling?

Javascript is actually a fairly interesting language now that I've recently (due to job requirements) got into it... it has its warts, most importantly the lack of a proper module system, but they're not show-stoppers. I'm actually surprised how profound the prototype-based object system is, and having closures is always good.

---

### Post by shadylookin on 2010-07-17
If you want to learn how to do it then I would suggest starting with a smaller project and working your way up. figure out the client side with html css and javascript. Then find a server side language of your preference. If you're feeling particularly lazy you can even write server side code with javascript so you don't have to learn another language. 


Though if you just want an online store then I would recommend just hiring a professional to do it for you.

---

### Post by digitalcitizenx on 2010-07-18
> **digitalcitizenx said:**
> bluefish

```
sudo apt-get install bluefish
```

+1

---

### Post by DanielWaterworth on 2010-07-18
It seems to me that you have a choice when it comes to web-development.

There's the easy route (in terms of getting a server up and running quickly), where you go for something like drupal, joomla, wordpress, phpbb etc. Generally, big monolithic applications that try to do everything, and actually work quite well.

You never have to get your hands dirty coding, because there's loads of extensions that do anything and everything, until you progress. One day, you think up an awesome idea for a website, the only problem is that it's an original idea. Why is that a problem? Being an original idea, nobody's thought to make an extension for it! 

Then there's no choice but to learn php. However, because you've just learnt it, you're awesome idea is beyond you're coding skills. Everything gets so complicated so quickly, if you actually manage to implement it, it's full of SQL injection vulnerabilities, that you didn't even know were possible.

The other option is learning a real world language, something like ruby or Python or even D&#9837; (C#) or Java if you're crazy enough. Definitely not C, like Krupski suggested. Sorry, but just no, the one thing you don't want from you're web app is seg faults. Even if you're competent, your still going to make it seg fault. They'll be some edge case you hadn't thought about and when it goes, it won't give you a nice stack-trace in a 500 msg, it'll crash.

These languages don't have web-applications like php does, they have frameworks (Django, rails and the like), an entirely different beast. You have to program from the start. Sure, there's still loads of extensions, but it's up to you to make them work nicely with your code. As for themes, you're on your own.

Isn't this more difficult? Yes, to begin with, but when you think up your killer app, you'll know how to write it. You're not going to be limited to doing the same thing that everyone else is doing and learning to code from the start is going to make you a more competent developer. The other thing to note, is that actually, doing it this way isn't that complicated, there are lots of tutorials on the web that can teach you to make highly professional sites.

The choice then is between a learning curve, which starts very easy, but then rockets, or a curve with a more difficult start, but then a gradually incline.

(I'm sorry this post has turned out a little wordy)

---

### Post by Copernicus1234 on 2010-07-18
I would start with Django actually. Its NOT a editor, its a web framework for creating your own web applications.

Make a basic site by following the tutorial at [http://docs.djangoproject.com/en/dev/intro/tutorial01/](http://docs.djangoproject.com/en/dev/intro/tutorial01/).

If you like it, there are plenty of information on google for how to implement a shopping cart system with Django.

Of course, Django is about creating the code that runs the site, so your user interface will be very basic at first, but its not hard to learn some basic HTML to put links and images on the site.

---

### Post by nvteighen on 2010-07-18
I don't get what you want, dear OP... How much HTML (in any of its various incarnations... HTML4.1, XHTML 1.x, HTML5, whatever) and CSS do you know? I ask you this because I read your post as if you wanted not a PHP scripts library or such, but a web designing IDE... such as Mozilla Composer was (is?) or even OpenOffice.org Writer...

If you don't know how (X)HTML works, how CSS is used, you'll have a lot of troubles understanding the various scripting languages you'll need if you want to code (or use someone else's code for) a web store. Its impossible to learn web-targeted Javascript if you don't know the basic (X)HTML Document Object Model, for example. And I guess the same goes for PHP.

---

### Post by andrew.46 on 2010-08-03
Hi digital,

> **digitalcitizenx said:**
> bluefish

Mind you lucid missed out on the new version of Bluefish which is a worthy upgrade. I suspect it is perhaps not what the OP is after but others might be interested in a guide I wrote to fill the gap in Lucid:

Howto: Build the newest version of Bluefish under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1426958](http://ubuntuforums.org/showthread.php?t=1426958)

I would echo several of the other posters in this thread when I say that it is an excellent idea to starts with the basics of html and css before perhaps moving on to other things, and for this bluefish is a great tool.

Andrew

---

### Post by nebu on 2010-08-05
try learning java... it has very nice enterprise solutions!

---

