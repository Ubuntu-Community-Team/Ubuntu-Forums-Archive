---
title: "Gnome-Do not working!"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by ivancamilov on 2008-05-18
Thanks in advance for your help! I installed Gnome-Do a while ago, and I think its a great program, but it isn't working entirely for me. It only opens my programs, but if I try to open a file, it doesn't do anything... here's something I pulled from the console when I ran it:

(/usr/local/lib/gnome-do/Do.exe:11115): libgnomevfs-WARNING **: Internal error: the configuration system was not initialized. Did you call _gnome_vfs_configuration_init?

(/usr/local/lib/gnome-do/Do.exe:11115): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed

it prints a LOT of this error messages, and then this:

[Info 18:51:51.038] Deserializing HistogramRelevanceProvider... 
[Info 18:51:51.081] Successfully deserialized HistogramRelevanceProvider. 
[Info 18:51:51.096] Successfully loaded "Applications" item source. 
[Info 18:51:51.203] Successfully loaded "Define" action. 
[Info 18:51:51.205] Successfully loaded "Copy to..." action. 
[Info 18:51:51.207] Successfully loaded "Move to..." action. 
[Info 18:51:51.208] Successfully loaded "Move to Trash" action. 
[Info 18:51:51.273] Successfully loaded "File Indexer" item source. 
[Info 18:51:51.293] Successfully loaded "Firefox Bookmarks" item source. 
[Info 18:51:51.296] Successfully loaded "GNOME Special Locations" item source. 
[Info 18:51:51.298] Successfully loaded "Email" action. 
[Info 18:51:51.327] Successfully loaded "Open" action. 
[Info 18:51:51.329] Successfully loaded "Open Terminal Here" action. 
[Info 18:51:51.340] Successfully loaded "Open URL" action. 
[Info 18:51:51.403] Successfully loaded "Recent Files" item source. 
[Info 18:51:51.405] Successfully loaded "Reveal" action. 
[Info 18:51:51.406] Successfully loaded "Run" action. 
[Info 18:51:51.408] Successfully loaded "Run in Terminal" action. 
[Info 18:51:51.411] Successfully loaded "Internal GNOME Do Items" item source. 
[Info 18:51:51.418] Successfully loaded "GNOME Do Item Sources" item source. 
[Info 18:51:51.426] Searching for plugins in directory 
                    /home/ivan/.local/share/gnome-do/plugins 
[Info 18:51:51.497] Searching for plugins in directory /usr/local/share/gnome-do/plugins 
[Warn 18:51:51.500] Could not read plugins directory /usr/local/share/gnome-do/plugins: 
                    Directory '/usr/local/share/gnome-do/plugins' not found. 
[Info 18:51:51.504] Searching for plugins in directory /usr/share/gnome-do/plugins 
[Warn 18:51:51.506] Could not read plugins directory /usr/share/gnome-do/plugins: 
                    Directory '/usr/share/gnome-do/plugins' not found. 
[Info 18:51:51.845] Universe contains 445 objects. 
36
[Info 18:51:52.430] Binding key '<Super>space' for 
                    '/apps/gnome-do/preferences/key_binding'. You may change this 
                    keybinding with Configuration Editor (gconf-editor). 
[Info 18:51:55.613] Opening "/home/ivan/Desktop/File.txt"... 
Error showing url: The location or file could not be found.

Gnome-Do has opened a file once before after trying many many times (actually, the same one I tried to open just above) but I didn't change anything in the configuration, so it's really weird...

Finally, I think I should tell you that I'm on Feisty (don't want to upgrade since the sound on my Toshiba A-105 doesn't work in Gutsy -Haven't tried Hardy but i think it's the same problem) and installed GnomeDo through bzr.

PD: forgive me if you don't understand everything clearly, I'm still learning English!

---

### Post by nowshining on 2008-05-18
in synaptic look for any gnome_vfs items and try installing them or re-installing if they are already installed.

---

### Post by ivancamilov on 2008-05-19
Thanks for your help nowshining! unfortunately, it didn' work. I opened synaptic and selected a lot of packages named like 'gnome_vfs', but it didn't do anything... are there any special packages I should look for? (btw, I didn't now that gnome-do used GnomeVFS)

---

