---
title: "[PHP]Need help on calling javascript function"
date: 2012-04-15
forum: Programming Talk
---

### Post by kenweill on 2012-04-15
Need help on this code to work.
Code below works but part of it needs to be encoded.
Encoding it makes it not working.

[PHP]header ( "location:".$web["AffilateURL"]."&redirect=".$web["CouponURL"]."?ci=O72&utm_source=OMG&utm_medium=affiliate-cps&utm_term=324056&utm_content=textad&utm_campaign=domhotels" ) ;[/PHP]

This part: 
```
$web["CouponURL"]."?ci=O72&utm_source=OMG&utm_medium=affiliate-cps&utm_term=324056&utm_content=textad&utm_campaign=domhotels"
```

Needs to be encoded with encodeURIComponent ()

I tried:

[PHP]
<script type="text/javascript">
function encode_url ( tempurl ) 
{ 
return ( encodeURIComponent ( tempurl ) ) ; 
}
</script>

header ( "location:".$web["AffilateURL"]."&redirect=".encode_url ($web["CouponURL"]."?ci=O72&utm_source=OMG&utm_medium=affiliate-cps&utm_term=324056&utm_content=textad&utm_campaign=domhotels") ) ;[/PHP]

to no avail... Can someone recommend a better solution?

---

### Post by myrtle1908 on 2012-04-16
You don't want to encode the entire URI, rather just parts (components) of it - usually those which can come from a user.

Look what happens when you use encodeURIComponent on your entire query string

```
encodeURIComponent('?ci=O72&utm_source=OMG&utm_medium=affiliate-cps&utm_term=324056&utm_content=textad&utm_campaign=domhotels');

```

Yields

```
"%3Fci%3DO72%26utm_source%3DOMG%26utm_medium%3Daffiliate-cps%26utm_term%3D324056%26utm_content%3Dtextad%26utm_campaign%3Ddomhotels"
```

Read the following ... [https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/encodeURIComponent](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/encodeURIComponent)

---

### Post by kenweill on 2012-04-16
The entire

```
$web["CouponURL"]."?ci=O72&utm_source=OMG&utm_medium=affiliate-cps&utm_term=324056&utm_content=textad&utm_campaign=domhotels"
```

needs to be encoded. Not just the ci=O72 part.

$web["CouponURL"] is a variable (value fetched from database), example, value is [http://www.yahoo.com](http://www.yahoo.com) and so the value that should be encoded will be:

```
http://www.yahoo.com?ci=O72&amp;utm_source=OMG&amp;utm_medium=affiliate-cps&amp;utm_term=324056&amp;utm_content=textad&amp;utm_campaign=domhotels
```

Code above should be submitted to encode_url function but doesn't seems to work. Don't know if it's not possible to call a function inside header function, or if the javascript function is not working.

I don't have a clue.

It should return a value from the function:
```
http%3A%2F%2Fwww.yahoo.com%3Fci%3DO72%26amp%3Butm_source%3DOMG%26amp%3Butm_medium%3Daffiliate-cps%26amp%3Butm_term%3D324056%26amp%3Butm_content%3Dtextad%26amp%3Butm_campaign%3Ddomhotels
```

return value, i guess needs to also be enclosed with " " to make it work as argument for header function. I don't know how.

which makes the header function works as:
[PHP]header ( "location:".$web["AffilateURL"]."&redirect="."http%3A%2F%2Fwww.yahoo.com%3Fci%3DO72%26amp%3Butm_source%3DOMG%26amp%3Butm_medium%3Daffiliate-cps%26amp%3Butm_term%3D324056%26amp%3Butm_content%3Dtextad%26amp%3Butm_campaign%3Ddomhotels" ) ;  [/PHP]

---

### Post by dharmavir on 2012-04-17
Try following function:

[http://phpjs.org/functions/urlencode:573](http://phpjs.org/functions/urlencode:573)

---

### Post by kenweill on 2012-04-17
> **dharmavir said:**
> Try following function:

[http://phpjs.org/functions/urlencode:573](http://phpjs.org/functions/urlencode:573)

Thank you very much. This is what I needed. A stand-alone encodeurl function. :)

---

