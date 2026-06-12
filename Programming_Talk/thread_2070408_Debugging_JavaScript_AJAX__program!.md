---
title: "Debugging JavaScript AJAX  program!"
date: 2012-10-12
forum: Programming Talk
---

### Post by TheodoreP on 2012-10-12
I am currently taking an online course for AJAX and I'm having a little trouble debugging the recent lessons assignment. It is basically an html page that has 11 buttons and they are supposed to start as disabled buttons except for the part 1 button. After you click the part 1 button is should be disabled by the javascript and the next button in the line should activate and so  on. If you would like to see it in action please visit: [http://www.sociablecooking.com/ajaxStory/AjaxStory.html](http://www.sociablecooking.com/ajaxStory/AjaxStory.html)

Please let me know in a reply to this thread if you would like for me to copy and paste the source code for the page.

---

### Post by mevun on 2012-10-12
It's kind of a pain, but one way to help debug is to use "window.alert()" calls to see what Javascript is being invoked.  This is equivalent to debugging with PRINT statements in other languages.

The other way is to use a debugger with your browser.  Firefox requires an add-on.  I think the Chrome browser has one built-in.  This would be equivalent to using **gdb** with a **C** program.

---

