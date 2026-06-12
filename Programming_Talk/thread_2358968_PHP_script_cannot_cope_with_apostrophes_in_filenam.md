---
title: "PHP script cannot cope with apostrophes in filenames"
date: 2017-04-19
forum: Programming Talk
---

### Post by raysa on 2017-04-19
I am making a collection of pdf files available on a website, using a PHP script in their directory to read all the filenames and present them as links to the pdf files. However, some of the filenames have an apostrophe (eg: "Sean Ryan's polka"), and these will not open. An error indicates that the file "Sean Ryan" is not found - the script has called the filename only up to its apostrophe, so of course it doesn't match. All the ones without apostrophes work fine.
Using htmlspecialchars seems to be often suggested when this problem arises, and I've tried putting "htmlspecialchars($file)" into the script at various places but I clearly haven't got it right because it won't work. If this is a good approach, could someone tell me exactly how and where to put it in the attached script? (Attached as a txt file because the forum firewall won't let me post it directly here).
The server PHP version is 7.
Many thanks for any help.

I realise that an alternative approach would be to batch-rename all the filenames to strip out all apostrophes, but the filenames are all the actual names of tunes, many of them very well known, and it seems very sloppy to list things like O'Carolan's Concerto as OCarolans Concerto, or Bess's Hornpipe as Besss Hornpipe. But if I'm advised that this is technically preferable to avoid online problems, I could resort to this.

---

### Post by SeijiSensei on 2017-04-19
Let's start with this:
```
echo "<li name='$file'><a href='$file'>$file</a></li>";
```
Try replacing the single quotes with double quotes like this
```
echo "<li name=\"".$file."\"><a href=\"".$file."\">$file</a></li>";
```
Any better?

Encasing strings with apostrophes inside single quotes can cause problems for the parser.

Alternatively you can replace apostrophes with the "&rsquo;" HTML entity as you suggest.  It might be easier simply to do a str_replace() like this:
```

    <? foreach (glob("*.pdf") as $file)
        $file=str_replace("'","&rsquo;",$file);
        echo "<li name='$file'><a href='$file'>$file</a></li>";
    ?>

```

---

### Post by slickymaster on 2017-04-19
Thread moved to **Programming Talk** for a better fit.

---

### Post by raysa on 2017-04-19
Many thanks SeijiSensei ... your revised echo line has done the trick.  I had actually tried changing this line with double instead of single quotes but I obviously didn't get it right because it didn't work. But your change works a treat.
Just before I mark the question solved, can I ask ... is this fix likely to work over all platforms & browsers (in which case I'm very happy with it), or would you advise playing safe by removing apostrophes from the filenames altogether?
Thanks again
Ray

---

### Post by SeijiSensei on 2017-04-19
I doubt it would fail on any browser, but if you're worried about that, you can use the method of replacing apostrophes with &rsquo;.  Since that's a standard HTML entity, all browsers know how to interpret it.
> I had actually tried changing this line with double instead of single quotes but I obviously didn't get it right because it didn't work.
You have to make sure to "escape" the double quotes with a leading backslash inside a double-quoted string so they will be treated literally by PHP.

---

### Post by raysa on 2017-04-19
Many thanks again SeijiSensei ... extremely helpful.

---

