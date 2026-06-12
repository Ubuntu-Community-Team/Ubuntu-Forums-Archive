---
title: "How to pass value with out variable in query string in PHP?"
date: 2008-12-01
forum: Programming Talk
---

### Post by Ali_ggl on 2008-12-01
Hello guyz.

I am working to find out some solution to access a web page in PHP that is showing information on the bases of given argument in query string variable, it can by any string. My problem is this that I want to get the value on the page that is coming in url with out any variable and file name. But I don’t have any idea ho to do this, i saw many of sites are showing there contests with out using the variable name and the file name just value is passing and on the bases of given value result is coming from database. This technique will reduce the url. and better for SEO purpose that's why i am looking for solution for this technique. Like below urls will be reduced if i got the technique.
:lolflag:

globalguideline.com/JavaScript_Guide/JavaScript_Examples.php?JScript=first_JavaScript
globalguideline.com/JavaScript_Guide/JavaScript_Examples.php?JScript=JavaScript_HelloWo rld
globalguideline.com/JavaScript_Guide/JavaScript_Examples.php?JScript=HTML_With_JavaScri pt

But I want to open the same pages as below urls instead of above all.

globalguideline.com/JavaScript_Guide/first_JavaScript
globalguideline.com/JavaScript_Guide/JavaScript_HelloWorld
globalguideline.com/JavaScript_Guide/HTML_With_JavaScript

I am sure this is possible in PHP i saw on many sites, i got hosting from web hosting company if i need to configure some server settings then please guide me with the entire solution.
Regards,
:confused:
Ali.

---

### Post by MicahCarrick on 2008-12-01
Sounds to me like you are looking to do URL rewriting. This is done with Apache's mod_rewrite module. Most hosting companies support mod_rewrite and you control it using a .htaccess file.

In short, your PHP scripts don't change, but apache "rewrites" URLs to match what your script is expecting while allowing you to have search engine friendly URLs. As the example you posted below, the rewrites might look something like (this is just an example, you'll have to read up on mod_rewrite):

```
RewriteEngine On

RewriteRule ^/JavaScript_Guide/(.*)$ /JavaScript_Guide/JavaScript_Examples.php?JScript=$1
```

---

