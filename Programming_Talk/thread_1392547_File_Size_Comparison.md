---
title: "File Size Comparison"
date: 2010-01-28
forum: Programming Talk
---

### Post by Obi-Won-Knewbie on 2010-01-28
I am new at scripting and need help developing a script that will look at a diff [URL="http://www.computing.net/answers/programming/file-size-comparison-script/20724.html#"][COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]file [/FONT][/COLOR][COLOR=blue ! important][FONT=Verdana]size[/FONT][/COLOR][/FONT][/COLOR][/COLOR][IMG]http://kona.kontera.com/javascript/lib/imgs/grey_loader.gif[/IMG]
[/URL] I've created from the original file and compare the size to the orignal and send a return code of 1 to the /etc/notify if the file is less than 6-% of its original size.


Basically:
If diff_file < 60% of original_file 


then 

send return code 1 to start paging.



else
send return code 0 to stop paging

---

