---
title: "How to deliver a static page to another website without iframes"
date: 2007-07-03
forum: Programming Talk
---

### Post by got_nix on 2007-07-03
I have a feature on my website where i wanna push content to other websites. a feed of some sort. Howver i dont want constnat hitting of my datbase accross variosu websites. So i resorted to doing a cron which produces a static page which gets updated every (x interval). What i need to know now is how to deliver a static page to another website without using an iframe ( i really dislike these thigns ). 

So far my brain has been trying to convince me that it is possible using javascripts dom innerhtml attribute. The problem is.. how do i get the content of my html page assigned to the innerthml attrib of the dom.. 

I"m sure i cannot pass it the url (it wont parse it)

I really dont wanna use any php btw. because i figure some sites that will utilize my little feature will be static.

---

### Post by LaRoza on 2007-07-03
> **got_nix said:**
> I have a feature on my website where i wanna push content to other websites. a feed of some sort. Howver i dont want constnat hitting of my datbase accross variosu websites. So i resorted to doing a cron which produces a static page which gets updated every (x interval). What i need to know now is how to deliver a static page to another website without using an iframe ( i really dislike these thigns ). 

So far my brain has been trying to convince me that it is possible using javascripts dom innerhtml attribute. The problem is.. how do i get the content of my html page assigned to the innerthml attrib of the dom.. 

I"m sure i cannot pass it the url (it wont parse it)

I really dont wanna use any php btw. because i figure some sites that will utilize my little feature will be static.

A static web page is just that, static. You won't be able to use any client-side scripting to do this. If all of these sites that will be using this are on the same server, you might try a server side include.

---

### Post by got_nix on 2007-07-03
Thanks for the reply.. Odly enough i think i might have found a solution. It will include some serverside (php) but it'll be on my server. .end result on the display on the other site would be done through clientside. Will test and post result

---

