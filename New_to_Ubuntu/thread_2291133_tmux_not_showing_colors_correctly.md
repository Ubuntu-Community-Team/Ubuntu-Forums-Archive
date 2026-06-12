---
title: "tmux not showing colors correctly"
date: 2015-08-18
forum: New to Ubuntu
---

### Post by Bakerconspiracy on 2015-08-18
I installed tmux and am really stoked on it but I cannot for the life of me get the colors to work for 'ls' and 'grep' (even though dir colors is enabled). It works correctly for vim though.... 
Btw I'm using gnome.

Here's my ~/.tmux.conf file:
```
  1 set -g default-terminal "screen-256color"
  2 
  3 #### COLOUR (Solarized dark)
  4 
  5 # default statusbar colors
  6 set-option -g status-bg black #base02
  7 set-option -g status-fg yellow #yellow
  8 set-option -g status-attr default
  9 
 10 # default window title colors
 11 set-window-option -g window-status-fg brightblue #base0
 12 set-window-option -g window-status-bg default
 13 #set-window-option -g window-status-attr dim
 14 
 15 # active window title colors
 16 set-window-option -g window-status-current-fg brightred #orange
 17 set-window-option -g window-status-current-bg default
 18 #set-window-option -g window-status-current-attr bright
 19 
 20 # pane border
 21 set-option -g pane-border-fg black #base02
 22 set-option -g pane-active-border-fg brightgreen #base01
 23 
 24 # message text
 25 set-option -g message-bg black #base02
 26 set-option -g message-fg brightred #orange
 27 
 28 # pane number display
 29 set-option -g display-panes-active-colour blue #blue
 30 set-option -g display-panes-colour brightred #orange
 31 
 32 # clock
 33 set-window-option -g clock-mode-colour green #green
```

when I'm in tmux my $TERM looks like this:

```
$ echo $TERM
screen-256color
```

and I've aliased tmux to "tmux -2":
```
$ alias
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -alF'
alias ls='ls --color=auto'
alias tmux='tmux -2'
```

Any idea on what I've got wrong?

---

