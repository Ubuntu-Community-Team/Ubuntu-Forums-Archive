---
title: "Libreoffice and Japanese Problem"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by WongFuChu on 2012-08-26
I don't know what happened; before, when I imported japanese text or wrote japanese via ibus into any libreoffice application, it would show correctly. Now, for some reason, it doesn't work and it only shows boxes rather than characters. In Libreoffice calc, I do see the actual Japanese text (btw, I do have the language installed on my system). Libreoffice changes the font automatically to droid sans. I don't remember the font that was used before, sorry. Is there a way to set the default text for japanese characters (at least change the choice of droid sans to droid sans japanese)?

---

### Post by Peter Maunder on 2012-08-30
There are four main areas where you may be having a Japanese font problem with Writer. I hope the following may be useful in your particular case.
 

        1. The Overall LibreOffice Language settings.
  2. The LibreOffice 	Writer setting
  3. The paragraph 	style settings and
  4. Directly in the 	document itself.

[LIST=1]
[*]Language Settings
 	Tools >> Options 	>> Language Settings >> Languages
[/LIST]
 Select > Enabled for Asian languages
 Select > Japanese as Asian default language, and then OK.
     When you reselect language settings you will be given two further options
 	Searching in Japanese and Asian Layout. You are on your own with these.

   
 
    
      2	Then select Tools >> Options >> LibreOffice Writer >> Basic Fonts (Asian)
 	Make certain the defaults fonts you choose support Japanese.
 

 …..3.	If the problem is the Default font in the individual document Paragraph setting    PF11 >> Paragraph Styles >> Default >> right mouse (Modify)
 			and again select a Japanese supported Font.
 

 
[LIST=1]
[*]If the problem is just in the 	document itself change the font. If the font entry field is not showing  View >> toolbars >> formatting will display the option.  Change the font and there you are! Good luck

[/LIST]
References Libreoffice 3 Writer Guide,  Free PDF download or paper copy from Lulu.

---

