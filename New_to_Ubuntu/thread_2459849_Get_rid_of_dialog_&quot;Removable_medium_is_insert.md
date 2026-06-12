---
title: "Get rid of dialog &quot;Removable medium is inserted&quot;"
date: 2021-03-27
forum: New to Ubuntu
---

### Post by phibuntu on 2021-03-27
Hello Community

Whenever I insert a removable Medium (normally an external drive or an SD-Card), I get a dialog popping up which says
«Removable medium is inserted»
Is there a way, to get rid of this dialog?
(I normally know, when I insert an removable medium, and I have to grab a mouse to close the dialog: So better don't show it and I go directly to the medium using the "cd" command from the bash).

I use lxde (openbox? gnome? no idea) and ubuntu 20.04.2 LTS (Focal Fossa).

Any Idea?

Thanks in advance.

---

### Post by TheFu on 2021-03-27
You probably won't like it, but install and configure **autofs** for the storage you want to connect and access. Autofs is a server, so no gui to set it up, but after that, the specific storage is auto-mounted as needed and umounted when unused.

Options for better performance can be provided with each mount too.

---

### Post by guiverc on 2021-03-27
I just hit the <ESC> key which closes the dialog.

I won't offer more, as I don't know what you're running (Lubuntu has used LXQt in it's last five releases, LXDE being last used in 18.04, and yes Lubuntu does offer a pure openbox session, but you also mention GNOME)

---

