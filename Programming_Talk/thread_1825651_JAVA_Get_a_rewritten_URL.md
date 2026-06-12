---
title: "JAVA? Get a rewritten URL"
date: 2011-08-15
forum: Programming Talk
---

### Post by CrusaderAD on 2011-08-15
Does anyone know how to retrieve a rewritten URL. Something like this:

#1 [http://www.mysite.com/page?id=77](http://www.mysite.com/page?id=77)
Rewritten to:
#2 [http://www.mysite.com/a/77](http://www.mysite.com/a/77)

I need to retrieve #2. Any ideas? I was thinking the only way was Java since I need to get it after it's been rewritten.

---

### Post by myrtle1908 on 2011-08-15
When/where you do wish to do this?  If on the client, then you can use JavaScript to obtain the current location via *document.location*.

You need to provide more information as to what you are trying to do.

---

### Post by CrusaderAD on 2011-08-16
Thanks for the reply. I just need to retrieve the URL after the page has loaded and the rewrite has been applied. document.location does not retrieve the rewritten URL.

---

### Post by slavik on 2011-08-16
you mean after mod_rewrite in apache http server does it's thing?

I don't think you can get that. I am pretty sure the original goes into the log, as well.

EDIT: Where is Java coming in to play? Seems some info is missing.

---

### Post by CrusaderAD on 2011-08-16
> **slavik said:**
> you mean after mod_rewrite in apache http server does it's thing?

I don't think you can get that. I am pretty sure the original goes into the log, as well.

EDIT: Where is Java coming in to play? Seems some info is missing.

Yep. after the rewrite. Bummer. I just thought Java cause it's client side code. If anyone any any other suggestions, I'm open to them.

---

### Post by Zugzwang on 2011-08-16
> **CerealCypher said:**
> Yep. after the rewrite. Bummer. I just thought Java cause it's client side code. If anyone any any other suggestions, I'm open to them.

Ah, is it possible that you are meaning JavaScript instead of Java? Otherwise, as slavik noted, your question would be quite confusing.

---

### Post by CrusaderAD on 2011-08-16
> **Zugzwang said:**
> Ah, is it possible that you are meaning JavaScript instead of Java? Otherwise, as slavik noted, your question would be quite confusing.

Whoops, you're right... sorry. I meant Javascript.

---

### Post by unknownPoster on 2011-08-16
Looks like this is REST to me. :P

If you run some simple PHP on the server it can tell you the URL it was given.

More specifically something like:

```

$url = $_SERVER['REQUEST_URI'];

```

---

