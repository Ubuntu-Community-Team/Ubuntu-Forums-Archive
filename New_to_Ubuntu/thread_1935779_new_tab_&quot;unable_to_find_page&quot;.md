---
title: "new tab &quot;unable to find page&quot;"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by soryu on 2012-03-05
whenever i open a new tab and do a search with the url bar i get a unable to find page from my isp.
i tried the solutions that show up on the page"about this page" link but they don't work.
i think that i can change one of the settings if i type about:config  in the url in firefox but don't know which one it is.
anyone know?

---

### Post by An Sanct on 2012-03-05
its "keyword.URL" 

I assume, that you know what to put there :) still I will give you a clue. If you want it to act as google, go to google.com and type "keyword" into the search edit, do a search.
you will get the results for "keyword", you can notice, that there is a '&q=_keyword_' in the URL, copy the whole URL to a text editor and place the '&q=keyword' to the last part of the URL, then remove "keyword", leaving just "&q=" at the end. this string now can be placed into the keyword.URL sting and you made it.

To make sure, copy the previous setting somewhere, so that you can revert it if you are unhappy with the results.

---

### Post by soryu on 2012-03-05
i tried it same results "unable to find page " shows up
 i tried remove first "&q=keyword' add to end remove "keyword" and keep first "&q=keyword" copy to end remove"keyword"



[http://www.google.com/#hl=en&gs_nf=1&cp=4&gs_id=s&xhr=t&q=keyword+tool&pf=p&output=search&sclient=psy-ab&pbx=1&oq=keyw&aq=0&aqi=g4&aql=&gs_sm=&gs_upl=&gs_l=&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=bcb2ebca30037deb&biw=1150&bih=541&q=:confused:](http://www.google.com/#hl=en&gs_nf=1&cp=4&gs_id=s&xhr=t&q=keyword+tool&pf=p&output=search&sclient=psy-ab&pbx=1&oq=keyw&aq=0&aqi=g4&aql=&gs_sm=&gs_upl=&gs_l=&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=bcb2ebca30037deb&biw=1150&bih=541&q=:confused:)

---

### Post by soryu on 2012-03-05
i'm looking at my settings in windows now and the "keyword url" is blank and works fine:confused:
also firefox.

---

### Post by An Sanct on 2012-03-05
I tried the link and it seems, you have left the first "&q=keyword" inside, this should not be there, as the first valid &q property is parsed and the second is mostly ignored (still works for me, get google running)

well, try this shorter string for keyword.URL
```
www.google.com/#&q=
```

PS. does going to google work? and ... you are using FireFox ... right?

---

### Post by soryu on 2012-03-05
also tried but this is what i get.
when i search google same thing 
firefox.
[http://www.results-page.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=euekiz39ksg8nwp7iqj2fp5wzfwi5q76&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fgoogle&AddInType=2&Version=2.1.8-1.90base&Referer=&Implementation=0&PlatformInfo=pbrgen](http://www.results-page.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=euekiz39ksg8nwp7iqj2fp5wzfwi5q76&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fgoogle&AddInType=2&Version=2.1.8-1.90base&Referer=&Implementation=0&PlatformInfo=pbrgen)

---

### Post by soryu on 2012-03-05
i just noticed that if i search for a random phrase or subject i get results.
but if i search a specific site  i get .
 [http://www.results-page.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=euekiz39ksg8nwp7iqj2fp5wzfwi5q76&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fpaypal&AddInType=2&Version=2.1.8-1.90base&Referer=&Implementation=0&PlatformInfo=pbrgen](http://www.results-page.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=euekiz39ksg8nwp7iqj2fp5wzfwi5q76&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fpaypal&AddInType=2&Version=2.1.8-1.90base&Referer=&Implementation=0&PlatformInfo=pbrgen)


[http://www.results-page.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=euekiz39ksg8nwp7iqj2fp5wzfwi5q76&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fchase&AddInType=2&Version=2.1.8-1.90base&Referer=&Implementation=0&PlatformInfo=pbrgen](http://www.results-page.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=euekiz39ksg8nwp7iqj2fp5wzfwi5q76&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fchase&AddInType=2&Version=2.1.8-1.90base&Referer=&Implementation=0&PlatformInfo=pbrgen)

[http://www.results-page.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=euekiz39ksg8nwp7iqj2fp5wzfwi5q76&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fdropbox&AddInType=2&Version=2.1.8-1.90base&Referer=&Implementation=0&PlatformInfo=pbrgen](http://www.results-page.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=euekiz39ksg8nwp7iqj2fp5wzfwi5q76&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fdropbox&AddInType=2&Version=2.1.8-1.90base&Referer=&Implementation=0&PlatformInfo=pbrgen)

---

### Post by jailbait on 2012-03-05
> **soryu said:**
> i just noticed that if i search for a random phrase or subject i get results.
but if i search a specific site  i get .
 [http://www.results-page.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=euekiz39ksg8nwp7iqj2fp5wzfwi5q76&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fpaypal&AddInType=2&Version=2.1.8-1.90base&Referer=&Implementation=0&PlatformInfo=pbrgen]("http://www.results-page.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=euekiz39ksg8nwp7iqj2fp5wzfwi5q76&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fpaypal&AddInType=2&Version=2.1.8-1.90base&Referer=&Implementation=0&PlatformInfo=pbrgen")


[http://www.results-page.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=euekiz39ksg8nwp7iqj2fp5wzfwi5q76&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fchase&AddInType=2&Version=2.1.8-1.90base&Referer=&Implementation=0&PlatformInfo=pbrgen](http://www.results-page.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=euekiz39ksg8nwp7iqj2fp5wzfwi5q76&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fchase&AddInType=2&Version=2.1.8-1.90base&Referer=&Implementation=0&PlatformInfo=pbrgen)

[http://www.results-page.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=euekiz39ksg8nwp7iqj2fp5wzfwi5q76&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fdropbox&AddInType=2&Version=2.1.8-1.90base&Referer=&Implementation=0&PlatformInfo=pbrgen](http://www.results-page.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=euekiz39ksg8nwp7iqj2fp5wzfwi5q76&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fdropbox&AddInType=2&Version=2.1.8-1.90base&Referer=&Implementation=0&PlatformInfo=pbrgen)
Your using verizon's DNS servers. And their running search/domain hijacking.

Use Google, Internap, or Level(3). OpenDNS has the same problem.

OpenDNS
208.67.222.222
208.67.220.220

Level3 
4.2.2.2
4.2.2.3

Dyn DNS
resolver1.dyndnsinternetguide.com
resolver2.dyndnsinternetguide.com

Internap 
ns[1-12].lon.pnap.net

Comodo (Secure) 
156.154.70.22
156.154.71.22

Scrubit 

67.138.54.100 
207.225.209.66

Google 
8.8.8.8 
8.8.4.4

Cogent 
66.28.0.45
66.28.0.61

---

### Post by soryu on 2012-03-05
how come this only happens on ubuntu?
there are three other pc's on this network and they don't have this problem.
i've changed servers before and when  i changed them none of the pc's could go online neither this one.
if i use chrome or opera this doesn't happen.
prefer firefox.
i guess i'll just deal with it for now.
thanks for the info.

---

