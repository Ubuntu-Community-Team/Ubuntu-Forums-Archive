---
title: "Javascript"
date: 2008-03-16
forum: Programming Talk
---

### Post by gjj391 on 2008-03-16
so i have this validate function....


function validate(){
  
    var errorField=document.getElementById("errorField")
    message = "<h3>please correct the following errors</h3>"
    
    if(entryName.value == "" || entryName.value.match(/[^a-zA-Z]/)){
       message += "<p>Please enter your name. Alphabetical letters only.</p>\n"
       entryName.style.border = "3px solid red"
       errorField.style.display = "block"
    }

    else if (entryEmail.value.indexOf("@") == -1 || entryEmail.value.indexOf("@") == 0) {
       message += "<p>Please enter valid email address. (name@domain.com)\n</p>"
       entryEmail.style.border = "3px solid red"
       errorField.style.display = "block"
    }
 
    errorField.innerHTML = message;
}


So right now it runs each if at a time while validating, so pretty much the next one will not get validated till the prior is valid.

How would I validate them all at once?

---

### Post by gjj391 on 2008-03-16
okay nvm.. that was dumb! else if ? haha

---

### Post by LaRoza on 2008-03-16
That wasn't dump, that was a bug :)

For debugging such scripts, you should use Firebug. It allows you to see exactly what is going on as the script runs and you can set break points.

It is a Firefox extension, so you'll have to use Firefox when you use it. Sorry about that, as Opera is better. 

[https://addons.mozilla.org/en-US/firefox/addon/1843](https://addons.mozilla.org/en-US/firefox/addon/1843)

---

### Post by Wybiral on 2008-03-16
> **LaRoza said:**
> Sorry about that, as Opera is better.

No way, FF could own Opera any day.

---

