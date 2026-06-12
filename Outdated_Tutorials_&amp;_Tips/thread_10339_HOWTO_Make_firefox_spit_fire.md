---
title: "HOWTO: Make firefox spit fire"
date: 2005-01-06
forum: Outdated Tutorials &amp; Tips
---

### Post by kamstrup on 2005-01-06
Here's how to give the firedox browser a significant speed boost in loading pages: 

Enter "about:config" in the adress bar and hit enter. Find the following fields and modify them to the following values (format: "field_name: value"):

**This entry has been updated to reflect the comments below:** 
network.dns.disableIPv6: true
network.http.pipelining: true
network.http.proxy.pipelining: true
network.http.pipelining.maxrequests: 8
browser.turbo.enabled: true

I don't know if you have to restart firefox, but it won't hurt :)

Happy browsing!

HINT: Clicking the left most columns title bar (in english: "Preference Name") will sort the options alphabetically. Clicking again reverses orientation.

NOTE: If you are on a slow connection (dial-up and alike) don't bother doing this!

---

### Post by jdong on 2005-01-06
NOTE: Changing pipeline requests to 30 violates web standards and places unnecessary overhead+load on YOUR system, and more importantly on the remote server. Don't raise this number past 8.

Also, pipelining may cause some pages to render wrongly. Usually, the result is a disastrously misshapen page. But I've yet to experience this with the sites I've visited. But there are a few "exhibit" sites that are used to demo this problem... too lazy to google for one.

---

### Post by nocturn on 2005-01-07
[QUOTE=jdong]NOTE: Changing pipeline requests to 30 violates web standards and places unnecessary overhead+load on YOUR system, and more importantly on the remote server. Don't raise this number past 8.

Also, pipelining may cause some pages to render wrongly. Usually, the result is a disastrously misshapen page. But I've yet to experience this with the sites I've visited. But there are a few "exhibit" sites that are used to demo this problem... too lazy to google for one.[/QUOTE]

I didn't know that...  I already applied this a couple of days ago following an article on The Inq:
[http://www.theinquirer.net/?article=20453](http://www.theinquirer.net/?article=20453)

Possibly, a lot of people are going to be doing this after the article...

---

### Post by jdong on 2005-01-07
Pipelining is nice to do, **especially** when you have a flaky or lossy connection. It prevents one slow connection from delaying the entire page.

However, if you open 30 pipes to a webpage, it multiplies your load on the server by **30**. Imagine if all the viewers did this. The server sees 30 times the usual load, and probably will struggle to sustain the load. This is not to mention that it'd probably take your computer longer to initiate 30 pipelines than to load the page.

---

### Post by nocturn on 2005-01-07
[QUOTE=jdong]Pipelining is nice to do, **especially** when you have a flaky or lossy connection. It prevents one slow connection from delaying the entire page.

However, if you open 30 pipes to a webpage, it multiplies your load on the server by **30**. Imagine if all the viewers did this. The server sees 30 times the usual load, and probably will struggle to sustain the load. This is not to mention that it'd probably take your computer longer to initiate 30 pipelines than to load the page.[/QUOTE]

Thanks for the explanation jdong.  I'm decreasing the number of pipes to 8 on my systems.

---

### Post by kamstrup on 2005-01-12
Point taken. I will lower mine to 8 as well.

---

### Post by eljefe6 on 2005-01-12
Another one that makes pages render faster.

"Right-click anywhere and select New-> Integer. Name it "nglayout.initialpaint.delay" and set its value to "0". This value is the amount of time the browser waits before it acts on information it receives."

Source ([http://forevergeek.com/open_source/make_firefox_faster.php](http://forevergeek.com/open_source/make_firefox_faster.php)).

---

### Post by jdodson on 2005-01-12
[QUOTE=kamstrup]Here's how to give the firedox browser a significant speed boost in loading pages: 

Enter "about:config" in the adress bar and hit enter. Find the following fields and modify them to the following values (format: "field_name: value"):

network.dns.disableIPv6: true
network.http.pipelining: true
network.http.proxy.pipelining: true
network.http.pipelining.maxrequests: 30

I don't know if you have to restart firefox, but it won't hurt :)

Happy browsing!

HINT: Clicking the left most columns title bar (in english: "Preference Name") will sort the options alphabetically. Clicking again reverses orientation.

NOTE: If you are on a slow connection (dial-up and alike) don't bother doing this![/QUOTE]

seriously i thought this was a howto to make the browser show some cool fire effects....  doh!

---

### Post by eljefe6 on 2005-01-12
I forgot to add that when I made these changes to 0.9.3 (The one that ships with Ubuntu) it started acting funny.  You may want to update your Firefox before trying these enhancements.

---

### Post by wallijonn on 2005-01-12
If you have DSL / Cable you may want to set to "true" browser-turbo. 

btw, I had 1.0 and reverted back to 0.93 because I love the "undoclosetab" extension.

---

### Post by kamstrup on 2005-01-13
It feels faster with turbo enabled, but I don't know if it is just placebo...

---

### Post by digitalpure on 2005-01-21
thank you to everyone that made this possible... I know that I was going nuts from waiting.  I am on a fiber connection with a 7mb downstream, and it was pain stakingly slow.

Again, thanks firefox is SCREAMING now.....

---

### Post by Quest-Master on 2005-01-21
Yeah. This thing really helps. :D

---

### Post by Gezzer on 2005-01-22
In the address bar place
about:config
press GO

copy/paste the following (if its not already listed)
if listed r/click and pick modify
boolean value use "add" then pick the boolean entry
integer value use "add" then pick the integer entry

also if useing BB try these settings
with the cache set to 0 (zero)


>setting the page rendering & display time<

nglayout.initialpaint.delay
integer value 750
(default is 250)

content.notify.ontimer
boolean value true


>setting the number of reflows to do before waiting for the rest of the page to arrive<

content.notify.backoffcount
integer value 5

content.interrupt.parsing
boolean value true

content.maxtextrun
integer value 8191


>sets the allowed time between reflows in microseconds<

content.notify.interval
integer value 750000

content.switch.threshold
integer value 750000

content.max.tokenizing.time
integer value 2250000


>Change maximum connection count<

network.http.max-connections
integer value 32
(default 24)

network.http.max-connections-per-server
integer value 8
(default 8)

network.http.max-persistent-connections-per-proxy
integer value 8
(default 4)

network.http.max-persistent-connections-per-server
integer value 4
(default 2)


>Network+DNS settings<

network.dnsCacheExpiration
integer value 360 (6 minutes)

network.dnsCacheEntries
integer value 100

network.ftp.idleConnectionTimeout
integer value 60 (1 minute)

network.http.keep-alive.timeout
integer value 30

network.http.connect.timeout
integer value 30


>enable pipelining via the preferences menu<

network.http.pipelining
boolean value true

network.http.proxy.pipelining
boolean value true

network.http.pipelining.maxrequests
integer value 8
(default value 4)


>Caching settings<

browser.cache.memory.enable
boolean value true

browser.cache.disk.enable
boolean value true

browser.cache.disk_cache_ssl
boolean value false
(default true)


>This for dailup connections<
If you go to:

Edit> Preferences> Advanced> Proxies
and then enable Automatic proxy configuration URL:

inside this type or copy/paste below

[HTTP://cache:8080](HTTP://cache:8080)

close the Preferences window
restart mozilla

U will notice a big speed difference in page rendering while browseing...
(only use this if your cache for mozilla is enabled)

these work on a windows or linux box...


i CANNOT take the credit for the above, all i have done is gleen them from different forums
and place them together in such a way in the hope that they are easier to apply

please enjoy your tweaking...

---

### Post by Ozitraveller on 2005-02-24
Firefox Tweak Guide
[http://www.tweakfactor.com/articles/tweaks/firefoxtweak/2.html](http://www.tweakfactor.com/articles/tweaks/firefoxtweak/2.html)

Sections:

Firefox Keyboard Shortcuts

Advanced Configuration Options
[INDENT]Disabling New Windows
Show Pictures As They are Loading (IE Style)[/INDENT]

Performance Settings
[INDENT]Quick and Dirty Settings
Common to all configurations
Fast Computer Fast Connection
Fast Computer, Slower Connection
Fast Computer, Slow Connection
Slow Computer, Fast Connection
Slow Computer, Slow Connection[/INDENT]

Extensions

Themes

Conclusions


Enjoy!

---

### Post by froggy on 2005-03-09
[http://911networks.com/node/300](http://911networks.com/node/300)

Then select Firefox, it has how to speed up firefox for various configuations.

---

