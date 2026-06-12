---
title: "Xorg crash and logout when opening some files with GVim"
date: 2014-03-13
forum: New to Ubuntu
---

### Post by Eleutharios on 2014-03-13
Hello,

I am experiencing an odd problem with GVim. Whenever I open a file, with the exception of a few really simple files without any code, Xorg crashes and I am booted back to a black screen and then the login screen. This problem does not occur when opening the same files GEdit or Vim, only with GVim. This problem occur when using both vim-gnome and vim-gtk and I have tried purging both and reinstalling one at a time. The problem seems to be related to my .vimrc file, since moving or renaming ir makes the problem go away. However, this file worked fine before I reinstalled Ubuntu. Here are its contents:

```
"Vim Configuration File
".vimrc

"UI Settings
"Background and Text Settings
colors koehler
set guifont=Monospace\ 12

"Line Numbering
set nu

"Hotkeys
map <F7> :tabp<Enter>
map <F8> :tabn<Enter>

"Text Layout
"Text Width and Wrapping
set tw=80
set fo+=t

"Indentation Settings
set autoindent
set tabstop=4
set shiftwidth=4
set expandtab

"Miscellaneous
set spell
set hls
```

Additional Information:
OS: Ubuntu 13.10, 64 bit, recently reinstalled.
Graphics: nvidia-331 with bumblebee, installed according to [this]("http://www.muktware.com/2013/12/install-nvidia-331-bumblebee-optimus-cards/18271") website, with the exception that nvidia-settings-331 was replaced by nvidia-settings.
Crash file: /var/crash/_usr_bin_Xorg.0.crash

Let me know if I can give any more information. Any help you oculd lend in helping me solve this problem would be most appreciated. Thank you!

---

### Post by Eleutharios on 2014-03-13
After some experimentation, it seems the secon-to-last line "set spell" is the cuplrit. Commenting that line causes the problem to go away and typing ":set spell" into the gvim terminal causes it to occur. Changing the line to "set spell spelllang-en_us" had no effect. Still not sure how to actually fix the problem.

---

### Post by Eleutharios on 2014-03-14
The problem also occurs when launching LibreOffice.

---

### Post by Eleutharios on 2014-03-14
Problem was an unmet dependancy if some sort. Fixed it by the instructions [here]("http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies").

---

