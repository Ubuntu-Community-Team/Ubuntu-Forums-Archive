---
title: "[SOLVED] Removing Home/Me/Examples"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by SonOfOdin on 2008-08-13
Is it safe to remove the /usr/share/example-content directory?  I have a link folder in /Home/Me called Examples

Its owned by root so I thought I had better check.

Cheers

---

### Post by nothingspecial on 2008-08-13
I`ve not got one anymore.

---

### Post by iaculallad on 2008-08-13
> **SonOfOdin said:**
> Is it safe to remove the /Home/Me/Examples directory?

Its locked so I thought I had better check.

Cheers

Yes, you could freely remove it:

```
sudo rm -rf ~/Examples
```

If you wanted back the contents, you could always browse to the /etc/skel directory and copy it.

---

### Post by SonOfOdin on 2008-08-13
Excellent, thanks for the replies.

---

### Post by kpkeerthi on 2008-08-13
You may also remove it with synaptic/apt-get
```
sudo apt-get purge example-content
```
* It may prompt you to remove ubuntu-desktop, which is just a meta-package and safe to remove

---

### Post by mcduck on 2008-08-13
> **iaculallad said:**
> Yes, you could freely remove it:

```
sudo rm -rf ~/Examples
```

If you wanted back the contents, you could always browse to the /etc/skel directory and copy it.

You don't need "sudo" to do that. Even when the actual directory is owned by root, the link in user home directories is owned by that user..

(so the link can be removed simply by dragging it into trash, or by selecting it and hitting del key)

---

### Post by kpkeerthi on 2008-08-13
If you look closely, ~/Examples is just a symbolic link to /usr/share/example-content. Deleting ~/Examples will only remove the symbolic link. To actually remove the content from your disk, you need to remove **example-content** package using Synaptic/apt-get

---

