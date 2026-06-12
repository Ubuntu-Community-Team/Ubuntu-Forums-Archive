---
title: "Has anyone here got ASP.NET MVC3 to work on mono?"
date: 2012-10-15
forum: Programming Talk
---

### Post by CrimpJiggler on 2012-10-15
If so, would you be able to teamviewer me and show me how to do it? I'll pay you for your time. I need to learn how to program MVC3 projects (with razor view engine) and my brother offered to set me up with Windows 8 and the whole Visual Studio suite but open source OSs like Ubuntu embody all the things I stand for in my philosophy and capitalistic, commercial OSs like Windows embody all the things I resent and oppose so I would really prefer to do it on linux rather than having to dual boot or programming on a VM. 

So far I've got razor (.cshtml) page to run on mono but a couple of problems I've run into are:
1.) The browser won't load static files (such as images, .css, or .js files), I don't know if this is a routing problem or what, all I know is that the browser can't find the files.

2.) I followed the official Microsoft ASP.NET tutorial and everything worked up until I tried to use the ViewBag command inside a control. When I did that, it wouldn't let me compile it, it said I needed Microsoft.Csharp.dll. I went on a Windows machine and found that .dll file then added it to my projects bin folder and loaded it into the references list. After that the project compiled fine but when I loaded the webpage in my browser, I got error messages. 

I'm a complete beginner to all this, if anyone here who programs MVC3 on mono can show me how its done, I'd greatly appreciate it. I'm aware that you're all busy so I'll pay you for your time.

---

