---
title: "Wierd bug on my website, possible PHP problem?"
date: 2009-04-04
forum: Programming Talk
---

### Post by gjoellee on 2009-04-04
Hi there!

I just updated my website [www.kshoster.net](www.kshoster.net) with a new template. It looks great, but of some reason it doe snot work great...

Every page looks the same as the home page. See yourself....try to go to, ie. The about page. It looks the same!

What makes it even more weird is that it works great on localhost! So if it works in localhost, why doesn't it work on the internet?

I am not sure which files you need to look at,but this might help you...?
```

            <div id="content-in"> 
            <?php 
            if(!isset($c)) { 
                $c = "main"; 
            } 
             
            $shitzang = "inc/$c.php"; 
             
            if(!file_exists($shitzang)) { 
                $shitzang = "inc/404.php"; 
            } 
             
            include($shitzang); 
            ?> 
      </div> 
               
```

---

### Post by s.fox on 2009-04-04
Hi,

Your links direct the user to the same page but you are passing a variable "c".  

Where are you reading in the variable "c" on your index.php page?  I don't see it in your code posted above.

Odd that it works on local host though...

---

### Post by gjoellee on 2009-04-04
The code above adds another file called "main.php" to the place where the code is (the code above) in the index.php file.

---

### Post by gjoellee on 2009-04-04
Here is an attachment on my index.php file (but because the forums don't allow .php it is in .txt)

---

### Post by gjoellee on 2009-04-04
It works! Don't know how...!

---

### Post by simz on 2009-04-04
Hi!

I have uploaded a fix.

The problem was that $c was not defined properly. I also fixed the tux gallery.

- simz

---

