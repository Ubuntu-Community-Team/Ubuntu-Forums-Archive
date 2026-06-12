---
title: "Issues with indentation in vim with PHP"
date: 2023-02-07
forum: New to Ubuntu
---

### Post by hanji866 on 2023-02-07
I'm new to Ubuntu. Just migrating over from Gentoo. I've been pulling my hair out in regards to the indentation and indentation on comments in vim. I've been messing with /etc/vim/vimrc and /usr/share/vim/vim82/indent

So, with // comments, it will indent AND comment

Without comments, it will indent with every line with mouse paste.

If I remove the php.vim file, the commenting indent goes away, but looks like indents are still happening -- staggered look, but the commenting of all lines after a comment stops.

Again, I come from Gentoo, and I'm using vim90 there, but I've been using vim for years, so I don't think it's a vim version issue. Just can't figure out the proper configuration to add to vimrc. Googling has all sorts of options to address this, and I add those options with no results.

```
:set paste
```

Does what I want, but unsure how to set this in vimrc

Any help?

Thanks!
hanji

---

### Post by TheFu on 2023-02-07
Why would you edit system-wide settings?   vim settings belong in your user's personal ~/.vimrc.  There are plugins for vim for almost every language with multiple different ecosystems to control their use.  These things are portable, so if you just migrate your HOME between systems, you'll have all your vim settings.  

Solve issues once. Be lazy.

---

### Post by hanji866 on 2023-02-08
> **TheFu said:**
> Why would you edit system-wide settings?   vim settings belong in your user's personal ~/.vimrc.  There are plugins for vim for almost every language with multiple different ecosystems to control their use.  These things are portable, so if you just migrate your HOME between systems, you'll have all your vim settings.  

Solve issues once. Be lazy.

Thanks for the helpful reply...

---

### Post by TheFu on 2023-02-08
[https://thevaluable.dev/vim-php-ide/](https://thevaluable.dev/vim-php-ide/) - for neovim
[https://github.com/StanAngeloff/php.vim](https://github.com/StanAngeloff/php.vim) and works with [https://github.com/2072/PHP-Indenting-for-VIm](https://github.com/2072/PHP-Indenting-for-VIm)

---

