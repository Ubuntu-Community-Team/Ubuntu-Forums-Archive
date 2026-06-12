---
title: "Mod Rewrite"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by hungryOrb on 2008-10-20
Hi! 
After having installed lamp I noticed my apache2 folder's httpd.conf was empty. I found out why from google. However, that didn't solve any problems, because I am trying to uncomment a line which doesn't seem to exist anywhere. 
To enable mod rewrite, apparently, you must first do this: 

Inside the httpd.conf file uncomment the line LoadModule rewrite_module modules/mod_rewrite.so

but this line doesn't exist in the apache2.conf file either. So I thought, hm I guess I gotta add the mod into the mods-enabled folder somehow..
Is this correct? and if so, please could someone point me in the right direction to finding it? 

Thanks for considering!
:S

---

### Post by stephanvaningen on 2008-10-20
> **hungryOrb said:**
> Hi! 
After having installed lamp I noticed my apache2 folder's httpd.conf was empty. I found out why from google. However, that didn't solve any problems, because I am trying to uncomment a line which doesn't seem to exist anywhere. 
To enable mod rewrite, apparently, you must first do this: 

Inside the httpd.conf file uncomment the line LoadModule rewrite_module modules/mod_rewrite.so

but this line doesn't exist in the apache2.conf file either. So I thought, hm I guess I gotta add the mod into the mods-enabled folder somehow..
Is this correct? and if so, please could someone point me in the right direction to finding it? 

Thanks for considering!
:S

I thought there's also a sites.enabled/sites.active/... folder somewhere with a file per site and 'default' for the standard?

---

### Post by hungryOrb on 2008-10-20
> **stephanvaningen said:**
> I thought there's also a sites.enabled/sites.active/... folder somewhere with a file per site and 'default' for the standard?

Thanks for reply!
but sorry, missed your point! :(

p.s. My apache is structured differently :( -I have a sites-enabled, but not sites-active.

---

