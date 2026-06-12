---
title: "git, WebDAV and hooks"
date: 2008-08-20
forum: Programming Talk
---

### Post by pronik on 2008-08-20
Hello,

I hope there are some git experts here... I have a server with a git repository which is accessed over WebDAV. I have noticed that my post-update hooks didn't work and started investigating. After I've checked everything I came to the conclusion that there is no way git can start a hook action over WebDAV, since there ain't any such command in the protocol (and would be a giant security hole). So two questions:

[LIST=1]
[*]Are my conclusions right, i.e. hooks can't be executed?
[*]How do git experts propose setting up this server so that I can access git even from firewalled networks?
[/LIST]
Thanks!

---

### Post by trentonknight on 2009-06-21
What client are you using to connect to WebDav? I'm assuming you are using davfs? Your welcome to try it on our site at [http://www.cipherhive.com]("http://www.cipherhive.com") we host git for free and use WebDav as well. There is a tutorial on our home page you could see if we do anything differently.

---

