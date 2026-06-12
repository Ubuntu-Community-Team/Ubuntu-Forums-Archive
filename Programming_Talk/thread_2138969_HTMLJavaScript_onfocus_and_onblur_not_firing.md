---
title: "HTML/JavaScript onfocus and onblur not firing"
date: 2013-04-25
forum: Programming Talk
---

### Post by wolfgentleman on 2013-04-25
I am trying to get the textboxes to clear on focus and if they are empty on unfocus they revert to the default values. However neither onfocus nor onblur is firing. I have a jsfiddle with the code [here]("http://jsfiddle.net/wolfgentleman/gTnSj/"). Any help is appreciated.

---

### Post by wolfgentleman on 2013-04-27
bump

---

### Post by epicoder on 2013-04-29
Your focus event is not firing. However, your unfocus is. I'm not quite sure of the reason why, but you could probably save yourself some trouble by using the placeholder attribute. [http://html5doctor.com/html5-forms-introduction-and-new-attributes/#placeholder](http://html5doctor.com/html5-forms-introduction-and-new-attributes/#placeholder)
Also, consider using the addEventListener way of doing this, as the attributes are discouraged:
```

document.getElementById('ip1').addEventListener("focus", function () {
    ...
}, false);

```

---

### Post by wolfgentleman on 2013-04-29
I could not get the onblur event to fire, I don't know what you are doing different... I tried the .addEventListener first, it didn't work. Then I used the placeholder attribute and it did work nicer than what I was trying to do. So thank you for your help.

BTW: if it makes any difference I am using Firefox, I don't know why that would be preventing the onblur to fire but whatever...

---

