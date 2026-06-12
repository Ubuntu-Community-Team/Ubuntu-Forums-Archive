---
title: "A css questions..."
date: 2009-03-06
forum: Programming Talk
---

### Post by hockey97 on 2009-03-06
Post closed!!!!!!!!

---

### Post by Can+~ on 2009-03-06
I see some excessive indentation.

CSS:```

.tabs {
    text-align:right;
    margin-top:20px;
}

.tabs ul {
    list-style:none;
    margin:0;
    padding:0;
}
.tabs ul li {
    display:inline;
    float:right;
    /*this is image background for tabs */background:url(http://www.xxx.com/images/tab_inactive.jpg) top left repeat-x;
    height:53px;
}
.tabs ul li.current { background-image:url(http://www.xxx.com/images/tab_active.jpg); }

.tabs ul li a {
    height:50px;
    padding:19px 30px 0;
    display:inline-block;
    text-decoration:none;
    text-transform:uppercase;
    color:#6d96cd;
    font-size:1.5em;
}
.tabs ul li a.color2 {
    color:#00CC66;
}

```Second: "http://www.xxx.com/images/tab_active.jpg"

You don't ever, EVER link with the full url

Third: omg is this a phishing website?

---

### Post by drubin on 2009-03-06
> **Can+~ said:**
> I see some excessive indentation.

Second: "http://www.xxx.com/images/tab_active.jpg"

You don't ever, EVER link with the full url

Third: omg is this a phishing website?

2) you might want to explain the reasoning for not doing that. It means this ccs/scripts are porable if you choose to move hosts/domains/folders nothing will work

3) Doesn't look like it to me. :s

---

### Post by hockey97 on 2009-03-06
Post closed!!!!!

---

### Post by Can+~ on 2009-03-06
CSS:```

.tabs {
    **text-align:right;**
    margin-top:20px;
}

.tabs ul {
    list-style:none;
    margin:0;
    padding:0;
}
.tabs ul li {
    display:inline;
    **float:right;**
    /*this is image background for tabs */background:url(http://www.xxx.com/images/tab_inactive.jpg) top left repeat-x;
    height:53px;
}
.tabs ul li.current { background-image:url(http://www.xxx.com/images/tab_active.jpg); }

.tabs ul li a {
    height:50px;
    padding:19px 30px 0;
    display:inline-block;
    text-decoration:none;
    text-transform:uppercase;
    color:#6d96cd;
    font-size:1.5em;
}
.tabs ul li a.color2 {
    color:#00CC66;
}

```Left in both and it should snap to the left. Use padding-right or padding-left to adjust it.

And add a background to the whole div.

---

### Post by hockey97 on 2009-03-06
Post closed!!!!!!

---

### Post by hockey97 on 2009-03-07
Post closed!!!!!

---

