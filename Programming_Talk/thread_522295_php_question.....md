---
title: "php question...."
date: 2007-08-10
forum: Programming Talk
---

### Post by hockey97 on 2007-08-10
HI  I made my own php script, and now want to make  a html doc, or at least use html for most of the layout of the site.

my php script was a ad switcher, so is their a way, where on every website I make that I can include this script??

like instead of rewriting or copy and past it into all my websites, 

is their a include or some function that I could just in every website 
put include , ad.php or somthing like that so that it could be intergrated with every site that I put that include.

like something like in C++ where you use include , same type of concept, where I could make a script and then include it in every site I made and then in the site's source code, i just use the fucntions I need for that one site???

---

### Post by smartbei on 2007-08-10
There is something exactly as you described:

```

<?php
include "ad.php";
?>

```

Then just call the relevant functions when you need them.

---

### Post by hockey97 on 2007-08-10
Thanks , that's what I was looking for, but do I have to tell the path to that file to php???

Um also does anyone know how to create your own custom gui type thing for flash videos??

I have seen on facebook.com a thing that would have a pic of a tv and use the flash video inside the tv right on the tv screen, made it look like your watching tv.

---

### Post by Wybiral on 2007-08-10
> **hockey97 said:**
> Thanks , that's what I was looking for, but do I have to tell the path to that file to php???

Um also does anyone know how to create your own custom gui type thing for flash videos??

I have seen on facebook.com a thing that would have a pic of a tv and use the flash video inside the tv right on the tv screen, made it look like your watching tv.

A border around an embedded video could be as simple as some well styled HTML.

But if you mean interactive, like part of the video, then it will probably have to be flash or something (I can't help much there, I've personally never programmed in flash).

---

### Post by smartbei on 2007-08-12
As for the question about includes - you need to specify the path to the included file in either absolute terms, or relative to the current file. Thus, if you had a directory "App" in which your "index.php" file resides, and another directory in "App" called "includes" in which your file to be included, "fff.php" resides:
```

<?php
include "includes/fff.php";
?>

```

---

