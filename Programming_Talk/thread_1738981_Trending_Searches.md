---
title: "Trending Searches"
date: 2011-04-25
forum: Programming Talk
---

### Post by jeezoflip on 2011-04-25
Hey, I have a website that does searches using some javascript and ajax. I wanted to make a trending searches feature that ranks search queries on the front page based on how many people are searching for them. I didn't program the site which is why I'm asking how to do this, or what to do it in. Any help is appreciated!

---

### Post by simeon87 on 2011-04-25
Count each search query and sort them from most to least searched? And then look only at the searches of the last n days... a search of 30 days ago is not really trending but perhaps within the last 7 days? Or 3 days? Something like that.

---

### Post by jeezoflip on 2011-04-25
Thank you for the response! Would I have to do this in mysql (or any other database). Also, what language would you suggest doing this in?

---

### Post by simeon87 on 2011-04-25
> **jeezoflip said:**
> Thank you for the response! Would I have to do this in mysql (or any other database). Also, what language would you suggest doing this in?

The language in which the website is currently written (back-end) seems the most obvious choice. If you store the queries in MySQL then you could write a page that analyzes the queries and computes the trending searches. So basically you obtain the queries from the database, you compute which ones are currently trending, and then you display that on your website. It depends on how many queries you're getting but just experiment to see how efficiently you can compute this information.

---

