---
title: "What's wrong with this PHP foreach() loop?"
date: 2011-03-28
forum: Programming Talk
---

### Post by x1a4 on 2011-03-28
Hi,

I've a function that worked for years and is now suddenly throwing an 'Invalid argument supplied for foreach()' warning.  Could someone please have a look and tell me what the problem is and how to fix it?  Thank you. 

[php]
function recurse($path,$walldirs=array()) //{{{
{
  foreach(glob($path."/*",GLOB_ONLYDIR) as $d) //{{{
  {
    $GLOBALS['walldirs'][]=$d;
    recurse($d,$walldirs);
  } //}}}

} //}}}


$walldirs=array();
recurse($_SERVER[DOCUMENT_ROOT]."/wallpapers");

$wallcount=0;
foreach($walldirs as $dd) //{{{
{
  $wallcount+=count(glob($dd."/*.jpg"));
} //}}}

$walldirs=array();
[/php]

The whole thing is supposed to recursively count JPEGs.  The function in question is supposed to get me all the directories and subdirectories.  The foreach() in question is the one inside the recurse() function.

---

### Post by SeijiSensei on 2011-03-28
Recent versions of PHP sometimes complain when a function is the argument to another function.  Try this:

```

function recurse($path,$walldirs=array()) {
  $myglob=glob($path."/*",GLOB_ONLYDIR);

  foreach($myglob as $d)  {
    $GLOBALS['walldirs'][]=$d;
    recurse($d,$walldirs);
  } 
}
```

Does that help?  I don't really understand the reasoning behind this and haven't invested the effort to figure out why the developers flag this as a problem.

You sure have a lot of extraneous braces in that code.  I suppose you have your reasons (debugging, perhaps?), but I removed them all for clarity.

---

### Post by x1a4 on 2011-03-28
Sorry. Didn't help.  
'PHP Warning:  Invalid argument supplied for foreach()'

I thought it might be because I use $_SERVER[DOCUMENT_ROOT] in the argument to the recurse() function but that's not it.  php.net has nothing useful. 

The commented braces are used for code folding by the jEdit editor.  I no longer use it but some of my older code still has the braces.  

I really need to figure this out since this function runs over 160 times each time the page is opened.  This makes the log file fill up significantly pretty fast.

---

### Post by Reiger on 2011-03-29
If you read the documentation of the glob() function you will find, buried in the return section, a little note. It says this function will return FALSE if an error occurs, and three guesses as to whether or not FALSE is iterable...?

---

