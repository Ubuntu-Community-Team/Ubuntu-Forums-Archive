---
title: "URGENT :: Progarming Help"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by anuraggautam on 2008-06-18
Hello Everyone,

I need a help from your side ,

I have a file named as "a.txt" having 10000 names.Now i want to change the contents formate like this :

Say i have a contents in "a.txt" like :

Apple
Banana
Mango
Pineapple


I want to make a new file named as "a1.txt" the formate like :

'Anurag',
'Banana',
'Mango',
'Pineapple',



Can you provide me how to do that in PHP ? I am stucked with this from last 1 hrs ...Please provide me code for this !

Thanks in Advance !

Regards,

---

### Post by hyper_ch on 2008-06-18
Can you show the code you have written so far?

---

### Post by hyper_ch on 2008-06-18
No double posts!  --> [http://ubuntuforums.org/showthread.php?t=832885](http://ubuntuforums.org/showthread.php?t=832885)

---

### Post by sim-value on 2008-06-18
I know how to write rename loops in PHP 

but what has this to do with ubuntu and WHAT ARE YOU TRYING TO DO ?

---

### Post by Tomatz on 2008-06-18
Yeah you shouldn't talk about hacking on the forums either ;)

---

### Post by fatality_uk on 2008-06-18
This may help.
[http://www.w3schools.com/php/default.asp](http://www.w3schools.com/php/default.asp)

---

### Post by aktiwers on 2008-06-18
Does it have to be in PHP?

---

### Post by hyper_ch on 2008-06-18
you're not going to provide what you have written/tried so far?

---

### Post by anuraggautam on 2008-06-18
Any language......I Just want Output

---

### Post by anuraggautam on 2008-06-18
Sorry I will take care abt that [;)]

---

### Post by anuraggautam on 2008-06-18
<?php
$file = fopen("list.txt", "r") or exit("Unable to open file!");
//Output a line of the file until the end is reached
$ret="'";
$ret1=",";
$ans;
while(!feof($file))
 {
       $str=fgets($file);

       for($i=0;$i<strlen($str);$i++)
       {
               if($i==0 ||$i==strlen($str)-1)
               {
                       $ans.=$ret;        
               }
               if($str[$i]==" ")
               {
                       $ans.=$ret.$ret1.$ret;
               }
               $ans.=$str[$i];
               
               
       }
       $ans.= "<br>";

 }
echo $ans;
fclose($file);
?>

---

### Post by anuraggautam on 2008-06-18
Done ! Thanks to me [:)]

---

### Post by hyper_ch on 2008-06-18
> **anuraggautam said:**
> Done ! Thanks to me [:)]

So, you have it already?
btw, putting code into [noparse]```

```[/noparse] brackets makes it easier to read... or even use [noparse][php][/php][/noparse] brackets if it's php - help making it easier for others to help you ;)

---

### Post by Tomatz on 2008-06-18
> **anuraggautam said:**
> Sorry I will take care abt that [;)]

You brute... sorry dictionary ;)

:lolflag:

---

### Post by frodon on 2008-06-18
Duplicate threads merged.

Please only open one thread per question.

---

