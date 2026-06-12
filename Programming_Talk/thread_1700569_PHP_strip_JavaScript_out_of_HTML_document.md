---
title: "PHP: strip JavaScript out of HTML document"
date: 2011-03-05
forum: Programming Talk
---

### Post by yc2 on 2011-03-05
Hello,

I want to machine-translate a PHP-JavaScript-HTML document.

I have found that "Google translate" translates well but really messes up the JavaScript. (only one example: "var i=0;" becomes "was i=0;" since the Swedish word for "was" is "var" !!)

I need to strip the javascript out of the document, translate the document and replace the JavaScript, I think.

I only have access to PHP through my web-server.

I thought maybe I could isolate all JS-parts in an array somewhat like this

$myHTML = curl("http:....")
preg_match("/<script.*?<\/script>/i", $myHTML, $matches) 

and then replace them each with a unique numbered code using preg_replace

then translate the document and finally replace the JS array components.

----

Before I start this program I just ask if anyone knows of a better way of temporarily removing JS out of a document, working on the document, and finally replacing the JS?

Thanks

EDIT:
I think I already see a problem with this approach. The reg ex .* will not work since I think PHP does not support the "lazy" .*?

---

