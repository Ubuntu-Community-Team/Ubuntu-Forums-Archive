---
title: "selling video watching permission"
date: 2012-05-25
forum: Programming Talk
---

### Post by rotem30010 on 2012-05-25
hello people,

programming question: how do i sell  a  24 hours video watching permission on a shop (kinda) site? i can't find a tutorial on this subject.



thanks in advance.

---

### Post by Tony Flury on 2012-05-25
Also sorts of questions spring to mind here, but I doubt you will find a specific tutorial on that arrow subject. I would break the problem down in to smaller chunks :

1. How do i take payment from someone
2. How do i give them the content but make sure no-one else has it
3. How do i make sure that their content only works for 24 hours.

No 1 is easy ish - lots of e-commerce sites do this - it might cost you though to take credit cards - but you can integrate with things like Paypal for free.

No 2 requires you to know your customer and give them a "key", once they have purchased the content - I would do this by giving them a unique URL which only works when they are logged in - so there is another question - how do they log in, and keep their details secure.

No 3 could be easy - your make sure that their unique URL with a key does not work after 24 hours - i.e. you hold the key in a database and when someone tries to use the key you check how old it is - and if it is over 24 hours - you throw up a simple page telling them it has expired. Or another approach is that your URL encodes the date/time that the "key" is issued - so you don't even need to check a database, your s/w simply decodes the key and works out the issue time/date.

The tricky bit comes I think with the actual content itself - If the content is streamed off a normal website - what is to stop someoe capturing the stream, saving it on their hard drive and watching it over and over again ? If you want to prevent that you will need your own desktop application like Netflicks or similar.

Also note - when i say the above is easy - i was meaning if you have suitable development skills. If you are a complete novice then most of the above is probably way beyond you.

---

