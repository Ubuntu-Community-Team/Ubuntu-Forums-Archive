---
title: "[RubyOnRails] Looking for an applications to look at"
date: 2007-12-29
forum: Programming Talk
---

### Post by hechizera on 2007-12-29
hi there!

Does anyone have an application created in ruby on rails, preferably with such functions as login/logout, signup, salted passwords and maybe something else. I just want to look at how does it work, I'm not looking for some huge applications, I want a small one, which would have those functions I mentioned before. Could you share a link please?

---

### Post by hechizera on 2007-12-30
noone knows rails or what? :(

---

### Post by quedigg on 2007-12-30
hi,
InstantRails (RoR stack for windows) includes 2 apps : cookbook and Typo(blogging engine). cookbook will be great for starters.

if using on ubuntu ,i hope so ;) , get the cookbook app from [here]("http://www.onlamp.com/onlamp/2005/03/03/examples/cookbook_part1_0.13.1.zip") ,then run it using mongrel command line (please stuck always with command line ).

Thanks,
que0x

---

### Post by hechizera on 2007-12-30
hi quedigg!
thanks for the example! maybe you know some more examples, so that there would be login and signup functions too?

---

### Post by quedigg on 2007-12-30
use the [LoginGenerator]("http://wiki.rubyonrails.org/rails/pages/LoginGenerator") ,the easiest way to get accounts on a website :)

---

### Post by hechizera on 2007-12-30
looks interesting, but still I wouldn't mind to see this in practice, I mean in application... does  this generator salt passwords?

---

### Post by quedigg on 2007-12-30
yep, [here]("http://wiki.rubyonrails.com/rails/pages/SaltedHashLoginGenerator")

---

### Post by Modred on 2007-12-30
I've had a good experience with [acts_as_authenticated](http://wiki.rubyonrails.com/rails/pages/Acts_as_authenticated), which apparently forked from LoginGenerator.

---

