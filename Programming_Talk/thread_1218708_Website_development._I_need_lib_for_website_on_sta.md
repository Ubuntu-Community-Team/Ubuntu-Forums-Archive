---
title: "Website development. I need lib for website on state,county,city data."
date: 2009-07-20
forum: Programming Talk
---

### Post by hockey97 on 2009-07-20
Hi, I am making a market system for my website. I need to have the country,state,county,city names for the U.S and canada province.  

I am making a market system where users can make postings to sell items for free. 

I want to make the postings to either local areas or national. This depends on what the user wants to sell and have far of a range around where they live will they offer to sell this stuff. 

So I want to organize the postings by country,state,county,city. That's for U.S for Canada it would be provance and then in other countries it would just be by cities and villages. 

I currently have a market system developed but I used a US html map. that you can click the states. 

The problem is that I found out right now that it's too complicated to use. 

I also allow the user to create the item. So when you search you can see an item or a city name in the drop down menu. The users will be able to type in the city name and country. I was told on another form that this is a bad method. 

They said that hackers could have fun. I did filter the input and made sure no code gets injected. 

the problem I still face is that people can keep creating random city names that don't exist and could flood my server.

So I was told I had to provide the city names and stuff. So I am decidinging to create classes. I then decided that I should ask on here if their any library or class that I can use.

So I would like  to know if their is any class or libary that already can do such a thing. They it will provide all the US,state names and county and city names in the U.S and provances in canada. Then cities in other countries.

---

### Post by ebharv on 2009-07-21
Try [Google Maps]("http://code.google.com/apis/maps/") (web) API. You could send what the user types to the API to see if the location is real. I don't know how complicated this would be but or if it would work at all but it's a shot.

Another thing you could do is ask for the user postal code and mile radius and let them choose from a loaded list of cities. Once again, I don't know how complicated this would be but or if it would work at all but it's a shot.

One more thing [Google Maps]("http://code.google.com/apis/maps/") uses AJAX.

Take a look and see if it'll help you.

---

### Post by hockey97 on 2009-07-22
ok, thanks for the reply. I was told that I would need to manually add the state counties and cities myself.

I want the user to be able to post a image and information about what they are selling. 

They then will have a choice on to where they want buyers to be from. 

Basically when someone searches for a city or location for local items. I want them to be able to look at all the items being sold or on sale in that area.

I have to create some interface like a map or something of my own or could use google maps. 

The only thing that would make me be afraid to use google maps is the legality. I am not sure if I can use google maps for a commercial site.

I am trying to provide a service where users can sell items on my site.

I would love to use google maps in some way.

I just wondered that somewhere should have a map already made or something that will show the state and counties in the state and cities in the state.

I will look into google maps thanks.

---

