---
title: "Syntax highlight source files inside browser"
date: 2007-05-15
forum: Programming Talk
---

### Post by st14n on 2007-05-15
When I browse the web I often stumble upon source files that is presented as plain text instead of being pretty formatted inside a HTML-page. (An example of such a file (Python): [http://matplotlib.sourceforge.net/screenshots/hstdemo.py]("http://matplotlib.sourceforge.net/screenshots/hstdemo.py").) I would really like the code to be syntax highlighted. One option of course is to copy/paste the text into my favorite editor, but that is rather cumbersome. Does anybody know a method to achieve such functionality *inside* Firefox, for instance using an extension? I'm surprised that I haven't found any by searching around. It should support several languages like C, Python, Shell etc..

---

### Post by kidders on 2007-05-16
Hi there,

You *could* consider using PHP to do it ... in which case it would work in all browsers, rather than just Firefox. Having said that, it does seem odd that there isn't an extension that will do the job for you.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by LaRoza on 2007-05-16
It would be difficult for the browser to do it as (X)HTML is now.

If there was a markup language, call it CodeML, for example, and you could embed it in the XHTML with a different namespace, it would be very practicle, as in:

<pCode xmlns="www.CodeML.org">

<lanuguage type="python">
print "I would be parsed and styled by the browser with syntax highlighting"
</language>

</pCode>

I wonder if there is such a language already, with its DTD already written out.

An extension would probably have to be used to style this, but at least it would fit in the markup.

---

### Post by harun on 2007-05-16
I have used enscript to format code I have into HTML with color coding.

[http://www.codento.com/people/mtr/genscript/enscript.man.html](http://www.codento.com/people/mtr/genscript/enscript.man.html)

You will have to tell it to create HTML. Something like:

```

enscript --color --language=html -Eruby --output=dest.html file.rb

```

Don't know how you would incorporate that easily in to Firefox though.

---

