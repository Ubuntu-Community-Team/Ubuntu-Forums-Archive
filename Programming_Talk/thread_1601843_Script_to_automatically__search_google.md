---
title: "Script to automatically  search google?"
date: 2010-10-20
forum: Programming Talk
---

### Post by mju4t on 2010-10-20
Does anybody know if it would be possible to write a script that would automatically search google (or some other search engine) and then pick a certain result from the results page?

For example, I want to look up how many employees are in a company.  So I search hoovers.com and look at 2009 employees.

I want to repeat this with different companies.

Does anybody know of a solution (other than typing in by hand)?

---

### Post by geirha on 2010-10-20
I'd look to see if there is some kind of yellow pages site of these companies, which would probably report such information in a consistent way. Then maybe you could script it.

Otherwise, if you write the most advanced AI in the world ... you might be able to pull that off.

---

### Post by oldfred on 2010-10-20
You can use python and screen scrap the data. I found this one with google that may be close to what you want:

[http://www.jbryanscott.com/2009/02/07/nasdaq-100-revenue-per-employee/](http://www.jbryanscott.com/2009/02/07/nasdaq-100-revenue-per-employee/)

---

### Post by coabiguy on 2010-10-20
I downloaded and tested a Python package to assist in automating web interaction.
I can't remember the name now and it is on my work machine, however, is you think you might want to try it, you can.

It would allow you to basically navigate to any page, fill in text boxes, drop downs, etc. and then hit the submit button. The results could be filtered with whatever python code you want to add.

---

### Post by mju4t on 2010-10-21
Thanks for the replies!  I think screen scraping is the way to go, this is the first time I've heard of this concept.  Sounds interesting. 

That script that J Bryan Scott did for the top-100 NASDAQ is exactly what I'm looking for...too bad he didn't post the source code!

Thanks for the input everybody.

---

### Post by SeijiSensei on 2010-10-21
You could probably do it in bash using wget to run the searches and save the results, then use grep+awk to find the lines with the data you need and extract them to a text file.  I've used PHP for similar tasks where I grab a remote web page, place the results in an array, than parse the rows to find the data I need.

---

### Post by KIAaze on 2010-10-21
Isn't that a bit like what wolfram alpha does?: [http://www.wolframalpha.com/](http://www.wolframalpha.com/)

They don't use google, but they automatically get their info from some other online sources (which is indeed easier since it limits the format of search results).

edit: Ok, so they don't "search the web", but just update their database from it. Sorry. ^^'
> Does Wolfram|Alpha get its data from the web?
No. It comes from Wolfram|Alpha's internal knowledge base. Some of the data in that knowledge base is derived from official public or private websites, but most of it is from more systematic primary sources.
[http://www.wolframalpha.com/faqs.html](http://www.wolframalpha.com/faqs.html)

---

### Post by v8YKxgHe on 2010-10-21
Scraping is against the Google ToS, use the correct API they offer. See [http://code.google.com/apis/ajaxsearch/documentation/#fonje](http://code.google.com/apis/ajaxsearch/documentation/#fonje)

---

### Post by kbryk on 2010-10-21
> **SeijiSensei said:**
> You could probably do it in bash using wget to run the searches and save the results, then use grep+awk to find the lines with the data you need and extract them to a text file.  I've used PHP for similar tasks where I grab a remote web page, place the results in an array, than parse the rows to find the data I need.

I've done something similar in Java.

---

