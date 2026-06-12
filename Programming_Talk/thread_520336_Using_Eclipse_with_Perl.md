---
title: "Using Eclipse with Perl"
date: 2007-08-08
forum: Programming Talk
---

### Post by spur on 2007-08-08
Steps to create and test a perl file in Eclipse using Epic.
This is targeted at people new to Eclipse and probably to Perl 
I found no directions on how to treat perl scripts that included html and so created this in the hope it would be useful for someone. Doing this will avoid the need to use apache to test your perl scripts.
Before you start, install Eclipse and perl. The go to the Epic home page at [http://e-p-i-c.sourceforge.net/faq.html#Is_a_Perl_interpreter_required](http://e-p-i-c.sourceforge.net/faq.html#Is_a_Perl_interpreter_required)
and install epic.The instructions are clear and basic.
Now create a new Perl Project by clicking new and selecting Perl project.
Thumb 1 and 2. Name the project anything you want and click finish.
Now create a new perl local file by clicking new again and selecting 'Perl file'.
Give the file a name and add the extension e.g. example.pl.
Thumb3
Enter your script code and save to the current workspace. Then click project _run.
Thumb4
In the Create manage and run configurations that comes up 'cgi root directory' and html 'root directory' make the workspace.
The 'html startup file' make the file you want  to run. Click 'apply' then 'run'. After a short while You will see the file in your browser
On thumb 5 you will see a tab 'browser' I found this worked best when I set it to Firefox. I left the other setting alone for now.
Using this method you can keep the browser open on one desktop alter the file you are testing and click on the browser refresh button to see your changes rather than have to go through everything again.

---

