---
title: "Make a script for download files"
date: 2014-01-15
forum: Programming Talk
---

### Post by raac on 2014-01-15
Hi all, I've got a question. Is it possible to make a Perl script that automatically would download files from a specific website.
I was thinking in adding wget commands into that script, but wget command doesn't do what I thought it would do.
Say the website [http://abcabcabc.com/123]("http://downloadFile.com/123") allows me to download a file named report.txt. In other words, by putting that URL in the browser the "Save" dialog would show up, and I would be able to download the file.

I thought the command wget [http://abcabcabc/com/123]("http://downloadFile/com/123") would download the report.txt. Instead, it download the actual .html file (which shows up with garbage)


What are my options?

Thanks.

---

### Post by ian-weisser on 2014-01-15
Perhaps you misunderstand how web sites and URLs work.

The scenario you describe only occurs using a web browser to download a link, or if the link is hidden by javascript.
You want the URL directly to report.txt instead of the 123.html page. For example: [http://abcabcabc.com/textfiles/report.txt](http://abcabcabc.com/textfiles/report.txt) .

If report.txt is dynamically generated, then you should manually analyze the page to determine how to get it. For example, by sending the correct POST or Javascript data.

Using a script to simulate a person traversing the website in a browser, clicking buttons and responding to prompts, is usually a frustrating and ineffective way to go.

---

### Post by raac on 2014-01-16
How would I analyze the website?? I tried typing the website with firebug enabled, but firebug doesn't get to report anything.

---

### Post by ian-weisser on 2014-01-16
I would read the html and/or javascript code.
Perhaps it's not dynamically generated. Perhaps you merely have the wrong static URL.

---

### Post by raac on 2014-01-16
Thanks for your reponse.See the weird thing is that the website itself, the one that makes the "Save" dialog to pop up, contains garbage. As I said before I did a wget <website>, and it downloaded the html file, there nothing meaningful..

Attached is a screen-shot

---

### Post by ofnuts on 2014-01-17
Use an add-on to watch the HTTP headers (like "Live HTTP Headers" for Firefox). What is the content-type of what you see? it could be some Flash thing...

You can also save one file by hand and check its download URL in the download manager, and see if you can algorithmically deduce the others from it (like continuing a number sequence) or relate that URL to something in the original link, and then algorithmically deduce the URL of the target files from the URLs of the original link in the web page.

---

