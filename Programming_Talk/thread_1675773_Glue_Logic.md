---
title: "Glue Logic"
date: 2011-01-26
forum: Programming Talk
---

### Post by worksofcraft on 2011-01-26
I'm trying to work out a neat way to interface two totally different libraries: The idea is to select a particular color space and then have all the appropriate constants and methods for both libraries implicitly defined with the same symbols e.g.
```


//typedef agg::renderer_base<rgb_pixels> renderer_type; // color
typedef agg::renderer_base<gray_pixels> renderer_type; // monochrome

```

here libjpeg wants a symbol of enumerated type J_COLOR_SPACE to identify it as RGB or grayscale, while AGG has a template structure that defines a load more symbols and so I derive my pixel format classes from those.

Somehow it seems to work using an inline static function, but I'm not sure if this actually is legitimate or a contradiction in terms producing pointless function calls?

[php]
// jpeg supports rgb and grayscale
struct rgb_pixels: agg::pixfmt_rgb24 {
	inline static J_COLOR_SPACE jpeg_color() { return JCS_RGB; }
	enum { pixel_components = 3 };
	explicit rgb_pixels(rbuf_type& rb): agg::pixfmt_rgb24(rb) {}
};
struct gray_pixels: agg::pixfmt_gray8 {
	inline static J_COLOR_SPACE jpeg_color() { return JCS_GRAYSCALE; }
	enum { pixel_components = 1 };
	explicit gray_pixels(rbuf_type& rb): agg::pixfmt_gray8(rb) {}
};
[/php]

Is there a more straight forward way to define symbolic constants for jpeg_color and pixel_components appropriate to the chosen color_space?

---

### Post by fct on 2011-01-26
I don't know how your full code is, or if I'm really answering your question at all.

Normally I'd settle for the most used API in the project and use its standards, then just write some "glue" functions when calling the "lesser" API that internally take care of the required conversions.

If you're using libjpeg just for saving and loading images, I'd just write functions for that purpose that isolate libjpeg's symbol usage to that code.

---

### Post by worksofcraft on 2011-01-26
> **fct said:**
> I don't know how your full code is, or if I'm really answering your question at all.

Normally I'd settle for the most used API in the project and use its standards, then just write some "glue" functions when calling the "lesser" API that internally take care of the required conversions.

If you're using libjpeg just for saving and loading images, I'd just write functions for that purpose that isolate libjpeg's symbol usage to that code.

Thanks, yes, sorry about the absence of full code... while it is operational it is kind of in an "experimental state" atm ;) Software library design methodology is still kind of new territory for me. :confused:

If I were just writing an application that uses both libraries I would do the same and move on, but this time I'm hoping to write a general purpose library that will be applicable for many different situations.

For instance "Out of the box" libjpeg provides conversion from it's internal YCbCr color space to popular formats which are all well and good for writing games for systems like X11 that render to the screen using plain RGB, but other sorts of applications need to [manipulate higher quality images]("http://jpeg2bw.sourceforge.net/").

I want to achieve that the only compile time option that the application programmer should have to consider is what color space his/her application wants to work with.

I'm hoping then to use templates to ensure the compiler selects appropriate conversion facilities, not only for rendering to the screen (as is currently implemented in AGG) but also for I/O to libjpeg and later for libpng also.

In my example, selecting a pixel format that is not supported by libjpeg simply results in a compile time error, (because it won't be defining a J_COLOR_SPACE converter). Similarly trying to choose a YCbCr pixel format won't compile because AGG has no blending capabilities for it.

I'm looking for generic ways to be able to easily add such facilities, not by branching the underlying source library code but by extending their base classes. Hence my extended pixel format classes which can plug in directly to the AGG templates as well as my libjpeg read and write methods at compile time to produce the desired code.

One thing I realize from what you wrote is that there is a danger that my header files will end up sucking in all the header files of all the other libraries and that won't be a good design either :(

---

### Post by worksofcraft on 2011-01-26
Incidentally I did try building that [jpeg2bw]("http://jpeg2bw.sourceforge.net/") example as it looked very interesting...

Alas right from the start I got problems with conflicting shared object library versions. Building against the static library produced a load of errors about the versions of yet other libraries and so on.

I also had to install the developer version of libguile which appears to be some kind of "scheme extension programming language". That too produced a raft of unresolved symbols to do with threaded applications... as if concurrent threads would serve any purpose what so ever in converting color jpeg to high resolution black and white :confused:

Eventually I managed to make it compile by messing about symbolic file links for the shared objects. And it converted the provided color picture as you can see in the folder view... however my default image viewer can't open it so there is some other kind of jpeg compatability problem here.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182036&stc=1&d=1296088112[/IMG]

I had a look in the source code but tbh I really wonder what all this kind of malarkey is about:
```

    if(strcmp(argv[i],"--circle1")==0) {
      curve = scm_c_eval_string("(lambda (n) (sqrt (- 1 (let (( x (- 1 n))) (* x x)))))");
      continue;
    }
    if(strcmp(argv[i],"--quarters0")==0) {
      curve = scm_c_eval_string("(lambda (n) (let* (( x (- n .5)) (z (sqrt (- .25 (* x x))))) (if (< n .5) z (- 1 z))))");
      continue;
    }
    if(strcmp(argv[i],"--quarters1")==0) {
      curve = scm_c_eval_string("(lambda (n) (if (< n .5) (- .5 (sqrt (- .25 (* n n)))) (let ((x (- 1 n))) (+ .5 (sqrt (- .25 (* x x)))))))");
      continue;

```

There is me thinking it was a C program :shock:

Now you may be wondering why I don't simply make do with the 8 bit grayscale that both libjpeg and AGG cater for by default?

I'm trying to avoid being **confined to the lowest common denominator**... I can see that when applying gamma corrections to high quality images we really DO want to have more depth in the dark shadows and a format that uses floating point pixel components would be a perfect test case :)

sigh - looks like I'll have to write my own - as usual.

---

### Post by fct on 2011-01-27
Uh, according to that error message the jpeg header isn't even there.

Wouldn't it be easier to use SDL + SDL_Img and use direct pixel access to perform conversions? There is also the GEGL library used in Gimp.

---

### Post by nvteighen on 2011-01-27
> **worksofcraft said:**
> 
I also had to install the developer version of libguile which appears to be some kind of "scheme extension programming language". That too produced a raft of unresolved symbols to do with threaded applications... as if concurrent threads would serve any purpose what so ever in converting color jpeg to high resolution black and white :confused:

Eventually I managed to make it compile by messing about symbolic file links for the shared objects. And it converted the provided color picture as you can see in the folder view... however my default image viewer can't open it so there is some other kind of jpeg compatability problem here.


I had a look in the source code but tbh I really wonder what all this kind of malarkey is about:
```

    if(strcmp(argv[i],"--circle1")==0) {
      curve = scm_c_eval_string("(lambda (n) (sqrt (- 1 (let (( x (- 1 n))) (* x x)))))");
      continue;
    }
    if(strcmp(argv[i],"--quarters0")==0) {
      curve = scm_c_eval_string("(lambda (n) (let* (( x (- n .5)) (z (sqrt (- .25 (* x x))))) (if (< n .5) z (- 1 z))))");
      continue;
    }
    if(strcmp(argv[i],"--quarters1")==0) {
      curve = scm_c_eval_string("(lambda (n) (if (< n .5) (- .5 (sqrt (- .25 (* n n)))) (let ((x (- 1 n))) (+ .5 (sqrt (- .25 (* x x)))))))");
      continue;

```

There is me thinking it was a C program :shock:


That's Scheme (a Lisp dialect) embedded into C via Guile. There are several programs using Scheme as scripting language, GIMP being the most notable example (it also uses Python). 

As you can imagine, I haven't read that program's source code, but what they seem to do is to define different kinds of curves as anonymous functions (lambdas)... I guess they call (apply) those lambda functions when drawing those curves or something.

About your general problem:
I've been researching about AGG and I think you're missing its point. Have you tried using its template-based generic interface? It seems AGG is designed in a very modular fashion that allows everyone extend its functionality...

---

### Post by worksofcraft on 2011-01-27
> **nvteighen said:**
> That's Scheme (a Lisp dialect) embedded into C via Guile. There are several programs using Scheme as scripting language, GIMP being the most notable example (it also uses Python). 

As you can imagine, I haven't read that program's source code, but what they seem to do is to define different kinds of curves as anonymous functions (lambdas)... I guess they call (apply) those lambda functions when drawing those curves or something.

About your general problem:
I've been researching about AGG and I think you're missing its point. Have you tried using its template-based generic interface? It seems AGG is designed in a very modular fashion that allows everyone extend its functionality...

I think they are applying those curves in converting color space. From what I can gather, simply linear averaging of the RGB values produces very grainy stepped results in dark areas... all very well for a quick and dirty conversion but not quite photographic quality. It did however put me off trying follow the code :(

AGG templates are all about rendering and blending images in memory with all sorts of pixel formats but has not a lot for transferring the results to or from files other than raw .ppm and .bmp forms. Application programs that want to use the capabilities of AGG need ways to get data in and out from more popular image formats like jpeg and png.

An alternative might be to extend the capabilities of AGG to support the native YCrCb pixel format that underpins the jpeg standard, but I'm still looking at how to integrate different color space converters.

---

### Post by worksofcraft on 2011-01-27
> **fct said:**
> Uh, according to that error message the jpeg header isn't even there.

Wouldn't it be easier to use SDL + SDL_Img and use direct pixel access to perform conversions? There is also the GEGL library used in Gimp.

I'm not sure where the jpeg header would have gone, but I wouldn't have thought the image icon in the folder would have displayed correctly if that was missing completely :shock:

Anyway you are probably right that SDL does provide facilities for this, but I get the impression that SDL is quite a comprehensive package that aims to cater for the complete set of graphics manipulation needs that an application programmer might have.

That black and white converter article I was playing with shows how the conversion in Gimp is limited and that is due to conversion algorithms adopted in it's libraries, choosing the library forces me to use the supplied integral converters of that library.

OTOH AGG is aimed purely at rasterizing and blending images in memory. It isn't intended as a complete package but as a building block that can be used in conjunction with other independent building blocks... like libjpeg.

I suppose it's a different approach and what I appear to be studying is how to use such independent software tools together:
Not being forced to find the lowest common denominator but by adding and extending the "glue logic" that binds then together ;)

---

