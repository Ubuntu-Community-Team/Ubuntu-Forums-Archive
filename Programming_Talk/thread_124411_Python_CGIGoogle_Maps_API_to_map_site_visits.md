---
title: "Python CGI/Google Maps API to map site visits"
date: 2006-02-01
forum: Programming Talk
---

### Post by anthro398 on 2006-02-01
I was kind of sick last weekend and I wanted to build a web app for friends for school, but discovered that it had already been done.  Instead, I played around with the Google Maps API and thought it would be kind of neat to make a visual record of where hits on my site are coming from.  It isn't terribly complicated and isn't meant to replace a real user statistics application.  It's just meant to be neat and it gave me a chance to play around with the api.

You can see it at [dead link].  It's still pretty raw.  I didn't try to catch any exceptions and I have no idea if the geolocation database can handle international ip addresses.  Aside from handling exceptions, I'd also like to limit the number of logged visits to the last 20 or 50 or some number.  I don't get a lot of traffic, but I don't want the map to be too crowded to pick out inidividual hits.

The cgi works by capturing the ip address and checking if it's on the ignore list or if it's already been seen.  If neither of those things are true, it sens the ip address of the requestor to a free geolocation service, [http://www.hostip.info/]("http://www.hostip.info/"), to gather the city, country, latitude, and longitude.  Then if the ip address is new, the cgi writes the information to the xml file that the Google Maps API uses to draw icons to the map.  Finally, the cgi reads the map page and the xml data and draws the map.  It also substitutes a variable in map page with helpful messages about where it thinks you are.

Let me know how it works for you and what you think.  I'm open to sharing development if anyone is interested in working on this.

See it at [dead link].  Update:  That link is no longer live.  You can see the code, though, on my projects page.  [http://braggtown.com/projects.html]("http://braggtown.com/projects.html")

---

### Post by Van_Gogh on 2006-02-01
It's not terribly accurate, it seems. I'm logged in as being in Germany, which I'm not. Nice idea though and a fun thing to do.

P.S. a part of me is relieved that it is not all that accurate, as Big Brother is closing in on us everyday, it seems.

---

### Post by anthro398 on 2006-02-02
No, it isn't that accurate.  I'm using a free service for geolocation so I can't expect a great deal from it.  I think that it often locates proxy servers, too, so that will make it less accurate.  There are, however, pay services that are extremely accurate at geolocation.  

I can certainly understand concerns about "Big Brother".  The information I'm displaying here is no more, and generally much less, than any decent web statistics program or service like [Webalizer]("http://www.mrunix.net/webalizer/") or [AWStats]("http://awstats.sourceforge.net/") or [StatCounter.com]("http://www.statcounter.com/").  Notice also that I don't display your IP address to anyone but you and I don't display the host name portion of your domain name.  I could capture the user agent field and parse it for browser name, os name and version, etc.  I could also grab the pages visited, referring link, etc, but then I'd just be recreating the functionality of the excellent applications mentioned above.

---

### Post by hod139 on 2006-02-02
Located me accurately at my school.  I only wish there was decent satellite imagery of it.  Neat idea though, it's interesting to visually see where other people reading this thread are from.

---

### Post by anthro398 on 2006-02-02
I was thinking about the to-do list for this project and came up with some interesting questions (that I mostly don't have the time to answer).  For instance, how do you show the last 20 visitors?  I mean, you don't want to show the last 20 page-loads as 1 ip address could load the page 20 times.  Currently, I write a visitors ip address to a file and if that visitor visits again they get a message saying that a data point has already been created for them.  That means that each ip address can only be counted once, not once per visit as it should.

Also, I see that the Frankfurt point doesn't display a country and it should.  The Finland point displays odd characters.  The cgi should do a lot of checking on the data it receives back from the goelocation call.  And for ip addresses that don't have any information returned the cgi should fail gracefully and still display the map. Removing data points from the xml file is no trivial task, I suspect.  I've chosen not to treat the data as xml for the sake of speed and simplicity, but to really implement this it would have to understand the document model.  

Anyway, food for thought.

---

### Post by anthro398 on 2006-02-15
I rewrote this in PHP and MySQL.  It's now located at [http://braggtown.com/maps/index.php]("http://braggtown.com/maps/index.php").

---

### Post by anthro398 on 2006-11-10
The code for this project is available at [http://braggtown.com/projects.html]("http://braggtown.com/projects.html")  Please let me know if you find it useful.

---

