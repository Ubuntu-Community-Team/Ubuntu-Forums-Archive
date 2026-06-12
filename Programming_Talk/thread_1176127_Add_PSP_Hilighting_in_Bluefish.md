---
title: "Add PSP Hilighting in Bluefish"
date: 2009-06-02
forum: Programming Talk
---

### Post by drewigg on 2009-06-02
Hello everyone!

I was wondering if anyone knew how to add a new language highlighting in Bluefish? I know how to edit one (using both the Preferences window and the ~/.bluefish/highlighting file), but not create a new one. I have already tried integrating it by editing the highlighting file but it appears that bluefish just ignores it. (see below)

What is PSP?
- PSP is a handler for mod_python. In other words, mod_python is a mod for Apache that allows it understand python. The PSP Handler allows for integration into an html file (but w/ a .psp extension) just like php. More info: [http://webpython.codepoint.net/mod_python_psp](http://webpython.codepoint.net/mod_python_psp) 

How would this highlight w/ Bluefish?
- PSP would require almost the exact same highlighting as php as it integrates into html just has php does just with <% %> tags instead.

What have you tried so far?
- I have already attempted adding the language highlighting support by copying the php lines in the ~/.bluefish/highlighting file and editing them appropriately for psp but when I open bluefish and attempt to language highlighting type, it does not have psp as an option.

Here is what I added to the highlighting file: (it is a hybrid between the php and python highlighting schemes)
```

patterns: psp:String (SQL Functions):0:\\b(MATCH|AGAINST|ASCII|CHAR|SOUNDEX|MAX|MIN|MD5|LCASE|UCASE|PASSWORD|ENCRYPT|RAND|LAST_INSERT_ID|COUNT|AVG|SUM|NOW|CURDATE|CURDATE|FROM_DAYS|FROM_UNIXTIME|PERIOD_ADD|PERIOD_DIFF|TO_DAYS|UNIX_TIMESTAMP|USER|WEEKDAY|CONCAT|DATE_(FORMAT|ADD|SUB))\\b\\(:\\):1:^(psp Block|String \\(double quoted\\)|String \\(single quoted\\))$:#999966::2:1:
patterns: psp:String (SQL Keywords):0:\\b(SELECT|INSERT|UPDATE|DELETE|DROP|GROUP BY|FROM|INTO|ON|AS|AND|NOT|OR|NULL|SET|VALUES|WHERE|ORDER BY|LIMIT|(LEFT|RIGHT|FULL) JOIN|ASC|DESC)\\b::2:^(psp Block|String \\(single quoted\\)|String \\(double quoted\\))$:#996699::2:1:
patterns: psp:Numbers:1:(0x)?[0-9]+(?![0-9]*[a-z\\(_\\-])::2:^psp Block$:#330099::2:1:
patterns: psp:Operators:1:[\\+\\-\\*\\/\\.<>=`!%]+(?!\\?php)::2:^psp Block$:#cc0000::2:1:
patterns: psp:Comment:1:#.*?$::2:^psp Block$:#aaaaaa::0:0:
patterns: psp:String (single quoted escape):0:\\\\.::2:^String \\(double quoted\\)$:#009900::0:0:
patterns: psp:String (single quoted):0:':':1:^psp Block$:#009900::0:0:
patterns: psp:String (double quoted escape):0:\\\\.::2:^String \\(single quoted\\)$:#009900::0:0:
patterns: psp:String (double quoted):0:":":1:^psp Block$:#009900::0:0:
patterns: psp:Braces:0:[{()}\\[\\]]::2:^psp Block$:#000000::2:0:
patterns: psp:Keywords:0:\\b(and|break|continue|del|elif|else|exec|for|from|global|if|import|in|is|not|or|pass|print|raise|return|while|yield|(assert|except|finally|try))\\b::2:^psp Block$:#ff8800::0:0:
patterns: psp:Keywords Self:1:self\\.?::2:^psp Block$:#000088::0:0:
patterns: psp:Keywords Exception:0:2::3:^Keywords$:#ff8800::2:0:
patterns: psp:Name:1:1::3:^Definition$:#ff8800::1:0:
patterns: psp:Definition:0:(class|def)[\\t ]+[a-zA-Z0-9_-]+(\\([^)]*\\))?[\\t ]*\:::2:^psp Block$:#0000aa::0:0:
patterns: psp:psp Block:1:<\\%(psp|=):\\%>:1:^(top|HTML|HTML Attribute Contents)$:#0000FF::0:0:
patterns: psp:Comment:0:<!--:-->:1::#aaaaaa::1:2:
patterns: psp:HTML Entities:1:&[^; ]*;::2::#999999::2:0:
patterns: psp:HTML DocType:1:<![a-z0-9]+:[^?-]>:1::#bb8800::1:1:
patterns: psp:HTML Attribute Contents:1:2::3:^HTML Attributes$:#cc0000::0:0:
patterns: psp:HTML Attributes:1:((?\:xml\:)?[a-z][a-z-]*=)[ \\n\\t]*((?\:"[^"]+")|(?\:'[^']+'))::2:^HTML$:#660099::0:0:
patterns: psp:<html> Tags:1:1::3:^HTML$:#000066::2:0:
patterns: psp:HTML:1:<(/?[a-z][a-z0-9]*):>:1::#0000ee::0:0:

``` 

If anybody has any suggestions please let me know.

Thanks in advance!!
drewigg

---

