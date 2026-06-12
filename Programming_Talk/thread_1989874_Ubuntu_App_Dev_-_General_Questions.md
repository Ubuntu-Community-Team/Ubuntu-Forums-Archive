---
title: "Ubuntu App Dev - General Questions"
date: 2012-05-28
forum: Programming Talk
---

### Post by amedrano on 2012-05-28
Don't know if this is the proper place for this type of stuff... please redirect me if its not...

I just finished writing my first Ubuntu App (PyGTK + Glade and Quickly) and I had some questions.


1) Where can I find the most up to date info regarding using PyGTK + Quickly/Glade to make Ubuntu apps
2) Is there any documentation about using HTML5 to make Ubuntu apps?
3) Is using Bazzar as a VCS  *required* for packaging or something or can I still use git? 
4) I'd like to contribute to Ubuntu app dev, maybe helping organizing the docs so it will be easier for developers to start (esp: Python). Any Recommendations?

Thanks

---

### Post by Cheesehead on 2012-05-28
> **amedrano said:**
> 3) Is using Bazzar as a VCS  *required* for packaging or something or can I still use git?
Use any VCS you wish, and any project manager/bug tracker you wish. Bazaar is sponsored by Canonical, and so is quite integrated into Launchpad. Using Bazaar and Launchpad offer some cool benefits, like easy PPA creation and distributuon. But neither Bazaar nor Launchpad are required. 
 

> **amedrano said:**
>  4) I'd like to contribute to Ubuntu app dev, maybe helping organizing the docs so it will be easier for developers to start (esp: Python). Any Recommendations?
Start with [http://wiki.ubuntu.com](http://wiki.ubuntu.com)
Also look at [http://developer.ubuntu.com](http://developer.ubuntu.com)
One of the best ways to contribute to development is to find unpatched bugs in Launchpad or unpatched opportunities in Harvest. Triaging bugs will teach you a lot about the community and the Ubuntu systems. Patching bugs and Harvest items will teach you a lot about packaging, testing, the Ubuntu release cycle, and Ubuntu's relationships with upstream projects. Both will introduce you to developers who may share your interests.

---

### Post by PeterP24 on 2012-05-29
To answer:

> 2) Is there any documentation about using HTML5 to make Ubuntu apps?

I didn't know that you can write HTML5 as being platform dependent (in this case Ubuntu OS). I always thought that a web browser must adhere to the standards and if it is cross platform then writing HTML5 webpages would mean that you can render those on any platform your browser is ported on. I can only deal with HTML4. I heard rumours about HTML5 as a sort of a revolution in the markup languages field - but never tried it. But my original thought remains: why write HTML5 apps for a specific platform (if this is possible) when you can write for a much larger audience? 

> 4) I'd like to contribute to Ubuntu app dev, maybe helping organizing the docs so it will be easier for developers to start (esp: Python). Any Recommendations?

Same here - I am specialised on writing and organising documentation, albeit most of it is for my own use. My only advice - if you don't know, then you should learn how to modify wiki pages (it is trivial but the first look at the wiki markup may shock you).

---

### Post by amedrano on 2012-05-29
You can use HTML5 to make GUIs for ubuntu apps *I think* Check out the section where it says Languages and Platforms [http://developer.ubuntu.com/resources/platform/documentation/platform-diagram/](http://developer.ubuntu.com/resources/platform/documentation/platform-diagram/)

---

