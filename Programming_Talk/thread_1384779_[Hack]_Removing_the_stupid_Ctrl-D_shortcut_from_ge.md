---
title: "[Hack] Removing the stupid Ctrl-D shortcut from gedit"
date: 2010-01-18
forum: Programming Talk
---

### Post by sdaau on 2010-01-18
Hi all, 

Well, I had a lot of trouble getting rid of the stupid Ctrl-D keyboard shortcut in Gedit, which deletes a line. Why stupid? Because unlike a ton of other shortcuts in the menus in gedit, this one is NOT in the menus, and thus it cannot be edited via "Editable menu shortcut keys" ([Gedit/KeyboardShortcuts](http://live.gnome.org/Gedit/KeyboardShortcuts))

So basically, the situation is as here: 
[quote="http://osdir.com/ml/gedit-list/2009-11/msg00005.html"]
I was helping a buddy who is having the problem that he cannot change the shortcut for Delete Line, CTRL-D.

We have used a plugin for editing menu shortcuts, but this specifik shortcut does not seem to be a menu shortcut, and thus cannot be edited with the plugin.

Can somebody tell me how to change/remove the shortcut CTRL-D?

He is using Ubuntu 9.10[/quote]

In my case, I'd want [Gedit/LineToolsPlugin](http://live.gnome.org/Gedit/LineToolsPlugin) which uses Ctrl-D for duplicate line. Of course, by default it will not work either. 

Now, sure I can do:
```

apt-get source gedit
cd gedit-2.26.1/
nano ./gedit/gedit-view.c

```
and comment out this section in gedit-view.c:
```

	/* gtk_binding_entry_add_signal (binding_set, 
				      GDK_d, 
				      GDK_CONTROL_MASK,
				      "delete_from_cursor", 2,
				      G_TYPE_ENUM, GTK_DELETE_PARAGRAPHS,
				      G_TYPE_INT, 1); */

```
but since I don't know the exact compilation line, in the end, the gedit I can build fails quite miserably; the steps I take are: 
```

sudo apt-get install intltool gedit-dev libgconf2-dev
./configure --disable-spell
make

```
and while running gedit built in that way, I get errors: 
```

Error opening directory '/usr/local/lib/gedit-2/plugin-loaders': No such file or directory

```

So I thought, maybe there is a way to make a binary hack, so I don't have to go through all this building - and it turns out, there is! :D 

First, find out where is the binary, and change ownership to yourself
```

$ which gedit
/usr/bin/gedit
$ sudo chown myself\:myself /usr/bin/gedit

```

Then open /usr/bin/gedit in a hex editor (I actually used Notepad++ under wine :) ), then search for the string "delete_from_cursor", and change it to "delete_from_cursXX"; and then save /usr/bin/gedit. 

If now you run gedit under gdb, you will notice that when you press Ctrl-D, you get: 
```

sys:1: GtkWarning: gtk_binding_entry_activate(): binding "GeditView::<Control>d": could not find signal "delete_from_cursXX" in the `GeditView' class ancestry

```

and FINALLY - no more deletion of lines happen! In fact, if you have LineToolsPlugin installed, Ctrl-D starts duplicating lines instead - which finally makes gedit truly rock :) 

Before I found this hack, I also tried using gconf-editor to set the **/desktop/gnome/interface/gtk_key_theme** from Default to Emacs ([Gconf-editor - Wsms](http://wsms.wikiplanet.com/mediawiki/index.php/Gconf-editor) - btw, those themes refer to files: 
```

/usr/share/themes/Default/gtk-2.0-key/gtkrc
/usr/share/themes/Emacs/gtk-2.0-key/gtkrc

``` ); of course, while most key bindings changed, Ctrl-D was untouched. 

Also, I tried the suggestion in [Proper keyboard shortcuts in GTK+ &#8722; JNRowe](http://www.jnrowe.ukfsn.org/articles/configs/gtk.html): that is, I tried to make a new **~/.gtkrc-2.0** file, and place a key theme that would specifically override Ctrl-D: 
```

$ gedit ~/.gtkrc-2.0

binding "gtk-skip-d"
{
    bind "<ctrl>d" { "move-cursor" (logical-positions, 1, 0) }
}

class "GtkEntry" binding "gtk-skip-d"
class "GtkTextView" binding "gtk-skip-d"

```
While this also didn't have any effect before the hack, after the hack this Ctrl-D (which moves a cursor) takes precedence in gedit, from the Ctrl-D functionality enforced by the LineToolsPlugin (the line duplication) - so I had to (re)move ~/.gtkrc-2.0 in order to get the proper functioning I wanted. 

Well, hope this helps someone, 

Cheers!

---

### Post by harmck on 2010-04-20
Thanks a million, I normally would use Notepad++ and was always deleting lines just from habit in gedit. I had recently installed the same plugin as you, and thought it would override the Ctrl+D. 

Your little binary hack worked a charm. Took me 2 mins and works great :)

Cheers for the hard graft, 
Har

---

### Post by simmonds78 on 2010-08-05
Thanks so much for this tip. It worked perfectly. I've been trying on and off for a week to sort this CTRL+D issue out.  I'm also coming from notepad++ and using CTRL+D to duplicate a line was a feature I used constantly. That was the most nagging issue I had in making ubuntu my primary OS.  I was still willing to deal with it for all of the advantages though.

Thanks again,
-simmond78

---

### Post by emrys.r on 2010-12-02
Much easier work around....

[Unbind/Rebind Ctrl+D in Gedit]("http://blockofcode.wordpress.com/2010/05/09/unbindrebind-ctrld-in-gedit/")
The second example in page above has code to disable the default CTRL+D. Just make a new file [touch ~/gtkrc-2.0] and paste the code in.

This gedit plugin now works for duplicating lines using CTRL + D
[Gedit Advanced Editing Plugin]("http://live.gnome.org/Gedit/AdvancedEditingPlugin")

Awsome! at last I can duplicate lines in gedit! It was doing my head in![IMG]http://www.wackyb.co.nz/skype/smileys_v1.5.0.60/skype-wackyb-0170-headbang.gif[/IMG]

---

### Post by phishsauce on 2011-01-13
Awesome the ~/.gtkrc-2.0 unbinding worked for me (and the Advance editing tool Ctrl + d short works as well).

---

### Post by FloydPink on 2011-03-22
> **emrys.r said:**
> Much easier work around....

[Unbind/Rebind Ctrl+D in Gedit]("http://blockofcode.wordpress.com/2010/05/09/unbindrebind-ctrld-in-gedit/")
The second example in page above has code to disable the default CTRL+D. Just make a new file [touch ~/gtkrc-2.0] and paste the code in.

This gedit plugin now works for duplicating lines using CTRL + D
[Gedit Advanced Editing Plugin]("http://live.gnome.org/Gedit/AdvancedEditingPlugin")

Awsome! at last I can duplicate lines in gedit! It was doing my head in![IMG]http://www.wackyb.co.nz/skype/smileys_v1.5.0.60/skype-wackyb-0170-headbang.gif[/IMG]Thanks... Worked like a charm...
How would I make that change for all users? Also would this change be wiped with the next version of Gedit?

---

### Post by silverhawk_184 on 2011-06-27
Thanks,

Also, could someone make a plugin that incorporates duplication of selection? Like in notepad++. 

I would do it myself, but am swamped with work right now.

---

