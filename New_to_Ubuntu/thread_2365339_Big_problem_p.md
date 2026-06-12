---
title: "Big problem :p"
date: 2017-07-05
forum: New to Ubuntu
---

### Post by mac187 on 2017-07-05
Hi, i just installed neofetch, and wanted it to load everytime i run Terminator terminal, i followed the step at the end of this page : [https://superuser.com/questions/591321/execute-a-command-every-time-terminal-is-open](https://superuser.com/questions/591321/execute-a-command-every-time-terminal-is-open)

I put 'neofetch' at Run a custom command of my shell.

My default terminal works ok, but terminator terminal is bad :/

Everytime i use this 'Ctrl+Alt+T' , terminater load and quit after a second, now my problem is how to go in there and remove this neofetch from 'Run a custom command of my shell'
haha, 
Im trying to go to perferences but problem is when i click 'Ctrl+Alt+T' its open up terminator terminal and quit after a second, lol.. So now, how to remove the neofetch from there and how make it run everytime i run terminator terminal ?

Please help me out.. 

Thanx !

i typed this:

gedit ~/.config/terminator/config

and here is my config file:

```
[global_config]
  handle_size = 0
  title_font = Monospace 11
  title_hide_sizetext = True
  title_transmit_bg_color = "#12b4ab"
  title_use_system_font = False
[keybindings]
[layouts]
  [[default]]
    [[[child1]]]
      parent = window0
      type = Terminal
    [[[window0]]]
      parent = ""
      type = Window
[plugins]
[profiles]
  [[default]]
    background_color = "#300a24"
    background_darkness = 0.85
    background_image = None
    background_type = transparent
    cursor_shape = ibeam
    custom_command = neofetch (What is used to be here orginally?) 
    font = Monospace 12
    foreground_color = "#ffffff"
    scroll_on_output = False
    scrollback_infinite = True
    scrollback_lines = 5000
    scrollbar_position = hidden
    use_custom_command = True
    use_system_font = False
```

---

