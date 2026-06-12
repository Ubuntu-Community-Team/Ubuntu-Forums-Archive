---
title: "[php+regex] remove new lines"
date: 2010-08-24
forum: Programming Talk
---

### Post by ELD on 2010-08-24
Okay people say i have this:
[php]
        $pattern = '#\
[list\](.*?)\[/list\]#m'; 
         
        //$replace = ; 
         
        $text = preg_replace($pattern, '<ul>$1</ul>', $text); 
[/php]How would i go about removing any new lines found between the list bbcode tags in the $pattern ?

Is there a way to either remove any new lines directly in that or is there a way to ignore them and grab everything else?

---

### Post by Bachstelze on 2010-08-24
[php]$text = str_replace("\n", "", preg_replace($pattern, '<ul>$1</ul>', $text));[/php]

---

### Post by ELD on 2010-08-24
Not what i was looking for, as stated it needed to be directly in what i posted, the answer was this:
[php]
 $pattern = '#(?:\r\n?|\n)*\*(.*?)\*(?:\r\n?|\n)*#m';  
[/php]
Cheers anyway.

---

