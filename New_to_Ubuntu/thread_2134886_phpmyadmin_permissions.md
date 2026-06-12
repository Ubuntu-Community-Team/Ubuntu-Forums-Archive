---
title: "phpmyadmin permissions"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by BobosAbelMihai on 2013-04-12
Hello everybody.
I installed lamp, and i must have done something wrong because when I try to enter phpmyadmin it says:
> Wrong permissions on configuration file, should not be world writable!

I moved the phpmyadmin folder into www, and i think maybe i give www full permissions, i don't know for sure.

Thank you very much.

---

### Post by fr2632 on 2013-04-12
> **BobosAbelMihai said:**
> Hello everybody.
I installed lamp, and i must have done something wrong because when I try to enter phpmyadmin it says:


I moved the phpmyadmin folder into www, and i think maybe i give www full permissions, i don't know for sure.

Thank you very much.

Can you login into mysql ? You can grant the permissions also from there:

[COLOR=#000000]mysql [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]u root [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]p
[/COLOR]
[COLOR=#000000]GRANT ALL PRIVILEGES ON [/COLOR][COLOR=#666600]*.*[/COLOR][COLOR=#000000] TO [/COLOR][COLOR=#008800]'yourusernamehere'[/COLOR][COLOR=#666600]@[/COLOR][COLOR=#008800]'localhost'
[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]WITH GRANT OPTION[/COLOR][COLOR=#666600];[/COLOR]

---

### Post by BobosAbelMihai on 2013-04-12
I solved it with this commands:
```

sudo dpkg -P phpmyadmin   
sudo rm -f /etc/apache2/conf.d/phpmyadmin.conf 
sudo service apache2 restart
```

Thank's.

P.S.: How to i check this thread as SOLVED, I am new to this forum and I don't know.

Thank you.

---

