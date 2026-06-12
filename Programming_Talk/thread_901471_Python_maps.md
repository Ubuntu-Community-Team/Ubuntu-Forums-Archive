---
title: "Python maps?"
date: 2008-08-26
forum: Programming Talk
---

### Post by Tomosaur on 2008-08-26
Hi guys - I've taken a look on the web for this but I'm having no luck (getting a lot of 'results pollution' so to speak!), so I'm wondering whether you lot know of anything like this.

What I'm looking for is some kind of python module which would enable me to utilise street-names and whatnot, in a kind of 'fuzzy' geo-location style.

Basically what I want is to be able to register user street-addresses (and thereby the town / city, state / county, country etc) in a non-specific manner (ie: no house numbers or anything like that, just the street name).

I realise I could just ask users to simply type in their street-names or whatever, but the issue with this is that the whole point of the project I have in mind is to allow people to find people who are physically near to them, allow them to talk to each other or spark up a real-life friendship or whatever, and so I feel that the best way to go about this would be to allow users to 'register' themselves (although I generally want users to be allowed anonymity so registration is not strictly necessary) with a particular street and thereby be automatically registered with that street's local content (nothing too elaborate, just a way for people to communicate really).

Anyway, I realise what I'm asking is kind of 'Facebook-ish', but really what I'm trying to visualise is some kind of location-dependent IRC system - ie: you can talk to the people close to you (or, if you feel like, go 'up' a level to the town / city group, up further to the state / county group, and so on). So whereas Facebook is a way for friends to communicate, this would effectively be a way to make new friends who are physically near to you. I'm aware of the issues that arise when lots of people are allowed to talk all at once, but for the time being I've pretty much fallen at the first hurdle.

What I need then, is a way to access street-map data (ie: which town a street belongs to, which city, state / county, country etc). I don't need to generate an actual map (the Google Maps API, for example, doesn't seem to be able to cater for this, unfortunately), I just need to be able to recognise when more than one person lives in the same street, and I feel it would be much, much better for users to simply pick their street from a search rather than type in a street and thereby introduce human error etc.

Although I am intending to do this in Python (I would like to make this a Screenlet, and eventually make this available cross-platform), I am not necessarily set on Python 100%, so if you are aware of something using a different language, please let me know!

Alternatively, if I've completely missed something and you know that Google Maps API or Yahoo Maps API or whatever is capable of doing this (ideally I would like to keep away from having to make HTTP requests and all that palaver, if possible), feel free to smack me about the head :guitar:.

---

### Post by red_Marvin on 2008-08-26
I don't really get if your problem is locating people without asking them, or how to store it so it can be searched.
If it is the latter I see two ways:

1) Make a sort of linked list, or rather, something meshlike where each node contains the streetname, some representation of people who live there and a list of other nodes which represent other streets this node/street is connected to.
Then getting a list of people close to you, would consist of finding your street node, and based on how local/global you want your actions to be, select how "deep" you want to traverse nodes. Since some roads can be of varying length you'd need to implement som distance filter or something, which is why I think #2 is better.

2) Find a way to convert street/address data into geographical coordinates and then do a search for all other users within a determined radius, note that you might need to use spherical coordinates.

---

### Post by Tomosaur on 2008-08-26
> **red_Marvin said:**
> I don't really get if your problem is locating people without asking them, or how to store it so it can be searched.
If it is the latter I see two ways:

1) Make a sort of linked list, or rather, something meshlike where each node contains the streetname, some representation of people who live there and a list of other nodes which represent other streets this node/street is connected to.
Then getting a list of people close to you, would consist of finding your street node, and based on how local/global you want your actions to be, select how "deep" you want to traverse nodes. Since some roads can be of varying length you'd need to implement som distance filter or something, which is why I think #2 is better.

2) Find a way to convert street/address data into geographical coordinates and then do a search for all other users within a determined radius, note that you might need to use spherical coordinates.

Well what I was actually hoping for was some way of accessing map data which already exists - so that users may simply choose their street and thus be registered with that location. I don't think actually finding people near to each other will be a problem - what I am looking for initially though is some way of accessing map data programmatically. For example, if you type in a street address in any online map, it will find that street for you. It is this data which I am trying to find a way to access.

If this were, say, a web application, then I wouldn't really have a problem - but I am having difficulty finding a way to access the underlying map data through a desktop application which isn't technically an actual map.

So here's a simple use-case:

User A starts the program.
Program asks user to select country, city / town, then begin to type street name.
Program filters local street names for the city in question and user selects correct one.

User B does the same as user A.

Server notices a matching street address between users A and B and notifies both that they have a neighbour who is online.

From there both users have a variety of options to interact with each other.

So do you see what I mean? The issue is finding a way to access pre-existing street map data (for example, the data which allows Google Maps to find the correct street when you do a search with enough information).

Thanks for your help anyway - much appreciated!

---

### Post by Cheesehead on 2008-08-26
Option 2 is a lot easier, and is long solved - including an address-to-coordinates server. It has the added benefit of finding associations on nearby streets, not just same-name street.

[http://en.wikipedia.org/wiki/ICBM_address](http://en.wikipedia.org/wiki/ICBM_address)

---

### Post by pmasiar on 2008-08-26
> **Tomosaur said:**
> some way of accessing map data which already exists

I don't follow this area closely, but IIRC there is some public repository with all mapping info of all streets in USA (provided at taxpayer expense). This is what you want?

[http://en.wikipedia.org/wiki/Open_Geospatial_Consortium](http://en.wikipedia.org/wiki/Open_Geospatial_Consortium)

I found CRAN project: [http://cran.r-project.org/web/packages/GEOmap/index.html](http://cran.r-project.org/web/packages/GEOmap/index.html)

[http://cran.r-project.org/web/packages/geomapdata/index.html](http://cran.r-project.org/web/packages/geomapdata/index.html)

Try your google-fu on those :-) 

Good luck!

---

### Post by dekushrub on 2008-08-26
Another thing you may want to consider is possibly just using zip codes for people who live within the united states. That would make your life significantly easier and simpler.

---

### Post by Tomosaur on 2008-08-26
Thanks guys - I'll take a look at the links!

---

### Post by winch on 2008-08-26
The [Openstreetmap](http://openstreetmap.org) project provides a [name finder](http://wiki.openstreetmap.org/index.php/Name_finder) service. At the moment they will also let you use there map tiles in a desktop app.

I'm not sure how practical it is to use the other map apis in a desktop app. [Google won't let you](http://code.google.com/support/bin/answer.py?answer=55143&topic=10028). I'm not sure about others but I suspect at best they require you use their javascript apis so you would end up embedding a browser in your app.

---

### Post by Paul Miller on 2008-08-29
If your use case allows you to restrict the domain to US addresses, then there is code on [this page]("http://zips.sourceforge.net/") to do what you want, based on the ZIP code.

---

### Post by Endolith on 2008-12-31
[http://exogen.case.edu/projects/geopy/](http://exogen.case.edu/projects/geopy/)

---

