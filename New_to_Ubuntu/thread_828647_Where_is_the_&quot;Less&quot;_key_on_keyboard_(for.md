---
title: "Where is the &quot;Less&quot; key on keyboard (for FreeMind)"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by hanzj on 2008-06-13
Hello,  
Using FreeMind 0.9.0 Beta 18, Freemind/Navigate/Note Edit Switch says that its shortcut is "Control+Less". What in the world is the "Less" key? 
 
I've tried: 
[SIZE=4]**< **[/SIZE]
and  
[SIZE=4]**-  **[/SIZE]
but neither work. 
 
How can i switch from node to its note without using my mouse? 

----------
FreeMind is at [http://freemind.sourceforge.net/wiki/index.php/Main_Page](http://freemind.sourceforge.net/wiki/index.php/Main_Page)

---

### Post by alexandremrj on 2008-06-19
Hello,

Freemind usually uses the down arrow key, have you tried that?

You can also edit your shortcuts keys (from their wiki)

To add a new keyboard shortcut, say for "Change node background color", open the file mindmap_menus.xml (in freemind.jar) and search for "background", say.

You'll find

  <menu_action field="nodeColor" key_ref="keystroke_node_color"/>
  <menu_action field="nodeColorBlend" key_ref="keystroke_node_color_blend"/>
  <menu_action field="nodeBackgroundColor"/>
  <menu_action field="removeNodeBackgroundColor"/>
</menu_category>

Here, you add a new keyboard ref attribute like:

  <menu_action field="nodeColor" key_ref="keystroke_node_color"/>
  <menu_action field="nodeColorBlend" key_ref="keystroke_node_color_blend"/>
  <menu_action field="nodeBackgroundColor" key_ref="keystroke_node_background_color"/>
  <menu_action field="removeNodeBackgroundColor"/>
</menu_category>

Open the file freemind.properties and add a line like

#
keystroke_node_color = alt F
keystroke_node_color_blend = alt B
keystroke_edge_color = alt E
keystroke_node_background_color=alt N

But you have to search for free keys...

---

### Post by dimeotane on 2009-11-15
I found that in version .9  I was able to enter in the tools menu properties "keystrokes" to define shortcut keys.  Instead of 'less' I used the down arrow key. 

I downloaded the newer version here:
[http://launchpadlibrarian.net/32070458/freemind_0.9.0RC4-0ubuntu1_all.deb](http://launchpadlibrarian.net/32070458/freemind_0.9.0RC4-0ubuntu1_all.deb)

---

### Post by hanzj on 2009-11-16
thanks, dimeotane, for the tip of changing keystrokes and the link to a ubuntu deb.

---

