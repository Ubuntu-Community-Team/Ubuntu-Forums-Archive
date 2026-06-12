---
title: "Providing dynamic input to dapper"
date: 2011-07-24
forum: Programming Talk
---

### Post by RobikShrestha on 2011-07-24
I am not sure if this is the right forum to ask this question, but it certainly is the most helpful forum so here my question:

I have created a dapper to fetch article from a site.
Now I would like to fetch new articles each day. So I want the dapper to fetch article from new web page each day. I have generated xml for getting the new address of the new web page containing article. How will I provide this as input to the dapper so that it fetches me new articles each day?

---

### Post by RobikShrestha on 2011-07-24
Well, if anyone is interested in the solution, here it is:

First create a dapper which gives out links.
Then create another dapper which would read articles from links similar to the above links.
Then, enter the first dapper and click on "[Link Dapp's output to another Dapp]("http://open.dapper.net/dapp-linker.php?startDapp=EKantipurBusiness")".

Then, enter the name of the second dapper.
Then, provide the url of first dapper to URL of second dapper.

---

