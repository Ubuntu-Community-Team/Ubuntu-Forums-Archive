---
title: "A simple script to set keyboard short cuts"
date: 2006-09-19
forum: Outdated Tutorials &amp; Tips
---

### Post by parktownprawn on 2006-09-19
I hate using the gnome configuration editor to set my keyboard shorts cuts when setting up gnome. Here's a simple script which sets them for you. 

just type 

```
gvim shortcuts.sh
```

and copy the script below.

Once you've edited it your your liking, save it and type

```
sh shortcuts.sh
``` 

and you're done.

The script:
```

#!/bin/sh

function set_command {

gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_$1 $2

}

function set_shortcut {

gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_$1 $2

}

# Modify the following to set your custom keyboard shortcuts

set_command 1 "/usr/bin/evolution"
set_shortcut 1 "<Control><Alt>2"

set_command 2 "/usr/bin/swiftfox"
set_shortcut 2 "<Control><Alt>3"


# Uncomment the lines below to set new commands

#set_command 3 "Your command"
#set_shortcut 3 "Your short cut"


#set_command 4 ""
#set_shortcut 4 ""

#set_command 5 "Your command"
#set_shortcut 5 "Your short cut"


#set_command 6 ""
#set_shortcut 6 ""

#set_command 7 "Your command"
#set_shortcut 7 "Your short cut"


#set_command 8 ""
#set_shortcut 8 ""

#set_command 9 "Your command"
#set_shortcut 9 "Your short cut"


#set_command 10 ""
#set_shortcut 10 ""

#set_command 11 ""
#set_shortcut 11 ""

#set_command 12 ""
#set_shortcut 12 ""


```

---

### Post by mikeym on 2006-09-26
Try this one on for size:

```

#!/bin/sh

function set_command {

gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_$1 $2
}

function get_command {

gconftool-2 --get /apps/metacity/keybinding_commands/command_$1
}


function set_shortcut {

gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_$1 $2

}

function get_shortcut {

gconftool-2 --get /apps/metacity/global_keybindings/run_command_$1

}


if [ $1 == "-get" ]; then
        if [ -z $2 ]; then
                echo "Useage: $0 [ -get | -set ] commandno [shortcut] [command]"
                exit 1
        fi
        get_shortcut $2
        get_command $2
elif [ $1 == "-set" ]; then
        if [ -z $2 ] | [ -z $3 ] | [ -z $4 ]; then
                echo "Useage: $0 [ -get | -set ] commandno [shortcut] [command]"
                exit 1
        fi
        set_shortcut $2 $3
        set_command $2 $4
else
        echo "Useage: $0 [ -get | -set ] commandno [shortcut] [command]"
        exit 2
fi

```

Lets you check what a shortcut is before you replace it.

Type checking doesn't realy exist so be carefull use like:

```

$ shortcut.sh -get 1
      <Alt>Home
      /usr/local/bin/somefile
$ shortcut.sh -set 1 "<Alt>Home" "playpause.sh"

```

---

