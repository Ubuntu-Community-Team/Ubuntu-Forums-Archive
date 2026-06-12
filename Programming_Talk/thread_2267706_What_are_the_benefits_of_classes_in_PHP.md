---
title: "What are the benefits of classes in PHP?"
date: 2015-03-03
forum: Programming Talk
---

### Post by Dragonbite on 2015-03-03
I'm rewriting a PHP site for an auction bidder registration and checkout system.  It's a LAMP system I have used before but like rewriting it so I can take advantage of programming skills learned since last year (usually via work).

One of the pages is for adding and editing Customer information (customers.php) and from I can tell I can perform the actions easily enough in the PHP code before the HTML coding, or I could easily create a class to manage the fields and database activity (get, input, update).

I know PHP is not as OO as other languages (Java, C#, etc.).  I don't know if there is a performance benefit, security difference, code location or any other benefit to one way or the other.

So is there any benefit to using a class in PHP, or is it "6 to one, half-dozen to another"  (or that there is no difference either way)?

---

### Post by tgalati4 on 2015-03-03
There is no difference.

Unless there is a difference.

It's hard to say without any performance metrics.  Many PHP pages have a compute/render time printed at the bottom so you can see how long it takes to go through each web action.  So I would instrument your PHP and collect some metrics.  Since this is just bidder registration and not actual bidding performance, then it probably doesn't make any difference.  If you have 300 bidders lined up and you can save 0.1 seconds on each new registration you can save 30 seconds or the time it takes for a few more bidders to get in line.  

Let the performance data guide your programming.  Here's an example of a slow PHP service--SugarCRM:  [http://www.webperformance.com/library/reports/SugarAPC/](http://www.webperformance.com/library/reports/SugarAPC/)

Taking working, production code and changing it because you want to try a few new things is a useful exercise, but not if it takes time away from your operational responsibilities.  In other words, if you drop the ball in other critical, operational areas because you are rewriting working code is not a good trade-off, in my opinion.  Your boss will have a pretty clear idea of priorities.

---

### Post by Dragonbite on 2015-03-03
This whole project is volunteer and is used by my church at their annual flea market and auction. It isn't until May, so I have a little time to work on it and tweak it. First I'm going for the skeleton before adding nice touches (usually in javascript) and styling (css).

I decided on the PHP site because I could easily create a LAMP server on a variety of systems (dual-boot my laptop for instance) and get the cashier volunteers to access it without having to use or install any special software or care what OS they are running.  I don't think I've had more than 4 active users at one time.

When a customer comes in we search the database to see if they have been there before (I have about 3-4 years of customers in there).  If they are new, add them. If they are previous customers then all we need to do is associate them with a bidding number.  I am hoping this builds a customer list and saves time processing repeat customers.

All of the auction items are previously entered (gotta work on a CSV or Excel import routine though) and numbered.

As the auction is going on, somebody next to the auctioneer is data entering the winning bidder number and for how much.  At the same time somebody in the audience is writing down all of the winners, as a backup.

Meanwhile the cashiers can update the silent auction items, which has been completed, with who won it and for how much.

When the customer go to cash out we enter their bidder number, the system pulls up a list of all items they have won, totals it and we print the receipt (after verifying with the bidder).  They can use credit cards, but that process is self-contained so I cannot integrate it with this PHP app.

If somebody wins a bid he or she can get up immediately, walk out to the cashiers and the data is all set for cashing out.
If they have a conflict of some sort, we can refer to the paper version from the 2nd person.  Usually (99% of the time) the two match and the customer accepts it.

When things are working alright, I can actually walk away from the system once the cashiers are trained.  Usually something goes "pththt" and often it is the network. But that's another, separate issue.

---

### Post by tgalati4 on 2015-03-03
Well, that is a completely different Use Case that I had in mind when I responded to your initial question.  There might be an application that someone has already written to use as a guide.

I would look into some of the CRM solutions (including SugarCRM, but that may be too heavy for a Church).  Many have plug-in modules.  It might be easier to install a CRM framework and look for or write a bidder plug-in.  You could simply add a bidder field to the basic contact database and filter on that during the auction.  Include enough meta-data for the auction to be useful in the future.

[https://civicrm.org/](https://civicrm.org/)

[http://www.nten.org/blog/2008/05/21/open-source-crms-how-do-they-stack-up](http://www.nten.org/blog/2008/05/21/open-source-crms-how-do-they-stack-up)

---

### Post by terrypearson on 2015-03-03
I've worked on systems with large amounts of procedural code and classes mixed in. It is not the worst thing in the world. 

Performance-wise, it really depends on your use case. I like the clean, structured use of classes.

My approach has been to slowly migrate over to classes. Don't rework everything. Instead, for example, create a user class. Use it for new stuff and maybe convert a few pages. Maybe load your code in Eclipse and do a search for every time they query the database for user name and see if you can convert some or all of those. Now, every time there is a new feature, make sure you use an OOP approach. Then go back and see what can be changed in the old code to match it.

 We've converted a good deal of certain sites over time this way. If you convert everything in a massive, do it all project. You would probably be better just rewriting the code from scratch and interfacing with the existing database. 

In any case, my humble advice is to bite off little chunks and not do a full rewrite. At first, it does not seem like much, but over time, it gets better.

---

### Post by Dragonbite on 2015-03-03
I have this down to less than or about a dozen pages.

At work I recently went through a spat of PHP work, including a Drupal upgrade and re-vamping some custom sites and removing CakePHP framework.  So I am hoping to incorporate what I learned there to make the site more stable and maintainable.

---

