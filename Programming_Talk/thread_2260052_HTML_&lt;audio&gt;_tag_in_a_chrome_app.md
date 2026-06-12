---
title: "HTML &lt;audio&gt; tag in a chrome app"
date: 2015-01-08
forum: Programming Talk
---

### Post by Dave.YNA on 2015-01-08
Hello All,
 I am new to HTML, Javascript development and was playing around with creating a chrome web app. I have a html file that contain as HTML audio tag as follows:

```

<audio controls id="player">
  <source src="http://radio.talksport.com/stream" type="audio/mpeg" />
  <em>Sorry, your browser doesn't support HTML5 audio.</em>
  </audio>

```

My problem is that the player works when the page is opened in the browser but does not when opened as a chrome web app. I assume this has something to do with the chrome web-app permissions or content security policy but being new, I am not able to tell which one it is (if any) and what I need to do in order to get the stream to work. 

This is the [Content Policy]("https://developer.chrome.com/extensions/contentSecurityPolicy")
and this is the permissions page [https://developer.chrome.com/apps/declare_permissions#host-permissions]("https://developer.chrome.com/apps/declare_permissions#host-permissions")

I tried adding a few permissions to my manifest.json which seemed relevant but no luck. Any pointers in the right direction would be appreciated.

---

