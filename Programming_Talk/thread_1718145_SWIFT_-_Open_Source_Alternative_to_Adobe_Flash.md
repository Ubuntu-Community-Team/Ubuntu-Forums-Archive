---
title: "SWIFT - Open Source Alternative to Adobe Flash"
date: 2011-03-30
forum: Programming Talk
---

### Post by skykooler on 2011-03-30
I was rather disappointed to learn that there wasn't an open-source alternative to Adobe Flash like there is GIMP for Photoshop. So, I decided to create one myself. It is currently in heavy development, but I intend to release the beta soon. It uses swfc for compiling, and Python/Cairo for almost everything else.
Currently implemented features:
[LIST]
[*]Export programmed SWF content.
[*]Export programmed HTML5 content. I have written an Actionscript wrapper in JavaScript, so there is no need to re-write code.
[*]Animated objects (currently only motion tweens)
[*]Buttons
[*]Export Images (currently only PNG)
[*]Export Animated GIFs
[*]Export Video: support for all ffmpeg-supported codecs, which is quite a lot!
[*]Export PDF
[*]Import images (currently only PNG)
[*]Support for dynamic plugins (using external Python modules)
[/LIST]

And a screenshot:

---

### Post by ChipOManiac on 2011-03-30
Sweet man! Great job trying to get something like this up and running... :)

---

### Post by rg4w on 2011-03-31
Looks really nice.  Got a donation page?  Looks like a project well worth encouraging.

---

### Post by skykooler on 2011-03-31
UPDATE: I have now got movie clips (sprites) working!

---

### Post by skykooler on 2011-04-02
Update: I have now got miscellaneous shapes drawing properly, and added rotation support. I intend to release the beta within the next few days.

---

### Post by hakermania on 2011-04-02
Nice! Keep it up!

---

### Post by Malcy on 2011-04-02
Cool, I will be watching your progress with interest. :)

---

### Post by Telengard C64 on 2011-04-02
What about your project makes it different from or better than [gnash](http://www.gnashdev.org/)?

---

### Post by skykooler on 2011-04-02
> **Telengard C64 said:**
> What about your project makes it different from or better than [gnash](http://www.gnashdev.org/)?

I believe you may misunderstand me. Adobe makes two SWF related tools: Adobe Flash and Adobe Flash Player. Flash is used to *create* the content; Flash Player is used to *play* the content. Gnash is an alternative to Flash Player, while Swift is an alternative to Flash.
Swift actually uses Gnash for playback of SWFs, as it logs trace messages (which the Flash Player browser plugin does not).

---

### Post by Telengard C64 on 2011-04-03
Thanks for clearing me up on that  :)

---

### Post by JanuaryJones on 2011-04-04
Great! We really need a good alternative to Adobe Flash!

---

### Post by skykooler on 2011-05-28
I have made a blog. [http://swift-swf.blogspot.com]("http://swift-swf.blogspot.com")

I will post progress updates here.

---

### Post by skykooler on 2011-10-09
I have finally released the alpha! Testers wanted. Please note that many key functions are still in development; in particular the drawing tools are not working (besides rectangles). However, this still allows for animation via image-based sprites.

Download from here: [https://launchpad.net/~skykooler/+archive/swift-swf]("https://launchpad.net/~skykooler/+archive/swift-swf")

Also, I have a donate button on [my blog]("http://swift-swf.blogspot.com/") if you like where this is going.

---

### Post by hakermania on 2011-10-09
> **skykooler said:**
> I have finally released the alpha! Testers wanted. Please note that many key functions are still in development; in particular the drawing tools are not working (besides rectangles). However, this still allows for animation via image-based sprites.

Download from here: [https://launchpad.net/~skykooler/+archive/swift-swf]("https://launchpad.net/%7Eskykooler/+archive/swift-swf")

Also, I have a donate button on [my blog]("http://swift-swf.blogspot.com/") if you like where this is going.

Hey, great work, keep it up. Just you need to make it look very professional and so you need to be a bit typical and careful. For example, I just noticed a typo in launchpad:
```
(currently vey basic)
haven\'t

```Also, you mention that you don't know how to add these (the gnash etc) as Dependencies to the program. Well, this is being done through the 'debian/control' file in the 'Depends' field. An example is: [http://paste.ubuntu.com/704783/](http://paste.ubuntu.com/704783/)

Good luck.

---

### Post by skykooler on 2011-10-09
> **hakermania said:**
> Hey, great work, keep it up. Just you need to make it look very professional and so you need to be a bit typical and careful. For example, I just noticed a typo in launchpad:
```
(currently vey basic)
haven\'t

```Also, you mention that you don't know how to add these (the gnash etc) as Dependencies to the program. Well, this is being done through the 'debian/control' file in the 'Depends' field. An example is: [http://paste.ubuntu.com/704783/](http://paste.ubuntu.com/704783/)

Good luck.

Thank you. I haven't updated the Launchpad description in a while; I actually do have those as dependencies now.

---

### Post by t3h m00kz on 2011-10-10
When I run the .deb file, I get this:

```
Error: Dependency is not satisfiable: swftools
```

I'm a nub at linux. Any ideas?

---

### Post by skykooler on 2011-10-11
> **t3h m00kz said:**
> When I run the .deb file, I get this:

```
Error: Dependency is not satisfiable: swftools
```

I'm a nub at linux. Any ideas?

If it complains that swftools isn't in the repository, download my package from here: [i386]("https://launchpad.net/~skykooler/+archive/swift-swf/+files/swftools_1.0-1_i386.deb") or [amd64]("https://launchpad.net/~skykooler/+archive/swift-swf/+files/swftools_1.0-1_amd64.deb").

---

### Post by skykooler on 2011-10-12
Update: SWIFT is now cross-platform, more or less. I have got it to *run* on both Windows and Mac, and to compile SWFs on Mac, but I haven't got either of them to play them back yet. That will come though.
Has anybody tested it yet? I know it is mostly bugs right now, but I can't find all of them myself.

---

