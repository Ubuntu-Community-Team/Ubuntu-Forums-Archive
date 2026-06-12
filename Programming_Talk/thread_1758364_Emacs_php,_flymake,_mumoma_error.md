---
title: "Emacs: php, flymake, mumoma error"
date: 2011-05-14
forum: Programming Talk
---

### Post by lykwydchykyn on 2011-05-14
I use Emacs for php development, using mumamo and flymake.  The first time I open a php file after opening emacs, the command fails and I get this backtrace:

```


  set-auto-mode()
  normal-mode(t)
  after-find-file(nil t)
  find-file-noselect-1(#<buffer index.php> "~/public_html/adm/index.php" nil nil "~/public_html/adm/index.php" (173646 2054))
  find-file-noselect("~/public_html/adm/index.php" nil nil t)
  find-file("~/public_html/adm/index.php" t)
  call-interactively(find-file nil nil)


```

Of course, "~/public_html/adm/index.php" is replaced by whatever file I happen to be opening. I don't see an error in that backtrace.

After getting this, I can close the backtrace, re-open the file and php files open fine from that point on.

Anyone know what could be happening?

---

