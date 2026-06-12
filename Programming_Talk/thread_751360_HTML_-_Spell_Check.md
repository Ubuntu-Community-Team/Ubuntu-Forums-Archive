---
title: "HTML - Spell Check"
date: 2008-04-10
forum: Programming Talk
---

### Post by stooshbunutu on 2008-04-10
Hi,

I am looking for a piece of software that can spell check my web-pages.

I am no after the tags and attributes being checked, but my spelling is terrible and so I would like something that would check the displayed text, or limit to within the <a> tags (all my text is contained within these)

I will be grateful of anyone who can recommend me something.

Regards, stooshbunutu.

---

### Post by alexforcefive on 2008-04-10
Can't you just use the spellchecker on your text editor?

---

### Post by stooshbunutu on 2008-04-10
i have been but it is constantly questioning aspects o the script (<br> href= and such)

so it takes ages and i sometimes get so caught up clicking ignore on these bits that I miss a real error when it appears

---

### Post by stooshbunutu on 2008-04-16
anyone please?

---

### Post by Zugzwang on 2008-04-16
Now here's a lame solution: Display the page in firefox, copy&paste it to your favourite text editor and use the spell checker there. Correct any mistakes in the original HTML source.

This is is not a solution to your problem, just a workaround which unfortunately is not very good. Just in case you don't get better answers....

---

### Post by ghostdog74 on 2008-04-16
```

awk '{gsub("<[^>]*>", "")if ( $0 ) print $0 }' file | ispell

```

---

### Post by OffAxis on 2008-04-16
what text editor are you using?
One that recognizes syntax (html, php, etc) shouldn't be flagging your tags. kate (one of several quality text editors out there) also has a dictionary that you can add words to so it'll stop flagging them.

[http://kate-editor.org/](http://kate-editor.org/)

---

### Post by stooshbunutu on 2008-04-16
> **OffAxis said:**
> what text editor are you using?
One that recognizes syntax (html, php, etc) shouldn't be flagging your tags. kate (one of several quality text editors out there) also has a dictionary that you can add words to so it'll stop flagging them.

[http://kate-editor.org/](http://kate-editor.org/)

At the moment I am using the basic text editor from the applications menu (gedit) which is fairly nice as it colours certain parts of the text accordingly so I know if I have missed out a space or a ", I can add words to the dictionary but some of them are so similar to words I often miss-spell that I don't want to add them as it wouldn't flag my genuine spelling mistakes. Also as I use the english dictionary on what I type but then american for things such as html then I have to have both languages supported in one dictionary (eg. my favourite colour is red. color="FF0000")

---

### Post by stooshbunutu on 2008-04-16
> **Zugzwang said:**
> Now here's a lame solution: Display the page in firefox, copy&paste it to your favourite text editor and use the spell checker there. Correct any mistakes in the original HTML source.

This is is not a solution to your problem, just a workaround which unfortunately is not very good. Just in case you don't get better answers....

Cheers for that, nice idea for a work around

---

