---
title: "Ubuntu One &quot;no pairing record&quot;"
date: 2011-09-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sturmf on 2011-09-15
Hi!


I have my laptop upgraded to Oneiric and can't sync with Ubuntu One anymore. 
Therefore I deleted:

  > 
rm -r ~/.config/desktop-couch/  
rm -r ~/.local/share/desktop-couch/  
rm -r ~/.cache/desktop-couch/   


and removed the DesktopCouch and the Ubuntu One token entries from the gnome keyring.
  If I now start ubuntuone-control-panel-gtk on the  the services pane I get the message:[INDENT]   There is no Ubuntu One pairing record.
 [/INDENT]I now also executed without success:
  dbus-send --print-reply --dest=com.ubuntu.sso /credentials \     com.ubuntu.sso.ApplicationCredentials.login_to_get_credentials \     "string:Ubuntu One" "string:Workaround for LP:657850" int64:0 


Any idea what is still wrong?

Thanks Fabian

---

### Post by sturmf on 2011-09-15
Ok, by chance I just found an couchdb pairing tool.
After clicking on pairing with ubuntu one I got rid of the eror message.

Unfortunately still no contacts are synced and therefore the contacts list in evolution is empty.

So I still welcome any help!

---

