---
title: "Web Handling scripts"
date: 2012-07-07
forum: Programming Talk
---

### Post by c2tarun on 2012-07-07
Hi friends,
Is it possible to write scripts that can pass parameters to a website?

Like I have an ISP which each time requires a username and password in order to connect to internet. Can I write a script that passes my username and password to their website and receive the log in successful message?

If I can write that kind of script, what technologies do I need to know in order to write that script?
If I can't write that kind of script is there any other way of automating that log in?

---

### Post by ofnuts on 2012-07-08
> **c2tarun said:**
> Hi friends,
Is it possible to write scripts that can pass parameters to a website?

Like I have an ISP which each time requires a username and password in order to connect to internet. Can I write a script that passes my username and password to their website and receive the log in successful message?

If I can write that kind of script, what technologies do I need to know in order to write that script?
If I can't write that kind of script is there any other way of automating that log in?

For a GET (parameters in the URL) a plain WGET will do it.

For a POST, use WGET with --post-data

To figure that out, use some HTTP header display/logger during a connection (LiveHTTPHeaders for Firefox, for instance).

---

### Post by c2tarun on 2012-07-09
> **ofnuts said:**
> For a GET (parameters in the URL) a plain WGET will do it.
 
For a POST, use WGET with --post-data
 
To figure that out, use some HTTP header display/logger during a connection (LiveHTTPHeaders for Firefox, for instance).
 
 
Thanks for replying, can you please elaborate a bit. What do you mean by WGET? All I know is WGET is a download manager. 
Are you suggesting that I should retrieve the page using WGET and check whether the parameters are passed throught GET or POST? And then some how use the same WGET to send the data as well?
 
I'll also try to look into your HTTP header display/logger today. Can you please suggest some logger for Google Chrome and rekonq

---

### Post by Habitual on 2012-07-09
[101 Spidering Hacks]("http://www.bournetoraiseshell.com/article.php/20100813204255221") ?

---

### Post by ofnuts on 2012-07-09
> **c2tarun said:**
> Thanks for replying, can you please elaborate a bit. What do you mean by WGET? All I know is WGET is a download manager. 
Are you suggesting that I should retrieve the page using WGET and check whether the parameters are passed throught GET or POST? And then some how use the same WGET to send the data as well?
 
I'll also try to look into your HTTP header display/logger today. Can you please suggest some logger for Google Chrome and rekonq
No, I meant ot use a logger to see what requests are sent by your browser, and then emulate them with wget (which I don't categorize as a "download manager", but as a command to issue arbitrary HTTP requests....)

---

### Post by c2tarun on 2012-07-09
> **ofnuts said:**
> No, I meant ot use a logger to see what requests are sent by your browser, and then emulate them with wget (which I don't categorize as a "download manager", but as a command to issue arbitrary HTTP requests....)

Hi I downloaded httpfox addon for Firefox and tried to open simple website like [www.google.in](www.google.in) I got the following page.

[ATTACH]220968[/ATTACH]

Can you please explain me the ouput??

---

### Post by c2tarun on 2012-07-09
> **ofnuts said:**
> No, I meant ot use a logger to see what requests are sent by your browser, and then emulate them with wget (which I don't categorize as a "download manager", but as a command to issue arbitrary HTTP requests....)

Hi I downloaded httpfox addon for Firefox and tried to open simple website like [www.google.in](www.google.in) I got the following page.

[ATTACH]220968[/ATTACH]

Can you please explain me the output??

---

### Post by ecnahc515 on 2012-07-10
Not to say you shouldn't try writing this script, that would be great practice; however most routers provide this functionality built in. Just thought I would let you know.

---

### Post by c2tarun on 2012-07-10
> **ecnahc515 said:**
> Not to say you shouldn't try writing this script, that would be great practice; however most routers provide this functionality built in. Just thought I would let you know.
I checked, this feature is not available with my router. :(
And I really want to write this script. Meanwhile I was reading about curl and I think I can use curl + php to write this kind of script. I'll post if I am able to do this successfully.


Please reply if anyone have suggestions regarding writing this script.
Thank you.

---

### Post by juancarlospaco on 2012-07-10
Google for "UserScript.JS" :)

---

