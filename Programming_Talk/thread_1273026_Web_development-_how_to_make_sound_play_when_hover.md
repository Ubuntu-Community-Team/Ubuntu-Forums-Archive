---
title: "Web development- how to make sound play when hover over a link"
date: 2009-09-22
forum: Programming Talk
---

### Post by lightningfox on 2009-09-22
Hello

I'm practicing web design.

So far I know HTML, CSS, and a little Javascript.

I want to know if there is a way to make a sound play when I hover over a link in a webpage I'm creating, using Javascript.

Please tell me if there is and how to do it.

---

### Post by hessiess on 2009-09-23
With the up cumming HTML5 standard this will be possible, however currently it is not. You may be able to achieve something with Flash.

---

### Post by StunnerAlpha on 2009-09-23
When is HTML 5 due to become the new standard?

---

### Post by CptPicard on 2009-09-23
Please consider that web pages making noises is generally very, very bad design... you better have a very good reason to want to do this.

---

### Post by froggyswamp on 2009-09-23
> **CptPicard said:**
> Please consider that web pages making noises is generally very, very bad design... you better have a very good reason to want to do this.

+1
It's also old fashioned and just annoying the majority of users.

---

### Post by Ascenti0n on 2009-09-23
> **CptPicard said:**
> Please consider that web pages making noises is generally very, very bad design... you better have a very good reason to want to do this.

As a full-time web developer, I particularly agree with the above quote, it doesn't answer your question.

Let me point you in the right direction:

You need to use 'onMouseOver' within yout <A> tag, but you will also need some javascript too.

I'd advise not doing it, as most people find this sort of thing more of an annoyance and it shouts AMATEUR.

Good luck

---

### Post by hessiess on 2009-09-23
> **CptPicard said:**
> Please consider that web pages making noises is generally very, very bad design... you better have a very good reason to want to do this.

Agree, but it doesn't answer the question. I find any computer which makes any sounds besides some music that I put on deliberately to be extremely annoying, First thing I do if I have to  use a `default configuration' XP machine for some reason is mute it.

> 
When is HTML 5 due to become the new standard?

When its ready (tm). Parts of the working draft for the standard have already bean implemented in Firefox and Opera, but it is not standardised across browsers.

---

### Post by Reiger on 2009-09-23
It is actually possible. Many embedded players have a JavaScript API; the following spring to mind:

-VLC,
-Youtube's flash app (many other, similar players exist; APIs may differ)
-MPlayer
-Windows Media Player
-Real Player
-Quicktime

If this site is for personal use (e.g. a personal media gallery) or is used in an environment where you can reasonably expect/enforce certain software to be available (i.e. VLC) you can simply write a JavaScript wrapper around the appropriate APIs to invoke the right commands and configure/convert parameters as necessary.

---

### Post by TheBuzzSaw on 2009-09-23
Do not add sound to your site.

---

### Post by ve4cib on 2009-09-23
I'll echo the general tone of the replies so far in saying that you should not add unnecessary sounds to your web page with the following caveat:

There are very rare circumstances where having sounds on a website is actually desirable (or at the very least acceptable and understandable).  Good example of this would be a musician with a built-in media player showcasing their work.  Or if you have MP3s for download and you advertise that "you can hover over the link to hear a short preview."  Or obviously if your site is dedicated to streaming audio in some way/shape/form.

Now, assuming that you have a *damned good reason* for inflicting your sound effects on the internet at large there are several possibilities.  The easiest would probably be to use Flash or Silverlight/Moonlight (though given those choices I'd go for Flash -- it's more widely-supported).

Another option would be to embed the audio file using an <embed> tag and set the mimetype appropriately.  You'd need to play around with the Javascript required to play and pause/stop the sound (I can't help you there), but it should be doable.  Worst-case you just constantly add and remove the embed element from the page to make the sound play or stop.  It'd be slow and hacky, but it might work.

Anyway, as mentioned above you'll need use the onmouseover and onmouseout events to hook the sounds up:

```

<div onmouseover="playHoverSound()" onmouseout="stopHoverSound()">
    ...
</div>

<script type="text/javascript>
function playHoverSound() {
    // TODO: fill this in to play the sound
    ...
}
function stopHoverSound() {
    // TODO: fill this in to stop the sound
    ...
}
</script>

```

---

### Post by A_Fiachra on 2009-09-23
> **cptpicard said:**
> please consider that web pages making noises is generally very, very bad design... You better have a very good reason to want to do this.
+2

---

### Post by lightningfox on 2009-09-23
Thank you for your replies.

And your advice to not use sounds on web pages unless necessary.


Right now I'm making a local website on my computer for practcing my web design skills, and am not planning to upload it to the internet yet.

But when I do create an online wbsite I'll follow your advice of not putting sounds on webpages.

---

### Post by nmccrina on 2009-09-23
> **lightningfox said:**
> 
But when I do create an online wbsite I'll follow your advice of not putting sounds on webpages.

ZOMG!!! We have a listener :P
:lolflag:

---

### Post by JimFuqua on 2009-10-14
Sounds on web pages are often annoying, but there are pages where sounds are appropriate.

Educational pages for children who do not read are of very limited use without sound.

For adults some studies have shown that retention is greater when the student both reads and hears the information spoken.

How would you build a web site to teach a foreign language efficiently without sound?  

Web dictionaries that have sound sometimes take more than one click to hear the proper pronunciation.  Would not on hover or mouseover be better?

I am still looking for a convenient way to do sound on hover.  People who condemn using sound without knowing the use are being both dogmatic and off topic.  The topic is "how to" not "whether".

---

### Post by TheBuzzSaw on 2009-10-15
> **JimFuqua said:**
> I am still looking for a convenient way to do sound on hover.  People who condemn using sound without knowing the use are being both dogmatic and off topic.  The topic is "how to" not "whether".

Considering that 9 times outta 10 the person just wants to add gimmicky sound, it is quite natural to add a voice of warning. We're not saying, "We will not help you no matter what." We're trying to prevent unnecessary work by simply saying that sound is often unnecessary. With that said, if he still wants sound, we're more than happy to provide the techniques.

Also, since *we* are the ones willing to take the time to explain the process, we reserve every right to question the use of the sound. It's not that complicated. :-/

---

