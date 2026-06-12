---
title: "Problems with php displaying in internet explorer"
date: 2010-02-01
forum: Programming Talk
---

### Post by Zigon on 2010-02-01
[PHP]
$exmenu .= '<li><a href="products.php?page='. $links['sub_category'][$second_counter] .'#'. $links['id'][$second_counter] .'" ">' . ucwords($links['name'][$second_counter]) .'</a></li>';
[/PHP]
This is working fine in firefox, chrome and safari, but when I try to view the page in IE I don't get an error or anything the list just doesn't appear. I'm also using javascript with this menu to expand expand and collapse.

EDIT: IE is actually showing me an error in my menu.js on the red line char 5. It's all outputting correctly now that it's telling me there's an error, but I didn't even change anything yet I just refreshed the page a million times.
```
function initMenu(){
  var menus, menu, text, a, i;
  menus = getChildrenByElement(document.getElementById("menu"));
  for(i = 0; i < menus.length; i++){
    menu = menus[i];
    text = getFirstChildByText(menu);
    a = document.createElement("a");
   [COLOR="Red"] menu.replaceChild(a, text);[/COLOR]
    a.appendChild(text);
    a.href = "#";
    a.onclick = showMenu;
    a.onfocus = function(){this.blur()};
  }
}
```
What's happening?

---

### Post by Hellkeepa on 2010-02-01
HELLo!

First off, the title is a misnomer: PHP does not ever reach the browser, it's all handled by the server. What the browser sees is HTML, CSS and JavaScript. The latter of which is your issue here.

If I were to guess, I reckon that either you have an error with the parameters, or that IE does not support the "replaceChild()" method. Without knowing the error message I cannot help you further.

Happy codin'!

---

### Post by CyberJack on 2010-02-02
Maybe a bit offtopic, but why aren't you using a javascript framework like jquery?
Javascript frameworks make tasks like this easy to develop and cross-browser compatible. 

If I take a look at your code, you are trying to replace all menu items (disable the href and add a onclick to each new menu item).
I guess you do this to prevent the browser from going to the selected page. And when clicked, a function "showMenu" is called.

If for example you should have written this in jquery, it would have taken 6 lines of code and it is cross-browser compatible:
```

$(document).ready(function() {
  $("#menu a").click(function(e) {
    e.preventDefault();
    showMenu();
  });
});

```

So instead of reinventing the wheel over and over and solve all cross-browser issues manually, I recommend the usage of a Javascript framework.

---

### Post by Zigon on 2010-02-02
Thanks a lot for your help. I'm also having problems when using substr_replace(), in and only in IE. :mad:

---

### Post by CyberJack on 2010-02-02
Well IE is a pain in the *ss most of the time.

What do you need "substr_replace" for?  Can you show us a part of the code?
Without it, it will be very difficult to help

---

