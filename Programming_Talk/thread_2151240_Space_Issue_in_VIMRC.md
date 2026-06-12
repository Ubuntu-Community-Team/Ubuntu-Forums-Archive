---
title: "Space Issue in VIMRC"
date: 2013-06-03
forum: Programming Talk
---

### Post by huangyingw on 2013-06-03
Hello all,
     Bellowing is part of my .vimrc file.
```
function! CHANGE_CURR_DIR()
  let _dir = expand("%:p:h")
  exec "cd " . _dir
  unlet _dir
  if filereadable(".vimdc")
    source .vimdc
  endif
endfunction

autocmd BufEnter * call CHANGE_CURR_DIR()

```
      The problem is exec "cd " . _dir will mis-function, when the _dir contains space. I have tried simply wrap the _dir like "$_dir", but it does not work.
      Could someone help me to solve this?

---

