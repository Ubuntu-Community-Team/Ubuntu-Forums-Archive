---
title: "html form submission"
date: 2011-05-23
forum: Programming Talk
---

### Post by zobayer1 on 2011-05-23
Hello, I am trying to create a submission page, which will submit to some other page. When I use &lt;form&gt; after submission, the page redirects to the action page I mentioned. But I want to stay on my current page as submit as well. What can I do?
Thanks in advance and if I am not clear, then please mention, I will try to explain further.

---

### Post by s.fox on 2011-05-23
Hello,

I would set the action to the current page written in a server side language. Run a test to see if the post data is available and if so  process it, otherwise display the form.

-s.fox

---

### Post by r-senior on 2011-05-23
What language are you processing the form data with on the server? Java/JSP? php? Something else?

---

### Post by zobayer1 on 2011-05-23
> 
I would set the action to the current page written in a server side  language. Run a test to see if the post data is available and if so   process it, otherwise display the form.

Thanks s.fox for your quick reply. Here is what I am trying to do actually:

Say, I have a page mydomain.com/submit.php and I am sending the data to otherdomain.com/submit.php and I have no control on otherdomain.com pages. After submission, my submit.php will load otherdomain's submit.php (well, not necessarily it is always a php file), but I want to stay in my submit.php instead of going anywhere and submit data as well.

---

### Post by zobayer1 on 2011-05-23
> **r-senior said:**
> What language are you processing the form data with on the server? Java/JSP? php? Something else?

I am not processing the data, I am sending it to an external form, probably they process it with perl.

---

### Post by r-senior on 2011-05-23
You could do that with an AJAX submit:

[http://stackoverflow.com/questions/1960240/jquery-ajax-submit-form](http://stackoverflow.com/questions/1960240/jquery-ajax-submit-form)

Your AJAX call can get the response from the other server and you can report that in your page as you wish (typically by parsing the response and then changing the body of a node in your page).

---

### Post by s.fox on 2011-05-23
I did not realise you were posting to another domain.   On that basis I agree with r-senior, ajax can help you here. :)

---

### Post by zobayer1 on 2011-05-23
Thanks s.fox and r-senior, let me try that :)
Actually, I like programming problem solving and I use to solve on various online-judges, so If I could create a page from where I can submit on all the sites according to my wish, then it would be interesting.
:)

---

### Post by SeijiSensei on 2011-05-23
You could also post the information in the background using the [CURL]("http://www.php.net/manual/en/intro.curl.php") extensions to PHP, parse the result, then display an appropriate local result page.

---

### Post by zobayer1 on 2011-06-02
> **SeijiSensei said:**
> You could also post the information in the background using the [CURL]("http://www.php.net/manual/en/intro.curl.php") extensions to PHP, parse the result, then display an appropriate local result page.

Thanks that worked for me :D

---

