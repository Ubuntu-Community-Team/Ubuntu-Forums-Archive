---
title: "Web based application development in python"
date: 2007-06-14
forum: Programming Talk
---

### Post by Betelgeuse on 2007-06-14
Hi,

I'm a web application developer working on web based database applications. I'm currently using asp for web programming and whatever database (MS SQL, oracle, etc...) my clients use as backends. I do not want to contunie using ASP because I'm now converted to be a Kubuntu user and I want my applications platform independent. I know java, ajax and I consider myself an expert on database programming but for the user interface, I'm looking for alternatives. I know PHP but I do not want to use it, it's equally boring as ASP. So, I'm considering to switch over to using python language. What tools should I have to install my computers to start developing and running python web based applications ? I have seperate database servers to connect so all I need is some advice on using some IDE and some web server to run python applications in a browser.

---

### Post by elst on 2007-06-14
I've just started playing with the Django framework, and am very impressed so far, particularly with the quality of the documentation. The package in the Ubuntu repository is for the previous version, but the download from the Django Website works without issue on Feisty.

Django includes a Web server for development, and the documentation covers production deployment. I will probably use the lighttpd and FastCGI configuration rather than Apache with modpython, as lighttpd consumes a lot less memory IME.

I've been using a combination of gedit and Eric for Python work so far, but will probably look at SPE in the near future.

---

### Post by pmasiar on 2007-06-14
Another popular web app framework (and my preferred :-) ) is TurboGears. Instead "monolithic" Django, it has plugin architecture, with best-of-breed modules integrated. 

You are right to reject PHP after you learned in ASP that mixig presentation and code created unmaintenable mess. Both TG and Django nudge you to use much cleaner model-view-controller application architecture.

(Note to barmazal: yes I know that MVC is not invented by TG or Python :-) )

As you will start using Python more, you realize that IDE is less important, because language is cleaner and API simpler to remember than other languages. Any progammer's editor will do: just set it up to replace tabs with 4 spaces. I prefer SciTE for simple edits, and SPE for real work. SPE's author Stani is Ubuntu user...

Many good Python books are available free online, see wiki in my sig. But you may want to splurge $10 on pocket Python reference.

---

