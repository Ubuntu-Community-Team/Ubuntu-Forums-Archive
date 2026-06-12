---
title: "Python and JavaScript (?) - I find it difficult to make the title more specific"
date: 2011-09-04
forum: Programming Talk
---

### Post by navneeth on 2011-09-04
Hi,
 **Disclaimer: I'm not a web-developer, so apart from the basics of HTML, XML and JS, I'm pretty much a blank slate on this topic.**

Here's what I want to do: get the information on the currently playing track from my music player and then print it as part of my signature in a forum post.

The first and simplest part has been taken care of (in Python -- the info. is stored in a text file), but I don't know how to do the second, if it can be done at all; i.e. somehow automatically print this information when I make a forum post. (I read that executing system/application commands from JavaScript is not advisable, since it's a security risk, so I haven't bothered to do the whole thing in JS. Let me know if I'm mistaken.)

I came across the Pyjamas project, but I'm unsure, even after reading their FAQ, if that is what I'm looking for. Therefore, I would appreciate any advice on this issue.

I currently use Firefox 3.6.21 on Maverick, if that helps.

Thanks.

---

### Post by SecretCode on 2011-09-04
The (vBulletin) forum side of this may not be what you expect ... you only have one signature & it displays in all your posts. Do you want that, or do you want the currently playing track to be inserted in the body of a new post? There's no way to automate that in vBulletin, but if you're prepared to use a hotkey it would be fairly simple in bash using the xte command (from the xautomation package) to type keystrokes into your posting.

If you really want it in your signature, you can only call javascript from your signature text if you are allowed to call html, and I don't think general users here are. Second problem would be that the javascript running on anyone else's machine has no access to your machine (I hope!) - you would have to save the currently playing track info to a publicly accessible web server.

---

### Post by juancarlospaco on 2011-09-04
Make Python do a JPG image file, always with the same name, on a Public URL,
then link your signature to that image, you dont even need JS there...

---

### Post by navneeth on 2011-09-04
> **SecretCode said:**
> The (vBulletin) forum side of this may not be what you expect ... you only have one signature & it displays in all your posts. Do you want that, or do you want the currently playing track to be inserted in the body of a new post? There's no way to automate that in vBulletin, but if you're prepared to use a hotkey it would be fairly simple in bash using the xte command (from the xautomation package) to type keystrokes into your posting.

If you really want it in your signature, you can only call javascript from your signature text if you are allowed to call html, and I don't think general users here are. Second problem would be that the javascript running on anyone else's machine has no access to your machine (I hope!) - you would have to save the currently playing track info to a publicly accessible web server.

It's not for this forum but another which uses Simple Machines. (But doesn't mean I have access to run scripts form the signature.)

As for your question, I suppose I wouldn't mind it at the bottom of the body of the text. I'll take a look at xte.

> **juancarlospaco said:**
> Make Python do a JPG image file, always with the same name, on a Public URL, then link your signature to that image, you dont even need JS there...

That's a nice idea... I will try that also.

Thanks, both of you.

---

### Post by SecretCode on 2011-09-04
> **juancarlospaco said:**
> Make Python do a JPG image file, always with the same name, on a Public URL,
then link your signature to that image, you dont even need JS there...

That's a brilliant solution.

But I'd suggest a PNG for better font sharpness.

---

### Post by juancarlospaco on 2011-09-04
I suggest a[ WebP ]("http://code.google.com/speed/webp/")for better font sharpness and size.

---

### Post by SecretCode on 2011-09-04
I stick with my PNG suggestion since afaik only Chrome and Opera of the major browsers support it. :)

---

### Post by hakermania on 2011-09-04
> **juancarlospaco said:**
> Make Python do a JPG image file, always with the same name, on a Public URL,
then link your signature to that image, you dont even need JS there...


[spam]Hey, this is just like how Wallch live earth works ;)[/spam]

I suggest making the image using imagemagick, it's brilliant on writing text!
EDIT: BTW I do not suggest putting the image in Dropbox Public folder as it allows only 10GB of file transfers and if the forum is busy..... you got me

Here: [http://www.imagemagick.org/Usage/text/](http://www.imagemagick.org/Usage/text/)

---

### Post by juancarlospaco on 2011-09-04
> **SecretCode said:**
> I stick with my PNG suggestion since afaik only Chrome and Opera of the major browsers support it. :)

[Wrong you are.]("http://antimatter15.github.com/weppy/demo.html")

---

