---
title: "Invisible windows instead of hide...C programming"
date: 2007-08-19
forum: Programming Talk
---

### Post by Hopeless on 2007-08-19
```
if (thePrefs::GetStartMinimized()) { 
		if (thePrefs::UseTrayIcon() && thePrefs::DoMinToTray()) {
			[COLOR="Red"]Hide_aMule();[/COLOR]
		} else {
			Iconize(TRUE);
		}
	}
```

Is there a way to make it invisible instead of hide...?

Thanks...

---

### Post by loell on 2007-08-19
i'm not sure i follow you, invisible window is a hidden window,

i believe this is c++ code not c .

could you provide more info on what would like to do?

---

### Post by Hopeless on 2007-08-19
sorry my programming skills are limited...

when you minimise you can see it at the bottom....i want to make it invisible completely and then use say ctrl+D to make visible again...

---

### Post by loell on 2007-08-19
in amule, in the preference --> general

check the **enable tray icon** and **minimize to tray icon**

and it wouldn't just minimize, it will hide the whole window when you click the minimize button, and show or hide when you click amule tray icon.

---

### Post by Hopeless on 2007-08-19
thanks,

unfortunately i know that one... 

i want to make it invisible completely and then use say ctrl+D to make visible again...

So instead of ```
Hide_aMule();
``` can i say ```
Invisible_aMule();
``` 

here is some more code that i think i might be able to fiddle with...

```
void CamuleDlg::CreateSystray()
{
	m_wndTaskbarNotifier = new CMuleTrayIcon();
	wxASSERT(m_wndTaskbarNotifier->IsOk());			
	// This will effectively show the Tray Icon.
	UpdateTrayIcon(0);
}	
	

void CamuleDlg::RemoveSystray()
{
	delete m_wndTaskbarNotifier;
	m_wndTaskbarNotifier = NULL;
}
```

maybe i could just ...

```
void CamuleDlg::CreateSystray()
{
	If Ctrl+D = True then {m_wndTaskbarNotifier = new CMuleTrayIcon();
	wxASSERT(m_wndTaskbarNotifier->IsOk());			
	// This will effectively show the Tray Icon.
	UpdateTrayIcon(0);
}
}	
```

???

What do you think? that way it would not create a icon... i know my c knowledge is very poor coming from a visual basic 6...into linux...neverless it's fun fun fun...

---

### Post by Hopeless on 2007-08-19
or fiddle here...
```
void CamuleDlg::Hide_aMule(bool iconize)
{
	if (IsShown() && ((last_iconizing + 2000) < GetTickCount())) { // 1 secs for sanity
		last_iconizing = GetTickCount();

		if (m_prefsDialog and m_prefsDialog->IsShown()) {
			m_prefsVisible = true;
			m_prefsDialog->Iconize(true);;
			m_prefsDialog->Show(false);
		} else {
			m_prefsVisible = false;
		}
		
		if (iconize) {
			Iconize(TRUE);
		}
		
		Show(FALSE);
	}

}


void CamuleDlg::Show_aMule(bool uniconize)
{
	if (!IsShown() && ((last_iconizing + 1000) < GetTickCount())) { // 1 secs for sanity
		last_iconizing = GetTickCount();
	
		if (m_prefsDialog && m_prefsVisible) {
			m_prefsDialog->Show(true);
			m_prefsDialog->Raise();
		}
		
		if (uniconize) {
			Show(TRUE);
			Raise();
		}
	}
}
```

to show 
```
void CamuleDlg::Hide_aMule(bool iconize)
{
	if (IsShown() && ((last_iconizing + 2000) < GetTickCount())) { // 1 secs for sanity
		last_iconizing = GetTickCount();

		if (m_prefsDialog and m_prefsDialog->IsShown()) {
			m_prefsVisible = true;
			m_prefsDialog->Iconize([COLOR="Red"]false[/COLOR]);;
			m_prefsDialog->Show(false);
		} else {
			m_prefsVisible = false;
		}
		
		if (iconize) {
			Iconize(TRUE);
		}
		
		Show(FALSE);
	}

}
```

????

easier? will it work do you think?

---

### Post by loell on 2007-08-19
the problem would be the key binding, ones it gets invisible , the key input will transfer to whatever desktop environment you're at. and the app could not listen for the keybaord input.

---

### Post by Hopeless on 2007-08-19
ideas on what should be done?
:popcorn:

---

### Post by loell on 2007-08-19
hmm.. looking at amule closely not the code by the way, but just how it behaves,

when in its trayed minimize, executing another amule instance will actually bring the app to visible mode. you could costumize Desktop Environment keyboard shortcuts , to just execute amule :)

programmaticaly, maybe you could use DBUS

---

