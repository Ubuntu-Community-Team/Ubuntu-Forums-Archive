---
title: "php with form submit"
date: 2007-08-11
forum: Programming Talk
---

### Post by prostock3 on 2007-08-11
Hi,

I'm uploading a file through php from a form.  Everything works, except that after clicking the submit, the browser navigates away from my html page which holds the form.  From the form, I go to the url of php file.  Is there anyway to stay on the html page after clicking the form submit?

Thanks in advance.

---

### Post by neoguy2012 on 2007-08-11
Yes, but it requires a bit of knowledge in AJAX.  I would recommend using the onSubmit function in Javascript that'll send it to a function to send your form data through one of those HTTP request thing-a-ma-bobbers.

EDIT:

Here's a link that has some code examples:

[http://www.webmasterworld.com/javascript/3136170.htm](http://www.webmasterworld.com/javascript/3136170.htm)

---

### Post by prostock3 on 2007-08-11
thanks.  looks like the guy on the link has the same issue as me.  I will try to use ajax to handle the event with some handler.

Do you know why when u click submit, the page gets redirected in the first place?

Thanks!

---

### Post by orlox on 2007-08-11
Actually, if you're submitting files its not possible to use AJAX to do that because of restrictions on the XMLHTTPRequest object that is the core of AJAX. Asynchronous file submitting requires more complex constructs than a simple AJAX request.

However, if you only submit ordinary data, (no files) you can use AJAX to do the submit without changing the current url.

---

### Post by orlox on 2007-08-11
A way in wich you could make the browser return to the page that holds your form would be to direct the action of the form to the same page that holds it, or redirecting from the php script that procceses your form to the php file that contains the form.

---

### Post by Mirrorball on 2007-08-11
I was searching for a way to do this some time ago and the only way is to submit the file to an iframe.

---

