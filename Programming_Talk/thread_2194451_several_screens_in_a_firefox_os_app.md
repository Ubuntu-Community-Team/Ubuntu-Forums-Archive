---
title: "several screens in a firefox os app"
date: 2013-12-18
forum: Programming Talk
---

### Post by chuchi on 2013-12-18
Hi everyone!! 
 
I am developing a firefox os app and the app will have several screens. I am wondering how to implement several screens.

I see two options: 
 
To create only one file (index.html) and use several divs (sections) in that file. 
 
```
 
<div id="presentation" class="page" data-role="page"> 
                
</div> 
 
<div id="page_signin" class="page" data-role="page"> 
                 
</div> 

``` 
 
 
 
The second option would be to use several files, and in the index.html use several "<a>" elements  and href attribute. So when you click on the "a" element a new page, lets say signin.html will open. 
 
 ```
 
<div id="presentation"> 
    <a href=”signin.html”>Sign in</a>                

</div> 

``` 


Which option would you prefer? Let me know if you would prefer a new solution.

Thank you very much!

---

