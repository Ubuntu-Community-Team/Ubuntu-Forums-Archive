---
title: "[SOLVED] Selected wrong Flash, how to remove"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by MockY on 2008-04-25
When I launched a flash site for the first time, I got the option on what flash "engine" I would want to use. Usually you have Adobe's version and Gnash, but now with FF3 I had 3 options. I choose the first option (can't remember what the name was) but it is clearly not working. How do I uninstall it?

---

### Post by Theo148 on 2008-04-26
Well I'm not sure about uninstalling, but you can disable the plugin under Tools>Add-ons. :)

Edit: I think you can get rid of the plugin by deleting its .so file under 'usr/lib/firefox/plugins'. I'm not sure though, so it would be best to wait for somebody who has better knowledge of how this works than me.

---

### Post by MockY on 2008-04-26
So I thought as well, but it is not listed there.

---

### Post by InGunsWeTrust on 2008-04-26
I have the same problem and sadly, when you disable it doesn't prompt you to insstall a different plugin :(

---

### Post by spiderbatdad on 2008-04-26
For example: 

```
sudo apt-get purge swfdec-mozilla
```


```
sudo apt-get install flashplugin-nonfree
```

---

### Post by MockY on 2008-04-26
I used Synaptic and searched for Flash, and then removed every installed entry. I was now prompted again and now Adobe is installed instead. This would be the same result as you suggested **spiderbatdad**. Thank you so much.

---

### Post by alejandro.mc on 2008-04-26
Place SOLVE in this post, probably will help many new Ubuntu users..

---

### Post by MockY on 2008-04-26
> **alejandro.mc said:**
> Place SOLVE in this post, probably will help many new Ubuntu users..

Didn't know I could do that because I looked around and couldn't find anything. I still can't find where to do such.

---

