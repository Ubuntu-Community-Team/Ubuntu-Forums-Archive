---
title: "Help with xmule compiling"
date: 2004-12-19
forum: Packaging and Compiling Programs
---

### Post by Humble on 2004-12-19
when i try to make xmule it gives me the following error report:

```
If you want verbose make output, try make VERBOSE=1.
make[1]: Entering directory `/home/pentti/programs/xmule-1.8.4/src'
make[2]: Entering directory `/home/pentti/programs/xmule-1.8.4/src/wx/xrc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/pentti/programs/xmule-1.8.4/src/wx/xrc'
Compiling AddFriend.cpp...
In file included from ListenSocket.h:27,
                 from updownclient.h:27,
                 from Friend.h:25,
                 from AddFriend.h:25,
                 from AddFriend.cpp:31:
Preferences.h: In member function `CString CPreferences::GetIRCNick()':
Preferences.h:1027: error: no matching function for call to `CString::CString(
   char[30])'
mfc.h:478: error: candidates are: CString::CString(const CString&)
mfc.h:454: error:                 CString::CString(const wxChar*)
mfc.h:450: error:                 CString::CString(wxChar*)
mfc.h:446: error:                 CString::CString()
Preferences.h: In member function `CString CPreferences::GetIRCServer()':
Preferences.h:1035: error: no matching function for call to `CString::CString(
   char[50])'
mfc.h:478: error: candidates are: CString::CString(const CString&)
mfc.h:454: error:                 CString::CString(const wxChar*)
mfc.h:450: error:                 CString::CString(wxChar*)
mfc.h:446: error:                 CString::CString()
Preferences.h: In member function `CString CPreferences::GetIRCChanNameFilter()
   ':
Preferences.h:1051: error: no matching function for call to `CString::CString(
   char[50])'
mfc.h:478: error: candidates are: CString::CString(const CString&)
mfc.h:454: error:                 CString::CString(const wxChar*)
mfc.h:450: error:                 CString::CString(wxChar*)
mfc.h:446: error:                 CString::CString()
Preferences.h: In member function `CString CPreferences::GetIrcPerformString()
   ':
Preferences.h:1075: error: no matching function for call to `CString::CString(
   char[255])'
mfc.h:478: error: candidates are: CString::CString(const CString&)
mfc.h:454: error:                 CString::CString(const wxChar*)
mfc.h:450: error:                 CString::CString(wxChar*)
mfc.h:446: error:                 CString::CString()
Preferences.h: In member function `CString CPreferences::GetMessageFilter()':
Preferences.h:1186: error: no matching function for call to `CString::CString(
   char[512])'
mfc.h:478: error: candidates are: CString::CString(const CString&)
mfc.h:454: error:                 CString::CString(const wxChar*)
mfc.h:450: error:                 CString::CString(wxChar*)
mfc.h:446: error:                 CString::CString()
Preferences.h: In member function `CString CPreferences::GetCommentFilter()':
Preferences.h:1190: error: no matching function for call to `CString::CString(
   char[512])'
mfc.h:478: error: candidates are: CString::CString(const CString&)
mfc.h:454: error:                 CString::CString(const wxChar*)
mfc.h:450: error:                 CString::CString(wxChar*)
mfc.h:446: error:                 CString::CString()
Preferences.h: In member function `CString CPreferences::GetDateTimeFormat()':
Preferences.h:1204: error: no matching function for call to `CString::CString(
   char[32])'
mfc.h:478: error: candidates are: CString::CString(const CString&)
mfc.h:454: error:                 CString::CString(const wxChar*)
mfc.h:450: error:                 CString::CString(wxChar*)
mfc.h:446: error:                 CString::CString()
Preferences.h: In member function `CString CPreferences::GetWSPass()':
Preferences.h:1217: error: no matching function for call to `CString::CString(
   char[256])'
mfc.h:478: error: candidates are: CString::CString(const CString&)
mfc.h:454: error:                 CString::CString(const wxChar*)
mfc.h:450: error:                 CString::CString(wxChar*)
mfc.h:446: error:                 CString::CString()
Preferences.h: In member function `CString CPreferences::GetWSLowPass()':
Preferences.h:1257: error: no matching function for call to `CString::CString(
   char[256])'
mfc.h:478: error: candidates are: CString::CString(const CString&)
mfc.h:454: error:                 CString::CString(const wxChar*)
mfc.h:450: error:                 CString::CString(wxChar*)
mfc.h:446: error:                 CString::CString()
Preferences.h: In member function `CString CPreferences::GetTemplate()':
Preferences.h:1285: error: no matching function for call to `CString::CString(
   char[2048])'
mfc.h:478: error: candidates are: CString::CString(const CString&)
mfc.h:454: error:                 CString::CString(const wxChar*)
mfc.h:450: error:                 CString::CString(wxChar*)
mfc.h:446: error:                 CString::CString()
In file included from Friend.h:25,
                 from AddFriend.h:25,
                 from AddFriend.cpp:31:
updownclient.h: In member function `void CUpDownClient::SetFileComment(char*)':
updownclient.h:288: error: no matching function for call to `CString::Format(
   const char[3], char*&)'
mfc.h:466: error: candidates are: void CString::Format(const wxChar*, ...)
AddFriend.cpp: In member function `void CAddFriend::OnAddBtn(wxCommandEvent&)':
AddFriend.cpp:119: error: no matching function for call to `CString::Format(
   const char[3], const wxChar*)'
mfc.h:466: error: candidates are: void CString::Format(const wxChar*, ...)
AddFriend.cpp:124: error: no matching function for call to `CString::Format(
   const char[3], const wxChar*)'
mfc.h:466: error: candidates are: void CString::Format(const wxChar*, ...)
AddFriend.cpp:136: error: cannot convert `const wxChar*' to `const char*' for
   argument `1' to `int atoi(const char*)'
AddFriend.cpp:136: error: cannot convert `const wxChar*' to `const char*' for
   argument `1' to `int atoi(const char*)'
AddFriend.cpp:166: error: cannot convert `const wxChar*' to `const char*' for
   argument `1' to `int sscanf(const char*, const char*, ...)'
make[1]: *** [AddFriend.o] Error 1
make[1]: Leaving directory `/home/pentti/programs/xmule-1.8.4/src'
make: *** [all] Error 2
```

---

