---
title: "Menu"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by laurielegit on 2008-11-23
Ok, this is a classic idiot mucks up his computer story. I was playing around with the edit menu utility in Xubuntu when I deleted somthing I shouldn't have. As a result I have had to manualy reconstruct my menu but there are still holes. Could someone post up the content of their menu so that I may copy it.

Thanks,

Laurie

---

### Post by m_l17 on 2008-11-23
Here is mine I modified a little: added run, terminal, home, and firefox to the menu.

I can't attach the menu.xml file but here it is:

```
<?xml version="1.0" encoding="UTF-8"?>
<xfdesktop-menu>
	<app name="Xfce Menu" cmd="" icon="xubuntu-logo"/>
	<separator/>
	<app name="Run Program" cmd="xfrun4" icon="xfce-system"/>
	<separator/>
	<app name="Terminal" cmd="xfterm4" icon="Terminal"/>
	<app name="Firefox" cmd="firefox" icon="firefox-3.0"/>
	<app name="Home" cmd="thunar" icon="gohome"/>
	<separator/>
	<menu name="Settings" icon="gnome-settings">
		<app name="Settings Manager" cmd="xfce-setting-show" icon="gnome-settings" snotify="true"/>
	</menu>
	<separator/>
	<include type="system" style="simple" unique="true" legacy="true"/>
	<separator/>
	<app name="Help" cmd="xfbrowser4 /usr/share/xubuntu-docs/about/xubuntu-index.html" icon="gnome-help"/>
	<app name="About Xfce" cmd="xfce4-about" icon="info"/>
	<builtin name="Quit" cmd="quit" icon="gnome-logout"/>
</xfdesktop-menu>
```

Copy, paste to mousepad and save as it menu.xml, in ~/.config/xfce4/desktop

Then go to Settings Manager ---> Menu editor, select the previous saved file. It should now work for you.

---

