---
title: "penalty for using meta/javascript redirect"
date: 2008-02-02
forum: Programming Talk
---

### Post by RocketRanger on 2008-02-02
Hi

I want to run a script which checks for javascript capability and the reloads the page with a token attached to the url so php can see if javascript is present or not.

Having read on various websites how to do redirects they all warn against both meta and javascript methods, claiming that search engines will penalize the site if a redirect if detected. However it is unclear if all redirects are penalized or just redirects to other domains.

Is anyone able to clarify this? Alternatively is there a way around this with a different technique?

---

### Post by Colonel Kilkenny on 2008-02-02
Edit. Forget this one, stupid idea.
Perhaps you should just use <noscript> and plan everything carefully..

Anyway, search engines do not like redirects.

---

### Post by xlinuks on 2008-02-02
I don't know, but I'm pretty sure that if you build your site to please your visitors you'll get lots of hits/visitors regardless of what kind of redirects you use. I mean you might spend a lotta time and there will still be no definitive answer that can prove it's 100% true, so I guess this should be one of the last questions to worry about (unless you have a special reason).

---

### Post by RocketRanger on 2008-02-02
No special reason. It's really more about vanity. I would just hate to be penalized for doing a check at the index page for added functionality. And since I don't of any other way to test for javascript before the page a rendered I'm more or less forced to use this approach.

---

### Post by aks44 on 2008-02-02
> **RocketRanger said:**
> And I definitely don't want to go into something like a <noscript> as that has been depricated

Proof please?

---

### Post by RocketRanger on 2008-02-02
> **aks44 said:**
> Proof please?

Dammit! I was wrong. I apologize about that. I have reading up on xhtml recently and was certain to have come across it but a quick check with w3c schools shows I was wrong in that claim. Sorry.

---

### Post by aks44 on 2008-02-02
No problem, it happens. ;)

Anyway, as far as I can think of the only way to achieve what you want is actually to use <noscript> tags.

IMHO the redirect "solution" is very bad, you should really write web pages that can handle both scenarios using the very same HTML / JS / CSS source. Your PHP code should not need to know whether the client has Javascript enabled, if it needs to then you're quite likely to have a design problem.

---

### Post by RocketRanger on 2008-02-02
The design should be sound enough. My problem is that I'm trying to create a slideshow where I want to first image to fade in. If javascript isn't present there is not problem. Php selects an image at random and uses that. If javascript is present however the slideshow begins and the images is changed every six seconds or so. 

If I try to manipulate the source with javascript after it's run the image will be visible for a split second second, then disappear only to fade in half a second later. Hardly elegant coding.

However, I think what I'm arriving at is just to place the first image and use js for the subsequent slideshow.

---

