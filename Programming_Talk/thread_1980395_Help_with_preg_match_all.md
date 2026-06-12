---
title: "Help with preg_match_all"
date: 2012-05-15
forum: Programming Talk
---

### Post by mandza on 2012-05-15
i dont know is this right place for asking this, but i need help.

i want to read xml with preg_match_all.

this is my xml structure:

<site>
<st-id>$sitelerl[id]</st-id>
<st-url>$sitelerl[url]</st-url>
<st-puan>$sitelerl[puan]</st-puan>
<st-bayipuan>$sitelerl[bayipuan]</st-bayipuan>
</site>

(this is being repeated)
------------------
i writed preg_match_all like this:

preg_match_all('/<site>(.*?)<\/site>/i',$sonuc,$cikti);
echo $cikti[1][0];
-----------
my question is what i need (.*?) to repleace with so i can pull all data between <site></site> ?????

Thank you a lot.

---

### Post by roelforg on 2012-05-15
May i advise you to use php's SimpleXML?
Because, like the name says, it's simple!
Here's a sample:
```

<?php
$xml = <<< XML
<site>
<st-id>a</st-id>
<st-url>b</st-url>
<st-puan>c</st-puan>
<st-bayipuan>d</st-bayipuan>
</site>
XML;
$sxml=new SimpleXMLElement($xml);
var_dump($sxml);
echo $sxml->{"st-id"}.PHP_EOL;
?>

```
See the result at: [http://codepad.org/o1ChNQ5i](http://codepad.org/o1ChNQ5i)
 
I strongly advise against parsing it yourself.

---

### Post by mandza on 2012-05-15
Thank you very much roelforg this solved my problem

---

### Post by roelforg on 2012-05-15
> **mandza said:**
> Thank you very much roelforg this solved my problem
 
No probs.

---

