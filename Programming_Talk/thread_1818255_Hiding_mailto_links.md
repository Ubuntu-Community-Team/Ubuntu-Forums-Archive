---
title: "Hiding mailto links"
date: 2011-08-04
forum: Programming Talk
---

### Post by nmaster on 2011-08-04
Not sure if this should have gone in "Programming" or "Security"... feel free to move it if necessary.

i need to post contact information on a website, but i want to protect it from spambots. i originally posted email address formatted like "johnDoe[AT]blah.net" (just replace '@' with '[AT]').  some thought that this made things less convenient for users (which is true).

i've started to use the mail2() javascript function given here: [http://www.bronze-age.com/nospam/](http://www.bronze-age.com/nospam/) 
i haven't added it yet, but i'll need to put a <noscript> tag with my first solution as a fallback.

is this good enough? i've also read about using php to convert the plain text into ASCII codes with mb_convert_encoding() and a couple of other things so i'm not sure what is best.

---

### Post by wojox on 2011-08-04
You could always use an image as well.

---

### Post by SoFl W on 2011-08-04
You could have the visitor fill out a form and have the form data sent to the intended email address.

---

### Post by nmaster on 2011-08-04
> **wojox said:**
> You could always use an image as well.
doesn't solve the problem.  using an image wouldn't prevent a mailto link from being in the HTML

---

### Post by Bachstelze on 2011-08-04
Just get a good antispam and put your email address unobfuscated. :)

---

### Post by nmaster on 2011-08-04
> **SoFl W said:**
> You could have the visitor fill out a form and have the form data sent to the intended email address.
i guess this would require a reCAPTCHA though... i personally find reCAPTCHAs annoying but this is another option i've considered

---

### Post by nmaster on 2011-08-04
> **Bachstelze said:**
> Just get a good antispam and put your email address unobfuscated. :)
and the best way to prevent pick-pockets is to walk around with C-notes in one open palm and a Bible in the other.

;)

---

### Post by Bachstelze on 2011-08-04
> **nmaster said:**
> and the best way to prevent pick-pockets is to walk around with C-notes in one open palm and a Bible in the other.

;)

Mock if you want. That's what I do, and it works very well. Good luck with your convoluted solution. :)

---

### Post by nmaster on 2011-08-04
> **Bachstelze said:**
> Mock if you want. That's what I do, and it works very well. Good luck with your convoluted solution. :)
well that would probably work well if it was my own email address.  since this is contact info for other people, i think i should be more careful about it. i did once put up a raw mailto link... i did receive an irate email asking for it to be taken down.

---

### Post by nmaster on 2011-08-04
> **Bachstelze said:**
> Just get a good antispam and put your email address unobfuscated. :)

lol, i also just realized how severely this contradicts your signature.  unless of course, you write antispam software yourself, in which case, you are totally legit and you deserve a gold star: :KS

---

