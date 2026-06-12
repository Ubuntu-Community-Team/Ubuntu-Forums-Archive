---
title: "Bash script to auto fill web forums?"
date: 2015-05-01
forum: Programming Talk
---

### Post by black8 on 2015-05-01
[COLOR=#000000][FONT=Verdana]Hey,[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I am working in an factory which employees 200+ contract workers. They don't have internet or computer access. Out government has issued a number, called UAN which will get them a lot of benefits.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]All that stands between them an the number is an online verification process. I thought of helping them out by collecting all the information required and typing it into a file. Then I could write a bash script to read the values and submit it. I tried following this guide.

My FORM REPORT is  like this:

Uses POST to URL "<form name="check_uan_status" id="check_uan_status" method="post" >"

So how do i frame the cURL command?

Here is the concerned website:
uanmembers.epfoservices.in/check_uan_status.php
And here is the formfind report:
[http://pastebin.com/dXgNrNiW](http://pastebin.com/dXgNrNiW)

Or is there a better way to do this?

[/FONT][/COLOR]

---

### Post by ofnuts on 2015-05-01
Typically you add the LiveHTTPheaders to your browser and issue a request to check what the browser sends. It is then rather straightforward to mimic that (the hard part isn't sending the data, it's keeping the authorizations and cookies where necessary).

For examples of curl syntax, see [http://superuser.com/questions/149329/what-is-the-curl-command-line-syntax-to-do-a-post-request](http://superuser.com/questions/149329/what-is-the-curl-command-line-syntax-to-do-a-post-request)

IMHO you'll be better off with Python for this kind of work. using the urllib2 & urllib modules.

---

