---
title: "Help needed with Firefox mixed HTTP/HTTPS pages"
date: 2019-08-03
forum: New to Ubuntu
---

### Post by c855b on 2019-08-03
Ubuntu Desktop 18.04.2 LTS, Firefox 68.0.1

I belong to forums that allow external HTTP links, such as images, within their HTTPS page. Mixed-mode pages are usually no problem with FF on other platforms, the help text says there is an "allow" process either with a warning dialog from the HTTPS lock icon; this "allow" (or whatever) button doesn't seem to exist. Alternately, there is a setting in about:config allowing mixed-mode passive content, but it accomplishes nothing under Ubuntu.

In short, I cannot get mixed-mode pages to display the HTTP content under Ubuntu/FF.

Possibly related... right-click on an HTTP image in many forum packages will have a "View Image" in the menu. This doesn't work, either, because FF changes the HTTP link in the HTML code to HTTPS. Also, these relevant about:config lines in OSX FF 68.0.1 - security.warn_viewing_mixed and security.warn_viewing_mixed.show_once - do not exist in Ubuntu FF 68.0.1.

At my wit's end, knowing just enough about this to get into trouble much less solve my issue.

TIA for any assist.

---

### Post by &amp;KyT$0P# on 2019-08-03
In FF [FONT=Courier New]about:config[/FONT] how have you set [FONT=Courier New]security.mixed_content.block_display_content[/FONT] and [FONT=Courier New]security.mixed_content.upgrade_display_content[/FONT] ?

---

### Post by c855b on 2019-08-03
block_display_content = false (the default), upgrade_display_content = true

---

### Post by &amp;KyT$0P# on 2019-08-03
> **c855b said:**
> upgrade_display_content = true

That's the culprit.  Try setting it to [FONT=Courier New]false[/FONT]

---

### Post by c855b on 2019-08-04
No joy. All the HTTP content still shows as broken links.

---

### Post by c855b on 2019-08-04
SOLVED. I reset Firefox to defaults for a fresh start. There is evidently something _I_ changed in security preferences during initial setup behind the problem. Don't know what that is just yet, but at least it's now behaving as expected. Will post if I have a definitive answer.

EDIT: It was Ghostery, in the middle changing HTTP links to HTTPS. Never seen this behavior before. Live and learn, I guess.

Sorry to have taken folks time with this, but truly appreciate the timely help, @halogen2 .

---

