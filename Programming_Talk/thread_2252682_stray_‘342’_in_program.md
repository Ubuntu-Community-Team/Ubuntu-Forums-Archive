---
title: "stray ‘\342’ in program"
date: 2014-11-13
forum: Programming Talk
---

### Post by COKEDUDE on 2014-11-13
If you get a message similar to this it means you are using unicode character instead of standard ascii characters. 342 in particular is a unicode character called "smart quotes". 

```
hungry.c: In function &#8216;main&#8217;:
hungry.c:10:3: error: stray &#8216;\342&#8217; in program
hungry.c:10:3: error: stray &#8216;\200&#8217; in program
hungry.c:10:3: error: stray &#8216;\234&#8217; in program
hungry.c:10:28: error: expected expression before &#8216;/&#8217; token
hungry.c:10:28: error: stray &#8216;\342&#8217; in program
hungry.c:10:28: error: stray &#8216;\200&#8217; in program
hungry.c:10:28: error: stray &#8216;\235&#8217; in program
hungry.c:13:24: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217; [enabled by default]
hungry.c:19:3: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217; [enabled by default]
```

The quickest and easiest way to fix this problem is like this. 

You can use the sed command to fix these issues. 

This will give you a quick preview of what will be replaced. 

```
sed s/[&#8221;&#8220;]/'"'/g File.txt
```

This will do the replacements and put the replacement in a new file called WithoutSmartQuotes.txt. 

```
sed s/[&#8221;&#8220;]/'"'/g File.txt > WithoutSmartQuotes.txt
```

This will overwrite the original file. 

```
sed -i ".bk" s/[&#8221;&#8220;]/'"'/g File.txt
```

[http://developmentality.wordpress.com/2010/10/11/how-to-remove-smart-quotes-from-a-text-file/](http://developmentality.wordpress.com/2010/10/11/how-to-remove-smart-quotes-from-a-text-file/)

If that doesn't work try looking through the unicode table for the appropriate thing to substitute. 

[http://unicode-table.com/en/#spacing-modifier-letters](http://unicode-table.com/en/#spacing-modifier-letters)
[http://www.tamasoft.co.jp/en/general-info/unicode.html](http://www.tamasoft.co.jp/en/general-info/unicode.html)
[http://en.wikipedia.org/wiki/List_of_Unicode_characters](http://en.wikipedia.org/wiki/List_of_Unicode_characters)

Original thread : [http://ubuntuforums.org/showthread.php?t=1945999](http://ubuntuforums.org/showthread.php?t=1945999)

---

### Post by dargaud2 on 2014-11-14
Use iconv (from whatever charset you think your char is from):
```
$ chardet File.txt
File.txt: utf-8 (confidence: 0.99)
$ iconv -f UTF-8 -t ASCII//TRANSLIT File.txt >Clean.txt
```

---

### Post by ofnuts on 2014-11-14
If you have a problem like this, you are using the wrong editor (or you are copy/pasting code from a Word document which is even worse) :)

---

