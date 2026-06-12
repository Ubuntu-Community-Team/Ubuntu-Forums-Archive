---
title: "Ajax problem in Firefox"
date: 2008-09-25
forum: Programming Talk
---

### Post by suvarthi on 2008-09-25
Hi,

I have a registration from. Where there is some checkbox which loads dynamically at "onclick" event of a radio button. The checkbox loads from a different php page by ajax. The problem is the value of checkbox cannot be fetched by the parent page. The code is: 

$.post("sh_sub.php", {
id:+ selected},
 function(data){
parent: "data.parentNode",
$('div#subs').parent().append(data);
 });

Which is working in IE but not working is Firefox.

Can anyone help ?

---

### Post by henchman on 2008-09-25
Well, it always helps when posting the whole source code and not just a snippet :> are you using some kind of javascript framework here, looks strange to my eyes O_o

Try using the Error Console of Firefox for this problem (, too) -> Tools -> ErrorConsole. Clean it once to throw away the old dust and then it will tell you your problems! :)

---

