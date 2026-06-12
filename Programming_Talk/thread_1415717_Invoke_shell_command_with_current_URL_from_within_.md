---
title: "Invoke shell command with current URL from within firefox"
date: 2010-02-25
forum: Programming Talk
---

### Post by conehead77 on 2010-02-25
Hi,

i have a shell script which takes a URL as parameter. I want to obtain the current URL from my browser and then execute the script with it.

Ideally i could just right click and select "run my script" from firefox' context menu (just like "send link" in the context menu).

Any hints on how to do that? Do i need to write a firefox extension?

EDIT: If someone is interested how i solved it, here is the firefox extension i installed: [External Application Buttons]("https://addons.mozilla.org/en-US/firefox/addon/12892"). The address bar can be given as a parameter to the external application.

---

### Post by Bynack on 2010-05-09
Hello

Wondering how to were able to use the current firefox url in your shell script? I need to do this in one for my scripts but can't work out how to do it. Any help would be great

Cheers

---

### Post by conehead77 on 2010-05-09
> **Bynack said:**
> Hello

Wondering how to were able to use the current firefox url in your shell script? I need to do this in one for my scripts but can't work out how to do it. Any help would be great

Cheers

Actually i don't use a script but a compiled executable. Then i pass the current url as command line parameter (this should be easy with bash too). 

To pass the url, right click on the button in the firefox toolbar which you made with the extension and select "properties". 
There is a section "Optional Settings" where you select "%addressbar%" from the drop down menu. When you now click the button, the content from the address bar is passed to the executable as a parameter.

---

