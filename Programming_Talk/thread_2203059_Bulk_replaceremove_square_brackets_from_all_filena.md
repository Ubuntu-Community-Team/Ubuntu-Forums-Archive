---
title: "Bulk replace/remove square brackets from all filename in a folder"
date: 2014-02-01
forum: Programming Talk
---

### Post by shantiq on 2014-02-01
i usually use rename to do this kind of task ```
rename 's/whatever/newwhatever/g' *
```

but found it did not accept apostrophe even with backward slash  ```
rename 's/\'//g' *
```


so i googled it and found excellent



remove [apostrophe]("http://linuxconfig.org/remove-an-apostrophe-from-a-filename") from filename


```
for f in *; do mv "$f" `echo $f | sed 's/\x27//g'`; done

```


and that worked



**NOW**   and here is my question why does it not also work for square brackets []

i tried using [ASCII codes]("http://www.idautomation.com/product-support/ascii-chart-char-set.html")

```
for f in *; do mv "$f" `echo $f | sed 's/\x5b//g'`; done

```


[FONT=century gothic][SIZE=2]replacing [/SIZE][CENTER][COLOR=#000000]x27 with x5b as shown in chart[/COLOR][/CENTER]
[/FONT][CENTER]
[/CENTER]
[FONT=arial][SIZE=2]
[/SIZE][/FONT]

and no joy  .....

gives me

```
[B]for f in *; do mv "$f" `echo $f | sed 's/\x5b//g'`; done
[/B]sed: -e expression #1, char 9: Invalid regular expression
mv: missing destination file operand after &#8216;[10].mp3&#8217;
Try 'mv --help' for more information.
sed: -e expression #1, char 9: Invalid regular expression
mv: missing destination file operand after &#8216;[1].mp3&#8217;
Try 'mv --help' for more information.
sed: -e expression #1, char 9: Invalid regular expression
mv: missing destination file operand after &#8216;[2].mp3&#8217;
Try 'mv --help' for more information.
sed: -e expression #1, char 9: Invalid regular expression
mv: missing destination file operand after &#8216;[3].mp3&#8217;
Try 'mv --help' for more information.
sed: -e expression #1, char 9: Invalid regular expression
mv: missing destination file operand after &#8216;[4].mp3&#8217;
Try 'mv --help' for more information.
sed: -e expression #1, char 9: Invalid regular expression
mv: missing destination file operand after &#8216;[5].mp3&#8217;
Try 'mv --help' for more information.
sed: -e expression #1, char 9: Invalid regular expression
mv: missing destination file operand after &#8216;[6].mp3&#8217;
Try 'mv --help' for more information.
sed: -e expression #1, char 9: Invalid regular expression
mv: missing destination file operand after &#8216;[7].mp3&#8217;
Try 'mv --help' for more information.
sed: -e expression #1, char 9: Invalid regular expression
mv: missing destination file operand after &#8216;[8].mp3&#8217;
Try 'mv --help' for more information.
sed: -e expression #1, char 9: Invalid regular expression
mv: missing destination file operand after &#8216;[9].mp3&#8217;
Try 'mv --help' for more information.
sed: -e expression #1, char 9: Invalid regular expression


shan@shan:~/Music/SONNY$ **for f in *; do mv "$f" `echo $f | sed 's/x5b//g'`; done**
mv: &#8216;[10].mp3&#8217; and &#8216;[10].mp3&#8217; are the same file
mv: &#8216;[1].mp3&#8217; and &#8216;[1].mp3&#8217; are the same file
mv: &#8216;[2].mp3&#8217; and &#8216;[2].mp3&#8217; are the same file
mv: &#8216;[3].mp3&#8217; and &#8216;[3].mp3&#8217; are the same file
mv: &#8216;[4].mp3&#8217; and &#8216;[4].mp3&#8217; are the same file
mv: &#8216;[5].mp3&#8217; and &#8216;[5].mp3&#8217; are the same file
mv: &#8216;[6].mp3&#8217; and &#8216;[6].mp3&#8217; are the same file
mv: &#8216;[7].mp3&#8217; and &#8216;[7].mp3&#8217; are the same file
mv: &#8216;[8].mp3&#8217; and &#8216;[8].mp3&#8217; are the same file
mv: &#8216;[9].mp3&#8217; and &#8216;[9].mp3&#8217; are the same file



```







Any of you conversant with all this?    Another route would be cool also

---

### Post by vanadium on 2014-02-01
It works for me, unless I misunderstood the question.
```

~/test$ rename -n 's/\[/#/g' *
this[is]the[truth] renamed as this#is]the#truth]

```

[Edit]: I start to get your point: square brackets works with rename, not with sed, ' works with sed but not with rename.

For ' you can work around by using double quotes as delimiter for the search/replace. I suppose, however, that this may prevent some expressions from working because double quotes do not entirely shield the expression from bash as the single quotes do.
I cannot help debugging the sed issue, though: that's too difficult for me.
[/edit]

---

### Post by ofnuts on 2014-02-01
The trick with the apostrophe is just a way to make it invisible to the shell, but apostrophes have no special meaning in regular expressions. By contrast the square brackets do have a special meaning in the regexps, while they are ignored by the shell (unless surrounded by spaces), so what you need is way to tell the regexp parse to consider them as plain characters (the backslash escape).

---

### Post by steeldriver on 2014-02-01
You could use a character range like

```

$ rename -nv 's/[[\]]//g' *.mp3
[1].mp3 renamed as 1.mp3
```

Explanation:

- the first [ is treated as a special character marking the start of a character range
- the second [ is treated as a literal character (because it's inside a [...] range)
- the first ] needs to be escaped so that it is **not** treated as the end of the character range
- the second ] marks the end of the range enclosing literal [ and ]

---

### Post by sisco311 on 2014-02-01
> **shantiq said:**
> i usually use rename to do this kind of task ```
rename 's/whatever/newwhatever/g' *
```

but found it did not accept apostrophe even with backward slash  ```
rename 's/\'//g' *
```


Please check out [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

```
prename -n 's/'\''/xxxx/' ./*\'* 
```
There is no typo in the command name; In Ubuntu/Debian rename is the Perl based rename utility a.k.a prename.

> **shantiq said:**
> 
so i googled it and found excellent



remove [apostrophe]("http://linuxconfig.org/remove-an-apostrophe-from-a-filename") from filename


```
for f in *; do mv "$f" `echo $f | sed 's/\x27//g'`; done

```


and that worked


Google is not always your friend ;)

Let's see why this code is not so excellent and why it will fail in some cases. 

First of all you don't want to rename all the files in the directory just the ones with an apostrophe their name:
 ```
for file in *\'*; do ...
```

Secondly, filenames with leading dashes may cause problems. See BashPitfalls 003 (link in my sig)

And `` is obsolete. The preferred form of a command substitution in a POSIX shell is $() 
See BashFAQ 082 
  
Also in Bash you can use pattern substitution instead of sed:
```
file=\'\'
printf '%s\n' ${file//\'/foo}
```

> **shantiq said:**
> 
**NOW**   and here is my question why does it not also work for square brackets []

i tried using [ASCII codes]("http://www.idautomation.com/product-support/ascii-chart-char-set.html")

```
for f in *; do mv "$f" `echo $f | sed 's/\x5b//g'`; done

```


[FONT=century gothic][SIZE=2]replacing [/SIZE][CENTER][COLOR=#000000]x27 with x5b as shown in chart[/COLOR][/CENTER]
[/FONT][CENTER]
[/CENTER]
[FONT=arial][SIZE=2]
[/SIZE][/FONT]

and no joy  .....



Well, this one was already answered by ofnuts. It's because the evaluation order of the PATTERN you use in sed. In Perl it works how you would expect it:
```

[sisco@acme bar]$ > foo
[sisco@acme bar]$ > foo[bar
[sisco@acme bar]$ prename -n 's/\x5b.*/ fighters/' ./*[*
./foo[bar renamed as ./foo fighters

```


You may also want to check out:
[http://mywiki.wooledge.org/BashGuide/Patterns](http://mywiki.wooledge.org/BashGuide/Patterns)
and
[http://mywiki.wooledge.org/RegularExpression](http://mywiki.wooledge.org/RegularExpression)

---

### Post by shantiq on 2014-02-02
ok guys    first off thanx so much for all the clever replies   ....    i love our community   always helping each other


i got hung up on the sed route    since my failure with apostrophe using rename   and thought it would be easier   [i am no programmer just a guy seeking a manageable solution to a simple need]


so as Vanadium suggested rename works with square brackets i did not even think of trying it 
works for me ```
[COLOR=#000000][FONT=Ubuntu Mono]rename  's/\[/#/g' *[/FONT][/COLOR]
```  but only without [COLOR=#000000][FONT=Ubuntu Mono]-n[/FONT][/COLOR]


so to remove


```
rename 's/\[//g' * ; rename 's/\]//g' *
```    solves it!


sisko  and ofnuts thanx too but     slightly too advanced for my current understanding :]
steeldriver that line for me did not remove the brackets   but if i remove the -nv    fine then   so  ```
rename  's/[[\]]//g' *
```

thanx to all for your time on this






**SUMMARY [**tested and all good here[B]]


[/B]**remove apostrophe from filename**


```
for f in *; do mv "$f" `echo $f | sed 's/\x27//g'`; done
```

or

```
[COLOR=#000000]rename  -- s/\'//g *[/COLOR]

```
[COLOR=#000000]as does
[/COLOR][COLOR=#000000]

```
rename -v "s/'//g" *
```[/COLOR]

**remove square brackets from filename**


```
rename 's/\[//g' * ; rename 's/\]//g' *

```

or better! ```
rename  's/[[\]]//g' *
``` 




**PS**    the 54 million question is can **rename** remove an apostrophe from a filename?    there must be a way ... backslash is not enough

---

### Post by ofnuts on 2014-02-02
> **shantiq said:**
> 
**PS**    the 54 million question is can **rename** remove an apostrophe from a filename?    there must be a way ... backslash is not enough
If you enclose the substitution command in double quotes instead of single quotes then you can use single quotes freely in the command (and in file names in general):
```

>>>touch "1'2'3"
>>>ls "1'2'3"
1'2'3
>>>rename -v "s/'//g" *
1'2'3 renamed as 123

```

---

### Post by steeldriver on 2014-02-02
Apologies I should have mentioned that the -n is used to do a 'dry run' so you can check it's going to do the desired replacement

You *can* remove an escaped apostrophe with plain rename - but it requires a bit of understanding about shell expansions and why expressions are enclosed in quotes to start with. When you see a command such as

```
rename [COLOR=#0000ff]**'**[/COLOR]s/pattern/replacement/[COLOR=#0000ff]**'**[/COLOR] *
```

the single quotes are really only required to stop the shell from expanding any special characters in the string s/pattern/replacement/ - the trouble comes when pattern or replacement contain an apostrophe, in which case it is treated as the closing quote, leaving a hanging quote at the end

```

[COLOR=#0000ff]**'**[/COLOR]s/\[COLOR=#0000ff]**'**[/COLOR]//g**[COLOR=#ff0000]'[/COLOR]**

```

If neither pattern nor replacement contain any shell-special characters, then just escaping the apostrophe should work - WITHOUT quoting the expression. Taking on board sisco's warning about filenames starting with dashes, that would be

```

$ rename -nv -- s/\'//g *
funny'file renamed as funnyfile

```

Alternatively, you can quote everything up to the apostrophe, then escape it, then quote the rest of the expression

```

$ rename -nv -- [COLOR=#0000ff]**'**[/COLOR]s/[COLOR=#0000ff]**'**[/COLOR]\'[COLOR=#0000ff]**'**[/COLOR]f/!!F/g[COLOR=#0000ff]**'**[/COLOR] *
funny'file renamed as funny!!File

```

This should work in cases where using double quoting doesn't (because shell special characters are expanded inside double quotes, but not inside single quotes).

---

### Post by shantiq on 2014-02-02
```
rename  -- s/\'//g *
```ok   steeldriver this works a treat     all i had missing was the double-hyphen

as does  ```
rename -v "s/'//g" *
```  ofnuts

thanx to both of you

---

