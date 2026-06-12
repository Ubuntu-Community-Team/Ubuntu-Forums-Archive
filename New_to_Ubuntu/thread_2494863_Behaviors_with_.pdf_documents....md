---
title: "Behaviors with .pdf documents..."
date: 2024-01-29
forum: New to Ubuntu
---

### Post by Innernet on 2024-01-29
Hello.
Clicking to see a .pdf document on the web;  recently takes me to a save screen, only few times I can see/open its contents and later decide if I want to save.  What has changed ?  
Is there a way/setting as before to always show instead of pushing me to a save prompt ?

---

### Post by Holger_Gehrke on 2024-01-29
In what browser do you encounter this problem ? If it's Firefox, open the settings, go to 'Applications' on the 'General settings' page, find the file type 'Portable Document Format (PDF)' and select 'open in Firefox' as the action to take. 
Hopefully you are aware of the 'Content-Disposition' header which sites can send to force a download of a file - if that is what's going on, then the problem is on the server side.

Holger

---

### Post by Innernet on 2024-01-29
Thanks. 
 I use 'Brave' web browser and do not want to go back to Firefox.  :(

---

### Post by TheFu on 2024-01-30
> **Innernet said:**
> Thanks. 
 I use 'Brave' web browser and do not want to go back to Firefox.  :(

It is smart to use multiple web browsers.  Use one for daily use on trusted websites and use the other for super secure stuff like banking. Bonus points by running the super secure browser under a container or sandbox like **firejail**.

If you need to visit uglier parts of the internet, firejail has a --private mode that prevents anything on the account or disk from being seen or saved.  I use this also for banking and brokerage web logins for the extra security.

No need to limit yourself to just 1 browser.  Heck, I use 4 different browsers for different purposes.  Sometimes **lynx** is just what I need or Dillo.

---

### Post by MAFoElffen on 2024-01-30
@TheFu

Funny coincidence that you should say that... My old professor for CyberSecurity. His recommends for "Online Banking" (that he used) is that he had a separate "special use" account which all he did on that User account was his online banking. That User had no admin rights or privileges. He did not go to any other sites except that.

For surfing the net, he had another User account, that also had no admin privileges.

Not very convenient. But a secure pratice.

---

### Post by TheFu on 2024-01-30
I have a separate VM just for banking and it has the browser and firejail only installed.
Back when I was CFO for a few small companies, I followed Brian Kreb's advice on having a dedicated machine (really just a USB boot) just for online banking. In the US, business accounts don't have the same protections that consumer bank accounts get from the FDIC, so if our monthly payroll was stolen, our employees wouldn't be able to pay their mortgages and we'd miss their 401k and health care payments.  I couldn't risk that for our employees.

The risks are real: [https://krebsonsecurity.com/2022/10/report-big-u-s-banks-are-stiffing-account-takeover-victims/](https://krebsonsecurity.com/2022/10/report-big-u-s-banks-are-stiffing-account-takeover-victims/)

---

### Post by Norm24 on 2024-01-30
+1 for Firejail.

---

