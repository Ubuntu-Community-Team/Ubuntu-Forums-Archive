---
title: "[php]Easy MySql Commands"
date: 2008-08-18
forum: Programming Talk
---

### Post by Pyro.699 on 2008-08-18
Hello,

I am almost 100% sure that there are scripts that are out there that make programming with MySQL more efficient. When programming with vBulletin there are commands like **$vb->mysql->write('MySQL Code');** that make it so that writing/reading/executing MySQL code becomes something that is one line. I tried to search MySQL Frameworks and came up dry, does anyone know of something that i could use?

Thanks
~Cody Woolaver

---

### Post by mssever on 2008-08-18
> **Pyro.699 said:**
> I am almost 100% sure that there are scripts that are out there that make programming with MySQL more efficient. When programming with vBulletin there are commands like **$vb->mysql->write('MySQL Code');** that make it so that writing/reading/executing MySQL code becomes something that is one line. I tried to search MySQL Frameworks and came up dry, does anyone know of something that i could use?
When I'm forced to write PHP, I use the Code Igniter framework, which includes a set of active record classes. You might be able to use them, but OO in PHP is verbose, no matter how you slice it. I ended up just configuring my editor of choice to use templates, so when I type 'dbw<tab>' I get [php]$this->db->where('where_clause');[/php].

---

