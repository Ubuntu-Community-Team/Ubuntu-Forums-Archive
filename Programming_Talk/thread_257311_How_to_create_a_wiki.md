---
title: "How to create a wiki?"
date: 2006-09-14
forum: Programming Talk
---

### Post by Blacktalon on 2006-09-14
Anyone know any good sites for show me how to create a wiki, (especially one where the wiki updates instantly after it's been edited...... [http://sl33p3r.free.fr/tutorials/rails/wiki/wiki-en.html](http://sl33p3r.free.fr/tutorials/rails/wiki/wiki-en.html) this one doesn't do that! )

Any help would be appreciated!

Thanks
  ~BT

---

### Post by nereid on 2006-09-14
Do you want to write your own wiki engine or do you want to know whether any existing engine can do this?

The instant update is done via the Ajax technique (using JavaScript and a server backend).

---

### Post by Blacktalon on 2006-09-14
I am writing my own wiki engine.  Well I have writen most of it, but the only problem I am really having is trying to make a validator for it.

---

### Post by X.Cyclop on 2006-09-14
Look for MediaWiki. ;)

---

### Post by Blacktalon on 2006-09-14
Thanks but it's not quit what I am looking for, I am creating it in Ruby on Rails.  And I just need an example source code for a validator for a wiki.  And also if anyone knows how to do the backtrack...like with a history of previous versions of it incase someone makes a mistake in it they can click on a previous version button and bring back the previous version.


Thanks

---

### Post by Klaidas on 2006-09-14
Why create a thing that has already been created? :)

Unless your're creating on educational purposes, of course

---

### Post by Blacktalon on 2006-09-14
I am creating cause someoone has asked me to create it.  And this has been bugging me for a while now.:-\"

---

### Post by Magnes on 2006-09-14
Well, check MediaWiki for code samples (like validator) nevertheless.

---

### Post by Blacktalon on 2006-09-14
Thanks for the suggestion, but mediawiki as far as I can tell, has it in PHP, and im doing it in _**Ruby**on Rails_, maybe I just missed it from veiwing over that site but all i saw was PHP.

---

### Post by NoWhereMan on 2006-09-14
I don't understand what you mean with "validate" :)

---

### Post by Blacktalon on 2006-09-14
ok maybe I should re-explain the problem.  Now I have created a wiki, and for the past couple days I been trying to figure out why it wasn't updating the edit correct until today I realized that the front page of the wiki (where I was trying to update), I realized that for some reason it had assigned 2 ID's to the page, so it was cycling between the update for each ID.  Now I need to create a Validator method to Keep 1 ID to the page.  This is what I mean by vadilate.

I hope this helps you, help me.

Thanks
  ~BT

---

### Post by Klaidas on 2006-09-14
> **Blacktalon said:**
> I am creating cause someoone has asked me to create it.  And this has been bugging me for a while now.:-\"

Just tell him there is no need to re-invent a bike (as we say it:)). Why wouldn't that someone just use a wiki that's already made?

---

### Post by Blacktalon on 2006-09-14
I do appreciate everyones help and suggestions, but do I know the saying (why re-invent the wheel) and so does he, but this wiki need to go into a huge, and I mean huge web application, and we need it to do specific stuff. (and if you are wondering what huge is I am talking about over 1000 file web application, and nearly a 1 Gig of space it takes up)

---

### Post by Tomosaur on 2006-09-14
I too am creating a wiki 'style' thing, mostly to teach myself perl. If it works satisfactorily when I'm done, I'm gonna pass it on to my uni's English Dept. I'm sure they'd find a use for it. It's kind of a hybrid between a wiki and a forum, I'll show you guys when I'm done (shouldn't be too long now really) and you can be my bug testers :P

It's running on my home pc though so don't expect speed. At all :O

---

### Post by NoWhereMan on 2006-09-15
> **Blacktalon said:**
> ok maybe I should re-explain the problem.  [...]

I guess I can't help as I've really understood little of what you're saying :D

---

