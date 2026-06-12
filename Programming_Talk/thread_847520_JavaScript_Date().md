---
title: "JavaScript Date()"
date: 2008-07-02
forum: Programming Talk
---

### Post by Tux.Ice on 2008-07-02
how can i get a picture on a website to change depending on the time of day?

from 6am-10am == mornlogo.png
from 10am-3pm == daylogo.png
from 3pm-5pm == setlogo.png
from 5pm-6am == nightlogo.png

could i just use an array with a Date() function and then do document.images or document.write?

---

### Post by LaRoza on 2008-07-02
> **Tux.Ice said:**
> how can i get a picture on a website to change depending on the time of day?

from 6am-10am == mornlogo.png
from 10am-3pm == daylogo.png
from 3pm-5pm == setlogo.png
from 5pm-6am == nightlogo.png

could i just use an array with a Date() function and then do document.images or document.write?

It would be easy...

Just use the DOM to change the image src attribute (have a default one coded in) according to the date.

---

### Post by Tux.Ice on 2008-07-02
im a pretty big n00ber at JS, how would i put a DOM into this, ii was actually thining of using an if statement.

---

### Post by LaRoza on 2008-07-02
> **Tux.Ice said:**
> im a pretty big n00ber at JS, how would i put a DOM into this, ii was actually thining of using an if statement.

I hope you were thinking about it...

First make the <img /> element, with a default image and give it an id. For this, I am giving it an id="time".

[php]
window.onload = function()
{
    var imgElement = document.getElementById("time");
    var d = new Date().getHours() + 1;
    if (imgElement)
    {
        if (d >= 6 && d <= 10)
        {
           imgElement.setAttribute("src","mornlogo.png")
        } 
        //etc 
    }
}
[/php]

---

