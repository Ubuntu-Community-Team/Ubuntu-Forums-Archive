---
title: "gEdit - PHP Syntax Highlighting &amp; Replace Function"
date: 2006-11-14
forum: Programming Talk
---

### Post by altonbr on 2006-11-14
These question are regarding gEdit (Ubuntu's default text editor):

1) Is there a way to highlight embedded PHP variables (the kind that show up in strings).
```
<?php
print("<td>$todays_month</td>");
?>
```
> [COLOR=Red]<?php[/COLOR]
[COLOR=Blue] print[/COLOR]("[COLOR=Gray]<td>[/COLOR]**[COLOR=DarkRed]$todays_month[/COLOR]**[COLOR=Gray]</td>[/COLOR]");
[COLOR=Red] ?>[/COLOR]
2) Is there a way to use the replace function on only text you've selected? Sometimes when I am copying and pasting HTML in my PHP, I need to PHPize the HTML code (aka: replace " with \") and it's annoying that I the settings aren't verbose enough to do a replace only on a section of the page.

I love gEdit other than that. It's the best replacement for Notepad++ I've found so far. And I am aware that Bluefish as it's own Syntax Highlighting Editor, where you can see the regular expressions the program uses, but I wouldn't know where to begin in creating one for embedded variables in PHP. I'm still a beginner mind you.


EDIT:: Also, as I just noticed, gEdit doesn't have ASP highlighting. I mean I hate ASP as much as the next man, but I find it interesting that it only has VB.NET for highlighting. I just need to use my desktop temporarily until my laptop's ethernet connection software (that the school provides) is fixed.

---

### Post by altonbr on 2006-12-06
Bump.

---

### Post by altonbr on 2006-12-12
Does no one find this a necessary function?

---

### Post by Kurt` on 2006-12-15
Don't output HTML like that... just do this:

```
echo <<<WHATEVER
blah
blah
<p style="font-size: 20px;">
more stuff and html, oh look a $variable
</p>
blahblah
WHATEVER;
```

It's called "here document" syntax and it kicks *** :p

---

### Post by altonbr on 2006-12-15
But how do you get it so there is a syntax colour change for the variables embedded in the HTML?

Like this:
> [COLOR="Blue"]echo([/COLOR]"
[COLOR="Gray"]blah
blah
<p style="font-size: 20px;">
more stuff and html, oh look a [/COLOR][COLOR="DarkRed"]**$variable**[/COLOR]
[COLOR="Gray"]</p>[/COLOR]
"[COLOR="Blue"]);[/COLOR]

---

### Post by Helmi on 2007-07-21
Any news on that?

I found a solution for Ruby - perhaps someone is able to adept it for php?

[http://grigio.org/textmate_gedit_few_steps](http://grigio.org/textmate_gedit_few_steps)

---

### Post by altonbr on 2007-07-22
> **Helmi said:**
> Any news on that?

I found a solution for Ruby - perhaps someone is able to adept it for php?

[http://grigio.org/textmate_gedit_few_steps](http://grigio.org/textmate_gedit_few_steps)

No, but that syntax highlighting sure looks slick.

Oddly, I was JUST going to make another post on this topic and you replied to my old thread. I just took this screenshot a couple of minutes ago comparing Notepad++ (4.1.2) to gEdit (2.18.1).

I had Gusty loaded for quite some time and tried gEdit 2.19 but it seems as though this function isn't built into gtksourceview yet. I also joined the gEdit development mailing list, so I'll make a post on there soon.

---

### Post by smartbei on 2007-07-24
I am very satisfied with the way Geany does the higlighting - it detects variables inside quotes, etc. It's also very lightweight and responsive, which is what I always liked about notepad++ when I still had windows.

---

### Post by altonbr on 2007-08-28
Well my ranting and raving finally go through to somebody. 2006-11-14 to 2007-08-28 was the length it took to fix.

I made a post here: [http://ubuntuforums.org/showthread.php?p=3269797](http://ubuntuforums.org/showthread.php?p=3269797) describing how gEdit 2.19.91 finally highlights PHP variables inside strings. It even has a new gorgeous theme too!

---

