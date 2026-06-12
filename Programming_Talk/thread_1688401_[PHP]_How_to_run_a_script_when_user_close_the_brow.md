---
title: "[PHP] How to run a script when user close the browser"
date: 2011-02-15
forum: Programming Talk
---

### Post by The_Aegidius on 2011-02-15
Is it possible to run a PHP script when user close the browser?

I need to change a falg in the db that indicate the user has no longer logged in the system.

---

### Post by epicoder on 2011-02-15
I've heard that the body element attribute "onbeforeunload" can be used to detect when the window is about to close. You could use ajax to cause a php script to be executed with this attribute. For example:
[HTML]<html><head>
<script type="text/javascript">
function logout() {
 var xmlhttp=new XMLHttpRequest();
 xmlhttp.open("GET", "logout.php", true);
 xmlhttp.send();
}
</script></head>
<body onbeforeunload="logout()">
Your page here
</body></html>[/HTML]

I don't know if this actually works, because I don't have the time atm to test it. Good luck.

---

### Post by The_Aegidius on 2011-02-15
Thanks. I'll try and I'll let you know.

---

### Post by The_Aegidius on 2011-02-16
I tried it and it doesn't work because the function run even when you change page of the same site.

---

### Post by Ferrat on 2011-02-16
if you make a script to start the web-browser then it could keep track of the PID and when the pid closes down you just runt the remainder of the script?

---

### Post by Zugzwang on 2011-02-16
> **The_Aegidius said:**
> Is it possible to run a PHP script when user close the browser?

I need to change a falg in the db that indicate the user has no longer logged in the system.

Technically, what you want to do cannot be done reliably - the user could force-quit his/her browser. Then, no script of any kind can be executed when this happens.

The common way to circumvent this problem is to time-out a session after a few minutes and have some JavaScript on your page that fetches data from the server every minute or so, which triggers a PHP script that resets the time-out timer.

---

