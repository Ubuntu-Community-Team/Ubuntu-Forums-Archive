---
title: "Webkit for python"
date: 2008-09-04
forum: Programming Talk
---

### Post by mohtasham1983 on 2008-09-04
Today after installing google chrome on windows, I really enjoyed the speed and simplicity of webkit. That's why, I decided to create a desktop application similar to my website. I only want to add some parts of web app and VoIP feature to the desktop application, which is not possible to implement in the web application. 

I used django to develop my web application. That's why I'm planning to develop my desktop application on python, so that i can share some code between them. I tried to find articles about pywebkitgtk and pyqtwebkit online, but I wasn't able to find anything useful. I don't know if these projects are still incomplete or what.

I'm wondering if anyone has ever done anything with webkit and python? I don't care about gtk or qt as far as it is python based and does the job.

---

### Post by pmasiar on 2008-09-04
For desktop apps, use popular toolkits like wxPython and friends. Not sure how webkit (== web app framework?) can be used for desktop app. It would have to run in browser, and that has known bad effects on usability.

---

### Post by deuce868 on 2008-09-04
Check out gwibber: [http://launchpad.net/gwibber](http://launchpad.net/gwibber)

I uses pywebkit to render and should be a good example for you

---

### Post by mohtasham1983 on 2008-09-06
> **pmasiar said:**
>  It would have to run in browser, and that has known bad effects on usability.

Most programs are going to use webkit as their engine. Pidgin is one of the example of such programs. I think they use c++ for that, though.

I just  want to use the latest technologies. 

> Check out gwibber: [http://launchpad.net/gwibber](http://launchpad.net/gwibber)
 

Thanks, I will have a look at it.

---

### Post by pmasiar on 2008-09-06
> **mohtasham1983 said:**
> Most programs are going to use webkit as their engine. Pidgin is one of the example of such programs. I think they use c++ for that, though.

[http://en.wikipedia.org/wiki/Webkit](http://en.wikipedia.org/wiki/Webkit) is a tool to build browser. It just shows your app to the user, you need to write your app (server part: creating the pages to show) using something else (LAMP: Python/Ruby/Perl/PHP), and  C++ would be the **worst** language to implement the server part.

---

### Post by mohtasham1983 on 2008-09-06
That's exactly what I'm looking for. I don't want to make exact same thing in desktop application. For example, I need a wxPython based gui application with two tabs. First tab will be regular desktop application interface, and second tab will contain html data using webkit. I couldn't find any tool that I can use to achieve that. :(

---

