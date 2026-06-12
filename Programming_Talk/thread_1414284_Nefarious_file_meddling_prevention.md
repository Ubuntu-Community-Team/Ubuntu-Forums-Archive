---
title: "Nefarious file meddling prevention"
date: 2010-02-23
forum: Programming Talk
---

### Post by propagation_of_sound on 2010-02-23
Hiya, 

I'm making a site in PHP, and in part of the site, the user downloads a cache file of their data. The next time the user visits the site, they can upload their cache and their data will be restored. However, I can suddenly detect that various nefarious users would try to meddle with their data for whatever reason. This cannot happen. So, I've decided to include some measures to stop this. 
I cannot decide between 
[LIST]
[*]Creating a hash of the data that is permanently stored on the server for each cache
[*]Or encrypting each cache to stop users meddling with it at all
[/LIST]
What do you think is the best way? Should I do one, the other, both, something else?

Thanks :)

---

### Post by Simon17 on 2010-02-23
Is there some reason you can't just store the data on the server?

---

### Post by propagation_of_sound on 2010-02-23
I am not storing data on the server to keep the site's footprint down. I am expecting a lot of data, and after all, it's the user's data, why should I clog up MY server with it? :)

---

### Post by Simon17 on 2010-02-23
So if it's the user's data, then why isn't he allowed to screw with it?

Let's ignore that question for now.

Encrypting the data or storing it in some non human readable form will make it more difficult to screw with for sure, but by no means impossible.

Storing a hash on the server, (depending on the hash that you use) will make it for all practical purposes tamper evident.

In my opinion, going with the hash would be simpler and more robust.

---

### Post by propagation_of_sound on 2010-02-23
Thanks. I will use a hash. :)
Sorry, its not the user's data, but EVERYONE'S data, and if people start messing with it, then everyone's going to have a different version of the data, which is obviously not a good idea :o
Thanks again. :D

---

### Post by Simon17 on 2010-02-23
Okay then. Is this for a game or something?
Let us know how it turns out.

I think you should be fine, but the only way to be absolutely certain that your data is trustworthy is to store it yourself on the server.

---

### Post by wmcbrine on 2010-02-23
Yeah, client-side security is... not secure. Also, as for "footprint", it sounds like you're trading off reduced storage space for increased bandwidth use. Are you sure that's what you want?

---

