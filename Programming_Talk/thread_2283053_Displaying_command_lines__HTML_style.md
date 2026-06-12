---
title: "Displaying command lines  HTML style"
date: 2015-06-18
forum: Programming Talk
---

### Post by RobGoss on 2015-06-18
I was wondering if anyone knew what this website is using as far as **Syntax Highlighter **to display the command lines see were it says [B][COLOR=#222222][FONT=Verdana]
[B]
[SIZE=3]Install Cairo Dock[/SIZE][/B][/FONT][/COLOR][/B]

[http://www.webupd8.org/2013/03/cairo-dock-32-released-with-improved.html](http://www.webupd8.org/2013/03/cairo-dock-32-released-with-improved.html)

I'm not sure what codes is being used to contain them. Thanks

---

### Post by overdrank on 2015-06-18
Not sure I understand correctly. The link you have given is to a search page :)
Ok got it, that is fairly  old  March 25, 2013

---

### Post by RobGoss on 2015-06-18
Try the link now for some reason when I CCP it, it's not displaying correctly. Thank you

---

### Post by papibe on 2015-06-18
Are you referring to this (click to see)?
[ATTACH=CONFIG]262687[/ATTACH]

---

### Post by RobGoss on 2015-06-18
> **papibe said:**
> Are you referring to this (click to see)?
[ATTACH=CONFIG]262687[/ATTACH]

Yep that's correct any idea how this is accomplished

---

### Post by papibe on 2015-06-18
Not an Ubuntu support question. Thread moved to **Programming Talk**.

I'd recommend changing the title for HTML style help, or something alike.

Regards.

---

### Post by RobGoss on 2015-06-18
Don't know how to change the title of this post but thanks

---

### Post by papibe on 2015-06-18
Go to the first post. Press 'Edit Post' below the post's text. Then press the big orange button called 'Go Advanced'.

There you'll find an option to change the title of the thread.

Regards.

---

### Post by RobGoss on 2015-06-18
Thanks so much

---

### Post by Dimarchi on 2015-06-19
That is simple CSS formatting of pre elements. Inspect that particular piece of the page (for example, in Firefox right click above it and select Inspect Element (Q)) and you'll find everything related to it.

---

### Post by RobGoss on 2015-06-19
Yes already did and added the CSS to my style.sheet but can't see to get it to appear.

---

### Post by Dimarchi on 2015-06-19
Really? Well, here's a test for it (apart from the image mentioned in the background url):

```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8" />
<title>Code example</title>
<style type="text/css">
pre.linux-code {
    background: #E5CACA url("lincode.gif") no-repeat scroll 0px 0px;
    border-color: #9B0505;
    border-style: solid;
    border-width: 1px 1px 1px 20px;
    color: #000;
    font-size: 13px;
    font-family: "UbuntuBeta Mono","Ubuntu Mono","Courier New",Courier,monospace;
    margin: 10px;
    max-height: 500px;
    min-height: 16px;
    overflow: auto;
    padding: 28px 10px 10px;
    z-index: 10000;
}
</style>
</head>

<body>

<pre class="linux-code">
<code>sudo add-apt-repository ppa:cairo-dock-team/ppa
sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins</code></pre>

</body>
</html>
```

As it says, this will only apply to pre elements that have linux-code in their class attribute. All other pre elements that do not include this particular class are not affected.

---

### Post by RobGoss on 2015-06-19
Got it working thanks so much

---

