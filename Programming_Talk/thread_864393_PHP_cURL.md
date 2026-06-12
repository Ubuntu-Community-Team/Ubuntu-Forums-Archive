---
title: "PHP cURL"
date: 2008-07-19
forum: Programming Talk
---

### Post by instanttron on 2008-07-19
I opened the browser with this url, [http://77.666.555.44:8080/file/test.jsp](http://77.666.555.44:8080/file/test.jsp)
That is a sample server address
It works fine in the browser, I see the page.

But when I run it through cUrl it stalls and returns a blank page.
The error message I get from cUrl is “couldn’t connect to host”

Any reason why?
I am new to PHP
If anyone knows the answer please help
I have been stuck on this for weeks.
Any advice will be appreciated. 

The PHP code:

$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, “[http://77.666.555.44:8080/file/test.jsp”);](http://77.666.555.44:8080/file/test.jsp”);)
curl_setopt($ch, CURLOPT_TIMEOUT, 20);
curl_setopt($ch, CURLOPT_FOLLOWLOCATION, 1);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);

$response = curl_exec($ch);

if (curl_errno($ch)) {
    echo curl_error($ch);
} else {
    echo $response;
    curl_close($ch);
}

could this be a permission thing?

---

