---
title: "natcasesort in php file doesn't change the sort order"
date: 2017-05-01
forum: Programming Talk
---

### Post by raysa on 2017-05-01
I've been using this code to list files from a directory on a web page. It works well except that the listing comes up in standard sorting and I'd prefer it to be in natural order. So I changed the 'natsort' line to 'natcasesort' expecting that to fix it, but it doesn't make any difference. Does anything else need to change? 
I notice that the resultant html source lists all the files in a long line instead of a line each - is that part of the problem, if so how can I fix this? 
The server runs php7.
```
<?php
function getFiles(){
    $files=array();
    if($dir=opendir('.')){
        while($file=readdir($dir)){
            if($file!='.' && $file!='..' && $file!=basename(__FILE__)){
                $files[]=$file;
            }   
        }
        closedir($dir);
    }
    natsort($files); //sort
    return $files;
}
?>

  ... *Then some standard html code to lay out the page, but including, at the bottom before the </body> and </html>:*

<ul class="dir">
    <? foreach(getFiles() as $file)
        echo "<li name='$file'><a href='$file'>$file</a></li>";
    ?>
</ul>
```
Thanks for any help.

---

