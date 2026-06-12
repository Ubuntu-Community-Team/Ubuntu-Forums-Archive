---
title: "Scrolling in a web page column created with glob search"
date: 2017-07-26
forum: Programming Talk
---

### Post by raysa on 2017-07-26
I'm using a glob search to display a very long list of links to pdf files in one column of a two-column web page. I would like a vertical scroll bar to be visible in that column to make it easier for users to whizz up and down the list (rather than using the scroll bar on the outer edge of the whole site). Putting the line "overflow: scroll" in the css for that column makes the bar appear but it is empty - no tag to click on and drag.

I assume this is because until the foreach/glob/echo/href stuff does its job there is very little content in the column, so the overflow command doesn't think there is anything to scroll. How can I make it recognise that when the column is filled with the links, it is very long and worth scrolling?

Here's the php code at the top of the page:

[PHP]<?php
header('Content-Type: text/html; charset=utf-8');
function getFiles(){
$files=array();
if($dir=opendir('.')){
    while($file=readdir($dir)) {
        if($file!='.' && $file!='..' && $file!=basename(__FILE__)){
            $files[]=($file);
        }   
    }
    closedir($dir);
}
natcasesort($files); //sort
return $files;
}
?>[/PHP]

Then there's the HTML for the head stuff, including the link to the css file, followed by some navigation buttons and then the div content for the two columns, with the problematic "col1" as below:

[HTML]<div id="content">
<div id="col1">
<h1><span style="font-weight: bold;">Tune library<br>
</span></h1>
<strong>Full library - alphabetical</strong><br>
<ul class="dir">
<? foreach (glob("*.pdf") as $file)
echo "<li name=\"".$file."\"><a href=\"".$file."\">$file</a></li>";
?>
</ul>
</div>
<div id="col2">[/HTML]

The page file is in the same server directory as all the pdf files whose links then form the list in col1.

If the css file has "overflow: auto" in the css for col1, no scroll bar appears at the side of the column, and if it is "overflow: scroll", the empty bar appears but with no scrolling tab. So the command is apparently not recognising the size of the column once the list is built. Is it possible to enable scrolling for the final length of the column?

Thanks for any help.

---

### Post by norobro on 2017-07-26
You didn't show your css. Are you giving your ul a height? 
```
#content #col1 .dir {
    overflow : auto;
    height : 500px;
}

```

---

### Post by raysa on 2017-07-27
Many thanks norobro ... adding this to the css has solved the problem perfectly.

---

