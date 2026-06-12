---
title: "developing a web ui for my deskytop running into issues"
date: 2013-08-15
forum: Programming Talk
---

### Post by Veuned on 2013-08-15
hello everyone i an trying develop a web ui to run a series of scripts that are loocared on my desktop for a project at school 

i have apache2 , php5(with sgi), mysql, and i am able to connect to the "it works" web page anywhere in my house not just that i have a cgi script that shows memory, disk and users logged on to my desktop

but what i am wanting to do is just exicute a script from a button on a web page 

all my scripts are loaded in /scripts i have tried usinf the [B]exec 
[/B]command aswell as a number of other ways of doing this but the only
 resaults i get are either it prints the command on the web page or
the webpage staying blank

regards veund

---

### Post by Crusty Old Fart on 2013-08-17
Here's how I do it on my website:
My button is a hyperlink that loads a php page into the browser. The php page has code in it that executes bash scripts, calls php functions, and makes mysql queries. Data returned is manipulated with php code on the calling php page and then the desired output is wrapped in php generated html code for display in the browser. It's all pretty easy.

If you could post some of your code, we could start debugging it.

Best wishes,

Crusty

---

