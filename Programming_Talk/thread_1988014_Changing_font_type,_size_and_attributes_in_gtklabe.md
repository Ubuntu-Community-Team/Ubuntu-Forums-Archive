---
title: "Changing font type, size and attributes in gtklabel"
date: 2012-05-26
forum: Programming Talk
---

### Post by anewguy on 2012-05-26
Having set up a font selection area as I need (the font selection that GTK provides doesn't fit well with what I'm doing), I now want to show a sample text of the font and its attributes.  So, if someone selected Arial, checked bold and/or italic and set the size to 12, how do I modify the text in a gtklabel to reflect that?  I've seen somethings involving Pango to do this, but I honestly don't understand them.

Any help is greatly appreciated!

Thanks in advance!

dave ;)

---

### Post by anewguy on 2012-05-27
Given:
```
     panel_font_sample = gtk_label_new("Font Test");
     gtk_label_set_max_width_chars(panel_font_sample, 9);
     gtk_label_set_justify(panel_font_sample,GTK_JUSTIFY_LEFT);
     sprintf(wrkpangofont,"%s, %d",wrkstr[0],10);
printf("built font string: %s\n",wrkpangofont);
     gtk_widget_override_font (panel_font_sample,pango_font_description_from_string (wrkpangofont));

```
Where:
     wrkstr[0] is loaded with a pango font name
     the printf shows "Andale Mono, 10"

I get a segment fault at the override_font.  According the the docs, I was to use this in place of gtk_widget_modify_font.  I have tried placing the literal quoted string "Andale Mono, 10" in place of the string variable wrkpangofont but still get the segment fault.  I also tried gtk_widget_modify_font and get the same segment fault.

Don't know if that helps anyone who may be trying to help or not.


dave ;)

All I'm trying to do is programmatically set the font on a gtk_label.

---

### Post by anewguy on 2012-05-27
Apparently I had some syntax error somewhere, as I just re-typed the statement and it works.

---

