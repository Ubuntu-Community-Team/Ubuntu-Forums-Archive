---
title: "Link Grabber in bash ?"
date: 2010-04-09
forum: Programming Talk
---

### Post by Ahmedmb on 2010-04-09
:)Dear All

i need one line command  or bash acript to get download link from html page :

```
<h1>Alternative download page</h1>
<p>
	Right-click and select "Save as" on the subtitle link below:
	<h2>
		<span id="downloadIcon"><img src="/themes/base/images/downloadicon.gif"></span>
		<a id="ctl00_bcr_downloadlink" href="/Downloads/Temporary/Subtitles/human.target.2010.0105.hdtv.xvid-notv_104961.zip">human.target.2010.0105.hdtv.xvid-notv - Arabic by Birdy</a></h2>
</p>
<br /> 
<br /> 
<br /> 
<p> 
```

returned link :

/Downloads/Temporary/Subtitles/human.target.2010.0105.hdtv.xvid-notv_104961.zip

THX to all :P

---

### Post by heikaman on 2010-04-09
I'm sure you can find that if you google, but it was fun to write :), here's a one line command in python:

[PHP]
python -c "import sys,re; map(sys.stdout.write, re.findall(r'href=[\'\"]?([^\'\" >]+)', open('page.html').read()))"[/PHP]

**Substitute page.html with the file name.**

---

