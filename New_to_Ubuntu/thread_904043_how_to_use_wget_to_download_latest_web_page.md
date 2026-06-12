---
title: "how to use wget to download latest web page"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by say2sky on 2008-08-28
situation:
I search Youtube for olympic and sort search results by date added. I get a web address as 

[http://www.youtube.com/results?search_query=olympics&search_sort=video_date_uploaded](http://www.youtube.com/results?search_query=olympics&search_sort=video_date_uploaded)

next time when I visit this address I get the latest content about olympic. I hope to use wget to download the same page but I only get some past content listed.

my question is:
1) why I cannot download the latest content page through wget as I visit Youtube through FF?   java script?
2) is there a way to get the same content page by using wget as through FF.

---

### Post by say2sky on 2008-08-28
Please help. Your suggestion are greatly appreciated.

---

### Post by unutbu on 2008-08-29
Try

```

wget "http://www.youtube.com/results?search_query=olympics&search_sort=video_date_uploaded"
```
Without the quotations, bash snatches the & and interprets it in a way you do not intend and the "sort by date" directive never gets to youtube.

---

### Post by say2sky on 2008-08-29
> **unutbu said:**
> Try

```

wget "http://www.youtube.com/results?search_query=olympics&search_sort=video_date_uploaded"
```
Without the quotations, bash snatches the & and interprets it in a way you do not intend and the "sort by date" directive never gets to youtube.

great, you are right. thanks a lot for your help. :)

---

### Post by aloshbennett on 2008-08-29
Very interesting! I've been on it for past 30 mins. This is what I found out:
You are getting the same contents using wget. Just that it's sorted in the order of relevence and not by the date added. Maybe they do that by forwarding the request once more using javascript?

---

### Post by aloshbennett on 2008-08-29
> **unutbu said:**
> 
Without the quotations, bash snatches the & and interprets it in a way you do not intend and the "sort by date" directive never gets to youtube.

This one is worth remembering! :)

---

