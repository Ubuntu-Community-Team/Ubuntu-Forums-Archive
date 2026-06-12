---
title: "Using Vim for Web development"
date: 2008-12-24
forum: Programming Talk
---

### Post by Rokurosv on 2008-12-24
Well I've been using vim for a week now after a failed attempt last time, but I'm beginning to see it's true power. I mostly do PHP,HTML,Javascript and the ocationaly python script. I'm using Komodo Edit right now but I was wondering if you could turn Vim into a Web Development IDE of sorts. What plugins should I use? Also I'm very fond of snippets, one of the reasons I use Komodo Edit, is there any snippet support for Vim besides snippetsEmu? I tried configuring but it didn't worked out :S.

Thanks

---

### Post by catchmeifyoutry on 2008-12-24
Maybe you'll find this link interesting, when your a bit more comfortable with vim:
[How to Debug PHP with Vim and XDebug on Linux]("http://tech.blog.box.net/2007/06/20/how-to-debug-php-with-vim-and-xdebug-on-linux/")

---

### Post by SeanHodges on 2008-12-26
> **Rokurosv said:**
> I was wondering if you could turn Vim into a Web Development IDE of sorts.

Well Vim is a programmable text editor, rather than an IDE. There are a whole host of plugins and scripts available on [vim.org]("http://www.vim.org/scripts/index.php") and tips/tricks on the [Wiki]("http://vim.wikia.com/wiki/Main_Page"), but Vim is a bit different to a conventional IDE, as you add these features yourself. An IDE usually provides a massive library of features out-of-the-box, most of which you never use or are even aware exists. 

With Vim, you also get to link features together and bind complex commands to specific keys, with a little tweaking of the scripts.

> **Rokurosv said:**
> What plugins should I use?

The best approach is to stick with just the basic editor until you find yourself missing something, then go onto the Vim sites and investigate possible solutions. It's worth knowing how to [get in touch with the Vim community]("http://www.vim.org/community.php") as well, as there are plenty of people around who will happily help you with problems.

> **Rokurosv said:**
> Also I'm very fond of snippets, one of the reasons I use Komodo Edit, is there any snippet support for Vim besides snippetsEmu? I tried configuring but it didn't worked out :S.

Thanks

I'm not familiar with Komodo/TextMate snippets, or the snippetsEmu plugin, but from what I can see it looks like a form of macro support. There are a number of ways of making/replaying macros in Vim, the simplest being the ["q" recording command.]("http://vim.wikia.com/wiki/Recording_keys_for_repeated_jobs"). You can also (with a bit of practice) write small functions in your .vimrc file to perform more complex tasks when you press a given key combination.

However, if you are looking specifically into using TextMate snippets in Vim, then you might want to email the author of snippetsEmu and ask him for some help (his email address is given on the snippetsEmu script page). This way, you will get the plugin working more quickly, and he will be able to identify the trouble-spots with configuring his plugin and improve on the instructions.

---

### Post by Bjorn Enki on 2009-05-31
You might also like a link to a [Vim color scheme I made specifically for HTML, PHP, CSS ]("http://www.bjornenki.com/blog/vim-gvim-colorscheme-website-development")and JavaScript - most of your favorite web development languages as well.

HTML
[IMG]http://www.bjornenki.com/blog/gvim-colorscheme/html.png[/IMG]

CSS
[IMG]http://www.bjornenki.com/blog/gvim-colorscheme/css.png[/IMG]

PHP
[IMG]http://www.bjornenki.com/blog/gvim-colorscheme/php.png[/IMG]

JavaScript
[IMG]http://www.bjornenki.com/blog/gvim-colorscheme/javascript.png[/IMG]

:)

---

### Post by Elfy on 2009-05-31
Closed - necromancy

well that was a fail - forgot to close it - I'll leave it open and see what happens :)

---

### Post by tyfius on 2009-05-31
Take a look at the slides from Andrei Zmievski's [VIM for (PHP) Programmers]("http://gravitonic.com/2007/02/vim-for-php-programmers-slides-and-resources") presentation.
The article also contains a link to his VIM setup which includes a whole lot of useful VIM scripts and shortcuts.

I have been using them myself, and modified it to my needs, for quite some time now and it's pretty much basically all that's required.

---

### Post by myhieu on 2010-06-27
Thanks for slides :p

---

