---
title: "Vim color switcher plugin ( python )"
date: 2007-10-26
forum: Programming Talk
---

### Post by revenant_org on 2007-10-26
This is my first time to write VIM plugin using python. This plugin changes the current colorscheme with the next one, and so on. 

I often use VIM to script in many languages ( php, python, ruby, and latex ), unfortunately there is no color scheme that fits my needs for all of them. Because of that, I have created this script.

Current features: 

 - Incremental color switching ( one direction )
 - available colors ( ~/.vim/colors/*.vim)

Todos:

 - bi-directional color switching.
 - system-wide colors.


changecolors.vim:
```


" Vim global plugin for colors switching
" Last Change:	2007 Oct 25
" Maintainer:	Hasan Abdel Halim <hasana@gmail.com>
" License:      GPL

let s:curr_index = 0

nmap <c-a> :call NextColor() <cr> 

function! NextColor()
python << EOF
import vim,os

curr_index = int(vim.eval("s:curr_index"))
curr_dir = vim.eval("$HOME")
curr_dir += "/.vim/colors/"
colors   = os.listdir(curr_dir)
colors_names = []

for color in sorted(colors):
  color, ext = color.split('.')
  colors_names.append(color)


if curr_index >= len(colors_names):
  curr_index = 0
else:
  vim.command("let s:curr_index= s:curr_index +1 ")
  curr_index = curr_index + 1 

vim.command("colorscheme " + colors_names[curr_index])
EOF

endfunction

```

Please feel free to comment, or suggest :guitar:

---

