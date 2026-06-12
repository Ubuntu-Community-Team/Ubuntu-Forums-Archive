---
title: "Running Neovim snap version  as defaullt editor"
date: 2024-01-08
forum: Programming Talk
---

### Post by townhill on 2024-01-08
I use Neovim as my default code editor and in order to run the current version I installed 0.9.4 as a snap package.  I made the alias `nv` for `snap run nvim`  and it works just fine but my default editor is set to the older version of Neovim and the snap does not appear as an option when I run `sudo update-alternatives --config editor`. 

This has created a problem when I do a git commit because the old version pops up to write the commit message and complains that it can't run the plugins (like TreeSitter) that run on the current version. Not a big problem but annoying.  Also, I use ZSH and when I type `nv file...` (with a partial file name) I no longer get the autocomplete that I used to on a partial file name.

I think I need to create an alias that will allow Ubuntu to see the snap version and let me add it as the default editor. Is that correct and if so I would really appreciate some guidance on how to go about it. 

Thanks

---

### Post by townhill on 2024-01-12
In case someone is having the same issue, it turns out this is a two-step process:
1. To add the snap version of Neovim as a choice of editors
 ```
sudo update-alternatives --install /usr/bin/editor editor /snap/bin/nvim 1111
```
(thanks to [StackExchange]([https://askubuntu.com/questions/1304472/update-alternatives-list-editor-does-not-show-editors-installed-via-snap](https://askubuntu.com/questions/1304472/update-alternatives-list-editor-does-not-show-editors-installed-via-snap)))

2. Edit .gitconfig to set /var/snap/nvim as the editor for commits.

---

