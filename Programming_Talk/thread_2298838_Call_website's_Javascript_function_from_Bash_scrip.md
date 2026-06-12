---
title: "Call website's Javascript function from Bash script"
date: 2015-10-14
forum: Programming Talk
---

### Post by fingerheroes on 2015-10-14
I'm running a program called QLC+ to run a light show. It has a web interface option, which is great. It allows the entire light show to be controlled through a built-in webserver.

Each of the buttons in this built-in webserver call Javascript functions to interact with the program. I can make a bookmarklet which will "press" a button in the site for me, but of course, that only works if I'm already on the site, which isn't very useful.

My question is pretty open-ended, but I couldn't find a good answer anywhere else on the web. I need some way of calling these Javascript functions remotely--that is, while not having the website open in a browser.

A bash script would be great. So would some sort of Android app. Even some way of telling the bookmarklet which site to execute the function on would be tremendously useful.

Sorry for such a vague question, but my problem here seems like a simple one. I just can't figure it out.

Thanks in advance.

---

### Post by Vaphell on 2015-10-14
python + selenium using PhantomJS driver for a virtual webbrowser?



```
#!/usr/bin/env python3

from selenium import webdriver

url = 'http://xxx.yyy.com'

driver = webdriver.PhantomJS()  # PhantomJS for headless, Firefox or whatever otherwise
driver.get(url)
# find relevant element in the html tree, eg...
view_all = driver.find_element_by_css_selector('a.view-all')     # <a class="view-all">
view_all.click()      
driver.close()
```

---

### Post by fingerheroes on 2015-10-14
So, say that I just need to execute function "javascript:functionx(a, b);"

Would the script use that like this?

```
#!/usr/bin/env python3

from selenium import webdriver

url = 'http://xxx.yyy.com'

driver = webdriver.PhantomJS()  # PhantomJS for headless, Firefox or whatever otherwise
driver.get(url)
# don't need to find HTML element
# view_all = driver.find_element_by_css_selector('a.view-all')     # <a class="view-all">
# view_all.click()
**functionx(a, b);**
driver.close()
```

(Sorry, I haven't used Python much before) (or Javascript) (in fact, this whole thing is going to be a learning experience for me)

---

### Post by Vaphell on 2015-10-14
I don't think it will be THAT easy, i doubt selenium, no matter how awesome it might be, will expose remote code in foreign language as first class functions 
Python is secondary here, you do whatever selenium api tells you to do.

Assuming your actions are under some buttons on the website you can locate an elem and click it as if you did it with mouse and you need to figure out how to unambiguously describe it by analyzing the html elements. That said, it seems that selenium also supports running custom jscript snippets using *execute_script()* so you should be able to embed your functions here.

[http://stackoverflow.com/questions/7794087/running-javascript-in-selenium-using-python](http://stackoverflow.com/questions/7794087/running-javascript-in-selenium-using-python)

---

