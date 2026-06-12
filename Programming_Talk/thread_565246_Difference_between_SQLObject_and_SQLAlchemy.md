---
title: "Difference between SQLObject and SQLAlchemy"
date: 2007-10-02
forum: Programming Talk
---

### Post by CostaRica on 2007-10-02
What is the difference between SQLObject and SQLAlchemy?  Thanks in advance!

---

### Post by pmasiar on 2007-10-02
in context of Turbogears?

SQLObject is simpler, but cannot make some tricky SQL statements. SQLAlchemy can do more. TG is moving from SO to SA in v2, but currently SO is the standard in docs. Most experienced TG gurus use SA anyway.

---

### Post by hibernaculus on 2007-10-02
I agree with pmasiar... :)
In my opinion SA is harder (in learn) than SO and less "pythonic"  programming paradigm (lots of ways, methods). If you want to use this library I recommend Elixir: [http://elixir.ematia.de/index.html](http://elixir.ematia.de/index.html) (wrapper with simple syntax like ActiveRecord from Rails) and Migrate: [http://erosson.com/migrate/trac/](http://erosson.com/migrate/trac/) ... 
BTW, my favorite is: Ruby on Rails :)

---

### Post by CostaRica on 2007-10-02
Puff... another decision to make.  From what you say SA is the way to go, but, Elixir or Migrate?

---

### Post by CostaRica on 2007-10-02
I have been reading and learning Python for a couple of weeks and I love it, but in the back of my head I wonder about RoR...

---

### Post by pmasiar on 2007-10-02
Elixir is what most people use with SA.

I understand why you think about the heresy of RoR: No choices, no problems, not afraid of making bad choice.

But multiple choices in Python is good: this is why free software wins! One size DOES NOT fit all!

What kind of app do you plan to create? If you are just a beginner, maybe Django is better fit for you: no choices, no confusion: just like RoR :-)

---

### Post by CptPicard on 2007-10-02
Don't. I've looked into RoR and it really holds that it makes 90% trivial and 10% impossible. What's the point in having fancy things auto-generated for you when you have to hack and hack to actually make it resemble anything you actually want to achieve? :)

Besides the rumour has it RoR has scalability issues.

I am in the middle of migrating from Java web app development to TurboGears...

---

### Post by CostaRica on 2007-10-02
First of all, I want to thank you, pmasiar, because you were the one who really convinced me of learning Python, I will always be thankful for that :).

I am writing a wxPython GUI app with a MySQL back-end to have an accounting-POS system for four eyewears-optometrist's stores that need to share data.  The MySQL database is going to be outsourced-hosted in a server with PHPMyAdmin to manage it (I tried hard to find a linux-friendly VPN Router but could not find it, in order to host the database server myself).

I do not want to make a web-app because I really like control over my app, and I do not want to use a generic app for accounting-POS.  Last night I was reading about SQLObject and loved the concepts, and if SA is better I should give it a try but...is it mature enough? Is Elixir mature enough, too?

Thanks in advance!

---

### Post by CostaRica on 2007-10-02
You are right.  I do not want auto-generated stuff.  I hate not having control over that and, as you said, having to hack and hack.  Let's concentrate on my beloved Python :)

---

### Post by CostaRica on 2007-10-02
So, is SA mature enough? Is Elixir mature enough, too?

---

### Post by pmasiar on 2007-10-02
You are welcome :-)

Yes, SA + Elixir is becoming new TG standard, when guys will get around and update the docs. Code is OK, docs are behind as always. IMHO you can safely go to next standard, SA.

---

### Post by CptPicard on 2007-10-02
> **CostaRica said:**
> 
I do not want to make a web-app because I really like control over my app, and I do not want to use a generic app for accounting-POS.


Why not a web app for your accounting-piece-of-^H^H *cough* :oops: point-of-sale app? IMO you would gain control, not lose it, and your users would be happier when you can roll out new features or bug fixes without making them install anything or you coming on site yourself to do it... I do pretty much the same thing as a web app for this very reason. :)

---

### Post by pmasiar on 2007-10-02
Yes, but maybe internet speed, price, and  reliability in Finland and Costa Rica are different? We were talking about this before.

But yes, I  agree with CtpPicard, web apps is way to go. I just re-read another excellent article by Paul Graham, about his startup, and starting a startup, and getting rich by programming web apps.

[http://www.paulgraham.com/road.html](http://www.paulgraham.com/road.html)

---

### Post by CptPicard on 2007-10-02
> **pmasiar said:**
> Yes, but maybe internet speed, price, and  reliability in Finland and Costa Rica are different? We were talking about this before.

Perhaps, but if I understood this correctly, the database is still going to be hosted somewhere else, so he's having a critical component somewhere on the Internet anyway. Plus, "having control over the application" was specifically mentioned as the reason of *not* doing a web app, and I strongly object to that :)

---

### Post by pmasiar on 2007-10-02
IIRC for Costa Rica best solution looked like offline local databases with occasional synchronization.

I still dont see why not run web server for each LAN, and be ready to tighter integration later (and learn web apps - be first cool kid in your block to have web apps) but all can I is suggest.

---

### Post by CostaRica on 2007-10-02
> **pmasiar said:**
> IIRC for Costa Rica best solution looked like offline local databases with occasional synchronization.

I still dont see why not run web server for each LAN, and be ready to tighter integration later (and learn web apps - be first cool kid in your block to have web apps) but all can I is suggest.

That is correct (occasional synchronization).

Please tell me:
1. What is the control that I loose in web apps?  
2. Are events possible?  
3. Isn't it slower even in local LAN?
4. Can I have grids with comboboxes, checks, etc?
5. Isn't it annoying to keep changing pages every update or change in the info you enter?
6. Can I have wizard-like screens?
7. What happens if the user backs-up?

---

### Post by pmasiar on 2007-10-03
> **CostaRica said:**
> That is correct (occasional synchronization).


If you aim for occasional synchronization, with apps running on LAN, and each LAN having own copy of central database, IMHO it is reasonable to write it as good old client/server app, and have decent desktop GUI program instead of web app/AJAX, unless you **want** to learn web apps/AJAX and be ready for time when they will be feasible - which might be in a year or two, about time when your app will be deployed :-)

> 1. What is the control that I loose in web apps?  

CtpPicard can explain his thoughts (I am not Ruby programmer so i cannot read his mind :-) ). IIUC in web app you do not lose any substantial control over app. Graham's article linked above explains it. With desktop you have little more power, but quite a lot more responsibility: maintaining correct versions and upgrading them in sync. Web app is deployed only on the server alone, so you have no synchronization dance when you want to deploy a bug fix which changes date format.

> 2. Are events possible?  

As much events as you can add to your javascript code. Yes, it is pain to have browser-side code, and in different language that the one used for server side. Major pain.

> 3. Isn't it slower even in local LAN?

IIUC comparing web app vs LAN-based app? With connection as fast as is common in developed countries (like USA and Finnland :-) ) time lag is almost negligent, and convenience for users is substantial (they can access your app from any PC with internet, which is any PC). It is your call to decide how it is relevant to your country - and how fast internet connection would be when you will deploy your app.

I would still advice to go web app way, and run them on LAN. You HAVE to learn web apps, no way around it (including sucky AJAX), and when fatter pipes will become available, your app will be ready to go online with minimal changes.

> 4. Can I have grids with comboboxes, checks, etc?

You can gave anything what HTML provides - and even grids, with some unsane AJAX libraries. Try Google calendar.

Of course web form layout is different, you will never know how big the user's window is, and if it is maximized. Yes it is pain.

TurboGears has sub-framework to develop custom wigets, you may want to look at them too. Yes, they are very different from desktop widgets.

> 5. Isn't it annoying to keep changing pages every update or change in the info you enter?

With [AJAX](http://en.wikipedia.org/wiki/Ajax_%28programming%29),  part of so called web2.0, you can update parts of page without reloading. Try Google Calendar or even Google documents or spreadsheet. Feels like magic.

> 6. Can I have wizard-like screens?

Whatever you want - anything what your browser can handle.

> 7. What happens if the user backs-up?

IIUC if user clicks on back button? Yes it is pain, you need to track status, and BACK button does not unroll last AJAX change but gets you to previous page.

Did I mention that web apps with AJAX is pain? :-)

So IMHO it is reasonable to do your app as classic GUI desktop client/server app running on LAN. Downside is, that when (not if: when) your internet will become fast enough to support web apps, you need to throw it all and learn web apps anyway. It will be easier later, more and better AJAX libraries, but the pain will be only a slightly less.

Or maybe even then you can run it as desktop GUI, communicating over internet.... maybe.

Decision depends also on what you want to learn, and how much learning you can handle.

---

