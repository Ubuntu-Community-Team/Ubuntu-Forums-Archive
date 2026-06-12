---
title: "How To: Make Firefox pass &quot;browser checks&quot;."
date: 2010-10-08
forum: Outdated Tutorials &amp; Tips
---

### Post by tekkidd on 2010-10-08
Ever tried to use a web application (ie. iCollege) but realized that you couldn't because in the system check section recognized that firefox was running on linux which was not compatable. Well here is a quick tweak that will make web sites see your computer as running a Windows or Mac OS. 

1. Open up firefox and in the search type in ```
about:config
```

2. You will be prompted to proceed, proceed.

3. Right click on any value and select New>String

4. A window will pop up, type in ```
general.useragent.override
```

5. Another window will pop up. If you are running firefox 3.6.10 type in ```
Mozilla/5.0 (Windows; U; Windows NT 6.1; ro; rv:1.9.2.10) Gecko/20100914 Firefox/3.6.10
``` if you are running another version go to: [HTML]http://www.useragentstring.com/pages/Firefox/[/HTML] and search for your version of firefox (you can find your version by going to Help>About Mozilla Firefox). Once you find your version, look for a the windows user agent (The title will contain something like Windows NT 6.1) then copy the user agent and paste it in the second window. 

6. Save the configuration and restart firefox

Now, websites will recognize your computer as running Win7 and will pass you on the browser check.

---

