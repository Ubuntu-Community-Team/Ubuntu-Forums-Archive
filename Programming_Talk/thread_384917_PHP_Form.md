---
title: "PHP Form"
date: 2007-03-15
forum: Programming Talk
---

### Post by amitroy5 on 2007-03-15
I have an HTML form that uses the get method to submit data located at [www.mydomain.com/form.php](www.mydomain.com/form.php). It does this by taking in all variables and sorting them behind the URL. My form currently submits to:

[www.otherdomain.com/submit.php?name=John&email=john@yahoo.com&formpassword=someone88](www.otherdomain.com/submit.php?name=John&email=john@yahoo.com&formpassword=someone88)

How can I let the data submit, but redirect to another page. Also, I do not want the user to be able to see the "formpassword" variable or any of the variables when the data is submitted to prevent abuse (formpassword is a constant variable not controlled by the visitor).

Finally, I want to be able to redirect my visits to [www.mydomian.com/submitted.php](www.mydomian.com/submitted.php) when they are done.

I was wondering if there is any PHP solution to this without requiring me to have access to the script located at [www.otherdomain.com](www.otherdomain.com). Thanks!

---

### Post by Mirrorball on 2007-03-15
Set the form to submit data to [www.mydomain.com/submitted.php](www.mydomain.com/submitted.php) and submit the data to [www.otherdomain.com](www.otherdomain.com) yourself in your PHP script.

---

### Post by Colonel Kilkenny on 2007-03-15
And use POST instead of GET in your form so that variables aren't shown in URL.

---

