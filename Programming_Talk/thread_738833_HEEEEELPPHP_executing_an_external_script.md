---
title: "HEEEEELP::PHP: executing an external script?"
date: 2008-03-29
forum: Programming Talk
---

### Post by astrosoft on 2008-03-29
Hi guys!
Does anyone know how to execute

killall -v pppd

via PHP?

I've tried everything and have a feeling that I simply can't through ubuntu's permissions...

Thx.

---

### Post by kidders on 2008-03-30
Hi there,

[PHP]echo `killall -v pppd`;[/PHP]

Permissions only become an issue if something other than your web server started the processes you want to terminate ... the same rule that would apply to you if you ran the command yourself.

---

