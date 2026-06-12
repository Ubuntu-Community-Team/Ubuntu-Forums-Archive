---
title: "Creating a Fantasy Football website"
date: 2008-11-05
forum: Programming Talk
---

### Post by MGVP on 2008-11-05
Hey everyone,

Im considering creating my own fatasy football website as part of a project lasting several months. The main stumbling block I have is getting the real live data from the weekly football results..eg who scored/assists/yellow card..and so forth.
I know the major fantasy football sites use data feeds from agencies (mostl XML format), and they just use that data to update the scores. However that is very costly, so isnt an option for me.

The only other way I can think of (that is automatic),is where I can go to a website, highlight the results/scorers etc , and then use some sort of tool to sort the data out, or even export it to an XML format, and use that as my data feed. 

Does anyone have any idea on the best way (and cheapest) to go about doing this?

Would really appreciate it if you could help me out here..I know Im new an all but I would be very greatful!

Thanks

---

### Post by y@w on 2008-11-05
[http://www.gamblerspalace.com/xml_sports_betting_feeds.htm](http://www.gamblerspalace.com/xml_sports_betting_feeds.htm)

Does this help?

---

### Post by ankursethi on 2008-11-05
Why not use the feeds from the *other* fantasy football sites? It never hurts to cheat a little ...

Another option is screen scraping. Just download the HTML page containing the data using urllib2 and then use an HTML parser (BeautifulSoup) to single out the data you want. As usual, Google is your friend. I've done this before with an exam results website, and it works like a charm *if* the page you're downloading contains well formed HTML (okay, *relativey* well formed HTML).

---

### Post by era86 on 2008-11-05
I would parse NFL.com scores pages on Sun/Mon.  It would be a workload, but this is definately doable.  What are you using to develop your page?

---

### Post by MGVP on 2008-11-05
y@w - Thanks, I should have been clearer when I said football, - im referring to English Premiership Football. Your site has some useful information on XML feeds, but what would be of real interest would be a site offering free XML feeds of football results (I googled around but coudnt find any :I )

ankursethi - How would I go about using feeds from other fantasy football sites? I can only see the way in which they present the data feeds...which leads me to your next point on screen capturing.
I need to google that a bit more, but from what your saying.. for example:

[http://news.bbc.co.uk/sport1/hi/football/eng_prem/results/default.stm](http://news.bbc.co.uk/sport1/hi/football/eng_prem/results/default.stm)

I would be able to use the resources you mentioned, import the above into a DB for example and use that?

era86 - I will be using ASP.NET and VB for coding (know someoen who made a similar website using the same method, except his wasnt automated results..whcih kinda sucked :P ) I think parsing is definetly the best option I have seen so far, and I think this point is similar to ankursethi's of screen scraping unless Im mistaken. I'l google up the tools he mentioned soon and learn a bit more on that technique

Thanks for the prompt replies

---

### Post by MGVP on 2008-11-06
So I did some reading up on the tools mentioned, and they all seem related to Python. Unfortunately I have no clue on that language, and think it will be a bit too much for me to take on (as well as getting to grips with VB and ASP). Are you aware of any other methods that can be used to screen scrape? 
Thanks!

---

### Post by looking on 2009-05-29
mg
 
if u are still intresting in this please mail me thanks

---

