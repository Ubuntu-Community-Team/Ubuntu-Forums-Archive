---
title: "New browser tabs for pdf files from glob-created list?"
date: 2017-08-16
forum: Programming Talk
---

### Post by raysa on 2017-08-16
To list a large number of sheet-music pdfs on a website, I'm using this at the top of my php/html file:

[PHP]<?php
header('Content-Type: text/html; charset=utf-8');
function getFiles(){
    $files=array();
    if($dir=opendir('.')){
        while($file=readdir($dir)) {
            if($file!='.' && $file!='..'){
                $files[]=($file);
            }   
        }
        closedir($dir);
    }
    natsort($files); //sort
    return $files;
}
?>[/PHP]

... then in the <ul> bit of the html section I have this:

[HTML] <? foreach (glob("*.pdf") as $file)
	echo "<li name=\"".$file."\"><a href=\"".$file."\">$file</a></li>";
    ?>[/HTML]

It works fine, except that when clicked on, the pdf replaces the web page content in the browser, and I would prefer it to appear in a separate browser tab.
I've tried inserting "_blank" in various places but it kills the page, so I'm obviously not doing it right (I'm a musician, not a programmer!).
How can I get this otherwise successful set-up to trigger a new browser tab for each tune clicked?
Thanks

---

### Post by raysa on 2017-08-16
OK now ... changing the template bit as follows did the trick:

[HTML]<?php
foreach (glob("*.pdf") as $file) {
    echo '<li name="'.$file.'"><a href="'.$file.'" target="_blank">'.$file.'</a></li>';
}
?>[/HTML]

---

