---
title: "PS1 Prompt Colors"
date: 2023-03-26
forum: New to Ubuntu
---

### Post by rich332 on 2023-03-26
Hi folks.  I have a SBE with Ubuntu installed. Jammy Jellyfish.  I'm trying to change my prompt in zsh.  Here is my entry into ~/.zshrc:

    ```
export PS1="[\[$(tput sgr0)\]\[\033[38;5;41m\]\d\[$(tput sgr0)\] \[$(tput sgr0)\]\[\033[38;5;42m\]\T\[$(tput sgr0)\] \[$(tput sgr0)\]\[\033[38;5;9m\]\u\[$(tput sgr0)\]\[\033[38;5;215m\]@\[$(tput sgr0)\]\[\033[38;5;214m\]\h\[$(tput sgr0)\] \W]\[$(tput sgr0)\]"
```

For some reason I'm getting a long string that's similar.  I don't know why it isn't working.  This is my current prompt:

    ```
[\[\]\[\033[38;5;41m\]\d\[\] \[\]\[\033[38;5;42m\]\T\[\] \[\]\[\033[38;5;9m\]\u\[\]\[\033[38;5;215m\]@\[\]\[\033[38;5;214m\]\h\[\] \W]\[\]
```

Can anybody provide some insight as to how to get this to work?  Cheers

For so

---

