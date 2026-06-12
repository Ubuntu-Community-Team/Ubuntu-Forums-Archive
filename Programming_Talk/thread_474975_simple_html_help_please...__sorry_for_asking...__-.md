---
title: "simple html help please...  sorry for asking...  -blushes-"
date: 2007-06-15
forum: Programming Talk
---

### Post by locke.dragon on 2007-06-15
i've got a site where i want to have a little "sticker" display in the top right corner of the main window.

[www.paperclipsandscrambledeggs.blogspot.com](www.paperclipsandscrambledeggs.blogspot.com)

i already have a simple bit of code keeping it up there, but it kinda malfunctions when you resize the window.  is there any way i can just make it stay in the corner no matter what size the window/screen is?

here's the code i have now:

```

<img style="position:absolute; TOP:5px; LEFT:72%; WIDTH:148px; HEIGHT:148px" src="http://i159.photobucket.com/albums/t147/clipsandeggs/web2.png"/>

```

---

### Post by SoloSalsa on 2007-06-15
Maybe it is just for you.  Are you talking about the huge 'Web 2"?  Because that resizes into every position, just fine.

---

### Post by locke.dragon on 2007-06-15
yeah.  the web 2 thing.  if you try resizing the window, it stays at 72% percent the screen width when i only want it to stay in that one corner.  it also poses a problem if you have a computer monitor that's not 1280x800.

---

### Post by justin whitaker on 2007-06-15
Yeah, I think this is on your side, because I tried FF and IE and it works fine. 

Although I would drop the scrolling contact text. It's distracting, too fast, and messes up the minimalism of the design.

Otherwise, really nice!

---

### Post by Doovoo on 2007-06-15
Well, I'll just avoid criticizing the fact that it's a button that says Web2.0 and just assume it's meant to be ironic.

Anyway, it works okay for me, but it gets moved to the left a little bit on resizing because you're using position: absolute, which is usually not a good idea.  When you DO use it, you pretty much need to define it's position exactly with pixels, because that percentage you're using is relative.  

If it was me I'd use a float and some margins.

---

### Post by locke.dragon on 2007-06-15
how would i do the float with margins thing?

---

### Post by Doovoo on 2007-06-15
Well, it depends upon how the rest of your site is laid out and how dynamic you want it to be.  Basically, though, I'd make a wrapper for the entire layout and do a 

```

wrapper{
width: 100%;
margin: 0 auto 0 auto;
}

img.button{
width: 148px;
height: 148px;
float: right;
margin: 5px 0 0 0;
}

```

I feel like I'm probably getting a little ahead of you, though.  Look up some CSS guides.

Tizag's is probably pretty good (their tutorials usually are)
[http://www.tizag.com/cssT/](http://www.tizag.com/cssT/)

---

### Post by airtonix on 2007-06-15
Replace lines 1159 through to 1162 with this :  
* (i dont recommend using css inline with html but im only one person and i need to sleep so....im not going to bend your arm)*

> 
<div class="widget-content" style="position:fixed;top:5px;width:180px;">
 <img src="http://i159.photobucket.com/albums/t147/clipsandeggs/web2.png" style="float: right; display: inline; position: relative;"/>
</div>


---

### Post by Tundro Walker on 2007-06-15
Yeah, I think the W3C is poo-poo'ing on inline styles...they want everything handled through CSS going forward.

But, inline styles still work, and they'd be flippin stupid to force CSS upon everyone, seeing as how some folks don't know how to use it.  Tons of web-pages would no longer be "valid".  Silly.

Remember when HTML started out as a simple little language anyone could easily learn to make web-pages?  Now it's all techno-philed to the point where you have to be a programmer to do anything with it.  It started out to empower the common person, and now that power's being taken away.

---

### Post by RawMustard on 2007-06-15
Hmm!  Why not just position right instead of left: 72%?

```
<img style="position:absolute; TOP:5px; RIGHT:5px; WIDTH:148px; HEIGHT:148px" src="http://i159.photobucket.com/albums/t147/clipsandeggs/web2.png"/>
```

you could even give it a z-index so it doesn't effect other elements on the page :)

---

### Post by locke.dragon on 2007-06-15
yeah.  that didn't do anything.  it still re-positions each time i resize the screen.

---

### Post by RawMustard on 2007-06-16
did you try position: fixed;  Not sure if that will work in Infernal Exploiter though.

---

### Post by SoloSalsa on 2007-06-16
Oh, I think I just realized what you meant.  Do you want it to *always* look like picture one, in the right *corner*; or want it to be like picture two, where it floats to 72% of the screen?

---

### Post by locke.dragon on 2007-06-16
i want it to ALWAYS stay RIGHT in that one corner no matter what the screen size is.

---

### Post by tturrisi on 2007-06-17
This will do it:
```
  <div id='container'>
<img style="FLOAT:right; POSITION:relative; TOP:-40px; WIDTH:148px; HEIGHT:148px" src="http://i159.photobucket.com/albums/t147/clipsandeggs/web2.png"/>
    <!-- skip links for text browsers -->
    <span id='skiplinks' style='display:none;'>
      <a href='#main'>skip to main </a> |
      <a href='#sidebar'>skip to sidebar</a>
    </span>

    <div id='header1'>
      <div class='header section' id='header'><div class='widget Header' id='Header1'>
    <h1 class='title'>
      
        paperCLiPS & scrambledEGGs
      
    </h1>
    <h2>My place to write about anything and everything.</h2>
</div></div>

    </div>
```

If you don't want the image all the way in right corner then bump it left a bit with:
```
<img style="FLOAT:right; POSITION:relative; TOP:-40px; PADDING-RIGHT:20px; WIDTH:148px; HEIGHT:148px" src="http://i159.photobucket.com/albums/t147/clipsandeggs/web2.png"/>
```

---

### Post by locke.dragon on 2007-06-17
where am i supposed to put that?  i use blogger by the by...  strange interface...  :P

---

### Post by SoloSalsa on 2007-06-17
I was going to have a go at giving you a code, too.  But, I know nothing about blogger, and would not know what to tell you.  I might look into it if I finish my homework early...

---

### Post by tturrisi on 2007-06-18
> **locke.dragon said:**
> where am i supposed to put that?  i use blogger by the by...  strange interface...  :P

Put this:
```
<div style="width:200px; height:148px; float:right; text-align:right; position:absolute; top:0px;"><img style="width:148px; height:148px" src="http://i159.photobucket.com/albums/t147/clipsandeggs/web2.png"/></div>
```
in the same place & same way you put the existing code.  Just replace the existing with the above new code.

---

### Post by locke.dragon on 2007-06-18
thanks!  :)  i actually got it working, but i haven't posted it on the real site yet.  i'm messing with the test site i made (so if i screw up i don't destroy the real page.  :P )

---

