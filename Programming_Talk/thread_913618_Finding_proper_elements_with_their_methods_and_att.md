---
title: "Finding proper elements with their methods and attributes in wxPython"
date: 2008-09-07
forum: Programming Talk
---

### Post by mohtasham1983 on 2008-09-07
Hi.

I just started working with wxPython. I really like it. The only thing that I don't like about is, its poor documentation.

I have been looking for an element for password field, similar to that of input type='password' in html, but I cannot figure out how I can find that element.

Also, I'm looking for another element, which can be hidden in the window and when an error happens, a message appears in it. I used a StaticText element with no text in it. After an error appeared, I tried to change the value of that, but didn't find the appropriate method for it.

Basically, I was looking for an easy way to find appropriate elements and methods in wxPython. I've just started working with wxPython and I know that I will need to find everything easily in future.

Also, I tried to use python shell, but some classes have so many methods which is very hard to understand what they do.

Thanks in advanced.

---

### Post by kjohansen on 2008-09-07
I know there are some editors (like WingIDE) that have advanced code completion specifically designed and advanced for wxPython.

You can easily search through the available elements and methods in the package.

WingIDE is not free but there are free trials to see if you like it or get you started in wxPython.

---

### Post by mohtasham1983 on 2008-09-07
I use gvim and it only has text-completion feature, if a text has been already written in the code.

---

### Post by viordiasko on 2008-09-08
Perhaps you could try SPE. It's in the repositories. 

 I can't be 100% sure if it has code-completion, but I'm sure I  wrote a small wxPython prog using it.

---

### Post by Wybiral on 2008-09-08
IDEs are great for convenience, but if pythons 'help' and 'dir' functions (coupled with the libraries documentation) don't help you then the API you're using is just poorly written (in this case, I doubt that's it, but as a general rule).

Documentation for an API goes miles further than any autocomplete / attribute listing feature that an IDE will give you. IDEs like that just make it faster once you know those things.

---

### Post by mohtasham1983 on 2008-09-08
> **viordiasko said:**
> Perhaps you could try SPE. It's in the repositories. 

I can't be 100% sure if it has code-completion, but I'm sure I  wrote a small wxPython prog using it.

Thanks, it looks pretty good. I don't know why I've never heard of it before. I hope it is not buggy.

It seems to provide a list of methods for each module. However, some modules have a lot of methods. It's kinda hard to find out what each method does.

I really appreciate your help. 

Thanks

---

### Post by SledgeHammer_999 on 2008-09-08
> **mohtasham1983 said:**
> Hi.

I just started working with wxPython. I really like it. The only thing that I don't like about is, its poor documentation.

I have been looking for an element for password field, similar to that of input type='password' in html, but I cannot figure out how I can find that element.

Also, I'm looking for another element, which can be hidden in the window and when an error happens, a message appears in it. I used a StaticText element with no text in it. After an error appeared, I tried to change the value of that, but didn't find the appropriate method for it.

Basically, I was looking for an easy way to find appropriate elements and methods in wxPython. I've just started working with wxPython and I know that I will need to find everything easily in future.

Also, I tried to use python shell, but some classes have so many methods which is very hard to understand what they do.

Thanks in advanced.

I don't know about the python bindings but the documentation for C++ is excellent. I'll give you the answers for the C++ and you can look them for the python equivalents.

1.For the "password" thing, just use a wxTextCtrl and specify the window style as "wxTE_PASSWORD". link-->[http://docs.wxwidgets.org/stable/wx_wxtextctrl.html](http://docs.wxwidgets.org/stable/wx_wxtextctrl.html)

2.To change the value of the statictext do this:
```
wxStaticText label;
label.SetLabel("your error goes here");

```
Documentation link--->[http://docs.wxwidgets.org/stable/wx_wxstatictext.html#wxstatictextsetlabel](http://docs.wxwidgets.org/stable/wx_wxstatictext.html#wxstatictextsetlabel)

---

### Post by mohtasham1983 on 2008-09-08
> **SledgeHammer_999 said:**
> 
1.For the "password" thing, just use a wxTextCtrl and specify the window style as "wxTE_PASSWORD". link-->[http://docs.wxwidgets.org/stable/wx_wxtextctrl.html](http://docs.wxwidgets.org/stable/wx_wxtextctrl.html)

2.To change the value of the statictext do this:
```
wxStaticText label;
label.SetLabel("your error goes here");

```
Documentation link--->[http://docs.wxwidgets.org/stable/wx_wxstatictext.html#wxstatictextsetlabel](http://docs.wxwidgets.org/stable/wx_wxstatictext.html#wxstatictextsetlabel)

Thanks for help. I found out that for wxPython, the password style is wx.TE_PASSWORD. Just an extra "." after wx.

The other method worked perfectly fine, too.

---

### Post by mohtasham1983 on 2008-09-23
I just wanted to let you guys know that vim has a feature that can show the list of all methods with their description.

Based on the information I found in a web page I added:

[PHP]
autocmd FileType python set omnifunc=pythoncomplete#Complete
inoremap <Nul> <C-x><C-o>
[/PHP]

to my vimrc and by pressing ctrl+space, it gives me the list of methods and their descriptions on top of the window.

My reference was from here:
[http://blog.sontek.net/2008/05/11/python-with-a-modular-ide-vim/](http://blog.sontek.net/2008/05/11/python-with-a-modular-ide-vim/)

---

