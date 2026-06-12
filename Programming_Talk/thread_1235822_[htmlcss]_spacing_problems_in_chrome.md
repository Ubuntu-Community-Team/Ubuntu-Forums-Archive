---
title: "[html/css] spacing problems in chrome"
date: 2009-08-09
forum: Programming Talk
---

### Post by ELD on 2009-08-09
I currently have a problem with chrome not displaying a page properly under windows that a user emailed me about.

I have tested on my windows xp install with chrome and i do not see the error:

What he sees:
[http://i43.photobucket.com/albums/e397/clericvash/chrome-xp-sp3.gif](http://i43.photobucket.com/albums/e397/clericvash/chrome-xp-sp3.gif)

What i see:
[http://i43.photobucket.com/albums/e397/clericvash/Clipboard01-2.jpg](http://i43.photobucket.com/albums/e397/clericvash/Clipboard01-2.jpg)

Just below the logo you have the main links "home, rules" etc but on his install the line below the links is way too far down, same version of chrome and all.
[U]
Code
```

.menu_fancy
{
        width: 100%;
}
    
.menu_fancy ul
{
        margin: 0; 
    padding: 0;
        float: left;
    list-style-type: none;
}

.menu_fancy ul li
{
    text-align: center;
    float: left;
    padding: 0px 10px 3px 10px;
    margin-left: 5px;
    border-bottom: 1px solid #0099CC;
    border-top: 1px solid #FFFFFF;
    border-left: 1px solid #FFFFFF;
    border-right: 1px solid #FFFFFF;
    display: block;
}

.menu_fancy ul li a
{
    text-decoration: none;
    padding: 5px;
    display: block;
}

```[/U]

---

### Post by TheBuzzSaw on 2009-08-09
Why does one have a home button while the other doesn't? You sure they're the same version?

---

### Post by ELD on 2009-08-10
Your right it can't be the same version, he emailed me to say it is fine on his desktop so it's deffo his end, thanks.

---

