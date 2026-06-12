---
title: "Using wget and javascript"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by jcclubb15 on 2013-07-10
Ok, so I use the command wget -E -H -k -K -p -l 2 (because I only want the website two layers deep) [www.website.com]("http://www.website.com"). It downloads the webpage, but the part that's javascript doesn't load or doesn't download I don't know which one it is. Please help.

---

### Post by slickymaster on 2013-07-10
In some sites some of the asset links required to render the page in a browser are themselves created through javascript. Wget has a feature request pending to run javascript: [JavaScript Functionality For Wget]("http://wget.addictivecode.org/FeatureSpecifications/JavaScript")
Sites that build asset links using javascript won't be cloneable using wget. The easiest solution is to find a tool that is actually building a DOM and parsing javascript like a browser engine.

---

