---
title: "gedit for ruby on rails"
date: 2007-10-06
forum: Programming Talk
---

### Post by codeking on 2007-10-06
After trying several IDE's such as JEdit, I realized that I was really comfortable with GEdit.  The only problem was it didn't highlight ruby syntax in .rhtml files.  I found some instructions at [http://grigio.org/textmate_gedit_few_steps](http://grigio.org/textmate_gedit_few_steps) , and I downloaded x-rhtml.xml and rhtml.lang and moved them to the appropriate places.  But it still doesn't highlight the syntax.  What am I doing wrong?

---

### Post by Wolki on 2007-10-06
> **codeking said:**
> After trying several IDE's such as JEdit, I realized that I was really comfortable with GEdit.  The only problem was it didn't highlight ruby syntax in .rhtml files.  I found some instructions at [http://grigio.org/textmate_gedit_few_steps](http://grigio.org/textmate_gedit_few_steps) , and I downloaded x-rhtml.xml and rhtml.lang and moved them to the appropriate places.  But it still doesn't highlight the syntax.  What am I doing wrong?

Taking a look at that guide from google cache (site refuses connection :-/ ) it looks like the mime cache doesn't get updated. If you right-click->properties a rhtml file in nautilus and it doesn't tell you it's mime type as x-rhtml, try running "sudo update-mime-database /usr/share/mime/".

---

### Post by codeking on 2007-10-06
i did that, it still says the mime type was text/html.  I double-checked that x-rhtml.lang was in /usr/share/mime/packages/, and it was.  Any ideas?

---

### Post by Wolki on 2007-10-06
Can you set the rhtml highlighting manually in gedit?

---

### Post by codeking on 2007-10-07
I go into preferences and there is rhtml as a highlight mode, and it should be highlighting stuff fine, which it does with HTML, but Ruby is still not highlighted.

---

### Post by codeking on 2007-10-07
I can get it to work if I select the highlighting mode is rhtml manually.  Anyway to get it to work automatically?

Also, I don't like the syntax highlighting scheme in gedit.  Any way to get it like dreamweavers?

---

### Post by aflax on 2007-11-22
I was having the same problem.  Here is how I fixed it:

```
gksudo gedit /usr/share/gtksourceview-2.0/language-specs/rhtml.lang
```

then change the 3rd line to this:
```

<language _name="rhtml" version="1.0" _section="Markup" mimetypes="text/x-eruby;text/x-rhtml">

```

---

### Post by sweetperceptions on 2008-02-26
Hi Everyone, I had the same problem, up until I found this: [http://snakesgemscoffee.blogspot.com/2007/04/registering-rails-file-extensions-in.html](http://snakesgemscoffee.blogspot.com/2007/04/registering-rails-file-extensions-in.html)

and it finally worked! :)

---

### Post by firecrow8 on 2008-03-27
I've been able to edit my highlighting, I'm not a rails programming but I've posted how the .lang xml in combination with the style selected in gedit come together here:
[http://ubuntuforums.org/showthread.php?t=736843]("http://ubuntuforums.org/showthread.php?t=736843")

hope that works.

---

