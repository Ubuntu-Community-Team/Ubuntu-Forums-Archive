---
title: "Gedit External Tools"
date: 2008-02-27
forum: Programming Talk
---

### Post by Jeremiah Griffin on 2008-02-27
I'm not exactly sure if this is the correct category, as I have not spent much time on the forum, so please correct me if it belongs somewhere else.

Gedit's external tools plugin adds a newline after the following "tool":

```
#!/bin/sh

echo "["`date +"%Y-%m-%d"`"] "`whoami`": "


```
Input: Nothing
Output: Insert at cursor position

Would it be possible to edit the plugin and remove the newline? It's pretty annoying to have to backspace whenever I create a change log entry.

Also somewhat related: Can the external tools "Shell Output" window be prevented from popping up when a shell command is run? My screen is only 15.1", having a pane at the bottom of the window wastes precious screen space.

Thanks.

---

### Post by Jeremiah Griffin on 2008-02-27
Nevermind. I delved into the plugin's source code and edited it myself. Here is a patch:

```
diff -urp externaltools/functions.py externaltools.old/functions.py
--- externaltools/functions.py	2008-02-27 12:23:04.000000000 -0800
+++ externaltools.old/functions.py	2008-02-27 12:28:07.000000000 -0800
@@ -36,7 +36,7 @@ def capture_menu_action(action, window, 
 
     # Get the panel
     panel = window.get_data("ExternalToolsPluginWindowData")._output_buffer
-    #panel.show()
+    panel.show()
     panel.clear()
 
     # Configure capture environment
@@ -195,6 +195,6 @@ def capture_stdout_line_panel(capture, l
     panel.write(line)
 
 def capture_stdout_line_document(capture, line, document, pos):
-    document.insert(pos, line.strip("\r\n"))
+    document.insert(pos, line)
 
 # ex:ts=4:et:
```

---

### Post by Meson on 2010-01-02
The echo command inserts a newline at the end. You want to call
```
echo -n "STUFF"
```

---

