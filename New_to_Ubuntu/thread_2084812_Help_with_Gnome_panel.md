---
title: "Help with Gnome panel"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by Hellaxe on 2012-11-16
Hello guys:
BIG digging on this but i&#7743; P****d off.
This is what happened yesterday when I was giving a class: the projector when't crazy and it blocked the desktop. Don't know why this was wierd.
Anyway after a reboot the "WindowPicker" was between the clock and the "switch user" applets.
After digging here I found this thread and I managed to put WindowPicker where it belongs on the right of GoHome applet, but it stays locked near the indication applet (battery, wireless, etc).
I can't move it to the left just near the GoHome applet.
Any ideas???
I'll give you the gconf-tree.xml, or part of it.
Thanks.

> <dir name="applet_1">
					<entry name="locked" mtime="1272540841" type="bool" value="true"/>
					<entry name="position" mtime="1272540841" type="int" value="5"/>
					<entry name="panel_left_stick" mtime="1272540841" type="bool" value="true"/>
					<entry name="bonobo_iid" mtime="1272540841" type="string">
						<stringvalue>OAFIID:GNOME_WindowPicker</stringvalue>
					</entry>
					<entry name="object_type" mtime="1272540841" type="string">
						<stringvalue>bonobo-applet</stringvalue>
					</entry>
					<entry name="toplevel_id" mtime="1272540841" type="string">
						<stringvalue>top_panel</stringvalue>

PS: made some changes: "locked" to false nothing happens and  add "panel_left_stick" also no changes.

---

### Post by oldos2er on 2012-11-16
Post moved to its own thread.

---

