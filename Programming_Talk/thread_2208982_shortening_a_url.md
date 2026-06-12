---
title: "shortening a url"
date: 2014-03-03
forum: Programming Talk
---

### Post by peter_brickles on 2014-03-03
HI Guys im harvesting urls from google for a project 

and get the following results 

> 
[http://www.proconnectmarketing.co.uk/appointments/pension-leadsDEF%252Bfinancial%2Bservice%2Bleads%26hl%3Den%26ct%3Dclnk&sa=U&ei=O44UU-66LvOw7AahzIHQCg&ved=0CD8QIDAE&usg=AFQjCNFqGxaLICPQbh_OlSf6AoR0PaV87Q](http://www.proconnectmarketing.co.uk/appointments/pension-leadsDEF%252Bfinancial%2Bservice%2Bleads%26hl%3Den%26ct%3Dclnk&sa=U&ei=O44UU-66LvOw7AahzIHQCg&ved=0CD8QIDAE&usg=AFQjCNFqGxaLICPQbh_OlSf6AoR0PaV87Q)
[http://www.firstimpression.comDEFfinancial-leads&sa=U&ei=O44UU-66LvOw7AahzIHQCg&ved=0CEIQFjAF&usg=AFQjCNGByOraTEFqagNfp7_4f-GM5qJI7g](http://www.firstimpression.comDEFfinancial-leads&sa=U&ei=O44UU-66LvOw7AahzIHQCg&ved=0CEIQFjAF&usg=AFQjCNGByOraTEFqagNfp7_4f-GM5qJI7g)
[http://www.firstimpression.comDEFfinancial-leads%252Bfinancial%2Bservice%2Bleads%26hl%3Den%26ct%3Dclnk&sa=U&ei=O44UU-66LvOw7AahzIHQCg&ved=0CEUQIDAF&usg=AFQjCNFtbkhNA6YTQlyj_bEP_cn0VEE9bA](http://www.firstimpression.comDEFfinancial-leads%252Bfinancial%2Bservice%2Bleads%26hl%3Den%26ct%3Dclnk&sa=U&ei=O44UU-66LvOw7AahzIHQCg&ved=0CEUQIDAF&usg=AFQjCNFtbkhNA6YTQlyj_bEP_cn0VEE9bA)
[http://www.iabuk.net/blogDEFtaking-the-lid-off-generating-financial-service-leads-online&sa=U&ei=O44UU-66LvOw7AahzIHQCg&ved=0CEcQFjAG&usg=AFQjCNFjuB75bgbZQyeR_Dcxrgnob0cIGw](http://www.iabuk.net/blogDEFtaking-the-lid-off-generating-financial-service-leads-online&sa=U&ei=O44UU-66LvOw7AahzIHQCg&ved=0CEcQFjAG&usg=AFQjCNFjuB75bgbZQyeR_Dcxrgnob0cIGw)


what i want to get to is 

> 
proconnectmarketing.co.uk
firstimpression.com
firstimpression.com
iabuk.net



is there any easy way to accomplish this with sed grep awk or any other cli tools ? 

Cheers Pete

---

### Post by Lars Noodén on 2014-03-03
Maybe something like this:

```

echo "http://www.iabuk.net/blog" | sed -e 's#^.*://##; s#/.*$##'

```

Normally it is **s///** but using the pound (#) instead makes it easier (IMHO) to search for and remove the slashes (/)

---

### Post by peter_brickles on 2014-03-03
thanks Lars that works partially but if i get a domain with a co.uk (should have included one in my example with hindsight) it doesnt catch all any ideas ?

---

### Post by Lars Noodén on 2014-03-03
It catches all the ones that I can think to try.  Can you post the one that gives sed trouble for you?

---

### Post by bluefrog on 2014-03-08
sed 's-http://\(.*\)/.*-\1-'

---

