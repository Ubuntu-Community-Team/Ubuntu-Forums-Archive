---
title: "Handling large projects"
date: 2008-09-18
forum: Programming Talk
---

### Post by Stex on 2008-09-18
To all of you who work in development (whether alone or in a group):

I'm creating a large e-commerce site (PHP & mySQL) and it's my first big paid job. I'm doing this for a friend's company at discount rates to give me experience in the business but with all the things they're asking for it just feels way over my head. Their current small site has a £1m/year turnover already so I can't just bodge this up.

I'm not asking for help, I know I'm capable of doing this as I'm seasoned in PHP and pretty handy in SQL. I'm just not used to the sheer scale and pressure. I'm 20 hours in and after another meeting have been ladened with some more complex features for which I'm going to have to really juggle the database.

How do you guys keep stress levels down and productivity up? Because I'm finding myself shying away and just writing the easy admin panel bits.

---

### Post by xlinuks on 2008-09-18
The main rule (for me) is don't bite off more than you can chew. It is very important, because in the end you might not only abandon the job (project) but also leave the clients pissed off and wasted time. If you're gonna work more than 10 hours a day on the project you're likely to give up within a month or two, so I would only recommend like 6-8 hours a day, otherwise you will burn out.

---

### Post by cb951303 on 2008-09-18
I never start from scratch. I either use a framework or my old codes. this way I never feel that the project is over my head since most of the low-level stuff (and some high-level stuff like rss) is already implemented.

good luck on your project

---

### Post by jpeddicord on 2008-09-18
> **cb951303 said:**
> I never start from scratch. I either use a framework or my old codes. this way I never feel that the project is over my head since most of the low-level stuff (and some high-level stuff like rss) is already implemented.

good luck on your project

I used to start from scratch, but then I found out about frameworks that were out there. I'm a Django nut, but I know there are some really nice PHP frameworks out there. Spend a day evaluating some of them, it will save you a lot of time in the end with a much faster development speed.

---

### Post by xlinuks on 2008-09-18
For that matter I heard lots of people saying NetBeans 6.5 has very good support for PHP, might help you do things faster.

---

### Post by cb951303 on 2008-09-18
> **xlinuks said:**
> For that matter I heard lots of people saying NetBeans 6.5 has very good support for PHP, might help you do things faster.

once it comes out of beta it will be really nice. better than eclipse + pdt in my opinion. it's just not stable enough right now. error dialogs are popping up every 2 minutes.

---

### Post by LaRoza on 2008-09-18
> **Stex said:**
> 
I'm creating a large e-commerce site (PHP & mySQL) and it's my first big paid job. I'm doing this for a friend's company at discount rates to give me experience in the business but with all the things they're asking for it just feels way over my head. Their current small site has a £1m/year turnover already so I can't just bodge this up.

First, a few things:

[list]
[*] I don't know what you mean by "large", but e-commerce is very important to do right. If you can't do it, and don't have experience in e-commerce development, you shouldn't be the head of the project.
[*] Your friend's company. Discount rates. Sounds like management is using you. Don't give discounts except to friends and small tasks. Remember, to your friend, not a company!
[*] Over your head? Then tell them. Either you need more people, or it can't be done. Don't be silent. Letting the contract go is better than failing because you thought you could. Only in kids stories does "I think I can..." work.
[*] Lots of pressure there for a complex task at a discount... 
[/list]


> 
I'm just not used to the sheer scale and pressure. I'm 20 hours in and after another meeting have been ladened with some more complex features for which I'm going to have to really juggle the database.

Use a version control system. I recommend bazaar or git (bazaar might be easier to use). You can use them locally for version control and they will help you track and maintain the code.

> 
How do you guys keep stress levels down and productivity up?
Chosing a task you know you can complete and by being honest with the client. If they have unrealistic expectations, or expectations beyond your known ability (not what you "think" you can do), tell them.

> 
 Because I'm finding myself shying away and just writing the easy admin panel bits.

That is probably a sign ;)

---

### Post by Tomosaur on 2008-09-18
Might be worth investigating a few CMSs. Many have plugins and modules available to provide the basic functionality you need, and if they're open source (many Joomla modules / extensions are for example), then you can tweak them to get it integrated into your site properly. You can also create your own template or just modify an existing one. There really isn't much point starting from scratch, big projects are complex and for a single developer, the sheer amount of stuff to get done can lead to mistakes, poor security, and bad design. Break everything into manageable chunks.

---

### Post by henchman on 2008-09-19
You may also have a look at osCommerce.... wp is describing it well: [http://en.wikipedia.org/wiki/Oscommerce](http://en.wikipedia.org/wiki/Oscommerce)

---

### Post by escapee on 2008-09-19
Since it sounds like you're looking into freelance work, you may want to check out [http://freelanceswitch.com/]("http://freelanceswitch.com/").  It has helpful information from motivation, to humor, to legal and financial advice.

Other than that, I have to repeat what LaRoza and a few others have said and recommend you use a version control system.  SVN, git, bzr, CVS, all fine choices, choose what works for you.

---

### Post by cb951303 on 2008-09-19
I also found this in my favorite web design page: [http://www.sitepoint.com/subcat/site-planning](http://www.sitepoint.com/subcat/site-planning) it might ease your job a little bit

---

### Post by pmasiar on 2008-09-19
> **Stex said:**
> I'm creating a large e-commerce site (PHP & mySQL) and it's my first big paid job. I'm doing this for a friend's company at discount rates to give me experience in the business

You are setting yourself, **and** your friend, for a spectacular failure. There is a reason why first jobs for junior programmer is doing maintenance and bug fixing for big projects: because as you found, you don't have skills to design and manage big project by yourself. It's not your fault, but you do not have clue how to protect your code from SQL injection (and likely have no clue what it is), and many other 'tricks of trade' which you can learn by participating (as junior programmer) on big projects.

I advice you to confess up and ask for expert guidance, you do not want to learn programming by making mistakes which may cost your friend bug money.

Edit: BIG money of course :-)

---

### Post by Tomosaur on 2008-09-19
> **pmasiar said:**
> 
I advice you to confess up and ask for expert guidance, you do not want to learn programming by making mistakes which may cost your friend bug money.

Bug money eh? Is that money which shouldn't be there? Because if it is, I've got a few thousand pounds worth of debt it could be useful solving :P

---

### Post by Stex on 2008-09-19
I think I came off somewhat like a 14 year old kid who's found some PHP tutorials there but I've been developing in PHP for 5 years. I've done all the maintenance in (and writing my own) big projects, which is why he came to me. It's the business side of things that I'm a rookie at, not the coding.

Rest assured I've already created classes for the database interaction to avoid sql injection, a safe emailing class and I've built cart & checkout classes with security in mind. I know what I'm doing but, coming from open source projects, I'm not so used to rigid specifications and time limits.

I think I did sell myself too short, even for my inexperience in business, but I'm using this opportunity too. I'm creating classes that I'm sure I'll keep in my toolkit for later work, anything that isn't directly linked to the security of the site I'm at liberty to keep.

It's a bit late to use a CMS now but thanks for the tips. I think I'll force myself to work on each module until it's completed to split the workload and not worry about the bigger picture too much. It's a lot of work for 1 developer but I've got plenty of time and a steady income like that isn't anything bad for a freelancer.

---

### Post by DrMega on 2008-09-19
> **Stex said:**
> To all of you who work in development (whether alone or in a group):

I'm creating a large e-commerce site (PHP & mySQL) and it's my first big paid job. I'm doing this for a friend's company at discount rates to give me experience in the business but with all the things they're asking for it just feels way over my head. Their current small site has a £1m/year turnover already so I can't just bodge this up.

I'm not asking for help, I know I'm capable of doing this as I'm seasoned in PHP and pretty handy in SQL. I'm just not used to the sheer scale and pressure. I'm 20 hours in and after another meeting have been ladened with some more complex features for which I'm going to have to really juggle the database.

How do you guys keep stress levels down and productivity up? Because I'm finding myself shying away and just writing the easy admin panel bits.

I agree with what some have said, that you should never start from scratch, but on the other hand, don't spend ages trying and discarding loads of different frameworks and stuff. Take what works for you.

The trick is to make sure you have everything broken into chunks. If one bit gives you bother, the last thing you want is to have to work out which bit it is that's playing up, and try to isolate everything a bit at a time.

For a data driven website, you should have at least three tiers. The client side stuff (all the HTML, which of course will be styled with one or more common CCS files so you can make sweeping changes throughout the site without loads of seperate cutting and pasting). The database side (build and test all your SQL bits completely independently of the website and PHP. Make sure they work so that any problems later can be put down to the PHP side). And then your PHP to hold it all together.

If it is a business app, you should have a library (at least one PHP file with all your functions in it) which you include from each page. That way if there are bugs you only fix them in one place, and again you can test the library independently of the site by having a test page which effectively unit tests your library functions).

Use some sort of version control. It is almost essential on big projects, especially if you value your sanity. If anyone else might work on the project with you, then version control is essential for your freindship. Trust me, when your freind overwrites a couple of days worth of your work when you're already snowed under, it can be a real test of your patience.

---

