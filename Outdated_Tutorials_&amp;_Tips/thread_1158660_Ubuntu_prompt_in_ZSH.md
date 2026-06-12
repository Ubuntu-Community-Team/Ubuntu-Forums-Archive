---
title: "Ubuntu prompt in ZSH"
date: 2009-05-13
forum: Outdated Tutorials &amp; Tips
---

### Post by sgargan on 2009-05-13
I've recently been playing with zsh and while its proving itself very useful, I much prefer the basic ubuntu prompt. So having looked at how zsh defines its prompt themes I put together this simple profile to replicate ubuntu's


All the profiles are stored in /usr/share/zsh/functions/Prompts. As root open a file in here called prompt_ubuntu_setup
```
sudo gedit /usr/share/zsh/functions/Prompts/prompt_ubuntu_setup
```

Save the following script to this file
```

#
# Ubuntu Default Prompt
# Styled like the default prompt in Ubuntu 9.04 Jaunty
# Cloned by Steve Gargan
#
prompt_ubuntu_setup () 
{
  local userhost=${1:-'green'}
  local cwd=${2:-'blue'}

  PS1="%B%F{$userhost}%n@%m%F{$cwd%} %~ $ %b%k%f"
  PS2="> "
  RPS1=""

  prompt_opts=( cr percent )
}

prompt_ubuntu_preview () {
  if (( ! $#* )); then
    prompt_preview_theme ubuntu
    print
    prompt_preview_theme ubuntu red white
  else
    prompt_preview_theme ubuntu "$@"
  fi
}

prompt_ubuntu_setup "$@"
```

Save and restart the shell. You can list the available prompts using 
```
prompt -l
```
and should see 
```
Currently available prompt themes:
adam1 adam2 bart bigfade clint elite2 elite fade fire off oliver pws redhat suse ubuntu walters zefram
```

Add these two lines to your .zshrc to use this prompt by default. (Or replace with one of the other available profiles if it so suits your style)

```
autoload -U promptinit && promptinit
prompt ubuntu
```

Enjoy.

ste

---

