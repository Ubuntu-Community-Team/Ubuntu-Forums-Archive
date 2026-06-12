---
title: "Is there something wrong with the Ubuntu distro of tidy?"
date: 2009-03-26
forum: Programming Talk
---

### Post by jds340 on 2009-03-26
I've installed tidy (to tidy up bad html) via the usual apt-get and now have version 6 Nov 2007 (odd that there's no version number) but it doesn't do what it says on the tin.

I need it to do a pretty simple job "tidy some_crap_page.htm -o a_cleaned_up_page.html" but I get these problems

1) If I give it any commmand line option e.g. -o or -asxml then I get a screen full of cleaned up html, and then it sits waiting for user input so I have to ctrl-c it. Not much use in a command line script. 
2) It takes no notice of the -o option, well it sort of takes notice, it will complain that it can't write to file, which is odd, so I've created the file by "touch my_new_file.html" and then it doesn't complain, but also it doesn't write anything into the file.
3) I can't pipe the screen output to a file because it adds a "helpful" message onto the end of the screen dump, outside the html tag. 

In short it's useless, but I can't believe that it could be so useless. Is there something wrong with the Ubuntu version and should I get the source and compile it myself.

I've actually resolved the problem for this job, Firefox cleans up html, so for the small number of pages I need cleaned up right now I can just open then save in Firefox. But in future I might need to clean up hundreds or thousands of pages so I will need a working version of tidy.

Any advice?

Thanks

John Small

---

### Post by jds340 on 2009-03-26
Ah! I've solved the problem. I had the options after the file to be processed. Now it nearly works, it does things like remove <tbody> tags from tables but I can live with that.

---

