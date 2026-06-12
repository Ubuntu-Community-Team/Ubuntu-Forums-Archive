---
title: "PHP: deyaed download"
date: 2007-01-29
forum: Programming Talk
---

### Post by MadeR on 2007-01-29
I'm trying to write a page that displayes some text and sends a file to the users: for example when you download something from sourceforge, downloading starts after a web page is shown.

How to achieve that?

usually I use this method, but in this case it does not work because I can't output daata to the webpage before a header() command:


$nome_file = "ghillies_final.pdf";
$dimensioni_file = filesize( $nome_file );

header("Content-type: Application/octet-stream");
header("Content-Disposition: attachment; filename=$nome_file");
header("Content-Description: Download PHP");
header("Content-Length: $dimensioni_file");
readfile($nome_file);

---

### Post by lnostdal on 2007-01-29
http-equiv redirect @ google

---

