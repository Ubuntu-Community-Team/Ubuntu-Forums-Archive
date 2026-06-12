---
title: "Problems with JS and IE"
date: 2008-04-12
forum: Programming Talk
---

### Post by ipaqman23 on 2008-04-12
Hi,

I got a problem with my JS-Code and IE. Does anyone know a solution to debug JS in IE under Ubuntu?

Everything is fine with Firefox.

Maybe someone can give me a hint, what is wrong with IE and I can fix my script so that it is accessable as well for IE-Users!

The URl to my project is [www.tubesearch.de](www.tubesearch.de)

---

### Post by LaRoza on 2008-04-12
What version of IE?

---

### Post by ipaqman23 on 2008-04-12
i think I'm getting the bug in any IE version. I tried it with IE6.

---

### Post by LaRoza on 2008-04-12
> **ipaqman23 said:**
> i think I'm getting the bug in any IE version. I tried it with IE6.

Describe the bug...

What is supposed to happen? What doesn't happen?

Note: This is an Ubuntu Linux forum, and this is the Programming Talk. I see this is your first post, and it has a link to a site, of which you claim to be a developer. Spam is not allowed on this forum. However, if this is a genuine programming problem, I will allow it. Be more specific about what is the problem or this will be jailed.

---

### Post by ipaqman23 on 2008-04-12
Sorry, I should have been more specific:

I'm calling several js-scripts on page load. Everything works fine in Firefox. But calling the page in IE throws out an error and tubescript.js doesn't get executed which results in total unfunctionality of my site. 

So now is my question, if somebody could give my a hint where the error in my script could be. 

The error which IE throws out should be on line 277 but I can't find anything that seems wrong...

---

### Post by LaRoza on 2008-04-12
> **ipaqman23 said:**
> Sorry, I should have been more specific:

I'm calling several js-scripts on page load. Everything works fine in Firefox. But calling the page in IE throws out an error and tubescript.js doesn't get executed which results in total unfunctionality of my site. 

So now is my question, if somebody could give my a hint where the error in my script could be. 

The error which IE throws out should be on line 277 but I can't find anything that seems wrong...

Before looking at the code, I will say that this this a sign of poor design.

The three aspects of web design (on the client) are Content (XHTML), Presentation (CSS) and Behavior (Scripts). Content is king, it should never be jeopardized. Presentation is for looks, however, if CSS fails, the site should still be functional. The last one is Behavior. A failed script should never through errors, and it should never disable the site. If it is so important, it should state the requirements on the page.

I will look at the code, but I suggest you rethink your design.

---

### Post by LaRoza on 2008-04-12
Back. The site also fails in Opera. It should be redesigned. Working in one browser is a sign of a problem, not a sign of problems with the browser.

---

### Post by ipaqman23 on 2008-04-12
Ok, thank you!

---

### Post by pmasiar on 2008-04-12
Often this kind of browser compatibility problems can be solved by using JS library, instead of direct JS calls. jQuery is rather popular.

---

### Post by LaRoza on 2008-04-12
> **pmasiar said:**
> Often this kind of browser compatibility problems can be solved by using JS library, instead of direct JS calls. jQuery is rather popular.

JQuery is being used.

The site doesn't degrade gracefully, so it should be rethought for usabilities sake.

---

### Post by ipaqman23 on 2008-04-25
So,

thanks for your help! 

I now made "Javascript enabled" a requirement! 

Do you have any suggestions or improvements? Or is this too offtopic?

---

