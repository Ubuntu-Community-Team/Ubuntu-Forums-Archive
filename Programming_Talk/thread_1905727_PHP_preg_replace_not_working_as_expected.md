---
title: "PHP preg_replace not working as expected"
date: 2012-01-07
forum: Programming Talk
---

### Post by epicoder on 2012-01-07
I'm using the following code to apply html tags to a chat style collection of lines.
[PHP]while ($char=mysql_fetch_assoc($chars)) {
    $pattern="/%s:(.*?)([01]?[0-9]:[0-5][0-9])\\s*$/m";
    if ($char['casesensitive']==0) { $pattern .= "i"; }
    $pattern=sprintf($pattern, $char['name']);
    $replace=sprintf('%s:<span style="color:%s;">$1</span> $2', $char['name'], $char['color']);
    $caption=preg_replace($pattern, $replace, $caption);
}
[/PHP]The database query and sprintf are coded correctly and return the proper values, and $caption is defined before the loop shown. I have tested that many times. I have also taken the values that would have been passed into preg_replace, and run them on my local installation of PHP, which replaces the text as expected. However, on the webserver I'm attempting to use this on, the pattern doesn't match anything and doesn't modify $caption at all.
I'm attempting to replace lines like this:
[HTML]<br>Name: This text will be colored. 8:47[/HTML]With this:
[HTML]<br>Name:<span style="color:color;"> This text will be colored.</span> 8:47[/HTML]I'm using preg_replace several other times to perform similar operations in the same script, and it works perfectly.
Both installations of PHP are version 5.3.8.

---

### Post by dazman19 on 2012-01-07
have you tried to preg_match( it first. 

if you cant get it to match, then it will be a problem with the pattern not being correct. 

I generally tend to use single quotes ' rather than double quotes " when using regular expressions. Unfortunately i dont have my regexbuddy on this PC so i cant check your pattern. In php the quotes are different and can have different behaviours.

also, you should check to see if your preg_replace( is retuning NULL) this way you can determine if your pattern has become invalid. 

preg_replace() returns an array if the subject parameter is an array, or a string otherwise.

If matches are found, the new subject will be returned, otherwise subject will be returned unchanged or NULL if an error occurred.

---

### Post by epicoder on 2012-01-07
> I have also taken the values that would have been passed into  preg_replace, and run them on my local installation of PHP, which  replaces the text as expected. However, on the webserver I'm attempting  to use this on, the pattern doesn't match anything and doesn't modify  $caption at all.
The pattern is definitely syntactically correct, as $caption is not modified at all- preg_replace simply returns the string it was passed. I have echoed the generated pattern and replacement string, taken them, and pasted them exactly as they were into my local installation of PHP, testing on exactly the same data. The text was processed as expected, that is, the tags were applied.

---

