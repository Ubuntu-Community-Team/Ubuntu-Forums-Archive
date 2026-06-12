---
title: "PHP framework: PRADO"
date: 2005-05-20
forum: Programming Talk
---

### Post by klaas on 2005-05-20
Hi all,

I'm starting up a PHP/MySQL web project and I'm looking for a good framework to speed up development. I stumbled upon PRADO ([http://www.xisc.com/](http://www.xisc.com/)) and it looks verry interesting. Has anyone used it and if so, is it any good or would you advise on another framework?

Thanx,
Klaas

---

### Post by Rodrigo on 2005-05-21
Why dont use MAMBO?

---

### Post by deuce868 on 2005-05-21
[QUOTE=Rodrigo]Why dont use MAMBO?[/QUOTE]

I think they're just a bit different. Mambo is a complete CMS while prado is more a system of parts you use to build your own project be it a CMS project or otherwise.

---

### Post by klaas on 2005-05-23
Indeed PRADO is a component-based and event-driven PHP development framework, more something like ASP.NET. I know mambo (very good, did some websites with it) but this is a real CMS and I do not require a CMS for my current project, just building blocks to speed up and streamline development. 

For the moment I'm evaluating PRADO and Ruby on Rails so comments of people who have used one of them, are more than welcome!

---

### Post by deuce868 on 2005-05-23
Well I've not use either. Actually I've just started getting into this type of component development in php. Prado looks interesting, but I think I want to learn what it's doing so I could adjust to it before I started using it. 

As for Ruby on Rails, I checked it out briefly and talked with some people. The comments I heard were, while it makes it easy to get things started, once it's going it's then a pain to adjust to your specific project. Kind of like working with Dreamweaver for php or asp design. It's got all these great tools for creating edit/update/delete pages and will write the database code and such for you, but the first time you go to make a combined insert/update form you realize you're better off coding your own setup. 

I just left ROR alone after that. Make sure you drop back to let us know what you think in the end.

---

### Post by jdonnell on 2005-05-24
[QUOTE=deuce868]
As for Ruby on Rails, I checked it out briefly and talked with some people. The comments I heard were, while it makes it easy to get things started, once it's going it's then a pain to adjust to your specific project. Kind of like working with Dreamweaver for php or asp design. It's got all these great tools for creating edit/update/delete pages and will write the database code and such for you, but the first time you go to make a combined insert/update form you realize you're better off coding your own setup. 
[/QUOTE]

I recently started using ruby on rails for two projects, and I think your assesment is simply wrong. Combining inserts and updates is as easy as it is in php. You use an if statement :)

Second, why would you want to combine them when it's much easier and cleaner in rails to use two seperate methods for inserting and updating.

---

### Post by deuce868 on 2005-05-24
[QUOTE=jdonnell]I recently started using ruby on rails for two projects, and I think your assesment is simply wrong. Combining inserts and updates is as easy as it is in php. You use an if statement :)

Second, why would you want to combine them when it's much easier and cleaner in rails to use two seperate methods for inserting and updating.[/QUOTE]

I meant this more as an example of where a program begins to get inflexible. I have not used Rails so I don't know where things broke down for the people I was talking with. 

As for why combine an insert and an update?

My code using a single function call updateWhatever(); In that script I see if one of the parameters is a valid ID if it is then I run an update query, if not I do the insert query. This consolidates all of the validatation and such into a single place so if I add a new field or something I have one function to modify.

Not only that, but the form and everything else will be the same from an insert to an update so why create two separate files for them. They are too similiar so I run a single page to handle it all.

---

### Post by jdonnell on 2005-05-25
[QUOTE=deuce868]
As for why combine an insert and an update?

My code using a single function call updateWhatever(); In that script I see if one of the parameters is a valid ID if it is then I run an update query, if not I do the insert query. This consolidates all of the validatation and such into a single place so if I add a new field or something I have one function to modify.

Not only that, but the form and everything else will be the same from an insert to an update so why create two separate files for them. They are too similiar so I run a single page to handle it all.[/QUOTE]

This can be done just as easily in two seperate files, you just have to have one template for the display and one verification function. I prefer to have two seperate files than to have if else statements in this regard. This is just a personal preference though, and you can still do it your way in rails. I'll see how my rails app goes. Maybe I'll run into those same limitations your talking about, but so far I haven't seen it. Typically frameworks that make things easy also make them inflexible. I get the feeling that a lot of the people that say rails is inflexible are saying it based on this assumption eventhough they've never actually made anything complex with rails. I see no reason why a framework can't be flexible and easy and rails seems this way so far, but I'm just getting started with it so take that with a grain of salt :)

---

