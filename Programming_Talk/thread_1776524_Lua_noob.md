---
title: "Lua noob"
date: 2011-06-06
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2011-06-06
Hello I am writing Lua script for Aegisub but I have some problems with the language. I am used to coding in C++ only(as a hobby) and can't figure out many things in Lua. The error is in line 11 of the script. The message I get from Aegisub is this: **[string "remove_unused_styles.lua"]:11: attempt to get length of local 'styles' (a nil value)**

Here is the relevant link on the Aegisub forum: [http://forum.aegisub.org/viewtopic.php?f=5&t=2944](http://forum.aegisub.org/viewtopic.php?f=5&t=2944)

And here is my code:
```
    script_name = "Remove Unused Styles"
    --script_description = "Displays a dialog that let's the user decide which unused styles to remove."
    script_description = "Scan and remove the unused styles"
    script_author = "sledgehammer_999"
    script_version = "1.00"

    function remove_unused_styles_macro(subtitles, selected_lines, active_line)
       local styles   
       for i = 1, #subtitles do
          if subtitles[i].class == "style" then
             styles[#styles + 1].name = subtitles[i].name
             styles[#styles + 1].index = i
          end
       end
       
       --Styles definitions collected
       --Now let's go over the dialogue lines and see which ones are used
       for i = 1, #styles do
          for k = 1, #subtitles do
             styles[i].used = false
             if subtitles[k].class == "dialogue" and subtitles[k].style == styles[i].name then
                styles[i].used = true
                break
             end         
          end
       end
       
       --At this point we have marked the unused styles
       --TODO: display a dialog and let the user decide which ones to remove. Currently don't know how to determine optimal size of the controls.
       
       --remove the unused styles.
       local styles_index
       --This loop is redundant. It could be incorporated above, but it's placed here for when the dialog is implemented.
       for i = 1, #styles do
          if styles[i].used == false then
             styles_index[#styles_index + 1] = i
          end
       end
       
       --Now we have all the unused styles let's remove them and make and an undo point
       subtitles.delete(unpack(styles_index))
       aegisub.set_undo_point(script_name)
    end

    aegisub.register_macro(script_name, script_description, remove_unused_styles_macro)

```

---

### Post by gmargo on 2011-06-06
Try initializing the "styles" table:
```

local styles = {}

```[http://www.lua.org/pil/11.1.html](http://www.lua.org/pil/11.1.html)

---

### Post by SledgeHammer_999 on 2011-06-06
Let's say that I "solved" it. Look at the link in my first post.

---

