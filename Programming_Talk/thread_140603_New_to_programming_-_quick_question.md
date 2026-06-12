---
title: "New to programming - quick question"
date: 2006-03-06
forum: Programming Talk
---

### Post by robtotheb on 2006-03-06
I'm a simple web designer, know all the easy stuff like xHTML, CSS, Flash & bit of Java.  Recently I've been researching the best way to build a site that will need some heavy server side thinking.  
I can't give too many details on the site but Ill try and make what it needs to do clear:

A user can sign up for a fee (so will need a secure payment and login system)
Given access to their own page they can author (templates and up-datable content)

I know it just sounds like blogger.com with a fee but its not!

What would be best way for me to build this?  I'm learning PHP & MSQL but will I need something more powerful like python?

---

### Post by knalle on 2006-03-06
**pivotlog.net** is easy and simple, **joomla.org** is advanced and flexible.

---

### Post by robtotheb on 2006-03-06
Thanks knalle but I'm not building a personal blog.  Its basically going to be like [http://www.moonfruit.com/]("http://www.moonfruit.com/") but targeted at a specific group of people.

---

### Post by stoffe on 2006-03-06
If you are going to build an interactive website designer you will have to learn some programming, unless there is some kit like the above that already does what you want. :) PHP, Python, Perl, Ruby and so on doesn't really matter all that much unless it's in a framework - apart from personal preference in style of course.

I'd advice you to look at [prototype]("http://prototype.conio.net/") and [script.aculo.us]("http://script.aculo.us/") for the interactive building, and if you want something to go as backend, I personally recommend Ruby on Rails. It has everything you need, good up-front integration with the above libs, easier syntax than PHP (in my opinion) and good solid structure which helps you get on with building functionality. I'm sure there's plenty of alternatives too, but this is the one I can vouch for. Pick up the [RoR book]("http://www.pragmaticprogrammer.com/titles/rails/") and you'll be alright. One drawback: not as common to find hosting as PHP, but there is plenty. Textdrive is excellent.

For secure payments you will need to find one or several partners, companies that specialize in this. They usually have services that are dead easy to integrate, often you send the customer to their page which you have skinned to look like yours, and then they come back to you after they have paid. You don't really need to worry about that, though you of course need some login system on your side. This goes for any choice of platform.

---

### Post by knalle on 2006-03-06
[QUOTE=robtotheb]Thanks knalle but I'm not building a personal blog.  Its basically going to be like [http://www.moonfruit.com/]("http://www.moonfruit.com/") but targeted at a specific group of people.[/QUOTE]

joomla.org, its a complete cms, not a blog system

---

### Post by robtotheb on 2006-03-07
Stoffe thanks for your suggestions. Ruby on Rails looks great.  Shame that pdf book isn't "open source"

---

### Post by gord on 2006-03-07
don't forget [django](http://www.djangoproject.com/). its like ruby on rails but for python. has a book in projects too (open source :))

---

### Post by robtotheb on 2006-03-07
:confused: 
Which is faster & easier to learn, Ruby on Rails or Django?

---

### Post by NoWhereMan on 2006-03-07
[QUOTE=robtotheb]:confused: 
Which is faster & easier to learn, Ruby on Rails or Django?[/QUOTE]
I'm starting loving ruby, but it's probably a matter of taste :D

---

### Post by stoffe on 2006-03-07
[QUOTE=robtotheb]Stoffe thanks for your suggestions. Ruby on Rails looks great.  Shame that pdf book isn't "open source"[/QUOTE]
Yeah, but after buying it anyways I absolutely think it's worth it, and I'm happy to pay that low price for their excellent work in this particluar case. :)

There's plenty of resources on the ruby on rails site and many 3rd party ones too, and many do well without the book. Still recommend it if you have the cash.

[QUOTE=robtotheb]:confused: 
Which is faster & easier to learn, Ruby on Rails or Django?[/QUOTE]
I have no idea, I can only say that I think RoR was fast and easy to learn, and comes with tons of prebuilt functionality. It also supports, even enforces great programming practices so you have an easy time throughout the whole project. Django might be all of this too, but I haven't used it. In the end, pick the one you think looks best.

---

### Post by arachn1d on 2006-03-08
Sigh - screw django and ror. Go with php and cakephp - It's more reliable for the future and will benefit you, trust me. 

ROR is just a trend. Django might have potential, but it's python. Python doesn't have a huge community as PHP does.

---

### Post by NoWhereMan on 2006-03-09
[QUOTE=arachn1d]Sigh - screw django and ror. Go with php and cakephp - It's more reliable for the future and will benefit you, trust me.[/QUOTE]

I really hope you're wrong... I see a lot of potential in ruby, and a large community. Also it has a beautiful syntax and a lot of consistence

---

### Post by hagen00 on 2006-03-09
IMHO

For something that just requires some basic server side interpretation, why on earth not just go for php. It's easy to learn (great for a newbie as yourself), has a huge community with lots of support and is absolutely ideal for what you want to achieve. Really now, learning Ruby on Rails will take you so much longer to learn than php. And if you are a web developer, chances are php will stand you in much better stead than Ruby.

---

