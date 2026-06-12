---
title: "begginer python........"
date: 2009-01-26
forum: Programming Talk
---

### Post by abhilashm86 on 2009-01-26
i am in process of learning python,found it top and easy compared to c or c++,but i use vim to do programs,it irritates at times because i can't identify indentation errors,due to which i do silly errors which seems troublesome to me.
so is there any interface or good editor which shows way to python, can anyone tell some good book which has good program examples of python,
book i use has lot of syntax and others,not much programs......

---

### Post by Kilon on 2009-01-26
> **abhilashm86 said:**
> i am in process of learning python,found it top and easy compared to c or c++,but i use vim to do programs,it irritates at times because i can't identify indentation errors,due to which i do silly errors which seems troublesome to me.
so is there any interface or good editor which shows way to python, can anyone tell some good book which has good program examples of python,
book i use has lot of syntax and others,not much programs......

I use Eclipse with the pyDev plugin , with no complaints. 

[http://www.eclipse.org/](http://www.eclipse.org/)

[http://pydev.sourceforge.net/](http://pydev.sourceforge.net/)

---

### Post by abhilashm86 on 2009-01-26
ok fine its like vb.net interface, so how do i install? 
from terminal or synaptic, the link you gave dosen't tell how to install.
I want to give try to eclipse,tell procedure,this is version of python i use, 

abhilash@abhi:~$ python
Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

so help this python fan:)

---

### Post by Kilon on 2009-01-26
> **abhilashm86 said:**
> ok fine its like vb.net interface, so how do i install? 
from terminal or synaptic, the link you gave dosen't tell how to install.
I want to give try to eclipse,tell procedure,this is version of python i use, 

abhilash@abhi:~$ python
Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

so help this python fan:)

Actually the links does tell if you do some further search .

You can install eclipse from add/remove or synaptic. It is straightforward should not create you any problems.

For pydev if you go to the download page via the link I provided, it will show you how to install it from inside eclipse which again it is extremely easy.  

Then as an option you can install the pydev extensions which extend pydev functionality , again in the download section show you the process for installing from inside eclipse which is pretty much the same as installing the PyDev.

Try it and if you got stuck , I am here to help you out.

---

### Post by WelterPelter on 2009-01-26
Stani's Python Editor works fine also.

---

### Post by abhilashm86 on 2009-01-26
> **WelterPelter said:**
> Stani's Python Editor works fine also.

oh well then does it support my version of python,just give information about how to install that editor,pls

---

### Post by Kilon on 2009-01-26
[http://ubuntuforums.org/showthread.php?t=297440](http://ubuntuforums.org/showthread.php?t=297440)

---

### Post by WelterPelter on 2009-01-26
```
 sudo apt-get install spe
```

---

### Post by abhilashm86 on 2009-01-26
Try it and if you got stuck , I am here to help you out.[/QUOTE]

thanks i'm trying now,wil inform later:)

---

### Post by sujoy on 2009-01-26
there is also a lot of info in the stickies.
regarding books, you can go for Learning Python, or use the online docs.

+1 for eclipse and pydev

---

### Post by nvteighen on 2009-01-26
Simplify: you can perfectly use Gedit for Python. Be sure to enable the plugins and you're there.

But in text editors, flamewars are ensured, so I won't comment further ;)

---

### Post by Mud.Knee.Havoc on 2009-01-26
A great book for beginners is: [Python Programming for the Absolute Beginner (2nd edition) by Michael Dawson]("http://www.amazon.com/Python-Programming-Absolute-Beginner-Second/dp/1598631128/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1233010295&sr=8-1")

---

### Post by airjaw on 2009-01-28
> **Kilon said:**
> 
You can install eclipse from add/remove or synaptic. It is straightforward should not create you any problems.


No no no no no. Do NOT install Eclipse from Synaptic. Please reference [this]("http://ubuntuforums.org/showthread.php?t=941461&highlight=eclipse+3.4") thread for information about installing the latest ver. of Eclipse (3.4) in Ubuntu.

The latest version of Eclipse is not in Add/Remove yet, you have to download and install 3.4 manually.

I also use Eclipse + PyDev, mostly because I had to use Eclipse at work and am familiar with it.  The 4 main IDEs for Python are:

Wing IDE, Komodo IDE, Eclipse+PyDev, and NetBeans.
The first 2 require purchase, the 3rd has a free version and a paid version w/ more features, and I think NetBeans is free.
[http://wiki.python.org/moin/IntegratedDevelopmentEnvironments]("http://wiki.python.org/moin/IntegratedDevelopmentEnvironments")

---

### Post by DocForbin on 2009-01-28
haven't used it much, but python support seems solid in netbeans. 6.5 is nice.

---

### Post by Greyed on 2009-01-28
> **abhilashm86 said:**
> i am in process of learning python,found it top and easy compared to c or c++,but i use vim to do programs,it irritates at times because i can't identify indentation errors,due to which i do silly errors which seems troublesome to me.
so is there any interface or good editor which shows way to python

Yes, vim.  Turn on syntax highlighting and configure it for sane Python development.  As an editor it is as good as the editors in the IDEs other people are pointing you.  Difference being vim is just an editor not an IDE and especially not an IDE written in Java, for Java, with Python bolted onto the side.

Here's the Python relevant portion of my .vimrc
```

let python_highlight_all = 1
augroup Python
  au!
  "au BufNewFile *.py read ~/util/templates/Python.py
  " see also :help smartindent , cinwords
  au FileType python set autoindent smartindent et sts=4 sw=4 tw=80 fo=croq
  " turn off the C preprocessor indenting
  " (allow comments in Python to be indented properly)
  " au FileType python inoremap # X^H#
  " au FileType python set foldenable foldmethod=indent
augroup END

```

---

### Post by DocForbin on 2009-01-28
just givin options dude. I wouldn't consider the python plugin bolted on the side of netbeans  anymore than a syntax/autocomplete file is bolted onto the side of an editor. It does handle refactoring, for example. And has the jpydbg debugger.

---

