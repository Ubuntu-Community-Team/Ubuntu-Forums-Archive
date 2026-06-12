---
title: "File Joiner 'PHP class' now you can join the online files"
date: 2010-05-13
forum: Programming Talk
---

### Post by astkboy2008 on 2010-05-13
This class can be used to join files retrieve via **HTTP**  into a single file.
It takes a list of **HTTP URLs** and  retrieves the data from the specified  locations.
The class gathers the retrieved data and save it to a single local file.
see in action example from its [wiki]("http://www.jooria.com/projects/view?wiki=12")
        to Get the files you should push the files in array like that:
[PHP]$fileList = array();
$fileList[] = 'http://www.ackrentals.net/css/reset.css';
$fileList[] = 'http://www.ackrentals.net/css/960_24_col.css';[/PHP]and then you should start new **FileJoiner**  
[PHP]$joiner = new FileJoiner($fileList);[/PHP]then you have option enable you to compress the file by delete any   Unhelpful comments 
[PHP]$joiner->compression  = true;[/PHP]then you should determine the file that will join it some thing like  this 
[PHP]$joiner->join('css/allstyles.css');[/PHP]and at end you should unset the variables  
[PHP]unset($joiner);[/PHP]
[the  class page]("http://www.jooria.com/projects/view?project=977")
[download it]("http://www.jooria.com/projects/view?project=977&m=downloads")

---

