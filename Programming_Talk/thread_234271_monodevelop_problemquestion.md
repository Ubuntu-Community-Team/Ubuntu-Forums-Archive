---
title: "monodevelop problem/question"
date: 2006-08-11
forum: Programming Talk
---

### Post by papernik on 2006-08-11
Hi, i'm trying to use monodevelop 0.10 integrated IDE ( stetic ) to build a small test interface, i'm not expert, but i have a big problem.

When i drag and drop a control in the main windows, this control expand size into this windows ( a button become a big button filling all main windows for example ), and there is no way to resize or move it .

Have someone the same problem ?

How can i solve this ? 

Please Heeelppp :eek: 

Thanks Papernik

PS : Look at attachments to better understand.

---

### Post by moma on 2006-08-11
That is a correct behavior.  
The button extends to the same size as the container.

You must add layout-guides (container widgets) to your form.
HBox, VBox and Table layout are all very usefull. You can create resizable areas with HPaned and VPaned widgets.

You may also change the "Child layout" properties.

---

### Post by papernik on 2006-08-13
Ok, thank you..

I will make some experiment :)

bye

papernik

---

