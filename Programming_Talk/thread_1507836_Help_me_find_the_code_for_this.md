---
title: "Help me find the code for this:"
date: 2010-06-12
forum: Programming Talk
---

### Post by MadCookie on 2010-06-12
I am looking for the code for having a download section like on this website: [http://www.zune.net/en-us/products/software/download/default.htm](http://www.zune.net/en-us/products/software/download/default.htm)

Where you can select (with checkboxes) if you either want to download 64bit or 32bit version of Zune, then press download. Does anyone know where I could find that code?

PS. I know I can find the code in the sources of the website, but I am not going there...you may do that though :P

---

### Post by DanielWaterworth on 2010-06-12
This is just the simplest of javascript.

```
<script>
function set(url) {
    document.getElementById("btn").url = url;
}
function go(el) {
    document.location.href = el.url;
}
</script>
<p>64-bit: <input type="radio" name="group1" value="64-bit" onclick="set('64-bit url')"></p>
<p>32-bit: <input type="radio" name="group1" value="32-bit" onclick="set('32-bit url')"></p>
<p><input type="button" id="btn" onclick="go(this)" value='Download'></p>
```

---

### Post by sanderj on 2010-06-12
Tip @MadCookie

Use Firefox to go to that site, with your mouse select the part you want to inspect, then right-click and then View Selection Source ...

Easy, isn't it?

---

### Post by MadCookie on 2010-06-12
> **DanielWaterworth said:**
> This is just the simplest of javascript.

```
<script>
function set(url) {
    document.getElementById("btn").url = url;
}
function go(el) {
    document.location.href = el.url;
}
</script>
<p>64-bit: <input type="radio" name="group1" value="64-bit" onclick="set('64-bit url')"></p>
<p>32-bit: <input type="radio" name="group1" value="32-bit" onclick="set('32-bit url')"></p>
<p><input type="button" id="btn" onclick="go(this)" value='Download'></p>
```

EDIT: Works great, thank you!

---

