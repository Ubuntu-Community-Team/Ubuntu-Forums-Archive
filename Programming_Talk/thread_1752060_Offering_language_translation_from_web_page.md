---
title: "Offering language translation from web page"
date: 2011-05-07
forum: Programming Talk
---

### Post by Nytram on 2011-05-07
Hi folks

I'm looking to build a web page with the capability of translating English to Spanish and vice versa.

Something like this:

[http://www.spanishdict.com/translation]("http://www.spanishdict.com/translation")

What that page does is accept one line of text from the user, feeds it to 3 translation services, and then refreshes the page with the results each in their own iframe.

How would I go about replicating this? I'm not asking for the code, just pointers in the right direction. Can it be done with client-side languages alone, or do I need a CGI script?

Thanks.

---

### Post by cgroza on 2011-05-07
This would run on the server side.
You need to use the API of those 3 services.
They would send you back the data in a format or another, you interpret it and display it.

---

### Post by myrtle1908 on 2011-05-07
The Google Translate APIs are good.  You want the Transliterate API ... [http://code.google.com/apis/language/transliterate/v1/getting_started.html](http://code.google.com/apis/language/transliterate/v1/getting_started.html)

---

### Post by Nytram on 2011-05-09
Thanks for the advice.

I've never done server side scripting before but I'm familiar with Python so it shouldn't be too difficult.

---

### Post by myrtle1908 on 2011-05-10
> **Nytram said:**
> Thanks for the advice.

I've never done server side scripting before but I'm familiar with Python so it shouldn't be too difficult.

No need for server side programming if you use the Google Translate API.  It couldn't be easier ... [http://code.google.com/apis/language/transliterate/v1/getting_started.html#hiworld](http://code.google.com/apis/language/transliterate/v1/getting_started.html#hiworld) :)

---

