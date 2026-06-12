---
title: "[SOLVED] PHP Regex Help"
date: 2009-01-06
forum: Programming Talk
---

### Post by cerealtx on 2009-01-06
im parseing a page for
```

so.addVariable("content_video", "http://movielink.flv");
```
for my regex what i have is
```

so.addVariable\(\"content_video\", \"(.*?)
```
which returns
```

movielink.flv");

```
how do i get rid of the "); its driving me crazy
here is the rest of the code
```
$url = "http://www.site.com/file.html";
 $input = @file_get_contents($url) or die('Could not access file: $url');
 $regexp = "so.addVariable\(\"content_video\", \"(.*?)";

 if(preg_match_all("/$regexp/siU", $input, $matches, PREG_SET_ORDER))
 {
 foreach($matches as $match)
    {
   //echo $match[0]; Matches what i want, and the rest of the page
   //echo $match[1]; Matches what i want, and the rest of the page
   echo $match[2]; //Supposed to be the link, comes up blank
   echo "\n";
   echo "\n";
   }
```

---

### Post by Bachstelze on 2009-01-06
```
php > $line = 'so.addVariable("content_video", "http://movielink.flv");';
php > print $line;
so.addVariable("content_video", "http://movielink.flv");
php > preg_match("/\"content_video\",\ \"(.*)\"/", $line, $tmp);
php > print $tmp[1];
http://movielink.flv

```

---

### Post by cerealtx on 2009-01-06
thank you so much has been driving me crazy all day

---

