---
title: "Saving Javascript array using PHP to file."
date: 2009-12-06
forum: Programming Talk
---

### Post by niiize on 2009-12-06
Hi. 
I have this huge Javascript Array, and need to somehow save the content of it to a text-file...

Thanks

---

### Post by myrtle1908 on 2009-12-06
What's in the array?  If it's just basic one dimension string/number then you could simply join the array and submit it to the server.  If it's a more complex array then encode/serialize it to a JSON string and submit it.

---

### Post by niiize on 2009-12-06
do you mean using a hidden html input element to store the variable in and post it?

---

### Post by myrtle1908 on 2009-12-06
That would work fine.  Or you could execute an AJAX request using your favourite JS lib eg. jQuery

---

### Post by niiize on 2009-12-06
The thing is the array is 10kb in size. So I don't think the browser can store this data that way, can it? might have to go with Ajax then?

---

### Post by mnemonik on 2009-12-06
I'm pretty sure you can POST strings of that size, but I think GET has a somewhat arbitrary limit (can someone affirm or correct this?) but the point is there isn't a difference between using ajax or a hidden field. Its all HTTP.

Definitely use a json encoder for safety though. ([http://www.json.org/json2.js](http://www.json.org/json2.js))

---

### Post by mnemonik on 2009-12-06
Also, what is your larger goal? There is possibly a Better Way to do whatever it is than putting the array in a text file...

---

### Post by myrtle1908 on 2009-12-06
> **mnemonik said:**
> but I think GET has a somewhat arbitrary limit (can someone affirm or correct this?)

Fairly certain there is no limit on URL size (at least in the specification) however some web browsers (eg. IE) have smaller limits than others.  Also, the web server may truncate overly long GET requests.  Best to use POST.

---

### Post by niiize on 2009-12-06
using hidden field along with POST method worked.

---

