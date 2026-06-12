---
title: "need help tweaking gedit"
date: 2007-09-14
forum: Programming Talk
---

### Post by pedrotuga on 2007-09-14
Hey all... i love gedit and gnome in general... as i find more about it's potential I just like it more and more.
I use the snippets plugin like every 20 seconds or so, and i love the file browser on the side, it's essential to me as i work in a remote filesystem.

But there is an feature that it would be so handy that i would even consider gedit the ultimate editor.

Does anybody knows how to quickly turn ON or OFF the text wraping?
A key binding or a button on the toolbar would be handy... going through the menus sucks :(

I am not familiar with gtk otherwise i would teak it myself. should be possible to mess up with the UI and or create an overlay or something.

Any gtk geek out there? Or any solution at all to this?

---

### Post by AlexenderReez on 2007-09-14
to get the many gedit option...install gedit plugin ...search it in synaptic...hm...you set it in preferences ...see gedit option there...

---

### Post by pedrotuga on 2007-09-14
> **AlexenderReez said:**
> to get the many gedit option...install gedit plugin ...search it in synaptic...hm...you set it in preferences ...see gedit option there...

sorry, didn't understand you.
which plugin is there that does this? 
I now i set it preferences, but i want a quicker way to do it.

---

### Post by engla on 2007-09-14
If you use the external tools plugin you can add two tools to toggle this, and add keyboard shortcuts.

Wrap off:
```
gconftool-2 --type string --set /apps/gedit-2/preferences/editor/wrap_mode/wrap_mode "GTK_WRAP_NONE"
```

Wrap on:
```
gconftool-2 --type string --set /apps/gedit-2/preferences/editor/wrap_mode/wrap_mode "GTK_WRAP_WORD"
```


For even more hackiness, you can make a ***snippet*** that activates this.. just make a snippet with the text '$(1:command)' where command is one of the above... perhaps that is even better, even if quirky

---

### Post by pedrotuga on 2007-09-15
> **engla said:**
> If you use the external tools plugin you can add two tools to toggle this, and add keyboard shortcuts.

Wrap off:
```
gconftool-2 --type string --set /apps/gedit-2/preferences/editor/wrap_mode/wrap_mode "GTK_WRAP_NONE"
```

Wrap on:
```
gconftool-2 --type string --set /apps/gedit-2/preferences/editor/wrap_mode/wrap_mode "GTK_WRAP_WORD"
```


For even more hackiness, you can make a ***snippet*** that activates this.. just make a snippet with the text '$(1:command)' where command is one of the above... perhaps that is even better, even if quirky

Awsome! It works lika a charm!
If it's not asking to much... anyway to do this a toggle instead so i can use the same keybinding?

---

### Post by engla on 2007-09-15
I don't know why I answer, but I guess I think it is fun :)

Here's a shell script typical of how you might do it: (this can go in the external tools plugin)
```

#!/bin/sh

# Toggle wrapping in gedit

KEY="/apps/gedit-2/preferences/editor/wrap_mode/wrap_mode"
NO="GTK_WRAP_NONE"
YES="GTK_WRAP_WORD"

gconftool-2 --get "$KEY" | grep $YES >/dev/null && gconftool-2 --type string --set "$KEY" "$NO" || gconftool-2 --type string --set "$KEY" "$YES" 
```

If you want that for snippets insted (in that freaky hack) you use that thing but as an obfuscated oneliner enclosed in $(1: ):
```

$(1:gconftool-2 --get "/apps/gedit-2/preferences/editor/wrap_mode/wrap_mode" | grep GTK_WRAP_WORD >/dev/null && gconftool-2 --type string --set "/apps/gedit-2/preferences/editor/wrap_mode/wrap_mode" GTK_WRAP_NONE || gconftool-2 --type string --set "/apps/gedit-2/preferences/editor/wrap_mode/wrap_mode" GTK_WRAP_WORD)

```


Note on how that works:

See the grep command? it sees if it can find the text corresponding to the YES option, and returns a "success value". If successful, the command after && is executed. If not, the command after || is executed.

---

