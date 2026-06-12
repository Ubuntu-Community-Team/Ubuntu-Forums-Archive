---
title: "need to produce .txt file from php order form"
date: 2009-11-25
forum: Programming Talk
---

### Post by methodicalx on 2009-11-25
I have designed a very basic order from in HTML that asks for customers personal information and asks the customers the quantity of shirts they wish to purchase.  Customer hits submit and I have php to produce an output page that summarizes the customers order.  How do I have this output page created as a downloadable .txt file?

---

### Post by Mr. Devil on 2009-11-25
[php]$content = "Append this with the content you want to be written to the output file ( .txt ).";
$file = fopen("output.txt", "w");
fwrite($file, $content);
fclose($file);[/php]

---

### Post by methodicalx on 2009-11-25
Mr. Devil, I appreciate your response.  I am quite new to php so I am confused as to where in my file I would place this code.

---

### Post by CyberJack on 2009-11-26
You can create it the same way you created the html file witch summarizes the order.
Instead echoing/printing html code, you add the text to one big variable.

Like Mr. Devil wrote:
[PHP]
$content = "Append this with the content you want to be written to the output file ( .txt ).";
[/PHP]
The complete order should end up in $content.

After that you can do write the text file to a file on the server
[PHP]
$file = fopen("output.txt", "w");
fwrite($file, $content);
fclose($file);
[/PHP]

---

### Post by v8YKxgHe on 2009-11-26
Instead of fopen/fwrite/fclose it is far easier to use [http://php.net/file_put_contents](http://php.net/file_put_contents), e.g.

[php]file_put_contents('foo.txt', 'bar');[/php]

However, to answer the OPs question - you'll need to use [http://php.net/header](http://php.net/header) to set the needed headers. Scroll down to example 1 and read that. A small example of mine:

[php]
header('Content-Type: text/plain; charset=utf-8');
header('Content-Disposition: attachment; filename=foo.txt');
echo 'contents of file';[/php]

---

