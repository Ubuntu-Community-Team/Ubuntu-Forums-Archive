---
title: "How do I redirect in PHP"
date: 2008-07-08
forum: Programming Talk
---

### Post by thenetduck on 2008-07-08
Hi 
I have a little php app I am making that is structured like this.It has three or four parts. 

GUI
Control that talks to classes
Classes that talk to database

When information gets posted to the control.php I use a switch/case to handle the information and it calless classes to do different tasks. After a task is done, I would like to redirect to a specific page but I don't know how to do that because php requires me to user the header("location:stuff.php"); at the top of the page. How can I do this? 

Thanks!
The Net Duck

---

### Post by cpetercarter on 2008-07-08
header("location: stuff.php") does not have to be the first line of your php script. It has to be the first output sent to the browser. If it isn't the first output to the browser, you get a "headers already sent" error. And, obviously, you need to be careful about blank lines etc sending "hidden" output which you did not intend. Provided you are meticulous about this, you can do a load of php before sending the headers.

---

### Post by MasterProg on 2008-07-08
You can also use output buffering. Call *ob_start* to turn buffering on. After that you can call *header* function everywhere you want, even after some output. But don't forget to call *ob_end_flush* before the script finishes.

The other method is to use HTML instead. Something like *<meta http-equiv="refresh" content="0;url=stuff.php">*.

---

