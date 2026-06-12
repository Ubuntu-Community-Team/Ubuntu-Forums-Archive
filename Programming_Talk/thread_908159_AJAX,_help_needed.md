---
title: "AJAX, help needed"
date: 2008-09-02
forum: Programming Talk
---

### Post by suvarthi on 2008-09-02
Hi,

I'm totally new in JQuery and ajax. 

I've loaded a php page inside another by ajax. Here is the code snippet. 

function GetList(){
$.ajax({
   type: "GET",
   url: "list_main.php",
   data: "",
   success: function(msg){
   document.getElementById("List").innerHTML = "" + msg;
   }
 });
}
Now I try to load another page inside the ajax loaded page list_main.php. But whenever I want to load the function in the onload event in list_main.php it triggers "object expected" error message. 

So the problem is to load a page or load a function inside an ajax loaded page.

Please suggest.

---

### Post by rogeriopvl on 2008-09-02
It seems that you are complicating the code too much. Could you explain what kind of web app/site your trying to make?

---

### Post by suvarthi on 2008-09-02
Hi rogeriopvl,

Thanks for your reply.

It will display search results. Suppose the results will fetch from the file results.php which will load in parent.php through ajax. And in results.php there is some small portion which will be fetched from other pages through ajax.

Sorry to make it complex, but I think I can make you understand.

Thanks in advance.

---

