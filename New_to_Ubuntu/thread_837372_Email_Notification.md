---
title: "Email Notification"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by JohnTheMacGeek on 2008-06-22
I am wondering if there is an application that runs in the menubar that would notify me of new mail? Gmail has a great one for my Mac but nothing for Linux. Any suggestions?

Thanks, JohnTheMacGeek

---

### Post by UltraMathMan on 2008-06-22
> **JohnTheMacGeek said:**
> I am wondering if there is an application that runs in the menubar that would notify me of new mail? Gmail has a great one for my Mac but nothing for Linux. Any suggestions?

Thanks, JohnTheMacGeek

You could try gmail-notify, checkgmail, or cgmail. All are available through Synaptic Package Manager.

```
sudo apt-get install "program-name"
```

-Hope this helps :)

---

### Post by apoth on 2008-06-22
```
sudo aptitude search gmail
```

I've tried a few, most seem fine. These days I get them forwarded to my phone so I don't bother with a notify app.

---

### Post by JohnTheMacGeek on 2008-06-22
> **UltraMathMan said:**
> You could try gmail-notify, checkgmail, or cgmail. All are available through Synaptic Package Manager.

```
sudo apt-get install "program-name"
```

-Hope this helps :)It sure did, thanks! I installed gmail-notify and it works great! I have a couple questions regarding it, though.

1. How do I get it to start up when I login?

2. I don't understand the time increments. It's set to check mail every 20000 ??? I don't get it.

Again, thanks! I'm loving Ubuntu!

---

### Post by the_doc on 2008-06-22
Time increment is measured in milliseconds, so 20000 is 20 seconds.

---

### Post by UltraMathMan on 2008-06-22
You can add it to the list of programs under the "Startup Programs" tab in System -> Preferences -> Sessions

---

### Post by JohnTheMacGeek on 2008-06-22
> **UltraMathMan said:**
> You can add it to the list of programs under the "Startup Programs" tab in System -> Preferences -> SessionsHow do I add it? I see the "Add" button in the Sessions window but don't understand how to add it.

---

### Post by UltraMathMan on 2008-06-22
> **JohnTheMacGeek said:**
> How do I add it. I see the Sessions window but don't understand how to add it.

Click the Add button on the right.

For the name something like "Gmail Notify"

For the command, enter the terminal command used to start the program - probably gmail-notify.

For the comments, enter anything or nothing.

Click Ok.

---

### Post by JohnTheMacGeek on 2008-06-22
> **UltraMathMan said:**
> Click the Add button on the right.

For the name something like "Gmail Notify"

For the command, enter the terminal command used to start the program - probably gmail-notify.

For the comments, enter anything or nothing.

Click Ok.That worked flawlessly ... thanks!

---

### Post by UltraMathMan on 2008-06-22
Glad to hear it!

---

