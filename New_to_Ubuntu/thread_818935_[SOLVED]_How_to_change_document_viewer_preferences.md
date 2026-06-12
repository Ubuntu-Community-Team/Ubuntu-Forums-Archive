---
title: "[SOLVED] How to change document viewer preferences?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-06-04
Need to look at a PDF link on a website, so I click on it (in Ubuntu 8.04 Hardy) and I get a window which says

"...you have chosen to open  (filename) which is a: PDF document from (website) What should Firefox do with this file?"

And I select "open with document viewer (default)".

But then a window pops open and says "Download Error  (file name) could not be opened, because the associated helper application does not exist.  Change the association in your preferences."

On my System > Preferences menu the only thing that comes close is "Preferred Applications" but this choice has no place to set anything like a file association.  Where should I be looking?

Thanks in advance.

---

### Post by wdaniels on 2008-06-04
This error message comes from firefox, so that's where you need to change it (Edit->Preferences->Applications). Seemingly your firefox is set to use some application that is not installed to open pdf files. To change file associations in Ubuntu you can right-click a pdf file, select properties, and the "Open With" tab. By default, I think Ubuntu uses a program called evince for pdf files, so if it's not installed do:

```
sudo apt-get install evince
```

(or you can always install the Adobe reader, but I don't recommend it)

---

### Post by raymondvillain on 2008-06-04
I found Evince.  Thanks very much.  But I can't get past the selection process for setting preferences in Firefox.

If I go to Edit > preferences > PDF document > use other...

I get a window in which I need to select a file, an executable file, I think.  I've located the Evence folder (/usr/include/evince-2.20) but I'm clueless about where to go from there.

Any suggestions?

Never Mind!  Just figured it out.  The Evince executable is in /usr/bin and I already have it working.  But thanks again for your great suggestions.

---

### Post by Maestro23 on 2008-06-04
The path you want in that window is:

> /usr/bin/evince

Just select that path and hit close.

Should be like screenshot below.

---

