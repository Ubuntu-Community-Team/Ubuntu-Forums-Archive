---
title: "Ubuntu 20.04 repository still for mariadb 10.3 question"
date: 2020-06-12
forum: New to Ubuntu
---

### Post by blueclcl on 2020-06-12
Hi all.


[COLOR=#333333][FONT=Sailec-Regular]I am new to using a VPS / Ubuntu and was hoping that someone could advise me on the following:[/FONT][/COLOR]
[COLOR=#333333][FONT=Sailec-Regular]If I build a wordpress blog on Ubuntu 20.04 vps then MariaDB installs with version 10.3. Although this is not the latest version, I understand that this is a stable version and have been advised that its ok to use 10.3 for the next couple of years.[/FONT][/COLOR]
[COLOR=#333333][FONT=Sailec-Regular]My question are:[/FONT][/COLOR]
[COLOR=#333333][FONT=Sailec-Regular]How come Ubunto 20.04 downloads an old version of Mariadb?

Will Ubuntu likely update the repositories in the future so I can update my database easier?

If not , then how  easy is it to update in say 2 years when support runs out for the version of Mariadb?[/FONT][/COLOR]
[COLOR=#333333][FONT=Sailec-Regular]Will it be a case of updating to the new ubuntu next main its release which will then upgrade my version of mariadb to a more recent version?[/FONT][/COLOR]
[COLOR=#333333][FONT=Sailec-Regular]My blog by then will have lots of content on it, so I suppose im a bit worried about not being able to just transfer it over to a new version when needed.[/FONT][/COLOR]
[COLOR=#333333][FONT=Sailec-Regular]Im I worrying for nothing here.[/FONT][/COLOR]

Thanks in advance

blueclcl

---

### Post by ActionParsnip on 2020-06-12
Ubuntu isn't a rolling release distribution. Packages can be left in favour of stability. This is especially true in the LTS releases.
There are PPAs on Launchpad.net
[https://launchpad.net/ubuntu/+ppas?name_filter=mariadb](https://launchpad.net/ubuntu/+ppas?name_filter=mariadb)

These come with the usual caveats of a PPA. Remember to filter the PPA for your release name as not all PPAs support all releases

---

### Post by blueclcl on 2020-06-12
Thanks for the reply.

---

