---
title: "tutorial on audacity language."
date: 2008-08-25
forum: Programming Talk
---

### Post by cmay on 2008-08-25
hi .
i was looking for something on my old backup when i used windows and found my very first programs again.
its the built in language audacity uses. do anyone know what this language exactly is and is there any tutorials for it.
i made a lot of plugins for my selve and i posted what i think must be the first program i ever written.
how ever i am completly blank as how i found out how to do this in the first place and i want to start recording again and writing new plugins on linux.
thanks  
[PHP]
 ;nyquist plug-in

  ;version 1

  ;type process

  ;name "Delay..."

  ;action "Performing Delay Effect..."

  ;info "my echo gekko."  ; 

  ;control decay "Decay amount" int "dB" 6 0 24

  ;control delay "Delay time" real "seconds" 0.5 0.0 5.0

  ;control count "Number of echos" int "times" 5 1 30



  (defun delays (s decay delay count)

    (if (= count 0) (cue s)

	   (sim (cue s)

        (loud decay (at delay (delays s decay delay (- count 1)))))))

  (stretch-abs 1 (delays s (- 0 decay) delay count))
[/PHP]

---

### Post by Wybiral on 2008-08-25
It's some dialect of Lisp...

---

### Post by cmay on 2008-08-25
> It's some dialect of Lisp..
thanks do you know where i can find a tutorial on this dialect.
its been more than two years ago i started to code small plugins in audacity for some time but i never found any tutorial on it.
i had a small intro i found somewhere but i cant find it again.
not on audacitys webside either.
thanks for your time.

---

### Post by Wybiral on 2008-08-25
Google gives: [http://audacity.sourceforge.net/help/nyquist](http://audacity.sourceforge.net/help/nyquist)

---

### Post by Kadrus on 2008-08-25
> **cmay said:**
>  where i can find a tutorial on this dialect.

Well,I don't know if it would help with what you want.
But :[Practical Common Lisp]("http://www.gigamonkeys.com/book/") might help you out.
Take a look at the [Common Lisp Wiki]("http://www.cliki.net/index"),as it might be helpful as well.

---

### Post by cmay on 2008-08-25
> Google gives: [http://audacity.sourceforge.net/help/nyquist](http://audacity.sourceforge.net/help/nyquist)
can you acces the page . i cant it says page not found.
if you can then i have to be able to load the page too.

> 
Well,I don't know if it would help with what you want.
But :Practical Common Lisp might help you out.
Take a look at the Common Lisp Wiki,as it might be helpful as well. 
thanks. to be honest i did not know i was actually programming when i first learned a bit of this lisp dialect and and i dident even know up to know that it was lisp. its  along time since i used my recording studio but when i found this cd whit all that old stuff i thought i would ask. i will check out this page maybe i can find some tutorials there. 

thanks for your time.

---

### Post by Kadrus on 2008-08-25
Weird.The link works fine...try loading it again.

---

### Post by cmay on 2008-08-25
ok
i got it to work.
thank you both of you.:)

---

