---
title: "GTK UIManager - can I add stars in a menu?"
date: 2012-05-11
forum: Programming Talk
---

### Post by mendhak on 2012-05-11
Hi, I will try to explain what I want to achieve.  

Banshee used to have a notification area icon, from which you could rate the current song.  It looked like this:

[IMG]http://i.imgur.com/dhCdG.png[/IMG]

Now I am using Rhythmbox.  I would like to do something similar.  I found [this plugin project on github]("https://github.com/palfrey/rhythmbox-tray-icon/blob/master/tray_icon.py") which did the basics (play, next, prev) but it didn't have stars in it.  

[img]http://ubuntuforums.org/attachment.php?attachmentid=217729&stc=1&d=1336770327[/img]

I had a look at the code and it uses GTK UIManager XML:

```

    ui.add_ui_from_string(
		"""
		<ui>
		  <popup name='PopupMenu'>
			<menuitem action='PlayPause' />
			<menuitem action='Next' />
			<menuitem action='Previous' />
			<separator />
			<menuitem action='Quit' />
		  </popup>
		</ui>
		""")

```

My question, I'm actually looking for advice or even links, but please can you point me in the right direction?  I want to add stars to the menu, but how can I do it?  

There seems to be a <placeholder> you can add to the menu but ultimately, I don't know how to add the stars in there.  Any ideas?  Or, do I need to rewrite the plugin using some other framework?

Thanks in advance.   I am using Ubuntu 12.04.

---

