---
title: "Emacs encoding pound sign oddity"
date: 2010-05-11
forum: Programming Talk
---

### Post by bg11 on 2010-05-11
When I insert the pound sign (£) into a file using emacs, it sometimes appears as Â£.

For example, the pound sign in the attached html file gets rendered this way by firefox.

I tried changing emacs' and firefox's character encoding to utf-8, but that didn't help.

Does anyone else get this problem?

---

### Post by ju2wheels on 2010-05-11
Use html entities where you can [http://www.w3schools.com/html/html_entities.asp](http://www.w3schools.com/html/html_entities.asp) .

&pound; is what you want.

---

### Post by bg11 on 2010-05-12
> **ju2wheels said:**
> Use html entities where you can [http://www.w3schools.com/html/html_entities.asp](http://www.w3schools.com/html/html_entities.asp) .

&pound; is what you want.

That's what I normally use for that particular case, but it's not a general fix for the problem.  For example, editing a non-html text file in emacs and later in a different editor could cause problems.

---

