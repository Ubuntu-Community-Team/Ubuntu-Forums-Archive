---
title: "CSS @font-face problems"
date: 2011-11-11
forum: Programming Talk
---

### Post by WebDrake on 2011-11-11
Hello all,

I'm trying to set up my website css to load specified fonts using the @font-face tag.

I've downloaded a kit from Font Squirrel which I then tweaked according to the instructions here:
[http://stackoverflow.com/questions/2436749/how-to-define-bold-italic-using-font-face](http://stackoverflow.com/questions/2436749/how-to-define-bold-italic-using-font-face)

Unfortunately I'm running into browser-dependent problems.  Firefox (7.0.1) prints all text as Italic.  Rekonq fails to apply _any_ text formatting (bold, italic) even where it's requested, and will not print certain special characters using the font.  Only Chromium seems to get everything right.

I've posted the @font-face CSS below.  Are there any definite errors in it which could be causing the above problems?  Or is this just the wrong way to approach embedding fonts in a webpage via CSS?

Thanks in advance for any advice.

```
@font-face {
    font-family: 'WebFontSerif';
    src: url('fonts/linlibertine_re-4.7.5ro-webfont.eot');
    src: url('fonts/linlibertine_re-4.7.5ro-webfont.eot?#iefix') format('embedded-opentype'),
         url('fonts/linlibertine_re-4.7.5ro-webfont.woff') format('woff'),
         url('fonts/linlibertine_re-4.7.5ro-webfont.ttf') format('truetype'),
         url('fonts/linlibertine_re-4.7.5ro-webfont.svg#LinuxLibertineORegular') format('svg');
}

@font-face {
    font-family: 'WebFontSerif';
    src: url('fonts/linlibertine_bd-4.1.5ro-webfont.eot');
    src: url('fonts/linlibertine_bd-4.1.5ro-webfont.eot?#iefix') format('embedded-opentype'),
         url('fonts/linlibertine_bd-4.1.5ro-webfont.woff') format('woff'),
         url('fonts/linlibertine_bd-4.1.5ro-webfont.ttf') format('truetype'),
         url('fonts/linlibertine_bd-4.1.5ro-webfont.svg#LinuxLibertineOBold') format('svg');
    font-weight: bold;
}

@font-face {
    font-family: 'WebFontSerif';
    src: url('fonts/linlibertine_it-4.2.6ro-webfont.eot');
    src: url('fonts/linlibertine_it-4.2.6ro-webfont.eot?#iefix') format('embedded-opentype'),
         url('fonts/linlibertine_it-4.2.6ro-webfont.woff') format('woff'),
         url('fonts/linlibertine_it-4.2.6ro-webfont.ttf') format('truetype'),
         url('fonts/linlibertine_it-4.2.6ro-webfont.svg#LinuxLibertineOItalic') format('svg');
    font-style: italic, oblique;
}

@font-face {
    font-family: 'WebFontSerif';
    src: url('fonts/linlibertine_bi-4.1.0ro-webfont.eot');
    src: url('fonts/linlibertine_bi-4.1.0ro-webfont.eot?#iefix') format('embedded-opentype'),
         url('fonts/linlibertine_bi-4.1.0ro-webfont.woff') format('woff'),
         url('fonts/linlibertine_bi-4.1.0ro-webfont.ttf') format('truetype'),
         url('fonts/linlibertine_bi-4.1.0ro-webfont.svg#LinuxLibertineOBoldItalic') format('svg');
    font-weight: bold;
    font-style: italic, oblique;
```

---

### Post by WebDrake on 2011-11-11
Whoops: how embarrassing, the answer is already there in the stackoverflow comment thread.

The CSS used here contains the line,
```
font-style: italic, oblique;
```
which is not compatible with Firefox: instead two different @font-face entries need to be created, one for font-style: italic and one for font-style: oblique.

---

