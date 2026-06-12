---
title: "gedit + LaTeX plugin. Inverse search?"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by khoda on 2008-07-31
Hi all,

I'm currently using gedit and the LaTeX plugin to edit my .tex files. I'm trying to make the "inverse search" to work. When I build using DVI (Special Sources), and ctrl + click on the dvi file, nothing happens. I was hoping it would take me to the place in the .tex file I click on. 

Has anyone successfully gotten this to work? I googled, but came up shored.

Thanks

---

### Post by saj0577 on 2008-07-31
Not tried the plguin myself. To be honest I dont know what .tex files are, but if you post a basic one in here as code then I will save it install the plugin and see if it works and if I can get it to work.

Saj

---

### Post by khoda on 2008-07-31
Wow! This community is awesome. 

Here's an example of a .tex file. > 
\documentclass[11pt,a4paper]{article}
\title{Example}
\author{khoda}
\date{\today}

\author{khoda}
\title{Example .tex file}

\begin{document}
	\maketitle
	This is a test! Let's get gedit + LaTeX plugin to work!
	
\end{document}



---

### Post by saj0577 on 2008-07-31
Thanks when I get a little bit of spare time I will sort this out for you.

I have sub subscribed to this thread untill I have solved the problem for you.

Saj

---

### Post by reia on 2009-05-16
If you use KDVI, then go to Configure, DVI Special and set
1)for Editor, User-Defined Editor
2)for Shell command, gedit +%l %f

---

