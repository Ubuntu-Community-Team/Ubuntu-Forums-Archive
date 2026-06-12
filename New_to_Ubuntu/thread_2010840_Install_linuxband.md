---
title: "Install linuxband"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by paulemony on 2012-06-26
Been using Ubuntu for a while but still have gaps in knowledge, e.g. I'm trying to install linuxband from [www.linuxband.org](www.linuxband.org) into Ubuntu 12.04. I've downloaded & extracted linuxband-12.02.1.tar.gz into Downloads folder but then what? The Read-me page just says to check the website. I've installed the dependencies from the documentation page, cd into the folder & ./configure but linuxband doesn't appear & doesn't show in Software centre or Synaptic, I imagine there's just a simple terminal command that I can't find in order to switch it on?

---

### Post by MG&amp;TL on 2012-06-26
Usually, software compilation goes like this:

```

./configure
make
sudo make install

```

Have you run the last two steps?

---

### Post by paulemony on 2012-06-26
I have now! As I said, just a simple command I didn't know (or probably did but just forgot, I'll tattoo it on my forehead), thanks.

---

### Post by MG&amp;TL on 2012-06-26
> **paulemony said:**
> I have now! As I said, just a simple command I didn't know (or probably did but just forgot, I'll tattoo it on my forehead), thanks.

Not a problem. Although normally the README should tell you that...meh, as long as you got it installed. :)

---

### Post by Cheesemill on 2012-06-26
> **MG&TL said:**
> Not a problem. Although normally the README should tell you that...meh, as long as you got it installed. :)
The README doesn't have any installation instructions, they are all on the website though....
[http://linuxband.org/documentation.html](http://linuxband.org/documentation.html)

---

