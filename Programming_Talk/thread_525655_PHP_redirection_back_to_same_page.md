---
title: "PHP redirection back to same page"
date: 2007-08-14
forum: Programming Talk
---

### Post by LaRoza on 2007-08-14
The situation:

I want to have someone click a link, and have that link set a session variable, and then have the user go back to the same page with that variable set. 

The problem is, the page relies on $_GET[] variable in every URL. Is there a way of extracting the URL of the page and appending "&lang=es" to the end?

---

### Post by aks44 on 2007-08-14
> **LaRoza said:**
> The problem is, the page relies on $_GET[] variable in every URL. Is there a way of extracting the URL of the page and appending "&lang=es" to the end?

$_SERVER['REQUEST_URI'] ?

If this particular one doesn't fit your needs, maybe some other $_SERVER variable will.

As far as I'm concerned, whenever I had to do something similar I rebuilt the whole request from the $_GET variables (along with $_SERVER variables to get the server & script names).

Hope this helps.

EDIT: foreach ($_GET as $key => $val) may be what you're looking for if you want to rebuild the request. Just don't forget to urlencode() $key and $val.

---

### Post by LaRoza on 2007-08-14
Thanks, I just have to refine the script now.

---

