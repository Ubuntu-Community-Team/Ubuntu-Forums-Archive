---
title: "Change Default Search Engine in Firefox"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by JDL Wahaha on 2012-06-24
Hi,

For some reason, firefox changes my default search engine in the search bar from google to ask.com without any notification. The drop-down triangle beside the icon doesn't given me anything except ask.com. Does anyone know how to change it back to google?

Thanks in advance.

---

### Post by Shadius on 2012-06-24
You can select "Manage Search Engines" from that same drop-down menu and select "Google". Also, you can try removing the "Ask.com" entry. If "Google" doesn't show up as a choice, then you can try adding it by selecting "Get more search engines" from the **Manage Search Engine List** dialog box. If that doesn't work try, "Restore Defaults".

---

### Post by critin on 2012-06-24
In the drop down triangle, only Ask is there?  There is a Manage Search Engines on the same page.  There also should be a 'Get more search engines' link.  What about "Restore Defaults"

Something you downloaded did that.  You might also go to View toolbars and delete ASK or it will keep coming back.

Oops--slow again, there were no replies when I began typing. lol

---

### Post by zombifier25 on 2012-06-24
ask.com usually injects inself very deep into your browser. You can follow the tutorial [here](http://www.paperstreet.com/blog/582) to remove it from about:config.

---

### Post by Shadius on 2012-06-24
You might have the Ask.com add-on. Go into your Add-ons and remove it or disable it. Whichever you prefer. You can find it by going to *Tools>Add-ons*. From there, you'll be able to choose whether to disable or remove it.

---

### Post by JDL Wahaha on 2012-06-24
Thanks for all your reply, but it didn't work. 

From Manage Search Engine, I couldn't find google in the list and ask.com IS the default one that I just restore ask.com again when I click "restore default". 

When I click "Get more search engine", it takes me to another add-on page where I still can't find google. (Found google image, but i want the web)

about:config solution doesn't seem to have any effect on the browser too and I don't have ask.com add-on installed.

Just wondering now how you can add google one of the option in the list now.

---

### Post by Shadius on 2012-06-24
> **JDL Wahaha said:**
> Thanks for all your reply, but it didn't work. 

From Manage Search Engine, I couldn't find google in the list and ask.com IS the default one that I just restore ask.com again when I click "restore default". 

When I click "Get more search engine", it takes me to another add-on page where I still can't find google. (Found google image, but i want the web)

about:config solution doesn't seem to have any effect on the browser too and I don't have ask.com add-on installed.

Just wondering now how you can add google one of the option in the list now.

You could try reinstalling Firefox. I would do that as a last resort though, but I'm out of ideas. Remember if you do reinstall Firefox, you'll lose your bookmarks and such.

---

### Post by JDL Wahaha on 2012-06-24
Ok, thanks for all your helps! I'll try re-installing firefox.

---

### Post by zombifier25 on 2012-06-24
> **Shadius said:**
> You could try reinstalling Firefox. I would do that as a last resort though, but I'm out of ideas. Remember if you do reinstall Firefox, you'll lose your bookmarks and such.

Not really. The configs will still be there.
Thankfully, Firefox 13 implemented a [s]nuke all[/s] Reset Button, which will delete all settings, addons, configs, while still keeping your bookmarks and passwords. Open about:support (or go to Help > Troubleshooting Information), click "Reset Firefox".

---

### Post by Shadius on 2012-06-24
> **zombifier25 said:**
> Not really. The configs will still be there.
Thankfully, Firefox 13 implemented a [s]nuke all[/s] Reset Button, which will delete all settings, addons, configs, while still keeping your bookmarks and passwords. Open about:support (or go to Help > Troubleshooting Information), click "Reset Firefox".

Oh, right, I forgot about that! Thanks for the correction.

---

### Post by paradoja on 2013-02-13
Did you try going to about:config, searching for keyword.URL and seeing what's there? If you go there, you will see which search engine is set, not in a special little bar, but in the navigation bar.  Then you can eliminate the little bar (sorry for my non-professional language) with the search engine and use the navigation bar the same way. You only have to change the value when you go to about:config and search keyword.URL. Then put this:

**[SIZE=2]http://www.google.com/search?ie=UTF-8&oe=utf-8&q=[/SIZE]**





Hope it's useful!

---

