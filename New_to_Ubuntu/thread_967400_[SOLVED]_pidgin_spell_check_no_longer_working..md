---
title: "[SOLVED] pidgin spell check no longer working."
date: 2008-11-02
forum: New to Ubuntu
---

### Post by fr.theo on 2008-11-02
I recently discovered that pidgin no longer underlines misspelled words and although my spelling is acceptable academically I still need help form time to time.  


don't worry allot of the words you see here have been corrected, so if you think I can spell or say my spelling has improved don't be fooled.


can anyone help with this problem?

---

### Post by Daveth on 2008-11-02
though a bit obvious, it might be worth uninstalling it and then putting it back.

---

### Post by LunaMouse on 2008-11-02
Pidgin relies on aspell for spellchecking. Make certain that aspell and aspell-en (and whatever other languages you might be using) are installed.

apt-get install aspell aspell-en

That *should* do the trick.

---

### Post by fr.theo on 2008-11-15
sudo apt-get install aspell worked, thanks for the help.

---

### Post by juanp.contreras on 2009-02-06
Hi.... I'm having automated spellcheking problems on pidgin... I have installed aspell-es. My PC is configured to English but I want every program to use aspell-es for spell checking.... do you know how to?

thanks

---

### Post by khc on 2009-02-06
> **juanp.contreras said:**
> Hi.... I'm having automated spellcheking problems on pidgin... I have installed aspell-es. My PC is configured to English but I want every program to use aspell-es for spell checking.... do you know how to?

thanks

use the switchspell plugin that comes with the purple plugin pack

---

### Post by juanp.contreras on 2009-02-07
I've installed purple pack (at least when I put "purple" on synaptic there seems to be installed that pack) but I didn't found that specific plugin.... :(

---

### Post by derlinuxer on 2009-02-11
Moin,

yes the description shows the switch spell but it's not in the package (see the file list).
That is the root cause. Or I can't see it.

A very dirty trick:

[LIST]
[*]deinstall the current pidgin-plugin.pack
[*]install the old pack [http://download.ubuntu.pl/_Feisty_Fawn/pidgin/2.1.1/pidgin-plugin-pack_2.1.1-1_i386.deb](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/2.1.1/pidgin-plugin-pack_2.1.1-1_i386.deb) (the switchspell plugin is included)

[*]save the files “switchspell.la” “switchspell.so” form ”/usr/lib/pidgin” (THE PLUGIN we need)
[*]run a update (let him update the old plugin pack again)
[*]copy the switchspell files back in the directory ”/usr/lib/pidgin” again
[*]start pidgin
[*]AND    ?????
[/LIST]

As I sad very dirty. But it works fine for me.

---

### Post by juanp.contreras on 2009-02-11
Thanks... very useful!

---

### Post by teh_Dekar on 2009-02-16
I have the latest version:
[http://dekar.wc3edit.net/2009/01/31/pidgin-add-on-pack-for-linux-2/](http://dekar.wc3edit.net/2009/01/31/pidgin-add-on-pack-for-linux-2/)

---

