---
title: "how to use vi editior in ubuntu 7.04"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by saurabh kakkar on 2008-08-22
Hi
I have to Learn shell scripting so can any one tell me how to use vi editor in ubuntu 7.04 i m unable to understand what to do after firing 
vi [Filename] 
in command prompt 
basically i want to use some set commands Can any one help
me on this

---

### Post by HalPomeranz on 2008-08-22
You might find these useful:

[http://www.viemu.com/a_vi_vim_graphical_cheat_sheet_tutorial.html](http://www.viemu.com/a_vi_vim_graphical_cheat_sheet_tutorial.html)
[http://www.sm.luth.se/csee/courses/smd/139/smd139_vi.pdf](http://www.sm.luth.se/csee/courses/smd/139/smd139_vi.pdf)

---

### Post by tuxulin on 2008-08-22
i thought id do the search for you :)
the first hit on google showed [http://www.eng.hawaii.edu/Tutor/vi.html](http://www.eng.hawaii.edu/Tutor/vi.html)

Tuxulin

---

### Post by SeanHodges on 2008-08-22
Type in the command line (NOT in Vim):

vimtutor

Ubuntu ships with Vim, which is vi with extra features. Though if you want to use Vim properly you should install the full version:

sudo apt-get install vim-full

This will give you all the extra documentation and functionality that you will need.

EDIT: I forgot to mention... vimtutor is a "teach-by-doing" help tool. It will run you through commands and give you some interactive tasks to test what you have learned. If (like me) you learn more efficiently by trying things out as you go, vimtutor will be better than any book or on-line guide.

---

### Post by Nepherte on 2008-08-22
When you have installed the vim-full package, there is also a well explained tutorial you can use. Just run:
```
vimtutor
```

---

### Post by saurabh kakkar on 2008-08-25
Thanks everyone for ur inputs I have learned how to use Vi 
Now i will try my hands in shell scripting 

Regards
saurabh kakkar

---

### Post by Joeb454 on 2008-08-25
> **SeanHodges said:**
> Though if you want to use Vim properly you should install the full version:

sudo apt-get install vim-full

This will give you all the extra documentation and functionality that you will need.

It will also install gvim (a graphical implementation) amongst other things. If you just want [vim]("apt://vim") on it's own then you just run ```
sudo apt-get install vim
``` That will install the full version of vim, but none of the extra's that come in vim-full

---

### Post by SeanHodges on 2008-08-26
> **Joeb454 said:**
> It will also install gvim (a graphical implementation) amongst other things.

Good point, thanks for the correction.

> **saurabh kakkar said:**
> I have learned how to use Vi

Wow that was quick! :)

Come back if you hit any problems, good luck with the scripting!


Sean

---

