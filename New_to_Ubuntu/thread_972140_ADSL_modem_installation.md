---
title: "ADSL modem installation"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by Helena84 on 2008-11-05
Hello... 

I've got Ubuntu 8.4 yesterday and I couldn't make the modem work. I've downloaded eagle-usb-2.3.2.tar.bz2, but I have no idea what to do with it and I couldn't follow any online instructions... 

The adsl modem is Sagem F@st 800.

If someone could guide me step-by-step through installation I would be thankful forever :)

---

### Post by FreewheelinFrank on 2008-11-05
Here's the installation guide from the Sagem site:

[http://www.sagem.com/support/site/livret/gu_Linux_en.pdf](http://www.sagem.com/support/site/livret/gu_Linux_en.pdf)

And the driver:

[http://www.sagem.com/support/site/driver/Fast8x0_3-0-6.tgz](http://www.sagem.com/support/site/driver/Fast8x0_3-0-6.tgz)

Product home page:

[http://www.sagem.com/support/site/modele_fax.php?page=produit&prd=SAGEMF@st800/840&pays=uk](http://www.sagem.com/support/site/modele_fax.php?page=produit&prd=SAGEMF@st800/840&pays=uk)

Hope this helps!

You can also get info in other languages, I think:

[http://www.sagem.com/support/site/sagem_carte.php](http://www.sagem.com/support/site/sagem_carte.php)

---

### Post by Helena84 on 2008-11-05
After typing su - it asks me for a password. What password should I type in? When I type in my login password it says it is wrong...

---

### Post by FreewheelinFrank on 2008-11-05
That'll be 'sudo' in Ubuntu, I think.

---

### Post by FreewheelinFrank on 2008-11-05
You'll need to prepend the commands with 'sudo', rather than gain root access with 'su'.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

