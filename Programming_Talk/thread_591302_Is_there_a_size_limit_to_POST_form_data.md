---
title: "Is there a size limit to POST form data?"
date: 2007-10-25
forum: Programming Talk
---

### Post by Sporkman on 2007-10-25
Is there a size limit to POST for data, say entered into a single textarea?

Is the limit imposed by the HTML protocal spec, the browser, Apache, or what?

---

### Post by pmasiar on 2007-10-25
I hope someone has a link proving it, but IMHO there is no limit on POST data. IIRC you can set limits on uploaded files, if you want to, but there is no 2K limit like on GET.

---

### Post by LaRoza on 2007-10-25
As for proof, I cannot find any links with hard evidence. It seems to be browser based, and based on the server's configuration. I don't think (theoretically) there is a limit.

For IE: [http://support.microsoft.com/default.aspx?scid=kb;EN-US;q208427](http://support.microsoft.com/default.aspx?scid=kb;EN-US;q208427)

HTTP 1.1 places no limit on the size, it seems to be up to the browsers: [http://www.faqs.org/rfcs/rfc2068.html](http://www.faqs.org/rfcs/rfc2068.html), short answer: [http://classicasp.aspfaq.com/forms/what-is-the-limit-on-querystring/get/url-parameters.html](http://classicasp.aspfaq.com/forms/what-is-the-limit-on-querystring/get/url-parameters.html)

---

### Post by Sporkman on 2007-10-25
> **LaRoza said:**
> ...and based on the server's configuration.

Is that adjustable in the standard Ubuntu LAMP server setup?

I'm writing an online app that I'll run on my own server which requires potentially large text input...

---

### Post by Sporkman on 2007-10-25
> **LaRoza said:**
> For IE: [http://support.microsoft.com/default.aspx?scid=kb;EN-US;q208427](http://support.microsoft.com/default.aspx?scid=kb;EN-US;q208427)


BTW that specifies max URL size, not max POST data size...

---

### Post by LaRoza on 2007-10-25
> **Sporkman said:**
> BTW that specifies max URL size, not max POST data size...

> 
Microsoft Internet Explorer has a maximum uniform resource locator (URL) length of 2,083 characters._ **Internet Explorer also has a maximum path length of 2,048 characters. This limit applies to both POST request and GET request URLs**_.


(Emphasis mine)

---

### Post by Sporkman on 2007-10-25
> **LaRoza said:**
> (Emphasis mine)

Right... path length on URLs. POST data doesn't reside in the URL (it's the GET data that resides in the URL).

---

### Post by LaRoza on 2007-10-25
> **Sporkman said:**
> Right... path length on URLs. POST data doesn't reside in the URL (it's the GET data that resides in the URL).

Internet Explorer also has a maximum path length of 2,048 characters. This limit applies to both **POST request** and **GET request URLs**.

The URL is only for the "GET". The POST data is not in the URL, it is in the header. 

Read it this way: This limit applies to both **POST requests** and **GET requests**.

In other words, IE limits both with the same limit. Yes, you can change the amount the server will accept. It is in an .ini file I think.

---

### Post by Sporkman on 2007-10-25
> **LaRoza said:**
> Yes, you can change the amount the server will accept. It is in an .ini file I think.

Thanks, I'll look around for it...

---

### Post by pmasiar on 2007-10-25
I did some testing of this some time ago, Firefox does not have this limit, with FF lenght of URL for GET can go up to IIRC 20K or 60K characters (which IE cannot process correctly), and I needed workaround for it.

---

### Post by LaRoza on 2007-10-25
> **Sporkman said:**
> Thanks, I'll look around for it...

[http://www.radinks.com/upload/config.php](http://www.radinks.com/upload/config.php)

(I am not pullings these links from memory, I am getting really efficient with google...)

---

