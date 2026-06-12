---
title: "newbie mono gtk# install probs"
date: 2005-09-19
forum: Programming Talk
---

### Post by vector on 2005-09-19
hi all
Im wanting to run skynet which requires mono and gtk#
I apt-get install mono
then  sudo apt-get install gtk-sharp-gapi
but got the error below when i tried to ./configure.pl in skynet

 ./configure.pl 
Looking for a suitable compiler...Looking for a suitable graphical toolkit...
Unable to find Gtk# or Qt# (using the gac)
You need one of these toolkits in order to build and run SkyNET
You can get them at [http://gtksharp.sourceforge.net](http://gtksharp.sourceforge.net) or [http://qtcsharp.sourceforge.net](http://qtcsharp.sourceforge.net)

i went to the above sites but learnt nothing
i did some more apt-cache searching and found this
and sudo apt-get install mono-gac

but same result.

what on earth do i need to compile this sucker??

thanks guys

---

### Post by m87 on 2005-09-19
apt-get install libgtk2.0-cil

---

### Post by vector on 2005-09-21
ok real close
./configure.pl worked fine with no errors
i typed "make" as directed it got half way thru and then  said
no package glade-sharp found.

I tried apt-cache search glade-sharp but found nothing
tried installing glade..didnt help
even tried libglade2.0-cil   :) hey worth a try.

---

### Post by m87 on 2005-09-21
apt-get install libglade2.0-cil

---

### Post by vector on 2005-09-21
> tried installing glade..didnt help
even tried libglade2.0-cil hey worth a try.
 erm
tried that it made no difference :( 

Im on holidays for two weeks now..looks like ill be without any skycharts :( thanks anyway
i may give it a go when i get back... kstars is just too big for this little laptop.
i think skynet will be simpler if I can only get it to compile

---

