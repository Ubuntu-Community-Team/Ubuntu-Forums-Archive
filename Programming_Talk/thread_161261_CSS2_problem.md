---
title: "CSS2 problem"
date: 2006-04-16
forum: Programming Talk
---

### Post by Ferio on 2006-04-16
Hi, I've just made my personal blog @ [http://www.tecniferio.com]("http://www.tecniferio.com") using XHTML 1.1 + CSS2. I'm no designer, but I've got just a slight idea; when I use Ctrl++ in Firefox to make letters bigger, the structure of the site breaks up, and I don't know how to fix it. My CSS file is attached as a text file, just in case it's needed. I know it could be better, but I still haven't got the time to look at the hierarchy thing and so...

Any help will be useful, thanks!

---

### Post by Littleweseth on 2006-04-17
After a cursory glance, it appears your problem is this;

#content
{
        background-color: #A1A3A1;
        border: 1px solid #000505;
        color: #000505;
        float: left;
        font-size: 1.2em;
        line-height: 1.4em;
        padding: 1.4em;
        width: 570px;
}

You've defined padding in ems. The box model works by defining the initial width of your content block to the [width] you specify, *then* adds padding on top of that. Since when you resize the base text size you're essentially changing the size of an em, this leads to your content block growing.

Cheers;
-lws

---

### Post by Ferio on 2006-04-17
Wow, you're completely right! Now my problem is solved, I must do my homework for the next time. Thank you very much!

---

