---
title: "ASP syntax Highlight for BlueFish"
date: 2007-11-19
forum: Programming Talk
---

### Post by Svalde on 2007-11-19
Hey,

I have looked for a long time for a "guide" on how to make Bluefish "syntax highlight capable" with ASP, I finally found it the other day but I can't get it to work.

Link to the code: [Link]("http://article.gmane.org/gmane.comp.web.bluefish.user/152")

I have tried to add the "code" to the *highlight.default* file in the */share/bluefish* dir. but nothing happens. :confused:

I would really appreciate it if any one could help.

Thanks i advance,
Anders.

---

### Post by Svalde on 2007-11-25
Please

---

### Post by litemotiv on 2008-02-20
this reply is way overdue, but just in case someone is still looking for it:

add this to the bottom of the **~/.bluefish/highlighting** file:

```

patterns: asp:Numbers:0:\\-?([0-9]*\\.)?[0-9]+::2:^ASP Block$:#330099::2:1:
patterns: asp:Operators:1:[\\+\\-\\*\\/\\.\\\\,<>=\\(\\)_]+::2:^ASP Block$:blue::1:1:
patterns: asp:Variables:1:[a-z_][a-z0-9]*::2:^ASP Block$:#cc0000::1:0:
patterns: asp:Comment (single line):0:'.*?$::2:^ASP Block$:#7777aa::1:2:
patterns: asp:String (double quoted):0:":":1:^ASP Block$:green::1:1:
patterns: asp:String (double quote escaped):0:""::3:^String \\(double quoted\\)$:::1:1:
patterns: asp:Flow Control:1:\\b(if|and|or|then|else|elseif|case|select|while|until|wend|do|loop|for|to|step|next|end|each|in)\\b::2:^ASP Block$:#000000::2:0:
patterns: asp:Keywords:1:\\b(session|server|request|response|dim|redim|end|sub|function|set|nothing|not|true|false)\\b::2:^ASP Block$:#000000::2:0:
patterns: asp:String (SQL Functions):1:\\b(MATCH|AGAINST|ASCII|CHAR|SOUNDEX|MAX|MIN|MD5|LCASE|UCASE|PASSWORD|ENCRYPT|RAND|LAST_INSERT_ID|COUNT|AVG|SUM|NOW|CURDATE|CURDATE|FROM_DAYS|FROM_UNIXTIME|PERIOD_ADD|PERIOD_DIFF|TO_DAYS|UNIX_TIMESTAMP|USER|WEEKDAY|CONCAT|DATE_(FORMAT|ADD|SUB))\\b\\(:\\):1:^String \\(double quoted\\)$:#999966::2:1:
patterns: asp:String (SQL Keywords):1:\\b(SELECT|INSERT|UPDATE|DELETE|DROP|GROUP BY|FROM|IN|INTO|ON|AS|AND|NOT|OR|NULL|SET|VALUES|WHERE|ORDER BY|LIMIT|LEFT|RIGHT|FULL|INNER|OUTER|JOIN|ASC|DESC|AND|OR)\\b::2:^String \\(double quoted\\)$:green:yellow:2:1:
patterns: asp:ASP Block:1:<%:%>:1:^(top|HTML|HTML Attribute Contents)$:#0000FF::0:0:
patterns: asp:Comment:0:<!--:-->:1::#aaaaaa::1:2:
patterns: asp:HTML Entities:1:&[^; ]*;::2::#999999::2:0:
patterns: asp:HTML DocType:1:<![a-z0-9]+:[^?-]>:1::#bb8800::1:1:
patterns: asp:HTML Attribute Contents:1:2::3:^HTML Attributes$:#cc0000::0:0:
patterns: asp:HTML Attributes:1:((?\:xml\:)?[a-z][a-z-]*=)[ \\n\\t]*((?\:"[^"]+")|(?\:'[^']+'))::2:^HTML$:#660099::0:0:
patterns: asp:<html> Tags:1:1::3:^HTML$:#000066::2:0:
patterns: asp:HTML:1:<(/?[a-z][a-z0-9]*):>:1::#0000ee::0:0:


```

and add this line to the **~/.bluefish/rcfile_v2** file:

```

filetypes: asp:.asp:::1::0:

```

---

### Post by larsdk on 2008-02-22
I needed it - this will make the maintaining of my ASP sites so much more doable. Very, very, very appreciated :)

---

### Post by Svalde on 2008-02-26
Better late then never! :)
Thank's alot!

/Anders

---

### Post by danstever on 2008-03-19
I've got a question relating to the file... where is it?
Is it in /usr/share/bluefish?
And is it the highlighting.default?
If so, I am also assuming that when adding the content the "pattern" part is to be omitted.
Second, if the files are in this directory, I do not have the "rcfile_v2." Should I create this?

Any help to these questions would be greatly appreciated. I just recently made the switch and am trying to go completely to Ubuntu. The only thing holding me back has been the web development.

Thanks everyone!

---

### Post by Svalde on 2008-03-22
Hi,

open your home folder and find the folder called **.bluefish** if you can't see it try pressing **CTRL+H**.

Here you'll find the **highlighting** and **rcfile_v2**.

I hope this was of any use,

/Anders. :)

---

### Post by danstever on 2008-03-24
Hey thanks Svlade! That's exactly what I needed to know! AND, I finally realized what "./" means!

---

### Post by MiniMe on 2008-05-09
Sweet! I've been looking for something like this for ages.

---

### Post by run4flat on 2008-07-22
This is great!  Works perfectly!  Why can't I issue a thanks for this?  Seriously ubuntuforums, litemotiv deserves it!

---

### Post by nanotube on 2008-07-22
> **run4flat said:**
> This is great!  Works perfectly!  Why can't I issue a thanks for this?  Seriously ubuntuforums, litemotiv deserves it!

the "thanks" feature was only implemented a few months ago - and i suppose it doesn't work on any posts made prior to that.

---

