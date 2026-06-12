---
title: "Help with omnicomplete in Vim"
date: 2009-10-28
forum: Programming Talk
---

### Post by Amablue on 2009-10-28
I'm trying to get OmniCppcomplete to work and I'm running into trouble. I've followed the steps on [this page]("http://vim.wikia.com/wiki/VimTip1608") (including the things to add to the .vimrc file). I downloaded and extracted the zip file to ~/.vim, I ran the commands it says, I have exuberant ctags installed, I did everything there and it still doesn't work. I also tried downloading the modified stl for the __STD_NAMESPACE_BEGIN fix. I ran ctags on the directory and placed the tags file in ~/.vim/tags/cpp.

Whenever I type a class name or namespace name followed by a . or :: or whatever, I only get an error saying "Omni completion (^O^N^P) Pattern not found". I've run "tselect TestClass" to see that the tags were actually being generated and they are, so I'm at a loss as to what's happening.

---

