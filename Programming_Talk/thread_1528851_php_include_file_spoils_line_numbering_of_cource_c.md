---
title: "php include file spoils line numbering of cource code"
date: 2010-07-11
forum: Programming Talk
---

### Post by yc2 on 2010-07-11
Hello guys,

Thanks for all good advice in the past.

I have some texts on php-webpages. Some material is repeated and I want to use php:
```
include 'filename';
```

However, I fear this will spoil the linenumbering of the pages. If I later, for example, get problems in JavaScript the errormessages will not give the same linenumber as the editor/sourcecode.

The linenumber in the JavaScript errormessage will inculde the php-include-file. But when I will look for the linenumber giving the error, the editor linenumbering will not include the php-includefile.

It will therefore be difficult to f.ex. debug JavaScript.

Is there any way to use includefiles for php without spoiling the linenumbering of the sourcecode?

Thanks

ycc

---

### Post by new_tolinux on 2010-07-11
> **yc2 said:**
> ]However, I fear this will spoil the linenumbering of the pages. If I later, for example, get problems in JavaScript the errormessages will not give the same linenumber as the editor/sourcecode.
The line-number that javascript spits out when producing an error isn't the same as the line number in your PHP code anyway. It's the line-number in the source of the HTML (Page - View Source).
You can have 4000 lines of PHP and only 100 lines of HTML without any problem. If the error then shows line 25, you'll have to look for the 25th line of HTML-output (which don't have to be the 25th line anyway, since PHP does not include linebreaks after each HTML-line by default).

Short story, the include-file won't mess anything up, because it's already messed up before the include.

---

### Post by yc2 on 2010-07-11
Thanks new_tolinux that is true, I didn't explain myself clearly.

In these texts I use php sparingly. I use it to contact database for visitor statistics and some includes at the bottom of the file. I do not output a lot with php here.

I just made an intentional error in JavaScript and it came out in perfect paralell with the edtor "error on line 4871".

Is there a way to keep this while introducing more includefiles at the top or mid of the text?

(The pages are an introduction to Ubuntu, they are in Swedish
[http://e-dog.info/t/63/doc/Ubuntu_installation.php](http://e-dog.info/t/63/doc/Ubuntu_installation.php)
)

---

### Post by simeon87 on 2010-07-11
> **yc2 said:**
> Thanks new_tolinux that is true, I didn't explain myself clearly.

In these texts I use php sparingly. I use it to contact database for visitor statistics and some includes at the bottom of the file. I do not output a lot with php here.

I just made an intentional error in JavaScript and it came out in perfect paralell with the edtor "error on line 4871".

Is there a way to keep this while introducing more includefiles at the top or mid of the text?

(The pages are an introduction to Ubuntu, they are in Swedish
[http://e-dog.info/t/63/doc/Ubuntu_installation.php](http://e-dog.info/t/63/doc/Ubuntu_installation.php)
)

Since a semi-colon separates statements, you could put multiple statements on one line to keep the line numbering the way you want, I guess. However, you would spend more time keeping that in sync than actually developing and as the project becomes more complex, I see no reasons to do this. Your PHP, HTML and JavaScript files should be regarded as separate files and the line-by-line content is only loosely related.

---

### Post by soltanis on 2010-07-11
But along that line of reasoning, if you actually separated your code into .php and .js files, then I would expect whatever environment you are using will refer you to the appropriate line number in the .js file, which does not contain any of your PHP scripts.

---

### Post by yc2 on 2010-07-12
Just to clarify the problem:
What I want to do now is to intruduce larger php-include files in the beginning of the file. These do not contain so much php or javascript *code*. They mostly contain html, but I use the php-include function since the same material is introduced in several files. (Like the logo etc)


That is true soltanis,

If I put all javascript functions in one include file and all php functions (the latter are not so many) in another include I would know where to look for possible errors.

I have two larger includefiles for javascript specifically connected to this page. Some javascript must be in its proper location for timing reasons though (like calls to document.write that is read at page load).

Sometimes it is also convenient to have some code in the main file. I think I call at least ten js include-files (different libraries) in the text I referred to above and sometimes when I just want to find a function I don't know in which of the them to look.

Some js is also of the following kind. I am not sure the code validators love inline css, but it is very convenient to have formatting js where it is active, I think. Otherwise it is difficult to find.
```
<script type="text/javascript">
if (compensate_for_large_font == 1)
{document.write('<div class="title-box" style="width: 560px; padding-top: 16px;">');}
else if (reduce_font_size == 1)
{document.write('<div class="title-box" style="width: 446px; padding-top: 16px;">');}
else if ((BrowserDetect.OS == "Linux") && (BrowserDetect.browser == "Firefox"))
{document.write('<div class="title-box" style="width: 418px; padding-top: 16px;">');}
else {document.write('<div class="title-box" style="width: 416px; padding-top: 16px;">');}
</script>

```

But I think what you say is a useful point:

_If I introduce some more complicated JavaScript that is likely to require debugging, it is practical to put it in a separate file._

---

### Post by new_tolinux on 2010-07-12
If you're working on those scripts on a regular basis and the includes (logo etc.) aren't subject to regular change, it shouldn't be that hard to remember for yourself that you'll need to add X lines to an error-message.

On my own pages, everything is PHP (I'm using "print"-statements to output HTML because most of the pages are database-driven in some way or another), but I don't use that much javascript.
But if there's an error, most times the error message contains enough information for me to know where I have to look for the error.
Since I'm not a frequent user of line-breaks (\n) I can have a lot of code on line 1. Actually the only points where I'm using linebreaks is at the end of some JS-lines, since they're needed at some places (otherwise the page loads with a bunch of errors relating to nothing).
I also use an include-file to produce the "head" of the page, another for the menu, a third for some kind of submenu, etc. so even if I knew a line number it wasn't going to tell me much anyway.

But still, I'm more frequently having problems with forgotten semicolons [noparse](;)[/noparse], quotes (") etc. than I have with finding out where the real error in a script is.

---

### Post by yc2 on 2010-07-13
well, I started "cutting the pages to pieces". As more include-statements are inserted it will be difficult to remember how many lines to add, but hopefully the older JS will not break. It is very convenient to have only one file representing a repeating part of the pages.

Any inconveniance is well compensated by the pleasure to work with PHP. I think PHP is one of the languages giving the least number of unpleasant surprises. It stores numbers, characters, lines, entire texts in one kind of variable and usually no confusion occurs.

Being able to transfer values in a simple way from PHP to JS makes the environment very quick to work with, IMHO.

```
function Ubuntu_logo($left, $top) {
?>
<div id="blockDiv_logga" style="left: <? echo $left; ?>px; top: <? echo $top-94; ?>px;">
...

or
<script language="javascript" type="text/javascript">
var jsLanguage = "<?php echo $language; ?>";
...
```

---

